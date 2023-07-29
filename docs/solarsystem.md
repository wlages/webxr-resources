---
title: Solar System
description: How to build online XR applications!
---

* sdfasdfs
{:toc}

# Solar System


![LibDoc layout](/record.gif)


 [bkbkb]({{site.url}}{{site.baseurl}}/iframe.html?src={{site.url}}{{site.baseurl}}/sphere)

```javascript
        const createScene = function () {
            // Creates a basic Babylon Scene object
            const scene = new BABYLON.Scene(engine);
            // Creates and positions a free camera
            const camera = new BABYLON.FreeCamera("camera1", 
                new BABYLON.Vector3(0, 5, -10), scene);
            // Targets the camera to scene origin
            camera.setTarget(BABYLON.Vector3.Zero());
            // This attaches the camera to the canvas
            camera.attachControl(canvas, true);
            // Creates a light, aiming 0,1,0 - to the sky
            const light = new BABYLON.HemisphericLight("light", 
                new BABYLON.Vector3(0, 1, 0), scene);
            // Dim the light a small amount - 0 to 1
            light.intensity = 0.7;
            // Built-in 'sphere' shape.
            const sphere = BABYLON.MeshBuilder.CreateSphere("sphere", 
                {diameter: 2, segments: 32}, scene);
            // Move the sphere upward 1/2 its height
            sphere.position.y = 1;
            // Built-in 'ground' shape.
            const ground = BABYLON.MeshBuilder.CreateGround("ground", 
                {width: 6, height: 6}, scene);
            return scene;
        };
        const scene = createScene(); //Call the createScene function
        // Register a render loop to repeatedly render the scene
        engine.runRenderLoop(function () {
                scene.render();
        });

```

[Babylon.js](https://www.babylonjs.com/) | 
[Playground](https://playground.babylonjs.com/#F41V6N) | 
[Docs](https://doc.babylonjs.com/features/featuresDeepDive/webXR/introToWebXR)

Babylon.js is a real time 3D engine using a JavaScript library for displaying 3D graphics in a web browser via HTML5. The source code is available on GitHub and distributed under the Apache License 2.0.


## Features

* **<sup>New</sup> physics**<br> through a special new WASM plugin partnered with a complete overhaul of the Babylon.js Physics API<br><br>
* **Node Material Editor**<br> You can edit advanced material types and create shaders visually throught the [material editor](https://nme.babylonjs.com/)<br><br>
* **Gem free, plugin free** <br>LibDoc runs without any Gem nor plugin.<br><br>


## Steps

1. Play with the playground [here](https://playground.babylonjs.com/#2KRNG9)
2. Test the scripts in VR 
    * Copy the link with QR Code 
    * You can also type in the browser *https://playground.babylonjs.com/#F41V6N*
3. Do each of the exercises
    * `Solar system` <br>Sun, earth, and moon
    * `Lunar Lander` <br> 
    * `title` <br>Title of the documentation
    * `description` <br>Description of your documentation project
4. Profit!:
    * Learn more about VR

## Online

![Github.dev](https://olivier3lanc.github.io/Jekyll-LibDoc/assets/libdoc/img/libdoc-edit-online.webp)


## Credits

This material was based on:
