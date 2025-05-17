# Vector Math

## Purpose

This document outlines how vector mathematics operates within the custom math system of *Nothing Beside Remains*. All calculations are rooted in **relative position**, ensuring that spatial relationships and motion remain grounded in the perspective of the player and the world around them.

---

## Notes:

### 1. Coordinate Basis

The world uses a **local-relative 3D coordinate system**:

- **Forward (Z+)** – Direction the player is facing  
- **Right (X+)** – Perpendicular to forward  
- **Up (Y+)** – Vertical relative to the world

All vectors are computed relative to the **player or object origin**, not absolute world space.

---

### 2. Core Vector Functions

#### Vector Representation
```text
Vector3(x, y, z)
```

#### Common Operations

| Function | Signature | Description |
|---------|-----------|-------------|
| `add(A, B)` | `Vector3` | Adds two vectors |
| `subtract(A, B)` | `Vector3` | A relative to B |
| `scale(A, s)` | `Vector3` | Scales vector by scalar `s` |
| `normalize(A)` | `Vector3` | Returns unit vector in direction of A |
| `dot(A, B)` | `float` | Returns cosine of angle between A and B |
| `cross(A, B)` | `Vector3` | Returns perpendicular vector |
| `magnitude(A)` | `float` | Length of vector A |
| `distance(A, B)` | `float` | Euclidean distance between A and B |
| `reflect(I, N)` | `Vector3` | Reflects vector I around normal N |

---

### 3. Relative Positioning

Movement, targeting, and sensing all rely on vector differences:

```text
direction = normalize(target.pos - origin.pos)
```

- Movement inputs are mapped relative to character orientation.
- Sensory systems (vision, sound, pulse) detect based on angular alignment using dot products.

---

### 4. Environment-Based Vector Modifiers

- Gravity and slopes affect movement vectors non-linearly.
- Curved vectors simulate friction, air resistance, or terrain pressure.
- Artifact emissions apply vector distortion effects within a radius.

---

### 5. Application Examples

#### Movement:
```python
input_vector = get_input_vector()  # In local space
facing = get_facing_vector()
world_vector = rotate_relative(input_vector, facing)
```

#### Line of Sight:
```python
to_target = normalize(target.pos - eye.pos)
if dot(eye.forward, to_target) > 0.95:
    target_visible = True
```

#### Artifact Pulse Direction:
```python
field_direction = normalize(artifact.pos - player.pos)
```

---

## Key Terms:

- **Vector3**: 3D vector storing position, direction, or force
- **Relative Vector**: Computed from one object's local perspective
- **Dot Product**: Measures alignment between vectors
- **Cross Product**: Returns vector perpendicular to plane of two inputs
- **Normalization**: Converts vector to unit length

---

## Questions & Answers:

**Q: Why base everything on relative vectors?**  
A: This keeps interactions meaningful to the player’s position and ensures all physics and behavior support the narrative themes of orientation, isolation, and discovery.

**Q: Can vectors be non-linear?**  
A: Yes. The math system allows curving and distortion of vectors based on physical forces or narrative logic.

**Q: How does this integrate with physics?**  
A: See `math_system/functions/Physics.md` for collision, gravity, and motion resolution using these vectors.
