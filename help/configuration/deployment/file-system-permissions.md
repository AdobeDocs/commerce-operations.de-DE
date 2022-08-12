---
title: Zugriffsberechtigungen für Dateisysteme
description: Erfahren Sie, wie Sie den Eigentümer des Commerce-Anwendungs-Dateisystems für ein Entwicklungs- und Produktionssystem einrichten.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 0%

---


# Zugriffsberechtigungen für Dateisysteme

In diesem Abschnitt wird beschrieben, wie Sie den Eigentümer des Commerce-Dateisystems für ein Entwicklungs- und Produktionssystem einrichten. Bevor Sie fortfahren, sollten Sie die unter [Übersicht über die Eigentümerschaft und Berechtigungen des Dateisystems](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

Dieses Thema konzentriert sich auf Commerce-Entwicklungs- und Produktionssysteme. Wenn Sie Commerce installieren, lesen Sie [Festlegen von Eigentümern und Berechtigungen vor der Installation](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html).

In den folgenden Abschnitten werden die Anforderungen für einen oder zwei Dateisysteminhaber besprochen. Das bedeutet:

- **Ein Benutzer**—In der Regel bei freigegebenen Hosting-Anbietern erforderlich, die den Zugriff auf nur einen Benutzer auf dem Server ermöglichen. Dieser Benutzer kann sich anmelden und Dateien über FTP übertragen. Außerdem führt dieser Benutzer den Webserver aus.

- **Zwei Benutzer**—Wir empfehlen zwei Benutzer, wenn Sie Ihren eigenen Commerce-Server ausführen: eine, um Dateien zu übertragen und Befehlszeilen-Dienstprogramme auszuführen, und ein separater Benutzer für die Webserver-Software. Wenn möglich, ist dies vorzuziehen, da es sicherer ist.

   Stattdessen haben Sie separate Benutzer:

   - Der Webserver-Benutzer, der den Administrator und die Storefront ausführt.

   - A _Befehlszeilenbenutzer_: ein lokales Benutzerkonto, mit dem Sie sich beim Server anmelden können. Dieser Benutzer führt Commerce-Cron-Aufträge und Befehlszeilen-Dienstprogramme aus.

## Eigentümerschaft des Produktionsdateisystems für freigegebenes Hosting (ein Benutzer)

Um das Setup eines Eigentümers zu verwenden, müssen Sie sich bei Ihrem Commerce-Server als derselbe Benutzer anmelden, der den Webserver ausführt. Dies ist typisch für freigegebenes Hosting.

Da ein Dateisysteminhaber weniger sicher ist, empfehlen wir, Commerce möglichst auf einem privaten Server anstatt auf freigegebenem Hosting bereitzustellen.

### Einrichten eines Eigentümers im Standard- oder Entwicklermodus

Im Standard- oder Entwicklermodus müssen die folgenden Ordner vom Benutzer schreibbar sein:

- `vendor`
- `app/etc`
- `pub/static`
- `var`
- Alle anderen statischen Ressourcen
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Sie können diese Berechtigungen entweder über die Befehlszeile oder eine Datei-Manager-Anwendung festlegen, die von Ihrem freigegebenen Hosting-Anbieter bereitgestellt wird.

### Einrichten eines Eigentümers für den Produktionsmodus

Wenn Sie bereit sind, Ihre Site für die Produktion bereitzustellen, sollten Sie den Schreibzugriff aus Dateien in den folgenden Verzeichnissen entfernen, um die Sicherheit zu verbessern:

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- Alle anderen statischen Ressourcen
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Um Komponenten zu aktualisieren, neue Komponenten zu installieren oder die Commerce-Software zu aktualisieren, müssen alle vorherigen Verzeichnisse schreibgeschützt sein.

#### Codedateien und Ordner schreibgeschützt machen

So entfernen Sie Schreibberechtigungen für Dateien und Ordner aus der Gruppe des Webserver-Benutzers:

1. Melden Sie sich bei Ihrem Commerce-Server an.

1. Wechseln Sie zum Installationsverzeichnis für Commerce.

1. Wechsel zum Produktionsmodus.

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Entfernen Sie Schreibberechtigungen für die folgenden Ordner.

   ```bash
   find app/code var/view_preprocessed vendor pub/static app/etc generated/code generated/metadata \( -type f -or -type d \) -exec chmod u-w {} + && chmod o-rwx app/etc/env.php
   ```

1. Machen Sie das Befehlszeilen-Tool ausführbar.

   ```bash
   chmod u+x bin/magento
   ```

#### Code-Dateien und Ordner schreibbar machen

Damit Dateien und Ordner schreibbar sind, können Sie Komponenten aktualisieren und die Commerce-Software aktualisieren:

1. Melden Sie sich bei Ihrem Commerce-Server an.
1. Wechseln Sie zum Installationsverzeichnis für Commerce.
1. Geben Sie die folgenden Befehle ein:

   ```bash
   chmod -R u+w .
   ```

### Optional festgelegt `magento_umask`

Siehe [Festlegen einer Umfrage](https://devdocs.magento.com/guides/v2.4/install-gde/install/post-install-umask.html) im _Installationshandbuch_.

## Eigentümerschaft des Produktionsdateisystems für privates Hosting (zwei Benutzer)

Wenn Sie Ihren eigenen Server verwenden (einschließlich des privaten Server-Setups eines Hosting-Providers), gibt es zwei Benutzer:

- Die **Webserver-Benutzer**, wodurch Admin und Storefront ausgeführt werden.

   Linux-Systeme bieten für diesen Benutzer normalerweise keine Shell. Sie können sich nicht beim Commerce-Server als Webserver-Benutzer anmelden oder zu ihm wechseln.

- Die **Befehlszeilenbenutzer**, bei dem Sie sich bei Ihrem Commerce-Server als anmelden oder zu wechseln.

   Commerce verwendet diesen Benutzer zum Ausführen von CLI-Befehlen und Cron.

   >[!INFO]
   >
   >Der Befehlszeilenbenutzer wird auch als _Dateisysteminhaber_.

Da diese Benutzer Zugriff auf dieselben Dateien benötigen, empfehlen wir, eine [freigegebene Gruppe](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html#mage-owner-about-group) denen sie beide angehören. Die folgenden Verfahren setzen voraus, dass Sie dies bereits getan haben.

Siehe einen der folgenden Abschnitte:

- Zwei Dateisysteminhaber im Entwickler- oder Standardmodus
- Zwei Dateisysteminhaber im Produktionsmodus

### Einrichten von zwei Eigentümern für den Standard- oder Entwicklermodus

Dateien in den folgenden Ordnern müssen sowohl vom Benutzer im Entwickler- als auch im Standardmodus schreibbar sein:

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

Legen Sie die [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) in Verzeichnissen hinzugefügt werden, sodass Berechtigungen immer vom übergeordneten Verzeichnis erben.

>[!INFO]
>
>`setgid` gilt nur für Verzeichnisse, _not_ in Dateien.

Darüber hinaus sollten die Ordner von der Webserver-Gruppe schreibbar sein. Da in diesen Verzeichnissen möglicherweise Inhalt vorhanden ist, fügen Sie die Berechtigungen rekursiv hinzu.

#### Berechtigungen festlegen und `setgid`

Zum Festlegen `setgid` und Berechtigungen für den Entwicklermodus:

1. Melden Sie sich bei Ihrem Commerce-Server als Dateisysteminhaber an oder wechseln Sie zu ihm.
1. Geben Sie die folgenden Befehle in der angegebenen Reihenfolge ein:

   ```bash
   cd <magento_root>
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

### Zwei Dateisysteminhaber im Produktionsmodus

Wenn Sie bereit sind, Ihre Site für die Produktion bereitzustellen, sollten Sie den Schreibzugriff aus Dateien in den folgenden Verzeichnissen entfernen, um die Sicherheit zu verbessern:

- `vendor`
- `app/code`
- `app/etc`
- `lib`
- `pub/static`
- Alle anderen statischen Ressourcen
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

#### Codedateien und Ordner schreibgeschützt machen

So entfernen Sie Schreibberechtigungen für Dateien und Ordner aus der Gruppe des Webserver-Benutzers:

1. Melden Sie sich bei Ihrem Commerce-Server an.
1. Wechseln Sie zum Installationsverzeichnis für Commerce.
1. Geben Sie als Eigentümer des Dateisystems den folgenden Befehl ein, um in den Produktionsmodus zu wechseln:

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Geben Sie den folgenden Befehl als Benutzer mit `root` -Berechtigungen:

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### Code-Dateien und Ordner schreibbar machen

Damit Dateien und Ordner schreibbar sind, können Sie Komponenten aktualisieren und die Commerce-Software aktualisieren:

1. Melden Sie sich bei Ihrem Commerce-Server an.
1. Wechseln Sie zum Installationsverzeichnis für Commerce.
1. Geben Sie den folgenden Befehl ein:

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```