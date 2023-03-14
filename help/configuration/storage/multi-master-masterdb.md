---
title: Automatische Konfiguration Übergeordneter Datenbanken
description: Siehe Anleitungen zum automatischen Konfigurieren der geteilten Datenbanklösung.
source-git-commit: d029d1ac66bff2ac34b22b2d3b8aafbfc062e082
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---


# Automatische Konfiguration Übergeordneter Datenbanken

{{ee-only}}

{{deprecate-split-db}}

In diesem Thema werden die ersten Schritte mit der geteilten Datenbanklösung durch folgende Schritte erläutert:

1. Installieren von Adobe Commerce mit einer einzigen Übergeordneten Datenbank (mit dem Namen `magento`)
1. Erstellen von zwei zusätzlichen Übergeordneten Datenbanken für [Kasse](https://glossary.magento.com/checkout) und OMS (mit dem Namen `magento_quote` und `magento_sales`)
1. Konfigurieren von Adobe Commerce für die Verwendung der Checkout- und Verkaufsdatenbanken

>[!INFO]
>
>In diesem Handbuch wird davon ausgegangen, dass sich alle drei Datenbanken auf demselben Host wie die Commerce-Anwendung befinden und dass sie `magento`, `magento_quote`und `magento_sales`. Sie können jedoch selbst entscheiden, wo die Datenbanken zu finden sind und wie sie benannt sind. Wir hoffen, dass unsere Beispiele die Befolgung der Anweisungen erleichtern.

## Installieren der Adobe Commerce-Software

Sie können die Aufspaltung von Datenbanken jederzeit nach der Installation der Adobe Commerce-Software aktivieren. Sie können also geteilte Datenbanken zu einem Adobe Commerce-System hinzufügen, das bereits über Kasse- und Bestelldaten verfügt. Verwenden Sie die Anweisungen in Adobe Commerce README oder dem [Installationshandbuch](../../installation/overview.md) , um die Adobe Commerce-Software mit einer einzigen Übergeordneten Datenbank zu installieren.

## Einrichten zusätzlicher Übergeordneter Datenbanken

Erstellen Sie die Übergeordneten Datenbanken Checkout und OMS wie folgt:

1. Melden Sie sich bei Ihrem Datenbankserver als ein beliebiger Benutzer an.
1. Geben Sie den folgenden Befehl ein, um zu einer MySQL-Eingabeaufforderung zu gelangen:

   ```bash
   mysql -u root -p
   ```

1. MySQL eingeben `root` das Kennwort des Benutzers bei Aufforderung.
1. Geben Sie die folgenden Befehle in der angezeigten Reihenfolge ein, um Datenbankinstanzen mit dem Namen `magento_quote` und `magento_sales` mit denselben Benutzernamen und Kennwörtern:

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

1. Eingabe `exit` , um die Eingabeaufforderung zu beenden.

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

## Konfigurieren von Commerce für die Verwendung Übergeordneter Datenbanken

Nachdem Sie insgesamt drei Übergeordnete Datenbanken eingerichtet haben, konfigurieren Sie über die Befehlszeile Commerce für deren Verwendung. (Der Befehl richtet Datenbankverbindungen ein und verteilt Tabellen auf die Übergeordneten Datenbanken.)

### Erste Schritte

Siehe [Ausführen von Befehlen](../cli/config-cli.md#running-commands) um sich anzumelden und CLI-Befehle auszuführen.

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

```terminal
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

```terminal
Migration has been finished successfully!
```
