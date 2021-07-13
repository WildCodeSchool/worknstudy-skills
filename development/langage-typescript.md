# TypeScript
> ❌ A travailler
> ✔️ Auto validation par l'étudiant
> 👌 Validation par le formateur


## 🎓 J'ai compris et je peux expliquer
- l'intéret de TypeScript dans l'IDE ✔️
- les types de bases ✔️
- comment et pourquoi étendre une interface ✔️
- les classes et les decorators ❌


## 💻 J'utilise
### Un exemple personnel commenté ✔️
```javascript
// interface indiquant les types de chaque props
interface InscriptionConnexionLayoutProps {
  title: string;
  children: React.ReactNode;
  img?: boolean;
  goHome?: boolean;
}
```

### Utilisation dans un projet ✔️
[lien github projet lood](https://github.com/mathildetho/lood/blob/authentification/apps/front-client/src/app/components/DataDisplay/Icon/Icon.component.tsx)
Description : utilisation de typeScript sur mon projet personnel côté front et back.

### Utilisation en production si applicable ✔️
### Utilisation en environement professionnel ✔️
[lien du projet Hellia](https://app.hellia.fr/)
Description : Mise en place progressive de TypeScript sur tous les composants front de l'application
```javascript
export type Adresse = {
  numRue: string;
  nomRue: string;
  ville: string;
  codePostal: string;
  pays: string;
};

export type Proposition = {
  component: ReactNode;
  onClick: () => void;
};

export interface AdresseInputProps {
  required?: boolean;
  className?: string;
  adresse?: Adresse;
  handleChange: (adresse: Adresse) => void;
  additionalPropositions?: Proposition[];
  style?: Record<string, unknown>;
  name: string;
  isValid: boolean;
  error?: string;
  erreurValidation?:boolean;
  index?: string;
}

interface AdresseInputState {
  propositions: Record<string, Record<string, unknown>>;
  adresse: Adresse;
  open: boolean;
  isfocused: boolean;
  villesCorrespondantsAuCP: string[];
  villeCPOnSearch: boolean
}

class AdresseInput extends Component<AdresseInputProps, AdresseInputState> {}
```


## 🌐 J'utilise des ressources
### [TypeScript](https://www.typescriptlang.org)
- Documentation de Typescript
### [Quêtes de la Wild Code School](https://odyssey.wildcodeschool.com/quests/1412)
- Présentation de Typescript
### [Je suis un dev](https://www.jesuisundev.com/comprendre-typescript-en-5-minutes/)
- Article sur Typescript


## 🚧 Je franchis les obstacles
### Point de blocage ❌ 


## 📽️ J'en fais la démonstration ❌
