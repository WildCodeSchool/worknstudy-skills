# Node
> ❌ A travailler
> ✔️ Auto validation par l'étudiant
> 👌 Validation par le formateur


## 🎓 J'ai compris et je peux expliquer
- Comment développer en utilisant un système de *livereloading* (`nodemon` par exemple) ✔️
- La connexion de mon application à une base de données avec et sans ORM/ODM (avec `mongodb` puis `mongoose` par exemple) ✔️
- Le développement d'une API REST et GraphQL (avec les packages `express` et `graphql` par exemple) ✔️
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
[Projet personnel lood](https://github.com/mathildetho/lood/blob/back/apps/back/src/app.ts)
Description : Création d'une application dans le même esprit que Tinder mais qui met en relation en fonction des goûts culinaires. Elle permet de trouver son âme soeur culinaire. Création d'une REST API avec NodeJS et express.

### Utilisation en production si applicable ✔️
[lien du projet lamas](https://lamas.wns.wilders.dev)
Description : Projet réalisé durant l'alternance en équipe de 5 développeurs. Il s'agit d'une application pour les cours à distance. Le but ? Avoir plus d'interactions entre les élèves et professeurs. Comment ? Avec des partage d'émotions avec des emojis mais aussi l'interaction visuelle et textuelle.

### Utilisation en environement professionnel ✔️
Description : utilisation d'une API REST via NodeJS. Mise en place de triggers avec node-schedule.


## 🌐 J'utilise des ressources
### [NodeJS](https://nodejs.org/en/)
- Documentation de NodeJS
### [Objection.js](https://vincit.github.io/objection.js/)
- Documentation de Objection.js


## 🚧 Je franchis les obstacles
### Point de blocage ❌


## 📽️ J'en fais la démonstration ✔️
- J'ai fait une [fiche](https://docs.google.com/document/d/1wRjaaq-eUdF7M-VcnttxCNtm9GA6Epd8rOUKq4W4ym4/edit)
