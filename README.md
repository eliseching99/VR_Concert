WebVR Starter Kit: Make Your Own Planetarium ✨FANCY Edition
=================
In our [first project](https://glitch.com/~starter-aframe) we made a simple solar system. Now let's upgrade things to show off some of A-Frame's capabilities and make our solar system more realistic. 

A-Frame is an easy way to build your own WebVR (Web Virtual Reality) scenes. You don't need to install anything and scenes can be made with HTML. Our starter projects have code that can be easily [remixed](https://glitch.com/help/remix/) to create their own scenes. 

This is the second of [four projects in our WebVR starter kit](https://glitch.com/@glitch/web-vr-starter-kit). The other projects include:
* 1) 🌎[starter-aframe](https://glitch.com/~starter-aframe): Get started with your first A-Frame scene
* 3) 💞[starter-aframe-animated](https://glitch.com/~starter-aframe-animated): Add animations and lighting
* 4) 🌌[starter-aframe-deep-space](https://glitch.com/~starter-aframe-deep-space): Create a totally different experience with custom planets

## 🔑 Key Tool: The A-Frame Inspector
We recommend you use the [A-Frame inspector](https://aframe.io/docs/0.8.0/introduction/visual-inspector-and-dev-tools.html), a powerful tool that comes with A-Frame and allows you to explore and modify the code of your scene visually. Open it by going to your scene and pressing `<ctrl> + <alt> + i` on Windows or `<ctrl> + <option> + i` on Mac. 

![the A-Frame inspector](https://cdn.glitch.com/77ecffe2-9e20-4c26-b5d7-fd6c9e4a0d6e%2Faframe-inspector.png?1541721410592)

## 📓 Our Project/Code
* README.md - project info/instructions
* index.html - this is our scene, click "Show" to see it
* assets - a folder of goodies like models (3D shapes like asteroids) and images. [Check this out to learn how it works.](https://glitch.com/help/how-do-i/)

## 🚀 Exploring The Scene
In the browser you can click and drag your cursor to rotate your view of the scene. You can use your arrow keys to move left, right, backwards, and forwards. On a mobile device you can tilt the screen to rotate the view. 

In VR mode moving your head should change the view of the scene. 

![Exploring the scene](https://cdn.glitch.com/77ecffe2-9e20-4c26-b5d7-fd6c9e4a0d6e%2Fplanetarium-fancy-compressed.gif?1541719443795)

## 💻 What the code does
### 🔳 Adding Components
A-Frame does many cool things, but you can also extend it with custom components. There are many out there and using them is as simple as adding them in a script tag. Here we use [aframe-star-system](https://www.npmjs.com/package/aframe-star-system-component) to add a starry background to our scene. 

```
<!-- add it -->
<script src="https://unpkg.com/aframe-star-system-component@1.0.0/index.js"></script> 

```

```
<!-- use it -->
<a-entity star-system="count: 1000; radius: 250; depth: 0"></a-entity>   
```

Here are some other popular components you can try out:
* [A-Frame Extras](https://github.com/donmccurdy/aframe-extras)
* [aframe-mountain](https://www.npmjs.com/package/aframe-mountain-component)
* [aframe-environment](hhttps://github.com/feiss/aframe-environment-component)

### 🖼 Assets
The [`<a-assets>`](https://aframe.io/docs/0.8.0/core/asset-management-system.html) section is a place to keep images, audio, and 3D models organized. A-Frame automatically preloads them to make our scenes faster. 

Here is an example. Let's say we want to add a realistic texture to Jupiter.
1. Download the texture from [Planet Pixel Emporium](http://planetpixelemporium.com/)
2. [Add the asset to your Glitch assets](https://glitch.com/help/how-do-i/)
3. Copy the URL - it should look something like this `https://cdn.glitch.com/d558c128-2ed0-4284-a0da-4d18b9163ad6%2Fjupitermap.jpg?1541101634813`
![how to copy the url](https://cdn.glitch.com/77ecffe2-9e20-4c26-b5d7-fd6c9e4a0d6e%2Fcopy-url.png?1541716904168)
4. Create a new asset tag (you can copy from those already included). Give it any `id` you want but it should be something descriptive and not include a space. Crossorigin is just used to prevent certain errors– [read more about it here](https://developer.mozilla.org/en-US/docs/Web/HTML/CORS_settings_attributes)
```
<img id="jupiter-texture" src="" crossorigin="anonymous">

```
5. Paste the URL from step 3 into the `src` attribute.
```
<img id="jupiter-texture" src="https://cdn.glitch.com/d558c128-2ed0-4284-a0da-4d18b9163ad6%2Fjupitermap.jpg?1541101634813" crossorigin="anonymous">

```
6. Woohoo, now you can just use it anywhere you want just by adding `#jupiter-texture` to the `src` attribute of the sphere. A major advantage is you can use it multiple times, so if you want 2 Jupiters, it's easy. You can even use the  `color` attribute with the `src` attribute to give it a tint.

```
<a-sphere id="jupiter" position="0 0 24" radius="2.5" src="#jupiter-texture"></a-sphere>

<a-sphere id="anotherJupiter" position="0 0 22" radius="3" src="#jupiter-texture"></a-sphere>

<a-sphere id="blueJupiter" position="0 0 22" radius="2" src="#jupiter-texture" color="blue"></a-sphere>
```

### ☄️ Models
You could add asteroids by using a bunch of spheres, but it would take you some time and asteroids don't really seem like a bunch of spheres anyway. They are more like giant rocks. So here we used a model instead. 

You add models in a similar way except the tags are different. Here is how you add a model to your assets:
```
<a-asset-item id="asteroids" response-type="arraybuffer"  src="https://cdn.glitch.com/d558c128-2ed0-4284-a0da-4d18b9163ad6%2Fasteroides.glb?1541106805090"></a-asset-item>

```
And here is an example of using it:
```
<a-entity id="asteroid-belt" gltf-model="#asteroids" scale="2.1 2.1 2.1" position="0 0 0"></a-entity>

```

The best type of 3D models to use on Glitch are `gltf` models in the `glb` format. The glb format just means all its assets have been bundled into a single easy to use file. 

Use the [glb-packer](https://glb-packer.glitch.me) on Glitch to convert glTF to GLB. Another option for `OBJ` and other types of models is [the blackthread converter](https://blackthread.io/gltf-converter/)

Some places to download models for free include:
* [Google Poly](https://poly.google.com/)
* [Clara.io](https://clara.io)
* [SketchFab](https://sketchfab.com/mozillareality)

There are tons of ways to make your own models, but here are a few that are fun for beginners:
* [Supercraft](https://supermedium.com/supercraft/)
* [Google Blocks](https://vr.google.com/blocks/)
* [MagicaVoxel](https://aframe.io/docs/0.8.0/guides/building-with-magicavoxel.html)

### 🔲 Entity-Component System 
We've changed the `<a-torus>` rings to rings made with `<a-entity>`. In the last starter we used `<a-entity>` just for wrapping things together, but here we show how it can be used as almost anything by adding **components** to it. Adding a component is the same as adding an attribute, you just use the component's name. A-Frame contains many components and you can also add custom ones like the `star-system` we added before. Here we add the `geometry` component which turns it into a torus. 

The attribute `geometry` also has multiple attributes inside of it like `radius`. They are seperated by semicolons. The reason we're doing this? It gives us a little bit more control over how our scene elements look and behave. 

Curious to know more? [Check out the official documentation](https://aframe.io/docs/0.8.0/introduction/entity-component-system.html). 

### 📸 Camera
All A-Frame scenes have a default [camera](https://aframe.io/docs/0.8.0/components/camera.html#sidebar). A camera is how the scene is viewed. If you place the camera higher for example you'll start out seeing the planets from higher. To override the default camera add your own. This one has a camera that's placed higher and rotated a bit. In addition it has some attributes like  [`wasd-controls`](https://aframe.io/docs/0.8.0/components/wasd-controls.html) which allows you to navigate the scene with arrow keys or the w, a, s, and d keys on your keyboard. 

## 💫 Remix me!

[Remix](https://glitch.com/edit/#!/remix/starter-aframe-fancy) this to make your own planetarium. Some fun ideas:
* Change the camera position
* Check out the assets folder for some other textures and apply them to planets to make your own custom planets
* Remove all the planets except Earth and the Moon, place them in the middle and focus the camera on them, add the the space shuttle model from the assets folder to the scene to create a moon mission!


# 🛰 Bonus Starters
* [Volcano](https://a-volcano.glitch.me/) a volcano scene with aframe-environment
* [Vaporwave](https://glitch.com/~a-wave) with aframe-environment and cool text
* [Photo Tour](https://glitch.com/~a-photo-tour) using a panoramic photo from Google Streetview for both a texture and the "sky"

## 🌟 What's next?
Check out the next starter project in the series 💞[starter-aframe-animation](https://glitch.com/~starter-aframe-animated) to make your planets actually rotate and orbit! 

# Credits
* [Planet Pixel Emporium](http://planetpixelemporium.com/)
* [Moon texture](https://commons.wikimedia.org/wiki/File:Moonmap_from_clementine_data.png)
* [Other planet textures](http://www.texturesforplanets.com/texture-packs.shtml)
* [Asteroid texture](https://commons.wikimedia.org/wiki/File:Generic_Celestia_asteroid_texture.jpg)
* [Extra asteroids model](https://poly.google.com/view/9k18F9bT43N)
* [Space Shuttle model](https://poly.google.com/view/djxolbz_CYC)