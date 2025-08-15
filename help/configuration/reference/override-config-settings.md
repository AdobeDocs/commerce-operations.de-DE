---
title: Konfigurationseinstellungen überschreiben
description: Erfahren Sie, wie Sie Umgebungsvariablen verwenden können, um Konfigurationseinstellungen zu überschreiben.
exl-id: 788fd3cd-f8c1-4514-8141-547fed36e9ce
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 0%

---

# Konfigurationseinstellungen überschreiben

In diesem Abschnitt wird beschrieben, wie Sie einen Umgebungsvariablennamen ableiten, wenn Sie einen Konfigurationspfad kennen. Sie können Adobe Commerce-Konfigurationseinstellungen mithilfe von Umgebungsvariablen überschreiben. Sie können beispielsweise den Wert der Live-URL eines Zahlungsprozessors auf Ihrem Produktionssystem überschreiben.

Sie können den Wert der _any_-Konfigurationseinstellung mithilfe von Umgebungsvariablen überschreiben. Adobe empfiehlt jedoch, konsistente Einstellungen mithilfe der freigegebenen Konfigurationsdatei `config.php` und der systemspezifischen Konfigurationsdatei `env.php` beizubehalten, wie unter [Allgemeine Übersicht über die Bereitstellung](../deployment/overview.md) beschrieben.

>[!TIP]
>
>Sehen Sie sich das Thema [Umgebungen konfigurieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html?lang=de) im Handbuch zu _Commerce in Cloud-Infrastrukturen an_.

## Umgebungsvariablen

Ein Umgebungsvariablenname besteht aus seinem Gültigkeitsbereich gefolgt von seinem Konfigurationspfad in einem bestimmten Format. In den folgenden Abschnitten wird beschrieben, wie Sie einen Variablennamen detaillierter bestimmen.

Sie können Variablen für eine der folgenden Aktionen verwenden:

- [Sensitive Werte](config-reference-sens.md) müssen entweder mithilfe von Umgebungsvariablen oder mit dem [`magento config:sensitive:set`](../cli/set-configuration-values.md)-Befehl festgelegt werden.
- Systemspezifische Werte müssen mithilfe von Folgendem festgelegt werden:

   - Umgebungsvariablen
   - Der [`magento config:set`](../cli/set-configuration-values.md) Befehl
   - Der Administrator gefolgt vom Befehl [`magento app:config:dump`](../cli/export-configuration.md)

Konfigurationspfade finden Sie unter:

- [Referenz zu sensiblen und systemspezifischen Konfigurationspfaden](config-reference-sens.md)
- [Referenz zu Zahlungskonfigurationspfaden](config-reference-payment.md)
- [Referenz zu Konfigurationspfaden für Commerce B2B-Erweiterungen](config-reference-b2b.md)
- [Referenz zu anderen Konfigurationspfaden](config-reference-general.md)

### Variablennamen

