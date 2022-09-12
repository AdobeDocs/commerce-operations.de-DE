---
title: Festlegen einer Umfrage (optional)
description: Verbessern Sie die Sicherheitsbereitschaft Ihrer Adobe Commerce- oder Magento Open Source-Installation vor Ort, indem Sie die Dateisystemberechtigungen einschränken.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# Festlegen einer Umfrage (optional)

Die Webserver-Gruppe muss über Schreibberechtigungen für bestimmte Ordner im Dateisystem verfügen. Sie möchten jedoch möglicherweise eine höhere Sicherheit, insbesondere in der Produktion. Wir bieten Ihnen die Flexibilität, diese Berechtigungen mithilfe eines [umfragen](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

Unsere Lösung besteht darin, Ihnen die Möglichkeit zu geben, optional eine Datei mit dem Namen `magento_umask` in Ihrem Stammverzeichnis der Anwendung, das die Berechtigungen für die Webservergruppe und alle anderen einschränkt.

>[!NOTE]
>
>Es wird empfohlen, die Umfrage nur für ein einzelnes oder freigegebenes Hosting-System zu ändern. Wenn Sie über einen privaten Anwendungsserver verfügen, muss die Gruppe Schreibzugriff auf das Dateisystem haben. Die Umfrage entfernt Schreibzugriff von der Gruppe.

Standardumfrage (ohne `magento_umask` specified) `002`, was bedeutet:

* 775 für Verzeichnisse, was bedeutet volle Kontrolle durch den Benutzer, volle Kontrolle durch die Gruppe, und ermöglicht jedem, das Verzeichnis zu durchlaufen. Diese Berechtigungen sind normalerweise für freigegebene Hosting-Anbieter erforderlich.

* 664 für Dateien, was bedeutet, dass der Benutzer schreiben kann, von der Gruppe geschrieben werden kann, und schreibgeschützt für alle anderen

Ein häufiger Vorschlag besteht darin, den Wert `022` im `magento_umask` -Datei, d. h.:

* 755 für Verzeichnisse: volle Kontrolle für den Benutzer, und alle anderen können Verzeichnisse durchlaufen.
* 644 für Dateien: Lese- und Schreibberechtigungen für den Benutzer und Schreibzugriff für alle anderen Benutzer.

Zum Festlegen `magento_umask`:

1. Melden Sie sich in einem Befehlszeilen-Terminal bei Ihrem Anwendungsserver als [Dateisysteminhaber](../prerequisites/file-system/overview.md).
1. Navigieren Sie zum Installationsverzeichnis der Anwendung:

   ```bash
   cd <Application install directory>
   ```

1. Verwenden Sie den folgenden Befehl, um eine Datei mit dem Namen `magento_umask` und schreiben Sie die `umask` -Wert.

   ```bash
   echo <desired umask number> > magento_umask
   ```

   Sie sollten jetzt eine Datei mit dem Namen `magento_umask` im `<Magento install dir>` , wobei der einzige Inhalt die `umask` Zahl.

1. Melden Sie sich ab und melden Sie sich als [Dateisysteminhaber](../prerequisites/file-system/overview.md) , um die Änderungen anzuwenden.
