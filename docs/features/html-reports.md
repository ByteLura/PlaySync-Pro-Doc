---
layout: default
title: HTML Change Reports
parent: Core Features
nav_order: 8
description: "Generate self-contained dark-theme HTML change reports for pull requests, QA reviews, and game design handoffs."
---

# Team-Ready HTML Change Reports
{: .no_toc }

Communicating runtime gameplay adjustments to level designers, programmers, and QA leads often creates communication bottlenecks. PlaySync Pro's **HTML Change Report Generator** turns staged session tweaks into beautiful, standalone web reports with one click.

---

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Generating an HTML Report

1. Open `Tools > ByteLura > PlaySync > PlaySync Studio`.
2. Navigate to the **HTML Report** tab (or click **HTML Report** in the Quick Restore footer).
3. Fill in optional report metadata:
   * **Project / Build Name:** (e.g., `PlayModeSave_Milestone_Alpha_3`)
   * **Author / Designer Name:** (e.g., `Alex (Lead Game Designer)`)
   * **Category Filters:** Check or uncheck Transforms, Scripts, Components, Prefabs.
4. Click **⚡ Generate & Open HTML Report**.

The report is compiled in under 1 second and automatically opens in your default web browser!

---

## Sample Report Layout

```text
┌────────────────────────────────────────────────────────────────────────┐
│  ⚡ PlaySync Pro   ● 9 Changes Tracked                                 │
│                                                                        │
│  Play Mode Change Report                                               │
│  Play Mode Save · DemoScene · Sat, Aug 15 2026 01:43                   │
├────────────────────────────────────────────────────────────────────────┤
│  AUTHOR: Alex (Lead Designer)    │  SCENE: DemoScene                   │
│  OBJECTS MODIFIED: 2             │  TOTAL CHANGES: 9                   │
├────────────────────────────────────────────────────────────────────────┤
│  [  9  ]       [  5  ]      [  0  ]      [  4  ]      [  0  ]          │
│   TOTAL       TRANSFORM      SCRIPT     COMPONENT     PREFAB           │
├────────────────────────────────────────────────────────────────────────┤
│  ▼ Modify Me (Cube) (5 changes)                                        │
│  ┌───────────────────────────────────────────────────────────────────┐ │
│  │ Property           Type         WAS             NOW               │ │
│  │ Local Rotation     Transform    (0, 0, 0)       (-0.01, -0.02, 0) │ │
│  │ Local Position     Transform    (-1.5, 0.5, 0)  (-3.56, 2.27, 0)  │ │
│  │ BoxCollider Size   BoxCollider  (1, 1, 1)       (1.0, 1.0, 1.2)   │ │
│  │ BoxCollider Center BoxCollider  (0, 0, 0)       (0.35, 0, 0)      │ │
│  └───────────────────────────────────────────────────────────────────┘ │
└────────────────────────────────────────────────────────────────────────┘
```

---

## Key Benefits for Development Teams

* **100% Self-Contained:** Zero external CSS or JavaScript dependencies. All styling is embedded inside a single `.html` file that can be emailed, shared over Slack, or attached to Jira issues.
* **Side-by-Side Visual Diff Tables:** Color-coded `WAS` (red/dim) vs `NOW` (emerald green) comparison for instant verification.
* **Pull Request Documentation:** Attach the HTML report directly to your GitHub/GitLab pull request to provide undeniable visual proof of balance adjustments.
* **Automatic Storage:** Reports are saved in `[Project]/PlaySyncReports/` with ISO timestamps for easy archival.

> **Pro Tip:** You can customize your organization's name and default author credit inside `Tools > ByteLura > PlaySync > Auto-Save Settings`.
