# Tester son application

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- les tests unitaires ✔️
- les mocks ✔️
- les tests d'integration ✔️
- les tests de bout en bout (end to end) ✔️
- le TDD ✔️
- les tests par snapshot ✔️

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```javascript
const request = require("supertest");
const app = require("../app");
const connection = require("../connection");

// Voici un test qui porte le nom Test routes

describe("Test routes", () => {
  beforeEach((done) => connection.query("TRUNCATE bookmark", done));
  it('GET / sends "Hello World" as json', (done) => {
    request(app)
      .get("/")
      .expect(200)
      .expect("Content-Type", /json/)
      .then((response) => {
        const expected = { message: "Hello World!" };

        // On s'attends à ce que sur la route / avec le verbe GET,
        // un statut 200, un "Content-Type" qui soit /json/
        // { message: "Hello World!" } soit égal à la response du body

        expect(response.body).toEqual(expected);
        done();
      });
  });

  // Voici un test qui porte le nom POST /bookmarks - error (fields missing)

  it("POST /bookmarks - error (fields missing) ", (done) => {
    request(app)
      .post("/bookmarks")
      .send({})
      .expect(422)
      .expect("Content-Type", /json/)
      .then((response) => {
        const expected = { error: "required field(s) missing" };

        // On s'attends à ce que sur la route /bookmarks avec le verbe POST,
        // un statut 422, un "Content-Type" qui soit /json/
        // { error: "required field(s) missing" } soit égal à la response du body

        expect(response.body).toEqual(expected);
        done();
      });
  });

  it("POST /bookmarks - OK (fields provided) ", (done) => {
    request(app)
      .post("/bookmarks")
      .send({ url: "https://jestjs.io", title: "Jest" })
      .expect(201)
      .expect("Content-Type", /json/)
      .then((response) => {
        const expected = {
          id: expect.any(Number),
          url: "https://jestjs.io",
          title: "Jest",
        };
        expect(response.body).toEqual(expected);
        done();
      })
      .catch(done);
  });
});

describe("GET /bookmarks/:id", () => {
  const testBookmark = { url: "https://nodejs.org/", title: "Node.js" };
  beforeEach((done) =>
    connection.query("TRUNCATE bookmark", () =>
      connection.query("INSERT INTO bookmark SET ?", testBookmark, done)
    )
  );
  it("GET / bookmarks with a wrong id / error", (done) => {
    request(app)
      .get("/bookmarks/9")
      .expect(404)
      .expect("Content-Type", /json/)
      .then((response) => {
        const expected = { error: "can't find this bookmark" };
        expect(response.body).toEqual(expected);
        done();
      });
  });

  it("GET / bookmarks OK (correct id)", (done) => {
    request(app)
      .get("/bookmarks/1")
      .expect(200)
      .expect("Content-Type", /json/)
      .then((response) => {
        const expected = {
          id: expect.any(Number),
          url: "https://nodejs.org/",
          title: "Node.js",
        };
        expect(response.body).toEqual(expected);
        done();
      });
  });
});
```

### Utilisation dans un projet ❌

[lien github](...)

Description :

### Utilisation en production si applicable ❌

[lien du projet](...)

Description :

### Utilisation en environement professionnel ❌

Description :

## 🌐 J'utilise des ressources

### Titre

- lien
- description

## 🚧 Je franchis les obstacles

### Point de blocage ❌

Description:

Plan d'action : (à valider par le formateur)

- action 1 essayer de faire des tests sur notre projet ❌
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌
- J'ai fait une [présentation](...) ❌
