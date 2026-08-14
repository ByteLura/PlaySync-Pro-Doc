---
layout: default
title: Getting Started
nav_order: 2
description: "Learn the core concepts, user interface layout, and tool access points of PlaySync Pro."
---

# Getting Started
{: .no_toc }

PlaySync Pro is built to blend seamlessly into your daily Unity editor workflow with zero setup overhead. This guide covers how to access the tools, understand the UI philosophy, and configure your default preferences.

---

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Accessing PlaySync Pro in Unity

All PlaySync Pro tools and windows are cleanly organized under the top editor menu bar:

```text
Tools > ByteLura > PlaySync >
  ├── PlaySync Studio           (Ctrl+Alt+S / Cmd+Option+S)
  ├── Quick Restore Window      (Ctrl+Alt+R / Cmd+Option+R)
  ├── Preset Vault              (Ctrl+Alt+P / Cmd+Option+P)
  ├── Flight Recorder (History)
  ├── Auto-Save Settings
  └── Welcome & Hub
```

> **Pro Tip:** You can dock the **PlaySync Studio** window next to your Scene or Inspector view for real-time live monitoring during long gameplay testing sessions.

---

## Core Interface Breakdown

```text
┌────────────────────────────────────────────────────────────────────────┐
│  PlaySync Pro Studio                                 [Edit Mode Ready] │
├────────────────────────────────────────────────────────────────────────┤
│  [⚡ Live Diff] [🏛️ Preset Vault] [📜 Flight Recorder] [🎯 Auto-Save] │
│  [💻 C# Patch Gen] [📊 HTML Report] [⚙️ Settings]                      │
├────────────────────────────────────────────────────────────────────────┤
│  Total Changes: 9  | Filter: [All] [Transforms] [Scripts] [Components] │
├────────────────────────────────────────────────────────────────────────┤
│  ▼ Modify Me (Player)                                     Commit Obj   │
│    ☑ Local Position  (0, 1, 0)   ──>  (5.2, 1.0, -12.4)     Transform  │
│    ☑ Speed           10.0        ──>  18.5                  PlayerCtrl │
│    ☑ Jump Force      5.0         ──>  8.2                   PlayerCtrl │
├────────────────────────────────────────────────────────────────────────┤
│  [ ⚡ COMMIT SELECTED CHANGES ]                    [ RESTORE ALL SAFE ]│
│  [ Discard All ]            [ Export JSON ] [ Save Preset ] [ HTML Rep]│
└────────────────────────────────────────────────────────────────────────┘
```

### The 3 Core Interaction Modes

1. **Passive Tracking (Zero Friction):**
   Simply press **Play**, tweak your character, weapons, or UI sliders, and press **Stop**. The lightweight **Quick Restore Window** will automatically pop up with all changed values staged for 1-click restore.

2. **Active Studio Workbench:**
   Open `Tools > ByteLura > PlaySync > PlaySync Studio` before entering Play Mode. Watch changes populate in real time with side-by-side color diffs, filter by category, and commit changes without stopping playback.

3. **In-Inspector Direct Apply:**
   Select any modified GameObject in your Hierarchy. A custom notification banner will appear right at the top of the Inspector header allowing you to commit that specific object's tweaks immediately.

---

## General Settings & Preferences

Open `Tools > ByteLura > PlaySync > Auto-Save Settings` (or the **Settings** tab in PlaySync Studio) to configure default behaviors:

* **Auto-Open Restore Window:** Automatically displays the Quick Restore popup whenever you exit Play Mode with detected changes (*Enabled by default*).
* **Track Inactive Objects:** Allows tracking GameObjects that were disabled or enabled during runtime.
* **Flight Recorder Max Capacity:** Number of historical play sessions stored in local project cache (*Default: 25 sessions*).
* **Scan Frequency:** Background poll interval for change detection (*Default: 0.25 seconds*).

---

## Next Steps

* Follow the [Installation Guide](installation/) to ensure your project meets all requirements.
* Walk through the [5-Minute Quickstart](quick-start/) with the interactive sandbox demo scene.
