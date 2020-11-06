# REST API

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- les verbes HTTP ✔️
- les statuts HTTP ✔️
- les endpoints ✔️
- CORS ❌ / ✔️
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

Description : Création d'une application dans le même esprit que Tinder mais qui met en relation en fonction des goûts culinaires. Elle permet de trouver son âme soeur culinaire. Création d'une API interne. Les fonctionnalités mises en place : authentification, filtrage, favoris, chat et site responsive.
Utilisation de ReactJS, Material-ui, Redux en front.

### Utilisation en production si applicable ❌

[lien du projet](...)

Description :

### Utilisation en environement professionnel ❌

Description :

## 🌐 J'utilise des ressources

### Titre

- lien
- description

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
