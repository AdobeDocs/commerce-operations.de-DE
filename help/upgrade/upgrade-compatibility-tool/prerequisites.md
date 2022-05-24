---
title: '"[!DNL Upgrade Compatibility Tool] Voraussetzungen"'
description: 'Stellen Sie sicher, dass Ihr System die zum Ausführen des [!DNL Upgrade Compatibility Tool] für Ihr Adobe Commerce-Projekt. '
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] Voraussetzungen

{{commerce-only}

Die Mindestanforderungen für die Ausführung der [!DNL Upgrade Compatibility Tool] sind:

| **Voraussetzungen** | **Einschränkungen** |
|----------------|-----------------|
| PHP-Version | >= 7.3 |
| Verfasser | Keine |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`oder `>=16.0.0`) |
| Speicherbeschränkungen | Mindestens 2 GB RAM |
| Zugriffsschlüssel für Adobe Commerce | Keine |
| Adobe Commerce | Keine |

Sie können die [!DNL Upgrade Compatibility Tool] in verschiedenen Betriebssystemen (Windows wird nicht unterstützt). Sie müssen die [!DNL Upgrade Compatibility Tool] wo sich Ihre Adobe Commerce-Instanz befindet.

Es ist notwendig, [!DNL Upgrade Compatibility Tool] , um Zugriff auf den Quellcode der Adobe Commerce-Instanz zu erhalten. Sie können es beispielsweise auf einem Server installieren und auf eine andere Adobe Commerce-Installation verweisen. Siehe Abschnitt [install](../upgrade-compatibility-tool/install.md) für weitere Informationen.

Wenn Sie die [!DNL Upgrade Compatibility Tool] Bei einer Adobe Commerce-Instanz mit großen Modulen und Dateien erfordert das Tool möglicherweise eine hohe RAM-Menge (mindestens 2 GB). Sie können die `[=MODULE-PATH]` -Option in Ihrem -Befehl zum Angeben des Modulpfadverzeichnisses, um Probleme aufgrund einer Speicherbegrenzung zu vermeiden:

```bash
bin/uct upgrade:check <dir> -m[=MODULE-PATH]
```

Wenn die Argumente wie folgt lauten:

- `<dir>`: Installationsordner von Adobe Commerce.
- `[=MODULE-PATH]`: Spezifisches Modulpfadverzeichnis.
