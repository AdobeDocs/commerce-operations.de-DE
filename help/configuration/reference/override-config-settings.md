---
title: Konfigurationseinstellungen überschreiben
description: Erfahren Sie, wie Sie Umgebungsvariablen verwenden, um Konfigurationseinstellungen zu überschreiben.
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '1228'
ht-degree: 0%

---


# Konfigurationseinstellungen überschreiben

In diesem Thema wird beschrieben, wie Sie einen Umgebungsvariablennamen ableiten, der einen Konfigurationspfad kennt. Sie können Adobe Commerce-Konfigurationseinstellungen mithilfe von Umgebungsvariablen überschreiben. Sie können beispielsweise den Wert der Live-URL eines Zahlungsverarbeiters auf Ihrem Produktionssystem überschreiben.

Sie können den Wert von _any_ Konfigurationseinstellung mithilfe von Umgebungsvariablen; Adobe empfiehlt jedoch, konsistente Einstellungen mithilfe der freigegebenen Konfigurationsdatei beizubehalten. `config.php`und der systemspezifischen Konfigurationsdatei, `env.php`, wie in [Allgemeine Übersicht über die Implementierung](../deployment/overview.md).

>[!TIP]
>
>Sehen Sie sich die [Umgebungen konfigurieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) Thema im _Leitfaden zu Commerce on Cloud Infrastructure_.

## Umgebungsvariablen

Der Name einer Umgebungsvariablen besteht aus ihrem Umfang und seinem Konfigurationspfad in einem bestimmten Format. In den folgenden Abschnitten wird ausführlicher beschrieben, wie Sie einen Variablennamen bestimmen können.

Sie können Variablen für eine der folgenden Optionen verwenden:

- [Sensible Werte](config-reference-sens.md) muss entweder mithilfe von Umgebungsvariablen oder der [`magento config:sensitive:set`](../cli/set-configuration-values.md) Befehl.
- Systemspezifische Werte müssen wie folgt festgelegt werden:

   - Umgebungsvariablen
   - Die [`magento config:set`](../cli/set-configuration-values.md) command
   - Der Administrator gefolgt von der [`magento app:config:dump` command](../cli/export-configuration.md)

Konfigurationspfade finden Sie unter:

- [Referenz zu vertraulichen und systemspezifischen Konfigurationspfaden](config-reference-sens.md)
- [Referenz zu Zahlungskonfigurationspfaden](config-reference-payment.md)
- [Referenz zu Commerce B2B-Erweiterungs-Konfigurationspfaden](config-reference-b2b.md)
- [Andere Konfigurationspfade](config-reference-general.md)

### Variablennamen

