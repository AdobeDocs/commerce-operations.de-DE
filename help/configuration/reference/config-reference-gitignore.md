---
title: .gitignore-Referenz
description: Erfahren Sie, wie Sie Dateien zur .gitignore-Liste für Adobe Commerce-Projekte hinzufügen. Best Practices für Versionskontrolle und Dateiausschluss.
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# .gitignore-Referenz

Magento Open Source enthält eine `.gitignore`. Siehe [die neueste Commerce-`.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore). Wenn Sie eine Datei hinzufügen müssen, die sich in der `.gitignore` befindet, können Sie beim Staging eines Commits die Option `-f` (erzwingen) verwenden:

```shell
git add <path/filename> -f
```
