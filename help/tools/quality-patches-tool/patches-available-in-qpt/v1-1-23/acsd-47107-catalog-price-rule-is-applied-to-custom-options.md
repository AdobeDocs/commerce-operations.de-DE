---
title: 'ACSD-47107: Katalogpreisregel wird auf benutzerdefinierte Optionen angewendet'
description: Wenden Sie den Patch ACSD-47107 an, um das Adobe Commerce-Problem zu beheben, bei dem die Katalogpreisregel auf benutzerdefinierte Optionen angewendet wird.
feature: Catalog Management, Orders, Price Rules
role: Developer
exl-id: 6fcf896b-ffa9-4cfb-926a-21659ac9f116
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-47107: Katalogpreisregel wird auf benutzerdefinierte Optionen angewendet

Der Patch ACSD-47107 behebt das Problem, dass die Katalogpreisregel auf benutzerdefinierte Optionen angewendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23 installiert ist. Die Patch-ID ist ACSD-47107. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.4-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Katalogpreisregel wird auf benutzerdefinierte Optionen angewendet.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Katalogpreisregel.
1. Setzen Sie ihn auf *Apply as a percentage of original price* und fügen Sie einen Rabatt von 10% hinzu.
1. Ein beliebiges Produkt auswählen.
1. Erstellen Sie einige benutzerdefinierte Optionen.
1. Überprüfen Sie den Preis am Frontend.

<u>Erwartete Ergebnisse</u>:

Die Katalogpreisregel wird nicht auf benutzerdefinierte Optionen angewendet, sondern nur auf den ursprünglichen Preis des Produkts.

<u>Tatsächliche Ergebnisse</u>:

Die Katalogpreisregel wird auf benutzerdefinierte Optionen angewendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
