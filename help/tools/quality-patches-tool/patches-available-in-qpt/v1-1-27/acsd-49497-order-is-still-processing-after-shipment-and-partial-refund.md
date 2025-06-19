---
title: 'ACSD-49497: Bestellung noch in Bearbeitung nach Versand und Teilrückerstattung'
description: Wenden Sie den Patch ACSD-49497 an, um das Adobe Commerce-Problem zu beheben, bei dem der Bestellstatus nach dem Versand als Verarbeitung beibehalten wird und eine teilweise Rückerstattung erfolgt.
feature: Admin Workspace, Orders, Shipping/Delivery
role: Admin
exl-id: e2e3d2b3-24be-4827-a735-aebfc6f475ea
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-49497: Bestellung noch in Bearbeitung nach Versand und Teilrückerstattung

Mit dem Patch ACSD-49497 wird das Problem behoben, dass der Bestellstatus nach dem Versand als Verarbeitung beibehalten wird und eine teilweise Rückerstattung angewendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 installiert ist. Die Patch-ID ist ACSD-49497. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Status einer neuen Bestellung bleibt auch nach dem Versand im *[!UICONTROL Processing]* Zustand und es wird eine Teilerstattung angewendet.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Bestellung mit mehreren Artikeln.
1. Erstellen Sie **[!UICONTROL Admin]** eine Rechnung für die Bestellung.
1. Erstellen Sie von **[!UICONTROL Admin]** aus eine Gutschrift und erstatten Sie einen Artikel nur teilweise.
1. Fordern Sie von **[!UICONTROL Admin]** an den Versand der restlichen Artikel in der Bestellung an.
1. Beobachten Sie den Bestellstatus.

<u>Erwartete Ergebnisse</u>:

Der Status der Bestellung sollte *[!UICONTROL Complete]* sein.

<u>Tatsächliche Ergebnisse</u>:

Der Status der Bestellung bleibt *[!UICONTROL Processing]*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
