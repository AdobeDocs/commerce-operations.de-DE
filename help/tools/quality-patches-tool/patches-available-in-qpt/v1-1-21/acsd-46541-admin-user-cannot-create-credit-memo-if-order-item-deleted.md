---
title: "ACSD-46541: Ein Administrator kann kein Kreditmemo erstellen, wenn ein Bestellelement gelöscht wird."
description: Wenden Sie den Patch ACSD-46541 an, um das Adobe Commerce-Problem zu beheben, bei dem Sie nach dem Löschen eines Produkts kein Kreditmemo in der Adobe Commerce Admin erstellen können.
feature: Admin Workspace, Orders, Returns
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-46541: Ein Administrator kann kein Kreditmemo erstellen, wenn ein Bestellelement gelöscht wird

Der Patch ACSD-46541 behebt das Problem, dass ein Admin-Benutzer kein Kreditmemo erstellen kann, wenn ein Bestellelement gelöscht wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.21 installiert ist. Die Patch-ID ist ACSD-46541. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.3 - p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nachdem ein Produkt gelöscht wurde, können Sie in der Commerce Admin kein Kreditmemo erstellen.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Commerce Admin an.
1. Erstellen Sie eine Bestellung.
1. Rechnungsstellung.
1. Löschen Sie das Produkt aus der Bestellung.
1. Klicken Sie auf der Seite zur Bestellbearbeitung auf den Link **[!UICONTROL Credit Memo]** .
1. Klicken Sie auf **[!UICONTROL Refund Offline]** , um ein Kreditmemo zu erstellen.

<u>Erwartete Ergebnisse</u>:

Ein Kreditmemo wurde erfolgreich erstellt.

<u>Tatsächliche Ergebnisse</u>:

Die folgenden _Produkte mit angeforderten SKUs wurden nicht gefunden: SKU001_-Fehler wird angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
