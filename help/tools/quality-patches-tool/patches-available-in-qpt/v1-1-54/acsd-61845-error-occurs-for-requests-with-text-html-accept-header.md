---
title: 'ACSD-61845: Fehler tritt bei Anfragen mit text/html Accept-Header auf'
description: Wenden Sie den Patch ACSD-61845 an, um das Adobe Commerce-Problem zu beheben, bei dem das Senden einer HTTP-Anfrage mit nur einem Accept-Header für *text/html* einen 500-Fehler verursacht, wobei B2B-Module installiert sind.
feature: B2B
role: Admin, Developer
exl-id: 6fa6c3ff-bb45-4b9e-afd4-95692acb0a90
source-git-commit: 29845fd4a8c1c744aa780e60bb4154dfc3c1a02c
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-61845: Bei Anfragen mit dem Accept-Header *text/*&quot; tritt ein Fehler auf

Mit dem Patch ACSD-61845 wird das Problem behoben, dass eine HTTP-Anfrage mit nur einer *text/html* Accept-Kopfzeile einen 500-Fehler verursacht, da bei der Antwortverarbeitung keine Übereinstimmung mit dem Medientyp vorliegt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 installiert ist. Die Patch-ID ist ACSD-61845. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Senden einer HTTP-Anfrage mit nur *text/html* in der Accept-Kopfzeile tritt ein 500-Fehler aufgrund einer Nichtübereinstimmung in der Medientyp-Konfiguration auf.

<u>Voraussetzungen</u>:

B2B-Module sind installiert und aktiviert.

<u>Schritte zur Reproduktion</u>:

1. Senden Sie wie folgt eine Anfrage, *im Accept* Header nur „text/html“ enthält:

   ```
   curl -I --header "Accept: text/html, text/plain" http://<hostname>/pub/
   ```

<u>Erwartete Ergebnisse</u>:

Die Seite wird mit einem *200-Status-Code)*.

<u>Tatsächliche Ergebnisse</u>:

Es wird ein 500-Fehler zurückgegeben, mit der folgenden Fehlermeldung im `exception.log`:

```
Magento\Framework\Webapi\Exception: Server cannot match any of the given Accept HTTP header media type(s) from the request: "text/html" with media types from the config of response renderer. in vendor/magento/framework/Webapi/Rest/Response/RendererFactory.php:84
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

[[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
