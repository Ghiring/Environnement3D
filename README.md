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
