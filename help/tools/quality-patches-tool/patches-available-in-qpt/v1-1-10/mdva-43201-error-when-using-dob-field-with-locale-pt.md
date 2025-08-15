---
title: 'MDVA-43201: Fehler bei Verwendung des DOB-Felds mit dem Gebietsschema PT'
description: Der Patch MDVA-43201 löst das Problem, dass ein Fehler auftritt, wenn das Attribut DOB customer im Kundenregistrierungsformular für das portugiesische Gebietsschema verwendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-43201. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: B2B, Cache
role: Admin
exl-id: be087420-1ee3-40cc-8ff7-62c5641609cc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-43201: Fehler bei Verwendung des DOB-Felds mit dem Gebietsschema PT

Der Patch MDVA-43201 löst das Problem, dass ein Fehler auftritt, wenn das Attribut DOB customer im Kundenregistrierungsformular für das portugiesische Gebietsschema verwendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-43201. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn das DOB-Kundenattribut zum Kundenregistrierungsformular für das portugiesische Gebietsschema hinzugefügt wird, gibt das Formular den Fehler *Argument 1, das an iterator_to_array() übergeben wird, muss eine durchsuchbare Schnittstelle implementieren, null angegeben*.

<u>Voraussetzungen</u>:

B2B-Module werden installiert.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu Admin **Stores** > **Configuration** > **General** > **Locale Options**, setzen Sie Locale auf **Portugiesisch (Portugal)** und klicken Sie auf **Speichern**.
1. Neuindizieren und Cache löschen.
1. Navigieren Sie **Stores** > **Attribut** > **Kunde**.
1. Öffnen Sie das DOB-Kundenattribut und setzen Sie **In Storefront anzeigen** auf **Ja**.
1. Wählen Sie alle aus **Formular zur Verwendung in**.
1. Speichern Sie das Attribut.
1. Navigieren Sie zur Seite Neues Konto erstellen im Frontend.

<u>Erwartete Ergebnisse</u>:

Das Formular zur Kundenregistrierung für den portugiesischen Store gibt beim Hinzufügen des Attributs „dob“ keinen Fehler zurück.

<u>Tatsächliche Ergebnisse</u>:

Das Formular zur Kundenregistrierung für den portugiesischen Store gibt beim Hinzufügen des Attributs „dob“ einen Fehler zurück.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch [!DNL Quality Patches Tool] Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
