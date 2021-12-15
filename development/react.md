# Titre de la compétence

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- l'état (_state_) pour contrôler l'affichage d'un composant ✔️
- les composants enfants et les _props_ qu'on leur passe ✔️
- le déclenchement d'instructions en fonction des actions de l'utilisateur ✔️
- le déclenchement d'instructions en fonction de l'étape du cycle de vie du composant ou du changement de valeur de ses props ✔️
- l'usage d'un reducer (_useReducer_) pour gérer un état composé dans un composant ✔️
- l'état stocké dans un composant avec un _context provider_ et accessible dans ses descendants via `useContext` ✔️

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```javascript

/* eslint-disable no-nested-ternary */
import React, { useContext, useEffect, useState } from 'react';
import './CampaignDetails.scss';
import { FaMicrophone } from 'react-icons/fa';
import { BiExport } from 'react-icons/bi';
import { RiFileEditLine } from 'react-icons/ri';
import { useHistory } from 'react-router-dom';

import moment from 'moment';
import 'moment/locale/fr';
import API from '../../services/API';
import { UserContext } from '../../context/UserContext';
import CampaignDetailsChart from './CampaignDetailsChart';

// Cette fonction prends en apramètre des props

const CampaignDetail = (props) => {
  moment.locale('fr');

  const { userDetails, setUserDetails } = useContext(UserContext);
  const { match } = props;
  const history = useHistory();

  // Ici on initialise 3 states

  const [currentCampaign, setCurrentCampaign, setLoggedIn] = useState({
    id: 0,
    id_client_user: 0,
    name: '',
    text_message: '',
    vocal_message_file_url: '',
    date: '',
    sending_status: 0,
    lam_campaign_id: 0,
    count: 0,
    call_success_count: 0,
    call_failed_count: 0,
    call_ignored_count: 0,
  });
  const [campaignContacts, setCampaignContacts] = useState();
  const [winRate, setWinRate] = useState(0);

  // Ce useEffect a comme tableau de dépendance cuurentCampaign

  useEffect(() => {
    setWinRate(currentCampaign.call_success_count / currentCampaign.count);
  }, [currentCampaign]);

  // On fait un Get vers le back en précisant des id spécifiques en params dans l'URL

  useEffect(() => {
    API.get(`/users/${userDetails.id}/campaigns/${match.params.campaign_id}`)
      .then((res) => {
        setCurrentCampaign(res.data);
      })

      // history.push('/signin') permet de rediriger le user vers le path /signin

      .catch((err) => {
        if (err.response.status === 401) {
          setLoggedIn(false);
          setUserDetails({});
          history.push('/signin');
        }
      });

  // Idem :on fait un Get vers le back en précisant des id spécifiques en params dans l'URL


    API.get(
      `/users/${userDetails.id}/campaigns/${match.params.campaign_id}/contacts`
    )
      .then((res2) => {
        setCampaignContacts(res2.data.contacts);
      })
      .catch((err) => {
        if (err.response.status === 401) {
          setLoggedIn(false);
          setUserDetails({});
          history.push('/signin');
        }
      });
  }, []);
```

### Utilisation dans un projet ✔️

[lien github](https://github.com/WildCodeSchool/lyon-js-sept2020-p3-lafrica-front-office)

Description : projet 3 de la wild - promo sept 2020

### Utilisation en production si applicable❌ / ✔️

[lien github](https://github.com/WildCodeSchool/lyon-js-sept2020-p3-lafrica-front-office)

Description : projet 3 de la wild - promo sept 2020

### Utilisation en environement professionnel ❌ / ✔️

Description : projet 3 de la wild - promo sept 2020

## 🌐 J'utilise des ressources

### Titre

- lien
- description

## 🚧 Je franchis les obstacles

### Point de blocage ❌

Description: cycle de vie à approfondir

Plan d'action : (à valider par le formateur)

- action 1 cycle de vie à approfondir ❌
- action 2 Terminer la quête sur useReducer ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌
- J'ai fait une [présentation](...) ❌
