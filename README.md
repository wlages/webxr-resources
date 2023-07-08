# webxr-resources

To load in Babylon.js use *raw.githubusercontent.com/user/repo-name/branch/path*

For textures:
```javascript
 // Apply a texture to the sphere
    var earthMaterial = new BABYLON.StandardMaterial("earthMaterial", scene);
    earthMaterial.diffuseTexture = new BABYLON.Texture("https://raw.githubusercontent.com/wlages/webxr-resources/main//textures/ear0xuu2.jpg", scene);
    sphere.material = earthMaterial;
