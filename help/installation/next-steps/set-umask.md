---
title: Maske festlegen (optional)
description: Verbessern Sie den Sicherheitszustand Ihrer lokalen Adobe Commerce-Installation, indem Sie die Dateisystemberechtigungen einschränken.
feature: Install, Configuration
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Maske festlegen (optional)

Die Webserver-Gruppe muss über Schreibberechtigungen für bestimmte Ordner im Dateisystem verfügen. Es empfiehlt sich jedoch, die Sicherheit zu erhöhen, insbesondere in der Produktion. Wir bieten Ihnen die Flexibilität, diese Berechtigungen mithilfe einer „umask[ weiter ](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html) beschränken.

Unsere Lösung besteht darin, es Ihnen zu ermöglichen, optional eine Datei mit dem Namen `magento_umask` in Ihrem Anwendungsstammverzeichnis zu erstellen, die die Berechtigungen für die Webservergruppe und alle anderen einschränkt.

>[!NOTE]
>
>Es wird empfohlen, die umask nur auf einem Einbenutzer- oder freigegebenen Hosting-System zu ändern. Wenn Sie über einen privaten Anwendungs-Server verfügen, muss die Gruppe Schreibzugriff auf das Dateisystem haben. Die umask entfernt Schreibzugriff aus der Gruppe.

Die Standardumaske (ohne angegebene `magento_umask`) ist `002`, was bedeutet:

* 775 für Verzeichnisse, was bedeutet volle Kontrolle durch den Benutzer, volle Kontrolle durch die Gruppe, und ermöglicht es jedem, das Verzeichnis zu durchlaufen. Diese Berechtigungen werden normalerweise von Anbietern für freigegebene Hosts benötigt.

* 664 für Dateien, d. h. für den Benutzer schreibbar, für die Gruppe schreibbar und für alle anderen schreibgeschützt

Häufig wird vorgeschlagen, in der `022`-Datei den Wert `magento_umask` zu verwenden. Das bedeutet:

* 755 für Verzeichnisse: Vollständige Kontrolle für den Benutzer, und alle anderen können Verzeichnisse durchlaufen.
* 644 für Dateien: Lese- und Schreibberechtigungen für den Benutzer und Schreibzugriff für alle anderen Benutzer.

So legen `magento_umask` fest:

1. Melden Sie sich als „Dateisystembesitzer“ über ein Befehlszeilen-Terminal [ Ihrem Anwendungs-Server ](../prerequisites/file-system/overview.md).
1. Navigieren Sie zum Installationsverzeichnis der Anwendung:

   ```bash
   cd <Application install directory>
   ```

1. Verwenden Sie den folgenden Befehl, um eine Datei mit dem Namen `magento_umask` zu erstellen und den `umask` Wert darin zu schreiben.

   ```bash
   echo <desired umask number> > magento_umask
   ```

   Sie sollten jetzt eine Datei mit dem Namen `magento_umask` im `<Magento install dir>` haben, wobei der einzige Inhalt die `umask` ist.

1. Melden Sie sich ab und melden Sie sich wieder als [Dateisystemeigentümer“ an](../prerequisites/file-system/overview.md) um die Änderungen anzuwenden.
