---
layout: default
title: Quick Start
nav_order: 4
description: "Get up and running with PlaySync Pro in under 5 minutes using the interactive sandbox demo scene."
---

# 5-Minute Quick Start
{: .no_toc }

Learn how to tweak GameObjects at runtime, inspect visual diffs, and persist values back to Edit Mode in four simple steps.

---

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Step 1: Open the Interactive Sandbox Scene

PlaySync Pro comes with a ready-to-test interactive sandbox scene:

1. In the top menu, navigate to `Tools > ByteLura > PlaySync > Welcome & Hub`.
2. Click the **Create Interactive Demo Scene** button.
3. Unity will open a clean test scene featuring interactive sample GameObjects:
   * `Modify Me (Cube)` — Transform, BoxCollider, and MeshRenderer.
   * `Modify Me (Sphere)` — Physics Bouncing Material, Transform, and SphereCollider.
   * `Sample Character Controller` — Custom MonoBehaviour with Speed and Jump stats.

---

## Step 2: Enter Play Mode and Make Changes

1. Press the Unity **Play** button (or `Ctrl+P` / `Cmd+P`).
2. Select `Modify Me (Cube)` in the Hierarchy:
   * Move its **Position** to a new location in the Scene view.
   * Rotate its **Rotation** by `45` degrees on the Y-axis.
   * In the **BoxCollider**, change its `Size` to `(2.0, 1.5, 3.0)`.
3. Select `Sample Character Controller`:
   * Increase `Move Speed` from `5.0` to `12.5`.
   * Increase `Jump Force` from `7.0` to `14.0`.

```csharp
// Example runtime values modified in Play Mode:
public class CharacterMovement : MonoBehaviour
{
    public float moveSpeed = 12.5f; // was 5.0f
    public float jumpForce = 14.0f; // was 7.0f
}
```

---

## Step 3: Exit Play Mode & Inspect Changes

1. Press **Stop** to exit Play Mode.
2. The **PlaySync Quick Restore Window** will automatically pop up on your screen.
3. You will see an organized tree showing:
   * Green arrows indicating value transitions: `WAS (5.0) ──> NOW (12.5)`.
   * Checkboxes next to each individual property change.
   * Filter tabs for **Transforms**, **Scripts**, and **Components**.

```text
▼ Modify Me (Cube) (3 changes)                      [ Apply Object ]
  ☑ Local Position   (0.0, 0.0, 0.0)  ──>  (-3.56, 2.27, 0.98)
  ☑ Local Rotation   (0.0, 0.0, 0.0)  ──>  (0.0, 45.0, 0.0)
  ☑ Collider Size    (1.0, 1.0, 1.0)  ──>  (2.0, 1.5, 3.0)
```

---

## Step 4: Commit Your Tweaks to Edit Mode

1. Click the green **⚡ APPLY SELECTED CHANGES** button (or **RESTORE ALL SAFE**).
2. Look at your scene objects in Edit Mode—all position, collider, and script tweaks are now permanently saved!
3. Press `Ctrl+Z` / `Cmd+Z` at any time—PlaySync Pro registers every single change cleanly with Unity's native Undo system.

> **Pro Tip:** If you want to experiment with multiple configurations before applying them to your scene, click **Save as Preset** to store the changes in your **Preset Vault** as a ScriptableObject.

---

## Where to Go From Here

Explore the in-depth documentation for each specialized module:
* [Live Diff Workbench](features/live-diff-workbench/)
* [Quick Restore Window](features/quick-restore-window/)
* [Inspector Integration](features/inspector-integration/)
* [Preset Vault](features/preset-vault/)
* [Flight Recorder](features/flight-recorder/)
