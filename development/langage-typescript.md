# TypeScript

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- l'intéret de TypeScript dans l'IDE ✔️
- les types de bases ✔️
- comment et pourquoi étendre une interface ✔️
- les classes et les decorators ❌ / ✔️

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```tsx
  //un handle change generique pour modifiier un state User
  
  const [user, setUser] = useState<User>(defaultUser);
  const onUserChange = <P extends keyof User>(prop: P, value: User[P]) => {
    setUser({ ...user, [prop]: value });
  };
  
```

### Utilisation dans un projet ✔️

[SkillzShare](https://github.com/WildCodeSchool/2020-11-wns-remote2-groupe5-projet)

### Utilisation en production si applicable ✔️

[SkillzShare](https://skillzshare.wns.wilders.dev/)

### Utilisation en environement professionnel ✔️

```ts
//exemples de types en unviers professionels

export type Experience = {
	id: string
	from: Date
	to?: Date
	title: string
	place?: string
	description?: string
	isValidate?: boolean
}

export type AuthFormData = Partial<(AuthFormTeacherData | AuthFormParentData | AuthFormStudentData)>

export type UpdateProfileTeacher = {
	lastName: string
  firstName: string
	location: GooglePlacesAutocompleteResponse
}

export type ExperienceForm = {
	isCurrentJob: boolean
	title: string
	fromDate: string
	toDate: string
	description: string
	school: School
	file?: File
}


```

## 🌐 J'utilise des ressources

- [le handbook typescript](https://www.typescriptlang.org/docs/handbook/intro.html)

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
