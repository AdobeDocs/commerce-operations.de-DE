---
title: Konfigurationseinstellungen überschreiben
description: Erfahren Sie, wie Sie Umgebungsvariablen verwenden, um Konfigurationseinstellungen zu überschreiben.
exl-id: 788fd3cd-f8c1-4514-8141-547fed36e9ce
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 0%

---

# Konfigurationseinstellungen überschreiben

In diesem Thema wird beschrieben, wie Sie einen Umgebungsvariablennamen ableiten, der einen Konfigurationspfad kennt. Sie können Adobe Commerce-Konfigurationseinstellungen mithilfe von Umgebungsvariablen überschreiben. Sie können beispielsweise den Wert der Live-URL eines Zahlungsverarbeiters auf Ihrem Produktionssystem überschreiben.

Sie können den Wert der Konfigurationseinstellung _any_ mithilfe von Umgebungsvariablen überschreiben. Adobe empfiehlt jedoch, konsistente Einstellungen mithilfe der freigegebenen Konfigurationsdatei `config.php` und der systemspezifischen Konfigurationsdatei `env.php` beizubehalten, wie in der [allgemeinen Übersicht über die Bereitstellung](../deployment/overview.md) beschrieben.

>[!TIP]
>
>Sehen Sie sich das Thema [Umgebungen konfigurieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) im Leitfaden _Commerce on Cloud Infrastructure_ an.

## Umgebungsvariablen

Der Name einer Umgebungsvariablen besteht aus ihrem Umfang und seinem Konfigurationspfad in einem bestimmten Format. In den folgenden Abschnitten wird ausführlicher beschrieben, wie Sie einen Variablennamen bestimmen können.

Sie können Variablen für eine der folgenden Optionen verwenden:

- [Sensible Werte](config-reference-sens.md) müssen entweder mit Umgebungsvariablen oder mit dem Befehl [`magento config:sensitive:set`](../cli/set-configuration-values.md) festgelegt werden.
- Systemspezifische Werte müssen wie folgt festgelegt werden:

   - Umgebungsvariablen
   - Der Befehl [`magento config:set`](../cli/set-configuration-values.md)
   - Der Administrator gefolgt von dem Befehl [`magento app:config:dump`](../cli/export-configuration.md)

Konfigurationspfade finden Sie unter:

- [Referenz zu vertraulichen und systemspezifischen Konfigurationspfaden](config-reference-sens.md)
- [Referenz zu Zahlungskonfigurationspfaden](config-reference-payment.md)
- [Commerce B2B-Erweiterungs-Konfigurationspfade referenzieren](config-reference-b2b.md)
- [Andere Konfigurationspfade - Referenz](config-reference-general.md)

### Variablennamen

