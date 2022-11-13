# Unboared game (React Demo)
![node](https://img.shields.io/badge/node-16.16.0-brightgreen)
![npm](https://img.shields.io/badge/npm-8.16.0-blue)
[![unboared](https://img.shields.io/badge/unboared-0.1.1-%23FF2453)](https://bit.cloud/unboared/native/lib?version=0.1.1)

## Ce que contient ce template

Une démo de jeu simple utilisant la technologie Unboared. 

Plus précisement:
- la déclaration d'un jeu *Unboared* avec deux sous applications:
  - l'application côté ***screen***
  - l'application côté ***gamepad***
- l'utilisation classique de la *lib unboared* (communication entre appareils, données des joueurs)
- la déclaration et la gestion des scènes
- l'utilisation d'états du jeu partagés
- la gestion des langues

## Créer un jeu depuis ce template 
- Cliquer sur le bouton : `Use this template` ci-dessus
- Remplir les informations requises à la création du nouveau jeu (nom, description, etc)
- En local, exécuter les commandes suivantes en remplaçant le nom du jeu:
```bash
git clone git@github.com:<username>/<game-name>.git
cd <game-name>
npm install --legacy-peer-deps
``` 

## Tester un jeu

Dans le but de tester notre jeu dans des conditions réelles, nous utilisons l'application [game-runner](https://game-runner.web.app/). Cette application nécessite que le jeu utilise un certificat SSL.

### Génération d'un certificat SSL pour le développement local

Dans un premier temps, nous devons générer un certificat SSL pour le développement local.

Pour se faire, nous utiliserons l'outil [mkcert](https://github.com/FiloSottile/mkcert).

> :bulb: **Info:** L'avantage de [mkcert](https://github.com/FiloSottile/mkcert) est qu'il ne nécessite **aucune configuration** et qu'il est beaucoup plus facile à mettre en place que d'autres outils. De plus, [mkcert](https://github.com/FiloSottile/mkcert) est compatible avec toutes les plates-formes.

1. Commencez par installer [mkcert](https://github.com/FiloSottile/mkcert)
    - on [Linux](https://kifarunix.com/how-to-create-self-signed-ssl-certificate-with-mkcert-on-ubuntu-18-04/)
    - on [macOS](https://github.com/FiloSottile/mkcert#macos)
    - on [Windows](https://github.com/FiloSottile/mkcert#windows)
2. Générez un certificat et une clé privée pour le domaine souhaité:
    - Sur ma machine:
        
        ```bash
        mkcert localhost
        ```
        
    - En domaine du réseau local (préférable):
        
        ```bash
        mkcert 192.168.1.23  # à remplacer par l'adresse IP de la machine
        ```
        
        
### Utilisation du certificat SSL généré pour tester le jeu

Nous pouvons désormais lancer le jeu en local et fournir l’URL de celui-ci au [game-runner](https://game-runner.web.app/).

> :warning: **Attention:** Le [game-runner](https://game-runner.web.app/) est une application qui permet de faire tourner les jeux sous la  technologie Unboared. **Vous ne pourrez pas tester vos jeux sans celui-ci.**


**1. Lancer le jeu en local**

Pour lancer le jeu en local et en mode sécurisé `https`, nous utilisons la commande suivante:

```bash
# Utiliser le chemin d'accès au certificat et à la clé SSL précédemment générés
HTTPS=true SSL_CRT_FILE=./192.168.1.23.pem SSL_KEY_FILE=./192.168.1.23-key.pem expo start:web --https
```

**2. Tester le jeu**

Pour tester le jeu, nous devons lancer le [game-runner](https://game-runner.web.app/) et lui fournir l'URL d'accès au screen ainsi que le nom du jeu. 

> :bulb: **Astuce:** Il est aussi possible de copier/coller directement  la requête suivante dans un navigateur web, en modifiant les paramètres:
>
> - `game-name` : le nom du jeu à tester
> - `screen-url` : l'URL d'accès au screen du jeu
> 
> ```html
> https://game-runner.web.app/screen?name=><game-name>&url=<screen-url>
> ```
