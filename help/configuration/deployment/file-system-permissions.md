---
title: Zugriffsberechtigungen für Dateisysteme
description: Erfahren Sie, wie Sie den/die Verantwortlichen des Commerce-Anwendungsdateisystems für ein Entwicklungs- und Produktionssystem einrichten.
feature: Configuration, Roles/Permissions
exl-id: 95b27db9-5247-4f58-a9af-1590897d73db
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# Zugriffsberechtigungen für Dateisysteme

In diesem Abschnitt wird beschrieben, wie Sie den/die Verantwortlichen für das Commerce-Dateisystem für ein Entwicklungs- und Produktionssystem einrichten. Bevor Sie fortfahren, lesen Sie die Konzepte unter [Übersicht über Dateisystemeigentum und -berechtigungen](../../installation/prerequisites/file-system/overview.md).

In diesem Abschnitt werden Entwicklungs- und Produktionssysteme für Commerce vorgestellt. Wenn Sie Commerce installieren, lesen Sie [Festlegen von Eigentum und Berechtigungen für die Vorinstallation](../../installation/prerequisites/file-system/configure-permissions.md).

In den folgenden Abschnitten werden die Anforderungen für einen oder zwei Dateisystembesitzer erläutert. Das bedeutet:

- **Ein Benutzer** - Wird in der Regel bei Anbietern für gemeinsam genutztes Hosting benötigt, die Ihnen den Zugriff auf nur einen Benutzer auf dem Server ermöglichen. Dieser Benutzer kann sich anmelden, Dateien über FTP übertragen, und dieser Benutzer führt auch den Webserver aus.

- **Zwei Benutzer** - Wenn Sie Ihren eigenen Commerce-Server ausführen, empfehlen wir zwei Benutzer: einen zum Übertragen von Dateien und Ausführen von Befehlszeilen-Dienstprogrammen und einen separaten Benutzer für die Webserver-Software. Wenn möglich, ist dies vorzuziehen, da es sicherer ist.

  Stattdessen haben Sie separate Benutzer:

   - Der Webserver-Benutzer, der die Admin- und Storefront ausführt.

   - Ein _Befehlszeilenbenutzer“,_ ein lokales Benutzerkonto ist, mit dem Sie sich beim Server anmelden können. Dieser Anwender führt Commerce Cron-Aufträge und Befehlszeilen-Dienstprogramme aus.

## Eigentümerschaft am Produktionsdateisystem für freigegebenes Hosting (ein Benutzer)

Um das One-Owner-Setup zu verwenden, müssen Sie sich beim Commerce-Server als derselbe Benutzer anmelden, der den Webserver ausführt. Dies ist typisch für freigegebenes Hosting.

Da es weniger sicher ist, einen Dateisystembesitzer zu haben, empfehlen wir, Commerce in der Produktion auf einem privaten Server bereitzustellen, anstatt auf freigegebenem Hosting, sofern möglich.

### Einen Besitzer für den Standard- oder Entwicklermodus einrichten

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

### Einen Verantwortlichen für den Produktionsmodus einrichten

Wenn Sie bereit sind, Ihre Site für die Produktion bereitzustellen, sollten Sie den Schreibzugriff aus Dateien in den folgenden Verzeichnissen entfernen, um die Sicherheit zu verbessern:

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- Alle anderen statischen Ressourcen
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Um Komponenten zu aktualisieren, neue Komponenten zu installieren oder die Commerce-Software zu aktualisieren, müssen alle vorangehenden Verzeichnisse Lese- und Schreibzugriff besitzen.

#### Code-Dateien und Verzeichnisse schreibgeschützt machen

So entfernen Sie Schreibberechtigungen für Dateien und Ordner aus der Gruppe der Webserverbenutzer:

1. Melden Sie sich beim Commerce-Server an.

1. Wechseln Sie in das Commerce-Installationsverzeichnis.

1. Wechseln Sie in den Produktionsmodus .

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

#### Schreiben von Code-Dateien und Verzeichnissen

