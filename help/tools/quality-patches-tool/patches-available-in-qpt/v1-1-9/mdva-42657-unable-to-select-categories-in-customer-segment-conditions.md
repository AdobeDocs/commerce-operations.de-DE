---
title: 'MDVA-42657: In den Segmentbedingungen des Kunden können keine Kategorien ausgewählt werden.'
description: Der Patch MDVA-42657 löst das Problem, dass der Admin-Benutzer keine Kategorien in den Segmentbedingungen des Kunden auswählen kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-42657. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Categories, Console, Customer Service
role: Admin
exl-id: 115bad99-a603-4940-897e-034974ed1a6c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# MDVA-42657: In den Segmentbedingungen des Kunden können keine Kategorien ausgewählt werden.

Der Patch MDVA-42657 löst das Problem, dass der Admin-Benutzer keine Kategorien in den Segmentbedingungen des Kunden auswählen kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-42657. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Administrator bzw. die Administratorin kann in den Bedingungen des Kundensegments keine Kategorien auswählen.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie **Kunden** > **Segmente**.
1. Erstellen Sie ein neues Segment.
1. Navigieren Sie zum neu erstellten Segment und klicken Sie **der linken** auf „Bedingungen“.
1. Klicken Sie auf das grüne Pluszeichen.
1. Wählen Sie Produktverlauf unter Produkte aus.
1. Ändern Sie „Angezeigt“ in „Bestellt“.
1. Ändern Sie „ALLE“ in „BELIEBIG“.
1. Klicken Sie auf das verschachtelte grüne Pluszeichen und wählen Sie Kategorie aus.
1. Klicken Sie auf das Symbol **…** und dann auf das Auswahlsymbol (links neben dem Häkchen).
1. Öffnen Sie die Browser-Dev-Konsole.
1. Aktivieren Sie die Kontrollkästchen für beliebige/mehrere Kategorien und beachten Sie den in der Konsole ausgelösten JavaScript-Fehler.
1. Klicken Sie auf **Speichern**.
1. Navigieren Sie zurück zur Bedingung und überprüfen Sie, ob die ausgewählten Kategorien gespeichert wurden.

<u>Erwartete Ergebnisse</u>:

Die ausgewählten Kategorien werden gespeichert und beim Anzeigen/Bearbeiten der Segmentbedingungen ausgewählt.

<u>Tatsächliche Ergebnisse</u>:

Die ausgewählten Kategorien fehlen und wurden nicht ordnungsgemäß gespeichert. In der Konsole wird die folgende Fehlermeldung angezeigt:

```
category-checkbox-tree.js:249 Uncaught TypeError: Cannot set properties of undefined (setting 'value')
    at Ext.tree.TreePanel.Enhanced.<anonymous> (category-checkbox-tree.js:249)
    at Ext.util.Event.fire (ext-tree.js:29)
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch [!DNL Quality Patches Tool] Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
