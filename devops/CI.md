# Integration continue
> ❌ A travailler
> ✔️ Auto validation par l'étudiant
> 👌 Validation par le formateur


## 🎓 J'ai compris et je peux expliquer
- les enjeux de l'integration continue ✔️
- la mise en place d'une github action ✔️


## 💻 J'utilise
### Un exemple personnel commenté ✔️
tests automatisés sur GitHub
```yml
name: Automated browser tests
on: [push,pull_request]

jobs:
  tests-backend:
    runs-on: ubuntu-latest
    steps:    
    # 1: setup node
      - name: Setup Node.js
        uses: actions/setup-node@v1
        with:
          node-version: 13

      # 2: Checkout repository in the CWD
      - name: Checkout repository
        uses: actions/checkout@v2

      # 3: install NPM dependencies
      - name: Install dependencies
        run: cd backend && npm ci

      # 4: Run jest test
      - name : Launch jest test
        run:  cd backend && npm run test:ci
        env: 
          MONGODB_URI_TESTING: ${{ secrets.MONGODB_URI_TESTING }}
          JWT_SECRET: ${{ secrets.JWT_SECRET }}


      # 5: Run lint test
      - name: Launch lint test
        run: cd backend && npm run lint
```

### Utilisation dans un projet ✔️
### Utilisation en production si applicable ✔️
[lien github du projet Lamas](https://github.com/WildCodeSchool/wns-2020-11-remote-1-lamas)
[lien du projet Lamas](https://lamas.wns.wilders.dev)
Description : utilisation d'un worklflow de tests automatisés back et frontend lors des push et des pull requests sur GitHub grâce aux GitHub Actions.

### Utilisation en environement professionnel ✔️
Description : tests automatisés back et front sur GitHub via circleCI.


## 🌐 J'utilise des ressources
### [CircleCi](https://circleci.com)
- documentation circleci
### [GitHub Actions](https://docs.github.com/en/actions)
- documentation GitHub Actions


## 🚧 Je franchis les obstacles
### Point de blocage ❌


## 📽️ J'en fais la démonstration ✔️
- J'ai ecrit une [fiche](https://docs.google.com/document/d/1FGA0tgKbsh0ykeOZ-uPFGOk2otyqaA5-QbALug4mSho/edit?usp=sharing)
