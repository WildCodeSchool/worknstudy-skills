# TypeScript

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- l'intéret de TypeScript dans l'IDE  ✔️
- les types de bases  ✔️
- comment et pourquoi étendre une interface  ✔️
- les classes et les decorators ❌ 

## 💻 J'utilise

### Un exemple personnel commenté ❌ / ✔️

```
type Callback = (req: Request, res: Response) => Promise<void>;
```
une fonction attendant 2 arguments req typé en Request et res typé en Response renvoyant une Promise

### Utilisation dans un projet ❌ / ✔️

[lien github](...)

Description :

### Utilisation en production si applicable❌ / ✔️
```
type WilderProps = {
  name: string;
  city: string;
  skills: TSkill[];
}

type SkillProps = {
  title: string;
  voteCount: number;
}

const Wilder = ({ name, city, skills }: WilderProps) => {
  return (
    <article className="card">
      <img src={blank_profile} alt="Jane Doe Profile" />
      <h3>{name}</h3>
      <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
        tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
        veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
        commodo consequat.
      </p>
      <h3>{city}</h3>
      <h4>Wild Skills</h4>
      <ul className="skills">
        {skills.map((skill: SkillProps) => (
          <Skill
            key={skill.title}
            title={skill.title}
            voteCount={skill.voteCount}
          />
        ))}
      </ul>
    </article>
  );
```
Description : wilder typé

### Utilisation en environement professionnel ❌ / ✔️

Description :

## 🌐 J'utilise des ressources

### Titre

- (la doc TS)[https://www.typescriptlang.org/docs/handbook/basic-types.html]
- voici la doc officielle TS très pratique pour n'importe quel questionnement sur typescript

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
