---
title: "ACSD-49389: Bereit für Abruf-E-Mail, die von der API gesendet wird, wenn sie nicht bereit für Abruf ist"
description: Wenden Sie den Patch ACSD-49389 an, um das Adobe Commerce-Problem zu beheben, bei dem eine für die Abruf-E-Mail bereite E-Mail von der API gesendet wird, wenn die Bestellung nicht bereit zur Abholung ist.
feature: REST, Communications
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49389: Bereit für die Abruf-E-Mail, die von der API gesendet wird, wenn sie nicht bereit zur Abruf ist

Der Patch ACSD-49389 behebt das Problem, dass eine Vorabruf-E-Mail von der API gesendet wird, wenn die Bestellung noch nicht abgeholt werden kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 installiert ist. Die Patch-ID lautet ACSD-49389. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` -Paket auf die neueste Version und überprüfen Sie die Kompatibilität auf der [QPT-Landingpage](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eine Vorabruf-E-Mail wird von der API gesendet, wenn die Bestellung noch nicht abgeholt werden kann.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie die *[!UICONTROL In-Store Delivery]* -Methode.
1. Erstellen Sie eine Stock-Quelle mit aktiviertem Pickup-Speicherort.
1. Erstellen Sie ein neues Lager mithilfe der Haupt-Website mit der oben erstellten Quelle.
1. Erstellen Sie ein Produkt, das dieselbe Quelle zuweist.
1. Legen Sie die Aktienanzahl = 1 fest.
1. Sehen Sie sich das Produkt an, das in Schritt 4 mit der Methode *[!UICONTROL In-Store Delivery]* in der Storefront erstellt wurde.
1. Erstellen Sie eine Rechnung für die Bestellung.
1. Setzen Sie die Menge des Produkts auf *0* und machen Sie es aus dem Lager.
1. Posten Sie die folgende API-Anfrage:

```
{
    "orderIds": [
        1
    ]
}
```

<u>Erwartete Ergebnisse</u>:

Bereit für die Abruf-E-Mail wird nicht gesendet.

<u>Tatsächliche Ergebnisse</u>:

Die API gibt *Bestellung ist nicht bereit für die Aufnahme* zurück, aber bereit für die Abruf-E-Mail wird gesendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbare Patches im [!DNL Quality Patches Tool] -Handbuch.
