---
title: 'ACSD-54026: Falsche Fehlermeldung für updateCompanyRole-GraphQL-Anfrage'
description: Wenden Sie den Patch ACSD-54026 an, um das Adobe Commerce-Problem zu beheben, bei dem eine falsche Fehlermeldung für eine GraphQL-Anfrage „updateCompanyRole“ für einen nicht autorisierten Benutzer vorhanden ist.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 21695333-5f18-48db-acde-246f269dd691
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e439352c-5b67-587d-b34e-d2a0aa5a0242
    internal-label: Roles/Permissions
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
source-wordcount: '380'
ht-degree: 0%
---
# ACSD-54026: Falsche Fehlermeldung für `updateCompanyRole` GraphQL-Anfrage

Mit dem Patch ACSD-54026 wird das Problem behoben, dass eine falsche Fehlermeldung für eine `updateCompanyRole` GraphQL-Anfrage für einen nicht autorisierten Benutzer vorhanden ist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.39 installiert ist. Die Patch-ID ist ACSD-54026. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Es wird eine falsche Fehlermeldung für eine `updateCompanyRole` GraphQL-Anfrage für einen nicht autorisierten Benutzer erhalten.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie B2B-Unternehmen in der Konfiguration.
1. Erstellen Sie eine Firma.
1. Senden Sie eine `updateCompanyRole` GraphQL-Anfrage, ohne ein Bearer-Token oder ein ungültiges Bearer-Token zu übergeben.
1. Beachten Sie die Fehlermeldung in der GraphQL-Antwort.

<u>Erwartete Ergebnisse</u>:

Sie erhalten die folgende Fehlermeldung: *Der aktuelle Kunde ist nicht autorisiert.*

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten die folgende Fehlermeldung: *Kunde ist kein Firmenbenutzer.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
