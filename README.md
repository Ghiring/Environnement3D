# Environnement3D

***

Le projet consiste en la modélisation d'un environnement 3D permettant à de jeunes enfants de s'initier au tir sportif tout en s'amusant. Les éléments sont modélisés via fusion 360 et implémentés dans A-frame sous HTML. Ce code sous-tend également diverses interactions. 

***

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
 
 Mise en place d'une sphère concernée par un event set click permettant de se téléporter au niveau suivant. 
 
  ```html
 <a-sphere
          position="0.01096 4.39408 2.69616"
          class="links"
          material="ambientOcclusionMap: [object HTMLImageElement]; color: #bb1111; roughnessMap: [object HTMLImageElement]"
          geometry=""
          event-set__click="_event:click ; _target:#camera; position:28.9 3.5 1.5"
        ></a-sphere>
 ```
 
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
 
 
