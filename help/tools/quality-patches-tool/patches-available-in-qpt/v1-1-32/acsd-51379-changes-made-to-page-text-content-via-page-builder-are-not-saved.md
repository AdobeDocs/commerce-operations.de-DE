---
title: 'ACSD-51379: Änderungen am Textinhalt der Seite über  [!DNL Page Builder]  nicht gespeichert'
description: Wenden Sie den ACSD-51379-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die Änderungen am Textinhalt einer Seite über nicht  [!DNL Page Builder]  werden.
feature: Page Builder, Page Content
role: Admin
exl-id: 03fc2865-04b6-4330-b80c-8d694baa8c88
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-51379: Änderungen am Textinhalt der Seite über [!DNL Page Builder] werden nicht gespeichert

Mit dem Patch ACSD-51379 wird das Problem behoben, dass Änderungen, die über [!DNL Page Builder] am Textinhalt einer Seite vorgenommen werden, nicht gespeichert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.32 installiert ist. Die Patch-ID ist ACSD-51379. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Änderungen, die über [!DNL Page Builder] am Textinhalt einer Seite vorgenommen wurden, werden nicht gespeichert.

<u>Schritte zur Reproduktion</u>:

1. Bei Admin anmelden.
1. Navigieren Sie zu **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**.
1. Erstellen Sie eine Testseite mit einer Zeile und einem Textelement auf der Registerkarte **[!UICONTROL Content]** .
1. Speichern Sie die Seite und kehren Sie zur Registerkarte **[!UICONTROL Content]** zurück.
1. Bearbeiten Sie den Text, indem Sie ihn auswählen und ändern.

   **Hinweis:** Das Problem ist nur reproduzierbar, wenn der Text ausgewählt und geändert wird, ohne den Editor zu aktivieren.

1. Klicken Sie auf der Testseite auf die Schaltfläche **[!UICONTROL Save and Close]** .
1. Öffnen Sie die Testseite erneut und überprüfen Sie die Registerkarte **[!UICONTROL Content]** .

<u>Erwartete Ergebnisse</u>:

Der neue Text wird für die ursprünglichen und duplizierten Textelemente erfolgreich gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Das Textelement wurde erfolgreich dupliziert, der neue Text wird jedoch nicht gespeichert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
