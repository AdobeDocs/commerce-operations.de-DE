---
title: Zugriffsberechtigungen für Dateisysteme
description: Erfahren Sie, wie Sie den Eigentümer des Commerce-Anwendungsdateisystems für ein Entwicklungs- und Produktionssystem einrichten.
feature: Configuration, Roles/Permissions
exl-id: 95b27db9-5247-4f58-a9af-1590897d73db
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# Zugriffsberechtigungen für Dateisysteme

In diesem Abschnitt wird beschrieben, wie Sie den Eigentümer des Commerce-Dateisystems für ein Entwicklungs- und Produktionssystem einrichten. Bevor Sie fortfahren, sollten Sie die unter [Überblick über die Eigentümerschaft und Berechtigungen des Dateisystems](../../installation/prerequisites/file-system/overview.md) behandelten Konzepte lesen.

Dieser Themenbereich konzentriert sich auf die Entwicklungs- und Produktionssysteme von Commerce. Wenn Sie Commerce installieren, finden Sie weitere Informationen unter [Einrichten von Eigentümern und Berechtigungen vor der Installation](../../installation/prerequisites/file-system/configure-permissions.md).

In den folgenden Abschnitten werden die Anforderungen für einen oder zwei Dateisysteminhaber besprochen. Das bedeutet:

- **Ein Benutzer**: In der Regel bei freigegebenen Hosting-Anbietern erforderlich, die den Zugriff auf nur einen Benutzer auf dem Server ermöglichen. Dieser Benutzer kann sich anmelden, Dateien über FTP übertragen und der Webserver wird auch von diesem Benutzer ausgeführt.

- **Zwei Benutzer**: Wir empfehlen zwei Benutzer, wenn Sie Ihren eigenen Commerce-Server ausführen: einen zum Übertragen von Dateien und zum Ausführen von Befehlszeilen-Dienstprogrammen und einen separaten Benutzer für die Webserver-Software. Wenn möglich, ist dies vorzuziehen, da es sicherer ist.

  Stattdessen haben Sie separate Benutzer:

   - Der Webserver-Benutzer, der den Administrator und die Storefront ausführt.

   - Ein _Befehlszeilenbenutzer_, bei dem es sich um ein lokales Benutzerkonto handelt, mit dem Sie sich beim Server anmelden können. Dieser Benutzer führt Commerce-Cron-Aufträge und Befehlszeilen-Dienstprogramme aus.

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

Um Komponenten zu aktualisieren, neue Komponenten zu installieren oder die Commerce-Software zu aktualisieren, müssen alle vorherigen Ordner schreibgeschützt sein.

#### Codedateien und Ordner schreibgeschützt machen

So entfernen Sie Schreibberechtigungen für Dateien und Ordner aus der Gruppe des Webserver-Benutzers:

1. Melden Sie sich bei Ihrem Commerce-Server an.

1. Wechseln Sie zum Installationsverzeichnis von Commerce.

1. Wechseln Sie in den Produktionsmodus.

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
1. Wechseln Sie zum Installationsverzeichnis von Commerce.
1. Geben Sie die folgenden Befehle ein:

   ```bash
   chmod -R u+w .
   ```

### Optional `magento_umask` festlegen

Siehe [Optional eine Umfrage festlegen](../../installation/next-steps/set-umask.md) im _Installationshandbuch_.

## Eigentümerschaft des Produktionsdateisystems für privates Hosting (zwei Benutzer)

Wenn Sie Ihren eigenen Server verwenden (einschließlich des privaten Server-Setups eines Hosting-Providers), gibt es zwei Benutzer:

- Der **Webserver-Benutzer**, der den Admin und die Storefront ausführt.

  Linux-Systeme bieten für diesen Benutzer in der Regel keine Shell. Sie können sich nicht beim Commerce-Server als Webserver-Benutzer anmelden oder zu ihm wechseln.

- Der **Befehlszeilenbenutzer**, bei dem Sie sich bei Ihrem Commerce-Server als anmelden oder zu ihm wechseln.

  Commerce verwendet diesen Benutzer zum Ausführen von CLI-Befehlen und Cron.

  >[!INFO]
  >
  >Der Befehlszeilenbenutzer wird auch als _Dateisysteminhaber_ bezeichnet.

Da diese Benutzer Zugriff auf dieselben Dateien benötigen, empfehlen wir, eine [freigegebene Gruppe](../../installation/prerequisites/file-system/configure-permissions.md#about-the-shared-group) zu erstellen, zu der sie beide gehören. Die folgenden Verfahren setzen voraus, dass Sie dies bereits getan haben.

Siehe einen der folgenden Abschnitte:

- Zwei Dateisysteminhaber oder Standardmodus
- Zwei Dateisysteminhaber im Produktionsmodus

### Einrichten von zwei Eigentümern für den Standard- oder Entwicklermodus

Dateien in den folgenden Ordnern müssen sowohl vom Benutzer im Entwickler- als auch im Standardmodus schreibbar sein:

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

Setzen Sie das Bit [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) in Verzeichnissen, damit die Berechtigungen immer vom übergeordneten Verzeichnis übernommen werden.

>[!INFO]
>
>`setgid` gilt nur für Verzeichnisse, _nicht_ für Dateien.

Darüber hinaus sollten die Ordner von der Webserver-Gruppe schreibbar sein. Da in diesen Verzeichnissen möglicherweise Inhalt vorhanden ist, fügen Sie die Berechtigungen rekursiv hinzu.

#### Festlegen von Berechtigungen und `setgid`

Festlegen von `setgid` und Berechtigungen für den Entwicklermodus:

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
1. Wechseln Sie zum Installationsverzeichnis von Commerce.
1. Geben Sie als Eigentümer des Dateisystems den folgenden Befehl ein, um in den Produktionsmodus zu wechseln:

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Geben Sie den folgenden Befehl als Benutzer mit `root` -Berechtigungen ein:

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### Code-Dateien und Ordner schreibbar machen

Damit Dateien und Ordner schreibbar sind, können Sie Komponenten aktualisieren und die Commerce-Software aktualisieren:

1. Melden Sie sich bei Ihrem Commerce-Server an.
1. Wechseln Sie zum Installationsverzeichnis von Commerce.
1. Geben Sie den folgenden Befehl ein:

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
