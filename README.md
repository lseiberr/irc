# IRC

![C++](https://img.shields.io/badge/language-C++-blue.svg)  
![License](https://img.shields.io/badge/license-MIT-green.svg)

Un serveur (et/ou client selon ton implémentation) IRC en C++, inspiré des projets traditionnels d’IRC — but : implémenter le protocole IRC et permettre à des clients IRC de se connecter, chatter, rejoindre des salons, etc.

---

## Table des matières

- [À propos](#à-propos)  
- [Fonctionnalités](#fonctionnalités)  
- [Prérequis](#prérequis)  
- [Installation & compilation](#installation--compilation)  
- [Utilisation](#utilisation)  
- [Protocole & commandes prises en charge](#protocole--commandes-prises-en-charge)  
- [Contribuer](#contribuer)  
- [Licence](#licence)

---

## À propos

Le projet `irc` a pour objectif de proposer une implémentation maison du protocole IRC (Internet Relay Chat) en C++. L’idée est de créer un serveur capable d’accepter des connexions clients IRC, gérer plusieurs utilisateurs, canaux, et permettre l’échange de messages en temps réel, tout en se conformant (autant que possible) aux spécifications standard.

---

## Fonctionnalités

Selon l’état actuel du projet — mais voici une structure typique adaptée à un serveur IRC :

- Gestion des connexions TCP pour plusieurs clients en simultané (multiplexage sockets, `poll()` / `select()`, etc.).  
- Authentification initiale (mot de passe si prévu), gestion des pseudos (nickname), usernames, etc.  
- Création, jonction et gestion de canaux / salons.  
- Envoi/réception de messages publics (dans un canal) ou privés (entre utilisateurs).  
- Gestion des commandes IRC de base : identification, JOIN, PART, NICK, USER, PRIVMSG, QUIT, etc.  
- Nettoyage et déconnexion correcte des clients, gestion des états.  
- Potentiellement options d’extensions (modes, topics, etc.), selon la portée du projet.  

---

## Prérequis

- Un compilateur C++ compatible (g++, clang++, …).  
- Outils de build : `make` (ou un autre système de build selon ce que tu utilises).  
- (Optionnel) Une machine ou un OS supportant les sockets réseau (Unix‑like, Linux, macOS, etc.).  

---

## Installation & compilation

Voici comment cloner et compiler le projet :

```bash
git clone https://github.com/lseiberr/irc.git
cd irc
make         # ou autre commande de compilation
````

---

## Utilisation

Après compilation, selon le mode (serveur ou client) :

* Pour lancer le serveur :

```bash
./ircserv <port> [<mot_de_passe_si_necessaire>]
```

* Puis depuis un client IRC (type `irssi`, `weechat`, ou un client graphique) ou un simple outil comme `netcat`, connecte-toi au serveur :

```bash
irc_client —h <adresse_serveur> —p <port>
```

* Une fois connecté.e, identifie-toi (NICK, USER, éventuellement PASS), puis rejoins un canal ou chats.

*(Adapte ces instructions à ce que ton projet fournit réellement — exécutable, nom, paramètres, etc.)*

---

## Protocole & commandes prises en charge

Le projet vise à implémenter les aspects fondamentaux du protocole IRC (conformément aux RFC classiques). Voici quelques commandes typiques supportées :

* `PASS` — mot de passe de connexion (si nécessaire)
* `NICK` — définir ou changer le pseudo
* `USER` — définir le nom d’utilisateur / hostname / realname
* `JOIN` — rejoindre un canal
* `PART` — quitter un canal
* `PRIVMSG` — envoyer un message privé à un utilisateur ou à un canal
* `QUIT` — se déconnecter du serveur
* (Éventuellement) gestion des modes, topics, kick, etc. selon l’avancement

---

## Contribuer

Contributions bienvenues ! Tu peux aider en :

* Corrigeant des bugs ou des comportements IRC incorrects.
* Ajoutant des commandes manquantes du protocole.
* Améliorant la gestion des connections concurrentes, la robustesse réseau.
* Ajoutant des tests, documentation, exemples d’usage, scripts d’installation.
* Documentant le protocole et l’architecture du serveur.

N’hésite pas à forker, proposer des *pull requests*, signaler des bugs, ou suggérer des fonctionnalités.

---

## Licence

Ce projet est — par défaut — sous licence **MIT**