Das allgemeine Format der Variablennamen der Systemeinstellungen ist wie folgt:

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` kann Folgendes sein:

- Globaler Umfang (d. h. die globale Einstellung für _alle_ Bereiche)

  Globale Bereichsvariablen haben das folgende Format:

  `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- Ein bestimmter Umfang (d. h. die Einstellung wirkt sich nur auf eine bestimmte Store-Ansicht oder Website aus)

  Variablen für den Bereich der Store-Ansicht haben beispielsweise das folgende Format:

  `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

  Weitere Informationen zu Bereichen finden Sie unter:

   - [Schritt 1: Suchen des Wertes der Website- oder Store-Ansicht](#step-1-find-the-website-or-store-view-scope-value)
   - [Commerce-Benutzerhandbuch - Thema zum Umfang](https://experienceleague.adobe.com/de/docs/commerce-admin/start/setup/websites-stores-views#scope-settings)
   - [Kurzanleitung zum Umfang](https://experienceleague.adobe.com/de/docs/commerce-admin/config/scope-change#scope-quick-reference)

`<SYSTEM__VARIABLE__NAME>` ist der Konfigurationspfad, bei dem `/` durch doppelte Unterstriche ersetzt werden. Weitere Informationen finden Sie [Schritt 2: Festlegen von Systemvariablen](#step-2-set-global-website-or-store-view-variables).

### Variablenformat

`<SCOPE>` wird durch zwei Unterstriche von `<SYSTEM__VARIABLE__NAME>` getrennt.

`<SYSTEM__VARIABLE__NAME>` wird vom Konfigurationspfad einer Konfigurationseinstellung abgeleitet _einer Zeichenfolge_ bei der es sich um eine durch `/` getrennte Zeichenfolge handelt, die eine bestimmte Einstellung eindeutig identifiziert. Ersetzen Sie jedes `/` Zeichen im Konfigurationspfad durch zwei Unterstriche, um die Systemvariable zu erstellen.

Wenn ein Konfigurationspfad einen Unterstrich enthält, bleibt der Unterstrich in der Variablen.

Eine vollständige Liste der Konfigurationspfade finden Sie unter:

- [Referenz zu sensiblen und systemspezifischen Konfigurationspfaden](config-reference-sens.md)
- [Referenz zu Zahlungskonfigurationspfaden](config-reference-payment.md)
- [Konfigurationspfade für Commerce Enterprise B2B-Erweiterungen - Referenz](config-reference-b2b.md)
- [Referenz zu anderen Konfigurationspfaden](config-reference-general.md)

## Schritt 1: Suchen des Wertes der Website- oder Store-Ansicht

In diesem Abschnitt wird beschrieben, wie Sie Systemkonfigurationswerte nach _Bereich“ (_ oder Website) suchen und festlegen können. Informationen zum Festlegen globaler Bereichsvariablen finden Sie [Schritt 2: Festlegen globaler, Website- oder Store-Ansichtsvariablen](#step-2-set-global-website-or-store-view-variables).

Bereichswerte stammen aus den `store`-, `store_group`- und `store_website`.

- Die `store` Tabelle gibt Namen und Codes der Speicheransichten an
- Die `store_website` Tabelle gibt Website-Namen und -Codes an

Sie können die Code-Werte auch über die Admin-Adresse finden.

So lesen Sie die Tabelle:

- Spalte `Path in Admin`

  Werte vor dem Komma sind Pfade in der Admin-Navigation. Werte nach dem Komma sind Optionen im rechten Bereich.

- `Variable name` Spalte ist der Name der entsprechenden Umgebungsvariablen.

  Sie haben die Möglichkeit, bei Bedarf Systemwerte für diese Konfigurationsparameter als Umgebungsvariablen anzugeben.

   - Der gesamte Variablenname lautet immer „ALL CAPS“
   - Variablenname mit `CONFIG__` beginnen (beachten Sie zwei Unterstriche)
   - Sie finden den `<STORE_VIEW_CODE>` oder `<WEBSITE_CODE>` Teil eines Variablennamens entweder in der Admin- oder in der Commerce-Datenbank, wie in den folgenden Abschnitten angegeben.
   - Sie finden `<SYSTEM__VARIABLE__NAME>` wie in [2: Festlegen von globalen, Website- oder Store-Ansichtsvariablen“ ](#step-2-set-global-website-or-store-view-variables).

### Suchen nach einer Website oder einem Store-Ansichtsbereich im Admin-Bereich

In der folgenden Tabelle ist zusammengefasst, wie Sie im Admin-Bereich nach einem Wert für die Website- oder Store-Ansicht suchen.

| Beschreibung | Pfad in Admin | Variablenname |
|--------------|--------------|----------------------|
| Store-Ansichten erstellen, bearbeiten und löschen | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| Erstellen, Bearbeiten und Löschen von Websites | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

So suchen Sie beispielsweise einen Wert für den Ansichtsbereich einer Website oder eines Stores im Admin-Bereich:

1. Melden Sie sich bei Admin als Benutzer an, der zum Anzeigen von Websites autorisiert ist.
1. Klicken Sie auf **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. Klicken Sie auf den Namen einer Website oder Store-Ansicht.

   Der rechte Bereich wird ähnlich der folgenden angezeigt.

   ![Website-Code suchen](../../assets/configuration/website-code.png)

1. Der Bereichsname wird im Feld **[!UICONTROL Code]** angezeigt.
1. Fahren Sie fort mit [Schritt 2: Festlegen von globalen, Website- oder Store-Ansichtsvariablen](#step-2-set-global-website-or-store-view-variables).

### Suchen einer Website oder eines Store-Ansichtsumfangs in der Datenbank

So rufen Sie diese Werte aus der Datenbank ab:

1. Melden Sie sich bei Ihrem Entwicklungssystem als Eigentümer des Dateisystems an, falls noch nicht geschehen.
1. Geben Sie den folgenden Befehl ein:

   ```bash
   mysql -u <database-username> -p
   ```

1. Geben Sie an der `mysql>` Eingabeaufforderung die folgenden Befehle in der angegebenen Reihenfolge ein:

   ```shell
   use <database-name>;
   ```

1. Verwenden Sie die folgenden SQL-Abfragen, um die relevanten Werte zu finden:

   ```shell
   SELECT * FROM STORE;
   SELECT * FROM STORE_WEBSITE;
   ```

   Es folgt ein Beispiel:

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

1. Verwenden Sie den Wert aus der Spalte `code` als Bereichsnamen, nicht den `name`.

   Um beispielsweise eine Konfigurationsvariable für „Website-Test“ festzulegen, verwenden Sie das folgende Format:

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   Wo `<SYSTEM__VARIABLE__NAME>` aus dem nächsten Abschnitt kommt.

## Schritt 2: Festlegen von globalen, Website- oder Store-Ansichtsvariablen

In diesem Abschnitt wird beschrieben, wie Sie Systemvariablen festlegen.

- Um Werte für den globalen Umfang festzulegen (d. h. alle Websites, Stores und Store-Ansichten), beginnen Sie den Variablennamen mit `CONFIG__DEFAULT__`.

- Um einen Wert für eine bestimmte Store-Ansicht oder Website festzulegen, starten Sie den Variablennamen wie in [Schritt 1: Suchen des Bereichswerts](#step-1-find-the-website-or-store-view-scope-value):

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- Der letzte Teil des Variablennamens ist der Konfigurationspfad, der für jede Konfigurationseinstellung eindeutig ist.

[Hier einige Beispiele](#examples).

Die folgende Tabelle zeigt einige Beispielvariablen.

| Beschreibung | Pfad in Admin (ohne **Stores** > **Settings** > **Configuration**) | Variablenname |
|--------------|--------------|----------------------|
| Hostname des Elasticsearch-Servers | Katalog > **Katalog**, **Hostname des Elasticsearch-Servers** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Elasticsearch-Server-Port | Katalog > **Katalog**, **Elasticsearch-Server-Port** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| Versandlandursprung | Verkauf > **Versandeinstellungen** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| Benutzerdefinierte Admin-URL | Erweitert > **Admin** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| Benutzerdefinierter Administratorpfad | Erweitert > **Admin** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## Beispiele

In diesem Abschnitt wird gezeigt, wie Sie Werte einiger Beispielvariablen finden.

### Hostname des Elasticsearch-Servers

So suchen Sie den Variablennamen für die globale HTML-Minimierung:

1. Bestimmen Sie den Umfang.

   Es ist der globale Bereich, sodass der Variablenname mit `CONFIG__DEFAULT__` beginnt

1. Der Rest des Variablennamens ist `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **Ergebnis**: Der Variablenname ist `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### Versandlandursprung

So suchen Sie den Variablennamen für das Versandland:

1. Bestimmen Sie den Umfang.

   Suchen Sie den Bereich in [Datenbank](#find-a-website-or-store-view-scope-in-the-database) wie in Schritt 1: Suchen der Website- oder Store-Ansichtsbereichswert beschrieben. (Sie können den Wert auch im Admin finden, wie in der Tabelle [ Schritt 2: Festlegen der Variablen für globale, Website- oder Store-Ansicht gezeigt]&#x200B;(#step-2-set-global-website-or-store-view-variables.

   Der Umfang kann beispielsweise `CONFIG__WEBSITES__DEFAULT` sein.

1. Der Rest des Variablennamens ist `SHIPPING__ORIGIN__COUNTRY_ID`.

   **Ergebnis**: Der Variablenname ist `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## Verwenden von Umgebungsvariablen

