---
title: Satellites
description: Step 7 - Creating satellites
order: 70
---

* sdfasdfs
{:toc}

# Creating Satellites

In this step we will create a moon and a invisible ship, which we will orbit the earth later.

Since we already created a method for planets, creating a moon is quite easy. Just add the line below in the "CreateScene" method, after the line creating the sun.

```javascript
var moon = CreatePlanet("moon",5,"textures/planets/moon.jpg",true,scene);
```

Notice that our moon has a ring. If you don't like you can change it to "false". Check that the moon has been created inside the 'earth'!

For the ship we will create only a Node, meaning that it has no visuals but we can use it move our camera. Add the lines below in "CreateScene", after the "CreatePlanet" line.

```javascript
var ship = new B.TransformNode("ship", scene);
    ship.rotationQuaternion = new B.Quaternion.Identity; //required because it does not exist by default
```

The last line initializes the rotation for the ship. 

Here is the [complete project for this step](https://playground.babylonjs.com/#EQHLXS#6).