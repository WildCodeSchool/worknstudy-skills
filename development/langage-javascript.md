# Langage Javascript

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- les `structures` de base du langage / ✔️
- les normes `ecmascript` / ✔️
- l'utilisation de l'`asynchrone` ❌ 
- les spécifités du mot-clef `this` ❌ 

## 💻 Je code en Javascript

### Un exemple de code commenté ❌ / ✔️
 `2 exemples de Hooks permettant de sauvegarder une latitude et une longitude`
  const [geoLat, setGeoLat] = useState();
  const [geoLong, setGeoLong] = useState();
  
  
  `une fonction utilisant un module React permettant d'accéder aux informations de géolocalisation et qui sauvegarde la donnée dans le Hook associé`
  const geoloc = () => Geolocation.getCurrentPosition(info => { console.log(info.coords.latitude, info.coords.longitude), setGeoLat(info.coords.latitude),    setGeoLong(info.coords.longitude) });
  
  `un exemple de return (affichage) avec un bouton qui lance la fonction 'geoloc' lorsque l'on appuie dessus`
  return (
    ...
      <TouchableOpacity onPress={geoloc}>
        ...

### Utilisation dans un projet ✔️

[lien github] https://github.com/BrianLag/dreamiverse-front

Description : Projet de la Wild avec lecture et ajout de contenu vidéoludique

### J'ai utilisé ce langage en production  ✔️

[lien du projet] https://github.com/WildCodeSchool/reims-js-202003-pjt-trott-client

Description :  Projet Client de la wild

### J'ai utilisé ce langage en environement professionnel  ✔️

Description : Utilisation dans le cadre du Projet Client avec la Wild pour un prototype

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

