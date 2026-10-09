---
title: 'MDVA-37725: E-Mails, die über nicht standardmäßige Sites gesendet werden, enthalten die Logo-URLs der Standard-Site'
description: Der Patch MDVA-37725 behebt das Problem, dass E-Mails mit asynchroner Reihenfolge über nicht standardmäßige Websites gesendet werden, die Logo-URLs von der Standard-Website enthalten.
feature: Communications, Orders
role: Admin
exl-id: 6e72897c-7652-4b5a-8575-090e94188daf
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%
---
# MDVA-37725: E-Mails, die über nicht standardmäßige Sites gesendet werden, enthalten die Logo-URLs der Standard-Site

>[!WARNING]
>
> Der Patch für MDVA-37725 ist veraltet.

Der Patch MDVA-37725 behebt das Problem, dass E-Mails mit asynchroner Reihenfolge über nicht standardmäßige Websites gesendet werden, die Logo-URLs von der Standard-Website enthalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-37725. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

E-Mails in asynchroner Reihenfolge werden über nicht standardmäßige Websites gesendet, die die Logo-URLs der Standard-Website enthalten.

<u>Voraussetzungen</u>:

1. Die zweite Website/Store/Store-Ansicht muss erstellt worden sein.
1. **Asynchrones Senden** Die Konfiguration muss unter **Stores** > **Einstellungen** > **Konfiguration** > **Verkauf** > **Verkaufs-E-Mail** > **Allgemeine Einstellungen** aktiviert sein.
1. **Store-Code zu URLs hinzufügen** wird die Konfiguration aktiviert, um den Zugriff auf die sekundäre Website unter **Stores** > **Einstellungen** > **Konfiguration** > **URL-Optionen** zu erleichtern.

<u>Schritte zur Reproduktion</u>:

1. Bestellungen aus dem ersten und zweiten Geschäft aufgeben.
1. Führen Sie cron aus, um die Verkaufs-E-Mails zu senden.
1. Überprüfen Sie die E-Mail von der zweiten Website.

<u>Erwartete Ergebnisse</u>:

Die Logo-URL der E-Mail enthält die URL der zweiten Website.

<u>Tatsächliche Ergebnisse</u>:

Die Logo-URL der E-Mail enthält die URL der Standard-Website.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
