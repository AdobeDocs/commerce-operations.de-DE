---
title: 'ACSD-56621: Aktualisierte Namen werden in der Kopfzeile der Grußformeln für den Administrator des Unternehmens nicht angezeigt'
description: Wenden Sie den Patch ACSD-56621 an, um das Adobe Commerce-Problem zu beheben, bei dem der aktualisierte Vor- und Nachname des Unternehmensadministratorbenutzers nicht im Abschnitt Grußkopfzeile angezeigt wird.
feature: Companies, B2B, User Account
role: Admin, Developer
exl-id: 739c1c8c-e079-4ad7-be97-7c60b0347e12
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-56621: Aktualisierte Namen werden in der Kopfzeile der Grußformeln für den Administrator des Unternehmens nicht angezeigt

Mit dem Patch ACSD-56621 wird das Problem behoben, dass der aktualisierte Vor- und Nachname des Admin-Benutzers des Unternehmens nicht im Abschnitt Grußkopfzeile angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.46 installiert ist. Die Patch-ID ist ACSD-56621. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die aktualisierten Namen werden für Benutzende, die Unternehmensadministratoren sind, nicht in der Kopfzeile „Grußformeln“ angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zum Bedienfeld **[!UICONTROL Admin]** .
1. Navigieren Sie zu **[!UICONTROL Stores]** und wählen Sie **[!UICONTROL Configuration]** aus.
1. Wählen Sie im Abschnitt **[!UICONTROL General]** die Option **[!UICONTROL B2B]** aus, um die B2B-Unternehmensfunktion zu aktivieren.
1. Gehen Sie zum **[!UICONTROL Storefront]** und registrieren Sie eine neue Firma.
1. Melden Sie sich als Admin-Benutzer des Unternehmens an.
1. Wechseln Sie zu **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** und ändern Sie die Felder Vor- und Nachname nach Bedarf.

<u>Erwartete Ergebnisse</u>:

Der Vor- und Nachname des Benutzers im Abschnitt Grußkopfzeile wird sofort geändert.

<u>Tatsächliche Ergebnisse</u>:

Der Vor- und Nachname des Benutzers wird nur geändert, wenn sich der Benutzer abmeldet und sich erneut anmeldet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
