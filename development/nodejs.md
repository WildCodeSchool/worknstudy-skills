# Titre de la compétence

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- Comment développer en utilisant un système de *livereloading* (`nodemon` par exemple) ✔️
- La connexion de mon application à une base de données avec et sans ORM/ODM (avec `mongodb` puis `mongoose` par exemple) ❌ / ✔️
- Le développement d'une API REST et GraphQL (avec les packages `express` et `graphql` par exemple) ❌
- *Bonus : la manipulation des fichiers système avec `fs` et l'utilisation des streams en NodeJS* ❌ 

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```javascript
// UPLOAD FILE
//to access the files in public folder
app.use(express.static('public'));
app.use(fileUpload());
// file upload api
app.post('/upload', (req, res) => {
   if (!req.files) {
       return res.status(500).send({ msg: "file is not found" })
   }
   // accessing the file
   const myFile = req.files.file;
   // mv() method places the file inside public directory
   myFile.mv(`${__dirname}/public/${myFile.name}`, function (err) {
       if (err) {
           console.log(err)
           return res.status(500).send({ msg: "Error occured" });
       }
       // return the response with file path and name
       return res.send({name: myFile.name, path: `/${myFile.name}`});
   });
})
```

### Utilisation dans un projet ✔️

[Projet personnel lood](https://github.com/mathildetho/lood_back)

Description : Création d'une application dans le même esprit que Tinder mais qui met en relation en fonction des goûts culinaires. Elle permet de trouver son âme soeur culinaire. Création d'une API interne. Les fonctionnalités mises en place : authentification, filtrage, favoris, chat et site responsive.
Utilisation de NodeJS, ExpressJS, MySQL, Socket.io en back.

### Utilisation en production si applicable ❌ 

[lien du projet](...)

Description :

### Utilisation en environement professionnel ❌ 

Description :

## 🌐 J'utilise des ressources

- [titre](lien) : description

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
