---
layout: default
title: Auto-Save Rule Matrix
parent: Core Features
nav_order: 6
description: "Configure zero-click automated persistence rules by Component Type, GameObject Tag, and C# attributes."
---

# Zero-Click Auto-Save Rule Matrix
{: .no_toc }

For high-frequency iteration workflows—such as adjusting level lighting, camera positions, or custom audio managers—stopping to click "Restore" every time can disrupt flow. PlaySync Pro's **Auto-Save Rule Matrix** allows you to designate specific components and tags to automatically persist upon Play Mode exit.

---

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## The 3 Persistence Rule Layers

```mermaid
graph TD
    A[Play Mode Exit] --> B{Auto-Save Rule Evaluator}
    B -->|Check 1| C[Component Type Rules e.g. Light, Camera]
    B -->|Check 2| D[GameObject Tag Rules e.g. 'Player', 'Environment']
    B -->|Check 3| E[C# [AutoSavePlayMode] Code Attribute]
    C -->|Match| F[Auto-Persist Immediately to Scene]
    D -->|Match| F
    E -->|Match| F
    B -->|No Match| G[Send to Quick Restore Window]
```

---

## Configuring the Rule Matrix

Open `Tools > ByteLura > PlaySync > Auto-Save Settings` (or the **Auto-Save Matrix** tab in PlaySync Studio):

```text
┌────────────────────────────────────────────────────────────────────────┐
│  Zero-Click Auto-Save Rule Matrix                                      │
├────────────────────────────────────────────────────────────────────────┤
│  ☑ Enable Auto-Save System                                             │
│                                                                        │
│  [+] Component Type Rules:                                             │
│  ├── UnityEngine.Light                    (Persist All Lights)         │
│  ├── UnityEngine.Camera                   (Persist Camera Adjustments) │
│  └── Game.AudioVolumeController           (Persist Audio Levels)       │
│                                                                        │
│  [+] GameObject Tag Rules:                                             │
│  ├── "Player"                             (Persist Player Transforms)  │
│  └── "MainCamera"                         (Persist Camera Rig)         │
└────────────────────────────────────────────────────────────────────────┘
```

### Adding a Component Type Rule
1. Click **+ Add Component Rule**.
2. Drag any Component or Script into the field, or select from the dropdown list.
3. Check **Auto-Persist**. Any runtime modifications to matching components will automatically save to your scene when exiting Play Mode.

### Adding a Tag Rule
1. Click **+ Add Tag Rule**.
2. Select any active project tag (e.g., `Player`, `Vehicle`, `SpawnPoint`).
3. All components on matching GameObjects will automatically persist.

---

## Code-Level Attribute: `[AutoSavePlayMode]`

If you are a programmer writing custom MonoBehaviours, you can tag individual scripts or fields with the `[AutoSavePlayMode]` attribute:

```csharp
using UnityEngine;
using ByteLura.PlaySync;

public class PlayerCombat : MonoBehaviour
{
    // Automatically persist this entire component upon Play Mode exit:
    [AutoSavePlayMode]
    public float attackPower = 25.0f;

    [AutoSavePlayMode]
    public float comboWindowSeconds = 0.45f;

    // This field will NOT auto-save (will go to Restore Window staging):
    public int currentAmmo = 100;
}
```

> **Pro Tip:** The `[AutoSavePlayMode]` attribute compiles cleanly into production runtime builds with zero performance penalty.
