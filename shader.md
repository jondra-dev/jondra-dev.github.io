<style>
  /* 1. Page Width & Base Typography */
  body {
    background-color: #16181d !important;
    color: #c9d1d9 !important;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Helvetica, Arial, sans-serif !important;
    line-height: 1.6 !important;
    max-width: 1020px !important;
    margin: 40px auto !important;
    padding: 0 32px !important;
  }

  /* 2. Top Navigation Pill Badges */
  .nav-pills {
    margin: 16px 0 24px 0 !important;
  }
  .nav-pills a {
    display: inline-block !important;
    padding: 5px 14px !important;
    background: #21262d !important;
    color: #58a6ff !important;
    border: 1px solid #30363d !important;
    border-radius: 20px !important;
    font-size: 0.9rem !important;
    font-weight: 500 !important;
    margin-right: 8px !important;
    margin-bottom: 8px !important;
    text-decoration: none !important;
  }
  .nav-pills a:hover {
    background: #30363d !important;
    border-color: #8b949e !important;
    text-decoration: none !important;
  }

  /* 3. Distinct Headers & Dividers */
  h1, h2, h3, h4 { 
    font-weight: 600 !important; 
  }
  h1 { 
    color: #f0f6fc !important; 
    border-bottom: 1px solid #30363d; 
    padding-bottom: 8px; 
  }
  h2 { 
    color: #f0f6fc !important; 
    font-size: 1.6rem !important;
    margin-top: 36px !important;
  }
  h3 { 
    color: #79c0ff !important; 
    font-size: 1.35rem !important;
    border-left: 4px solid #1f6feb;
    padding-left: 10px;
    margin-top: 28px !important;
  }
  hr { 
    border: 0; 
    border-top: 1px solid #30363d; 
    margin: 36px 0; 
  }

  /* 4. Links */
  a { 
    color: #58a6ff !important; 
    text-decoration: none !important; 
  }
  a:hover { 
    text-decoration: underline !important; 
  }

  /* 5. Snug, Dark Tables (Hugs content instead of full-width stretch) */
  table {
    width: auto !important;
    display: inline-table !important;
    background-color: #21262d !important;
    border: 1px solid #30363d !important;
    border-radius: 6px !important;
    border-collapse: separate !important;
    border-spacing: 0 !important;
    overflow: hidden !important;
    margin: 16px 0 !important;
  }
  table tr, table tr:nth-child(2n) {
    background-color: #21262d !important;
    border: none !important;
  }
  table td, table th {
    background-color: #21262d !important;
    border: 1px solid #30363d !important;
    color: #c9d1d9 !important;
    padding: 6px 14px !important;
  }
  table td a {
    font-weight: 600 !important;
  }

  /* 6. Code & Media */
  code, pre {
    background-color: #1f242c !important;
    color: #e6edf3 !important;
    border: 1px solid #30363d !important;
    border-radius: 6px !important;
  }
  img, video, iframe {
    border-radius: 8px;
    border: 1px solid #30363d;
    max-width: 100%;
  }
  figcaption {
    color: #8b949e !important;
    font-size: 0.85rem !important;
    margin-top: 6px !important;
  }
</style>

[⬅️ Back to Portfolio](./)

# SHADER: Simple Hardware Accelerated Deferred Engine and Renderer
*Interactive Computer Graphics Capstone / Final Project*

**Tech Stack:** C++ | OpenGL | GLSL | GLEW | FreeGLUT  
**Codebase Scale:** ~2,000 lines of C++ architecture, ~250 lines of custom GLSL shaders

---

<iframe
  width="100%"
  height="450"
  src="https://www.youtube-nocookie.com/embed/Cnc0-1fAuSU"
  title="SHADER Demo Recording"
  frameborder="0"
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
  allowfullscreen>
</iframe>

---

## 🎯 What to Look For in the Demo
* **Dynamic Point Light Scaling:** Spawning, managing, and distance-attenuating hundreds of individual point lights using the inverse-square law.
* **Animated Light Behaviors:** Custom motion paths including orbital ("solar") systems and clustered ("beehive") flitting patterns for the single teapot and teapot cube scenes, respectively.
* **Continuous Scene Rotation:** Stress-testing hardware rasterization and culling across changing viewing angles, and clearly contrasting render pipeline performance.
* **G-Buffer Diagnostic View:** Live 4-quadrant split showing internal render targets and final composited image.
* **The Procedural Teapot Cube:** Scalable geometric grids generating high vertex counts (combined with many lights) to push rendering stress tests.
* **Live Pipeline Toggle:** Real-time switching between Forward and Deferred pipelines to contrast hardware execution under load. (Look for `Deferred` and `Forward` in the Title Bar!)

