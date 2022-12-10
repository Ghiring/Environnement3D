# Environnement3D

***

Le projet consiste en la modélisation d'un environnement 3D permettant à de jeunes enfants de s'initier au tir sportif tout en s'amusant. Les éléments sont modélisés via fusion 360 et implémentés dans A-frame sous HTML. Ce code sous-tend également diverses interactions. 

***

## I - Core :

Définition de la physique, pose du cadre de base et import des textures et des obj.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>A-Frame: click event and impulse</title>
    <!-- A-Frame JavaScript library -->
    <script src="https://aframe.io/releases/1.1.0/aframe.min.js"></script>
    <!-- A-Frame physics engine -->
    <script src="https://cdn.jsdelivr.net/gh/n5ro/aframe-physics-system@v4.0.1/dist/aframe-physics-system.min.js"></script>
    <script src="https://cdn.jsdelivr.net/gh/donmccurdy/aframe-extras@v6.1.1/dist/aframe-extras.min.js"></script>
    <script src="https://unpkg.com/aframe-event-set-component@3.0.3/dist/aframe-event-set-component.min.js"></script>
    <script src="https://cdn.jsdelivr.net/gh/n5ro/aframe-physics-system@v4.0.1/dist/aframe-physics-system.min.js"></script>
  </head>

  <body>
    <a-scene>
      <a-assets>
        <img
          id="mars"
          src="https://cdn.glitch.global/125fb933-64c6-4db3-acd0-e508938a10fa/mars.jpg?v=1668509189551"
        />
        <img id="place" src="place.jpg" />
        <img id="terre" src="terre.jpg" />
        <img
          id="solmars"
          src="https://cdn.glitch.global/125fb933-64c6-4db3-acd0-e508938a10fa/solmars.jpeg?v=1668509199134"
        />
        <img
          id="matostable"
          src="https://cdn.glitch.global/125fb933-64c6-4db3-acd0-e508938a10fa/matostable.jpg?v=1668509206745"
        />
        <a-asset-item
          id="cible"
          src="https://cdn.glitch.global/125fb933-64c6-4db3-acd0-e508938a10fa/cible.obj?v=1668509171431"
        ></a-asset-item>
        <a-asset-item
          id="pistolet"
          src="https://cdn.glitch.global/125fb933-64c6-4db3-acd0-e508938a10fa/pistolet.obj?v=1668509179771"
        >
        </a-asset-item>
        <a-asset-item
          id="stand1"
          src="https://cdn.glitch.global/125fb933-64c6-4db3-acd0-e508938a10fa/stand.obj?v=1669651123008"
        >
        </a-asset-item>
        <a-asset-item
          id="stand2"
          src="https://cdn.glitch.global/125fb933-64c6-4db3-acd0-e508938a10fa/stand.mtl?v=1669651130939"
        >
        </a-asset-item>
        <a-asset-item
          id="Arme"
          src="https://cdn.glitch.global/125fb933-64c6-4db3-acd0-e508938a10fa/Arme.obj?v=1670017132742"
        ></a-asset-item>
        <a-asset-item
          id="Pion"
          src="https://cdn.glitch.global/125fb933-64c6-4db3-acd0-e508938a10fa/Pion.obj?v=1670019071739"
        ></a-asset-item>
        <a-asset-item
          id="Fou"
          src="https://cdn.glitch.global/125fb933-64c6-4db3-acd0-e508938a10fa/Fou.obj?v=1670018869483"
        ></a-asset-item>
        <a-asset-item
          id="Table"
          src="https://cdn.glitch.global/125fb933-64c6-4db3-acd0-e508938a10fa/Tablee.obj?v=1670020535538"
        ></a-asset-item>
        <a-asset-item
          id="Roi"
          src="https://cdn.glitch.global/125fb933-64c6-4db3-acd0-e508938a10fa/Roi.obj?v=1670054993413"
        ></a-asset-item>
        <a-asset-item
          id="Tour"
          src="https://cdn.glitch.global/125fb933-64c6-4db3-acd0-e508938a10fa/Tour.obj?v=1670055417196"
        ></a-asset-item>
        <a-asset-item
          id="Coupe"
          src="https://cdn.glitch.global/125fb933-64c6-4db3-acd0-e508938a10fa/Coupe.obj?v=1670508456360"
        ></a-asset-item>
      </a-assets>
