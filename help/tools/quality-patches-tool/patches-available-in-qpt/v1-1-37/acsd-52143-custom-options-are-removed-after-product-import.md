---
title: 'ACSD-52143: Benutzerdefinierte Optionen werden nach dem Produktimport entfernt'
description: Wenden Sie den Patch ACSD-52143 an, um das Adobe Commerce-Problem zu beheben, bei dem die Anpassungsoptionen nach dem Produktimport entfernt werden.
feature: Data Import/Export
role: Admin, Developer
exl-id: 630fffa7-012c-4539-9745-9a34571bd2eb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-52143: Benutzerdefinierte Optionen werden nach dem Produktimport entfernt

Mit dem Patch ACSD-52143 wird das Problem behoben, dass die benutzerdefinierten Optionen nach dem Produktimport entfernt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.37 installiert ist. Die Patch-ID ist ACSD-52143. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die benutzerdefinierten Optionen werden nach dem Produktimport entfernt.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu **[!UICONTROL Store]** > **[!UICONTROL All Stores]** und richten Sie eine Multi-Store-Instanz ein (eine Website mit zwei Store-Ansichten).
1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und erstellen Sie zwei Produkte mit [!UICONTROL Customizable Options].
1. Fügen Sie in jedem Produkt eine [!UICONTROL Customizable Option] hinzu.
1. Wechseln Sie zur zweiten Shop-Ansicht und ändern Sie den Produktnamen für jedes Produkt.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** und exportieren Sie die beiden von Ihnen erstellten Produkte.
1. CSV-Datei herunterladen.
1. Wechseln Sie zu **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** und importieren Sie die Datei erneut.
1. Überprüfen Sie beide Produkte.

<u>Erwartete Ergebnisse</u>:

Die benutzerdefinierten Optionen werden nach dem Produktimport nicht entfernt.

<u>Tatsächliche Ergebnisse</u>:

Die Zolloptionen werden nach dem Produktimport entfernt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
