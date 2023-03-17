# Titre de la compétence

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- l'état (_state_) pour contrôler l'affichage d'un composant ✔️
- les composants enfants et les _props_ qu'on leur passe ✔️
- le déclenchement d'instructions en fonction des actions de l'utilisateur ✔️
- le déclenchement d'instructions en fonction de l'étape du cycle de vie du composant ou du changement de valeur de ses props ✔️
- l'usage d'un reducer (_useReducer_) pour gérer un état composé dans un composant
- l'état stocké dans un composant avec un _context provider_ et accessible dans ses descendants via `useContext` ❌

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```tsx
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

### Utilisation dans un projet ✔️

[SkillzShare](https://github.com/WildCodeSchool/2020-11-wns-remote2-groupe5-projet)

```tsx
//Description : 
export default function App(): JSX.Element {
  const { data, loading } = useQuery(CHECK_AUTH);
  return (
    <>
      {!loading && (
        <CurrentUserContext isAuthenticate={!!data}>
          <RootRouter />
        </CurrentUserContext>
      )}
    </>
  );
}

```

### Utilisation en production si applicable ✔️

[SkillzShare](https://skillzshare.wns.wilders.dev/)

### Utilisation en environement professionnel ✔️

```tsx
//Description : le context de la gestion d'annonces (fonctionnalité principale) de Dmitri

import React, { Dispatch, SetStateAction, useContext, useEffect, useState } from 'react'
import { GetAdsDocument, GetArchivedAdsDocument } from '../generated/hooks'
import {
  AdArchivedFragment, AdFragment, AnnounceWhereInput, Exact, GetAdsQuery, GetAdsQueryVariables,
  GetArchivedAdsQuery, GetArchivedAdsQueryVariables,
} from '../generated/types'
import { useAwaitableQuery } from '../hooks/useAwaitableQuery'
import { useCurrentUser } from './currentUserContext'

type paramsRefetch = keyof AnnounceWhereInput
type AdsContextType = {
  ads?: AdFragment[]
  archivedAds?: AdArchivedFragment[]
  refetchAds?: ()=> Promise<void>
  loadingAds?: boolean
  currentTab?: number
  setCurrentTab?: Dispatch<SetStateAction<number>>
}

const AdsContext = React.createContext<AdsContextType>({})

type MapTabToStateType = { [key in number]: paramsRefetch}
const mapTabToStateTeacher: MapTabToStateType = { 0: 'isPublished', 1: 'isValidated', 2: 'isFinished' }
const mapTabToStateLearner: MapTabToStateType = { 0: 'isPublished', 1: 'isValidated', 2: 'isMarked' }
const mapTabToState: { [key in number]: MapTabToStateType} = { 0: mapTabToStateLearner, 1: mapTabToStateTeacher }

export const AdsProvider: React.FC = ({ children }) => {
  const { currentUser } = useCurrentUser()

  const [ads, setAds] = useState<AdFragment[]>()
  const [archivedAds, setArchivedAds] = useState<AdArchivedFragment[]>()
  const [loadingAds, setLoadingAds] = useState<boolean>(false)
  const [currentTab, setCurrentTab] = useState<number>(0)

  const getAds = useAwaitableQuery<GetAdsQuery, GetAdsQueryVariables>(GetAdsDocument)
  const getArchivedAds = useAwaitableQuery<GetArchivedAdsQuery, GetArchivedAdsQueryVariables>(GetArchivedAdsDocument)
  const abortController = React.useRef<AbortController>()

  const fetchLearnerAds = async () => {
    const queryStateKey = mapTabToState[Number(currentUser?.isTeacher)][currentTab]

    if (abortController.current) abortController.current.abort()

    const controller = new window.AbortController()
    abortController.current = controller

    try {
      setLoadingAds(true)
      const res = await getAds({ variables: {
        condition: {
          [currentUser?.isStudent ? 'student' : 'parent']: { id: currentUser?.id },
          [queryStateKey]: true,
        },
      },
                                 fetchPolicy: 'no-cache',
                                 context: {
                                   fetchOptions: {
                                     signal: controller.signal,
                                   },
                                 },
      })
      if (currentTab === 2) {
        const resArchived = await getArchivedAds({ variables: {
          condition: {
            [currentUser?.isStudent ? 'student' : 'parent']: { id: currentUser?.id },
            isArchived: true,
          },
        },
                                                   fetchPolicy: 'no-cache',
        })
        setArchivedAds(resArchived.data?.allAnnounces!)
      }
      if (!controller.signal.aborted)
        setAds(res.data?.allAnnounces!)

      setLoadingAds(false)
    } catch (err) {
      console.log(err)
    }
  }

  const fetchTeacherAds = async () => {
    try {
      setLoadingAds(true)
      if (currentTab === 0) {
        const res = await getAds({ variables: {
          condition: {
            [mapTabToState[Number(currentUser?.isTeacher)][currentTab]]: true,
            candidates_some: { id: currentUser?.id },
          },
        },
                                   fetchPolicy: 'no-cache',
        })
        setAds(res.data?.allAnnounces!)
        setLoadingAds(false)
      } else {
        if (currentTab === 2) {
          const resArchived = await getArchivedAds({ variables: {
            condition: {
              isArchived: true,
            },
          },
                                                     fetchPolicy: 'no-cache',
          })
          setArchivedAds(resArchived.data?.allAnnounces!)
        }
        const res = await getAds({ variables: {
          condition: {
            [mapTabToState[Number(currentUser?.isTeacher)][currentTab]]: true,
          },
        },
                                   fetchPolicy: 'no-cache',
        })
        setAds(res.data?.allAnnounces!)
        setLoadingAds(false)
      }
    } catch (err) {
      console.log(err)
    }
  }

  useEffect(() => {
    const getAddsAsync = async () => {
      if (currentUser?.isTeacher)
        await fetchTeacherAds()
      else
        await fetchLearnerAds()
    }
    getAddsAsync()
  }, [currentTab])

  return (
    <AdsContext.Provider
      value={{
        ads,
        archivedAds,
        refetchAds: currentUser?.isTeacher ? fetchTeacherAds : fetchLearnerAds,
        loadingAds,
        currentTab,
        setCurrentTab,
      }}
    >
      {children}
    </AdsContext.Provider>
  )
}

export const useAds = () => {
  const ctx = useContext(AdsContext)
  return ctx
}

```
## 🌐 J'utilise des ressources

### Titre

- [la doc react](https://reactjs.org/)
- [le handbook typescript](https://www.typescriptlang.org/docs/handbook/intro.html)
- [react router pour la navigation](https://reactrouter.com/)
- [chakra-ui pour le style](https://chakra-ui.com/docs/getting-started)

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
