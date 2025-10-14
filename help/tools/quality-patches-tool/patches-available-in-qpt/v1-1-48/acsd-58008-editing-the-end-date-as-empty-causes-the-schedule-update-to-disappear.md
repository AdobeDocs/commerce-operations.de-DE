---
title: 'ACSD-58008: Durch Bearbeitung des Enddatums als *leer* verschwindet die Zeitplanaktualisierung'
description: Wenden Sie den Patch ACSD-58008 an, um das Adobe Commerce-Problem zu beheben, bei dem das Bearbeiten des Enddatums als *leer* dazu führt, dass die Zeitplanaktualisierung ausgeblendet wird.
feature: Staging, Page Content
role: Admin, Developer
exl-id: 6d2279e5-6580-4325-b0a8-ed62a95da3c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-58008: Wird das Enddatum als *leer“*, wird die Zeitplanaktualisierung ausgeblendet

Der Patch ACSD-58008 behebt das Problem, dass durch die Bearbeitung des Enddatums als *leer* die Zeitplanaktualisierung ausgeblendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48 installiert ist. Die Patch-ID ist ACSD-58008. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wird das Enddatum als *leer* bearbeitet, wird die Zeitplanaktualisierung ausgeblendet

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich als [!UICONTROL Admin] an.
1. Gehen Sie zu **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** und erstellen Sie eine Seite.
1. Wählen Sie die erstellte Seite aus und klicken Sie auf **[!UICONTROL Schedule New Update]**. *(Navigieren Sie dazu in der oberen rechten Ecke der Seite)*.
1. Erstellen Sie vier Aktualisierungen. *(z. B. als Inkrement von* 2 *Minuten)*.
1. Aktualisieren Sie *Update 2* und ändern Sie die Zeit in eine Zeit, die vor der letzten *Update 4* liegt.
1. Speichert die vorgenommenen Aktualisierungen.

<u>Erwartete Ergebnisse</u>:

Die Zeitplanaktualisierung zeigt die *Aktualisierung 3*.

<u>Tatsächliche Ergebnisse</u>:

Die Zeitplanaktualisierung zeigt nicht die *Aktualisierung 3*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
