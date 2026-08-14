---
layout: default
title: Scripting API
parent: Scripting & API
nav_order: 2
description: "Programmatic C# editor methods, session triggers, and preset management."
---

# C# Scripting API
{: .no_toc }

Integrate PlaySync Pro directly into your custom editor tools, automated build scripts, and CI/CD pipelines.

---

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## `PlaySyncSession` (Editor Core)

The `PlaySyncSession` class manages the lifecycle of snapshots, active change queues, and commit triggers.

```csharp
#if UNITY_EDITOR
using UnityEditor;
using ByteLura.PlaySync.Editor;

public static class CustomBuildHelper
{
    public static void CheckPendingPlaySyncChanges()
    {
        int changeCount = PlaySyncSession.GetPendingChangeCount();
        if (changeCount > 0)
        {
            UnityEngine.Debug.LogWarning($"[PlaySync] You have {changeCount} uncommitted Play Mode changes staged!");
        }
    }
}
#endif
```

### Static Methods

| Method | Return Type | Description |
|:---|:---|:---|
| `PlaySyncSession.GetPendingChangeCount()` | `int` | Returns total number of staged property changes across active scene objects. |
| `PlaySyncSession.RestoreAllSafe()` | `void` | Automatically commits all non-conflicted staged changes with native Undo. |
| `PlaySyncSession.DiscardAll()` | `void` | Clears all staged changes without writing to active scene objects. |
| `PlaySyncSession.SaveCurrentAsPreset(string name, string desc)` | `PlaySyncPreset` | Creates and serializes a new ScriptableObject balance preset. |

---

## Event Hooks

Subscribe to PlaySync Pro lifecycle events to execute custom logic during Play Mode transitions:

```csharp
#if UNITY_EDITOR
using UnityEditor;
using ByteLura.PlaySync.Editor;

[InitializeOnLoad]
public static class PlaySyncEventSubscriber
{
    static PlaySyncEventSubscriber()
    {
        PlaySyncSession.OnChangesDetected += HandleChangesDetected;
        PlaySyncSession.OnChangesCommitted += HandleChangesCommitted;
    }

    private static void HandleChangesDetected(int changeCount)
    {
        UnityEngine.Debug.Log($"[PlaySync] Captured {changeCount} runtime tweaks upon Play Mode exit.");
    }

    private static void HandleChangesCommitted(int committedCount)
    {
        UnityEngine.Debug.Log($"[PlaySync] Successfully committed {committedCount} properties to scene.");
    }
}
#endif
```
