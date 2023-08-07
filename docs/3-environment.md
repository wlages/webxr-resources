---
title: Background
description: Step 3 - Configuring Camera and Background
order: 30
---

* sdfasdfs
{:toc}

# Configure Scene

Let's write a method to configure our scene. We want it to
1. Load a background skybox
2. Add a camera for us to inspect the scene
3. Configure background clear parameters

Add the method below after in the end of the current file.

```javascript
function ConfigureScene(scene)
{
    scene.clearColor = new B.Color4(0.02, 0.02, 0.02, 1.0);
    scene.imageProcessingConfiguration.contrast = 1.6;
    scene.imageProcessingConfiguration.exposure = 0.6;
    scene.imageProcessingConfiguration.toneMappingEnabled = true;
    
    //Adding an Arc Rotate Camera
   var camera = new B.ArcRotateCamera("Camera", 0, 0.8, 100, BABYLON.Vector3.Zero(), scene);
  camera.attachControl(canvas, false);
  
    var hdrTexture = B.CubeTexture.CreateFromPrefilteredData(serverContentURL+"textures/skybox/skyEnvHDR.dds", scene);
   hdrTexture.gammaSpace = false;
   scene.createDefaultSkybox(hdrTexture, true, 10000);

}

```
Now we need to call the method "ConfigureScene" from the CreateScene, so that it works. We need to call it after we create the new scene. Modify your createScene to insert the ConfigureScene call as shown below after "var scene = new B.Scene(engine);"  

```javascript
    ConfigureScene(scene); 
```

## Experiment

There are a few skyboxes ready for you to test. Just replace the file name in the CubeTexture creation to the one you want:

-blue-greenEnvHDR.dds
-complexEnvHDR.dds
-fuzyEnvHDR.dds
-orangeEnvHDR.dds
-purpleEnvHDR.dds
-redEnvHDR.dds
-yellowEnvHDR.dds
-skyEnvHDR.dds


Here is the [complete project for this step](https://playground.babylonjs.com/#EQHLXS#2).

