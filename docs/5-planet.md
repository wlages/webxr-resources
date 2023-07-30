---
title: Planets
description: Step 5 - Creating planets
order: 50
---

* sdfasdfs
{:toc}

# Creating a planet

To creat a planet we will have do the following:
1. Create a sphere with the appropriate size 
2. Create a material with the texture
3. Load a mesh for a ring (for ring planets!)

Add the method below after in the end of the current file.

```javascript
unction CreatePlanet(name,size,texture,hasRing,scene)
{
    const planet = B.MeshBuilder.CreateSphere(name, {diameter: size, segments: 32}, scene);
    planet.material= CreateMaterial(name+"_material",serverContentURL+texture,scene);

    if(hasRing)
    {
        B.SceneLoader.ImportMesh("",serverContentURL+"models/", "ring1.obj", scene, function Loaded(meshes){
            
        console.log("Mesh loaded:", meshes);
        const ring = meshes[0];
        if(ring == null)
            console.log("Could not find file");
        ring.scaling=new B.Vector3(10,10,10);
        ring.material= CreateMaterial("ringMat",serverContentURL+"textures/planets/Saturn_Rings.png",scene);
        ring.parent = planet;
             });
    }

    return planet;
}

```
Now we need to call the method "CreatePlanet" from the CreateScene, so that it works. Before "return scene", insert the line below:

```javascript
var earth = CreatePlanet("earth",10,"textures/planets/earth.jpg",false,scene);
  
```

We're creating a planet named 'earth', with size 10, using earth textures, and false for rings. Notice that because our scene does not have a light source (star) it will look dark. We will create a star in the next step.


Here is the [complete project for this step](https://playground.babylonjs.com/#EQHLXS#4).