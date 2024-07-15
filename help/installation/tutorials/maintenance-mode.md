---
title: Aktivieren oder Deaktivieren des Wartungsmodus
description: Führen Sie diese Schritte aus, um anzupassen, was Kunden sehen, wenn Ihre Adobe Commerce-Bereitstellung zur Wartung heruntergefahren ist.
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# Aktivieren oder Deaktivieren des Wartungsmodus

Das folgende Handbuch bezieht sich auf eine Seite mit dem Standard-Wartungsmodus. Wenn Sie eine benutzerdefinierte Wartungsseite verwenden müssen, lesen Sie das Thema [Erstellen der benutzerdefinierten Wartungsseite](../../upgrade/troubleshooting/maintenance-mode-options.md) .

Adobe Commerce verwendet den [Wartungsmodus](../../configuration/bootstrap/application-modes.md#maintenance-mode), um das Bootstrapping zu deaktivieren. Die Deaktivierung des Bootstrapping ist hilfreich, wenn Sie Ihre Site verwalten, aktualisieren oder neu konfigurieren.

Das Programm erkennt den Wartungsmodus wie folgt:

* Wenn `var/.maintenance.flag` nicht vorhanden ist, ist der Wartungsmodus deaktiviert und die Anwendung funktioniert normal.
* Andernfalls ist der Wartungsmodus aktiviert, es sei denn, `var/.maintenance.ip` ist vorhanden.

  `var/.maintenance.ip` kann eine Liste von IP-Adressen enthalten. Wenn über HTTP auf einen Einstiegspunkt zugegriffen wird und die Client-IP-Adresse einem der Einträge in dieser Liste entspricht, ist der Wartungsmodus deaktiviert.

## Installieren des Programms

Bevor Sie diesen Befehl zum Aktivieren oder Deaktivieren des Wartungsmodus verwenden, müssen Sie [die Anwendung installieren](../advanced.md).

## Aktivieren oder Deaktivieren des Wartungsmodus

Verwenden Sie den CLI-Befehl `magento maintenance` , um den Wartungsmodus zu aktivieren oder zu deaktivieren.

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

Die Option `--ip=<ip address>` ist eine IP-Adresse, die vom Wartungsmodus ausgenommen werden soll (z. B. Entwickler, die die Wartung durchführen). Verwenden Sie die Option mehrmals, um mehrere IP-Adressen im selben Befehl auszuschließen.

>[!NOTE]
>
>Durch Verwendung von `--ip=<ip address>` und `magento maintenance:disable` wird die Liste der IPs für die spätere Verwendung gespeichert. Um die Liste der ausgenommenen IP-Adressen zu löschen, verwenden Sie `magento maintenance:enable --ip=none` oder lesen Sie den Abschnitt [Liste der ausgenommenen IP-Adressen beibehalten](#maintain-the-list-of-exempt-ip-addresses).

Der Befehl `bin/magento maintenance:status` zeigt den Status des Wartungsmodus an.

So aktivieren Sie beispielsweise den Wartungsmodus ohne IP-Adressenausnahmen:

```bash
bin/magento maintenance:enable
```

So aktivieren Sie den Wartungsmodus für alle Clients außer 192.0.2.10 und 192.0.2.11:

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

Nachdem Sie die Anwendung in den Wartungsmodus versetzt haben, müssen Sie alle Verbraucherprozesse in der Nachrichtenwarteschlange stoppen.
Eine Möglichkeit, diese Prozesse zu finden, besteht darin, den Befehl `ps -ef | grep queue:consumers:start` auszuführen und dann den Befehl `kill <process_id>` für jeden Verbraucher auszuführen. Wiederholen Sie diese Aufgabe in einer Umgebung mit mehreren Knoten für jeden Knoten.

## Liste der ausgenommenen IP-Adressen beibehalten

Um die Liste der ausgenommenen IP-Adressen zu verwalten, können Sie entweder die Option `[--ip=<ip list>]` in den vorherigen Befehlen verwenden oder Folgendes verwenden:

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

Die Syntax `<ip address> .. <ip address>` ist eine optionale Liste mit durch Leerzeichen getrennten IP-Adressen, die ausgeschlossen werden sollen.

Die Option `--none` löscht die Liste.

## Multi-Store-Setups

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

Wenn Sie mehrere Stores mit jeweils unterschiedlichem Layout und lokalisierten Inhalten einrichten möchten, übergeben Sie den Parameter `$_GET['skin']` an den vorgesehenen Prozessor.

Im folgenden Beispiel wird eine Fehlervorlagendatei vom Typ `503` verwendet, die lokalisierten Inhalt erfordert.

Der Konstruktor der `Error_Processor` -Klasse akzeptiert einen `skin` -GET-Parameter, um das Layout zu ändern:

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

Dies kann auch zu einer Neuschreibungsregel in der Datei `.htaccess` hinzugefügt werden, die einen Parameter `skin` an die URL anhängt.

### Parameter $_GET[&#39;skin&#39;]

So verwenden Sie den Parameter `skin` :

1. Überprüfen Sie, ob die `.maintenance.flag` vorhanden ist.
1. Notieren Sie die Hostadresse, die auf `HTTP_HOST` verweist, oder jede andere Variable, z. B. ENV-Variablen.
1. Überprüfen Sie, ob der Parameter `skin` vorhanden ist.
1. Legen Sie den Parameter mithilfe der unten stehenden Neuschreibungsregeln fest.

   Im Folgenden finden Sie einige Beispiele für Neuschreibungsregeln:

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. Kopieren Sie die folgenden Dateien:

   * `pub/errors/default/503.phtml` bis `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` bis `pub/errors/sub/styles.css`

1. Bearbeiten Sie diese Dateien, um lokalisierten Inhalt in der Datei `503.phtml` und benutzerdefinierten Stil in der Datei `styles.css` bereitzustellen.

   Stellen Sie sicher, dass Ihre Pfade auf das Verzeichnis `errors` verweisen. Der Ordnername muss mit dem URL-Parameter übereinstimmen, der in `RewriteRule` angegeben ist. Im vorherigen Beispiel wird das Verzeichnis `sub` verwendet, das als Parameter in der Variablen `RewriteRule` (`skin=sub`) angegeben ist.

>[!NOTE]
>
>Die Einstellung [nginx](../../configuration/multi-sites/ms-nginx.md) muss für Multi-Store-Setups hinzugefügt werden.
