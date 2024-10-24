---
title: "ACSD-60816: [!DNL New Relic] vom APM-Agenten eingeführte Browserüberwachungsskripte sind nicht CSP-konform"
description: Wenden Sie den Patch ACSD-60816 an, um das Adobe Commerce-Problem zu beheben, bei dem die vom APM-Agenten eingebrachten [!DNL New Relic] Browserüberwachungsskripte nicht mit Content Security Policy (CSP) konform sind und deren Ausführung verhindert wird.
feature: Tools and External Services, Checkout
role: Admin, Developer
source-git-commit: 278cc668a9d6746a38845e54d173260e1a65bb22
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-60816: [!DNL New Relic] Browserüberwachungsskripte, die vom APM-Agenten eingefügt werden, sind nicht mit CSP konform

Der Patch ACSD-60816 behebt das Problem, dass die vom APM-Agenten eingebrachten [!DNL New Relic]-Browser-Überwachungsskripte nicht mit der Content Security Policy (CSP) konform sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51 installiert ist. Die Patch-ID ist ACSD-60816. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.4.8 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p6

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

[!DNL New Relic] Browserüberwachungsskripte, die vom APM-Agenten eingefügt werden, sind nicht mit CSP konform.

<u>Zu reproduzierende Schritte</u>:

1. Produkt zum Warenkorb hinzufügen.
1. Gehen Sie zum Checkout.

<u>Erwartete Ergebnisse</u>:

In der Entwicklerkonsole gibt es keinen CSP-Fehler.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den folgenden Fehler:

```
Content-Security-Policy: The page's settings blocked an inline script (script-src-elem) from being executed because it violates the following directive: "script-src 
...
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