```
## II - Définition du premier niveau

Placement du sol et du stand de tir.

```html
      <a-plane
        position="0 0 -11.4893"
        rotation="-90 0 0"
        width="10"
        height="10"
        color="#7BC8A4"
        material="color: #775555"
        geometry=""
        scale="2 4 3"
        src="#solmars"
        repeat="4 4"
      >
        <a-obj-model
          src="#stand1"
          position="-2 0 0"
          scale="0.001 0.001 0.001"
          rotation="00 -90 -90"
          color="#242424"
        ></a-obj-model>
 ```
 
 <img src="https://github.com/Ghiring/Environnement3D/blob/main/Stand%20de%20tir/Stand%20de%20tir%20Aframe%201.png" height="500" width="700" >
 
 <img src="https://github.com/Ghiring/Environnement3D/blob/main/Stand%20de%20tir/Stand%20de%20tir%20Aframe%202.png" height="500" width="700" >
 
 <img src="https://github.com/Ghiring/Environnement3D/blob/main/Stand%20de%20tir/Stand%20de%20tir%20Aframe%203.png" height="500" width="700" >

 <img src="https://github.com/Ghiring/Environnement3D/blob/main/Stand%20de%20tir/Stand%20de%20tir%20Aframe%204.png" height="500" width="700" >
 
 Mise en place d'une sphère concernée par un event set click permettant de se téléporter au niveau suivant. La sphère porte la classe "links" de façon à pouvoir interragir avec le laser que nous défiront plus loin.
 
  ```html
 <a-sphere
          position="0.01096 4.39408 2.69616"
          class="links"
          material="ambientOcclusionMap: [object HTMLImageElement]; color: #bb1111; roughnessMap: [object HTMLImageElement]"
          geometry=""
          event-set__click="_event:click ; _target:#camera; position:28.9 3.5 1.5"
        ></a-sphere>
 ```
 
  <img src="https://github.com/Ghiring/Environnement3D/blob/main/Cible/Sphere%20de%20teleportation.jpg" height="500" width="500" >
 
 Mise en place de la table et du décor (pistolet, pièces d'échecs).
 
 ```html
 <a-obj-model
          src="#Arme"
          position="0.34046 -1.76657 1.04109"
          scale="0.001 0.001 0.001"
          material="color: #313030"
          obj-model=""
          rotation="-7.585961207532099 167.10199503431434 41.88493369744857"
        ></a-obj-model>
        <a-obj-model
          src="#Pion"
          position="1.27548 -1.79656 0.96925"
          scale="0.004 0.004 0.004"
          obj-model=""
          material="color: #fcfcfc	"
          rotation="90 0 0"
        ></a-obj-model>
        <a-obj-model
          src="#Fou"
          position="0.7513 -1.95899 0.9505"
          scale="0.004 0.004 0.004"
          obj-model=""
          material="color: #fcfcfc	"
          rotation="90 0 0"
        ></a-obj-model>
        <a-obj-model
          src="#Table"
          position="0.9 -1.4032 0.89621"
          scale="0.001 0.001 0.0015"
          obj-model=""
          material="color: #B49051	"
          rotation="0 90 90"
        ></a-obj-model>
        <a-obj-model
          src="#Roi"
          position="1.38316 -1.06336 0.94395"
          scale="0.004 0.004 0.004"
          obj-model=""
          material="color: #322a2a	"
          rotation="0 90 90"
        ></a-obj-model>
        <a-obj-model
          src="#Tour"
          position="0.87614 -0.88483 0.98427"
          scale="0.004 0.004 0.004"
          obj-model=""
          material="color: #322a2a	"
          rotation="0 90 90"
        ></a-obj-model>
 ```
 
 Import de la coupe signifiant la victoire après avoir atteint les 15 cibles. 
 
 ```html
 <a-obj-model
          src="#Coupe"
          position="48.92791 1.24269 2.3751"
          scale="0.004 0.004 0.004"
          obj-model=""
          material="color: #E8C605"
          metalness="0.3"
          rotation="90 0 0"
        ></a-obj-model>
 ```
 
 <img src="https://github.com/Ghiring/Environnement3D/blob/main/Coupe/Coupe%201.png" height="500" width="700" >

 <img src="https://github.com/Ghiring/Environnement3D/blob/main/Coupe/Coupe%202.png" height="500" width="700" >

 <img src="https://github.com/Ghiring/Environnement3D/blob/main/Coupe/Coupe%203.png" height="500" width="700" >
 
 <img src="https://github.com/Ghiring/Environnement3D/blob/main/Scene/Salle%20finale.jpg" height="500" width="700" >
 
 Import de la cible.
 
 ```html
 <a-obj-model
          src="#cible"
          position="0.01119 4.39782 1.21756"
          scale="0.002 0.001 0.001"
          material="color: #cfc4c4"
          obj-model=""
          rotation="-90 90 90.00021045914971"
        ></a-obj-model>
