# REST API

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- les verbes HTTP ✔️
- les statuts HTTP ✔️
- les endpoints  ✔️
- CORS ✔️
- la nomenclature recommandée pour les routes ✔️

## 💻 J'utilise

### Un exemple personnel commenté  ✔️

```js

//différentes routes
router.get('/', (req, res) => {
  const query = 'SELECT * FROM Carte';
  connection.query(query, (err, results) => {
    if (err) {
      err;
      res.status(500).send('Erreur lors de la récupération des types de plat');
    } else {
      res.json(results);
    }
  });
});

router.put('/:id', (req, res) => {
  const idTypesDePlat = req.params.id;
  const { name } = req.body;
  connection.query('UPDATE Carte = ? WHERE id_Type_de_plat = ?', [name, idTypesDePlat], err => {
    if (err) {
      res.status(500).send("Erreur lors de la modification d'un type de plat");
    } else {
      res.sendStatus(200);
    }
  });
});

router.delete('/:id', (req, res) => {
  const { id } = req.params;
  connection.query('DELETE FROM Carte WHERE id= ?', [id], err => {
    if (err) {
      res.status(500).send("Erreur lors de la suppression d'un type de plat");
    } else {
      res.status(200).json({
        status: 'success',
        deletedId: id
      });
    }
  });
});

```
### Utilisation dans un projet ✔️

[Boudu Toulouse](https://github.com/WildCodeSchool/tlse-0919-js-boudu)

Description :

### Utilisation en production si applicable❌ / ✔️

### Utilisation en environement professionnel ❌ / ✔️

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
