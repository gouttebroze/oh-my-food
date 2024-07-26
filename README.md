# SASS - BEM - CSS animations

## CSS structure organisation

* Structure `CSS`-`SASS`:
  * Voir le [pattern SASS 7.1](https://sass-guidelin.es/#the-7-1-pattern)

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

* créer le `favicon`, voir ressources:
  * [mini-cours CSS](https://haudrey.notion.site/Changer-l-ic-ne-du-site-dans-l-onglet-favicon-b9d1a65f263541b6a1cbab3e95f06ce9),
  * [tuto alsacreations](https://www.alsacreations.com/astuce/lire/59-icon-link-rel-favicon-ico-navigateur.html)

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

* Continuer veille (sur custom-element & autres)

* fix pages 2 , voir 3 et 4 ...

* faire 1 base.css & un main.css

* mettre fichier font awesome scss ds 1 dossier à part

## HTML / CSS validator

* [`HTML` validator](https://validator.w3.org/nu/)

  * ``html`` code: issues to fix:

    * *Error: The element button must not appear as a descendant of the a element.*
      *From line 35, column 11; to line 35, column 47*

    ```html
          <button class="btn--linear-gardient">Explor...</button>
    ```

* [`CSS` validator](https://jigsaw.w3.org/css-validator) :

  * ``CSS`` code: issues to fix:

    * `Roboto` font family
