# Tp 5 de linux : Api minecraft server deploiment

#### collaborateur : Yanice Bousseria, Aymeric Lavaud, Victor Dalamel de Bournet


## Sommaire

- [TP5 : Hébergement d'une solution libre et opensource : "Api minecraft server deploiment"](#tp5--hébergement-dune-solution-libre-et-opensource)
  - [Sommaire](#sommaire)
  - [Déroulement](#déroulement)
    - [Choix de la solution](#choix-de-la-solution)
    - [Mise en place de la solution](#mise-en-place-de-la-solution)
    - [l'API et Amélioration de la solution](#maîtrise-de-la-solution)
  - [Rendu attendu](#rendu-attendu)
 
 ## Déroulement

### Choix de la solution

Pour le tp 5, nous avons choisi de faire une api capable de lancer rapidement des serveurs minecraft heberger sur un serveur (Notre machine, une vm ou meme un serveur qu'on loue).
Une fois le service executé, on à accès au serveur et jouer à Minecraft !


### Mise en place de la solution
port : 25565 mc -> 25575
node app.js 


### Maîtrise de la solution

Une fois en place, posez-vous les questions pour comprendre ce qui a été mis en place, plus en détail. Réfléchissez avec les outils et concepts qu'on a vus en cours :

- y a-t-il un fichier de conf ?
- combien de programmes y a-t-il ?
  - et donc quels processus ?
  - sous quelle identité, quel user, tournent chacun de ces processus ?
- où sont stockées les données de l'application ?
  - dans quel dossier ?
  - y a-t-il une base de données ?
- sur quel(s) port(s) écoute la solution ?
- comment on gère le sycle de vie de l'app ?
  - c'est un service ? un conteneur ? autre chose ?
  - où sont les logs ?
- l'architecture et/ou la conf de la solution respectent-elles les bonnes pratiques élémentaires ?
  - un service par machine (ou un service par conteneur)
  - base de données sur une machine dédiée
  - gestion correcte des utilisateurs et des permissions

### Amélioration de la solution

Cette partie dépendra beaucoup de la solution que vous avez retenu. Pensez comme au TP3.

Chaque brique peut-être améliorée, d'un point de vue sécurité, performances, ou facilité la maintenabilité. 

Quelques exemples :

- redondance
   - réplication de base de données
   - répartition de charges entre deux serveurs applicatifs
     - par ex, deux serveurs web pour accueillir 2x plus de clients sur un site web
- sécurité d'accès
  - mise en place d'un HTTPS pour un site web
- performances
  - ne pas utiliser les serveurs web des langages, mais préférer un serveur web dédié
  - préférez un php-fpm qu'un php géré par la machine
- autres, dépendant de la solution choisie

On pensera aussi, en plus de l'amélioration de chaque brique, au maintien en conditions opérationelles, notamment :

- monitoring + alerting
- sauvegarde + test de restauration
- documentation (ça, c'est votre compte-rendu)

## Rendu attendu

Vous livrerez dans un dossier dédié, dans le dépôt git de rendu habituel :

- une documentation d'installation
  - format Markdown
  - c'est l'ensemble des opérations à réaliser pour mettre en place votre solution
    - la suite des commandes donc
    - mais pas que, suivant vos sujets
  - vous livrerez aussi les fichiers nécessaires à la mise en place
    - fichiers de conf
    - `docker-compose.yml`
    - etc.


