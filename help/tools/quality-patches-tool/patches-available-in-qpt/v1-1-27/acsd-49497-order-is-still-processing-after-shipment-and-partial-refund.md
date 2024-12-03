---
title: 'ACSD-49497: Auftragsabwicklung nach dem Versand und Teilrückerstattung'
description: Wenden Sie den Patch ACSD-49497 an, um das Adobe Commerce-Problem zu beheben, bei dem der Auftragsstatus nach dem Versand als Verarbeitung beibehalten wird und eine teilweise Rückerstattung erfolgt.
feature: Admin Workspace, Orders, Shipping/Delivery
role: Admin
exl-id: e2e3d2b3-24be-4827-a735-aebfc6f475ea
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-49497: Auftragsabwicklung nach dem Versand und Teilrückerstattung

Der Patch ACSD-49497 behebt das Problem, dass der Auftragsstatus nach dem Versand als Verarbeitung gilt und eine teilweise Rückerstattung erfolgt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 installiert ist. Die Patch-ID lautet ACSD-49497. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Status einer neuen Bestellung bleibt auch nach dem Versand im Status *[!UICONTROL Processing]* und es wird eine teilweise Rückerstattung vorgenommen.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Bestellung mit mehreren Elementen.
1. Erstellen Sie von **[!UICONTROL Admin]** eine Rechnung für die Bestellung.
1. Erstellen Sie ab **[!UICONTROL Admin]** ein Kreditmemo und erstatten Sie einen Artikel nur teilweise zurück.
1. Fordern Sie von **[!UICONTROL Admin]** den Versand für die verbleibenden Elemente in der Bestellung an.
1. Beobachten Sie den Bestellstatus.

<u>Erwartete Ergebnisse</u>:

Der Status der Bestellung sollte *[!UICONTROL Complete]* sein.

<u>Tatsächliche Ergebnisse</u>:

Der Status der Bestellung bleibt *[!UICONTROL Processing]*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
