---
title: Beispiel mit einer freigegebenen Konfiguration
description: Sehen Sie sich ein Beispiel an, wie Sie Einstellungen in einem Entwicklungssystem mit einer freigegebenen Konfigurationsdatei ändern.
exl-id: c980ec01-ca2d-43db-b68d-8e9435e07e6a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Beispiel mit einer freigegebenen Konfiguration

In diesem Beispiel wird gezeigt, wie Sie die folgenden Einstellungen in Ihrem Entwicklungssystem ändern, die freigegebene Konfigurationsdatei `config.php` in Ihrem Build-System aktualisieren und dieselben Einstellungen in Ihr Produktionssystem implementieren:

- Zeitzone
- Gewichtseinheit

Diese Einstellungen sind im Admin unter **Geschäfte** > Einstellungen > **Konfiguration** > Allgemein > **Allgemein** verfügbar.

Sie können dasselbe Verfahren verwenden, um nicht vertrauliche, nicht systemspezifische Einstellungen in den folgenden Referenzen zu konfigurieren:

- [Andere Konfigurationspfade - Referenz](../reference/config-reference-general.md)
- [Referenz zu Zahlungskonfigurationspfaden](../reference/config-reference-payment.md)
- [Commerce Enterprise B2B-Erweiterungs-Konfigurationspfade - Referenz](../reference/config-reference-b2b.md)

## Bevor Sie beginnen

Richten Sie zunächst Dateisystemberechtigungen und -eigentum ein, wie unter [Voraussetzungen für Entwicklung, Build und Produktionssysteme](../deployment/prerequisites.md) beschrieben.

## Annahmen

Dieses Thema enthält ein Beispiel für die Änderung der Konfiguration des Produktionssystems. Sie können bei Bedarf verschiedene Konfigurationsoptionen auswählen.

Für die Zwecke dieses Beispiels gehen wir von Folgendem aus:

- Verwenden Sie die Git-Quellsteuerung.
- Das Entwicklungssystem ist in einem Git-Remote-Repository mit dem Namen `mconfig` verfügbar
- Ihre Git-Arbeitsverzweigung heißt `m2.2_deploy`

## Schritt 1: Konfiguration im Entwicklungssystem festlegen

So legen Sie die Zeitzonen- und Gewichtseinheiten in Ihrem Entwicklungssystem fest:

1. Melden Sie sich beim Administrator an.
1. Klicken Sie auf **Stores** > Einstellungen > **Konfiguration** > Allgemein > **Allgemein**.
1. Erweitern Sie im rechten Bereich **Gebietsschema-Optionen**.

   Die folgende Abbildung zeigt ein Beispiel.

   ![Gebietsschemaoptionen im Entwicklungssystem festlegen](../../assets/configuration/split-deploy-set-locale.png)

1. Klicken Sie in der Liste **Zeitzone** auf **GMT+00:00 (UTC)**.
1. Deaktivieren Sie das Kontrollkästchen **Systemwert verwenden** neben dem Feld **Gewichtungseinheit** .
1. Klicken Sie in der Liste **Gewichtungseinheit** auf **kgs**.
1. Klicken Sie auf **Konfiguration speichern**.
1. Wenn Sie dazu aufgefordert werden, leeren Sie den Cache.

## Schritt 2: Aktualisierung der freigegebenen Konfiguration

Generieren Sie die freigegebene Konfigurationsdatei &quot;`app/etc/config.php`&quot; in Ihrem Entwicklungssystem und übertragen Sie sie mithilfe der Quell-Code-Verwaltung auf Ihr Build-System, wie in diesem Abschnitt beschrieben.

{{$include /help/_includes/config-save-config.md}}

## Schritt 3: Aktualisieren Sie Ihr Build-System und generieren Sie Dateien.

Nachdem Sie Ihre Änderungen an der freigegebenen Konfiguration an die Quell-Code-Verwaltung übertragen haben, können Sie diese Änderungen in Ihrem Build-System abrufen, Code kompilieren und statische Dateien generieren. Der letzte Schritt besteht darin, diese Änderungen in Ihr Produktionssystem zu übernehmen. Daher stimmt die Konfiguration Ihres Produktionssystems mit Ihrem Entwicklungssystem überein.

{{$include /help/_includes/config-update-build-system.md}}

## Schritt 4: Produktionssystem aktualisieren

Der letzte Schritt im Prozess besteht darin, Ihr Produktionssystem von der Quell-Code-Verwaltung zu aktualisieren. Dadurch werden alle Änderungen abgerufen, die Sie an Ihren Entwicklungs- und Build-Systemen vorgenommen haben. Das bedeutet, dass Ihr Produktionssystem vollständig auf dem neuesten Stand ist.

{{$include /help/_includes/config-update-prod-system.md}}

### Überprüfen der Änderungen in der Admin-Konsole

**Um sicherzustellen, dass diese Einstellungen in Admin** nicht bearbeitet werden können:

1. Melden Sie sich beim Administrator an.
1. Klicken Sie auf **Stores** > Einstellungen > **Konfiguration** > Allgemein > **Allgemein**.
1. Erweitern Sie im rechten Bereich **Gebietsschema-Optionen**.

   Die soeben festgelegten Optionen werden wie folgt angezeigt:

   ![Konfigurationsoptionen können im Admin nicht bearbeitet werden](../../assets/configuration/split-deploy-not-editable.png)

>[!INFO]
>
>Um eine Einstellung zu ändern, die in Admin gesperrt ist, verwenden Sie den Befehl [`magento config:set --lock`](../cli/set-configuration-values.md).
