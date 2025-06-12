---
title: 'MDVA-41164: Firma mit benutzerdefinierten Kundenattributen kann nicht gespeichert oder bearbeitet werden'
description: Der Patch MDVA-41164 löst das Problem, dass der Administrator ein Unternehmen mit benutzerdefinierten Kundenattributen von Dateien oder Bildern beliebigen Typs nicht speichern oder bearbeiten kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41164. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
exl-id: 9d1792e0-ba7b-444b-b1b1-771fd0e328eb
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# MDVA-41164: Firma mit benutzerdefinierten Kundenattributen kann nicht gespeichert oder bearbeitet werden

Der Patch MDVA-41164 löst das Problem, dass der Administrator ein Unternehmen mit benutzerdefinierten Kundenattributen von Dateien oder Bildern beliebigen Typs nicht speichern oder bearbeiten kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41164. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein Administrator kann keine Firma mit benutzerdefinierten Kundenattributen von Dateien oder Bildern beliebigen Typs speichern oder bearbeiten.

<u>Voraussetzungen</u>:

B2B-Modul ist installiert.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie Firma in **Stores** > **config** > **B2B-Features**.
1. Erstellen Sie ein Kundenattribut unter **Stores** > **Attribute** > **Kunden** > **Neues Attribut hinzufügen**:
   * Eingabetyp: Datei (Anhang)
   * In Storefront anzeigen: Ja
   * Sortierreihenfolge: Beliebig
   * Forms zu verwenden in: Alle auswählen
1. Erstellen Sie unter **Kunden** > **Firmen** > **Neue Firma hinzufügen** eine Datei für das neue, oben erstellte Attribut.

<u>Erwartete Ergebnisse</u>:

Der Benutzer kann die Erstellung des Unternehmens abschließen, und die Anlage wird ohne Fehler hochgeladen.

<u>Tatsächliche Ergebnisse</u>:

* Sie erhalten eine Fehlermeldung: *Beim Speichern der Datei ist ein Fehler aufgetreten.*
* Ausnahmeprotokoll enthält einen Datensatz wie den folgenden:

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
  ```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
