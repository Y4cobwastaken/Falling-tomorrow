# Vector Math – Relative Spatial Calculations

This document explains how vector math operates within the custom spatial system of *Nothing Beside Remains*. All vectors are calculated **relative to anchors, perception, or local frames**, avoiding absolute global positions unless necessary for rendering.

---

# 1. Relative Vectors
def get_relative_vector(A, B, anchor_space):
    Returns the vector from point A to point B, expressed relative
    to the coordinate space of the given anchor.
    # Example usage:
    # get_relative_vector(player.position, artifact.position, anchor="MemoryStatue1")
    # Returns vector pointing toward artifact transformed by MemoryStatue1 space


# 2. Directional Intuition
def get_facing_vector(entity, anchor_space=None):
    Calculates the entity’s forward vector based on intention, focus, or camera,
    optionally filtered by anchor space.
    # Narrative example:
    # A boy focused on the horizon might have a forward vector pointing forward
    # even if physically turning away.


# 3. Relative Distance
def relative_distance(A, B, context=None):
    Returns perceived distance between two points, modified by:
    - Attention proximity
    - Anchor distortion (e.g., space folding)
    - Memory-based warping
    # Example:
    # distance = relative_distance(player, goal, context="EntropyZone")
    # Could return 3m or 50m even if world-space distance is 10m.


# 4. Meaningful Interpolation
def interpolate_toward(A, B, t, context=None):
    Interpolates between A and B along the shortest meaningful path,
    influenced by local topology or narrative context.
    - Curves or stalls if player is emotionally avoiding B.
    - May overshoot or lose precision if world is decaying


# 5. Projection and Alignment
def project_onto_reference(obj, reference_axis, anchor_space):
    Projects an object's position onto a vector axis,
    distorted by the curvature of the anchor space.
    Use cases include jump alignment, lock-on targeting,
    and adjusting environmental motion relative to narrative tilt.


# Optional Enhancements:

# Non-linear magnitude scaling:
# Magnitudes adjust logarithmically or exponentially based on entropy levels.

# Vector decay:
# Stored vectors (e.g., momentum) degrade over time unless refreshed by proximity or intention.
