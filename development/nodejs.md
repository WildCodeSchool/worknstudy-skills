# Titre de la compétence

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- Comment développer en utilisant un système de *livereloading* (`nodemon` par exemple) ✔️
- La connexion de mon application à une base de données avec et sans ORM/ODM (avec `mongodb` puis `mongoose` par exemple) ✔️
- Le développement d'une API REST et GraphQL (avec les packages `express` et `graphql` par exemple)  ✔️
- *Bonus : la manipulation des fichiers système avec `fs` et l'utilisation des streams en NodeJS* ❌ / ✔️

## 💻 J'utilise

### Un exemple personnel commenté  ✔️

```javascript
// get restaurant by id
router.get('/:id', (req, res) => {
  const { id } = req.params;
  const query = 'SELECT * FROM Restaurant WHERE id= ?';
  connection.query(query, id, (err, results) => {
    if (err) {
      res.status(500).send('Erreur lors de la récupération des informations sur les restaurants');
    } else {
      res.json(results);
    }
  });
});
```

### Utilisation dans un projet  ✔️

[lien github](https://github.com/WildCodeSchool/tlse-0919-js-boudu)

Description :

### Utilisation en production si applicable ✔️

[lien du projet](...)

Description : au sein de ma boite mais pas d'exemple sous la main

### Utilisation en environement professionnel ✔️

Description : architecture en package

## 🌐 J'utilise des ressources

### Titre

- [la doc](http://expressjs.com/fr/4x/api.html#res)
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
