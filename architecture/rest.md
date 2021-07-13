# REST API
> ❌ A travailler
> ✔️ Auto validation par l'étudiant
> 👌 Validation par le formateur


## 🎓 J'ai compris et je peux expliquer
- les verbes HTTP ✔️
- les statuts HTTP ✔️
- les endpoints ✔️
- CORS ✔️
- la nomenclature recommandée pour les routes ✔️


## 💻 J'utilise
### Un exemple personnel commenté ✔️
``` javascript
const express = require('express');
const router = express.Router();
const connection = require("../config");
const bcrypt = require('bcrypt');
const jwt = require('jsonwebtoken');

// create profile
router.post('/', (req, res) => {
    // verify password length >= 10
    // crypt the password
    const hash = bcrypt.hashSync(req.body.password, 10);
    // take all information about the user 
    const formBody = {
        pseudo: req.body.pseudo,
        description: req.body.description,
        image: req.body.image,
        sexe: req.body.sexe,
        password: hash,
    };
    // insert into the database the new user
    connection.query('INSERT INTO user SET ?', [formBody], (err, results) => {
        if(err) {
            // if error, response negative
            res.status(500).send('Erreur lors de la création de l\'utilisateur');
        };
        // send response positive
        res.sendStatus(201);
    });
});
```

### Utilisation dans un projet ✔️
[Projet personnel lood](https://github.com/mathildetho/lood_back/blob/master/routes/users.js)
Description : Création d'une application dans le même esprit que Tinder mais qui met en relation en fonction des goûts culinaires. Elle permet de trouver son âme soeur culinaire. Création d'une API interne. Les fonctionnalités mises en place : authentification, filtrage, favoris, chat et site responsive. Par exemple, pour créer un profil, l'endpoint sera '/users' et sera une requête de type POST. On indique une requête SQL d'insertion à la table user avec les données envoyées.

### Utilisation en production si applicable ✔️
### Utilisation en environement professionnel ✔️
[lien du projet Hellia](https://app.hellia.fr/)
Description : Utilisation d'une API Rest sur mon projet d'entreprise. Utilisation du Router d'express et de middlewares pour chaque requêtes souhaitées.


## 🌐 J'utilise des ressources
### [uptrends](https://www.uptrends.fr/qu-est-ce-que/rest-api)
- Article sur la rest api
### [practical programming](https://practicalprogramming.fr/node-js-api)
- Article sur la rest api


## 🚧 Je franchis les obstacles
### Point de blocage ✔️
Description: Lorsqu'une quittance est créée, elle est liée à un contrat de bail et donc à un locataire. Pour pouvoir récupérer toutes les quittances d'un locataire en particulier, il a fallu rajouté une route GET dans le router locataire avec un paramètre l'id du locataire. Nous devons d'abord récupérer tous les contrats liés au locataire, puis les quittances liées à chaque contrat. Afin de récupérer chaque quittance avec ses versements et ses possibles changements de loyer, il faut pouvoir regrouper ces 3 tables puis l'envoyer en front. 
Pour récupérer tous les contrats, il fallait utiliser objection.js, comme je ne connaissais pas encore, j'ai dû me documenter.

Plan d'action : (à valider par le formateur)
- action 1 : se documenter sur objection.js pour pouvoir récupérer une table lié par une clé étrangère avec une autre. 
- action 2 : utilisation de [eagerAlgorithm() et eager()](https://github.com/Vincit/objection.js/blob/v1/doc/api/query-builder/eager-methods.md#eageralgorithm) pour récupérer les relations. Ici, on récupère la relation du modèle Locataire avec sa relation many to many 'contrats'.
- action 3 : pour récupérer les quittances de chaque contrats liées au locataire, on récupère les quittances avec une query(). Ensuite pour récupérer les tables liées à cette quittance (versements et changementsLoyer), nous allons mapper, en utilisant async/await, sur chaque quittance et faire une query() sur chaque modèle de table en filtrant avec where() selon la clé étrangère refQuittance (l'id de la quittance). Pour attendre que toutes ces promesses soient résolues avant de passer à la suite, nous utilisons la méthode Promise.all().


## 📽️ J'en fais la démonstration ❌
