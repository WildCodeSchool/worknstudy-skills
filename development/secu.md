# Sécurité dans le développement Web
> ❌ A travailler
> ✔️ Auto validation par l'étudiant
> 👌 Validation par le formateur


## 🎓 J'ai compris et je peux expliquer
- Le rôle de l'OWASP ✔️
- Les injections SQL ✔️
- XSS ✔️
- CRSF ✔️


## 💻 J'utilise
### Un exemple personnel commenté ✔️
```javascript
// middleware qui vérifie que le token existe avant de passer à la suite et envoyer une donnée
const verifyToken = (token: string): Itoken | null => {
  // vérifie que la string est bien un token
  if (validator.isJWT(token)) {
    // vérifie que le token est valide grâce à une clé secrète
    return jwt.verify(token, jwtsecret) as Itoken;
  }
  return null;
};
```

### Utilisation dans un projet ✔️
### Utilisation en production si applicable ✔️
[lien github du projet Lamas](https://github.com/WildCodeSchool/wns-2020-11-remote-1-lamas)
[lien du projet Lamas](https://lamas.wns.wilders.dev)
Description : utilisation de bcrypt et jwt pour sécuriser l'accès aux données d'un compte

### Utilisation en environement professionnel ✔️
Description :
- back : utilisation de bcrypt et jwt pour sécuriser l'accès aux données d'un compte. Le middleware de vérification qu'un utilisateur est connecté est présent à chaque début de requêtes où les données sont sensibles et qu'il nécessite une authentification.
- front : utilisation de yup pour vérifier les données rentrées dans un formulaire (schema validation)


## 🌐 J'utilise des ressources
### [Yup](https://github.com/jquense/yup)
- documentation yup
### [dev.to](https://dev.to/eidorianavi/authentication-and-jwt-in-node-js-4i13)
- Article sur bcrypt et jwt dans Node


## 🚧 Je franchis les obstacles
### Point de blocage ❌ 


## 📽️ J'en fais la démonstration ❌ 
