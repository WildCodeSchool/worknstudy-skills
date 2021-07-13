# React
> ❌ A travailler
> ✔️ Auto validation par l'étudiant
> 👌 Validation par le formateur


## 🎓 J'ai compris et je peux expliquer
- l'état (_state_) pour contrôler l'affichage d'un composant ✔️
- les composants enfants et les _props_ qu'on leur passe ✔️
- le déclenchement d'instructions en fonction des actions de l'utilisateur ✔️
- le déclenchement d'instructions en fonction de l'étape du cycle de vie du composant ou du changement de valeur de ses props ✔️
- l'usage d'un reducer (_useReducer_) pour gérer un état composé dans un composant ✔️
- l'état stocké dans un composant avec un _context provider_ et accessible dans ses descendants via `useContext` ✔️ 


## 💻 J'utilise
### Un exemple personnel commenté ✔️
```javascript
import { ApolloError } from '@apollo/client';
import React from 'react';
import { connect } from 'react-redux';
import { StaticContext } from 'react-router';
import { Route, Redirect, RouteComponentProps } from 'react-router-dom';
import { AnyAction, bindActionCreators, Dispatch } from 'redux';
import * as snackbarsActions from '../../../reducers/snackbar/actions';

const PrivateRoute = (props: {
  addSnackbar: (
    icon: string,
    message: { message: string },
    time: number
  ) => void;
  path: string;
  component:
    | React.ComponentType<never>
    | React.ComponentType<RouteComponentProps<never, StaticContext, unknown>>;
}) => {
  // récupérer s'il y a un token (user connecté)
  const authToken = localStorage.getItem('token');

  if (!authToken) {
    // si pas connecté, redirection et snackbar d'indication
    props.addSnackbar(
      'warning',
      {
        message: 'Pour accéder à cette page, tu dois te connecter.',
      },
      3000
    );
    return <Redirect to="/se-connecter" />;
  }

  // sinon peut accèder à la route demandé
  return <Route path={props.path} component={props.component} />;
};

// permet de faire l'appel à l'action d'ajout de la snackbar
const mapDispatchToProps = (dispatch: Dispatch<AnyAction>) => {
  return {
    addSnackbar: bindActionCreators(snackbarsActions.add, dispatch),
  };
};

export default connect(null, mapDispatchToProps)(PrivateRoute);

// exemple private route dans le composant App.tsx
<PrivateRoute path="/looding/:userId" component={HomeLooder} />
```

