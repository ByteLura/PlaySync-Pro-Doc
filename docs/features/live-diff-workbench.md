---
layout: default
title: Live Diff Workbench
parent: Core Features
nav_order: 1
description: "Master real-time parameter tracking, search filters, and granular selective commits in PlaySync Studio."
---

# Live Diff & Staging Workbench
{: .no_toc }

The **PlaySync Pro Studio** is the master workbench designed for deep inspection and granular commit control during active play testing.

---

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Opening the Studio Workbench

* **Menu Path:** `Tools > ByteLura > PlaySync > PlaySync Studio`
* **Keyboard Shortcut:** `Ctrl+Alt+S` (Windows) / `Cmd+Option+S` (macOS)

---

## Anatomy of the Live Diff Tree

```text
┌────────────────────────────────────────────────────────────────────────┐
│ Total Changes: 9   [ Search changes... ]                               │
│ [ All (9) ]  [ Transforms (5) ]  [ Scripts (2) ]  [ Components (2) ]   │
├────────────────────────────────────────────────────────────────────────┤
│ ▼ Modify Me (Cube) (5 changes)                            [Commit Obj] │
│   ☑ Local Position  (-1.5, 0.5, 0.0) ──> (-3.56, 2.27, 0.98) Transform │
│   ☑ Local Rotation  (0, 0, 0)        ──> (-0.01, -0.02, 0.02)Transform│
│   ☑ Local Scale     (1, 1, 1)        ──> (-0.34, 1.0, 2.64)  Transform │
│   ☑ Size            (1, 1, 1)        ──> (1, 1, 1.2)        BoxCollider│
│   ☑ Center          (0, 0, 0)        ──> (0.35, 0, 0)       BoxCollider│
└────────────────────────────────────────────────────────────────────────┘
```

### 1. Real-Time Tracking Loop
PlaySync Pro snapshots the initial state of active scene objects upon entering Play Mode. While in Play Mode, its non-allocating scanner detects changes across:
* **Transforms:** Local Position, Rotation, Scale, and World Transforms.
* **Physics Colliders:** BoxCollider size/center, SphereCollider radius, CapsuleCollider height, PhysicMaterials.
* **Lighting & Cameras:** Intensity, Color, Range, Field of View, Clipping Planes.
* **MonoBehaviours:** All serialized public fields and `[SerializeField]` private fields (strings, ints, floats, Vector2/3/4, Colors, Enums, AnimationCurves).

### 2. Side-by-Side Value Diffs
Every modified property clearly displays its original Edit Mode value (`WAS` in red/muted) alongside its current runtime value (`NOW` in bright green/cyan), eliminating guesswork when comparing adjustments.

---

## Granular Commit Workflows

Unlike basic persistence tools that enforce all-or-nothing overwrites, PlaySync Pro offers four levels of granular commit:

1. **Individual Field Commit:** Check or uncheck specific property checkboxes (e.g., persist `Speed` without altering `Position`).
2. **Per-Object Commit:** Click the **Commit Object** button on any GameObject header to save only that entity's changes.
3. **Category Filter Commit:** Select the **Transforms** tab, search for `Player`, and commit all matching results simultaneously.
4. **Restore All Safe:** Automatically commits all non-conflicting properties across the entire scene in one click.

---

## Prefab & Nested Prefab Overrides

When modifying a Prefab instance in Play Mode:
* PlaySync Pro tracks the instance overrides and preserves prefab connections.
* Committing writes directly to the scene instance without breaking the parent prefab link.
* If desired, you can apply overrides directly to the source Prefab asset using standard Unity Inspector controls.

> **Pro Tip:** In the bottom toolbar of PlaySync Studio, you can click **Export JSON** to backup your staged changes into an external `.json` snapshot file for versioning.
