---
title: Cache-Leerung mit Varnish
description: Erfahren Sie, wie das Cache-Leeren mit Varnish funktioniert und wie Sie es als Web-Caching-Beschleuniger für die Adobe Commerce-Anwendung verwenden.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# Cache-Leerung mit Varnish

In diesem Thema werden die Grundlagen der Verwendung von Varnish als Web-Caching-Beschleuniger für Adobe Commerce und Magento Open Source erläutert.

## Abfallbereinigung

Gemäß [Varnish-Dokumentation](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;A *Bereinigung* ist das, was passiert, wenn Sie ein Objekt aus dem Cache auswählen und zusammen mit seinen Varianten verwerfen.&quot; Eine Bereinigung ähnelt einem Befehl zum Bereinigen des Caches (oder Klicken auf **Magento-Cache leeren** im Admin).

Wenn Sie den Commerce-Cache bereinigen, leeren oder aktualisieren, wird auch der Vorgang &quot;Varnish&quot;bereinigt.

Nachdem Sie Varnish installiert und für die Verwendung mit Commerce konfiguriert haben, können die folgenden Aktionen zu einer Bereinigung des Abstands führen:

- Pflegen einer Website.

   Alles, was Sie beispielsweise im Admin in tun:

   - **SPEICHER** > **Einstellungen** > **Konfiguration** > ALLGEMEIN > **Allgemein**
   - **SPEICHER** > **Einstellungen** > **Konfiguration** > ALLGEMEIN > **Währungseinstellungen**
   - **SPEICHER** > **Einstellungen** > **Konfiguration** > ALLGEMEIN > **E-Mail-Adressen speichern**

   Wenn Commerce eine solche Änderung feststellt, wird eine Meldung angezeigt, die Sie auffordert, den Cache zu aktualisieren.

- Wartung eines Stores (z. B. Hinzufügen oder Bearbeiten von Kategorien, Preisen, Produkten und Preisregeln für Werbeaktionen).

   Die Bereinigung erfolgt automatisch, wenn Sie eine dieser Aufgaben ausführen.

- Pflege des Quellcodes.

   Sie sollten den Cache aktualisieren und auch regelmäßig alle Elemente in `generated/code` und `generated/metadata` Verzeichnissen. Informationen zum Aktualisieren des Caches finden Sie im nächsten Abschnitt.

## Konfigurieren von Commerce zur Bereinigung von Varnish

Commerce bereinigt verschiedene Hosts, nachdem Sie verschiedene Hosts mithilfe der [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#setupconfigset) Befehl.

Sie können den optionalen Parameter verwenden `--http-cache-hosts` -Parameter, um eine kommagetrennte Liste unterschiedlicher Hosts und Listen-Ports anzugeben. Konfigurieren Sie alle gemischten Hosts, unabhängig davon, ob Sie einen oder mehrere Hosts haben. (Trennen Sie Hosts nicht durch Leerzeichen.)

Das Parameterformat muss `<hostname or ip>:<listen port>`, wo Sie weglassen können `<listen port>` wenn es Port 80 ist.

Beispiel:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

Sie können dann beim Aktualisieren des Commerce-Zwischenspeichers (auch als *Reinigung* den Cache) im Admin oder über die Befehlszeile verwenden.

Um den Cache mit dem Admin zu aktualisieren, klicken Sie auf **[!UICONTROL SYSTEM]** > Tools > **Cacheverwaltung** Klicken Sie auf **Magento-Cache leeren** oben auf der Seite. (Sie können auch einzelne Cache-Typen aktualisieren.)

Um den Cache mithilfe der Befehlszeile zu aktualisieren, verwenden Sie normalerweise das [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) als [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md).
