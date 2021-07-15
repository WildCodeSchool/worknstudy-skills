# Titre de la compétence

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- Comment développer en utilisant un système de *livereloading* (`nodemon` par exemple) ✔️
- La connexion de mon application à une base de données avec et sans ORM/ODM (avec `mongodb` puis `mongoose` par exemple) ✔️
- Le développement d'une API REST et GraphQL (avec les packages `express` et `graphql` par exemple)  ✔️
- *Bonus : la manipulation des fichiers système avec `fs` et l'utilisation des streams en NodeJS* ❌ / ✔️

## 💻 J'utilise

### Un exemple personnel commenté  ✔️

```ts

//un server express
export const getExpressServer = async (): Promise<{
  expressServer: Application;
  apolloServer: ApolloServer;
  graphQLSchema: GraphQLSchema;
}> => {
  const { apolloServer, graphQLSchema } = await getApolloServer();

  const expressServer = express()
    .use(cookieParser())
    .use(graphqlUploadExpress({ maxFileSize: 10000000, maxFiles: 10 }))
    .use('/public', express.static(path.join(__dirname, '..', 'public')));
  apolloServer.applyMiddleware({ app: expressServer });

  return { expressServer, apolloServer, graphQLSchema };
};

```

### Utilisation dans un projet  ✔️

[SkillzShare](https://github.com/WildCodeSchool/2020-11-wns-remote2-groupe5-projet)

Description :

### Utilisation en production si applicable ✔️

[SkillzShare](https://skillzshare.wns.wilders.dev/)

```ts

// connexion au back
const main = async () => {
  const connectionOptions = await getConnectionOptions();
  await createConnection({
    ...connectionOptions,
    synchronize: true,
    entities: ['dist/models/*.js'],
  });

  const { expressServer, apolloServer, graphQLSchema } =
    await getExpressServer();

  const server = createServer(expressServer);
  server.listen(4000, () => {
    console.log(
      `🚀 Server ready at http://localhost:4000${apolloServer.graphqlPath}`
    );
    new SubscriptionServer(
      {
        execute,
        subscribe,
        schema: graphQLSchema,
      },
      {
        server,
        path: apolloServer.graphqlPath,
      }
    );
  });
};

main();

```

Description : au sein de ma boite mais pas d'exemple sous la main

### Utilisation en environement professionnel ✔️

Description : architecture en package

## 🌐 J'utilise des ressources

### Titre

- [la doc](http://expressjs.com/fr/4x/api.html#res)
- la base

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
