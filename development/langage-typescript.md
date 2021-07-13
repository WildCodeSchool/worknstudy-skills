# TypeScript

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- l'intéret de TypeScript dans l'IDE ✔️
- les types de bases ✔️
- comment et pourquoi étendre une interface ✔️
- les classes et les decorators ❌ / ✔️

## 💻 J'utilise

### Un exemple personnel commenté ❌ / ✔️

```ts
//mapping sur une enum pour rattacher un objet a une variant pour avoir différentes tailles d'avatar et responsives
export enum AvatarVariants {
  Small = 'small',
  Medium = 'medium',
  Big = 'big',
}

export interface ISizes {
  base: string;
  sm: string;
  md: string;
  lg: string;
  xl: string;
}

export const avatarSizeMap: Record<AvatarVariants, ISizes | undefined> = {
  [AvatarVariants.Small]: {
    base: '30px',
    sm: '30px',
    md: '34px',
    lg: '36px',
    xl: '38px',
  },
  [AvatarVariants.Medium]: {
    base: '36px',
    sm: '36px',
    md: '38px',
    lg: '42px',
    xl: '44px',
  },
  [AvatarVariants.Big]: {
    base: '50px',
    sm: '60px',
    md: '64px',
    lg: '70px',
    xl: '70px',
  },
};

type AvatarCustomProps = {
  variant: 'small' | 'medium' | 'big';
  avatar: string | null;
};

const AvatarCustom = (props: AvatarCustomProps) => {
  const { avatar, variant } = props;

  return (
    <Avatar
      src={
        avatar === null
          ? undefined
          : document.location.origin + '/public/media/avatars/' + avatar
      }
      w={{
        base: avatarSizeMap[variant as AvatarVariants]?.base,
        sm: avatarSizeMap[variant as AvatarVariants]?.sm,
        md: avatarSizeMap[variant as AvatarVariants]?.md,
        lg: avatarSizeMap[variant as AvatarVariants]?.lg,
        xl: avatarSizeMap[variant as AvatarVariants]?.xl,
      }}
      h={{
        base: avatarSizeMap[variant as AvatarVariants]?.base,
        sm: avatarSizeMap[variant as AvatarVariants]?.sm,
        md: avatarSizeMap[variant as AvatarVariants]?.md,
        lg: avatarSizeMap[variant as AvatarVariants]?.lg,
        xl: avatarSizeMap[variant as AvatarVariants]?.xl,
      }}
    />
  );
};

export default AvatarCustom;


```

### Utilisation dans un projet ❌ / ✔️

[SkillzShare](https://github.com/WildCodeSchool/2020-11-wns-remote2-groupe5-projet)

### Utilisation en production si applicable❌ / ✔️

[SkillzShare](https://skillzshare.wns.wilders.dev/)

### Utilisation en environement professionnel ❌ / ✔️

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
