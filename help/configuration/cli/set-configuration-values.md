---
title: Festlegen von Konfigurationswerten
description: Erfahren Sie, wie Sie Konfigurationswerte festlegen und Werte ändern, die in Admin gesperrt sind.
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '1038'
ht-degree: 0%

---

# Festlegen von Konfigurationswerten

{{file-system-owner}}

In diesem Thema werden erweiterte Konfigurationsbefehle erläutert, die Sie für folgende Aufgaben verwenden können:

- Konfigurationsoption über die Befehlszeile festlegen
- Optional können Sie jede Konfigurationsoption sperren, sodass deren Wert im Admin nicht geändert werden kann
- Konfigurationsoption ändern, die in der Admin-Konsole gesperrt ist

Sie können diese Befehle verwenden, um die Commerce-Konfiguration manuell oder mithilfe von Skripten festzulegen. Sie legen Konfigurationsoptionen mit einem _Konfigurationspfad_ fest, bei dem es sich um eine durch `/` getrennte Zeichenfolge handelt, die diese Konfigurationsoption eindeutig identifiziert. Sie finden Konfigurationspfade in den folgenden Referenzen:

- [Referenz zu vertraulichen und systemspezifischen Konfigurationspfaden](../reference/config-reference-sens.md)
- [Referenz zu Zahlungskonfigurationspfaden](../reference/config-reference-payment.md)
- [Referenz zu allgemeinen Konfigurationspfaden](../reference/config-reference-general.md)
- [Commerce Enterprise B2B-Erweiterungs-Konfigurationspfade - Referenz](../reference/config-reference-b2b.md)

Sie können Werte zu folgenden Zeiten festlegen:

- Vor der Installation von Commerce können Sie Konfigurationswerte nur für den Standardbereich festlegen, da dies der einzige gültige Bereich ist.

- Nach der Installation von Commerce können Sie Konfigurationswerte für beliebige Website- oder Speicheransichtsbereiche festlegen.

Verwenden Sie die folgenden Befehle:

- `bin/magento config:set` legt einen nicht vertraulichen Konfigurationswert anhand seines Konfigurationspfads fest
- `bin/magento config:sensitive:set` legt einen beliebigen sensiblen Konfigurationswert anhand seines Konfigurationspfads fest
- `bin/magento config:show` zeigt gespeicherte Konfigurationswerte an; Werte verschlüsselter Einstellungen werden als Sternchen angezeigt

## Voraussetzungen

Um einen Konfigurationswert festzulegen, müssen Sie mindestens einen der folgenden Kenntnisse haben:

- Der Konfigurationspfad
- Um einen Konfigurationswert für einen bestimmten Bereich festzulegen, müssen Sie den Scope-Code kennen.

  Um einen Konfigurationswert für den Standardbereich festzulegen, müssen Sie nichts unternehmen.

### Suchen Sie den Konfigurationspfad

Siehe die folgenden Referenzen:

- [Referenz zu vertraulichen und systemspezifischen Konfigurationspfaden](../reference/config-reference-sens.md)
- [Referenz zu Zahlungskonfigurationspfaden](../reference/config-reference-payment.md)
- [Andere Konfigurationspfade - Referenz](../reference/config-reference-general.md)
- [Commerce Enterprise B2B-Erweiterungs-Konfigurationspfade - Referenz](../reference/config-reference-b2b.md)

### Suchen des Perimeter-Codes

Sie finden den Perimeter-Code entweder in der Commerce-Datenbank oder im Commerce Admin.

**So suchen Sie den Scope-Code im Admin**:

1. Melden Sie sich bei Admin als Benutzer an, der Websites anzeigen und Ansichten speichern kann.
1. Klicken Sie auf **[!UICONTROL Stores]** > Einstellungen > **[!UICONTROL All Stores]**.
1. Klicken Sie im rechten Bereich auf den Namen der Website- oder Store-Ansicht, um deren Code anzuzeigen.

   Die folgende Abbildung zeigt einen Beispiel-Website-Code.

   ![Abrufen eines Website- oder Store-Ansichtscodes vom Admin](../../assets/configuration/website-code.png)

