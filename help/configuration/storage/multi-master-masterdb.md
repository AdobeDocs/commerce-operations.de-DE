---
title: Automatische Konfiguration von Master-Datenbanken
description: Siehe Anleitungen zum automatischen Konfigurieren der geteilten Datenbanklösung.
recommendations: noCatalog
exl-id: a27ad097-de60-4cdd-81f9-eb1ae84587e4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# Automatische Konfiguration von Master-Datenbanken

{{ee-only}}

{{deprecate-split-db}}

In diesem Thema werden die ersten Schritte mit der geteilten Datenbanklösung durch folgende Schritte erläutert:

1. Installieren von Adobe Commerce mit einer einzelnen Master-Datenbank (mit dem Namen `magento`)
1. Erstellen von zwei zusätzlichen Master-Datenbanken für den Checkout und OMS (mit den Namen `magento_quote` und `magento_sales`)
1. Konfigurieren von Adobe Commerce für die Verwendung der Checkout- und Verkaufsdatenbanken

>[!INFO]
>
>In diesem Handbuch wird davon ausgegangen, dass sich alle drei Datenbanken auf demselben Host wie die Commerce-Anwendung befinden und dass sie `magento`, `magento_quote` und `magento_sales` heißen. Sie können jedoch selbst entscheiden, wo die Datenbanken zu finden sind und wie sie benannt sind. Wir hoffen, dass unsere Beispiele die Befolgung der Anweisungen erleichtern.

## Installieren der Adobe Commerce-Software

Sie können die Aufspaltung von Datenbanken jederzeit aktivieren, nachdem Sie die Adobe Commerce-Software installiert haben. Mit anderen Worten, Sie können Aufspaltungsdatenbanken zu einem Adobe Commerce-System hinzufügen, das bereits über Kasse- und Bestelldaten verfügt. Verwenden Sie die Anweisungen im Adobe Commerce README-Handbuch oder im [Installationshandbuch](../../installation/overview.md), um die Adobe Commerce-Software mit einer einzigen Master-Datenbank zu installieren.

## Einrichten zusätzlicher Master-Datenbanken

Erstellen Sie wie folgt Checkout- und OMS-Master-Datenbanken:

1. Melden Sie sich bei Ihrem Datenbankserver als ein beliebiger Benutzer an.
1. Geben Sie den folgenden Befehl ein, um zu einer MySQL-Eingabeaufforderung zu gelangen:

   ```bash
   mysql -u root -p
   ```

1. Geben Sie bei Aufforderung das Kennwort des MySQL `root`-Benutzers ein.
1. Geben Sie die folgenden Befehle in der angezeigten Reihenfolge ein, um Datenbankinstanzen mit den Namen `magento_quote` und `magento_sales` mit denselben Benutzernamen und Passwörtern zu erstellen:

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

   Datenbank des Bestellmanagementsystems:

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   Wenn der MySQL-Monitor angezeigt wird, haben Sie die Datenbank ordnungsgemäß erstellt. Wenn ein Fehler angezeigt wird, wiederholen Sie die vorherigen Befehle.

## Konfigurieren von Commerce für die Verwendung von Master-Datenbanken

Nachdem Sie insgesamt drei Master-Datenbanken eingerichtet haben, konfigurieren Sie über die Befehlszeile Commerce für deren Verwendung. (Der Befehl richtet Datenbankverbindungen ein und verteilt Tabellen auf die Master-Datenbanken.)

### Erste Schritte

Siehe [Ausführen von Befehlen](../cli/config-cli.md#running-commands) , um sich anzumelden und CLI-Befehle auszuführen.

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
