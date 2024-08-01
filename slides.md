---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides, markdown enabled
title: Welcome to Slidev
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply any unocss classes to the current slide
class: text-center
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# https://sli.dev/guide/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/guide/syntax#mdc-syntax
mdc: true
---

# Dynamiser

Presentation slides for developers

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: fade-out
---

# Dynamisez une page web avec des animations CSS

## interface mobile-first du site de la start-up OhMyFood

* implémenterez d'animations CSS 
* utilisation du pré-processeur SASS 
* versionning du projet avec Git et GitHub
* déploiement continue du site internet

* réalisation de l’animation du cœur
* réalisation du sélecteur de plat
* choix pour le loader de la page d’accueil
* comment vous avez abordé le code du projet en mobile first?

<br>
<br>

Read more about [Why Slidev?](https://sli.dev/guide/why)

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Animations

## Réalisation de l’animation du cœur - bouton "LIKE"

```html {1,8|3|2,3,4|6|5,6,7|all}
<span class="wrapper-icon">
  <span class="icon icon-default">
    <i class="fa-regular fa-heart"></i>
  </span>
  <span class="icon icon-hover">
    <i class="fa-solid fa-heart"></i>
  </span>
</span>
```

--- 

```scss {1,3|1,2,3,4|1,2,3,4,6,7|1,2,3,4,6,7,8,9,10|all}
.wrapper-icon {
  display: block;
  position: relative;
}

.wrapper-icon .icon {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  transition: opacity 600ms ease;
  font-size: 3rem;
}
```
--- 

```scss
.wrapper-icon .icon-default {
  opacity: 1;
}

.wrapper-icon .icon-hover {
  opacity: 0;
  background-image: linear-gradient(193.33deg, #9356DC -11.44%, #FF79DA 123.93%) !important;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

.wrapper-icon:hover .icon-default, 
.wrapper-icon:focus .icon-default {
  opacity: 0;
}

.wrapper-icon:hover .icon-hover, 
.wrapper-icon:focus .icon-hover {
  opacity: 1;
  background-image: linear-gradient(193.33deg, #9356DC -11.44%, #FF79DA 123.93%) !important;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}
```

---

# Explication code animation boutton "coeur"

## Elements de l'animation: Icons **Font Awesome**, stylisé avec les classes ``fa-regular`` et ``fa-solid``

* Nous plaçons dans notre code `html` 2 icons "fa-heart".
* Ces 2 icons sont identiques mais avec 2 styles différents.
* Nous donnons les styles suivants aux icônes **Font Awesome** `fa-heart`:
  
  + icône par défault, la classe ``fa-regular`` sans fond et avec bordure
  + icône du survol, la classe ``fa-solid`` avec fond plein (background plein ou rempli)

* Il est important que lorsque nous avons un effet au hover ou lors d’un clic, nous ayons l’effet inverse lorsque l’on quitte le survol.

* Le bouton "J’aime" en forme de cœur doit au clic se remplir progressivement. Pour cette première version, l’effet peut apparaître au survol sur desktop au lieu du clic.

1. Tout d'abord, il faut donner la même position aux 2 icones, afin qu'ils se chevauchent.

2. En gérant le niveau d'opacité:
  + nous cachons l'icône destiné au survol 
  + en lui attribuant une opacité à 0 
  (`opacity: 0;`)
  + nous laissons visible l'icône par défault en lui donnant une opacité à 1 (`opacity: 1;`).

3. Avec la propriété ``-webkit-text-fill-color`` de valeur ``transparent``, nous effaçons (transparent) ce qui déborde des contours de l'icon au survol (la couleur apporté par la propriété "background-image" forme par défault un carré autour de l'icône).

--- 

# Animation - Sélecteur de plat

```html {all|11,12,13}
<div class="card card-2">
  <div class="card__content">
    <div class="card__content--title">
      <h3>Foie gras de canard mi-cuit</h3>
    </div>
    <div class="card__content--description">
      <p>Et ses copeaux de truffe noire</p>           
    </div>
  </div>
  <p class="card__bold">35€</p>
  <div class="card__check"> 12
    <span class="fa-solid fa-check"></span>
  </div>
</div>
```

* Côté `html`:
  + nous créons une ``div`` portant la classe ``card__check``, qui contient une span avec l'icône **Font Awesome** et portant les classes ``fa-solid`` et ``fa-check``.

---

## Code CSS du sélecteur de plat

```scss
&__check {
    background-color: themes.$third-color;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 60px;
    height: 100%;
    margin-right: -60px; // permet de cacher la div
    transition: margin 500ms; // propriétés de la transition (indique quelle propriété animer, et la durée de la transition
  }

  &:hover {
    .card__check {
      margin-right: 0; // rend visible la div au survol
    }
  }
```
--- 

# Explication code / sélecteur de plats

