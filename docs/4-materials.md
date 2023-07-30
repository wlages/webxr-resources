---
title: Materials
description: Step 4 - Creating materials for planets
order: 40
---

* sdfasdfs
{:toc}

# Creating Materials

Materials determine how the light shine on objects. It includes diffuse reflection and specular reflection. If they vary along the object, they can be encoded into textures, which are then mapped over the surface of the object.

Let's write a method to create materials and textures for our scene. Because we're writing a generic method, we will need to pass the specific name and texture file we want to use. 

Add the method below after in the end of the current file.

```javascript
function CreateMaterial(name, file, scene) 
{
    var mat = new B.PBRMetallicRoughnessMaterial(name, scene);
    mat.metallic = 0;
    mat.roughness = 1.0;
    mat.baseTexture = new B.Texture(file, scene);

    if(mat.baseTexture == null)
        console.log("Could not find file!");
    else
        console.log("Loaded" + mat.baseTexture);

    return mat;
}

```
We will use this method when we create planets.  


Here is the [complete project for this step](https://playground.babylonjs.com/#EQHLXS#3).