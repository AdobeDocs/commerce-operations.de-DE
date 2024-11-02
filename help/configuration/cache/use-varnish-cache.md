---
title: Cache-Leerung mit Varnish
description: Erfahren Sie, wie das Cache-Leeren mit Varnish funktioniert und wie Sie es als Web-Caching-Beschleuniger für die Adobe Commerce-Anwendung verwenden.
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Cache-Leerung mit Varnish

In diesem Thema werden die Grundlagen der Verwendung von Varnish als Web-Caching-Beschleuniger für Adobe Commerce erläutert.

## Abfallbereinigung

Gemäß der [Varnish-Dokumentation](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html) &quot;Eine *Bereinigung* ist das, was passiert, wenn Sie ein Objekt aus dem Cache auswählen und zusammen mit seinen Varianten verwerfen.&quot; Eine Bereinigung ähnelt einem Befehl zum Bereinigen des Caches (oder klicken Sie im Admin auf **Magento-Cache leeren** ).

Wenn Sie den Commerce-Cache löschen, leeren oder aktualisieren, wird auch der Bereinigungsvorgang durchgeführt.

Nachdem Sie Varnish installiert und für die Verwendung mit Commerce konfiguriert haben, können die folgenden Aktionen zu einer Bereinigung des Abstands führen:

- Pflegen einer Website.

  Alles, was Sie beispielsweise im Admin in tun:

   - **STORES** > **settings** > **configuration** > ALLGEMEIN > **general**
   - **STORES** > **settings** > **configuration** > ALLGEMEIN > **Currency Setup**
   - **STORES** > **Einstellungen** > **Konfiguration** > ALLGEMEIN > **E-Mail-Adressen speichern**

  Wenn Commerce eine solche Änderung feststellt, wird eine Meldung angezeigt, die Sie auffordert, den Cache zu aktualisieren.

- Wartung eines Stores (z. B. Hinzufügen oder Bearbeiten von Kategorien, Preisen, Produkten und Preisregeln für Werbeaktionen).

  Die Bereinigung erfolgt automatisch, wenn Sie eine dieser Aufgaben ausführen.

- Pflege des Quellcodes.

  Sie sollten den Cache aktualisieren und auch regelmäßig alles in den Verzeichnissen `generated/code` und `generated/metadata` löschen. Informationen zum Aktualisieren des Caches finden Sie im nächsten Abschnitt.

## Konfigurieren von Commerce zum Bereinigen von Varnish

Commerce löscht verschiedene Hosts, nachdem Sie mit dem Befehl [`magento setup:config:set`](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#setupconfigset) verschiedene Hosts konfiguriert haben.

Sie können den optionalen Parameter `--http-cache-hosts` verwenden, um eine kommagetrennte Liste von &quot;Varnish Hosts&quot;und &quot;Listen Ports&quot;anzugeben. Konfigurieren Sie alle gemischten Hosts, unabhängig davon, ob Sie einen oder mehrere Hosts haben. (Trennen Sie Hosts nicht durch Leerzeichen.)

Das Parameterformat muss `<hostname or ip>:<listen port>` sein, wobei Sie `<listen port>` weglassen können, wenn es Port 80 ist.

Beispiel:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

Sie können dann &quot;Varnish&quot;-Hosts bereinigen, wenn Sie den Commerce-Cache (auch als *Bereinigung* des Caches bezeichnet) im Admin oder über die Befehlszeile aktualisieren.

Um den Cache mithilfe von Admin zu aktualisieren, klicken Sie auf &quot;**[!UICONTROL SYSTEM]**&quot;> &quot;Tools&quot;> &quot;**Cache-Verwaltung**&quot;, und klicken Sie dann oben auf der Seite auf &quot;**Magento-Cache leeren&quot;** . (Sie können auch einzelne Cache-Typen aktualisieren.)

Um den Cache mithilfe der Befehlszeile zu aktualisieren, verwenden Sie normalerweise den Befehl [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) als [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md).
