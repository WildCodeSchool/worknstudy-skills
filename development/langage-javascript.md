# Langage Javascript

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- les `structures` de base du langage ✔️
- les normes `ecmascript` ✔️
- l'utilisation de l'`asynchrone` ❌
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

[https://github.com/mathildetho/Treap] Projet Hackathon

Description : Le but était de créer une application web permettant de voyager tout en restant chez soi. Treap permet de nous faire voyager culinairement. Utilisation de 2 API externes. Développement en ReactJS. Plusieurs fonctionnalités ont été développés : recherche par pays, accès aléatoire d’un plat et d’une boisson, changement de plat ou boisson et accès aux informations d’un plat ou boisson en particulier.

### J'ai utilisé ce langage en production ✔️

[https://best-games.netlify.app] Projet école

Description : Création d'un générateur de jeux vidéos avec une API externe. Fonctionnalités : filtrage, suppression, accès plus en détail aux informations d'un jeu.

### J'ai utilisé ce langage en environement professionnel ✔️

exemple de code lié au projet :
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
Description : lors de mon alternance, je suis amené à utiliser javascript. Dans l'exemple, je réalisais un fil d'ariane pour un formulaire. Il existe plusieurs étapes à valider, si celle-ci n'est pas complétée ou en erreur, les prochaines étapes ne peuvent pas l'être et ne sont donc pas cliquable. Ainsi, ces dernières ont un style et un texte différent selon son état.

## 🌐 J'utilise des ressources ✔️

### MDN wdb docs

- [https://developer.mozilla.org/fr/docs/Web/JavaScript] : outil indispensable pour vérifier de la bonne utilisation de JavaScript

## 🚧 Je franchis les obstacles

### Point de blocage ❌ / ✔️

Description:

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ 
- J'ai fait une [présentation](...) ❌ / ✔️

