# GraphQL

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- la différence entre REST et GraphQL ✔️
- les besoins auxquels répond GraphQL ✔️
- la définition d'un schéma ✔️
- Query ✔️
- Mutation ✔️
- Subscription ✔️

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```
import { gql } from "@apollo/client";

import { ExpeditionFragment } from "../fragments";

export const QUERY_GET_ONE_EXPEDITION = gql`
  query oneExpedition($id: ID!) {
    oneExpedition(id: $id) {
      ...ExpeditionFragment
    }
  }
  ${ExpeditionFragment}
`;
// Ici on définit une query oneExpedition avec paramètre obligatoire
// Celle-ci retournera une expédition avec les champs spécifiés dans ExpeditionFragment

export const QUERY_GET_EXPEDITIONS = gql`
  query allExpeditions {
    allExpeditions {
      ...ExpeditionFragment
    }
  }
  ${ExpeditionFragment}
`;
```

// Ici on peut voir 2 querys : une pour récupérer une expedition avec son id et l'autres pour récupérer toute les expéditions

### Utilisation dans un projet ✔️

[lien github](https://github.com/wild-projet/2104-wns-lyon-groupe4-front)

Description : projet alternance

### Utilisation en production si applicable❌

[lien du projet](...)

Description :

### Utilisation en environement professionnel ❌

Description :

## 🌐 J'utilise des ressources

### Titre

- lien
- description

## 🚧 Je franchis les obstacles

### Point de blocage ❌

Description: ne connais pas du tout

Plan d'action : (à valider par le formateur)

- action 1 ❌
- action 2 ❌
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌
- J'ai fait une [présentation](...) ❌
