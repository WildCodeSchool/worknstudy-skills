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
module.exports.exportContacts = async (req, res) => {
  const campaignId = parseInt(req.campaign_id, 10);
  // eslint-disable-next-line no-unused-vars
  const [total, data] = await findContactsForCampaign(campaignId);
  if (data) {
    const workbook = new Excel.Workbook();

    const contactsFileName = Math.random()
      .toString(36)
      .replace(/[^a-z]+/g, "")
      .substring(0, 5);
    const worksheet = workbook.addWorksheet("Contacts");
    worksheet.columns = [
      { header: "lastname", key: "lastname" },
      { header: "firstname", key: "firstname" },
      { header: "phone_number", key: "phone_number" },
    ];
    worksheet.columns.forEach((column) => {
      // eslint-disable-next-line no-param-reassign
      column.width = column.header.length < 12 ? 12 : column.header.length;
    });
    worksheet.getRow(1).font = { bold: true };
    data.forEach((e) => {
      worksheet.addRow({
        ...e,
      });
    });
    const pathFile = path.join(
      `${__dirname}/../file-storage/private/${contactsFileName}.xlsx`
    );
    await workbook.xlsx.writeFile(pathFile);
    return res.status(200).download(pathFile);
  }
  return res.status(400).send(`Impossible d'afficher les contacts`);
};
```

### Utilisation dans un projet ✔️

[lien github](https://github.com/WildCodeSchool/lyon-js-sept2020-p3-lafrica-api)

Description : projet 3 de la wild promo sept 2020

### J'ai utilisé ce langage en production ✔️

[lien du projet](https://github.com/WildCodeSchool/lyon-js-sept2020-p3-lafrica-api)

Description : projet 3 de la wild promo sept 2020

### J'ai utilisé ce langage en environement professionnel ✔️

Description : projet 3 de la wild promo sept 2020

## 🌐 J'utilise des ressources

### Titre

- lien
- description

## 🚧 Je franchis les obstacles

### Point de blocage ❌

Description: l'asynchronisme, hooks et useEffect

Plan d'action : (à valider par le formateur)

- action 1 faire un custom hook ✔️
- action 2 approfondir l'asynchronisme et le useEffect ❌ 
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌
- J'ai fait une [présentation](...) ❌
