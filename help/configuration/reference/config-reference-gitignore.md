---
title: .gitignore-Referenz
description: Erfahren Sie, wie Sie eine Datei hinzufügen, die in der Ignorieren-Liste enthalten ist.
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '51'
ht-degree: 0%

---

# .gitignore-Referenz

Magento Open Source enthält eine `.gitignore`. Siehe [die neueste Commerce-`.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore). Wenn Sie eine Datei hinzufügen müssen, die sich in der `.gitignore` befindet, können Sie beim Staging eines Commits die Option `-f` (erzwingen) verwenden:

```bash
git add <path/filename> -f
```
