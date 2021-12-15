# Integration continue

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- les enjeux de l'integration continue ✔️
- la mise en place d'une github action ✔️

## 💻 J'utilise

### Un exemple personnel commenté

# /etc/Caddyfile

GNU nano 4.8 Caddyfile

# The Caddyfile is an easy way to configure your Caddy web server.

#

# Unless the file starts with a global options block, the first

# uncommented line is always the address of your site.

#

# To use your own domain name (with automatic HTTPS), first make

# sure your domain's A/AAAA DNS records are properly pointed to

# this machine's public IP, then replace ":80" below with your

# domain name.

```bash

# version fonctionnelle de l'application à l'adresse https://warscode.wns.wilders.dev

warscode.wns.wilders.dev {

        # Reverse proxy ur le port 8000

        reverse_proxy localhost:8000

        # des logs sont accesibles sur /var/log/caddy/production.log

        log {
                output file /var/log/caddy/production.log
        }

}


staging.warscode.wns.wilders.dev {
        reverse_proxy localhost:8001

        log {
                output file /var/log/caddy/staging.log
        }
}

ops.warscode.wns.wilders.dev {
        reverse_proxy localhost:9000

        log {
                output file /var/log/caddy/ops.log
        }
}

```

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
