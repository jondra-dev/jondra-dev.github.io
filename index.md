<style>
  /* Base page styling */
  body {
    background-color: #16181d !important;
    color: #c9d1d9 !important;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Helvetica, Arial, sans-serif !important;
    line-height: 1.6 !important;
    max-width: 880px !important;
    margin: 40px auto !important;
    padding: 0 24px !important;
  }

  /* Headings & Dividers */
  h1, h2, h3, h4 { color: #f0f6fc !important; font-weight: 600 !important; }
  h1 { border-bottom: 1px solid #30363d; padding-bottom: 8px; }
  hr { border: 0; border-top: 1px solid #30363d; margin: 32px 0; }

  /* Links & Accents */
  a { color: #58a6ff !important; text-decoration: none !important; }
  a:hover { text-decoration: underline !important; }

  /* Media containers */
  img, video, iframe {
    border-radius: 8px;
    border: 1px solid #30363d;
    max-width: 100%;
  }

  /* Top Navigation Pill Badges */
  .nav-pills a {
    display: inline-block;
    padding: 5px 14px;
    background: #21262d;
    color: #58a6ff !important;
    border: 1px solid #30363d;
    border-radius: 20px;
    font-size: 0.9rem;
    margin-right: 8px;
    margin-bottom: 8px;
  }
  .nav-pills a:hover {
    background: #30363d;
    border-color: #8b949e;
  }

  /* Call-to-action buttons */
  .cta-link {
    display: inline-block;
    margin-top: 8px;
    font-weight: 600;
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
