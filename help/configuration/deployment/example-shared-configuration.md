---
title: Beispiel mit einer freigegebenen Konfiguration
description: Sehen Sie sich ein Beispiel an, wie Sie Einstellungen in einem Entwicklungssystem mit einer freigegebenen Konfigurationsdatei ändern.
exl-id: c980ec01-ca2d-43db-b68d-8e9435e07e6a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# Beispiel mit einer freigegebenen Konfiguration

Dieses Beispiel zeigt, wie Sie die folgenden Einstellungen in Ihrem Entwicklungssystem ändern, die freigegebene Konfigurationsdatei aktualisieren, `config.php`, in Ihrem Build-System und implementieren Sie dieselben Einstellungen in Ihrem Produktionssystem:

- Zeitzone
- Gewichtseinheit

Diese Einstellungen sind in Admin verfügbar in **Stores** > Einstellungen > **Konfiguration** > Allgemein > **Allgemein**.

Sie können dasselbe Verfahren verwenden, um nicht vertrauliche, nicht systemspezifische Einstellungen in den folgenden Referenzen zu konfigurieren:

- [Andere Konfigurationspfade - Referenz](../reference/config-reference-general.md)
- [Referenz zu Zahlungskonfigurationspfaden](../reference/config-reference-payment.md)
- [Referenz zu den Konfigurationspfaden für Commerce Enterprise B2B-Erweiterungen](../reference/config-reference-b2b.md)

## Bevor Sie beginnen

Richten Sie zunächst die Dateisystemberechtigungen und den Eigentümer ein, wie hier beschrieben: [Voraussetzungen für Entwicklungs-, Build- und Produktionssysteme](../deployment/prerequisites.md).

## Annahmen

Dieses Thema enthält ein Beispiel für die Änderung der Konfiguration des Produktionssystems. Sie können bei Bedarf verschiedene Konfigurationsoptionen auswählen.

Für die Zwecke dieses Beispiels gehen wir von Folgendem aus:

- Verwenden Sie die Git-Quellsteuerung.
- Das Entwicklungssystem ist in einem Git-Remote-Repository mit dem Namen `mconfig`
- Ihre Git-Arbeitsverzweigung heißt `m2.2_deploy`

## Schritt 1: Konfiguration im Entwicklungssystem festlegen

So legen Sie die Zeitzonen- und Gewichtseinheiten in Ihrem Entwicklungssystem fest:

1. Melden Sie sich beim Administrator an.
1. Klicks **Stores** > Einstellungen > **Konfiguration** > Allgemein > **Allgemein**.
1. Erweitern Sie im rechten Bereich **Gebietsschemaoptionen**.

   Die folgende Abbildung zeigt ein Beispiel.

   ![Festlegen von Gebietsschemaoptionen im Entwicklungssystem](../../assets/configuration/split-deploy-set-locale.png)

1. Aus dem **Zeitzone** Liste, klicken Sie **GMT+00:00 (UTC)**.
1. Löschen Sie die **Systemwert verwenden** Kontrollkästchen neben dem **Gewichtseinheit** -Feld.
1. Aus dem **Gewichtseinheit** Liste, klicken Sie **kgs**.
1. Klicks **Konfiguration speichern**.
1. Wenn Sie dazu aufgefordert werden, leeren Sie den Cache.

## Schritt 2: Aktualisierung der freigegebenen Konfiguration

Generieren Sie die freigegebene Konfigurationsdatei, `app/etc/config.php`, in Ihrem Entwicklungssystem und übertragen Sie es mithilfe der Quell-Code-Verwaltung auf Ihr Build-System, wie in diesem Abschnitt beschrieben.

{{$include /help/_includes/config-save-config.md}}

## Schritt 3: Aktualisieren Sie Ihr Build-System und generieren Sie Dateien.

Nachdem Sie Ihre Änderungen an der freigegebenen Konfiguration an die Quell-Code-Verwaltung übertragen haben, können Sie diese Änderungen in Ihrem Build-System abrufen, Code kompilieren und statische Dateien generieren. Der letzte Schritt besteht darin, diese Änderungen in Ihr Produktionssystem zu übernehmen. Daher stimmt die Konfiguration Ihres Produktionssystems mit Ihrem Entwicklungssystem überein.

{{$include /help/_includes/config-update-build-system.md}}

## Schritt 4: Produktionssystem aktualisieren

Der letzte Schritt im Prozess besteht darin, Ihr Produktionssystem von der Quell-Code-Verwaltung zu aktualisieren. Dadurch werden alle Änderungen abgerufen, die Sie an Ihren Entwicklungs- und Build-Systemen vorgenommen haben. Das bedeutet, dass Ihr Produktionssystem vollständig auf dem neuesten Stand ist.

{{$include /help/_includes/config-update-prod-system.md}}

### Überprüfen der Änderungen in der Admin-Konsole

**Um sicherzustellen, dass diese Einstellungen in Admin nicht bearbeitet werden können**:

1. Melden Sie sich beim Administrator an.
1. Klicks **Stores** > Einstellungen > **Konfiguration** > Allgemein > **Allgemein**.
1. Erweitern Sie im rechten Bereich **Gebietsschemaoptionen**.

   Die soeben festgelegten Optionen werden wie folgt angezeigt:

   ![Konfigurationsoptionen sind in Admin nicht bearbeitbar](../../assets/configuration/split-deploy-not-editable.png)

>[!INFO]
>
>Um eine Einstellung zu ändern, die im Admin gesperrt ist, verwenden Sie die [`magento config:set --lock` command](../cli/set-configuration-values.md).
