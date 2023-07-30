---
title: WebXR
description: Step 2 - Activate WebXR
order: 20
---

* adsasd
{:toc}


# Create Scene in XR

Let's start a new babylonJS in the playground. Follow this [link](https://playground.babylonjs.com/) to create project with a sphere and a plane.

Delete all the code and replace by this:

```javascript
var B = BABYLON; 
var serverContentURL ="https://raw.githubusercontent.com/wlages/webxr-resources/main/docs/"
var previousPos;

var CreateScene = async function () 
{
    //Create VR scene
    var scene = new B.Scene(engine);
    const xr = await scene.createDefaultXRExperienceAsync({});
    
    
     return scene;
};
```

The first lines are some utility to make it easier for us later. The most important lines are these:

```javascript
var scene = new  B.Scene(engine);
const xr = await scene.createDefaultXRExperienceAsync({});
```

Where we create a Babylon scene and a default XR experience.

Here is the [complete project for this step](https://playground.babylonjs.com/#EQHLXS#1).