# Tester son application

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- les tests unitaires ❌ / ✔️
- les mocks ❌ / ✔️
- les tests d'integration ✔️
- les tests de bout en bout (end to end) ❌ / ✔️
- le TDD ❌ / ✔️
- les tests par snapshot ❌ / ✔️

## 💻 J'utilise

Jest

### Un exemple personnel commenté ✔️

```tsx
//tests d'intégration
describe('User resolvers', () => {
  let testClient;

  beforeEach(async () => {
    const connectionOptions = await getConnectionOptions();
    await createConnection({
      ...connectionOptions,
      dropSchema: true,
      entities: [
        User,
        UserSession,
        Article,
        Community,
        Diploma,
        Experience,
        ContentField,
        LikeArticle,
        CommentaireArticle,
      ],
      synchronize: true,
      logging: false,
    });

    const { expressServer } = await getExpressServer();

    testClient = createTestClient(expressServer);
  });

  afterEach(() => {
    const conn = getConnection();
    return conn.close();
  });

  describe('query me', () => {
    let user;

    beforeEach(async () => {
      user = User.create({
        pseudo: 'jesus',
        password: 'ilovedevil',
        email: 'jesus@god.com',
        bio: 'hell yeah',
      });
      await user.save();
    });

    describe('when user is not authenticated', () => {
      it('returns error', async () => {
        const response = await testClient.post('/graphql').send({
          query: `{
          me {
            pseudo
            userID
          }
        }
        `,
        });
        expect(response.text).toMatch('You are not authenticated.');
      });
    });

    describe('when user is authenticated', () => {
      it('returns user', async () => {
        const currentUserSession = UserSession.create({ user: user });
        await currentUserSession.save();

        const response = await testClient
          .post('/graphql')
          .set('Cookie', [`sessionId=${currentUserSession.uuid}`])
          .send({
            query: `{
              me {
                pseudo
              }
            }
          `,
          });

        expect(JSON.parse(response.text).data).toEqual({
          me: {
            pseudo: user.pseudo,
          },
        });
      });
    });
  });
});

```

### Utilisation dans un projet ✔️

[SkillzShare](https://github.com/WildCodeSchool/2020-11-wns-remote2-groupe5-projet)

### Utilisation en production si applicable ✔️

[SkillzShare](https://skillzshare.wns.wilders.dev/)

### Utilisation en environement professionnel ❌ / ✔️

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
