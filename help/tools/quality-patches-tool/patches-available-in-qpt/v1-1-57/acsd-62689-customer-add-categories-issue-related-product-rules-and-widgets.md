---
title: 'ACSD-62689: Kategorien können in [!UICONTROL Related Product Rules] und Widgets nach Tiefe 4 nicht mehr hinzugefügt werden'
description: Wenden Sie den Patch ACSD-62689 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Kunde nach der vierten Verschachtelung keine Kategorien in [!UICONTROL Related Product Rules] und Widgets hinzufügen kann.
feature: Categories
role: Admin, Developer
exl-id: 2506744a-01c8-462b-9a27-cd0bdb5664f9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-62689: Kategorien können in *[!UICONTROL Related Product Rules]* und Widgets nach Tiefe 4 nicht mehr hinzugefügt werden

>[!NOTE]
>
>Dieser Patch wurde durch [ACP2E-3689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3689-issues-with-category-tree-display-reflect-anchor-non-anchor-relationships.md) ersetzt.

Mit dem Patch ACSD-62689 wird das Problem behoben, dass ein Kunde nach der Verschachtelung der Tiefe vier keine Kategorien in *[!UICONTROL Related Product Rules]* und Widgets hinzufügen kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 installiert ist. Die Patch-ID ist ACSD-62689. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Eine Kundin oder ein Kunde kann nach der Verschachtelung mit Tiefe vier keine Kategorien mehr in *[!UICONTROL Related Product Rules]* und Widgets hinzufügen.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Kategorien mit den Namen *[!UICONTROL Anchor]* und *[!UICONTROL Non-Anchor]* unter der standardmäßigen Stammkategorie.
   * Stellen Sie sicher, dass das *[!UICONTROL Is Anchor]*-Flag für die *[!UICONTROL Non-Anchor]* deaktiviert ist.
1. Gehen Sie zu **[!UICONTROL Content]** > **[!UICONTROL Widgets]** und erstellen Sie ein Widget.
1. Wählen Sie unter *[!UICONTROL Layout Updates]* im Feld **[!UICONTROL Non-Anchor Categories]** die Option *[!UICONTROL Display on]* aus.
1. Klicken Sie auf **[!UICONTROL Specific Categories]**.
1. Klicken Sie auf das Symbol für die Kategorieauswahl.
1. Erweitern Sie die Stammkategorie .
1. Überprüfen Sie die Kategorien. Beide sollten deaktiviert und nicht auswählbar sein.
1. Wählen Sie unter *[!UICONTROL Layout Updates]* im Feld **[!UICONTROL Anchor Categories]** die Option *[!UICONTROL Display on]* aus. Führen Sie dann die Schritte 5 und 6 aus.
1. Überprüfen Sie die Kategorien. Beide sollten aktiviert und auswählbar sein.

<u>Erwartete Ergebnisse</u>:

In Schritt 7 sollte nur die Kategorie &quot;*[!UICONTROL Non-Anchor]*&quot; auswählbar sein. In Schritt 9 sollte die *[!UICONTROL Anchor]* auswählbar sein.

<u>Tatsächliche Ergebnisse</u>:

In Schritt 7 können beide Kategorien nicht ausgewählt werden. In Schritt 9 können beide Kategorien ausgewählt werden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.

