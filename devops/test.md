# Tester son application

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- les tests unitaires ✔️
- les mocks ❌
- les tests d'integration ✔️
- les tests de bout en bout (end to end) ❌
- le TDD ✔️
- les tests par snapshot ❌

## 💻 J'utilise

### Un exemple personnel commenté ✔️

const request = require("supertest");
const app = require("../app");
const connection = require("../connection");

describe("Test routes", () => {
beforeEach((done) => connection.query("TRUNCATE bookmark", done));
it('GET / sends "Hello World" as json', (done) => {
request(app)
.get("/")
.expect(200)
.expect("Content-Type", /json/)
.then((response) => {
const expected = { message: "Hello World!" };
expect(response.body).toEqual(expected);
done();
});
});

it("POST /bookmarks - error (fields missing) ", (done) => {
request(app)
.post("/bookmarks")
.send({})
.expect(422)
.expect("Content-Type", /json/)
.then((response) => {
const expected = { error: "required field(s) missing" };
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

### Utilisation dans un projet ❌

[lien github](...)

Description :

### Utilisation en production si applicable❌

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

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌
- J'ai fait une [présentation](...) ❌
