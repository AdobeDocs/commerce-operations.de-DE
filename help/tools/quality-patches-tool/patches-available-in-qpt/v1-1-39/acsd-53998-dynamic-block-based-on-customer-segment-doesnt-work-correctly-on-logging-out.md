---
title: 'ACSD-53998: Dynamischer Block basierend auf Kundensegment funktioniert nach der Abmeldung nicht korrekt'
description: Wenden Sie den ACSD-53998 Patch an, um das Adobe Commerce-Problem zu beheben, dass ein dynamischer Block, der auf einem Kundensegment basiert, nach der Abmeldung von einem Kundenkonto nicht ordnungsgemäß funktioniert.
feature: Customers, Page Builder, Personalization
role: Admin, Developer
exl-id: aa7001c7-bb35-4e5c-8ac9-3ed84b75d7cd
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
subfeature_v2:
  - id: ed510963-0b8c-4764-86f6-f3c7735bc334
    internal-label: Page Builder
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%
---
# ACSD-53998: Dynamischer Block basierend auf Kundensegment funktioniert nach der Abmeldung nicht korrekt

Mit dem Patch ACSD-53998 wird das Problem behoben, dass ein dynamischer Block, der auf einem Kundensegment basiert, nach der Abmeldung von einem Kundenkonto nicht korrekt funktioniert. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.39 installiert ist. Die Patch-ID ist ACSD-53998. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2 - 2.4.4-p6, 2.4.5-p1 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein dynamischer Block, der auf einem Kundensegment basiert, funktioniert nach der Abmeldung von einem Kundenkonto nicht ordnungsgemäß.

<u>Voraussetzungen</u>:

Installieren und Aktivieren von [!DNL Page Builder].

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Kundensegmente ohne Bedingungen.
1. Erstellen Sie zwei dynamische Blöcke für jedes Segment.
1. Erstellen Sie einen -Block mit den beiden dynamischen Blöcken [!DNL Page Builder] dynamischen Blöcken.
1. Erstellen Sie ein Widget mit dem oben genannten Block und machen Sie den Block unter dem Fußzeilenabschnitt aller Seiten sichtbar.
1. Löschen Sie die Caches.
1. Öffnen Sie die -Startseite.
1. Melden Sie sich als Kunde an.
1. Abmelden.

<u>Erwartete Ergebnisse</u>:

Das für angemeldete Kunden erstellte Banner wird nicht für Gastbenutzer angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Das für das angemeldete Kundensegment erstellte Banner wird auch nach dem Abmelden vom Kundenkonto angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