Das allgemeine Format der Variablennamen der Systemeinstellungen lautet wie folgt:

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` kann Folgendes sein:

- Globaler Umfang (d. h. die globale Einstellung für _alle_ Bereiche)

  Globale Perimeter haben das folgende Format:

  `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- Ein bestimmter Bereich (d. h. die Einstellung wirkt sich nur auf eine bestimmte Store-Ansicht oder Website aus)

  Speicheransichtsbereichsvariablen haben beispielsweise das folgende Format:

  `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

  Weitere Informationen zu Bereichen finden Sie unter:

   - [Schritt 1: Suchen Sie den Perimeter der Website- oder Store-Ansicht.](#step-1-find-the-website-or-store-view-scope-value)
   - [Commerce-Benutzerhandbuch zum Umfang](https://experienceleague.adobe.com/en/docs/commerce-admin/start/setup/websites-stores-views#scope-settings)
   - [Kurzübersicht zum Umfang](https://experienceleague.adobe.com/en/docs/commerce-admin/config/scope-change#scope-quick-reference)

`<SYSTEM__VARIABLE__NAME>` ist der Konfigurationspfad mit doppelten Unterstrichen, die durch `/` ersetzt werden. Weitere Informationen finden Sie unter [Schritt 2: Festlegen von Systemvariablen](#step-2-set-global-website-or-store-view-variables).

### Variable format

`<SCOPE>` wird von `<SYSTEM__VARIABLE__NAME>` durch zwei Unterstriche getrennt.

`<SYSTEM__VARIABLE__NAME>` wird vom _Konfigurationspfad_ einer Konfigurationseinstellung abgeleitet, der eine durch `/` getrennte Zeichenfolge ist, die eine bestimmte Einstellung eindeutig identifiziert. Ersetzen Sie jedes `/` -Zeichen im Konfigurationspfad durch zwei Unterstriche, um die Systemvariable zu erstellen.

Wenn ein Konfigurationspfad ein Unterstrichzeichen enthält, bleibt der Unterstrich in der Variablen erhalten.

Eine vollständige Liste der Konfigurationspfade finden Sie unter:

- [Referenz zu vertraulichen und systemspezifischen Konfigurationspfaden](config-reference-sens.md)
- [Referenz zu Zahlungskonfigurationspfaden](config-reference-payment.md)
- [Commerce Enterprise B2B-Erweiterungs-Konfigurationspfade - Referenz](config-reference-b2b.md)
- [Andere Konfigurationspfade - Referenz](config-reference-general.md)

## Schritt 1: Suchen Sie den Perimeter der Website- oder Store-Ansicht.

In diesem Abschnitt wird beschrieben, wie Sie Systemkonfigurationswerte für _scope_ (Store-Ansicht oder Website) finden und festlegen können. Informationen zum Festlegen globaler Scope-Variablen finden Sie unter [Schritt 2: Festlegen von globalen, Website- oder Store-Ansichtsvariablen](#step-2-set-global-website-or-store-view-variables).

Die Summenwerte stammen aus den Tabellen `store`, `store_group` und `store_website`.

- Die Tabelle `store` gibt Namen und Codes der Store-Ansichten an
- Die Tabelle `store_website` gibt die Namen und Codes der Websites an

Sie können die Codewerte auch mit dem Admin finden.

So lesen Sie die Tabelle:

- `Path in Admin` Spalte

  Werte vor dem Komma sind Pfade in der Admin-Navigation. Werte nach dem Komma sind Optionen im rechten Bereich.

- `Variable name` column ist der Name der entsprechenden Umgebungsvariablen.

  Sie können bei Bedarf Systemwerte für diese Konfigurationsparameter als Umgebungsvariablen angeben.

   - Der gesamte Variablenname ist immer ALL CAPS
   - Variablennamen mit `CONFIG__` beginnen (beachten Sie zwei Unterstriche)
   - Sie finden den Teil `<STORE_VIEW_CODE>` oder `<WEBSITE_CODE>` eines Variablennamens entweder in der Admin- oder Commerce-Datenbank, wie in den folgenden Abschnitten angegeben.
   - Sie finden `<SYSTEM__VARIABLE__NAME>` wie in [Schritt 2: Festlegen von globalen, Website- oder Store-Ansichtsvariablen](#step-2-set-global-website-or-store-view-variables) beschrieben.

### Suchen eines Website- oder Store-Ansichtsbereichs in der Admin-Konsole

In der folgenden Tabelle wird zusammengefasst, wie Sie den Anzeigewert der Website oder des Stores in der Admin-Konsole finden.

| Beschreibung | Pfad in Admin | Variablenname |
|--------------|--------------|----------------------|
| Erstellen, Bearbeiten und Löschen von Store-Ansichten | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| Websites erstellen, bearbeiten, löschen | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

So suchen Sie beispielsweise einen Website- oder Store-Ansichtsbereichswert in der Admin-Konsole:

1. Melden Sie sich bei Admin als Benutzer an, der zum Anzeigen von Websites berechtigt ist.
1. Klicken Sie auf **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. Klicken Sie auf den Namen einer Website- oder Store-Ansicht.

   Der rechte Bereich wird ähnlich dem folgenden angezeigt.

   ![Website-Code suchen](../../assets/configuration/website-code.png)

1. Der Bereichsname wird im Feld **[!UICONTROL Code]** angezeigt.
1. Fahren Sie mit [Schritt 2: Legen Sie globale, Website- oder Store-Ansichtsvariablen fest](#step-2-set-global-website-or-store-view-variables).

### Suchen eines Website- oder Store-Ansichtsbereichs in der Datenbank

So rufen Sie diese Werte aus der Datenbank ab:

1. Melden Sie sich bei Ihrem Entwicklungssystem als Eigentümer des Dateisystems an, falls Sie dies noch nicht getan haben.
1. Geben Sie den folgenden Befehl ein:

   ```bash
   mysql -u <database-username> -p
   ```

1. Geben Sie an der Eingabeaufforderung `mysql>` die folgenden Befehle in der angegebenen Reihenfolge ein:

   ```shell
   use <database-name>;
   ```

1. Verwenden Sie die folgenden SQL-Abfragen, um die relevanten Werte zu finden:

   ```shell
   SELECT * FROM STORE;
   SELECT * FROM STORE_WEBSITE;
   ```

   Ein Beispiel:

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

1. Verwenden Sie den Wert aus der Spalte `code` als Bereichsnamen, nicht den Wert `name` .

   Um beispielsweise eine Konfigurationsvariable für die Test-Website festzulegen, verwenden Sie folgendes Format:

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   wobei `<SYSTEM__VARIABLE__NAME>` aus dem nächsten Abschnitt kommt.

## Schritt 2: Festlegen der Variablen für globale, Website- oder Store-Ansichten

In diesem Abschnitt wird beschrieben, wie Sie Systemvariablen festlegen.

- Um Werte für den globalen Gültigkeitsbereich (d. h. alle Websites, Stores und Store-Ansichten) festzulegen, beginnen Sie den Variablennamen mit `CONFIG__DEFAULT__`.

- Um einen Wert für eine bestimmte Store-Ansicht oder Website festzulegen, starten Sie den Variablennamen wie in [Schritt 1: Suchen Sie den Perimeter-Wert](#step-1-find-the-website-or-store-view-scope-value) beschrieben:

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- Der letzte Teil des Variablennamens ist der Konfigurationspfad, der für jede Konfigurationseinstellung eindeutig ist.

[Siehe einige Beispiele](#examples).

Die folgende Tabelle zeigt einige Beispielvariablen.

| Beschreibung | Pfad in Admin (ohne **Speicher** > **Einstellungen** > **Konfiguration**) | Variablenname |
|--------------|--------------|----------------------|
| Hostname des Elasticsearch-Servers | Katalog > **Katalog**, **Hostname des Elasticsearch-Servers** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Elasticsearch-Serveranschluss | Katalog > **Katalog**, **Elasticsearch Server Port** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| Herkunft des Versandlandes | Vertrieb > **Versandeinstellungen** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| Benutzerdefinierte Admin-URL | Erweitert > **Admin** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| Benutzerdefinierter Administratorpfad | Erweitert > **Admin** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## Beispiele

Dieser Abschnitt zeigt, wie Sie Werte einiger Beispielvariablen finden.

### Hostname des Elasticsearch-Servers

So suchen Sie den Variablennamen für die globale HTML-Minimierung:

1. Legen Sie den Umfang fest.

   Es handelt sich um den globalen Umfang, sodass der Variablenname mit `CONFIG__DEFAULT__` beginnt

1. Der Rest des Variablennamens ist `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **Ergebnis**: Der Variablenname ist `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### Herkunft des Versandlandes

So suchen Sie den Variablennamen für den Versandlandherkunft:

1. Legen Sie den Umfang fest.

   Suchen Sie den Perimeter in der [Datenbank](#find-a-website-or-store-view-scope-in-the-database), wie in Schritt 1: Suchen Sie den Perimeter der Website- oder Store-Ansicht. (Sie können den Wert auch im Admin finden, wie in der Tabelle &quot;[in Schritt 2: Festlegen der globalen, Website- oder Store-Ansichtsvariablen]&quot;(#step-2-set-global-website-or-store-view-variables dargestellt.

   Der Umfang kann beispielsweise `CONFIG__WEBSITES__DEFAULT` sein.

1. Der Rest des Variablennamens ist `SHIPPING__ORIGIN__COUNTRY_ID`.

   **Ergebnis**: Der Variablenname ist `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## Verwenden von Umgebungsvariablen