```

 <img src="https://github.com/Ghiring/Environnement3D/blob/main/Cible/Cible.jpg" height="500" width="700" >

Placement des cercles qui feront office de cible grâce à un event set click. Les cibles portent la classe "link" de façon à pouvoir être atteintes par le laser que nous définiront plus loin.

```html
<a-circle
          id="cible1"
          class="links"
          position="-1.18884 4.39408 1.2105"
          scale="0.21495 0.118 1"
          color="#050505"
          geometry=""
          rotation="90 0 0"
          event-set__click="_event: click; _target: #cible1; color: green"
        ></a-circle>
        <a-circle
          id="cible2"
          class="links"
          position="-0.60804 4.39408 1.2105"
          scale="0.21495 0.118 1"
          color="#050505"
          geometry=""
          rotation="90 0 0"
          event-set__click="_event: click; _target: #cible2; color: green"
        ></a-circle>
        <a-circle
          id="cible3"
          class="links"
          position="0.00356 4.39408 1.2105"
          scale="0.21495 0.118 1"
          color="#050505"
          geometry=""
          rotation="90 0 0"
          event-set__click="_event: click; _target: #cible3; color: green"
        ></a-circle>
        <a-circle
          id="cible4"
          class="links"
          position="0.59768 4.39408 1.2105"
          scale="0.21495 0.118 1"
          color="#050505"
          geometry=""
          rotation="90 0 0"
          event-set__click="_event: click; _target: #cible4; color: green"
        ></a-circle>
        <a-circle
          id="cible5"
          class="links"
          position="1.19399 4.39408 1.2105"
          scale="0.21495 0.118 1"
          color="#050505"
          geometry=""
          rotation="90 0 0"
          event-set__click="_event: click; _target: #cible5; color: green"
        ></a-circle>
```
 Placement des murs D et G.
 
 ```html
 <a-box
          id="mur gauche"
          position="-4.82095 1.30925 1.87231"
          rotation="0 0 -180"
          scale="0.245 7.28557 3.96505"
          material="color: #363433"
          geometry=""
          src="#matostable"
          repeat="4 4"
        >
        </a-box>
        <a-box
          id="mur droite"
          position="4.9 1.30925 1.87231"
          rotation="0 0 -180"
          scale="0.245 7.28557 3.96505"
          material="color: #363433"
          geometry=""
          src="#matostable"
          repeat="4 4"
        >
 ```
 
 ### Rendu du niveau 1 : 
 
  <img src="https://github.com/Ghiring/Environnement3D/blob/main/Scene/Niveau%201.jpg" height="500" width="700" >

***
***
***

Répétition de la structure de base pour ne niveau 2 avec l'ajout d'un obstacle mouvant venant obstruerle champ de vision en direction de la cible pour complexifier le tir. 

```html
<a-box
          id="mur TEST"
          position="0.17953 2.63783 1.06443"
          rotation="0 0 90"
          scale="0.245 1.92559 2.30152"
          material="vertexColors: face; color: #9a989a; emissive: #404040"
          geometry=""
          animation="property: position; from: -3.5 3.2 0.5; to: 4 3.2 0.5; dur: 1500; easing: easeInOutQuad; dir: alternate; loop: true"
        >
        </a-box>
