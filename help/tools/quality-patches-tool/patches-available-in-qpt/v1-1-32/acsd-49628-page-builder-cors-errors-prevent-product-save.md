---
title: "ACSD-49628: [!DNL Page Builder] CORS-Fehler verhindern das Speichern von Produkten"
description: Wenden Sie den Patch ACSD-49628 an, um das Adobe Commerce-Problem zu beheben, bei dem die [!DNL Page Builder] CORS-Fehler das Speichern des Produkts verhindern.
feature: Categories, Page Builder, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-49628: [!DNL Page Builder] CORS-Fehler verhindern das Speichern von Produkten

Der Patch ACSD-49628 behebt das Problem, bei dem [!DNL Page Builder] CORS-Fehler verhindern, dass ein Administrator ein Produkt speichert. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.32 installiert ist. Die Patch-ID lautet ACSD-49628. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

[!DNL Page Builder] CORS-Fehler verhindern das Speichern eines Produkts.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich als Administrator an.
1. Erstellen Sie eine Benutzerrolle mit den folgenden Berechtigungen:

   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Products]**.
   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Categories]**.

1. Fügen Sie keine *[!UICONTROL Content]* -Berechtigungen hinzu.
1. Erstellen Sie einen weiteren Administrator-Benutzer und weisen Sie diesem die oben erstellten Rollen zu.
1. Erstellen Sie ein Produkt und melden Sie sich ab.
1. Melden Sie sich als zweiter Administrator an.
1. Versuchen Sie, das Produkt zu bearbeiten und zu speichern.

<u>Erwartete Ergebnisse</u>:

Der zweite Administrator kann das Produkt speichern, aber die Schaltfläche **[!UICONTROL Edit with Page Builder]** wird dem Administrator ohne *[!UICONTROL Content]* -Berechtigungen nicht angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Der zweite Administrator kann das Produkt aufgrund mehrerer [!DNL Page Builder] -Fehler nicht speichern.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
