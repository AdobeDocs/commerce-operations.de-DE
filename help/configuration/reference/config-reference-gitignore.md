---
title: .gitignore reference
description: Erfahren Sie, wie Sie eine Datei hinzufügen, die in der Liste "Ignorieren"enthalten ist.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 0%

---


# .gitignore reference

Magento Open Source umfasst eine Basis `.gitignore` -Datei. Siehe [den neuesten Commerce `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) -Datei. Wenn Sie eine Datei hinzufügen müssen, die sich im `.gitignore` -Liste verwenden, können Sie die `-f` (erzwungene) Option beim Staging eines Commit:

```bash
git add <path/filename> -f
```
