[⬅️ Back to Portfolio](./)

# SpellCatcher
### Lead Systems & Gameplay Engineer
*15-Person Capstone Team (SkuppyWuppies) | Unity (C#) | Published on Steam*
<img width="2735" height="1250" alt="Title Logo" src="https://github.com/user-attachments/assets/d6797fb6-3dc8-4eba-9467-cae29c842567" />

**Role:** Lead Engineer (Sub-team Lead of 3 Engineers)

**Deliverables:** UI/UX Architecture, Custom Audio Pipeline & Tooling, Movement Controller, Steam Release Packaging

**Links:** [Steam Store Page](https://store.steampowered.com/app/4551940/SpellCatcher/) | [Gameplay Trailer / Demo](https://youtu.be/0Kv8YTDxORs?si=TRYRSPAZV_7cTwtr)

---

## 🏗️ 1. UI/UX Architecture & Dynamic Data Systems
*Refactoring the front-end interface into an event-driven, decoupled presentation layer.*

* **Dynamic Spell Hotbar:** Engineered a responsive UI manager featuring an interpolated sliding indicator following active selection, dynamic rune counts, and real-time icon updates tied to player inventory state.
* **Codex Encyclopedia System:** Architected a modular creature encyclopedia utilizing instantiated button prefabs, dynamic scroll view data binding, and clean state toggles to prevent UI softlocks.
* **State Interrupt Handling:** Implemented logic to cleanly interrupt active spell casts, preventing spell execution desyncs during menu or inventory transitions.
* **Full Menu UI Systems:** Coordinated with 2D artist to make Main Menu, Settings Menu, and Pause Menus, all with dedicated artwork, buttons, and configurable keybinds.

INSERT VIDEO OF CHANGING SPELLS AND INVENTORY SLOTS WITH ITEMS IN THEM
---

## 🛠️ 2. Custom Audio Pipeline & Automation Tooling
*Building spatial audio systems and custom production utilities.*

* **Spatial Audio Engine:** Integrated dynamic audio management featuring 3D spatial positioning, loop control, and pitch variance for spell-casting, creature capture sequences, and environment interactions.
* **`AudioScanner.py` Pipeline Tool:** Developed an independent Python automation utility that parsed the entire C# codebase, cross-referencing registered audio metadata against active script invocations to identify orphaned clips and missing sound registrations.
* **Contextual Feedback:** Implemented surface-aware kinematic sound triggers (e.g., differentiated landing audio based on ground vs. water collision).

---
