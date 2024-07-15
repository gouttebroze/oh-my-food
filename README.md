# SASS - BEM - CSS animations

## Identité graphique

* **Polices**:
  * Logo et titres: ``Shrikhand`` (police téléchargable [ici](https://www.1001fonts.com/shrikhand-font.html))
  * Texte: ``Roboto`` (police téléchargable [ici](https://www.fontsquirrel.com/fonts/roboto))

* **Couleurs**:
  * Primaire: ``#9356DC``
  * Secondaire: ``#FF79DA``
  * Tertiaire: ``#99E2D0``

  * **Linear-gardient & box-shadow**:

  ```css
    background: linear-gradient(193.33deg, #9356DC -11.44%, #FF79DA 123.93%);
    box-shadow: 0px 4px 10px 0px rgba(0, 0, 0, 0.25);
  ```

  * **Linear-gardient & box-shadow** on button hover:

  ```css
    background: linear-gradient(200.64deg, #9356DC -5.2%, #FF79DA 110.74%),
                linear-gradient(0deg, rgba(255, 255, 255, 0.15), rgba(255, 255, 255, 0.15));
    box-shadow: 0px 4px 15px 0px rgba(0, 0, 0, 0.35);
  ```

  * **like** / **heart** icon
  * **like** / **heart** icon animated on **click**:

  ```css
  background: linear-gradient(193.33deg, #9356DC -11.44%, #FF79DA 123.93%);
  ```

  * **Badge / Nouveau button**

  ```css
  box-shadow: 0px 2px 4px 0px rgba(0, 0, 0, 0.15);
  ```

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

* créer la partie JavaScript du loader avec la base CSS déjà réalisée

* proposition: ``loader`` sous forme de ``custom element``, simple d'utilisation

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

## TODO - TROUBLES

* Finir animation loader

* Continuer veille (sur custom-element & autres)

* fix bugs (position titres des 3 cards ("entrée", "plat", "dessert"))

* fix pages 2 , voir 3 et 4 ...

* fix bordure entre logo & adresse : le logo passe par dessus le block de l'adresse ou l inverse ?

* icon like au click sur mobile

* responsive tablette & desktop

* faire 1 base.css & un main.css 

* mettre fichier font awesome scss ds 1 dossier à part

* fix title & sous-titre des cards (ds menu) pourquoi les ... fonctionne pas ?

<!-- OK * Problème sur animation **icons heart / like**:

  * après un survol, l'icon ne retrouve pas son état initial immédiatement mais il devient noir quelques secondes...
  * cette couleur noir correspond à la couleur donné à la propriété `background` sur le second icon (`fa-solid`). Pour rappel, on donne a cet icon une opacité de 0 qui passe à 1 au survol. On a deux icons, l'autre est un `fa-regular` avec une opacité de 1 qui passe à 0 au survol.
  * au survol, on donne un `background` de couleur `linear-gardient` à l'icon `fa-solid`, c'est cet élement qui à par défaut cette couleur noire. -->
