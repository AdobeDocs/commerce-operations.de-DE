---
title: "ACSD-46618: Produktlisten-Widget zeigt falsche zwischengespeicherte Preise für angemeldete Kunden an"
description: Wenden Sie einen Patch an, um das Adobe Commerce-Problem zu beheben, bei dem das Produktlisten-Widget falsche Preise im Cache für einen angemeldeten Kunden anzeigt.
feature: Cache, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-46618: Das Widget &quot;Produktliste&quot;zeigt falsche Preise im Cache für einen angemeldeten Kunden an

Der Patch ACSD-46618 behebt das Problem, dass das Produktlisten-Widget falsche Preise im Cache für einen angemeldeten Kunden anzeigt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html) 1.1.21 installiert ist. Die Patch-ID ist ACSD-46618. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Patch ACSD-46618 behebt das Problem, dass das Produktlisten-Widget falsche Preise im Cache für einen angemeldeten Kunden anzeigt.

<u>Zu reproduzierende Schritte</u>:

1. Wählen Sie im Adobe Commerce-Admin **[!UICONTROL Stores]**, dann **[!UICONTROL Configuration]**, erweitern Sie **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Tax]** aus. Aktualisieren Sie die Steuereinstellungen, um die Preise einschließlich und ohne Steuern anzuzeigen.
1. Legen Sie **[!UICONTROL Enable Cross Border Trade]** = _Ja_ fest.
1. Erstellen Sie eine Steuerregel, die nur für die USA gilt.
1. Fügen Sie der Startseite ein Widget hinzu, das mehr als ein Produkt umfasst.
1. Erstellen Sie zwei Kunden mit einer US-Adresse und einer Nicht-US-Adresse.
1. Melden Sie sich mit dem US-Kunden über die Storefront an. Stellen Sie sicher, dass die Seite zwischengespeichert ist.
1. Beachten Sie den im Widget zur Startseite angezeigten Preis.
1. Melden Sie sich mit dem Nicht-US-Kunden ab und melden Sie sich an.

<u>Erwartete Ergebnisse</u>:

Der im Widget der Startseite angezeigte Preis entspricht der Kundenadresse.

<u>Tatsächliche Ergebnisse</u>:

Das Startseiten-Widget zeigt Preise an, die die Steuer für Nicht-US-Kunden verwenden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
