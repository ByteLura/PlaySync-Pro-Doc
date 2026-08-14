---
layout: default
title: Attributes Reference
parent: Scripting & API
nav_order: 1
description: "Reference guide for the [AutoSavePlayMode] attribute and field serialization rules."
---

# Attributes Reference
{: .no_toc }

PlaySync Pro provides clean C# attributes to declare persistence behavior directly on your classes and serialized fields.

---

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## `[AutoSavePlayMode]`

The `[AutoSavePlayMode]` attribute marks a MonoBehaviour class or specific field for automatic persistence when exiting Play Mode, bypassing the need for manual staging in the Quick Restore Window.

### Syntax
```csharp
namespace ByteLura.PlaySync
{
    [AttributeUsage(AttributeTargets.Class | AttributeTargets.Field | AttributeTargets.Property, AllowMultiple = false, Inherited = true)]
    public class AutoSavePlayModeAttribute : PropertyAttribute
    {
        public bool PersistChildren { get; set; } = true;
        public string CategoryTag { get; set; } = "";
        
        public AutoSavePlayModeAttribute() {}
        public AutoSavePlayModeAttribute(string categoryTag) { CategoryTag = categoryTag; }
    }
}
```

---

## Usage Examples

### 1. Class-Level Auto-Save (All Fields Persist)
Decorating an entire class instructs PlaySync Pro to persist all serialized variables on that component automatically:

```csharp
using UnityEngine;
using ByteLura.PlaySync;

[AutoSavePlayMode]
public class EnemyAIBalance : MonoBehaviour
{
    public float patrolSpeed = 3.5f;
    public float chaseSpeed = 8.0f;
    public float detectionRadius = 15.0f;
    public LayerMask targetMask;
}
```

### 2. Field-Level Auto-Save (Selective Variables)
Decorating individual fields allows fine-grained control:

```csharp
using UnityEngine;
using ByteLura.PlaySync;

public class WeaponController : MonoBehaviour
{
    // Auto-persist gameplay tuning parameters:
    [AutoSavePlayMode]
    [SerializeField] private float fireRate = 0.12f;

    [AutoSavePlayMode]
    [SerializeField] private Vector3 recoilAngle = new Vector3(-2f, 0.5f, 0f);

    // Runtime state that should NOT persist:
    public int currentLoadedAmmo = 30;
    public bool isReloading = false;
}
```

---

## Compilation & Build Safety

`[AutoSavePlayMode]` is packaged in the runtime assembly `ByteLura.PlaySync.Runtime.dll`. It adds zero runtime overhead and can be left active in standalone PC, Console, Mobile, and WebGL shipping builds.
