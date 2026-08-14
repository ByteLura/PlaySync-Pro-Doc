---
layout: default
title: Preset Vault
parent: Core Features
nav_order: 4
description: "Save, manage, and A/B test gameplay configurations with ScriptableObject balance presets."
---

# Game Balance Preset Vault
{: .no_toc }

Game balancing is fundamentally an iterative science. PlaySync Pro's **Preset Vault** allows you to save complete snapshots of your runtime tweaks as standalone **ScriptableObject Assets** (`.asset`) for instant A/B comparison and team distribution.

---

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## What is a PlaySync Preset?

A `PlaySyncPreset` is a native Unity ScriptableObject asset saved inside your project (by default in `Assets/PlaySyncPresets/`). It stores:
* Target GameObject paths & hierarchy identifiers.
* Component full type names (e.g., `UnityEngine.CharacterController`, `Game.WeaponConfig`).
* Serialized property keys and values (Vectors, Colors, Floats, Strings, Enums).
* Creation timestamp and user author metadata.

```csharp
[CreateAssetMenu(fileName = "NewPlaySyncPreset", menuName = "ByteLura/PlaySync/Preset")]
public class PlaySyncPreset : ScriptableObject
{
    public string presetName;
    public string description;
    public string sceneName;
    public string author;
    public List<ObjectSnapshot> snapshots = new List<ObjectSnapshot>();
}
```

---

## Creating a Preset from Play Mode Tweaks

1. While in Play Mode (or inside the Quick Restore Window upon exiting), click **Save as Preset**.
2. Give your preset a descriptive name (e.g., `Heavy_Armor_Boss_Balance_V2`).
3. Add optional notes in the description field (e.g., `Increased boss projectile speed by 25%, reduced jump recovery delay`).
4. Click **Create Preset**. The new asset is instantly serialized into your project.

---

## Browsing & Managing Presets

Open `Tools > ByteLura > PlaySync > Preset Vault` (or the **Preset Vault** tab in PlaySync Studio):

```text
┌────────────────────────────────────────────────────────────────────────┐
│  Game Balance Preset Vault                                             │
├────────────────────────────────────────────────────────────────────────┤
│  Available Presets (4)                                                 │
│  ┌───────────────────────────────────────────────────────────────────┐ │
│  │ 📦 Player_Arcade_Physics_Fast (8 Changes)  [ Apply to Scene ] [X] │ │
│  │ 📦 Player_Realistic_Physics_Slow (8 Changes)[ Apply to Scene ] [X] │ │
│  │ 📦 Enemy_Wave_Aggressive_AI (14 Changes)   [ Apply to Scene ] [X] │ │
│  │ 📦 Weapon_Recoil_High_Spread (6 Changes)   [ Apply to Scene ] [X] │ │
│  └───────────────────────────────────────────────────────────────────┘ │
└────────────────────────────────────────────────────────────────────────┘
```

### 1-Click A/B Testing
Switching between game design iterations is instantaneous:
* Click **Apply to Scene** on `Player_Arcade_Physics_Fast`, enter Play Mode, and test the feel.
* Exit Play Mode, click **Apply to Scene** on `Player_Realistic_Physics_Slow`, and test immediately.
* No scene duplication, no manual note-taking, and zero merge conflicts.

---

## Team & Git Sharing

Because presets are standard Unity `.asset` files:
* They check cleanly into Git, Perforce, or Plastic SCM with zero binary bloat.
* Game designers can create balance presets and commit them to Git for programmers and QA testers to pull and verify in their local scenes.

> **Pro Tip:** You can ping or select any preset file directly in the Project tab by clicking the **Ping** button next to the preset name.
