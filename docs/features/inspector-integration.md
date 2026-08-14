---
layout: default
title: Inspector Integration
parent: Core Features
nav_order: 3
description: "Discover in-inspector change banners, direct Apply Now buttons, and context menu helpers."
---

# Direct Inspector Integration
{: .no_toc }

PlaySync Pro embeds contextual helpers directly inside Unity's native Component Inspectors, allowing developers to inspect and commit tweaks without switching windows.

---

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## In-Inspector Change Header

When you select a GameObject in the Hierarchy that has active runtime modifications, PlaySync Pro draws a clean, dark-theme status header at the top of the standard Inspector:

```text
┌────────────────────────────────────────────────────────────────────────┐
│ ⚡ PlaySync: Unsaved Changes                            [ Apply Now ]  │
├────────────────────────────────────────────────────────────────────────┤
│ • Local Rotation                                     (-0.01, -0.02, 0) │
│ • Local Position                                     (-3.56, 2.27, 0)  │
│ • Local Scale                                        (1.0, 1.0, 2.64)  │
│ • BoxCollider Size                                   (1.0, 1.0, 1.2)   │
│ • BoxCollider Center                                 (0.35, 0.0, 0.0)  │
└────────────────────────────────────────────────────────────────────────┘
```

### Key Capabilities
* **Immediate Visual Feedback:** Identifies modified GameObjects instantly when selecting items in the Hierarchy.
* **1-Click "Apply Now":** Commits all pending changes for that specific GameObject directly into your scene.
* **Component-Specific Breakdown:** Lists each modified property with its current staged value.

---

## Right-Click Context Menu Actions

You can right-click any Component header in the Inspector to access PlaySync Pro quick actions:

```text
Component Header > Right Click:
  ├── PlaySync > Commit Component Changes
  ├── PlaySync > Revert Component to Edit Mode
  ├── PlaySync > Copy Values as C# Code Patch
  └── PlaySync > Add [AutoSavePlayMode] Rule
```

---

## SceneView Floating HUD Bar

During active Play Mode sessions, PlaySync Pro optionally renders a lightweight, non-intrusive floating HUD pill at the top-center of the SceneView:

```text
┌──────────────────────────────────────────────────────────────┐
│  ⚡ PlaySync: 9 Changes Tracked   [ View Diff ]  [ Quick Save ]│
└──────────────────────────────────────────────────────────────┘
```

* **Zero Frame Impact:** Rendered using lightweight IMGUI overlays without blocking scene gizmos or camera navigation.
* **Live Counter:** Updates in real time as physics or script values drift during gameplay testing.
* **Quick Save:** Commits the current runtime state directly into Edit Mode memory on the fly.

> **Pro Tip:** You can toggle the SceneView HUD on or off in `Tools > ByteLura > PlaySync > Auto-Save Settings`.
