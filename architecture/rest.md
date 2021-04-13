# REST API

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- les verbes HTTP ✔️
- les statuts HTTP ✔️
- les endpoints ❌
- CORS ❌
- la nomenclature recommandée pour les routes ❌ ✔️

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```
const campaignsRouter = require('express').Router();

const asyncHandler = require('express-async-handler');
const campaignsController = require('../controllers/campaigns');
const handleTextUpload = require('../middlewares/handleTextUpload');
const handleUserConfirmed = require('../middlewares/handleUserConfirmed');

campaignsRouter.get(
  '/downloadaudio',
  asyncHandler(campaignsController.downloadAudio)
);

campaignsRouter.get('/video', asyncHandler(campaignsController.video));

campaignsRouter.get('/', asyncHandler(campaignsController.getCollection));
campaignsRouter.get('/audio', asyncHandler(campaignsController.playAudio));
campaignsRouter.get(
  '/:campaignId',
  asyncHandler(campaignsController.getOneCampaign)
);

campaignsRouter.post(
  '/',
  handleUserConfirmed,
  asyncHandler(campaignsController.createCampaignId)
);
campaignsRouter.post(
  '/uploadtext',
  handleTextUpload,
  asyncHandler(campaignsController.readText)
);

campaignsRouter.post('/TTS', asyncHandler(campaignsController.vocalization));

campaignsRouter.put(
  '/:campaignId',
  asyncHandler(campaignsController.updateCampaign)
);

campaignsRouter.put(
  '/:campaignId/stop',
  asyncHandler(campaignsController.stopCampaign)
);

campaignsRouter.delete(
  '/:campaignId',
  asyncHandler(campaignsController.deleteCampaign)
);
```

module.exports = campaignsRouter;

### Utilisation dans un projet ✔️

[lien du projet](https://github.com/WildCodeSchool/lyon-js-sept2020-p3-lafrica-api)

Description : projet 3 de la wild promo sept 2020

### Utilisation en production si applicable ✔️

[lien du projet](https://github.com/WildCodeSchool/lyon-js-sept2020-p3-lafrica-api)

Description : projet 3 de la wild promo sept 2020

### Utilisation en environement professionnel ✔️

Description : projet 3 de la wild promo sept 2020

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