### Utilisation dans un projet ✔️
[Projet personnel lood](https://github.com/mathildetho/lood/blob/authentification/apps/front-client/src/app/components/Feedback/SnackBar/SnackBar.component.tsx)
Description : Création d'une application dans le même esprit que Tinder mais qui met en relation en fonction des goûts culinaires. Elle permet de trouver son âme soeur culinaire. Le front est créé via cette librairie.

### Utilisation en production si applicable ✔️
[Projet Hackathon Treap](https://treap.netlify.app)
Description : Le but était de créer une application web permettant de voyager tout en restant chez soi. Treap permet de nous faire voyager culinairement. Utilisation de 2 API externes. Plusieurs fonctionnalités ont été développés : recherche par pays, accès aléatoire d’un plat et d’une boisson, changement de plat ou boisson et accès aux informations d’un plat ou boisson en particulier.

### Utilisation en environement professionnel ✔️
``` javascript
import React from 'react';
import { connect } from 'react-redux';

import { makeStyles } from '@material-ui/core/styles';
import CircularProgress from '@material-ui/core/CircularProgress';
import Icon from '../../DataDisplay/Icon/Icon';
import CheckSVG from '../../../resources/img/check.svg';
import ErreurSVG from '../../../resources/img/exclam.svg';
import EnCoursSVG from '../../../resources/img/encours.svg';
import ArrowUp from '../../../resources/img/arrowUp.svg';
import ArrowDown from '../../../resources/img/arrowDown.svg';

import './Stepper.css';

const useStyles = makeStyles(() => ({
	root: {
		'& .MuiCircularProgress-colorPrimary': {
			color: 'var(--secondary-color-400)',
			position: 'absolute',
			top: '-3px',
			left: '-3px',
		},
		'& .MuiCircularProgress-svg': {
			color: 'var(--secondary-color-400)',
			position: 'absolute',
			cursor: 'auto',
		},
	},
	erreur: {
		'& .MuiCircularProgress-colorPrimary': {
			color: 'var(--alert-color)',
			position: 'absolute',
			top: '-3px',
			left: '-3px',
		},
		'& .MuiCircularProgress-svg': {
			color: 'var(--alert-color)',
			position: 'absolute',
			cursor: 'auto',
		},
	},
}));

const Stepper = (props) => {
	const {
		steps,
		activeStep,
		pageName,
		message,
		availableStepsIndeces,
		setStep,
		nostepper,
		currentStep,
		visible,
		setVisible,
	} = props;

	const availableSteps = availableStepsIndeces.map((index) => steps[index]);

	const allEtapesIndex = [];
	availableStepsIndeces.forEach((step, index) => allEtapesIndex.push(index));

	const active = currentStep + 1;
	let progress;
	if (allEtapesIndex.length === active) {
		progress = allEtapesIndex.length;
	} else {
		progress = allEtapesIndex[active];
	}

	const progression = (progress / allEtapesIndex.length) * 100;

	const classes = useStyles();

	const indexErreur = availableSteps.findIndex((etape) =>
		['ETAT_ERREUR', 'ETAT_EN_COURS_ERREUR'].includes(etape.etat),
	);

	const etapeCliquable = (step) => {
		let newAvailableSteps;
		if (indexErreur === -1) {
			newAvailableSteps = availableSteps;
		} else {
			newAvailableSteps = availableSteps.slice(0, indexErreur + 1);
		}

		// si une étape contient une erreur toutes les suivantes sont disabled
		if (step.etat === 'ETAT_ERREUR' && newAvailableSteps.includes(step)) {
			return true;
		}

		if (step.etat === 'ETAT_COMPLET' && newAvailableSteps.includes(step)) {
			return true;
		}

		return false;
	};

	// aller à une étape
	const allerEtape = (index, step) => {
		let bonStep;
		if (index === 0 || activeStep === index) {
			return setStep(index);
		}
		if (
			activeStep + 1 === index &&
			(step.etat === 'ETAT_COMPLET' || step.etat === 'ETAT_ERREUR')
		) {
			bonStep = activeStep + 1;
			return setStep(bonStep);
		}
		if (activeStep - 1 === index) {
			bonStep = activeStep - 1;
			return setStep(bonStep);
		}
		if (
			activeStep === 0 &&
			(step.etat === 'ETAT_COMPLET' || step.etat === 'ETAT_ERREUR')
		) {
			bonStep = activeStep + index;
			return setStep(bonStep);
		}
		if (
			activeStep < index &&
			(step.etat === 'ETAT_COMPLET' || step.etat === 'ETAT_ERREUR')
		) {
			const difference = index - activeStep;
			bonStep = activeStep + difference;
			return setStep(bonStep);
		}
		const difference = activeStep - index;
		bonStep = activeStep - difference;
		return setStep(bonStep);
	};

	const dernierStep = (index) => {
		const etapes = [...availableSteps];
		const dernier = etapes.pop();
		return availableSteps[index] === dernier;
	};

	const voirToutesLesEtapes = () => {
		setVisible(!visible);
	};

	const stepperVisible = () => {
		if (visible) {
			return '--visible';
		}
		return '';
	};

	const calculerDonneesPourAffichage = (index) => {
		const step = steps[index];
		const { etat } = step;

		let donneesDAffichage = {
			texte: 'Non défini',
			icone: undefined,
			className: '',
			cliquable: false,
		};

		switch (etat) {
			case 'ETAT_INCOMPLET':
				donneesDAffichage = {
					texte: 'Incomplet',
					icone: undefined,
					className: '--incomplet',
				};
				break;
			case 'ETAT_COMPLET':
				donneesDAffichage = {
					texte: 'Complété',
					icone: CheckSVG,
					className: '--complet',
				};
				break;
			case 'ETAT_ERREUR':
				donneesDAffichage = {
					texte: 'Erreur',
					icone: ErreurSVG,
					className: '--erreur',
				};
				break;
			case 'ETAT_EN_COURS':
				donneesDAffichage = {
					texte: 'En cours',
					icone: EnCoursSVG,
					className: '--active',
				};
				break;
			case 'ETAT_EN_COURS_ERREUR':
				donneesDAffichage = {
					texte: 'En cours avec erreur',
					icone: ErreurSVG,
					className: '--erreur',
				};
				break;
			default:
				break;
		}

		donneesDAffichage.cliquable = etapeCliquable(step);
		donneesDAffichage.dernier = dernierStep(index);

		return donneesDAffichage;
	};

	return (
		<div className={nostepper ? 'no-stepper' : `stepper --is-flex`}>
			<div className="stepper__ici --is-flex --is-flex-row">
				<div className="stepper__ici-titre">
					<h4 className="stepper__ici-titre-page --h4">{pageName}</h4>
					<p className="stepper__ici-titre-etape">{message}</p>
				</div>
				<div
					className={`stepper__ici-progression ${
						indexErreur > 0 ? classes.erreur : classes.root
					}`}
				>
					<CircularProgress
						variant="static"
						value={indexErreur > 0 ? '100' : progression}
					/>
					{indexErreur > 0 && (
						<Icon
							className="stepper__ici-progression--erreur"
							path={ErreurSVG}
						/>
					)}
				</div>
				<div
					className="stepper_defilement"
					role="presentation"
					onClick={() => voirToutesLesEtapes()}
				>
					<Icon
						className="stepper_defilement-icone"
						path={visible ? ArrowDown : ArrowUp}
					/>
				</div>
			</div>
			<div className="stepper__compact" />
			<div
				className={`stepper__alletapes --is-flex stepper__alletapes${stepperVisible()}`}
			>
				{availableSteps.map((step, index) => {
					const donneesDAffichage = calculerDonneesPourAffichage(index);

					return (
						<div
							className="stepper__etapes --is-flex --is-flex-row"
							key={index}
						>
							<div
								className="stepper__etape --is-flex"
								role="presentation"
								onClick={
									donneesDAffichage.cliquable
										? () => allerEtape(index, step)
										: null
								}
							>
								<p
									className={`stepper__etape-title stepper__etape-title${donneesDAffichage.className}`}
								>
									{step.data.title}
								</p>
								<p
									className={`stepper__etape-complet stepper__etape-complet${donneesDAffichage.className}`}
								>
									{donneesDAffichage.texte}
								</p>
							</div>
							<div className="stepper__etapes-check">
								<Icon
									onClick={
										donneesDAffichage.cliquable
											? () => allerEtape(index, step)
											: null
									}
									path={donneesDAffichage.icone}
									className={`stepper__etapes-check-svg stepper__etapes-check-svg${donneesDAffichage.className}`}
								/>
								<div
									className={`stepper__etapes-check-line stepper__etapes-check-line${
										donneesDAffichage.className
									} ${
										donneesDAffichage.dernier
											? 'stepper__etapes-check-line--dernier'
											: ''
									}`}
								/>
							</div>
						</div>
					);
				})}
			</div>
		</div>
	);
};

const mapStateToProps = (state) => {
	return {
		message: state.header.additionalMessage,
	};
};

export default connect(mapStateToProps)(Stepper);
```
Description : Lors de mon alternance, j'ai été amené à créé un fil d'ariane, un composant nommé Stepper. Il sera appelé à chaque création/modification de formulaires, que ce soit pour un bail, un locataire, un logement ou une société. Le but est que l'utilisateur puisse savoir où il en est sur son formulaire (indication du type de formulaire, les différents titres, le nombre d'étapes qu'il lui reste, un circular progress, les états des étapes, etc).


## 🌐 J'utilise des ressources
### [Stackoverflow](https://stackoverflow.com)
- utilisation lors de problèmes que je n'arrive pas à résoudre moi-même, je regarde si d'autres développeurs ont eu le même problème et comment ils l'ont résolus.
### [Medium](https://medium.com)
- veille journalière sur des articles liés au développement. Pour cela, je suis inscrite à une newsletter qui présente les meilleurs articles du jour.


## 🚧 Je franchis les obstacles
### Point de blocage ❌ 


## 📽️ J'en fais la démonstration  ✔️
- J'ai fait une [présentation](https://gist.github.com/mathildetho/2a4d6c74aaf20f9a9b40dbaf5026833b "description des memoize hooks")
