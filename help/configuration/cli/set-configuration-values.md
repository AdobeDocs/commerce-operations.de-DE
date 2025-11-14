---
title: Festlegen von Konfigurationswerten
description: Erfahren Sie, wie Sie in Adobe Commerce Konfigurationswerte festlegen und gesperrte Admin-Werte ändern. Erfahren Sie mehr über erweiterte Konfigurationsbefehle und -techniken.
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: 5e2d11330d3334df36ba8b3d176fbe2d8bfe0486
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 0%

---

# Festlegen von Konfigurationswerten

{{file-system-owner}}

In diesem Thema werden erweiterte Konfigurationsbefehle erläutert, die Sie für Folgendes verwenden können:

- Legen Sie eine beliebige Konfigurationsoption über die Befehlszeile fest
- Optional können Sie jede Konfigurationsoption sperren, damit ihr Wert in der Admin-Instanz nicht geändert werden kann.
- Ändern einer Konfigurationsoption, die in der Admin gesperrt ist

Sie können diese Befehle verwenden, um die Commerce-Konfiguration manuell oder mithilfe von Skripten festzulegen. Sie können Konfigurationsoptionen mithilfe eines _Konfigurationspfads) festlegen_ bei dem es sich um eine `/` Zeichenfolge handelt, die diese Konfigurationsoption eindeutig identifiziert. Konfigurationspfade finden Sie in den folgenden Verweisen:

- [Referenz zu sensiblen und systemspezifischen Konfigurationspfaden](../reference/config-reference-sens.md)
- [Referenz zu Zahlungskonfigurationspfaden](../reference/config-reference-payment.md)
- [Referenz zu allgemeinen Konfigurationspfaden](../reference/config-reference-general.md)
- [Konfigurationspfade für Commerce Enterprise B2B-Erweiterungen - Referenz](../reference/config-reference-b2b.md)

Sie können Werte zu folgenden Zeiten festlegen:

- Vor der Installation von Commerce können Sie Konfigurationswerte nur für den Standardbereich festlegen, da dies der einzige gültige Bereich ist.

- Nach der Installation von Commerce können Sie Konfigurationswerte für beliebige Website- oder Store-Ansichtsbereiche festlegen.

Verwenden Sie die folgenden Befehle:

- `bin/magento config:set` legt jeden nicht sensiblen Konfigurationswert anhand seines Konfigurationspfads fest
- `bin/magento config:sensitive:set` legt jeden sensiblen Konfigurationswert anhand seines Konfigurationspfads fest
- `bin/magento config:show` zeigt gespeicherte Konfigurationswerte an. Werte verschlüsselter Einstellungen werden als Sternchen angezeigt

## Voraussetzungen

Um einen Konfigurationswert festzulegen, müssen Sie mindestens eine der folgenden Eigenschaften kennen:

- Der Konfigurationspfad
- Um einen Konfigurationswert für einen bestimmten Bereich festzulegen, müssen Sie den Bereichscode kennen.

  Um einen Konfigurationswert für den Standardbereich festzulegen, müssen Sie nichts tun.

### Suchen des Konfigurationspfads

Siehe die folgenden Verweise:

- [Referenz zu sensiblen und systemspezifischen Konfigurationspfaden](../reference/config-reference-sens.md)
- [Referenz zu Zahlungskonfigurationspfaden](../reference/config-reference-payment.md)
- [Referenz zu anderen Konfigurationspfaden](../reference/config-reference-general.md)
- [Konfigurationspfade für Commerce Enterprise B2B-Erweiterungen - Referenz](../reference/config-reference-b2b.md)

### Finden des Umfangscodes

Den Gültigkeitscode finden Sie entweder in der Commerce-Datenbank oder in Commerce Admin.

**So finden Sie den Bereichscode in der Admin**:

