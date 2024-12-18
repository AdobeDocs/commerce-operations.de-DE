---
title: Master-Datenbanken automatisch konfigurieren
description: Siehe Anleitungen zum automatischen Konfigurieren der Split-Datenbanklösung.
recommendations: noCatalog
exl-id: a27ad097-de60-4cdd-81f9-eb1ae84587e4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# Master-Datenbanken automatisch konfigurieren

{{ee-only}}

{{deprecate-split-db}}

In diesem Thema wird beschrieben, wie Sie mit der Split-Datenbanklösung beginnen, indem Sie:

1. Installieren von Adobe Commerce mit einer einzigen Master-Datenbank (namens `magento`)
1. Erstellen von zwei zusätzlichen Master-Datenbanken für Checkout und OMS (namens `magento_quote` und `magento_sales`)
1. Konfigurieren von Adobe Commerce für die Verwendung der Checkout- und Verkaufsdatenbanken

>[!INFO]
>
>In diesem Handbuch wird davon ausgegangen, dass sich alle drei Datenbanken auf demselben Host wie die Commerce-Anwendung befinden und dass sie `magento`, `magento_quote` und `magento_sales` heißen. Die Wahl, wo die Datenbanken zu finden sind und wie sie benannt sind, liegt jedoch bei Ihnen. Wir hoffen, dass unsere Beispiele die Anweisungen leichter zu befolgen machen.

## Installieren der Adobe Commerce-Software

Sie können Split-Datenbanken jederzeit nach der Installation der Adobe Commerce-Software aktivieren. Mit anderen Worten: Sie können Split-Datenbanken zu einem Adobe Commerce-System hinzufügen, das bereits über Checkout- und Bestelldaten verfügt. Verwenden Sie die Anweisungen in der Adobe Commerce-README oder im [Installationshandbuch](../../installation/overview.md), um die Adobe Commerce-Software mithilfe einer einzigen Master-Datenbank zu installieren.

## Einrichten zusätzlicher Master-Datenbanken

Erstellen Sie Checkout- und OMS-Master-Datenbanken wie folgt:

1. Melden Sie sich bei Ihrem Datenbank-Server als beliebiger Benutzer an.
1. Geben Sie den folgenden Befehl ein, um zu einer MySQL-Eingabeaufforderung zu gelangen:

   ```bash
   mysql -u root -p
   ```

1. Geben Sie bei Aufforderung das Kennwort des MySQL-`root`-Benutzers ein.
1. Geben Sie die folgenden Befehle in der angegebenen Reihenfolge ein, um Datenbankinstanzen mit dem Namen `magento_quote` und `magento_sales` mit denselben Benutzernamen und Kennwörtern zu erstellen:

   ```shell
   create database magento_quote;
   ```

   ```shell
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   ```

   ```shell
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. Geben Sie `exit` ein, um die Eingabeaufforderung zu beenden.

1. Überprüfen Sie die Datenbanken einzeln:

   Checkout-Datenbank:

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   Datenbank des Order Management-Systems:

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   Wenn der MySQL-Monitor angezeigt wird, haben Sie die Datenbank ordnungsgemäß erstellt. Wenn ein Fehler angezeigt wird, wiederholen Sie die vorherigen Befehle.

## Konfigurieren von Commerce für die Verwendung der primären Datenbanken

Nachdem Sie insgesamt drei Master-Datenbanken eingerichtet haben, verwenden Sie die Befehlszeile, um Commerce für deren Verwendung zu konfigurieren. (Der Befehl richtet Datenbankverbindungen ein und verteilt Tabellen auf die Master-Datenbanken.)

### Erste Schritte

Unter [Ausführen von Befehlen](../cli/config-cli.md#running-commands) finden Sie Informationen zum Anmelden und Ausführen von CLI-Befehlen.

### Checkout-Datenbank konfigurieren

Befehlssyntax:

```bash
bin/magento setup:db-schema:split-quote --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

Beispiel:

```bash
bin/magento setup:db-schema:split-quote --host="localhost" --dbname="magento_quote" --username="magento_quote" --password="magento_quote"
```

Die folgende Meldung wird angezeigt, um eine erfolgreiche Einrichtung zu bestätigen:

```
Migration has been finished successfully!
```

### OMS-Datenbank konfigurieren

Befehlssyntax:

```bash
bin/magento setup:db-schema:split-sales --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

Beispiel:

```bash
bin/magento setup:db-schema:split-sales --host="localhost" --dbname="magento_sales" --username="magento_sales" --password="magento_sales"
```

```bash
bin/magento setup:upgrade
```

Die folgende Meldung wird angezeigt, um eine erfolgreiche Einrichtung zu bestätigen:

```
Migration has been finished successfully!
```
