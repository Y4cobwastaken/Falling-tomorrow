# Custom Math System – Nothing Beside Remains

This directory documents the custom mathematical framework used in *Nothing Beside Remains*, a game where time is meaningless, but relative motion and spatial relationships shape the world’s logic.

Rather than relying on traditional absolute physics engines, this system is grounded in **relative positioning**, **local reference frames**, and **contextual transformations**. It supports a world where meaning arises not from fixed laws, but from how the player moves through and interprets space.

---

## ✨ Goals

* **Relativity over absolutes**: All positions, velocities, and interactions are computed relative to meaningful anchors (e.g., key objects, zones, or moments).
* **Scalable world geometry**: Support for a world as large as the UK with perceptual compression, stretching, and non-Euclidean transitions.
* **Narrative-integrated math**: Encounters, puzzles, and physics reflect the game's core themes of perception, entropy, and meaning.

---

## 🧠 Key Components

* [`principles.md`](./principles.md)
  Philosophical and mathematical foundations of the system.

* [`implementation-notes.md`](./implementation-notes.md)
  How the math system is used in the game engine, including performance and design considerations.

* `functions/`

  * `vector_math.md`: Localized distance, direction, and interpolation.
  * `motion.md`: Custom motion rules like phase-relative momentum and smooth inertia.
  * `transformations.md`: Warping and worldspace remapping.

* `examples/`

  * `combat_example.md`: How relative math alters enemy behavior and hit detection.
  * `platforming_example.md`: Puzzle space bending based on position and momentum.
  * `world_scale_example.md`: Distance compression and scale-shifting traversal.

---

## 🕹️ Usage in Gameplay

* **Combat**: Hitboxes and targeting are relative to player intent and proximity, not grid alignment.
* **Traversal**: Motion equations adjust based on memory, focus, and direction — you can “slip past” obstacles not because you're fast, but because you're *closer* in meaning.
* **Exploration**: Landmarks appear closer when sought, and vanish behind you when abandoned. Spatial math is used to shift terrain softly beneath perception.

---

## 🔧 Future Work

* Dynamic anchor points for story-driven spatial folding
* Context-sensitive physics simulations
* Artifact-induced geometry rewriting

---

This math system is designed not just to support gameplay — but to *tell a story through the way space works*.