1. Fahren Sie mit [Festlegen von Werten](#set-values) fort.

**So suchen Sie den Perimeter-Code in der Datenbank**:

Der Perimeter-Code für Websites und Store-Ansichten wird in der Commerce-Datenbank in den Tabellen `store_website` und `store` gespeichert.

1. Verbindung zur Commerce-Datenbank herstellen.

   ```bash
   mysql -u <Commerce database username> -p
   ```

1. Geben Sie die folgenden Befehle ein:

   ```shell
   use <Commerce database name>;
   ```

   ```shell
   SELECT * FROM store;
   ```

   ```shell
   SELECT * FROM store_website;
   ```

   Ein Beispielergebnis:

   ```
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   Verwenden Sie den Wert in der Spalte `code` .

1. Fahren Sie mit dem nächsten Abschnitt fort.

## Werte festlegen

**So legen Sie systemspezifische Konfigurationswerte fest**:

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**So legen Sie sensible Konfigurationswerte fest**:

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path value
```

In der folgenden Tabelle werden die Parameter des Befehls `set` beschrieben:

| Parameter | Beschreibung |
| --- | --- |
| `--scope` | Der Umfang der Konfiguration. Die möglichen Werte sind `default`, `website` oder `store`. Der Standardwert ist `default`. |
| `--scope-code` | Der Code der Konfiguration (Website-Code oder Code der Store-Ansicht) |
| `-e or --lock-env` | Entweder wird der Wert gesperrt, damit er nicht im Admin bearbeitet werden kann, oder eine Einstellung, die bereits in Admin gesperrt ist, wird geändert. Der Befehl schreibt den Wert in die Datei &quot;`<Commerce base dir>/app/etc/env.php`&quot;. |
| `-c or --lock-config` | Entweder wird der Wert gesperrt, damit er nicht im Admin bearbeitet werden kann, oder eine Einstellung, die bereits in Admin gesperrt ist, wird geändert. Der Befehl schreibt den Wert in die Datei &quot;`<Commerce base dir>/app/etc/config.php`&quot;. Die Option `--lock-config` überschreibt `--lock-env`, wenn Sie beide Optionen angeben. |
| `path` | _Erforderlich_. Der Konfigurationspfad |
| `value` | _Erforderlich_. Der -Wert der Konfiguration |

>[!INFO]
>
>Ab Commerce 2.2.4 ersetzen die Optionen `--lock-env` und `--lock-config` die Option `--lock`.
>
>Wenn Sie die Option `--lock-env` oder `--lock-config` verwenden, um einen Wert festzulegen oder zu ändern, müssen Sie den Befehl [`bin/magento app:config:import`](../cli/import-configuration.md) verwenden, um die Einstellung zu importieren, bevor Sie auf die Admin- oder Storefront zugreifen.

Wenn Sie einen falschen Konfigurationspfad eingeben, gibt dieser Befehl einen Fehler zurück

```text
The "wrong/config/path" does not exist
```

Weitere Informationen finden Sie in einem der folgenden Abschnitte:

- [Festlegen von Konfigurationswerten, die im Admin bearbeitet werden können](#set-configuration-values-that-can-be-edited-in-the-admin)
- [Festlegen von Konfigurationswerten, die nicht im Admin bearbeitet werden können](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### Festlegen von Konfigurationswerten, die im Admin bearbeitet werden können

Verwenden Sie `bin/magento config:set` _ohne_ `--lock-env` oder `--lock-config`, um den Wert in die Datenbank zu schreiben. Auf diese Weise festgelegte Werte können in der Admin-Konsole bearbeitet werden.

Einige Beispiele zum Festlegen einer Store-Basis-URL:

Legen Sie die Basis-URL für den Standardbereich fest:

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

Legen Sie die Basis-URL für die `base` -Website fest:

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

Legen Sie die Basis-URL für die `test` Store-Ansicht fest:

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### Festlegen von Konfigurationswerten, die nicht im Admin bearbeitet werden können

Wenn Sie die Option `--lock-env` wie folgt verwenden, speichert der Befehl den Konfigurationswert in `<Commerce base dir>/app/etc/env.php` und deaktiviert das Feld zur Bearbeitung dieses Werts im Admin.

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

Sie können die Option `--lock-env` verwenden, um Konfigurationswerte festzulegen, wenn Commerce nicht installiert ist. Sie können jedoch Werte nur für den Standardbereich festlegen.

>[!INFO]
>
>Die Datei &quot;`env.php`&quot; ist systemspezifisch. Sie sollten es nicht auf ein anderes System übertragen. Sie können damit Konfigurationswerte aus der Datenbank überschreiben. Sie können beispielsweise einen Datenbank-Dump von einem anderen System erstellen und die Werte `base_url` und andere überschreiben, sodass Sie die Datenbank nicht ändern müssen.

Wenn Sie die Option `--lock-config` wie folgt verwenden, wird der Konfigurationswert in `<Commerce base dir>/app/etc/config.php` gespeichert. Das Feld zum Bearbeiten dieses Werts im Admin ist deaktiviert.

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

Sie können `--lock-config` verwenden, um Konfigurationswerte festzulegen, wenn Commerce nicht installiert ist. Sie können jedoch Werte nur für den Standardbereich festlegen.

>[!INFO]
>
>Sie können `config.php` an ein anderes System übertragen, um dort dieselben Konfigurationswerte zu verwenden. Wenn Sie beispielsweise über ein Testsystem verfügen, bedeutet die Verwendung des gleichen `config.php`, dass Sie nicht dieselben Konfigurationswerte erneut festlegen müssen.

## Wert der Konfigurationseinstellungen anzeigen

Befehlsoptionen:

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

where

- `--scope` ist der Umfang der Konfiguration (Standard, Website, Store). Der Standardwert ist `default`
- `--scope-code` ist der Code für die Konfiguration (Website-Code oder Code für die Store-Ansicht)
- `path` ist der Konfigurationspfad im Format first_part/second_part/third_part/etc (_required_)

>[!INFO]
>
>Der Befehl `bin/magento config:show` zeigt die Werte aller [verschlüsselten Werte](../reference/config-reference-sens.md) als eine Reihe von Sternchen an: `******`.

### Beispiele

**So zeigen Sie alle gespeicherten Konfigurationen an**:

```bash
bin/magento config:show
```

Ergebnis:

```
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**So zeigen Sie alle gespeicherten Konfigurationen für die `base` Website** an:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

Ergebnis:

```
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**So zeigen Sie die Basis-URL für den Standardbereich an**:

```bash
bin/magento config:show web/unsecure/base_url
```

Ergebnis:

```
web/unsecure/base_url - http://example.com/
```

**So zeigen Sie die Basis-URL für die `base` Website** an:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

Ergebnis:

```
web/unsecure/base_url - http://example-for-website.com/
```

**So zeigen Sie die Basis-URL für den `default` store** an:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

Ergebnis:

```
web/unsecure/base_url - http://example-for-store.com/
```

>[!INFO]
>
>Der Gültigkeitscode kann nur Buchstaben (a-z oder A-Z), Zahlen (0-9) und Unterstriche (_) enthalten. Außerdem muss das erste Zeichen ein Brief sein. Wenn bei der Erstellung einer Website- oder Store-Ansicht Groß-/Kleinschreibung oder Kamelzeichen verwendet werden, wird bei der Übereinstimmung intern nicht zwischen Groß- und Kleinschreibung unterschieden, damit Konfigurationseinstellungen über Umgebungsvariablen außer Kraft gesetzt werden können. Siehe [Umgebungsvariablen verwenden, um Konfigurationseinstellungen zu überschreiben](../reference/override-config-settings.md#environment-variables).

