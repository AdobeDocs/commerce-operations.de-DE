---
title: Wartungsmodus aktivieren oder deaktivieren
description: Führen Sie diese Schritte aus, um anzupassen, was Kundinnen und Kunden sehen, wenn Ihre Adobe Commerce-Bereitstellung Wartungsarbeiten unterliegt.
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: a5dbefda6b77d993756143ef0e7270425f824c44
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Wartungsmodus aktivieren oder deaktivieren

Das folgende Handbuch bezieht sich auf eine standardmäßige Wartungsmodusseite. Wenn Sie eine benutzerdefinierte Wartungsseite verwenden müssen, lesen Sie den Abschnitt [Erstellen der benutzerdefinierten Wartungsseite](../../upgrade/troubleshooting/maintenance-mode-options.md) .

Adobe Commerce verwendet [Wartungsmodus](../../configuration/bootstrap/application-modes.md#maintenance-mode) um das Bootstrapping zu deaktivieren. Die Deaktivierung des Bootstrapping ist hilfreich, wenn Sie Ihre Site warten, aktualisieren oder neu konfigurieren.

Die Anwendung erkennt den Wartungsmodus wie folgt:

* Wenn `var/.maintenance.flag` vorhanden ist, ist der Wartungsmodus aktiviert und die Anwendung gibt eine 503-Wartungsseite zurück.
* Wenn `var/.maintenance.ip` vorhanden ist und die Client-IP einem der IP-Adresseinträge in dieser Datei entspricht, wird die Wartungsseite für die Anfrage ignoriert.

## Installieren des Programms

Bevor Sie diesen Befehl zum Aktivieren oder Deaktivieren des Wartungsmodus verwenden, müssen Sie [die Anwendung installieren](../advanced.md).

## Wartungsmodus aktivieren oder deaktivieren

Verwenden Sie den `magento maintenance` CLI-Befehl, um den Wartungsmodus zu aktivieren oder zu deaktivieren.

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

Die `--ip=<ip address>` Option ist eine IP-Adresse, die vom Wartungsmodus ausgenommen werden soll (z. B. Entwickler, die die Wartung durchführen). Wenn Sie mehr als eine IP-Adresse im selben Befehl ausschließen möchten, verwenden Sie die Option mehrmals.

>[!NOTE]
>
>Bei Verwendung von `--ip=<ip address>` mit `magento maintenance:disable` wird die Liste der IPs zur späteren Verwendung gespeichert. Um die Liste der ausgenommenen IPs zu löschen, verwenden Sie `magento maintenance:enable --ip=none` oder lesen Sie [Liste der ausgenommenen IP-Adressen verwalten](#maintain-the-list-of-exempt-ip-addresses).

Der Befehl `bin/magento maintenance:status` zeigt den Status des Wartungsmodus an.

So aktivieren Sie beispielsweise den Wartungsmodus ohne IP-Adressausnahmen:

```bash
bin/magento maintenance:enable
```

So aktivieren Sie den Wartungsmodus für alle Clients außer 192.0.2.10 und 192.0.2.11:

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

Nachdem Sie die Anwendung in den Wartungsmodus versetzt haben, müssen Sie alle Message Queue Consumer-Prozesse stoppen.
Eine Möglichkeit, diese Prozesse zu finden, besteht darin, den `ps -ef | grep queue:consumers:start`-Befehl und dann den `kill <process_id>`-Befehl für jeden Verbraucher auszuführen. Wiederholen Sie diese Aufgabe in einer Umgebung mit mehreren Knoten auf jedem Knoten.

## Liste der ausgenommenen IP-Adressen verwalten

Um die Liste der ausgenommenen IP-Adressen zu verwalten, können Sie entweder die Option `[--ip=<ip list>]` in den vorherigen Befehlen oder Folgendes verwenden:

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

Die `<ip address> .. <ip address>` Syntax ist eine optionale, durch Leerzeichen getrennte Liste von IP-Adressen, die von der Eingabe ausgenommen werden sollen.

Mit der Option `--none` wird die Liste gelöscht.

## Multi-Store-Setups

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

Wenn Sie mehrere Stores mit jeweils anderem Layout und lokalisierten Inhalten einrichten möchten, übergeben Sie den `$_GET['skin']` an den gewünschten Prozessor.

Im folgenden Beispiel verwenden wir eine Fehlervorlagendatei vom Typ &quot;`503`&quot;, für die lokalisierte Inhalte erforderlich sind.

Der Konstruktor der `Error_Processor` akzeptiert einen `skin` GET-Parameter, um das Layout zu ändern:

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

Dies kann auch zu einer Rewrite-Regel in der `.htaccess`-Datei hinzugefügt werden, die einen `skin` Parameter an die URL anhängt.

### $_GET[&#39;skin]Parameter

So verwenden Sie den `skin`:

1. Überprüfen Sie, ob die `.maintenance.flag` vorhanden ist.
1. Beachten Sie die Host-Adresse, die auf den `HTTP_HOST` verweist, oder jede andere Variable, z. B. ENV-Variablen.
1. Überprüfen Sie, ob der `skin` vorhanden ist.
1. Legen Sie den -Parameter mithilfe der folgenden Neuschreibungsregeln fest.

   Im Folgenden finden Sie einige Beispiele für Neuschreibungsregeln:

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. Kopieren Sie die folgenden Dateien:

   * `pub/errors/default/503.phtml` zu `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` zu `pub/errors/sub/styles.css`

1. Bearbeiten Sie diese Dateien, um lokalisierte Inhalte in der `503.phtml`-Datei und benutzerdefinierte Stile in der `styles.css`-Datei bereitzustellen.

   Stellen Sie sicher, dass Ihre Pfade auf Ihr `errors`-Verzeichnis verweisen. Der Verzeichnisname muss mit dem im `RewriteRule` angegebenen URL-Parameter übereinstimmen. Im vorherigen Beispiel wird das Verzeichnis `sub` verwendet, das als Parameter im `RewriteRule` (`skin=sub`) angegeben ist

>[!NOTE]
>
>Die [nginx](../../configuration/multi-sites/ms-nginx.md)-Einstellung muss für Multi-Store-Setups hinzugefügt werden.
