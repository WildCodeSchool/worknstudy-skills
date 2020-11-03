# Titre de la compétence

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- l'état (_state_) pour contrôler l'affichage d'un composant ✔️
- les composants enfants et les _props_ qu'on leur passe ✔️
- le déclenchement d'instructions en fonction des actions de l'utilisateur ✔️
- le déclenchement d'instructions en fonction de l'étape du cycle de vie du composant ou du changement de valeur de ses props ✔️
- l'usage d'un reducer (_useReducer_) pour gérer un état composé dans un composant
- l'état stocké dans un composant avec un _context provider_ et accessible dans ses descendants via `useContext` ❌

## 💻 J'utilise

### Un exemple personnel commenté ❌ / ✔️
```
  const [filtersQueryStr, setFiltersQueryStr] = useState('');
  useEffect(() => {
    const restaurantFilters = {
      moments: q1,
      specialties: q2,
      ambiances: q3,
      date: q4,
      districts: q5,
      dietSpecificities: q6,
      budget: q7,
      accesses: q8
    };

    if (q4) {
      const date = new Date(q4);
      restaurantFilters.date = date.getDay();
    }

    const updateQuery = async filters => {
      await setFiltersQueryStr(formatQueryStr(filters));
    };
    updateQuery(restaurantFilters);
  }, [q1, q2, q3, q4, q5, q6, q7, q8]);
  
  //un petit hook pour gérer les reponses du quizz qui sont sur des pages différentes
```

### Utilisation dans un projet ❌ / ✔️

[lien github](...)

Description :

### Utilisation en production si applicable ✔️

[lien du projet](https://github.com/WildCodeSchool/tlse-0919-js-boudu)

Description : 

### Utilisation en environement professionnel  ✔️

Description :

## 🌐 J'utilise des ressources

### Titre

- [la doc](https://reactjs.org/)
- la base

## 🚧 Je franchis les obstacles

### Point de blocage ❌ / ✔️

Description:

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️
