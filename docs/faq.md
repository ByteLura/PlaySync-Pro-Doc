---
layout: default
title: FAQ & Troubleshooting
nav_order: 8
description: "Frequently asked questions, common troubleshooting steps, and best practices."
---

# Frequently Asked Questions & Troubleshooting
{: .no_toc }

Find quick answers to common questions about PlaySync Pro workflows, compatibility, and edge cases.

---

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## General Questions

### Does PlaySync Pro work in standalone builds?
PlaySync Pro's editor features (Studio, Quick Restore Window, Flight Recorder) run exclusively within the Unity Editor environment. However, the `[AutoSavePlayMode]` attribute and `PlaySyncPreset` container compile cleanly into standalone builds with zero runtime footprint.

### How does PlaySync Pro handle Unity Undo?
Every single property restore operation calls `Undo.RecordObject()` before writing the new value and marks the component dirty with `EditorUtility.SetDirty()`. You can immediately press `Ctrl+Z` / `Cmd+Z` in the editor to undo any restore action.

### Does PlaySync Pro break Prefab links?
No. When restoring properties on a Prefab instance located in an active scene, PlaySync Pro applies standard instance property overrides without breaking the root prefab connection.

---

## Troubleshooting Common Issues

### 1. The Quick Restore Window didn't pop up upon exiting Play Mode.
* **Check Settings:** Open `Tools > ByteLura > PlaySync > Auto-Save Settings` and ensure **Auto-Open Restore Window on Exit** is checked.
* **Zero Changes Detected:** If no serialized properties were altered during the session, the popup will not trigger to prevent clutter.
* **Manual Access:** You can always open the window manually via `Tools > ByteLura > PlaySync > Quick Restore Window` (`Ctrl+Alt+R`).

### 2. A private field on my custom MonoBehaviour is not being tracked.
* Private fields in Unity C# are only serialized if they are decorated with `[SerializeField]`. Ensure your field has `[SerializeField]` above it:
  ```csharp
  [SerializeField] private float moveSpeed = 10f;
  ```

### 3. Flight Recorder history is missing after clearing project cache.
* Flight Recorder JSON logs are stored locally in `[Project]/Library/PlaySyncHistory/`. If you delete the `Library/` directory to rebuild your project cache, local session history will be reset.
* Important game balance configurations should always be saved as **ScriptableObject Presets** (stored permanently in `Assets/PlaySyncPresets/`).

---

## Support & Community

* **Publisher Support:** Contact us at `support@bytelura.com`
* **Official Website:** [https://bytelura.com](https://bytelura.com)
* **Unity Asset Store Page:** [ByteLura Asset Store Publisher](https://assetstore.unity.com/publishers/128366)
