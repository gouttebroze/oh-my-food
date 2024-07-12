# SASS - BEM - CSS animations

## Identité graphique

* **Polices**:
  * Logo et titres: ``Shrikhand`` (police téléchargable [ici](https://www.1001fonts.com/shrikhand-font.html))
  * Texte: ``Roboto`` (police téléchargable [ici](https://www.fontsquirrel.com/fonts/roboto))

* **Couleurs**:
  * Primaire: ``#9356DC`` 
  * Secondaire: ``#FF79DA``
  * Tertiaire: ``#99E2D0``


## Versionning / Déploiement

* Projet en déploiement continue sur les [Github actions](https://gouttebroze.github.io/oh-my-food/).
* Code source / Repo. disponible [ici](https://github.com/gouttebroze/oh-my-food).


## Notes

```scss
.card:hover .checked {

}

```

## TODO

* trier fichiers `scss` & mettre les `fontawsome` ds 1 dossier séparé
* finir l'animation des plats dess menus

## Questions

* logo coeur ds les cards:
  * signaler la couleur (transparent ou linear) ds le "alt" de la balise <img>?

* utilisation des polices (fonts) 
  * déclarer 1 sélecteur & ses propriété, puis l'utiliser ds les classes ds le `html` pour les déclarer & les utiliser? (comme c'est présenter ds **google font**...)

### A propos des animations

* trouver les valeurs des couleurs des boutons (``linear-gardient``) (& au survol)

* pr l'animation au survol de l'icon "coeur" ? avec une image (pr faire avec couleur, faire avec `svg`)

* Animation des cartes des restaurant 
  * chaque restaurant propose une carte, un menu avec plusieurs propositions pour l'entrée, le plat & le dessert
  * l'utilisateur peut choisir les propositions qu'il désire 
  * l'action de ce choix lance une animation (en CSS), à terme, ce choix sera fait au click (sûrement en JavaScript), pour l'instant (en CSS), ce sera au survol
  
  * donc, l'**animation** se joue au **survol** du block 

  * **comment construire cette animation ?**

    * avec les **keyframes** ? qui sera lancé (propriété "animation-name") au survol (`hover`) du block de proposition ? 
    
    * il faut faire apparaitre un icon (fontawsome)

      * icon sur un pseudo element `::before` ou avec une balise ds le `HTML` ?

      * ce survol fait apparaitre un autre élément (caché) ? ou modifie le block ? 
      


* pbm de marges (base du style, casse tout ...)
```scss
* {
  padding: 0;
  margin: 0;
}
```

## VEILLE - JAVASCRIPT

+ créer la partie JavaScript du loader avec la base CSS déjà réalisée 

+ proposition: ``loader`` sous forme de ``custom element``, simple d'utilisation

```html
...
<head>
  ...
  <title>Loader</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
    }
  </style>
  <script src="./index.js" type="module" defer></script>
<head>

<body>
  <spinning-dots></spinning-dots>
</body>
```

```js
/* our class must extends from HTMLElement to create our customelement into HTML file */
class SpinningDots extends HTMLElement {

}

customElements.define('spinning-dots', SpinningDots)

```

## MEMO 

### MEMO SASS

* La règle `@use` permet de charger les variables, mixins & fonctions, les partager & les réutiliser sans dupliquer de code entre différents fichiers `scss`.

* Pour en savoir **+**, voir la doc. de `sass` [ici](https://sass-lang.com/documentation/at-rules/use/).

## TODO

* Avec Sass, la directive @import permet d’importer durant la compilation le contenu d’un fichier SCSS dans un autre fichier SCSS.
Il est inutile de préciser l’extension du fichier importé à Sass.
Une feuille partielle ou partial, dont le nom commence par un underscore, est un fichier qui a uniquement vocation à être importé dans d’autres feuilles de styles. Aucun fichier CSS n’est généré pour lui à la compilation.

* créer des "partials" avec un underscore (_).