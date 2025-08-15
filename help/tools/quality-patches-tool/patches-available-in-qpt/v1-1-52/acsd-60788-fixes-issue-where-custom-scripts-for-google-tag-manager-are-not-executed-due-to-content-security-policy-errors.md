---
title: 'ACSD-60788: Benutzerdefinierte Skripte für  [!DNL Google Tag Manager]  aufgrund von CSP-Fehlern nicht ausgeführt'
description: Wenden Sie den ACSD-60788-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem benutzerdefinierte Skripte für  [!DNL Google Tag Manager]  aufgrund von CSP-Fehlern (Content Security Policy) nicht ausgeführt werden.
feature: Security
role: Admin, Developer
exl-id: 3392da76-86cb-4357-8658-c95d914a5829
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-60788: Benutzerdefinierte Skripte für [!DNL Google Tag Manager] werden aufgrund von Fehlern in der Content Security Policy nicht ausgeführt

Der Patch ACSD-60788 behebt das Problem, dass benutzerdefinierte Skripte für [!DNL Google Tag Manager] aufgrund von Fehlern in der Content Security Policy nicht ausgeführt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 installiert ist. Die Patch-ID ist ACSD-60788. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzerdefinierte Skripte für [!DNL Google Tag Manager] werden aufgrund von CSP-Fehlern (Content Security Policy) nicht ausgeführt.

<u>Schritte zur Reproduktion</u>:

1. Richten Sie die *[!DNL Google Tag Manager]* ein.
1. Richten Sie das *[!DNL Google Tag Manager]* benutzerdefinierte HTML-Tag ein.
1. Fügen Sie den folgenden JavaScript-Code in das erste Tag ein:

   ```
   <script nonce="{{gtmNonce}}">
   console.log("Nonce from simple JS {{gtmNonce}}");
   </script>
   ```

1. Leeren Sie Caches nach der Einrichtung von *GTM*.
1. Öffnen Sie die Entwicklerkonsole in Ihrem Browser.
1. Öffnen Sie die Startseite.

<u>Erwartete Ergebnisse</u>:

Die Entwicklerkonsole des Browsers zeigt *Nonce aus einfacher JS (zufällige Zeichen)*.

<u>Tatsächliche Ergebnisse</u>:

Die Browser-Dev-Konsole zeigt *Nonce aus Simple JS undefined* an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
