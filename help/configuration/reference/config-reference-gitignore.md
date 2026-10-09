---
title: .gitignore-Referenz
description: Erfahren Sie, wie Sie Dateien zur .gitignore-Liste für Adobe Commerce-Projekte hinzufügen. Best Practices für Versionskontrolle und Dateiausschluss.
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%
---
# .gitignore-Referenz

Magento Open Source enthält eine `.gitignore`. Siehe [die neueste Commerce-`.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore). Wenn Sie eine Datei hinzufügen müssen, die sich in der `.gitignore` befindet, können Sie beim Staging eines Commits die Option `-f` (erzwingen) verwenden:

```shell
git add <path/filename> -f
```