Setzen Sie Konfigurationswerte als Variablen mithilfe des PHP&#39;s [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) Associate-Arrays. Sie können die Werte in jedem PHP-Skript festlegen, das ausgeführt wird, wenn Commerce ausgeführt wird.

>[!TIP]
>
>Das Festlegen von Variablenwerten in `index.php` oder `pub/index.php` funktioniert nicht immer erwartungsgemäß, da je nach Webserverkonfiguration unterschiedliche Einstiegspunkte für Anwendungen verwendet werden können. Durch Platzieren von `$_ENV` Anweisungen in der `app/bootstrap.php`-Datei werden die `$_ENV` Anweisungen unabhängig von den verschiedenen Anwendungs-Einstiegspunkten immer ausgeführt, da die `app/bootstrap.php`-Datei als Teil der Commerce-Architektur geladen wird.

Nachfolgend finden Sie ein Beispiel für die Einstellung von zwei `$_ENV`:

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

Ein Beispiel mit einer schrittweisen Anleitung finden Sie unter [Festlegen von Konfigurationswerten mithilfe von Umgebungsvariablen](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- Um Werte zu verwenden, die Sie im `$_ENV`-Array festgelegt haben, müssen Sie `variables_order = "EGPCS"` (Environment, Get, Post, Cookie, and Server) in Ihrer `php.ini`-Datei festlegen. Weitere Informationen finden Sie unter [PHP-Dokumentation](https://www.php.net/manual/en/ini.core.php).
>
>- Wenn Sie für Adobe Commerce in der Cloud-Infrastruktur versuchen, Konfigurationseinstellungen mithilfe der [Project Web Interface](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=de#configure-the-project) zu überschreiben, müssen Sie dem Variablennamen `env:` voranstellen. Beispiel:
>
>![Beispiel für eine Umgebungsvariable](../../assets/configuration/cloud-console-envvariable.png)
