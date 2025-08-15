---
title: 'ACSD-46618: Das Produktlisten-Widget zeigt falsche zwischengespeicherte Preise für angemeldete Kunden an'
description: Wenden Sie einen Patch an, um das Adobe Commerce-Problem zu beheben, bei dem das Produktlisten-Widget falsche zwischengespeicherte Preise für einen angemeldeten Kunden anzeigt.
feature: Cache, Orders, Products
role: Admin
exl-id: fa350f84-2fe5-474b-b4fd-d6c1e8bb0f95
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-46618: Das Produktlisten-Widget zeigt falsche zwischengespeicherte Preise für einen angemeldeten Kunden an

Der Patch ACSD-46618 löst das Problem, dass das Produktlisten-Widget falsche zwischengespeicherte Preise für einen angemeldeten Kunden anzeigt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html?lang=de) 1.1.21 installiert ist. Die Patch-ID ist ACSD-46618. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Patch ACSD-46618 löst das Problem, dass das Produktlisten-Widget falsche zwischengespeicherte Preise für einen angemeldeten Kunden anzeigt.

<u>Schritte zur Reproduktion</u>:

1. Wählen Sie in Adobe Commerce Admin **[!UICONTROL Stores]** und dann **[!UICONTROL Configuration]** aus, erweitern Sie **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Tax]** aus. Aktualisieren Sie die Steuereinstellungen, um Preise mit und ohne Steuern anzuzeigen.
1. **[!UICONTROL Enable Cross Border Trade]** = _Ja_.
1. Erstellen Sie eine Steuerregel, die nur für die USA gilt.
1. Fügen Sie der Startseite ein Widget hinzu, das mehr als ein Produkt enthält.
1. Erstellen Sie zwei Kunden mit einer US-Adresse und einer Nicht-US-Adresse.
1. Melden Sie sich mit dem US-Kunden über die Storefront an. Stellen Sie sicher, dass die Seite zwischengespeichert wird.
1. Beobachten Sie den im Widget „Startseite“ angezeigten Preis.
1. Melden Sie sich ab und melden Sie sich mit dem nicht amerikanischen Kunden an.

<u>Erwartete Ergebnisse</u>:

Der im Widget Startseite angezeigte Preis entspricht der Kundenadresse.

<u>Tatsächliche Ergebnisse</u>:

Das Widget „Startseite“ zeigt Preise anhand der Steuer für Nicht-US-Kunden an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
