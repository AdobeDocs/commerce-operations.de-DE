---
title: "ACSD-51379: Änderungen am Textinhalt der Seite über [!DNL Page Builder] werden nicht gespeichert."
description: Wenden Sie den Patch ACSD-51379 an, um das Adobe Commerce-Problem zu beheben, bei dem die über [!DNL Page Builder] vorgenommenen Änderungen am Textinhalt einer Seite nicht gespeichert werden.
feature: Page Builder, Page Content
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-51379: Änderungen am Textinhalt der Seite über [!DNL Page Builder] werden nicht gespeichert

Der Patch ACSD-51379 behebt das Problem, dass Änderungen, die über [!DNL Page Builder] am Textinhalt einer Seite vorgenommen wurden, nicht gespeichert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.32 installiert ist. Die Patch-ID ist ACSD-51379. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Änderungen, die über [!DNL Page Builder] am Textinhalt einer Seite vorgenommen wurden, werden nicht gespeichert.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Admin an.
1. Gehen Sie zu **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**.
1. Erstellen Sie auf der Registerkarte **[!UICONTROL Content]** eine Testseite mit einer Zeile und einem Textelement.
1. Speichern Sie die Seite und kehren Sie zur Registerkarte **[!UICONTROL Content]** zurück.
1. Bearbeiten Sie den Text, indem Sie ihn auswählen und ändern.

   **Hinweis:** Das Problem kann nur reproduziert werden, wenn der Text ausgewählt und geändert wird, ohne den Editor zu aktivieren.

1. Klicken Sie auf der Testseite auf die Schaltfläche **[!UICONTROL Save and Close]** .
1. Öffnen Sie die Testseite erneut und überprüfen Sie die Registerkarte **[!UICONTROL Content]** .

<u>Erwartete Ergebnisse</u>:

Der neue Text wird erfolgreich für ursprüngliche und duplizierte Textelemente gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Das Textelement wurde erfolgreich dupliziert, der neue Text wird jedoch nicht gespeichert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
