![logo_ironhack_blau 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# LAB | Tuits de Vue.js

## Introducció

Passar dades a través d' *accessoris* és un concepte important de Vue.js que s'entén millor amb la pràctica pràctica. Utilitzarem aquest exercici per ajudar-vos a consolidar la vostra comprensió dels accessoris.

Clonarem una peça existent d'IU des d'una aplicació popular, Twitter. Comencem!

<p align="center"><img src="https://education-team-2020.s3.eu-west-1.amazonaws.com/web-frontend-vue/lab-vue-tweets-4.png" width="500"/></p>

## Configuració

- Bifurca aquest repo
- Clona aquest repo
- Obriu el LAB i comenceu:

  ```bash
   $ cd lab-vue-tweets-cat
   $ yarn install
   $ yarn dev
  ```

## Submissió

- En finalitzar, executeu les ordres següents:

  ```bash
  $ git add .
  $ git commit -m "done"
  $ git push origin main # or master if you are working from a master
  ```

- Creeu una sol·licitud d'extracció perquè els vostres TA puguin comprovar el vostre treball.

## Començant

1. Utilitzarem [Font Awesome](https://fontawesome.com/v5.15/icons?d=gallery\&p=1) per a les icones de la nostra aplicació. Afegiu el següent full d'estil a la `head` de la pàgina `index.html` :

   ```html
        <link
         rel="stylesheet"
         href="https://pro.fontawesome.com/releases/v5.10.0/css/all.css"
         integrity="sha384-AYmEC3Yw5cVb3ZcuHtOA93w35dYTsvhLPVnYs9eStHfGJvOvKxVfELGroGkvsg+p"
         crossorigin="anonymous"
       />
   ```

## Instruccions

### Iteració 1 | Contingut inicial

Per permetre-vos centrar-vos en Vue.js sense haver de preocupar-vos de l'estil, us hem proporcionat els estils CSS. Tot el CSS s'inclou al codi d'inici del fitxer `src/App.vue` dins de l'etiqueta`<style>`

També us hem proporcionat el contingut inicial de l' `App.vue` i hem inclòs l'estructura HTML del component `Tweet.vue` . Abans de començar a treballar, preneu un moment per repassar aquests dos fitxers.

Un cop executeu l'aplicació inicialment, hauríeu de veure el següent:

![Tweet component després de la configuració inicial](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-frontend-vue/lab-vue-tweets-1.png)

En aquests moments, el component `Tweet` està mostrant contingut estàtic. Ho canviarem en la propera iteració. Actualitzarem el component `Tweet` per mostrar el contingut procedent dels `props` .

### Iteració 2 | Passeu el tuit com a prop

A `App.vue` , tenim una matriu anomenada `tweetsArray` que conté objectes que representen tuits. Utilitzarem el component `Tweet` per mostrar aquests objectes de *tweet* . En el `Tweet` mostrarem el `name` de l'usuari, la `image` de l'usuari, l' `handle` de l'usuari, la `timestamp` de temps del tuit i el `message` .

**Passeu el tuit com a accessori**

Passeu el primer objecte de dades dels `tweets` com a complement al component `Tweet` :

```vue
<!-- src/App.vue -->
<!-- ... -->

<Tweet tweet="tweets" />
```

**Mostra el contingut del `Tweet` al component Tweet**

Actualitzeu el component `Tweet` per mostrar els valors procedents de l'accessori de `tweet` . Recordeu que el valor que hem passat és un objecte/

**Resultat Esperat**

Un cop fet, el vostre component `Tweet` hauria de mostrar el contingut següent:

![Component de piulades després de passar el suport de "tuits".](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-frontend-vue/lab-vue-tweets-2.png)

### Iteració 3 | Creeu els components

Ara crearem fitxers nous per als components que farem en les següents iteracions. Dins de la carpeta `src/components/` creeu els següents fitxers nous:

- `src/components/ProfileImage.vue` ,
- `src/components/User.vue` ,
- `src/components/Timestamp.vue` ,
- `src/components/Message.vue` i
- `src/components/Actions.vue` .

A les iteracions següents, haureu de refactoritzar el component `Tweet` . Se us demanarà que extreu parts de l'estructura HTML existent en components nous:

![Exemple: refactorització del component "Tweet".](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-frontend-vue/lab-vue-tweets-3.png)<br/>

**Quan s'hagin acabat amb totes les iteracions** , la versió final del vostre component `Tweet` tindrà aquest aspecte:

<details>
<summary> Feu clic per veure el codi </summary>

```vue
<!-- FINAL VERSION -->

<template>
  <div className="tweet">
    <ProfileImage image="user.image" />

    <div className="body">
      <div className="top">
        <User userData="user" />
        <Timestamp time="timestamp" />
      </div>

      <Message message="message" />
      <Actions />
    </div>

    <i class="fas fa-ellipsis-h"></i>
  </div>
</template>

<script>
export default {
  name: Tweet,
  props: {
    user: Object,
    timestamp: String,
    message: String
  }
}
</script>
```

:heavy_exclamation_mark: No copieu i enganxeu el codi anterior directament al component `Tweet` !

Ho fareu en les properes iteracions, pas a pas. Anireu substituint les parts d'HTML a mesura que creeu cada component nou.

<hr>
<br>
</details>

### Iteració 4 | Component ProfileImage

**Extreu HTML**

Extraieu l'etiqueta `img` existent i representa-la mitjançant el component `ProfileImage` :

```vuex
<img src="IMAGE_URL" className="profile" alt="profile"/>
```

**Renderitza el component**

Un cop fet, importeu el component `ProfileImage` a `Tweet.js` . Després d'importar-lo, renderitza el component dins de `Tweet` de la manera següent:

```vue
<!-- ... -->
<template>
  <div className="tweet">
    <ProfileImage image="user.image" />
<!-- ... -->
```

**Accediu als accessoris**

`ProfileImage` rep una `image` de suport. Estableix aquest valor com a `src` de l' `<img />` .

### Iteració 5 | Component d'usuari

**Extreu HTML**

Extreu les etiquetes d' `span` existents que mostren la informació de l'usuari i representa'ls mitjançant el component `User` :

```vue
<span className="user">
  <span className="name"> USER_NAME </span>
  <span className="handle">@ USER_HANDLE</span>
</span>
```

**Renderitza el component**

Importeu el component `User` a `Tweet.js` . Després d'importar-lo, renderitza el component dins de `Tweet` de la manera següent:

```vue
<!-- ... -->

<template>
  <div className="tweet">
    <ProfileImage image="user.image" />

    <div className="body">
      <div className="top">
        <User userData="user" />

<!-- ... -->
```

**Accediu als accessoris**

Hem passat l'objecte amb la informació de l'usuari a través del prop `userData` . Accediu i visualitzeu el *nom* de l'usuari i l' *identificador* de Twitter .

### Iteració 6 | Component de marca de temps

**Extreu HTML**

Extraieu l'etiqueta d' `span` existent que mostra la informació de *marca* de temps i representa-la mitjançant el component `Timestamp` de temps:

```vuex
<span className="timestamp"> TWEET_TIMESTAMP </span>
```

**Renderitza el component**

Importeu el component `Timestamp` a `Tweet.js` . Després d'importar-lo, renderitza el component dins de `Tweet` de la manera següent:

```vue
<!-- ... -->

<template>
  <div className="tweet">
    <ProfileImage image="user.image" />

    <div className="body">
      <div className="top">
        <User userData="user" />
        <Timestamp time="timestamp" />

<!-- ... -->
```

**Accediu als accessoris**

`Timestamp` de temps rep un `time` de prop. Mostra aquest valor com el contingut de l'etiqueta `span` .

### Iteració 7 | Component del missatge

**Extreu HTML**

Extreu l'etiqueta `p` existent i representa-la mitjançant el component `Message` :

```vuex
<p className="message"> TWEET_MESSAGE </p>
```

**Renderitza el component**

Quan acabeu, importeu el component `Message` i representeu-lo al `Tweet.js` de la manera següent:

```vue
<!-- ... -->

<template>
  <div className="tweet">
    <ProfileImage image="user.image" />

    <div className="body">
      <div className="top">
        <User userData="user" />
        <Timestamp time="timestamp" />
      </div>

      <Message message="message" />
<!-- ... -->
```

**Accediu als accessoris**

`Message` rep un `message` de suport. Mostra aquest valor a l'etiqueta `p` .

### Iteració 8 | Component d'Accions

**Extreu HTML**

Extreu l'etiqueta `div.actions` del missatge existent i representa-la mitjançant el component `Actions` :

```vuex
    <div className="actions">
      <i class="far fa-comment"></i>
      <i class="fas fa-retweet"></i>
      <i class="far fa-heart"></i>
      <i class="fas fa-share"></i>
    </div>
```

**Renderitza el component**

Quan acabeu, importeu el component `Actions` i representeu-lo al `Tweet.js` així:

```vue
<!-- ... -->

<template>
  <div className="tweet">
    <ProfileImage image="user.image" />

    <div className="body">
      <div className="top">
        <User userData="user" />
        <Timestamp time="timestamp" />
      </div>

      <Message message="message" />
      <Actions />

<!-- ... -->
```

El component d' `Actions` no requereix cap accessori.

### Iteració 9 | Renderitza diversos `Tweet`

Un cop hàgiu acabat de refactoritzar el component `Tweet` , actualitzeu `App.vue` per mostrar tres components ``. Cada ``hauria de rebre un *objecte* de tweets separat del `tweetsArray` .

Un cop acabat, la vostra aplicació hauria de mostrar el contingut següent:

<details>

<summary> Clica per veure la imatge</summary>

![Exemple - Resultat final](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-frontend-vue/lab-vue-tweets-4.png)

</details>

<hr/>

**Feliç codificació!** :blue_heart: