# Platform as a service

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- ce que c'est ✔️
- comment deployer une application sur une PaaS ✔️

## 💻 J'utilise

### Un exemple personnel commenté ✔️

Caddyfile de notre projet

skillzshare.wns.wilders.dev {
   reverse_proxy localhost:8000

   log {
     output file /var/log/caddy/demo.log
   }
}


staging.skillzshare.wns.wilders.dev {
   reverse_proxy localhost:8001

   log {
     output file /var/log/caddy/staging-demo.log
   }
}


ops.skillzshare.wns.wilders.dev {
   reverse_proxy /hooks/* localhost:9000

   log {
     output file /var/log/caddy/webhooks.log
   }
}


### Utilisation dans un projet ✔️

[SkillzShare](https://github.com/WildCodeSchool/2020-11-wns-remote2-groupe5-projet)


### Utilisation en production si applicable ✔️

[SkillzShare](https://skillzshare.wns.wilders.dev/)

### Utilisation en environement professionnel ❌ / ✔️


## 🌐 J'utilise des ressources

- [caddy](https://caddyserver.com/v2)
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
