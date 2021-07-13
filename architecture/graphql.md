# GraphQL
> ❌ A travailler
> ✔️ Auto validation par l'étudiant
> 👌 Validation par le formateur


## 🎓 J'ai compris et je peux expliquer
- la différence entre REST et GraphQL ✔️
- les besoins auxquels répond GraphQL ✔️
- la définition d'un schéma ✔️
- Query ✔️
- Mutation ✔️
- Subscription ✔️


## 💻 J'utilise
### Un exemple personnel commenté ✔️
``` javascript
  async activateUser(
      _: void,
      data: { token: string }
    ): Promise<UserWithToken> {
      const token = data.token;
      const payload = decode(token, SECRET_KEY);

      let userAccount: IUser;
      try {
        // récupère le compte de l'utilisateur
        userAccount = await UserSchema.findOne({ email: payload.email });
      } catch (err) {
        throw new UnauthorizedError("Vous n'êtes pas connecté");
      }

      if (payload.password === userAccount.password) {
        // change son statut
        const activeUser = await UserSchema.findByIdAndUpdate(
          userAccount._id,
          { status: 'active' },
          { new: true }
        );

        // envoie les données de l'utilisateur et son token
        return { user: activeUser, token };
      } else {
        throw new UnauthorizedError("Vous n'êtes pas connecté.");
      }
    },
```
### Utilisation dans un projet ✔️
[lien github projet lood](https://github.com/mathildetho/lood/blob/authentification/apps/back/src/graphql/resolvers/user.resolver.ts)
Description : Création d'une application dans le même esprit que Tinder mais qui met en relation en fonction des goûts culinaires. Elle permet de trouver son âme soeur culinaire. Création d'une API GraphQL. Dans ce projet, je suis amené à créer des queries et mutations, pour l'authentification d'un utilisateur notamment. Par exemple, pour le login, avec les données envoyées via le front (email et mot de passe), nous allons d'abord vérifier qu'il existe en cherchant l'utilisateur dans le schéma grâce à son email (UserSchema.findOne({ email })). S'il n'existe pas, nous renvoyons une erreur, sinon, on continue et on vérifie que le mot de passe envoyé est egal à celui de la base de données en utilisant bcrypt. Si c'est le cas, on crée le token de l'utilisateur et on retourne côté front le token et les données de l'utilisateur connecté.

### Utilisation en production si applicable ✔️
[lien du projet Lamas](https://lamas.wns.wilders.dev)
Description : Projet réalisé durant l'alternance en équipe de 5 développeurs. Il s'agit d'une application pour les cours à distance. Le but ? Avoir plus d'interactions entre les élèves et professeurs. Comment ? Avec des partage d'émotions avec des emojis mais aussi l'interaction visuelle et textuelle. Nous avons utilisé l'API GraphQL pour les requêtes de lecture et d'écriture et socket.Io pour le temps réel. Nous aurions pu également utiliser à la place de socket.Io, les subscriptions de GraphQL qui utlisent le même principe avec les wbe sockets.

### Utilisation en environement professionnel ❌


## 🌐 J'utilise des ressources
### [Apollo Server](https://www.apollographql.com/docs/apollo-server/)
- Documentation sur l'implémentation du serveur GraphQL
### [Quêtes de la Wild Code School](https://odyssey.wildcodeschool.com/quests/1425)
- Présentation sur la façon d'appeller une API GraphQL et l'écriture de la partie serveur
### [Repository d'express-graphql](https://github.com/graphql/express-graphql)
- Documentation sur l'utilisation de GraphQL et Express


## 🚧 Je franchis les obstacles
### Point de blocage ✔️
Description : Lors d'une création de compte, l'objectif était d'envoyer un email d'activation du compte, lorsque l'utilisateur clique sur le lien, l'activation est validée et son statut change. N'ayant pas déjà travaillé sur ce sujet, j'ai dû faire mes recherches et modifier mon code.

Plan d'action : (à valider par le formateur)
- action 1 : recherche sur internet des solutions qui pourrait m'aider à activer un compte grâce à un lien dans un email
- action 2 : recherche sur mon projet d'entreprise sur l'envoi d'email avec lien (projet en REST API)
- action 3 : dans la base de données et les types, ajout d'une nouvelle donnée 'statut'. Si l'utilisateur n'a pas un statut actif, il ne pourra pas se logguer
- action 4 : lors de la création d'un utilisateur, le statut est en attente ('pending'). C'est à ce moment qu'on lui crée son token, on y stocke dans le payload son email et son mot de passe hashé. C'est grâce aux données stockées dans le payload que l'on va pouvoir activer le compte au clic. Dans l'email envoyé, un bouton a pour lien l'url avec en paramètre le token de l'utilisateur (`http://localhost:4200/inscription/confirmation/${token}`). 
- action 5 : lorsque l'utilisateur va cliquer sur le lien, il va être dirigé sur une page de confirmation, lorsque le statut est activé, l'utilisateur est redirigé vers la page de connexion. Pour activer ce statut, côté front, on lui envoies dans la mutation en variable le token qui est stocké dans les paramètres d'url. Côté back, on décode le token grâce à notre clé secrète. Si l'on retrouve l'utilisateur dans la base de donnée avec son email et que le mot de passe stocké en payload est équivalent à celui de la base de données, on va modifier le statut de l'utilisateur. Enfin, on envoie les données de l'utilisateur et son token.


## 📽️ J'en fais la démonstration ❌