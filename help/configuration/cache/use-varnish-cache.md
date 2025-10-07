---
title: Cache-Löschen mit Lack
description: Erfahren Sie, wie das Löschen von Caches mit dem Web-Caching-Beschleuniger von Varnish für Adobe Commerce funktioniert. Entdecken Sie Methoden zur Cache-Verwaltung und -Optimierung.
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# Cache-Löschen mit Lack

In diesem Abschnitt werden die Grundlagen der Verwendung von Varnish als Web-Caching-Beschleuniger für Adobe Commerce erläutert.

## Lackspülung

In der [-](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html) heißt es: „Eine *Bereinigung* geschieht, wenn Sie ein Objekt aus dem Cache auswählen und zusammen mit seinen Varianten verwerfen.“ Eine Lackbereinigung ähnelt einem Cache-Bereinigungsbefehl (oder einem Klick auf **Magento-Cache leeren** in Admin).

Wenn Sie den Commerce-Cache bereinigen, leeren oder aktualisieren, bereinigt Varnish auch.

Nachdem Sie Varnish für die Verwendung mit Commerce installiert und konfiguriert haben, können die folgenden Aktionen zu einer Lackbereinigung führen:

- Wartung einer Website.

  Zum Beispiel alles, was Sie im Admin-Bereich in tun:

   - **STORES** > **Settings** > **Configuration** > GENERAL > **General**
   - **STORES** > **Einstellungen** > **Konfiguration** > ALLGEMEIN > **Währungseinstellungen**
   - **STORES** > **Einstellungen** > **Konfiguration** > ALLGEMEIN > **E-Mail-Adressen speichern**

  Wenn Commerce eine solche Änderung erkennt, werden Sie in einer Meldung darüber informiert, dass Sie den Cache aktualisieren müssen.

- Verwaltung eines Stores (z. B. Hinzufügen oder Bearbeiten von Kategorien, Preisen, Produkten und Preisregeln für Werbeaktionen).

  Der Lack wird automatisch bereinigt, wenn Sie eine dieser Aufgaben ausführen.

- Pflege des Quell-Codes

  Sie sollten den Cache aktualisieren und auch regelmäßig alles in den `generated/code`- und `generated/metadata` löschen. Informationen zum Aktualisieren des Caches finden Sie im nächsten Abschnitt.

## Konfigurieren von Commerce zum Löschen von Lack

Commerce löscht Varnish-Hosts, nachdem Sie Varnish-Hosts mit dem Befehl [`magento setup:config:set`](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/cli-reference/commerce-on-premises#setupconfigset) konfiguriert haben.

Sie können den optionalen Parameter `--http-cache-hosts` verwenden, um eine kommagetrennte Liste von Lack-Hosts und Listener-Ports anzugeben. Konfigurieren Sie alle Lack-Hosts, unabhängig davon, ob Sie einen oder mehrere haben. (Hosts dürfen nicht durch Leerzeichen getrennt werden.)

Das Parameterformat muss `<hostname or ip>:<listen port>` sein, wobei Sie `<listen port>` auslassen können, wenn es sich um Port 80 handelt.

Beispiel:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

Sie können dann Varnish-Hosts bereinigen, wenn Sie den Commerce-Cache (auch als *bezeichnet)* Admin aktualisieren oder die Befehlszeile verwenden.

Um den Cache mithilfe der Admin zu aktualisieren, klicken Sie auf **[!UICONTROL SYSTEM]** > Tools **Cache-Verwaltung** und dann oben auf der Seite **Magento-** leeren). (Sie können auch einzelne Cache-Typen aktualisieren.)

Um den Cache mithilfe der Befehlszeile zu aktualisieren, verwenden Sie normalerweise den [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types)-Befehl als [Dateisystembesitzer](../../installation/prerequisites/file-system/overview.md).
