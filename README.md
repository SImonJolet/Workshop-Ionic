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
De notre coté, on va tout faire à la main en commençant de "rien".

Pour finir taper `ionic serve`.

Vous êtes maintenant prêts à rentrer dans le vif du sujet: le code de notre application.

## Créeer son thème

Pour commencer on peut faire un tour de l'architecture, on se rends compte que c'ets une architecture Angular. Pas de panique, ici nous n'irons pas dans les méandres du _routing_ angular, nous allons juste utiliser l'architecture pour insérer toutes nos fonctionnalités.

Comme vous pouvez le voir, les feuilles de style sont en scss, donc lancer votre plugin "Live Sass Compiler" afin de compiler en direct.

Nos efforts vont se concentrer sur les .ts, .html et .scss du dossier `home`, avec quelques détours pour quelques lignes, mais tout sera expliqué (je l'espère) dans ce tuto.

Maintenant que vous êtes un peu familier avec notre environnement de travail, rendez-vous dans `src/app/home/home.page.htlm`.

Pour commencer, changez le titre de l'application.

Dans la balise `<ion-title> [Votre prénom]'s Todolist</ion-title>`.

Ensuite, allez dans le ficher `src/theme/variable.scss` et changer la première valeur (--ion-color-primary) pour la mettre en #5a8ca4.

Ici on peut voir que Ionic possède toute une série (9) de couleur de base pré-enregistrées qui peuvent être utilisée plus facilement. Ces couleurs possèdent aussi des variantes (contrast, shade et tint) qui sont utilisable.

Nous verrons comment les intégrer facilement au HTML plus tard.

```
<ion-toolbar color="primary">
  <ion-title>
    Todolist
  </ion-title>
</ion-toolbar>
```

Voila, notre en-tête est toute belle.

A présent, téléchargez l'image "bg" des assets.

Videz l'intérieur des balises `<ion-content>` et y intégrer une div ayant comme class "bg-img".

Ensuite, allez dans `src/app/home/home.page.scss` et mettez

![bg-img style](./asset/bg-img)
