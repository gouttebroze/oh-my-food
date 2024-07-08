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
      

### les icons

* pbm de redimentionnement (date d'hier soir donc pas encore eu le temps de creuser...)

* pbm de marges (base du style, casse tout ...)
```scss
* {
  padding: 0;
  margin: 0;
}
```

## import en SCSS

* voir pr importer (& factoriser) certains selecteurs (génériques) comme `header`, `footer` ... 
  * avec `@use` ? ok pr variables mais comment pr selecteurs ? créer mixins ? 
    * A CHERCHER