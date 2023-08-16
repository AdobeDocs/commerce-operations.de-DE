---
title: Aktivieren oder Deaktivieren des Wartungsmodus
description: Führen Sie diese Schritte aus, um anzupassen, was Kunden sehen, wenn Ihre Adobe Commerce- oder Magento Open Source-Bereitstellung zur Wartung heruntergefahren ist.
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# Aktivieren oder Deaktivieren des Wartungsmodus

Das folgende Handbuch bezieht sich auf eine Seite mit dem Standard-Wartungsmodus. Wenn Sie eine benutzerdefinierte Wartungsseite verwenden müssen, lesen Sie [Benutzerdefinierte Wartungsseite erstellen](../../upgrade/troubleshooting/maintenance-mode-options.md) Thema.

Verwendung von Adobe Commerce und Magento Open Source [Wartungsmodus](../../configuration/bootstrap/application-modes.md#maintenance-mode) zum Deaktivieren des Bootstrapping. Die Deaktivierung des Bootstrapping ist hilfreich, wenn Sie Ihre Site verwalten, aktualisieren oder neu konfigurieren.

Das Programm erkennt den Wartungsmodus wie folgt:

* Wenn `var/.maintenance.flag` nicht vorhanden ist, ist der Wartungsmodus deaktiviert und die Anwendung funktioniert normal.
* Andernfalls ist der Wartungsmodus aktiviert, sofern `var/.maintenance.ip` vorhanden ist.

  `var/.maintenance.ip` kann eine Liste von IP-Adressen enthalten. Wenn über HTTP auf einen Einstiegspunkt zugegriffen wird und die Client-IP-Adresse einem der Einträge in dieser Liste entspricht, ist der Wartungsmodus deaktiviert.

## Installieren des Programms

Bevor Sie diesen Befehl zum Aktivieren oder Deaktivieren des Wartungsmodus verwenden, müssen Sie [Installieren des Programms](../advanced.md).

## Aktivieren oder Deaktivieren des Wartungsmodus

Verwenden Sie die `magento maintenance` CLI-Befehl zum Aktivieren oder Deaktivieren des Wartungsmodus.

Befehlsverwendung:

```bash
bin/magento maintenance:enable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:disable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:status
```

Die `--ip=<ip address>` ist eine IP-Adresse, die vom Wartungsmodus ausgenommen werden soll (z. B. Entwickler, die die Wartung durchführen). Verwenden Sie die Option mehrmals, um mehrere IP-Adressen im selben Befehl auszuschließen.

>[!NOTE]
>
>Verwenden `--ip=<ip address>` mit `magento maintenance:disable` speichert die Liste der IPs zur späteren Verwendung. Um die Liste der ausgenommenen IPs zu löschen, verwenden Sie `magento maintenance:enable --ip=none` oder [Liste der ausgenommenen IP-Adressen beibehalten](#maintain-the-list-of-exempt-ip-addresses).

Die `bin/magento maintenance:status` zeigt den Status des Wartungsmodus an.

So aktivieren Sie beispielsweise den Wartungsmodus ohne IP-Adressenausnahmen:

```bash
bin/magento maintenance:enable
```

So aktivieren Sie den Wartungsmodus für alle Clients außer 192.0.2.10 und 192.0.2.11:

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

Nachdem Sie die Anwendung in den Wartungsmodus versetzt haben, müssen Sie alle Verbraucherprozesse in der Nachrichtenwarteschlange stoppen.
Eine Möglichkeit, diese Prozesse zu finden, besteht darin, die `ps -ef | grep queue:consumers:start` und führen Sie dann die `kill <process_id>` -Befehl für jeden Verbraucher. Wiederholen Sie diese Aufgabe in einer Umgebung mit mehreren Knoten für jeden Knoten.

## Liste der ausgenommenen IP-Adressen beibehalten

Um die Liste der ausgenommenen IP-Adressen zu verwalten, können Sie entweder die `[--ip=<ip list>]` -Option in den vorherigen Befehlen oder Sie können Folgendes verwenden:

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

Die `<ip address> .. <ip address>` -Syntax ist eine optionale, durch Leerzeichen getrennte Liste von IP-Adressen, die ausgeschlossen werden sollen.

Die `--none` löscht die Liste.

## Multi-Store-Setups

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

Wenn Sie mehrere Stores mit jeweils unterschiedlichem Layout und lokalisierten Inhalten einrichten möchten, übergeben Sie die `$_GET['skin']` -Parameter auf den vorgesehenen Prozessor.

Im folgenden Beispiel verwenden wir eine `503` Typ der Fehlervorlagendatei, die lokalisierten Inhalt erfordert.

Der Konstruktor der `Error_Processor` -Klasse akzeptiert eine `skin` GET-Parameter zum Ändern des Layouts:

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

Dies kann auch zu einer Neuschreibungsregel im Abschnitt `.htaccess` Datei, die eine `skin` -Parameter an die URL an.

### $_GET[&quot;haut&quot;] parameter

So verwenden Sie die `skin` Parameter:

1. Überprüfen Sie, ob die `.maintenance.flag` vorhanden ist.
1. Notieren Sie die Hostadresse, die auf die `HTTP_HOST`oder einer anderen Variablen, wie z. B. ENV-Variablen.
1. Überprüfen Sie, ob die `skin` vorhanden ist.
1. Legen Sie den Parameter mithilfe der unten stehenden Neuschreibungsregeln fest.

   Im Folgenden finden Sie einige Beispiele für Neuschreibungsregeln:

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. Kopieren Sie die folgenden Dateien:

   * `pub/errors/default/503.phtml` nach `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` nach `pub/errors/sub/styles.css`

1. Bearbeiten Sie diese Dateien, um lokalisierten Inhalt im `503.phtml` Datei und benutzerdefinierter Stil im `styles.css` -Datei.

   Stellen Sie sicher, dass Ihre Pfade auf Ihre `errors` Verzeichnis. Der Verzeichnisname muss mit dem im `RewriteRule`. Im vorherigen Beispiel wurde die `sub` verwendet wird, was als Parameter im `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>Die [nginx](../../configuration/multi-sites/ms-nginx.md) muss für Multi-Store-Setups hinzugefügt werden.
