---
title: "ACSD-61845: Fehler tritt bei Anforderungen mit Text/html accept-Kopfzeile auf."
description: Wenden Sie den Patch ACSD-61845 an, um das Adobe Commerce-Problem zu beheben, bei dem das Senden einer HTTP-Anfrage mit nur einem *text/html* accept-Header einen 500-Fehler verursacht, bei dem B2B-Module installiert sind.
feature: B2B
role: Admin, Developer
source-git-commit: 8dbf91806097281fb4f7c74e182f10b09b18e925
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-61845: Fehler tritt bei Anforderungen mit der Überschrift *text/html* accept auf

Der Patch ACSD-61845 behebt das Problem, bei dem eine HTTP-Anfrage mit nur einem *text/html* -Accept-Header einen 500-Fehler verursacht, da bei der Antwortverarbeitung Diskrepanzen zwischen den Medientypen vorliegen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 installiert ist. Die Patch-ID ist ACSD-61845. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Senden einer HTTP-Anfrage mit nur *text/html* im accept-Header tritt ein 500-Fehler auf, da in der Medientyp-Konfiguration eine Diskrepanz vorliegt.

<u>Voraussetzungen</u>:

B2B-Module werden installiert und aktiviert.

<u>Zu reproduzierende Schritte</u>:

1. Senden Sie wie folgt eine Anfrage mit nur *text/html* im accept-Header:

   ```
   curl -I --header "Accept: text/html, text/plain" http://<hostname>/pub/
   ```

<u>Erwartete Ergebnisse</u>:

Die Seite wird mit dem Statuscode *200* zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Es wird ein 500-Fehler zurückgegeben, wobei die folgende Fehlermeldung im `exception.log` enthalten ist:

```
Magento\Framework\Webapi\Exception: Server cannot match any of the given Accept HTTP header media type(s) from the request: "text/html" with media types from the config of response renderer. in vendor/magento/framework/Webapi/Rest/Response/RendererFactory.php:84
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

[[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