* Côté `css`: 

  + ON MASQUE LA `DIV` 
  
    + nous donnons une propriété `margin-right` avec une valeur de `-60px`
    + cette valeur négative permet de masquer la ``div`` sur le côté de la carte

  + Puis, NOUS FAISONS APPARAITRE cette `div` durant l'état de survol, nous allons surcharger le style de notre classe `card__check` avec la pseudo-classe `:hover` et apporter une nouvelle valeur à la propriété `margin-right`, cette fois-ci à 0, ce qui a pour effet de rendre notre div contenant l'icône **check**, visible, dans notre élément `card`.

* CREATION DE L'ANIMATION: 

  + Enfin, nous apportons la propriété `transition` sur notre classe `card__check`, afin de créer notre animation, et qui va nous permettre de passer progressivement de notre état de départ où la div est masquée à l'état final de l'animation, où cette div est dévoilée. On va alors signifier la propriété à animer, c'est-à-dire `margin`, ainsi que la durée de l'animation, soit `500 millisecondes`.

--- 

# Pourquoi ce choix de loader?

* J'ai choisi d'aller au plus simple pour le design du loader, afin de faciliter les futurs modifications.
* Ce loader sera simple à modifier, sur son design et sur son animation
* un loader avec une des trois couleur de la charte graphique: 
  + un cercle en fond avec couleur clair
  + avec un quard de cercle avec couleur plus foncé

```scss
.loader { 
  width: 50px;
  height: 50px;
  margin-right: 15px;
  display: inline-block;
  vertical-align: middle;
  position: relative;
  animation: spin 1000ms;
  animation-timing-function: linear;
  animation-iteration-count: infinite;

  &-quart {
    border-radius: 50%;
    border: 6px solid t.$third-color;
 
    &::after {
      content: "";
      position: absolute;
      top: -6px;
      left: -6px;
      bottom: -6px;
      right: -6px;
      border: 6px solid transparent;
      border-top-color: t.$btn-text-color;
      border-radius: 50%;
    }
  }
}
```

---

## @keyframes 

```scss
@keyframes spin {
  from {
    transform: rotate(0turn);
  }
  to {
    transform: rotate(1turn);
  }
}
```
--- 

# Comment vous avez abordé le code du projet en mobile first?

* J'ai d'abord écrit le code pour un format mobile.
* Puis j'ai créé différentes variables correspondantes aux breakpoints des formats d'écrans plus larges.
```scss
// ./partials/_responsive.scss

/* breakpoints */
$medium: 768px;
$large: 1024px;
$xl: 1200px;

/* tablette */
$medium-screen: "only screen and (min-width: #{$medium})";
/* desktop */
$large-screen: "only screen and (min-width: #{$large})";
/* xl desktop */
$xl-screen: "only screen and (min-width: #{$xl})";
```

* J'ai alors une variable pour viser les devices supérieur à 768 px, 
* une variable pour viser les devices supérieur à 1024 px, 
* et une variable pour viser les devices supérieur à 1200 px.

* Je peux alors utiliser ces variables directement dans mon code en mobile first, spécialement dans les sélecteurs dont je souhaite modifier le style, lorsque la taille d'écran est agrandie.

---

* exemple:

```html
<!-- index.html -->
<section class="hero"> <!-- ligne 31 -->
  <h1 class="hero__title">Réservez le menu qui vous convient</h1>
  <h3 class="hero__subtitle">Découvrez des restaurants d’exception, sélectionnés par nos soins.</h3>
  <a class="btn__block" href="#restaurants">
    <div class="btn--linear-gardient">
      <span>Explorer nos restaurants</span>
    </div>
  </a>
</section> <!-- ligne 39 -->
```

---

```scss
.hero {
  margin-top: 3.9rem;
  margin-bottom: 4.5rem;
  text-align: center;
  background-color: themes.$second-background-color;

  &__title {
    text-align: center;
    font-size: 2.4rem;
    padding-right: 2.9rem;
    padding-left: 3.8rem;

    @media #{$medium-screen} {
      font-size: 3rem;
    }
    @media #{$large-screen} {
      font-size: 3.5rem;
    }
    @media #{$xl-screen} {
      font-size: 4rem;
    }
  }

  &__subtitle {
    text-align: center;
    font-size: 1.8rem;
    font-weight: 300;
    padding: 1.7rem 2.2rem 2.9rem 2.2rem;
  }
}
```

---

* Je modifie la valeur de la propriété `font-size` du texte de la classe `hero__title`, soit le titre **Réservez le menu qui vous convient**, suivant la largeur de la taille d'écran. 

* Sur mobile, la police du titre aura une valeur de `2.4 rem`, puis avec la variable `medium-screen`, la valeur passe à `3 rem` au-dessus de 768 pixels, puis avec la variable `large-screen`, la valeur passe à `3.5 rem` au-dessus de 1024 pixels et enfin avec la variable `xl-screen`, la valeur passe à `4 rem` au-dessus de 1200 pixels.

---