1. Melden Sie sich bei Admin als Benutzer an, der Websites anzeigen und Ansichten speichern kann.
1. Klicken Sie auf **[!UICONTROL Stores]** > Einstellungen > **[!UICONTROL All Stores]**.
1. Klicken Sie im rechten Bereich auf den Namen der Website oder Store-Ansicht, um den Code anzuzeigen.

   Die folgende Abbildung zeigt einen Beispiel-Website-Code.

   ![Rufen Sie eine Website- oder Store-Ansicht-Code vom Administrator ab](../../assets/configuration/website-code.png)

1. Fahren Sie mit [Werte festlegen](#set-values) fort.

**So suchen Sie den Bereichscode in der Datenbank**:

Bereichscodes für Websites und Store-Ansichten werden in der Commerce-Datenbank in den `store_website`- bzw. `store`-Tabellen gespeichert.

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

   Es folgt ein Beispielergebnis:

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

**So legen Sie systemspezifische Konfigurationswerte**:

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**So legen Sie vertrauliche Konfigurationswerte**:

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path
```

In der folgenden Tabelle werden die `set`-Befehlsparameter beschrieben:

| Parameter | Beschreibung |
| --- |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `--scope` | Der Umfang der Konfiguration. Die möglichen Werte sind `default`, `website` oder `store`. Der Standardwert lautet `default`. |
| `--scope-code` | Der Umfang der Code-Konfiguration (Website-Code oder Code für die Store-Ansicht) |
| `-e or --lock-env` | Entweder wird der Wert gesperrt, sodass er nicht in der Admin bearbeitet werden kann, oder es wird eine Einstellung geändert, die bereits in der Admin gesperrt ist. Der Befehl schreibt den Wert in die `<Commerce base dir>/app/etc/env.php`. |
| `-c or --lock-config` | Entweder wird der Wert gesperrt, sodass er nicht in der Admin bearbeitet werden kann, oder es wird eine Einstellung geändert, die bereits in der Admin gesperrt ist. Der Befehl schreibt den Wert in die `<Commerce base dir>/app/etc/config.php`. Die Option `--lock-config` überschreibt `--lock-env`, wenn Sie beide Optionen angeben. |
| `path` | _Erforderlich_. Der Konfigurationspfad |
| `value` | _Erforderlich_. Der Wert der Konfiguration. Obwohl es als separates Argument in einem CLI-Befehl übergeben werden kann, empfiehlt Adobe, es nicht im ursprünglichen Befehl anzugeben. Führen Sie stattdessen den Befehl ohne den Wert aus und geben Sie dann den Wert ein, wenn Sie dazu aufgefordert werden. Mit dieser Methode wird verhindert, dass sensible Zugriffswerte in bash_history geschrieben werden, was der sicherste Weg ist, die Konfiguration festzulegen. |

>[!INFO]
>
>Ab Commerce 2.2.4 ersetzen die Optionen `--lock-env` und `--lock-config` die Option `--lock` . Wenn Sie eine dieser Optionen verwenden, wird der Wert direkt in die `app/etc/env.php`- oder `app/etc/config.php`-Datei geschrieben und wird in der Admin-Gruppe schreibgeschützt. Um Konfigurationsänderungen aus diesen Dateien in die Datenbank zu importieren, führen Sie den `bin/magento app:config:import`-Befehl aus, beispielsweise nach der manuellen Bearbeitung oder Neubereitstellung der Dateien.

Wenn Sie einen falschen Konfigurationspfad eingeben, gibt dieser Befehl einen Fehler zurück

```text
The "wrong/config/path" does not exist
```

Weitere Informationen finden Sie in einem der folgenden Abschnitte:

- [Legen Sie Konfigurationswerte fest, die in der Admin bearbeitet werden können](#set-configuration-values-that-can-be-edited-in-the-admin)
- [Legen Sie Konfigurationswerte fest, die in Admin nicht bearbeitet werden können](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### Legen Sie Konfigurationswerte fest, die in der Admin bearbeitet werden können

Verwenden Sie `bin/magento config:set` _ohne_ `--lock-env` oder `--lock-config`, um den Wert in die Datenbank zu schreiben. Auf diese Weise festgelegte Werte können im Admin bearbeitet werden.

Im Folgenden finden Sie einige Beispiele für das Festlegen einer Store-Basis-URL:

Legen Sie die Basis-URL für den Standardbereich fest:

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

Legen Sie die Basis-URL für die `base`-Website fest:

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

Festlegen der Basis-URL für die `test` Store-Ansicht:

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### Legen Sie Konfigurationswerte fest, die in Admin nicht bearbeitet werden können

Wenn Sie die Option `--lock-env` wie folgt verwenden, speichert der Befehl den Konfigurationswert in `<Commerce base dir>/app/etc/env.php` und deaktiviert das Feld für die Bearbeitung dieses Werts in Admin.

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

Sie können die Option `--lock-env` verwenden, um Konfigurationswerte festzulegen, wenn Commerce nicht installiert ist. Sie können jedoch Werte nur für den Standardbereich festlegen.

>[!INFO]
>
>Die `env.php` ist systemspezifisch. Nicht auf ein anderes System übertragen. Sie können damit Konfigurationswerte aus der Datenbank überschreiben. Sie können beispielsweise einen Datenbank-Dump von einem anderen System verwenden und die `base_url` und andere Werte überschreiben, sodass Sie die Datenbank nicht ändern müssen.

Wenn Sie die Option `--lock-config` wie folgt verwenden, wird der Konfigurationswert in `<Commerce base dir>/app/etc/config.php` gespeichert. Das Feld zum Bearbeiten dieses Werts im Admin-Bereich ist deaktiviert.

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

Sie können `--lock-config` verwenden, um Konfigurationswerte festzulegen, wenn Commerce nicht installiert ist. Sie können jedoch Werte nur für den Standardbereich festlegen.

>[!INFO]
>
>Sie können `config.php` auf ein anderes System übertragen, um dort dieselben Konfigurationswerte zu verwenden. Wenn Sie beispielsweise über ein Testsystem verfügen, bedeutet die Verwendung derselben `config.php`, dass Sie nicht dieselben Konfigurationswerte erneut festlegen müssen.

## Wert der Konfigurationseinstellungen anzeigen

Befehlsoptionen:

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

Hierbei gilt

- `--scope` ist der Umfang der Konfiguration (Standard, Website, Store). Der Standardwert ist `default`
- `--scope-code` ist der Konfigurations-Code des Umfangs (Website-Code oder Code für die Store-Ansicht)
- `path` ist der Konfigurationspfad im Format „first_part/second_part/third_part/etc“ (_erforderlich_)

>[!INFO]
>
>Der Befehl `bin/magento config:show` zeigt die Werte aller [verschlüsselten Werte](../reference/config-reference-sens.md) als eine Reihe von Sternchen an: `******`.

### Beispiele

**So zeigen Sie alle gespeicherten Konfigurationen**:

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

**So zeigen Sie alle gespeicherten Konfigurationen für die `base` Website an**:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

Ergebnis:

```
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**Anzeigen der Basis-URL für den Standardbereich**:

```bash
bin/magento config:show web/unsecure/base_url
```

Ergebnis:

```
web/unsecure/base_url - http://example.com/
```

**So zeigen Sie die Basis-URL für die `base` Website an**:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

Ergebnis:

```
web/unsecure/base_url - http://example-for-website.com/
```

**Anzeigen der Basis-URL für den `default` Store**:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

Ergebnis:

```
web/unsecure/base_url - http://example-for-store.com/
```

>[!INFO]
>
>Der Umfangscode kann nur Buchstaben (a-z oder A-Z), Zahlen (0-9) und Unterstriche (_) enthalten. Außerdem muss das erste Zeichen ein Buchstabe sein. Wenn beim Erstellen einer Website- oder Store-Ansicht Großbuchstaben oder Binnenmajuskeln verwendet werden, wird bei der Übereinstimmung intern nicht zwischen Groß- und Kleinschreibung unterschieden, um das Überschreiben von Konfigurationseinstellungen durch Umgebungsvariablen zu ermöglichen. Siehe [Verwenden von Umgebungsvariablen zum Überschreiben der Konfigurationseinstellungen](../reference/override-config-settings.md#environment-variables).