Das allgemeine Format der Variablennamen der Systemeinstellungen lautet wie folgt:

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` kann Folgendes sein:

- Globaler Umfang (d. h. die globale Einstellung für _all_ Bereiche)

   Globale Perimeter haben das folgende Format:

   `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- Ein bestimmter Bereich (d. h. die Einstellung wirkt sich nur auf eine bestimmte Store-Ansicht oder Website aus)

   Speicheransichtsbereichsvariablen haben beispielsweise das folgende Format:

   `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

   Weitere Informationen zu Bereichen finden Sie unter:

   - [Schritt 1: Suchen Sie den Bereichswert der Website- oder Store-Ansicht.](#step-1-find-the-website-or-store-view-scope-value)
   - [Thema zum Commerce-Benutzerhandbuch zum Umfang](https://docs.magento.com/user-guide/configuration/scope.html)
   - [Schnellverweis zum Umfang](https://docs.magento.com/user-guide/stores/store-scope-reference.html)

`<SYSTEM__VARIABLE__NAME>` ist der Konfigurationspfad mit doppelten Unterstrichzeichen, die ersetzt werden `/`. Weitere Informationen finden Sie unter [Schritt 2: Festlegen von Systemvariablen](#step-2-set-global-website-or-store-view-variables).

### Variablenformat

`<SCOPE>` getrennt von `<SYSTEM__VARIABLE__NAME>` um zwei Unterstriche.

`<SYSTEM__VARIABLE__NAME>` von einer Konfigurationseinstellung abgeleitet wurde, _Konfigurationspfad_, die `/` durch Trennzeichen getrennte Zeichenfolge, die eine bestimmte Einstellung eindeutig identifiziert. Ersetzen Sie jede `/` im Konfigurationspfad mit zwei Unterstrichzeichen, um die Systemvariable zu erstellen.

Wenn ein Konfigurationspfad ein Unterstrichzeichen enthält, bleibt der Unterstrich in der Variablen erhalten.

Eine vollständige Liste der Konfigurationspfade finden Sie unter:

- [Referenz zu vertraulichen und systemspezifischen Konfigurationspfaden](config-reference-sens.md)
- [Referenz zu Zahlungskonfigurationspfaden](config-reference-payment.md)
- [Referenz zu den Konfigurationspfaden für Commerce Enterprise B2B-Erweiterungen](config-reference-b2b.md)
- [Andere Konfigurationspfade](config-reference-general.md)

## Schritt 1: Suchen Sie den Bereichswert der Website- oder Store-Ansicht.

In diesem Abschnitt wird beschrieben, wie Sie Systemkonfigurationswerte pro _Umfang_ (Store-Ansicht oder Website). Informationen zum Festlegen globaler Scope-Variablen finden Sie unter [Schritt 2: Festlegen globaler, Website- oder Store-Ansichtsvariablen](#step-2-set-global-website-or-store-view-variables).

Die Bereichswerte stammen aus dem `store`, `store_group`und `store_website` -Tabellen.

- Die `store` -Tabelle gibt Namen und Codes für Speicheransichten an
- Die `store_website` Tabelle gibt Website-Namen und -Codes an

Sie können die Codewerte auch mit dem Admin finden.

So lesen Sie die Tabelle:

- `Path in Admin` column

   Werte vor dem Komma sind Pfade in der Admin-Navigation. Werte nach dem Komma sind Optionen im rechten Bereich.

- `Variable name` column ist der Name der entsprechenden Umgebungsvariablen.

   Sie können bei Bedarf Systemwerte für diese Konfigurationsparameter als Umgebungsvariablen angeben.

   - Der gesamte Variablenname ist immer ALL CAPS
   - Starten Sie einen Variablennamen mit `CONFIG__` (Hinweis: zwei Unterstriche)
   - Sie finden die `<STORE_VIEW_CODE>` oder `<WEBSITE_CODE>` Teil eines Variablennamens in der Admin- oder Commerce-Datenbank, wie in den folgenden Abschnitten angegeben.
   - Sie finden `<SYSTEM__VARIABLE__NAME>` wie in [Schritt 2: Festlegen globaler, Website- oder Store-Ansichtsvariablen](#step-2-set-global-website-or-store-view-variables).

### Suchen eines Website- oder Store-Ansichtsbereichs in der Admin-Konsole

In der folgenden Tabelle wird zusammengefasst, wie Sie den Anzeigewert der Website oder des Stores in der Admin-Konsole finden.

| Beschreibung | Pfad in Admin | Variablenname |
|--------------|--------------|----------------------|
| Erstellen, Bearbeiten und Löschen von Store-Ansichten | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| Websites erstellen, bearbeiten, löschen | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

So suchen Sie beispielsweise einen Website- oder Store-Ansichtsbereichswert in der Admin-Konsole:

1. Melden Sie sich bei Admin als Benutzer an, der zum Anzeigen von Websites berechtigt ist.
1. Klicken **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. Klicken Sie auf den Namen einer Website- oder Store-Ansicht.

   Der rechte Bereich wird ähnlich dem folgenden angezeigt.

   ![Website-Code suchen](../../assets/configuration/website-code.png)

1. Der Bereichsname wird im **[!UICONTROL Code]** -Feld.
1. Fahren Sie mit [Schritt 2: Festlegen globaler, Website- oder Store-Ansichtsvariablen](#step-2-set-global-website-or-store-view-variables).

### Suchen eines Website- oder Store-Ansichtsbereichs in der Datenbank

So rufen Sie diese Werte aus der Datenbank ab:

1. Melden Sie sich bei Ihrem Entwicklungssystem als [Dateisysteminhaber](https://glossary.magento.com/magento-file-system-owner) wenn Sie dies noch nicht getan haben.
1. Geben Sie den folgenden Befehl ein:

   ```bash
   mysql -u <database-username> -p
   ```

1. Im `mysql>` -Eingabeaufforderung die folgenden Befehle in der angegebenen Reihenfolge eingeben:

   ```shell
   use <database-name>;
   ```

1. Verwenden Sie die folgenden SQL-Abfragen, um die relevanten Werte zu finden:

   ```shell
   SELECT * FROM STORE;
   SELECT * FROM STORE_WEBSITE;
   ```

   Beispiel:

   ```shell
   mysql> SELECT * FROM STORE_WEBSITE;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

1. Verwenden Sie den Wert aus der `code` als Bereichsnamen, nicht als `name` -Wert.

   Um beispielsweise eine Konfigurationsvariable für die Test-Website festzulegen, verwenden Sie folgendes Format:

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   where `<SYSTEM__VARIABLE__NAME>` aus dem nächsten Abschnitt.

