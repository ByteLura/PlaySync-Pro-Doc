---
layout: default
title: Scripting & API
nav_order: 6
has_children: true
permalink: /docs/api/
description: "Reference guide for PlaySync Pro C# attributes, events, and scripting integrations."
---

# Scripting & API Reference
{: .no_toc }

PlaySync Pro is designed to be easily extensible from custom C# scripts and editor automation pipelines.

---

## API Documentation

* **[Attributes Reference](attributes/)** — Detailed documentation for `[AutoSavePlayMode]` and serialized field targeting.
* **[C# Scripting API](scripting-api/)** — Programmatic access to `PlaySyncSession`, preset management, and custom event hooks.

---

## Namespaces

PlaySync Pro provides two distinct namespaces:

1. **`ByteLura.PlaySync` (Runtime Namespace):**
   Contains runtime attributes (`[AutoSavePlayMode]`) and data container definitions (`PlaySyncPreset`). Safe to reference in standalone game scripts, builds, and runtime assemblies with zero editor dependencies.

2. **`ByteLura.PlaySync.Editor` (Editor Namespace):**
   Contains editor tracking controllers, diff resolvers, patch generators, and UI window controllers. Wrapped in `#if UNITY_EDITOR` blocks to guarantee clean runtime builds.
