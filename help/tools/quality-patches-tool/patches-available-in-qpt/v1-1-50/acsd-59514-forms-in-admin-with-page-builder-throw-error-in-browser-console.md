---
title: 'ACSD-59514: Forms in Admin mit  [!DNL Page Builder]  in der Browser-Konsole'
description: Wenden Sie den ACSD-59514-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem Formulare in Admin mit  [!DNL Page Builder] den Fehler "[!DNL Page Builder] wurde 5 Sekunden gerendert, ohne Sperren freizugeben“ auslösen. nach dem Absenden des Formulars in der Browser-Konsole und Änderungen können nicht gespeichert werden.
feature: Page Builder
role: Admin, Developer
exl-id: 3d1167d2-0a75-48ac-bc31-5bbd3c4a409e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-59514: Forms in Admin mit [!DNL Page Builder] Auslösefehler in der Browser-Konsole

Mit dem Patch ACSD-59514 wird das Problem behoben, dass die Formulare in Admin mit [!DNL Page Builder] den Fehler auslösten, den *[!DNL Page Builder]5 Sekunden lang gerendert hat, ohne Sperren freizugeben.nach dem Senden des Formulars in der Browser-Konsole* und Änderungen können nicht gespeichert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 installiert ist. Die Patch-ID ist ACSD-59514. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Forms in Admin mit [!DNL Page Builder] löste den Fehler aus, den *[!DNL Page Builder]5 Sekunden lang gerendert hat, ohne Sperren freizugeben.nach dem Senden des Formulars in der Browser-Konsole* und Änderungen können nicht gespeichert werden.

<u>Voraussetzungen</u>:

Adobe Commerce [!DNL Page Builder]-Module sind installiert und aktiviert.

<u>Schritte zur Reproduktion</u>:

1. Öffnen Sie das Admin-Bedienfeld und klicken Sie auf die Schaltfläche [!UICONTROL Content] .
1. Wählen Sie den Block aus und bearbeiten Sie den Block.
1. Ändern Sie den Inhalt und klicken Sie auf [!UICONTROL Save].
1. Öffnen Sie die Konsole und sehen Sie die Fehlermeldung.

<u>Erwartete Ergebnisse</u>:

Der Block wurde gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Der Lader hört nicht auf zu drehen, und der Block wird nicht gespeichert. Der folgende Fehler wird in der Browser-Konsole angezeigt:
*[!DNL Page Builder]wurde 5 Sekunden lang gerendert, ohne Sperren freizugeben.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
