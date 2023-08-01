---
title: Ship
description: Step 9 - Moving ship in orbit
order: 90
---

* sdfasdfs
{:toc}

# Moving the Ship


>*Caution* you may find that this perspective very unusual and that  it can make you dizzy. If you feel too uncomfortable after you try, you can stop the ship from moving by removing call to MoveShip (last step).

In this step we will move the ship around the earth. We want it to feel like a space station in orbit, so we will need to do a few thing differently than the moon.

We will need to:
1. Calculate the circular trajectory around the earth
2. Compute a reference frame for the ship
3. Rotate the camera so that the earth is down
4. Rotate the camera to be perpendicular to the earth surface

Add the method below in the end of the file.

```javascript
function MoveShip(earth, ship,t)
{
    // Ship orbit
    var sr = 6.2;
    var ss = 0.0002;
    ship.position = new B.Vector3(sr*Math.cos(t*ss), 0,sr*Math.sin(t*ss));
    ship.position = ship.position.addInPlace(earth.position);
        
    var gravityVector = earth.position.clone();
    gravityVector.subtractInPlace(ship.position);

    //t = (c_ship-c_earth)- (p_ship - p_earth)
    var tangentVector = ship.position.clone();
    tangentVector.subtractInPlace(previousPos);
    tangentVector.subtractInPlace(earth.position);
    tangentVector = B.Vector3.Normalize(tangentVector);
    var shipRight = B.Vector3.Cross(tangentVector,gravityVector);

    var downRotation =  B.Quaternion.RotationAxis(shipRight,t*ss);
    var camRotation = B.Quaternion.RotationAxis(tangentVector,-Math.PI/2);
     
    ship.rotationQuaternion = camRotation.multiply(downRotation);
    previousPos.copyFrom(ship.position.subtract(earth.position));

}

```

We will also need to make a few changes on "CreateScene" to:

1. Initialize the rotation for the camera
2. Set the desktop camera to look at earth (not required but nicer)
3. Reset the XR camera to zero
4. Make the XR camera follow the ship
5. Initialize the ship position

Add the following lines in "CreateScene", before the "return scene;" line:

```javascript
    scene.activeCamera.rotationQuaternion = BABYLON.Quaternion.FromEulerVector(new BABYLON.Vector3(0,0,0));
    scene.activeCamera.target = earth;

   xr.baseExperience.onStateChangedObservable.add((state) => {
        xr.baseExperience.camera.position=new B.Vector3.Zero;
        xr.baseExperience.camera.parent = ship;
    });

    previousPos = new B.Vector3.Zero;
```

Finally, since we will update the position of the ship after the earth has moved, we will call the "MoveShip" method at the end of "StepSimulation". Find the last line of "StepSimulation" (should be "moon.position = moon.position.addInPlace(earth.position);") and add after:

```javascript
MoveShip(earth, ship,t);
```

# Experiment

Play with the ship orbit radius (how far you are above surface), rotation speed (can you make it geosynchronous?)


Here is the [complete project for this step](https://playground.babylonjs.com/#EQHLXS#7).