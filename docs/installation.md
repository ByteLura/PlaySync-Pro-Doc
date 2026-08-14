---
layout: default
title: Installation
nav_order: 3
description: "How to purchase, download, and install PlaySync Pro into your Unity projects."
---

# Installation
{: .no_toc }

PlaySync Pro is a commercial Unity Editor extension distributed exclusively through the **Unity Asset Store**. Follow the steps below to import the package and verify your environment.

---

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Purchasing & Licensing

PlaySync Pro is available under standard Unity Asset Store licensing for both individual creators and development teams.

1. Visit the official store page: [PlaySync Pro on Unity Asset Store](https://assetstore.unity.com/publishers/128366).
2. Click **Add to My Assets** (or **Buy Now**).
3. Ensure you are signed in with the Unity ID associated with your development organization.

> **Important:** PlaySync Pro source code and binaries are licensed exclusively through the Unity Asset Store. Free or unauthenticated redistribution outside the Unity Package ecosystem is strictly prohibited.

---

## Importing into Your Unity Project

Once added to your Unity ID:

1. Open your Unity Project in **Unity 2021.3 LTS**, **2022.3 LTS**, or **Unity 6**.
2. Go to the top menu and select **Window > Package Manager**.
3. In the Package Manager dropdown (top-left), select **Packages: My Assets**.
4. In the search bar, type `PlaySync Pro`.
5. Click **Download**, then click **Import**.
6. In the Import Package window, ensure all files under `Assets/PlaySync/` are checked and click **Import**.

```text
Assets/
└── PlaySync/
    ├── Editor/
    │   ├── Core/           (Session manager, tracker, snapshots)
    │   ├── UI/             (Studio, Restore, Presets, Hub windows)
    │   ├── Utils/          (C# generator, HTML report exporter)
    │   └── Styles/         (Dark theme UI styles & layouts)
    ├── Runtime/
    │   ├── Attributes/     ([AutoSavePlayMode])
    │   └── Presets/        (PlaySyncPreset ScriptableObject definition)
    └── Documentation/      (Quickstart guide & release notes)
```

---

## Verifying Installation

After import is complete:

1. Look at your Unity console to ensure there are zero compilation errors.
2. Check the top menu bar for the new menu entry: `Tools > ByteLura > PlaySync`.
3. Open `Tools > ByteLura > PlaySync > Welcome & Hub`.
4. If you see the **PlaySync Pro Dashboard** with green status indicators, the tool is fully installed and ready to use!

---

## System & Project Requirements

| Requirement | Minimum Supported | Recommended |
|:---|:---|:---|
| **Unity Editor** | Unity 2021.3 LTS | Unity 2022.3 LTS / Unity 6 |
| **Operating System** | Windows 10/11, macOS 11+, Linux | Windows 11 / macOS Sonoma |
| **C# Language** | C# 9.0 (.NET Standard 2.1 / .NET Core) | C# 10 / C# 11 |
| **Render Pipeline** | Built-in RP, URP 12+, HDRP 12+ | URP / HDRP (Unity 6) |
| **Dependencies** | None (Zero external DLLs or packages) | Standalone |

---

## Upgrading to Newer Releases

When updating PlaySync Pro from the Asset Store:

1. Open **Window > Package Manager > My Assets**.
2. Click **Update** on PlaySync Pro.
3. Import the updated files. Your existing presets (`.asset`), local flight history (`Library/PlaySyncHistory/`), and project settings are stored safely outside the package code folder and will never be overwritten.
