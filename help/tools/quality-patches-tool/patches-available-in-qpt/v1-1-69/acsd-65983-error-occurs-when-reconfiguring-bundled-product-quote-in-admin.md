---
title: 'ACSD-65983: Fehler tritt auf, wenn das gebündelte Produktangebot in Admin neu konfiguriert wird'
description: Wenden Sie den Patch ACSD-65983 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Versuch, ein Bundle-Produkt im Bildschirm [!UICONTROL Sales] > [!UICONTROL Quotes] > [!UICONTROL Edit] im Backend zu konfigurieren, ein Fehler auftritt.
feature: B2B, Quotes
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8a8f2b273bcbcf135677ad7ca289398bf660e02e
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---


# ACSD-65983: Fehler tritt auf, wenn das gebündelte Produktangebot in Admin neu konfiguriert wird

Der Patch ACSD-65983 behebt das Problem, dass die Neukonfiguration eines gebündelten Produktangebots im Admin-Backend einen Fehler zurückgibt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 installiert ist. Die Patch-ID ist ACSD-65983. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Neukonfiguration eines gebündelten Produktangebots im Admin-Backend gibt einen Fehler zurück.

<u>Schritte zur Reproduktion</u>:

1. Wechseln Sie zum Admin-Bedienfeld und aktivieren Sie die **[!UICONTROL B2B Feature]**: **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Feature]**.
1. Erstellen Sie ein Bundle-Produkt mit festem Betrag (z. B.: *$10*) und fügen Sie drei oder mehr einfache Produkte mit *0* Betrag, *2* in **Option 1** und *Sonstige* in **Option 2** hinzu.
1. Erstellen Sie ein Unternehmenskonto aus dem Frontend.
1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** und weisen Sie das erstellte Unternehmen und die erstellten Produkte dem neuen/benutzerdefinierten freigegebenen Katalog zu.
1. Melden Sie sich als **Unternehmensbenutzer“** Frontend an und fügen Sie dem Warenkorb ein einfaches Produkt aus dem -Bundle hinzu.
1. Öffnen Sie die Warenkorbseite und senden Sie sie als **Angebot anfordern**.
1. Rufen Sie das Backend auf und bearbeiten Sie das erstellte Angebot.
1. Klicken **Abschnitt &quot;**&quot; auf die Schaltfläche **Konfigurieren**.
1. Wählen Sie ein anderes einfaches Produkt aus der **Option 2**.
1. Klicken Sie nun auf **OK** und sehen Sie die Fehlermeldung.

<u>Erwartete Ergebnisse</u>:

Sie können die angeforderten Angebotselemente erfolgreich vom Administrator konfigurieren, ohne dass eine Fehlermeldung angezeigt wird.

<u>Tatsächliche Ergebnisse</u>:

Die folgende Fehlermeldung wird angezeigt:

*Ein technisches Problem mit dem Server hat einen Fehler verursacht. Versuchen Sie erneut, mit Ihrer Arbeit fortzufahren. Wenn das Problem weiterhin besteht, versuchen Sie es später erneut.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > ](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch
