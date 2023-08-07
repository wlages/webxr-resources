---
title: Stars
description: Step 6 - Creating a star
order: 60
---

* sdfasdfs
{:toc}

# Creating a Star

To create we will do the following:
1. Create a sphere with appropriate size
2. Configure a special type of material that does not receive shadows
3. Add a light source to the center of the star

Add the method below after in the end of the current file.

```javascript
function CreateStar(name,size,texture,color,scene)
{
    star = B.MeshBuilder.CreateSphere(name, {diameter: size, segments: 32}, scene);
    var material = new B.StandardMaterial(name+"_material", scene);
    material.diffuseTexture = new B.Texture(serverContentURL+texture, scene);
    material.emissiveColor = new BABYLON.Color3(1, 1, 1);
    star.material = material;
    star.position = new B.Vector3.Zero;

    // Point Light
    var light = new B.PointLight(name +"_light", new B.Vector3.Zero, scene);
    light.diffuse = color;
    light.specular = new BABYLON.Color3(1, 1, 1);
    light.intensity = 2000000.5;
    light.parent = star;

    return star;

}

```

There are two colors with fixed values in this method. The first one sets the start material emmissive color and the second the light specular color. The specular is set to (1,1,1) which is OK if you are using the PBRMaterial. If you are using the StandarMaterial and there is bright spot on your planets, you might want to reduce it closer to (0,0,0).

Now we need to call the method "CreateStar" from the CreateScene, so that it works. Modify your createScene to insert the line below after the line creating the earth.

```javascript
var sun = CreateStar("sun",50,"textures/planets/sun.jpg",new BABYLON.Color3(0.87, 0.67, 0.34),scene);
  
```

Notice that for the colors we're using BABYLON instead of just B. This is because the Playground recognizes it and shows a little square for color pickup, in case you want and easy way to adjust the colors. 

You will also note that the planet has disappeared. In fact, it is inside the sun because they were all created in the same location. If you zoom in with the scroll wheel on the Playground window in your PC you can peek inside and see the planet there.

# Experiment

Play with different light colors and size for the sun.

Here is the [complete project for this step](https://playground.babylonjs.com/#EQHLXS#5).