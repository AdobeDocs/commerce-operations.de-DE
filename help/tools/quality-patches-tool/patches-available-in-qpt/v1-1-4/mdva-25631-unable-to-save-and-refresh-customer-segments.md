---
title: 'MDVA-25631: Kundensegmente können nicht gespeichert und aktualisiert werden'
description: Mit dem Patch MDVA-25631 wird das Problem behoben, dass Benutzerinnen und Benutzer keine Kundensegmente speichern und aktualisieren können, die eine große Anzahl von Kundinnen und Kunden enthalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-25631. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
feature: Customer Service
role: Admin
exl-id: 3cf40538-822a-4d3e-b8fa-20f9ef9228ae
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%
---
# MDVA-25631: Kundensegmente können nicht gespeichert und aktualisiert werden

Mit dem Patch MDVA-25631 wird das Problem behoben, dass Benutzerinnen und Benutzer keine Kundensegmente speichern und aktualisieren können, die eine große Anzahl von Kundinnen und Kunden enthalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-25631. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3 - 2.3.5-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzende können keine Kundensegmente speichern und aktualisieren, die eine große Anzahl von Kunden enthalten.

<u>Voraussetzungen</u>:

Generieren Sie eine große Anzahl von Kunden (mehr als 3 Millionen).

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Kundensegment und versuchen Sie, es zu speichern.

<u>Erwartete Ergebnisse</u>:

Das Kundensegment wird ohne Fehler gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten *500*-Fehler, da die zulässige Speichergröße erschöpft ist.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