So machen Sie Dateien und Verzeichnisse schreibbar, damit Sie Komponenten aktualisieren und die Commerce-Software aktualisieren können:

1. Melden Sie sich beim Commerce-Server an.
1. Wechseln Sie in das Commerce-Installationsverzeichnis.
1. Geben Sie die folgenden Befehle ein:

   ```bash
   chmod -R u+w .
   ```

### Optional `magento_umask` festlegen

Siehe [Optional eine Umaske festlegen](../../installation/next-steps/set-umask.md) im _Installationshandbuch_.

## Eigentümerschaft am Produktionsdateisystem für privates Hosting (zwei Benutzer)

Wenn Sie Ihren eigenen Server verwenden (einschließlich des privaten Server-Setups eines Hosting-Anbieters), gibt es zwei Benutzer:

- Der **Webserver-Benutzer**, der die Admin- und Storefront ausführt.

  Linux-Systeme stellen für diesen Benutzer in der Regel keine Shell bereit. Sie können sich nicht als Webserver-Benutzer beim Commerce-Server anmelden oder zu diesem wechseln.

- Der **Befehlszeilenbenutzer**, mit dem Sie sich beim Commerce-Server anmelden oder zu dem Sie wechseln.

  Commerce verwendet diesen Benutzer, um CLI-Befehle und Cron auszuführen.

  >[!INFO]
  >
  >Der Befehlszeilenbenutzer wird auch als &quot;_&quot;_.

Da diese Benutzer Zugriff auf dieselben Dateien benötigen, empfehlen wir, eine [freigegebene Gruppe“ zu erstellen](../../installation/prerequisites/file-system/configure-permissions.md#about-the-shared-group) der sie beide angehören. Bei den folgenden Verfahren wird davon ausgegangen, dass Sie dies bereits getan haben.

Siehe einen der folgenden Abschnitte:

- Zwei Dateisystembesitzer im Entwickler- oder Standardmodus
- Zwei Dateisystembesitzer im Produktionsmodus

### Zwei Eigentümer für den Standard- oder Entwicklermodus einrichten

Dateien in den folgenden Verzeichnissen müssen sowohl im Entwickler- als auch im Standardmodus schreibgeschützt sein:

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

Legen Sie das [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/)-Bit für Ordner fest, sodass Berechtigungen immer vom übergeordneten Ordner erben.

>[!INFO]
>
>`setgid` gilt nur für Verzeichnisse _nicht_ Dateien.

Darüber hinaus sollten die Ordner von der Webservergruppe beschreibbar sein. Da in diesen Verzeichnissen möglicherweise Inhalte vorhanden sind, fügen Sie die Berechtigungen rekursiv hinzu.

#### Festlegen von Berechtigungen und `setgid`

So legen Sie `setgid` und Berechtigungen für den Entwicklermodus fest:

1. Melden Sie sich bei Ihrem Commerce-Server als Dateisystembesitzer an oder wechseln Sie zu diesem.
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

### Zwei Dateisystembesitzer im Produktionsmodus

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

#### Code-Dateien und Verzeichnisse schreibgeschützt machen

So entfernen Sie Schreibberechtigungen für Dateien und Ordner aus der Gruppe der Webserverbenutzer:

1. Melden Sie sich beim Commerce-Server an.
1. Wechseln Sie in das Commerce-Installationsverzeichnis.
1. Geben Sie als Verantwortlicher für das Dateisystem den folgenden Befehl ein, um in den Produktionsmodus zu wechseln:

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Geben Sie den folgenden Befehl als Benutzer mit `root` ein:

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### Schreiben von Code-Dateien und Verzeichnissen

So machen Sie Dateien und Verzeichnisse schreibbar, damit Sie Komponenten aktualisieren und die Commerce-Software aktualisieren können:

1. Melden Sie sich beim Commerce-Server an.
1. Wechseln Sie in das Commerce-Installationsverzeichnis.
1. Geben Sie den folgenden Befehl ein:

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
