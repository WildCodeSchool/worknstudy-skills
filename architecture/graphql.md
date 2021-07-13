# GraphQL

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- la différence entre REST et GraphQL ✔️
- les besoins auxquels répond GraphQL ✔️
- la définition d'un schéma
- Query ✔️
- Mutation ✔️
- Subscription ✔️

## 💻 J'utilise

GrapqhQL, en entreprise et à l'école

### Un exemple personnel commenté ✔️

```une query pour get 1 article en fonction de son ID

  @Query(() => Article)
  oneArticle(
    @Ctx() { user }: { user: User | null },
    @Arg('articleID') articleID: string
  ): Promise<Article> {
    if (!user) {
      throw Error('You are not authenticated.');
    }
    return Article.findOne(articleID, {
      relations: [
        'user',
        'likesArticle',
        'likesArticle.user',
        'contentFields',
        'commentairesArticle',
        'commentairesArticle.user',
        'community',
      ],
    }) as Promise<Article>;
  }

```

```une mutation pour supprimer la session de connexion

  @Mutation(() => User)
  async deleteSession(@Ctx() { user }: { user: User | null }): Promise<User> {
    if (!user) {
      throw Error('You are not authenticated.');
    }
    await getConnection()
      .createQueryBuilder()
      .delete()
      .from(UserSession)
      .where('userUserID = :id', { id: user.userID })
      .execute();

    return User.findOne(user.userID) as Promise<User>;
  }

```

```une subscription ppour s'abonner à la création de nouveaux commentaires relatifs à un 

  @Subscription({
    topics: 'NEW_COMMENT',
  })
  subscribeToNewComment(
    @Root() notificationPayload: newCommentNotificationPayload
  ): CommentaireArticle {
    return notificationPayload.payload;
  }

```


### Utilisation dans un projet ❌ / ✔️

[lien github](...)

Description :

### Utilisation en production si applicable ❌ / ✔️

[lien du projet](...)

Description :

### Utilisation en environement professionnel ❌ / ✔️

Développement de la partie front end de Dmitri, un projet pour un client avec l'entreprise

```typescript

```

## 🌐 J'utilise des ressources

[la doc graphql](https://graphql.org/)
[le playground graphql pour le debug généralement sur le localhost:4000 de tout projet graphql](http://localhost:4000/graphql)
[la doc apollo](https://www.apollographql.com/docs/react/get-started/)

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
