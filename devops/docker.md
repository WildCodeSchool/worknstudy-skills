# Docker
> ❌ A travailler
> ✔️ Auto validation par l'étudiant
> 👌 Validation par le formateur


## 🎓 J'ai compris et je peux expliquer
- la création d'une image docker ✔️
- l'éxécution d'un container ✔️
- l'orchestration de containers avec docker-compose ✔️


## 💻 J'utilise
### Un exemple personnel commenté ✔️
DockerFile pour créer l'image back du projet lamas
```javascript 
FROM node:14-alpine
RUN mkdir /app
WORKDIR /app
COPY package.json package.json
RUN npm i
COPY tsconfig.json tsconfig.json
COPY .eslintrc .eslintrc
COPY .prettierrc .prettierrc
COPY ./src ./src
COPY ./public ./public
CMD npm run fix:lint && npm run start
```

### Utilisation dans un projet ✔️ et Utilisation en production si applicable ✔️
[lien github du projet Lamas](https://github.com/WildCodeSchool/wns-2020-11-remote-1-lamas)
[lien du projet Lamas](https://lamas.wns.wilders.dev)
Description : Projet réalisé durant l'alternance en équipe de 5 développeurs. Il s'agit d'une application pour les cours à distance. Le but ? Avoir plus d'interactions entre les élèves et professeurs. Comment ? Avec des partage d'émotions avec des emojis mais aussi l'interaction visuelle et textuelle.

### Utilisation en environement professionnel ✔️
Description : Pour mettre en production l'application Hellia, nous utilisons des fichiers DockerFile et Docker-Compose ainsi que kubernetes dans nos scripts de déploiement pour envoyer les images sur Google Gloud. On peut choisir grâce à des tags, la version de l'application à mettre en ligne.


## 🌐 J'utilise des ressources
### [Docker](https://www.docker.com)
- Documentation Docker
### [Quête de la Wild Code School](https://odyssey.wildcodeschool.com/quests/1512)
- Présentation de l'approche DevOps, l'intégration continue, le déploiement continu et Docker


## 🚧 Je franchis les obstacles
### Point de blocage ❌ 


## 📽️ J'en fais la démonstration ✔️
- J'ai fait une [fiche](https://docs.google.com/document/d/1N4WdBvEKm8s9ftN2uqB_HMTNH8o7xpVOluJ_rs1nhDw/edit?usp=sharing)
