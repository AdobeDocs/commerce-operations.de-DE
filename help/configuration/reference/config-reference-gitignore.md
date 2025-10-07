---
title: .gitignore-Referenz
description: Erfahren Sie, wie Sie Dateien zur .gitignore-Liste für Adobe Commerce-Projekte hinzufügen. Best Practices für Versionskontrolle und Dateiausschluss.
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 0%

---

# .gitignore-Referenz

Magento Open Source enthält eine `.gitignore`. Siehe [die neueste Commerce-`.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore). Wenn Sie eine Datei hinzufügen müssen, die sich in der `.gitignore` befindet, können Sie beim Staging eines Commits die Option `-f` (erzwingen) verwenden:

```bash
git add <path/filename> -f
```
