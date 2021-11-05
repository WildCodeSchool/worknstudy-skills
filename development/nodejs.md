# Titre de la compétence

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- Comment développer en utilisant un système de _livereloading_ (`nodemon` par exemple) ✔️
- La connexion de mon application à une base de données avec et sans ORM/ODM (avec `mongodb` puis `mongoose` par exemple) ✔️
- Le développement d'une API REST et GraphQL (avec les packages `express` et `graphql` par exemple) ✔️
- _Bonus : la manipulation des fichiers système avec `fs` et l'utilisation des streams en NodeJS_ ✔️

## 💻 J'utilise

### Un exemple personnel commenté

```javascript
const nodemailer = require("nodemailer");
const User = require("../models/users");
const {
  MAIL_SERVICE,
  MAIL_ADRESS,
  MAIL_PASSWORD,
  MAIL_CLIENT_URL,
} = require("../env");

module.exports.login = async (req, res) => {
  const user = await User.findByEmail(req.body.email, false);
  if (
    user &&
    (await User.verifyPassword(user.encrypted_password, req.body.password))
  ) {
    if (req.body.stayConnected) {
      req.session.cookie.maxAge = 7 * 24 * 60 * 60 * 1000;
    }
    req.session.cookie.maxAge = 24 * 60 * 60 * 1000;
    req.session.userId = user.id;
    req.session.save((err) => {
      if (err) return res.sendStatus(500);
      const userDetails = {
        id: user.id,
        firstname: user.firstname,
        lastname: user.lastname,
        role: user.role,
      };
      return res.status(200).json(userDetails);
    });
  } else {
    res.sendStatus(401);
  }
};

module.exports.logout = async (req, res) => {
  req.session.destroy((err) => {
    res.clearCookie("session_id", { path: "/" });
    if (err) return res.sendStatus(500);
    return res.sendStatus(200);
  });
};
```

### Utilisation dans un projet ❌

[lien github](https://github.com/cleroy117/Atelier-Fil-Rouge/blob/main/app.js)

Description :

const express = require("express");
require("dotenv").config;
const connection = require("./connection");

const app = express();
app.use(express.json());

app.get("/musics", (req, res) => {
const id = req.query.id;
const existsOnVinyl = req.query.existsOnVinyl;
const created_time = req.query.created_time;
const bpm = req.query.bpm;
let sql = "SELECT \* FROM track";
const sqlValues = [];
if (id && existsOnVinyl && created_time && bpm) {
sql += " WHERE id = ?";
sqlValues.push(id);
sql += " AND existsOnVinyl = ?";
sqlValues.push(existsOnVinyl);
sql += " AND created_time = ?";
sqlValues.push(created_time);
sql += " AND bpm = ?";
sqlValues.push(bpm);
} else if (id) {
sql += " WHERE id = ?";
sqlValues.push(id);
} else if (existsOnVinyl) {
sql += " WHERE existsOnVinyl = ?";
sqlValues.push(existsOnVinyl);
} else if (created_time) {
sql += " WHERE bpm = created_time";
sqlValues.push(bpm);
} else if (bpm) {
sql += " WHERE bpm = ?";
sqlValues.push(bpm);
}
connection.query(sql, sqlValues, (err, results) => {
if (err) {
return res.status(500).json({ err: err.message, sql: err.sql });
} else if (results.length === 0) {
res.status(200).send("No tracks match");
}
return res.status(200).json(results);
});
});

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

### Point de blocage ❌ / ✔️

Description:

Plan d'action : (à valider par le formateur)

- action 1 continuer d'approfondir en utilisant Node sur notre projet ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌
- J'ai fait une [présentation](...) ❌
