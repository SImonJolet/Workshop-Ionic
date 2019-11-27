# Workshop-Ionic

Notre but :

![Notre app](https://drissas.com/wp-content/uploads/2019/11/ionic-todolist.gif)

Bonjour à tous et bienvenue à ce Workshop Ionic, dans lequel nous allons développer une **ToDO List** grâce à l'environement Ionic, avec une base de donnée **FireBase**, en respectant une architecture **Angular.**

Pour ce faire, nous allons suivre ensemble toute une série d'étapes pour au final pouvoir créer des taches, les afficher et les supprimer.

Le tout en utulisant des balises <ion- .... >

## Installaton du projet

Pour commencer installer **Ionic** en glbal avec la commande
`npm install -g ionic`

Ca va mettre un peu de temps à s'installer.

Ensuite lancer le projet ou vous voulez dans votre ordinateur en tapant dans le terminal `ionic start Todolist blank`.

Tous les fichiers nécessaires se créent.

Le fait de mettre le " blank " va faire en sorte d'avoir un projet "vide". A la place, on peut mettre "tabs" pour une interface avec plusieurs onglets, "conference" pour un site avec toutes une séries de fonctuionnalité pré-faites, comme une carte, un calendrier etc ...
De notre coté, on va tout faire à la main en commençant de "rien"

Vous êtes maintenant prêts à rentrer dans le vif du sujet: le code de notre application.

## Créeer son thème

Pour commencer on peut faire un tour de l'architecture, on se rends compte que c'ets une architecture Angular. Pas de panique, ici nous n'irons pas dans les méandres du _routing_ angular, nous allons juste utiliser l'architecture pour insérer toutes nos fonctionnalités.

Nos efforts vont se concentrer sur les .ts, .html et .scss du dossier `home`, avec quelques détours pour quelques lignes, mais tout sera expliquer (je l'espère) dans ce tuto.

Maintenant que vous êtes un peu familier avec notre environnement de travail, rendez-vous dans `src/app/home/home.page.htl`.

Pour commencer, changez le titre de l'application.

Dans la balise `<ion-title> [Votre prénom]'s Todolist</ion-title>`.

Ensuite, allez dans le ficher `src/theme/variable.scss` et
