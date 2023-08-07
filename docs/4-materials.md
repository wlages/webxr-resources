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

The method above uses Physically Based Rendering (PBR) which aims to emulate real-life materials. The properties are controlled by adjusting the metallic and roughness component. A mirror would have metallic = 1 and roughness = 0, reflecting our skybox as a very polished metal. PBR creates very realistic materials, but can be unavailable in certain platforms. 

Another option is to create a standard material. If you are running on a smartphone this may be a good option.

```javascript
function CreateMaterialStandard(name, file, scene) 
{
    var mat = new B.StandardMaterial(name+"_material", scene);
    mat.diffuseTexture = new B.Texture(file, scene);
    mat.ambientColor = new BABYLON.Color3(0.5, 0.5, 0.5);

    if(mat.baseTexture == null)
        console.log("Could not find file!");
    else
        console.log("Loaded" + mat.baseTexture);

    return mat;

}

```

Ambient color will be used to light the areas which are not directly iluminated by the sun light. In order for this to work, we will need to add the line below "ConfigureScene", after the last "imageProcessingConfiguration" call:

```javascript
scene.ambientColor = new BABYLON.Color3(0.5, 0.5, 0.5);
```

We will use one of these two method when we create planets.  


Here is the [complete project for this step](https://playground.babylonjs.com/#EQHLXS#3).