Legen Sie Konfigurationswerte mithilfe des [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) -assoziierten Arrays von PHP als Variablen fest. Sie können die Werte in jedem PHP-Skript festlegen, das ausgeführt wird, wenn Commerce ausgeführt wird.

>[!TIP]
>
>Das Festlegen von Variablenwerten in `index.php` oder `pub/index.php` funktioniert nicht immer erwartungsgemäß, da je nach Webserverkonfiguration unterschiedliche Einstiegspunkte für die Anwendung verwendet werden können. Durch Platzierung von `$_ENV` -Direktiven in die Datei `app/bootstrap.php` werden unabhängig von den verschiedenen Einstiegspunkten der Anwendung die `$_ENV`-Direktiven immer ausgeführt, da die `app/bootstrap.php`-Datei im Rahmen der Commerce-Architektur geladen wird.

Ein Beispiel für die Festlegung von zwei `$_ENV` -Werten:

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

Ein schrittweises Beispiel wird unter [Festlegen von Konfigurationswerten mithilfe von Umgebungsvariablen](../deployment/example-environment-variables.md) gezeigt.

>[!WARNING]
>
>- Um die Werte zu verwenden, die Sie im Array `$_ENV` festgelegt haben, müssen Sie `variables_order = "EGPCS"` (Umgebung, Abruf, Beitrag, Cookie und Server) in Ihrer `php.ini`-Datei festlegen. Weitere Informationen finden Sie in der [PHP-Dokumentation](https://www.php.net/manual/en/ini.core.php).
>
>- Wenn Sie bei Adobe Commerce in der Cloud-Infrastruktur versuchen, Konfigurationseinstellungen mithilfe der [Projekt-Webschnittstelle](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project) zu überschreiben, müssen Sie dem Variablennamen &quot;`env:`&quot;voranstellen. Beispiel:
>
>![Beispiel für Umgebungsvariable](../../assets/configuration/cloud-console-envvariable.png)
