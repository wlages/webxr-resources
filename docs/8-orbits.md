---
title: Orbits
description: Step 8 - Moving earth and moon
order: 80
---

* sdfasdfs
{:toc}

# Moving Earth and Moon

In this step we will move the earth around the sun and the moon around the earth. We will also add spin for both.

We will translate each body along a circular trajectory on the plane X,Z. You can swap the planes to make different orbits.

Add the method below in the end of the file.

```javascript
function StepSimulation(earth, moon, ship) 
{
    return function()
    {
        var t = performance.now(); // Current time in ms

        //spin
        earth.rotationQuaternion = B.Quaternion.RotationAxis(B.Vector3.UpReadOnly, t*0.0001);
        moon.rotationQuaternion = B.Quaternion.RotationAxis(B.Vector3.UpReadOnly, t*0.001);

        // Earth orbit
        var er = 500;
        var es = 0.0001;
        earth.position = new B.Vector3(er*Math.cos(t*es), 0,er*Math.sin(t*es));

        // Moon orbit
        var mr = 30;
        var ms = 0.001;
        moon.position = new B.Vector3(mr*Math.cos(t*ms),0,  mr*Math.sin(t*ms));
        moon.position = moon.position.addInPlace(earth.position);

    }
}

```

Since we will update the position in the orbit for every frame, we need to call the "StepSimulation" in a different way. Add the line below in "CreateScene", right before "return scene;" line.

```javascript
//register the simulation method
scene.registerBeforeRender(StepSimulation (earth, moon,ship));
 
```

This lines registers the method with BabylonJS, so that it is called before every frame is rendered. Investigate the result in the PC and in the headset to make sure the orbits are working properly.

>> If you are running in a smartphone and the earth and moon are very dark, you may need to switch the planet material creation from "CreateMaterial" to "CreateMaterialStandard" in the second line of "CreatePlanet" method.


# Experiment

Play with different rotation speeds, orbit radius, and translation speeds. You can also experiment different orbit planes by swapping the components in the position Vector3.


Here is the [complete project for this step](https://playground.babylonjs.com/#EQHLXS#7).