---
layout: default
title: C# Patch Generator
parent: Core Features
nav_order: 7
description: "Turn runtime tweaks into clean, production-ready C# code initialization blocks with 1-click clipboard copying."
---

# C# Initialization Patch Generator
{: .no_toc }

When building procedural level generators, dynamic spawn scripts, or script-driven weapon setups, tweaking values in the Inspector is only half the battle. You still need to manually write those numbers into C# source code. PlaySync Pro's **C# Patch Generator** converts runtime tweaks into clean C# syntax with one click.

---

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Generating Code from Play Mode Tweaks

1. Open `Tools > ByteLura > PlaySync > PlaySync Studio`.
2. Navigate to the **C# Patch Gen** tab.
3. Select your target modified GameObject from the hierarchy tree.
4. The generator immediately produces formatted C# assignment snippets:

```csharp
// Auto-generated initialization patch by PlaySync Pro:
// Target: Modify Me (Cube) -> Transform & BoxCollider

// --- Transform Setup ---
transform.localPosition = new Vector3(-3.56f, 2.27f, 0.98f);
transform.localRotation = Quaternion.Euler(-0.01f, -0.02f, 0.02f);
transform.localScale = new Vector3(1.0f, 1.0f, 2.64f);

// --- BoxCollider Setup ---
BoxCollider boxCollider = GetComponent<BoxCollider>();
if (boxCollider != null)
{
    boxCollider.size = new Vector3(1.0f, 1.0f, 1.2f);
    boxCollider.center = new Vector3(0.35f, 0.0f, 0.0f);
}
```

---

## Supported Types & Formatting

The patch generator produces clean, standard C# formatting for all common Unity structures:

| Data Type | Generated C# Code Example |
|:---|:---|
| `Vector2` / `Vector3` / `Vector4` | `new Vector3(1.25f, 4.5f, -8.0f)` |
| `Quaternion` / Euler Angles | `Quaternion.Euler(0.0f, 45.0f, 0.0f)` |
| `Color` / `Color32` | `new Color(0.25f, 0.75f, 1.0f, 1.0f)` |
| `AnimationCurve` | `new AnimationCurve(new Keyframe(0f, 0f), new Keyframe(1f, 1f))` |
| `Enum` Values | `WeaponFireMode.BurstThreeRound` |
| Primitive Types (`float`, `int`, `bool`, `string`) | `speed = 14.5f; isActive = true;` |

---

## Quick Clipboard Actions

* **Copy Single Property:** Click the small clipboard icon next to any property row in the live diff tree.
* **Copy Full Component Block:** Click **Copy Component Patch** to grab initialization logic for all properties on a single component.
* **Copy Full GameObject Setup:** Generates an entire `void InitializeEntity()` method template ready to paste into your procedural script.

> **Pro Tip:** You can also right-click any Component header in the Unity Inspector and select `PlaySync > Copy Values as C# Code Patch`.
