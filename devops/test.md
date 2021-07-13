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
- les tests par snapshot ❌


## 💻 J'utilise
### Un exemple personnel commenté ✔️
test unitaire pour une fonction
``` javascript
describe('dateDebutDeclarationPaiement', () => {
  test('il n\'y a pas de précédente déclaration lié au contrat en cours, renvoie la date de début du contrat en cours', () => {
    let contratEnCours = {dateDebut: new Date('2021-04-29')};
    let derniereDeclaration = null;
    expect(dateDebutDeclarationPaiement(contratEnCours, derniereDeclaration)).toStrictEqual(contratEnCours.dateDebut)
  })
  test('une déclaration liée au contrat existe, on renvoie la date j+1 de cette déclaration', () => {
    let contratEnCours = {dateDebut: new Date('2021-04-29')};
    let derniereDeclaration = {dateFin: new Date('2021-05-31')};
    expect(dateDebutDeclarationPaiement(contratEnCours, derniereDeclaration)).toStrictEqual(moment(new Date('2021-06-01')).format())
  })
})
```

### Utilisation dans un projet ✔️
### Utilisation en production si applicable ✔️
[lien github du projet Lamas](https://github.com/WildCodeSchool/wns-2020-11-remote-1-lamas)
[lien du projet Lamas](https://lamas.wns.wilders.dev)
Description : Projet réalisé durant l'alternance en équipe de 5 développeurs. Il s'agit d'une application pour les cours à distance. Le but ? Avoir plus d'interactions entre les élèves et professeurs. Comment ? Avec des partage d'émotions avec des emojis mais aussi l'interaction visuelle et textuelle.

### Utilisation en environement professionnel ✔️
Description : Nous utilisons différents types de test dans l'entreprise, des tests unitaires en front et en back, des tests d'intégration et des tests e2e pour vérifier nos parcours utilisateurs tout en y respectant les scénarios juridiques.


## 🌐 J'utilise des ressources
### [Cypress](https://www.cypress.io)
- Documentation Cypress
### [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)
- Documentation React Testing Library
### [Jest](https://jestjs.io/docs/getting-started)
- Documentation Jest


## 🚧 Je franchis les obstacles
### Point de blocage ✔️
Description: Sur le test fonctionnel concernant le quittancement, nous devions vérifier, selon la valeur versée et le total à verser dans le mois, étaient les mêmes. Pour chaque test, nous faisons une déclaration sur 1 mois complet. Pour une quittance, les valeurs doivent être les mêmes, pour le reçu, la valeur versée doit être inférieure à celle souhaitée et pour un impayé, il ne doit pas y avoir de versement. Le blocage était au niveau de la valeur à indiquer selon le montant total du mois que nous n'avons pas sur notre base. Selon ce montant, le texte du bouton ne sera pas le même.
Sur l'application, le texte est de cette forme : "120 €" et "/ 200 €". Pour récupérer chaque montant il fallait donc les découper.

Plan d'action : (à valider par le formateur)
- action 1 : afin de récupérer les montants, il a fallu récupérer la className de l'élément les incluants et d'y récupérer le texte 
``` cy.get(".declaration-form__total-versements-number").invoke('text')```
- action 2 : après avoir récupérer ce texte nous devions récupérer d'un côté le total des versements et de l'autre le total à payer pour le mois
``` const totalVersements = text.split(' €')[0] ```
Pour le total du mois, il fallait être davantage précis et prendre une nouvelle className puis son montant
``` const total = text.slice(2,-2) ```
- action 3 : à partir du moment ou on a ces 2 valeurs on va pouvoir les comparer et vérifier selon celles-ci que le texte du bouton est le bon et cliquer dessus pour passer à la suite.

Code complet :
```javascript
cy.get(".declaration-form__total-versements-number").invoke('text').then((text) => {
            const totalVersements = text.split(' €')[0]
            cy.get(".declaration-form__total-versements").invoke('text').then((text) => {
                const total = text.slice(2,-2)
                // quittance
                if (Number(totalVersements) === Number(total)) {
                    cy.contains("Envoyer la quittance").click();
                    cy.intercept('POST', '/quittance')
                    cy.contains("Déclaration").should('exist')
                    recapitulatifVersements(values, 'quittance');
                } else if (Number(totalVersements) < Number(total)) {
                    // reçu
                    cy.contains("Envoyer le reçu").click();
                    cy.intercept('POST', '/quittance')
                    cy.contains("Déclaration").should('exist')
                    recapitulatifVersements(values, 'reçu');
                } else {
                    // trop perçu
                    cy.get('.form__info').should('exist')
                }
            })
        })
```


## 📽️ J'en fais la démonstration ✔️
- J'ai fait une [fiche](https://docs.google.com/document/d/1iQQsqCzbM-itLMkWJcr5-4-OBCHSxFkml1r0_QSmdcU/edit?usp=sharing)
