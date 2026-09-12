<style>
  /* 1. Page Width & Base Typography */
  body {
    background-color: #16181d !important;
    color: #c9d1d9 !important;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Helvetica, Arial, sans-serif !important;
    line-height: 1.6 !important;
    max-width: 1020px !important; /* Expanded width */
    margin: 40px auto !important;
    padding: 0 32px !important;
  }

  /* 2. Distinct, Punchy Headers */
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
  /* Project titles: brighter blue with a clean vertical accent bar */
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

  /* 3. Links */
  a { 
    color: #58a6ff !important; 
    text-decoration: none !important; 
  }
  a:hover { 
    text-decoration: underline !important; 
  }

  /* 4. Fix Table / Pipe Links (Converts White Boxes to Dark Containers) */
  table {
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
    padding: 8px 16px !important;
  }
  table td a {
    font-weight: 600 !important;
  }

  /* 5. Code Blocks & Captions */
  code, pre {
    background-color: #1f242c !important;
    color: #e6edf3 !important;
    border: 1px solid #30363d !important;
    border-radius: 6px !important;
  }
  figcaption {
    color: #8b949e !important;
    font-size: 0.85rem !important;
    margin-top: 6px !important;
  }

  /* 6. Media Styling */
  img, video, iframe {
    border-radius: 8px;
    border: 1px solid #30363d;
    max-width: 100%;
  }
</style>

# Portfolio
### Engineer: Software | Graphics | Games
<div class="nav-pills">
  <a href="./Resume_Jonathan_Draney.pdf" target="_blank">📄 Resume (PDF)</a>
  <a href="https://github.com/jondra-dev" target="_blank">GitHub</a>
  <a href="https://linkedin.com/in/YOUR_LINK" target="_blank">LinkedIn</a>
  <a href="mailto:your_email@example.com">Email</a>
</div>

---

## Featured Projects

### [SHADER: Simple Hardware-Accelerated Deferred Engine and Renderer](./shader.md)
*A custom C++/OpenGL graphics engine designed to contrast deferred and forward shading under dynamic lighting stress tests.*

<p align="center">
  <a href="./shader.html">
    <img src="./img/shader_teapot.png" width="70%" style="border-radius: 6px;" alt="SHADER Teapot Scene with Dynamic Lights">
  </a>
</p>

* **Architecture:** Built a multi-target G-Buffer (Position, Normals, packed Albedo + Specular) to decouple geometric rendering from screen-space lighting math.
* **Lighting Systems:** Distance-attenuated dynamic point lights with inverse-square falloff, randomized motion behaviors, and procedural spawning.
* **Stress Benchmarking:** Procedural 7 x 7 x 78 teapot cube (343 meshes) with 1,500 concurrent dynamic lights demonstrating real-time overdraw elimination.
* **Tech Stack:** C++, OpenGL, GLSL, GLEW, FreeGLUT

👉 **[Read Full Architecture Breakdown & Watch Demo ➔](./shader.md)** |

---

### [Spellcatcher: Systems & Gameplay Engineering](./capstone.md)
*First-person creature collection adventure published on Steam, developed by a 15-person interdisciplinary team in Unity (C#).*

<p align="center">
  <a href="./capstone.html">
    <img src="./img/spellcatcher_gameplay.png" width="70%" style="border-radius: 6px;" alt="Spellcatcher Gameplay and Active UI">
  </a>
</p>

* **Engineering Leadership:** Led a 3-engineer sub-team, managed repository branch integrity, resolved complex YAML merge conflicts, and packaged releases for Steam.
* **UI/UX Architecture:** Engineered a decoupled hotbar manager with animated selection tracking, inventory data binding, and state-interruption safety to prevent softlocks.
* **Custom External Tooling:** Created `AudioScanner.py`, an automated Python audit utility that parsed the C# codebase to detect unregistered and orphaned audio assets.
* **Gameplay & Kinematics:** Designed a 50-parameter first-person movement controller, raycast interaction dispatcher, and flexible designer-facing inventory mechanic systems.

👉 **[Read Systems Breakdown & Implementation Details ➔](./capstone.md)** | **[Steam Store Page](https://store.steampowered.com/app/4551940/SpellCatcher/){:target="_blank" rel="noopener"}**

---

## Technical Skills

**Languages:**
* C, C++, C#, Java, Python
* JavaScript, SQL, Bash, Kotlin, Rust, Go

**Engines & Graphics:**
* Unity (2022.3 LTS, 6), Unreal Engine 5, OpenGL, GLSL

**Development Tools & Workflows:**
* Git, GitHub, Visual Studio, VS Code, Emacs, Linux / WSL
