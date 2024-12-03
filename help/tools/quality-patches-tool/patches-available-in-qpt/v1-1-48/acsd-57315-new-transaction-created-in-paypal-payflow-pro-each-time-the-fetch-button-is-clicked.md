---
title: 'ACSD-57315: Neue Transaktion wird in [!DNL PayPal Payflow Pro] jedes Mal erstellt, wenn auf die Schaltfläche zum Abrufen geklickt wird'
description: Wenden Sie den Patch ACSD-57315 an, um das Adobe Commerce-Problem zu beheben, bei dem eine neue Transaktion in [!DNL PayPal Payflow Pro] jedes Mal erstellt wird, wenn auf dem Bildschirm "Ansichtstransaktion"im [!UICONTROL Admin] auf die Schaltfläche "Abruf"geklickt wird.
feature: Payments
role: Admin, Developer
exl-id: 1fb8a5af-fda1-4c24-859d-d45424bde12f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-57315: Jedes Mal, wenn auf die Schaltfläche zum Abrufen geklickt wird, wird eine neue Transaktion in [!DNL PayPal Payflow Pro] erstellt

Der Patch ACSD-57315 behebt das Problem, dass bei jedem Klick auf die Schaltfläche &quot;Abruf&quot;auf dem Bildschirm &quot;View transaction&quot;im [!UICONTROL Admin] eine neue Transaktion in [!DNL PayPal Payflow Pro] erstellt wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.48 installiert ist. Die Patch-ID ist ACSD-57315. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.5.0 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Jedes Mal, wenn auf die Schaltfläche &quot;Abruf&quot;im Bildschirm &quot;Transaktionen anzeigen&quot;in [!UICONTROL Admin] geklickt wird, wird eine neue Transaktion in [!DNL PayPal Payflow Pro] erstellt.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie [!DNL PayPal Payflow Pro].
1. Setzen Sie die Transaktionsmethode auf *[!UICONTROL Sale]*.
1. Platzieren Sie eine Bestellung mit *Kreditkarte*.
1. Öffnen Sie die Transaktion über &quot;[!UICONTROL Admin]&quot;.
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Fetch]** .
1. Überprüfen Sie das [!DNL PayPal]-Konto auf Transaktionen im Zusammenhang mit der platzierten Bestellung.

<u>Erwartete Ergebnisse</u>:

Es wird kein neuer Zahlungsvorgang erstellt.

<u>Tatsächliche Ergebnisse</u>:

Ein neuer Zahlungsvorgang wird für eine bereits bezahlte Bestellung erstellt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