## Schritt 2: Festlegen globaler, Website- oder Store-Ansichtsvariablen

In diesem Abschnitt wird beschrieben, wie Sie Systemvariablen festlegen.

- Um Werte für den globalen Gültigkeitsbereich (d. h. alle Websites, Stores und Store-Ansichten) festzulegen, starten Sie den Variablennamen mit `CONFIG__DEFAULT__`.

- Um einen Wert für eine bestimmte Store-Ansicht oder Website festzulegen, starten Sie den Variablennamen wie unter [Schritt 1: Suchen des Perimeter-Werts](#step-1-find-the-website-or-store-view-scope-value):

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- Der letzte Teil des Variablennamens ist der Konfigurationspfad, der für jede Konfigurationseinstellung eindeutig ist.

[Beispiele](#examples).

Die folgende Tabelle zeigt einige Beispielvariablen.

| Beschreibung | Pfad in Admin (ausgelassen) **Stores** > **Einstellungen** > **Konfiguration**) | Variablenname |
|--------------|--------------|----------------------|
| Hostname des Elasticsearch-Servers | Katalog > **Katalog**, **Hostname des Elasticsearch-Servers** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Elasticsearch-Serveranschluss | Katalog > **Katalog**, **Elasticsearch-Server-Port** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| Herkunft des Versandlandes | Vertrieb > **Versandeinstellungen** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| Benutzerdefinierte Admin-URL | Erweitert > **Admin** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| Benutzerdefinierter Admin-Pfad | Erweitert > **Admin** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## Beispiele

Dieser Abschnitt zeigt, wie Sie Werte einiger Beispielvariablen finden.

### Hostname des Elasticsearch-Servers

So suchen Sie den Variablennamen für die globale HTML-Minimierung:

1. Legen Sie den Umfang fest.

   Dies ist der globale Umfang, sodass der Variablenname mit `CONFIG__DEFAULT__`

1. Der restliche Variablenname lautet `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **Ergebnis**: Der Variablenname lautet `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### Herkunft des Versandlandes

So suchen Sie den Variablennamen für den Versandlandherkunft:

1. Legen Sie den Umfang fest.

   Suchen Sie den Bereich im [Datenbank](#find-a-website-or-store-view-scope-in-the-database) wie in Schritt 1 beschrieben: Suchen Sie den Bereichswert der Website- oder Store-Ansicht. (Sie können den Wert auch in Admin finden, wie im Abschnitt [Tabelle in Schritt 2: Festlegen globaler, Website- oder Store-Ansichtsvariablen](#step-2-set-global-website-or-store-view-variables.

   Der Umfang kann beispielsweise `CONFIG__WEBSITES__DEFAULT`.

1. Der restliche Variablenname lautet `SHIPPING__ORIGIN__COUNTRY_ID`.

   **Ergebnis**: Der Variablenname lautet `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## Verwenden von Umgebungsvariablen

Festlegen von Konfigurationswerten als Variablen mithilfe der von PHP verwendeten [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) verknüpfen. Sie können die Werte in jedem PHP-Skript festlegen, das ausgeführt wird, wenn Commerce ausgeführt wird.

>[!TIP]
>
>Festlegen von Variablenwerten in `index.php` oder `pub/index.php` funktioniert nicht immer wie erwartet, da je nach Webserverkonfiguration unterschiedliche Einstiegspunkte für die Anwendung verwendet werden können. durch `$_ENV` Richtlinien in `app/bootstrap.php` -Datei, unabhängig von verschiedenen Einstiegspunkten der Anwendung, die `$_ENV` Direktiven werden immer ausgeführt, da `app/bootstrap.php` -Datei als Teil der Commerce-Architektur geladen werden.

Ein Beispiel für die Festlegung von zwei `$_ENV` -Werte:

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

Ein Beispiel mit einer schrittweisen Anleitung finden Sie unter [Festlegen von Konfigurationswerten mithilfe von Umgebungsvariablen](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- So verwenden Sie Werte, die Sie in der Variablen `$_ENV` Array, müssen Sie `variables_order = "EGPCS"`(Umgebung, Get, Post, Cookie und Server) in Ihrer `php.ini` -Datei. Weitere Informationen finden Sie unter [PHP-Dokumentation](https://www.php.net/manual/en/ini.core.php).
>
>- Wenn Sie bei Adobe Commerce in der Cloud-Infrastruktur versuchen, Konfigurationseinstellungen mit der [Projekt-Webschnittstelle](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project), müssen Sie dem Variablennamen `env:`. Beispiel:
>
>![Beispiel für Umgebungsvariable](../../assets/configuration/cloud-console-envvariable.png)
