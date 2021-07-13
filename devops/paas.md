# Platform as a service
> ❌ A travailler
> ✔️ Auto validation par l'étudiant
> 👌 Validation par le formateur


## 🎓 J'ai compris et je peux expliquer
- ce que c'est ✔️
- comment deployer une application sur une PaaS ✔️


## 💻 J'utilise
### Un exemple personnel commenté ✔️
```sh
# Déployer une version de l'application
elif [ $user_input == 2 ]
    then
        echo " "
        printf "\e[1;34mVersions disponibles sur le gcloud container registry:\e[0m\n"
        gcloud container images list-tags eu.gcr.io/hellia-1539768848684/hellia-app-front
        echo ""
        printf "\nJarvis - Quel version / tags voulez-vous deployer ?\n"
        read user_version
        printf "\n🌟  Déploiement de la version \e[1;34m$user_version\e[0m de l'application 🌟 \n"
        correct_answer=true
        # Déploie
        ./kubernetes/version_deploy.sh $user_version
```

### Utilisation dans un projet ✔️
### Utilisation en production si applicable ✔️
### Utilisation en environement professionnel ✔️
[lien du projet Hellia](https://app.hellia.fr/)
Description : Utilisation de GoogleCloud Platform pour développer et gérer notre API (App engine, Compute Engine, Storage et SQL).


## 🌐 J'utilise des ressources
### [Google Cloud](https://cloud.google.com/docs)
- documentation Google Cloud


## 🚧 Je franchis les obstacles
### Point de blocage ❌ 


## 📽️ J'en fais la démonstration ❌
