# SASS - BEM - CSS animations

## Versionning / Déploiement

* Projet en déploiement continue sur les [Github actions](https://gouttebroze.github.io/oh-my-food/).
* Code source / Repo. disponible [ici](https://github.com/gouttebroze/oh-my-food).

## JavaScript - Propositions

* créer le `favicon`, voir ressources:
  * [mini-cours CSS](https://haudrey.notion.site/Changer-l-ic-ne-du-site-dans-l-onglet-favicon-b9d1a65f263541b6a1cbab3e95f06ce9),
  * [tuto alsacreations](https://www.alsacreations.com/astuce/lire/59-icon-link-rel-favicon-ico-navigateur.html)

* créer la partie ``JavaScript`` du **loader** avec la base CSS déjà réalisée

* proposition ``loader`` 

  * à masquer une fois le code `html` et `css` chargé

  * on peut écouter l'évenement `load` sur le `DOM` (événement qui assure un chargement complet contrairement à l'évenement `DOMContentLoaded`...)

  * ajouter / modifier les classes `CSS` une fois cet évenement terminé (soit tt le code chargé)

  * en savoir d'avantage sur les événements: 
  
    * ``DOMContentLoaded`` [ici](https://developer.mozilla.org/fr/docs/Web/API/Document/DOMContentLoaded_event)

    * ``load`` [ici](https://developer.mozilla.org/fr/docs/Web/API/Window/load_event)


## CSS structure organisation

* Structure `CSS`-`SASS`:
  * Voir le [pattern SASS 7.1](https://sass-guidelin.es/#the-7-1-pattern)

## Validation du code HTML et CSS

* [`HTML` validator](https://validator.w3.org/) / Showing results for https://gouttebroze.github.io/oh-my-food/:

  *Document checking completed. No errors or warnings to show.*

* [`CSS` validator](https://jigsaw.w3.org/css-validator/) / Résultats de la validation **W3C** **CSS** de https://gouttebroze.github.io/oh-my-food/ (CSS niveau 3 + SVG):

  *Félicitations ! Aucune erreur trouvée. Ce document est valide conformément à la recommandation CSS niveau 3 + SVG*
