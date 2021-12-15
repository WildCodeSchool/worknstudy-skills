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

```bash

# Entête correcte pour un script Bash.

#!/bin/bash

# On run de manière interractive l'image ayan le nom dev, les ports de docker spont 8080, 80 et 443,
# Ils sont respectivement exposés aux ports 8080, 80, 443 de ma machine

docker run -it --name dev -p 8080:8080 -p 80:80 -p 443:443 \

             # Ici plusieurs volumes sont montés, notamment pour permettre la persistance de données

            -v dev_data:/NNvision/media_root \
            -v dev_db_12:/var/lib/postgresql/12/main \
            -v /home/cedric/PycharmProjects/django:/NNvision/django \
            -v /backup_local:/backup \
            -v dev_cron:/var/spool/cron/crontabs --rm dev:latest bash


```

### Utilisation dans un projet ✔️

[lien github](https://github.com/Protecia/django)

Description : stage en alternance

### Utilisation en production si applicable ✔️

[lien github](https://github.com/Protecia/django)

Description : stage en alternance

### Utilisation en environement professionnel ✔️

[lien github](https://github.com/Protecia/django)

Description : stage en alternance

## 🌐 J'utilise des ressources

### Titre

- lien
- description

## 🚧 Je franchis les obstacles

### Point de blocage ❌

Description: différence entre image et conteneur par ex

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌
- J'ai fait une [présentation](...) ❌