---

## 🧠 Architecture: Forward vs. Deferred Shading

The core objective of SHADER was to build and benchmark a **deferred rendering pipeline** against a traditional **forward rendering pipeline** under heavy dynamic lighting loads.

<figure style="text-align: center;">
  <img src="./img/shader_gbuffer_textures.png" width="60%" alt="G-Buffer Quadrant Split View">
  <figcaption><i>G-Buffer Quadrant Diagnostic: Position (Top-Left), Surface Normals (Top-Right), Packed Albedo + Specular (Bottom-Left), Final Shaded Composite (Bottom-Right).</i></figcaption>
</figure>

### The Problem: Forward Rendering & Overdraw
In a traditional forward pipeline, lighting calculations are evaluated for **every fragment generated by every piece of geometry**, regardless of whether that fragment will actually be visible on the screen. 

Imagine 10 teapots sitting in a straight line extending away from the camera. In a worst-case scenario, the GPU processes and shades the back teapot, only to draw the next one directly on top of it, repeating this all the way to the front. 

If a scene contains 50 overlapping dynamic lights, a forward renderer runs expensive lighting mathematics for *every light on every overlapping surface*—even surfaces that get immediately covered up by another object in front of them. This wasted GPU work is called **overdraw**, which becomes exponentially more expensive as light and triangle counts scale up.

### The Solution: Decoupling Geometry from Lighting (The G-Buffer)
Deferred rendering splits the frame into two distinct stages:

1. **The Geometry Pass:** Objects are drawn once into multiple off-screen framebuffer render targets (the **G-Buffer**). Rather than calculating lighting here, the shaders simply record surface data per pixel:
   * **Target 1 (Position):** View-space coordinate data (X, Y, Z).
   * **Target 2 (Normals):** Surface normal vectors (X, Y, Z) for lighting calculations.
   * **Target 3 (Albedo & Specular):** Surface base color (RGB) packed with specular reflection intensity stored in the Alpha channel.
2. **The Deferred Lighting Pass:** Geometry is ignored entirely. The engine draws a single screen-space quad, samples the G-Buffer textures, and computes the lighting model (ambient, diffuse, specular attenuation) **only once per visible pixel on screen**. 

Whether there are 10 teapots or 1,000 teapots stacked behind each other, the expensive lighting equations only run for the pixels that end up on the screen.

---

## 📊 Stress-Testing Performance

<figure style="text-align: center;">
  <img src="./img/shader_inside_teapot_cube.png" width="60%" alt="Inside the Teapot Cube Stress Scene">
  <figcaption><i>Free-camera perspective inside a 125-teapot cube illuminated by 400 dynamic point lights.</i></figcaption>
</figure>

* **The Scene:** In the demo video, you see a procedural 7 × 7 × 7 grid (**343 teapots**) surrounded by **1,500 dynamic, animated point lights**.
* **The Result:** The forward rendering pipeline drops to sluggish framerates because it attempts to shade thousands of occluded surfaces for each light source. Switching over to the deferred pipeline instantly returns the scene to a smooth, interactive framerate. That demonstrates the core advantage of deferred shading, and why modern 3D engines rely on deferred or clustered rendering pipelines to handle heavy dynamic lighting loads.

---

## 🛠️ Engine & Interactive Features
* **Modular Scene Architecture:** Custom `SceneObject` encapsulation handling internal OpenGL buffers (VAO/VBOs), state transforms, and shader binding logic.
* **Light Visualizers:** Dynamic spherical indicators rendered through a secondary unlit forward pass with depth testing enabled.
* **Interactive Orbit Camera:** Unity-style view controls featuring yaw/pitch orbiting, origin re-centering, free-look translation, and dolly zooming.
* **Material Hot-Swapping:** Real-time texture coordinate toggling between procedural baseline albedo and complex UV-mapped diffuse materials.
