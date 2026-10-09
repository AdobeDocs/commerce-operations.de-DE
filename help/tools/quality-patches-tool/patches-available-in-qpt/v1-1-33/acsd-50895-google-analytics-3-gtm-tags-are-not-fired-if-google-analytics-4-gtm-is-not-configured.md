---
title: 'ACSD-50895: [!DNL Google Analytics] 3 GTM-Tags werden nicht ausgelöst, wenn [!DNL Google Analytics] 4 GTM nicht konfiguriert ist'
description: Wenden Sie den Patch ACSD-50895 an, um das Adobe Commerce-Problem zu beheben, bei dem [!DNL Google Analytics] 3 GTM-Tags nicht ausgelöst werden, wenn [!DNL Google Analytics] 4 GTM nicht konfiguriert ist.
role: Admin
exl-id: 871e2ca1-dc10-435c-9325-62f5b9b673ad
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%
---
# ACSD-50895: [!DNL Google Analytics] 3 GTM-Tags werden nicht ausgelöst, wenn [!DNL Google Analytics] 4 GTM nicht konfiguriert ist

Der Patch ACSD-50895 behebt das Problem, dass [!DNL Google Analytics] 3 GTM-Tags nicht ausgelöst werden, wenn [!DNL Google Analytics] 4 GTM nicht konfiguriert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.33 installiert ist. Die Patch-ID ist ACSD-50895. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!DNL Google Analytics] 3 GTM-Tags werden nicht ausgelöst, wenn [!DNL Google Analytics] 4 GTM nicht konfiguriert ist.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich als Administrator an.
1. Aktivieren Sie **[!DNL Google Analytics 3]** und **[!DNL Google Tag Manager]** in **Admin** > **Store** > **Configuration** > **Sales** > **Google API** > **Google Analytics**.
1. **[!DNL Google Analytics 4]** und **[!DNL Google Tag Manager]** nicht aktivieren.
1. Öffnen Sie die Produktseite in der Storefront.

<u>Erwartete Ergebnisse</u>:

Die GTM-Tags werden ausgelöst, wenn nur **[!DNL Google Analytics]** 3 GTM aktiviert ist.

<u>Tatsächliche Ergebnisse</u>:

Die GTM-Tags werden nicht ausgelöst, wenn **[!DNL Google Analytics]** 4 GTM deaktiviert ist.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
