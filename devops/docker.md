# Docker

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- la création d'une image docker ✔️
- l'éxécution d'un container ✔️
- l'orchestration de containers avec docker-compose ✔️


## 💻 J'utilise

### Un exemple personnel commenté ❌ / ✔️

```Dockerfile

FROM node:14.16-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . ./

```

docker-compose

```yml

version: '3'
services:
  db:
    image: postgres:13.2
    environment:
      - POSTGRES_PASSWORD=password
  api:
    build: .
    depends_on:
      - db
    environment:
      - TYPEORM_CONNECTION=postgres
      - TYPEORM_HOST=db
      - TYPEORM_PORT=5432
      - TYPEORM_DATABASE=postgres
      - TYPEORM_USERNAME=postgres
      - TYPEORM_PASSWORD=password
  web-client:
    build: ./web-client

```

### Utilisation dans un projet ✔️

[SkillzShare](https://github.com/WildCodeSchool/2020-11-wns-remote2-groupe5-projet)


Description : docker-compose de dev

```yml

version: '3'

services:
  api:
    command: npm run start:watch
    stdin_open: true
    volumes:
      - ./src:/app/src
      - ./public:/app/public
    ports:
      - ${API_PORT}:4000
    environment:
      - NODE_ENV=development
      - TYPEORM_LOGGING=true
      - TYPEORM_ENTITIES=dist/models/*.js
  web-client:
    command: npm run start
    stdin_open: true
    volumes:
      - ./web-client:/app
    ports:
      - ${WEB_CLIENT_PORT}:3000
    environment:
      - NODE_ENV=development
      - REACT_APP_API_BASE_URL=http://localhost:${API_PORT}


```

### Utilisation en production si applicable ✔️

[SkillzShare](https://skillzshare.wns.wilders.dev/)

Description : docker-compose de production

```yml

version: '3'

services:
  db:
    restart: always

  api:
    depends_on:
      db:
        condition: service_started
    command: sh -c "npm run build && npm run start"
    expose:
      - 4000
    restart: always
    volumes:
      - public:/app/public
    environment:
      - NODE_ENV=production

  web-client:
    depends_on:
      api:
        condition: service_started
    command: sh -c "npm run build"
    volumes:
      - web-client-build:/app/build
    environment:
      - NODE_ENV=production
      - REACT_APP_API_BASE_URL=/api

  nginx:
    depends_on:
      api:
        condition: service_started
      web-client:
        condition: service_started
    image: nginx:1.19.10
    restart: always
    ports:
      - ${GATEWAY_PORT}:80
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf
      - web-client-build:/web-client-build
      - public:/public

volumes:
  web-client-build:
  public:


```

### Utilisation en environement professionnel ❌ / ✔️

## 🌐 J'utilise des ressources

- [la dock](https://docs.docker.com/)
- [la dock - docker-compose](https://docs.docker.com/compose/)

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
