# Motion – Relative Movement and Perceived Physics

Motion in *Nothing Beside Remains* is governed by intention, memory, terrain familiarity, and narrative weight — not absolute force or friction. This document defines the core mechanics for movement, speed, jumping, falling, gliding, and acceleration.

---

## 1. Relative Velocity

**Function:** `get_velocity(entity, context_anchor)`  
**Description:** Returns the movement velocity of an entity relative to a nearby anchor or emotional tether.

- Example:
  ```python
  velocity = get_velocity(player, context_anchor="FamiliarPath")
  ```
  The player may appear to be moving faster or slower depending on their connection to the terrain or memory of it.

- Velocity may temporarily **increase** when near objects the player longs for, or **decrease** when nearing feared locations.

---

## 2. Jumping and Ascending

**Function:** `calculate_jump_arc(start, target, context)`  
**Description:** Produces a jump arc that curves through emotional or narrative space.

- Distance, height, and timing are context-sensitive.
- A simple jump may become **higher**, **floatier**, or even **stuttered** based on:
  - Confidence
  - World entropy
  - Player's intent

**Example:**  
```python
arc = calculate_jump_arc(player.position, ledge.position, context="CollapseSector")
```

---

## 3. Falling and Descent

**Function:** `fall_rate(entity, region_properties)`  
**Description:** Defines how fast and how hard an entity falls, based on world entropy and entity state.

- Gravity-like forces are **not constant**.  
- In high-chaos zones, characters may fall faster but **land lighter**, as if the world forgets to punish them.
- In dreamlike areas, falling may **never end** unless interrupted.

---

## 4. Gliding and Drift

**Function:** `glide_vector(entity, anchor_space)`  
**Description:** Computes a glide vector allowing horizontal motion through meaningful currents.

- Used with capes, cloths, or entropy gliders.
- Drift may curve automatically toward significant memories or resist movement near lost ones.

---

## 5. Momentum Memory

**Concept:** Stored motion is retained and **rediscovered** after stops, as if the world “remembers” your last step.

- The system may resume movement with a **ghost impulse** even after a pause.
- This is influenced by how clearly a player “knows where they’re going.”

---

## 6. Impulse Intuition

**Function:** `apply_impulse(entity, direction, magnitude, emotion_filter=None)`  
**Description:** Applies a force not purely in physics-space, but filtered through emotional weight.

- Example: Dashing away from an enemy you fear may yield a **stronger push**.
- Jumping with hope may result in **slightly longer airtime**.

---

## 7. Friction and Resistance

- Terrain resistance is based on how *welcoming* or *hostile* the space feels.
- **Memory-formed paths** reduce resistance.
- Areas of narrative friction (e.g., regret zones) slow motion even on flat ground.

---

## Optional Enhancements

- **Hesitation lag**: Adds a delay to movement in zones where the player is uncertain or overwhelmed.
- **Momentum tethering**: Allows players to “snap back” to a point of comfort or meaning if momentum fails mid-air.

---

Movement in this system is not about physics — it’s about *why* you move.  
The world listens, then answers with motion that reflects your reason for stepping forward.
