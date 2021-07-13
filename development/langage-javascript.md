# Langage Javascript
> ❌ A travailler
> ✔️ Auto validation par l'étudiant
> 👌 Validation par le formateur


## 🎓 J'ai compris et je peux expliquer
- les `structures` de base du langage ✔️
- les normes `ecmascript` ✔️
- l'utilisation de l'`asynchrone` ✔️
- les spécifités du mot-clef `this` ✔️


## 💻 Je code en Javascript
### Un exemple de code commenté ✔️
```javascript
// handle event to change the meal
const changeMeal = () => {
    // take the name of the flag
    const nameflag = props.match.params.nameflag;
    // take data of the nameFlag
    axios.get(`https://www.themealdb.com/api/json/v1/1/filter.php?a=${nameflag}`)
        .then((res) => {
            // after getting the promise change the state randomly
            setMeals(res.data.meals[Math.floor(Math.random()* res.data.meals.length)])
        })
};
```

### Utilisation dans un projet ✔️
[Projet Hackathon Treap](https://github.com/mathildetho/Treap)
Description : Le but était de créer une application web permettant de voyager tout en restant chez soi. Treap permet de nous faire voyager culinairement. Utilisation de 2 API externes. Développement en ReactJS. Plusieurs fonctionnalités ont été développés : recherche par pays, accès aléatoire d’un plat et d’une boisson, changement de plat ou boisson et accès aux informations d’un plat ou boisson en particulier. 

### J'ai utilisé ce langage en production ✔️
[Projet d'école Best Games](https://best-games.netlify.app)
Description : Création d'un générateur de jeux vidéos avec une API externe. Fonctionnalités : filtrage, suppression, accès plus en détail aux informations d'un jeu.

### J'ai utilisé ce langage en environement professionnel ✔️
exemple de code lié au projet lié à l'alternance :
```javascript
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
```
Description : lors de mon alternance, je suis amené à utiliser javascript. Dans l'exemple, je réalisais un fil d'ariane pour un formulaire. Il existe plusieurs étapes à valider, si une étape n'est pas complétée ou en erreur, les prochaines étapes ne peuvent pas l'être et ne sont donc pas cliquable. Ainsi, ces dernières ont un style et un texte différent selon son état.


## 🌐 J'utilise des ressources ✔️
- [MDN web docs](https://developer.mozilla.org/fr/docs/Web/JavaScript) : outil indispensable pour vérifier de la bonne utilisation de JavaScript


## 🚧 Je franchis les obstacles
### Point de blocage ✔️
Description: Pour mon projet d'entreprise, lors du développement de la fonctionnalité quittancement, il m'a fallu voir comment calculer le montant d'un élément au prorata (selon le temps écoulé dans le logement). Le nombre de jours dans le mois peuvent être différents selon les années (31, 30, 29 ou 28). Le montant journalier ne sera donc pas le même en fonction du mois et de l'année. Au départ, je ne savais pas comment calculer un montant au prorata.

Plan d'action : (à valider par le formateur)
- action 1 : j'ai d'abord effectué des recherches en ligne sur le calcul du loyer au prorata en fonction de la loi.
- action 2 : ensuite, j'ai créé un schéma des données souhaitées (date de début et fin de période, le montant de l'élément sur 1 mois complet) et ce qui doit être calculé (le nombre de mois dans la période, le nombre de jours dans le/les mois de la période, le montant journalier selon le nombre de jours compris dans chaque mois de la période), une fois avoir calculé tout cela, on calcule alors le total de chaque mois.
- action 3 : création de tests unitaires pour vérifier chaque calculs.


## 📽️ J'en fais la démonstration ✔️
- J'ai fait une [présentation](https://drive.google.com/drive/folders/1w0D8q6YaNfH4KkK4PrUm1oQLy9YgfRdp?usp=sharing "dossier composé de plusieurs fiches liées à JavaScript")