```

### Rendu du niveau 2 : 

 <img src="https://github.com/Ghiring/Environnement3D/blob/main/Scene/Niveau%202A.jpg" height="500" width="700" >

 <img src="https://github.com/Ghiring/Environnement3D/blob/main/Scene/Niveau%202B.jpg" height="500" width="700" >

***
***
***

Répétition de la structure de base pour le niveau 3 avec l'ajout de la cible elle-même mouvante.

```html
<a-obj-model
          src="#cible"
          scale="0.002 0.001 0.001"
          material="color: #cfc4c4"
          obj-model=""
          rotation="-90 90 90.00021045914971"
          animation="property: position; from: -3.2 4.39 1.21; to: 3.2 4.39 1.21; dur: 3000; easing: easeInOutQuad; dir: alternate; loop: true"
        >
```

### Rendu du niveau 3 : 

 <img src="https://github.com/Ghiring/Environnement3D/blob/main/Scene/Niveau%203A.jpg" height="500" width="700" >
 
 <img src="https://github.com/Ghiring/Environnement3D/blob/main/Scene/Niveau%203B.jpg" height="500" width="700" >
 
***
***
***

Ajout d'un collide pour pouvoir saisir le pistolet.

```html
<script>
        // Add a collide event listener to the object with id="box1"
        document.querySelector("#Arme").addEventListener("collide", (e) => {
          /*
    e.detail.target.el is the #box1 element
    e.detail.body.el is the other object in collision
    */
          if (e.detail.body.el.id === "sphere1") {
            e.detail.target.el.setAttribute("visible", "false");
            e.detail.body.el.setAttribute("visible", "false");
          }
        });
      </script>
```

Enfermement de la caméra dans une entité afin de pouvoir la placer à différentes hauteurs et la téléporter grâce à l'event set click de la sphère. Liaison du pistolet à la manette. 

```html
<a-entity id="camera" position="-1.7 3.5 1.5">
        <a-camera  position="-1.3 3.5 1.5"> </a-camera>
        <a-entity
          id="rightHand"
          laser-controls=""
          raycaster="objects: .links; far: 1000 ; lineColor: red"
        >
          <a-obj-model
            src="#Arme"
            position="-0.07 -0.12 0"
            rotation="10.90404398279458 90.009244493076984 0.261136229522865"
            scale="0.0005 0.0005 0.0005"
            shadow="cast: true; receive: true"
          >
            <a-cursor></a-cursor>
          </a-obj-model>
```

<img src="https://github.com/Ghiring/Environnement3D/blob/main/Pistolet/Pistolet%20Aframe%201.png" height="500" width="700" >

<img src="https://github.com/Ghiring/Environnement3D/blob/main/Pistolet/Pistolet%20Aframe%202.png" height="500" width="850" >

<img src="https://github.com/Ghiring/Environnement3D/blob/main/Pistolet/Pistolet%20Aframe%203.png" height="500" width="700" >

<img src="https://github.com/Ghiring/Environnement3D/blob/main/Pistolet/Pistolet%20Aframe%204.png" height="500" width="700" >

<img src="https://github.com/Ghiring/Environnement3D/blob/main/Scene/Pistolet.jpg" height="500" width="700" >
