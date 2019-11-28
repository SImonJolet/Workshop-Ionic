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

![bg-img style](./asset/bg-img.png)

Maintenant que nous avons un visuel, nous allons injecter les premières valeurs

![Hello](./asset/Hello.png)

On va réglé le problème de currentDate plus tard.

Vous pouvez bien sûr changer les textes avec par exemple "Bonjour [Votre prénom]"

Mettre un peu de style:

![StyleHello](./asset/StyleHello.png)

Pour finir cette partie, allez dans le fichier `src/app/home/home.page.ts`.

Dans export, déclarer currentDate comme étant une string :

```
export class HomePage {
    currentDate: string;

```

Et dans le constructor, ajouter la variable current date grâce à l'objet date de JavaScript

![NewDate](./asset/NewDate.png)

A présent, vous devriez avoir ceci:

![Step2](./asset/Step2.png)

Vous avez terminez la première étape: Bravo !!!!

On passe à la suite.

## Connecter son applicaton à FireBase

Pour ce faire, vous devrez commencer par avoir un compte google et vous rendre sur le site de [FireBase](https://firebase.google.com).

Ensuite, dans un nouvel onglet du termninal, faites la commande `npm install firebase @angular/fire --save`

Une fois ce package installé, allez dans `src/app/app.module.ts`.

Ici, nous allons importer d'une part **AngularFireModule** qui va associer notre application Ionic avec Firebase, et d'autre part **AngularFireDatabaseModule** pour utiliser les fonctions associées aux bases de données de Firebase.

![import-module](./asset/import-module.png)

Maintenant nous allons connecter Firebase à notre application.

Pour commencer, sur firebase, connectez-vous grâce à votre compte google.

Vous avez alors accès à la console. Clique sur "ajouter un projet", entrer le nom de votre projet, suivant, activer Google Analytics, suivant, accepter tout et créer le projet.

Ca peut prendre un peu de temps.
Vous avez alors accès à votre projet.

Pour faire le liaison avec votre appli,cliquez sur l'onglet web dans l'ajout d'application

![web](./asset/web.png)

Vous entrez un nom, et cliquez sur enregistrer l'application.

Vous avez alors un bloc de code, copiez-collez la partie `var firebaseConfig = {

Différents code

}`

et collez ce code dans l'export de l'export de `src/app/app.module.ts`.

Il faut ensuite déclarer ces packages.

Vous devez arriver un fichier qui ressemble à ça:

![BigPageConfig](./asset/bigPageConfig.png)

NB: grace à la fonction initializeApp, notre projet est lié à l'app.

A présent, allons dans la partie Database que vous trouvez dans dans l'onglet Développer (sur la gauche).

Cliquez sur "Créer une base de données", continuer en mode production, puis changez votre région en "eur3 (europe-west)".
De nouveau, ça prend un peu de temps.

Ensuite, c'est important: tout en haut, à coté de "Database", **passer de Cloud Firestore à RealTime Database !!!**

![Realtime](./asset/realtime.png)

Retour dans le code pour finir cette liaison.

Dans `src/app/home/home.page.ts` importez le module _AngularFireDatabase_ :

`import { AngularFireDatabase } from '@angular/fire/database';`

et déclarez ce module dans le constructor() pour povoir l'utiliser dans le reste de la page.

![constructorpublic](./asset/constructorpublic.png)

Voila, la liaison est finie.
C'est la partie la moins marrante et la plus abstraite, donc si vous êtes arrivé ici, ben vous êtes une re-sta et bravo !!
Au niveau du visuel, rien n'a changé, mais derrière tout fonctionne à présent!!

NB: Regardez quand même dans la console de l'inspecteur que rien ne soit cassé, c'est hautement probable.

## Ajouter une tâche à notre TodoList

Vous me direz: "T'es bien gentil Simon, mais on est loin du résultat". Je sais, donc je vous dis "Fooooooonce, le temps file et je passe pas ma journée ici !!! "

En avant pour une meilleure partie: l'ajout de tâche.

C'est à partir de cette partie que vous allez voir le plus de "particularités" d'**Ionic** et les avantages disponibles. Je vais en expliquer quelques dans le texte, mais il y en aura d'autres que je vous laisse découvrir.

Excusez-moi déjà pour le grand nombre de photo mais c'est plus simple et plus explicite qu'un long texte.

Pour commencer, nous allons créer un formulaire d'envoi qui contiendra simplement un champ de texte, et plus tard un bouton de validation.

![addButton](./asset.AddButton.png)

Petite explication:

- Le `lines="none"` re-style un peu le champ (esssayez sans pour voir la différence).
- le `[(ngModel)]="myTask"` sert à lié avec la partie .ts pour utilisé `myTask`.

On va donc aller déclarer le myTask en tant que string sous le currentDate.

Ajoutons à présent le bouton "ajouter" en insérant ce bout de code dans l' `ion-item` déjà là.

![plusIcon](./asset/pusIcon.png)

C'est ici qu'on rencontre pour la première fois les icones Ionic.

En effet, Ionic possède une bibliothèque d'icônes que l'on peut appeler avec leur nom. Ici: `name="add"`.

Nous voyons aussi pour la première fois une commande très utile pour le placement: le `slot`. Elle permet de placer un objet. Icon-only, je sais pas ce que ça veut dire, mais il y a aussi end et start qui sont très utilisés et qui mettre à gauche et à droite.

Ionic utilise déjà les nouvelles pratiues CSS (cf veille de Rimbaud.)

Enfin, le `(click)="addTaskToFirebase()"` appelle au click la fonction que nous allons implanter dans le fichier .ts

Encodez ce code dans le fichier `home.page.ts`.

![addTaskToFirebase](./asset/addTaskToFirebase.png)
