---
title: 'ACSD-46869: Konfigurierbare Produkte, die beim Checkout nicht mit der REST-API aktualisiert werden'
description: Der Patch ACSD-46869 behebt das Problem, dass die konfigurierbaren Produkte beim Checkout nicht mit der REST-API aktualisiert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 installiert ist. Die Patch-ID ist ACSD-46869. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
exl-id: f03d4b24-ac95-406e-8e9d-908149b9207c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-46869: Konfigurierbare Produkte, die beim Checkout nicht mit der REST-API aktualisiert werden

Der Patch ACSD-46869 behebt das Problem, dass konfigurierbare Produkte beim Checkout nicht mit der REST-API aktualisiert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 installiert ist. Die Patch-ID ist ACSD-46869. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der [[!DNL QPT] Landingpage](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Konfigurierbare Produkte werden beim Checkout nicht mit der REST-API aktualisiert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit Attributen für Farbe und Größe.
1. Wählen Sie **[!UICONTROL Options]** aus und fügen Sie das Produkt zum Warenkorb hinzu.
1. Wechseln Sie zu &quot;**[!UICONTROL Checkout]**&quot;, aktualisieren Sie die Größe mehrmals mit Ausnahme von &quot;qty&quot;und überprüfen Sie die Anforderung und Antwort.
1. Sie erhalten die folgende Antwort, wenn Sie die Größe aktualisieren.

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>Erwartete Ergebnisse</u>:

Der Wert wird entsprechend den Änderungen aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

`option_value` wird nicht aktualisiert. Wenn also die Bestellung platziert wird, hat sie den alten Größenwert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tools] > Nutzung](/help/tools/quality-patches-tool/usage.md) im Handbuch zum Werkzeug für Qualitätsmuster.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in [!DNL QPT] verfügbaren Patches finden Sie unter [In  [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbare Patches im Handbuch zum Werkzeug für Qualitätsmuster .
