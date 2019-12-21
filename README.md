# Let's build an augmented reality (AR) web app!

_These are the instructor notes for the workshop. They also contain useful links for the participants. The accompanying code can be found at <https://repl.it/@Teebusch/arworkshop>. There is a file with a minimal example for each of the eight lectures._

## Table of Contents
- [Introduction and Setup](#introduction-and-setup)
- [0 - Getting started](#0---getting-started)
- [1 - Add and style 3D primitives](#1---add-and-style-3d-primitives)
- [2 - Use assets](#2---use-assets)
- [3 - Add text and style it](#3---add-text-and-style-it)
- [4 - Expand aframe with components](#4---expand-aframe-with-components)
- [5 - Animation](#5---animation)
- [6 - Interactivity](#6---interactivity)
- [7 - Turning the scene into AR](#7---turning-the-scene-into-ar)
- [8 - Binding data to A-Frame objects](#8---binding-data-to-a-frame-objects)
- [Mini-Hackathon](#mini-hackathon)
- [Sources & Further Reading](#sources--further-reading)


## In this workshop you will learn how to...

- Use A-Frame to create 3D scenes for browser-based VR and AR
- Add and style text, simple 3D shapes, and pre-created 3D models
- Add animation and interactivity
- Turn an A-frame scene into an AR app
- Use AR markers to anchor AR objects in the real world
- Use QR codes to make accessing your app easy
- Learn how to bind data to A-Frame objects to create data-driven AR experiences
- Get creative and build the AR app of your (humble) dreams

## Introduction and Setup

- Why are you here?
- Inspiration: Some cool examples of AR
- What are we going to build today? An VR/AR greeting card! (see `card1.html` `card2.html`)

##### Exercise 

- Create account at repl.it, fork the [project template](https://repl.it/@Teebusch/arworkshop), change the name. Reload the page once (Press <kbd>F5</kbd>).
- Enter your project URL in the [Google sheet](https://docs.google.com/spreadsheets/d/1CForyLlUKzzmZNsQG0JXaGE289IyUQnhjvO8tkS7vmw/edit?usp=sharing).
- Open `index.html`, write your code in here.
- Pass around the example greeting card, try to use it with your phone or webcam.

##### Instructor

- Demonstrate final output (greeting card)
- Turn links from [Google sheet](https://docs.google.com/spreadsheets/d/1CForyLlUKzzmZNsQG0JXaGE289IyUQnhjvO8tkS7vmw/edit?usp=sharing) into QR codes, print and give to participants 
- give greeting card templates to participants
- give AR markers to participants (Hiro marker + 3 matrix markers, see pdf files in `ar-markers/` directory)

##### Help

- `README.md` (this file)
- [Slides](https://docs.google.com/presentation/d/1w6RXi930NecEbSmyv7L5u3LIiuqUiUfcP-Kfew72AvU/edit?usp=sharing)


-------------------------------------------------------------------------------

## 0 - Getting started

- Intro to [A-Frame](https://aframe.io/)
- Have a look at the A-Frame website and the docs (the docs are great!)
- Be aware: AFrame is actively being developed. Some tutorials use deprecated code. Best to always look at the docs first!
- where to find help (docs, example files in the repl)
- rundown of A-frame boilerplate
- add a pink box with `<a-box color="hotpink"></a-box>`

##### Exercise 

- Add a box with a color of your choice.
- Open the app on the phone. Is it working for everyone?

##### Help

- `00-getstarted.html`
- [A-Frame website](https://aframe.io/)

-------------------------------------------------------------------------------

## 1 - Add and style 3D primitives

- What are A-frame primitives?
- make and modify primitives
  - example: box, sphere, plane, ...
  - see [documentation](https://aframe.io/docs/0.9.0/introduction/html-and-primitives.html) for all primitives
  - change position, rotation, scale with `position="x y z"` `rotation="x y z"` `scale="x y z"`
  - understanding the A-Frame xzy coordinate system
- special primitive `<a-sky>` (note: sky is normally used with a picture. For single color background, and better performance, use `<a-scene background="color:...">`)
- use `<a-entity>` as a container - put shapes in entity to rotate, move and scale them as a whole
- explain entity-component system and show how an entity can become anything by rewriting a primitive as an entity.
- Open developer console to show the HTML in the DOM
- Open A-Frame inspector (Mac: <kbd>Ctrl</kbd> + <kbd>Option</kbd> + ,<kbd>i</kbd>; Windows & Ubuntu: <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + ,<kbd>i</kbd>) and use it to adjust objects interactively
- copy modifies entity html to clipboard to modify code

##### Exercise

- make a snowman using A-frame primitives. Use the Inspector to help you place the elements.
- Put everything into an entity to move it around more easily
- Position and scale the entire thing so that the user can see it when they open the app.
- _Advanced:_ rewrite a primitive into an entity by making an entity with a geometry component

##### Instructor

- Provide VR goggle so that scene can be tested in 3D. make a simple website that links everyone's projects and open it with the goggle browser

##### Help

- `01-primitives.html`
- [docs for primitives](https://aframe.io/docs/0.9.0/introduction/html-and-primitives.html)
- [docs for geometry component](https://aframe.io/docs/0.9.0/components/geometry.html)
- [docs for entity-component system](https://aframe.io/docs/0.9.0/introduction/entity-component-system.html)
- [docs for visual inspector](https://aframe.io/docs/0.9.0/introduction/visual-inspector-and-dev-tools.html)

-------------------------------------------------------------------------------

## 2 - Use assets 

- Assets can be textures, pre-created 3D objects, music...
- add images as assets and use them as textures for primitives
- example: add 360 degree image as sky, add a snow texture to the ground.
- **Tip:** For the best 360 degree experience search for ["equirectangular" panorama images](https://www.flickr.com/search/?license=2%2C3%2C4%2C5%2C6%2C9&text=equirectangular).
- add pre-created models as assets to the scene.
- what are gltf models and where to find them?
  - <https://poly.google.com>
  - <https://sketchfab.com>
  - <https://archive3d.net/>
  - <https://turbosquid.com>
  - <https://3dwarehouse.sketchup.com/> 
  - <https://clara.io/>
- or make your own models
  - [Blender](https://www.blender.org)
  - [MagicaVoxel](https://ephtracy.github.io/index.html?page=mv_main)
  - [Supercraft](https://supermedium.com/supercraft/)
- Want to use other 3d model formats with A-frame? See the docs.
- **Tip:** use models in "low poly" style to keep the app performant
- Example: include hat and present in the scene and scale it properly.
- we will see how to add sound assets later, because that requires user interaction to work properly

##### Exercise
- Add the hat and present to the snowman (remember you can use the editor to help placing and scaling them)
- Find and include another model you like. Perhaps add a christmas tree.

##### Help

- `02-assets.html`
- [Asset management system docs](<https://aframe.io/docs/0.9.0/core/asset-management-system.html>)
- [docs for obj-model component](<https://aframe.io/docs/0.9.0/primitives/a-obj-model.html>)
- [docs for a-img primitive](<https://aframe.io/docs/0.9.0/primitives/a-image.html>)
- [equirectangular panorama images with CC license on Flickr](https://www.flickr.com/search/?license=2%2C3%2C4%2C5%2C6%2C9&text=equirectangular)

-------------------------------------------------------------------------------

## 3 - Add text and style it

- add a basic text primitive
- adjust the text in inspector
- change text color, font family, size, anchor, align, baseline, wrap, width & height

##### Exercise 

- Add a greeting text that uses different size, color, etc.. change it to something you like. 
- Make sure to use entities so that you can scale and move all the parts at the same time

**Help:**

- `03-text.html`
- [docs for text primitive](https://aframe.io/docs/0.9.0/components/text.html)

-------------------------------------------------------------------------------

## 4 - Expand aframe with components

- You can find many components written by others at the [A-Frame registry](https://aframe.io/aframe-registry/) or on [NPM](<https://www.npmjs.com/search?q=keywords:aframe-component>)
- make the text camera-facing using the `look-at` component, use link from unpkg

##### Exercise 

- find the particle system component on NPM and use the unpkg link to load it into your scene. See the docs to see how to make it snow
- find and add a component from registry, e.g., skybox, environment, physics, fancy fonts (aframe-text-geometry-component), ....

##### Help

- `04-components.html`
- [docs for entitiy component system](<https://aframe.io/docs/0.9.0/introduction/entity-component-system.html>)
- [docs for component](https://aframe.io/docs/0.9.0/core/component.html)
- [The A-Frame registry](<https://aframe.io/aframe-registry/)>)
- [A-Frame Extras](<https://github.com/donmccurdy/aframe-extras>) has lost of useful components, e.g., for different types of interaction
- [NPM](<https://www.npmjs.com/search?q=keywords:aframe-component>) -  a good place to find components
- [the physics system component](<https://github.com/donmccurdy/aframe-physics-system>) [(examples)](https://glitch.com/~aframe-physics-examples)
- [live demos for many components](<https://github.com/supermedium/superframe>)

-------------------------------------------------------------------------------

## 5 - Animation

- animations are components
- animations are based on [anime.js](https://animejs.com/). If you want to do more complex things have a look at the anime.js docs
- add layers of animation to an object
- place objects in entities to center animations around a different point

##### Not covered

  - [using animation-timeline component](https://www.npmjs.com/package/aframe-animation-timeline-component) - to add more complex animations
  - use pre-made animations in gltf models using animation-mixin

##### Exercise 

- Add an animation to the scene. Can you make the Snowman dance!

##### Help

- `05-animation.html`
- [docs for animation](https://aframe.io/docs/0.9.0/components/animation.html)

-------------------------------------------------------------------------------

## 6 - Interactivity

- start an animation on click.
- Why doesn't it work? Because by default there is no cursor in an Aframe scene - Let's add a cursor!
- understand raytracing, curser component, add a cursor to the camera
- implement animation that triggers on look event (mouseover).
- add a mouse pointer cursor to the scene (`rayOrigin: mouse`), so that events can be triggered with the mouse, too
- implement click event. click events from the camera cursor work by "fusing". Demonstrate fusing.
- on mobile fusing is enabled by default. Disable it explicitely or increase the fuse duration to avoid accidental clicks.
- whitelist raycaster targets using a class (e.g., `.clickable`) to improve performance. Demonstrate performance imporvement by using too many snowflakes.

##### Advanced (cover only if time and energy)

- For certain interactions we can use the `event set` component from [A-Frame extras](https://github.com/donmccurdy/aframe-extras) to make our life easier 
- we can also write our own component and define event listeners for mouse event.

##### Exercise 

- Add an animation to the scene. Trigger it when the user is looking at an object.
- Add a music asset, trigger music when looking at object, stop when looking ends (see docs for help - Tip: It's similar to the animation `on` event.)
- remember to use a whitelist, to avoid collision-checking every snowflake!

##### Help

- `06-interactivity.html`
- [docs for interaction](https://aframe.io/docs/0.9.0/introduction/interactions-and-controllers.html)
- [docs for cursor component](https://aframe.io/docs/0.9.0/components/cursor.html)
- [docs for sound primitive](https://aframe.io/docs/0.9.0/primitives/a-sound.html)
- [docs for camera primitive](https://aframe.io/docs/0.9.0/primitives/a-camera.html)
- [docs for writing your own component](https://aframe.io/docs/0.9.0/introduction/writing-a-component.html)
- [docs for raycaster component](https://aframe.io/docs/0.9.0/components/raycaster.html)

-------------------------------------------------------------------------------

## Review: What have we learned so far?

- Let's put everything we have learned so far together.
- Here's my VR greeting card: `card1.html`
- What does your greeting card look like?
- Want to have a look in all it's VR glory? Use the goggles. (Instructor: provide goggles open link page)
- Are there any questions?

-------------------------------------------------------------------------------

## 7 - Turning the scene into AR

- What is AR.js? 
  - Have a look at the [project website](https://github.com/jeromeetienne/AR.js/blob/master/README.md).
  - certainly not the end-all of webAR (ARKit, Core API)
  - limited abilities but easy to use 
  - Supports marker-based and geolocation-based AR
  - doesn't [(really)](https://medium.com/arjs/ar-js-supports-tango-on-a-frame-too-2c098de4df34) support marker-free AR, tracking of planes, hands etc.
- What are markers?
- Loading AR.js, including a hiro marker and position the object on it, remove the sky, move the object to the origin, add an `<a-entity camera>` to the scene.
- try the app on your phone
- working with multiple markers - use a matrix marker and add another object
- combining markers with QR codes - How does it work?

##### Not covered
- how to make your own markers using the [marker trainer](https://jeromeetienne.github.io/AR.js/three.js/examples/marker-training/examples/generator.html)


##### Instructor

- make sure everyone has at least the Hiro AR markers (see pdfs in `ar-markers/` directory)

##### Exercise

- turn your app into an AR app using ARjs and a Hiro Marker
- get the QR code/marker that leads to your repl.it project and see your greeting card in action.
- **Tip:** You need to use `https://...` to open the link, otherwise Chrome will not be able to use the phone's camera!


##### Help

- `07-ar.html`
- [AR.js project page](<https://github.com/jeromeetienne/AR.js/>)
- [using multiple markers](<https://aframe.io/blog/arjs/#how-to-handle-multiple-distinct-markers>)
- [train and use custom markers](<https://jeromeetienne.github.io/AR.js/three.js/examples/marker-training/examples/generator.html>) [(Instructions)](https://medium.com/arjs/how-to-create-your-own-marker-44becbec1105)
- [using QR codes embedded in markers](<https://medium.com/arjs/ar-code-a-fast-path-to-augmented-reality-60e51be3cbdf>)
- [A good AR matrix marker generator](https://au.gmented.com/app/marker/marker.php)

-------------------------------------------------------------------------------

## 8 - Binding data to A-Frame objects

- Brief explanation of the DOM. Show how to use the browesr inspector to see the DOM elements.
- All A-Frame elemets are in the DOM. Thus, any library that can manipulate the DOM can be used to manipulate A-Frame objects.
- **We are going to use ... because ...** (depending on the audience, time frame)
  - **vanilla JS** because we are modest people and we like to keep things simple.
  - or **D3.js** because it is a great first step to making cool data visualizations.
  - **Vue** because it's a great first step to building a complex app with a backend, user authentication etc.

##### Help

- `08-data-d3.html`
- [D3.js](https://d3js.org/)
- [MDN for JavaScript docs](https://developer.mozilla.org/en-US/docs/Web/API/Element)

-------------------------------------------------------------------------------

## Review: What have we learned so far?

- here's my final AR card: `card2.html`
- let's have a look at your data-driven AR greeting cards!
- Congratulations! You are awesome!

-------------------------------------------------------------------------------

## Mini-Learnathon 

Now you know all you need to know to build an AR web app. Let's have a Mini-Learnathon. You (alone or in a group) pick a project and work on it for the next ... hours. We will help you along the way as good as we can. In the end all groups will present their results, discuss what they tried to achieve, what idifficulties they had and what they learned.

### Potential Project Goals

- The prettiest greeting card
- The most useful AR app
- The most fun AR game

### If you don't know where to start, here are some ideas:

##### No backend needed

- train and use a custom marker
- try to do a multi-marker set up [(link1,](https://github.com/artoolkit/artoolkit-docs/blob/master/3_Marker_Training/marker_multi.md) [link2)](https://medium.com/arjs/area-learning-with-multi-markers-in-ar-js-1ff03a2f9fbe)
- build a "measure it" app with AR.js [(link)](https://github.com/jeromeetienne/AR.js/blob/master/three.js/examples/measure-it.html)
- Put markers on things that add instructions (e.g. videos) that explain the use of tools and machines.
- make an "x-ray" app that shows / lists the content of a box when you point your phone at it, so you don't have to open the box.
- implement a [bowling game](https://hacks.mozilla.org/2017/05/having-fun-with-physics-and-a-frame/)
- try out different ways of interacting with the scene interact with the scene
- see if you can get marker-free AR to work
- make a 3D pie chart
- use GPS based tracking to place objects at different locations in the city [(link)](https://github.com/jeromeetienne/AR.js/blob/location-based/aframe/README.md#location-based)
- build an AR app with Vue.js [(inspiration)](https://github.com/prashant-andani/Augmented-Reality/blob/master/src/components/HelloWorld.vue)

##### Requires a backend

- access an API to show data
- leave notes or graffity on markers for others
- implement a multiplayer game using the physics component
- make a king of the hill or capture the flag game, similar to Pokemon GO gyms

**Tip:** As a backend you could use the [firebase component](https://github.com/supermedium/superframe/tree/master/components/firebase/) or [Sheetsu](https://sheetsu.com/) (note the limitations in the free version, though!)

-------------------------------------------------------------------------------

## Sources & Further Reading

- [The web AR playground](https://webxr.io/webar-playground/)
- [AR marker matrix codes](https://github.com/artoolkit/artoolkit5/tree/master/doc/patterns/Matrix%20code%203x3%20(72dpi))
- [Download individual files and folders from Github](https://minhaskamal.github.io/DownGit/#/home)
- [The ARjs Medium channel](https://medium.com/arjs)
- [JSON editor for AFrame](https://niebert.github.io/JSON3D4Aframe/)


##### Sources

This workshop uses media files created by others:

- [3D model Top Hat by Robin Butler](https://sketchfab.com/3d-models/top-hat-free-download-4fdf3ad3c88d4bb58ea7aabb9bfcffae)
- [3D model present box]()
- [Cat Meow Sound by Cat Stevens](http://soundbible.com/1954-Cat-Meow-2.html)
- [360 degree snow landscape by Janne](https://flic.kr/p/bmFEKz)
