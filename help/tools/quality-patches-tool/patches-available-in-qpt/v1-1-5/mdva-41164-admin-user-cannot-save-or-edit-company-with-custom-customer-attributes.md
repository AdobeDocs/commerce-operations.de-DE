---
title: 'MDVA-41164: Firma mit benutzerdefinierten Kundenattributen kann nicht gespeichert oder bearbeitet werden'
description: Der Patch MDVA-41164 löst das Problem, dass der Administrator ein Unternehmen mit benutzerdefinierten Kundenattributen von Dateien oder Bildern beliebigen Typs nicht speichern oder bearbeiten kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41164. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
exl-id: 9d1792e0-ba7b-444b-b1b1-771fd0e328eb
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%
---
# MDVA-41164: Firma mit benutzerdefinierten Kundenattributen kann nicht gespeichert oder bearbeitet werden

Der Patch MDVA-41164 löst das Problem, dass der Administrator ein Unternehmen mit benutzerdefinierten Kundenattributen von Dateien oder Bildern beliebigen Typs nicht speichern oder bearbeiten kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41164. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

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
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
