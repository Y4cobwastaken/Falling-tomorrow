# Implementation Notes – Custom Math System

This document details how the relative-position-based math system is implemented in the game engine for *Nothing Beside Remains*, and how it interacts with gameplay, performance, and design decisions.

---

## 🧩 Core Architecture

The math system is built around **anchored coordinate spaces** and **transformable frames**, which wrap Unity’s or Unreal’s built-in Vector3/Transform types (or your custom engine’s equivalents).

Each object or actor can be expressed in:
- **World-Space**: Deprecated unless used for rendering or skybox logic.
- **Local-Space**: Within a zone, biome, or room. Used for movement, interaction, and events.
- **Anchor-Space**: Relative to a concept or entity (e.g. "relative to the statue", "relative to where the boy died").
- **Perceptual-Space**: A dynamic reference that prioritizes what the player is looking for, fearing, or avoiding.

All math-based interactions resolve within the appropriate space — not globally.

---

## 🚦 Priority Rules

When performing operations like movement, collisions, or detection:
1. **Anchor-space overrides local-space** if defined.
2. **Perceptual-space** modifies values before resolution (e.g., proximity scaling).
3. **Local-space** is used as a fallback.
4. **World-space** is used only for visuals or default fallbacks.

This structure allows:
- Teleporting without breaking physics
- Warping terrain under a walking character
- Interpreting jump arcs differently across zones

---

## ⚙️ Engine Use Cases

### ✔ Movement
- Player movement is calculated based on *intended direction* and *relative gradient*.  
  Example: Walking toward a cliff might reduce slope penalty if it's a critical narrative beat.

### ✔ Triggers and Events
- Proximity triggers compare **perceptual-relative positions**, not absolute ones.
- Objects that are "ignored" by the player become mathematically *distant*, even if on-screen.

### ✔ Puzzles
- Spatial puzzles use **frame switches**: Walking into an archway might shift the local origin, rotating the perceived space.
- Rooms that loop actually *shift frames behind the scenes* to fake infinite continuity.

### ✔ Combat
- Hit registration is adjusted for **angle-relative intent** — a lunge toward the side of an enemy might register as a hit even if slightly misaligned in world-space.
- Enemies can "phase out" when out of emotional relevance, not just visibility.

---

## 🧵 Narrative Hooks

The math system is directly influenced by:
- **Artifacts held**: Each one can subtly alter physics (e.g. lower gravity, wider jump parabola, longer ledge grab range).
- **Player history**: Past deaths or choices may create *coordinate memory echoes* that distort nearby space.
- **World entropy level**: As the world nears collapse, transformations become more dramatic and less stable.

---

## 🔄 Debugging Tools

To aid testing and tuning:
- Toggle overlays for all space types (anchor, local, perceptual)
- Log the math behind motion and hit detection
- Visualize world folding transitions in real time

---

## 🧠 Final Thoughts

This system transforms space into a narrative tool. By warping math itself around meaning, *Nothing Beside Remains* allows environments to feel alive — not as objects, but as **reflections of the boy’s journey**.
