---
title: Festlegen einer Umfrage (optional)
description: Verbessern Sie die Sicherheitsbereitschaft Ihrer Adobe Commerce-Installation vor Ort, indem Sie die Dateisystemberechtigungen einschränken.
feature: Install, Configuration
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Festlegen einer Umfrage (optional)

Die Webserver-Gruppe muss über Schreibberechtigungen für bestimmte Ordner im Dateisystem verfügen. Sie können jedoch eine strengere Sicherheit insbesondere in der Produktion wünschen. Wir bieten Ihnen die Flexibilität, diese Berechtigungen mithilfe eines [umask](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html) weiter einzuschränken.

Unsere Lösung besteht darin, Ihnen die Möglichkeit zu geben, optional eine Datei mit dem Namen `magento_umask` in Ihrem Stammverzeichnis der Anwendung zu erstellen, die die Berechtigungen für die Gruppe der Webserver und alle anderen einschränkt.

>[!NOTE]
>
>Es wird empfohlen, die Umfrage nur für ein einzelnes oder freigegebenes Hosting-System zu ändern. Wenn Sie über einen privaten Anwendungsserver verfügen, muss die Gruppe Schreibzugriff auf das Dateisystem haben. Die Umfrage entfernt Schreibzugriff von der Gruppe.

Die standardmäßige Umfrage (ohne &quot;`magento_umask`&quot;) ist &quot;`002`&quot;, was bedeutet:

* 775 für Verzeichnisse, was bedeutet volle Kontrolle durch den Benutzer, volle Kontrolle durch die Gruppe, und ermöglicht jedem, das Verzeichnis zu durchlaufen. Diese Berechtigungen sind normalerweise von freigegebenen Hosting-Anbietern erforderlich.

* 664 für Dateien, was bedeutet, dass der Benutzer schreiben kann, von der Gruppe geschrieben werden kann, und schreibgeschützt für alle anderen

Ein häufiger Vorschlag besteht darin, den Wert `022` in der Datei `magento_umask` zu verwenden, was Folgendes bedeutet:

* 755 für Verzeichnisse: volle Kontrolle für den Benutzer, und alle anderen können Verzeichnisse durchlaufen.
* 644 für Dateien: Lese- und Schreibberechtigungen für den Benutzer und schreibgeschützt für alle anderen.

Festlegen von `magento_umask`:

1. Melden Sie sich in einem Befehlszeilen-Terminal bei Ihrem Anwendungsserver als [Dateisysteminhaber](../prerequisites/file-system/overview.md) an.
1. Navigieren Sie zum Installationsverzeichnis der Anwendung:

   ```bash
   cd <Application install directory>
   ```

1. Verwenden Sie den folgenden Befehl, um eine Datei mit dem Namen `magento_umask` zu erstellen und den Wert `umask` darin zu schreiben.

   ```bash
   echo <desired umask number> > magento_umask
   ```

   Sie sollten jetzt eine Datei mit dem Namen `magento_umask` im `<Magento install dir>` haben, wobei der einzige Inhalt die Nummer `umask` ist.

1. Melden Sie sich ab und melden Sie sich wieder als [Dateisysteminhaber](../prerequisites/file-system/overview.md) an, um die Änderungen anzuwenden.
