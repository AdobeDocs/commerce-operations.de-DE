---
title: 'ACP2E-3753: Bestands-E-Mails, die keine Store-spezifischen Design-Vorlagen im Multi-Store-Setup verwenden'
description: Wenden Sie den ACP2E-3753-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem Warnungs-E-Mails in einer Multi-Store-Einrichtung immer mit dem Standard-Design gesendet werden, unabhängig von der Store- oder Design-Konfiguration.
feature: Themes, Personalization
role: Admin, Developer
exl-id: ad44ffdd-f122-4119-83e3-1816951b662c
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8b440f30-6794-5ed6-981f-391de4e9b0cc
    internal-label: Themes
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
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
source-wordcount: '406'
ht-degree: 0%
---
# ACP2E-3753: Bestands-E-Mails, die keine Store-spezifischen Design-Vorlagen im Multi-Store-Setup verwenden

Mit dem Patch ACP2E-3753 wird das Problem behoben, dass E-Mails zu Produktwarnungen in einer Multi-Store-Einrichtung immer mit dem Standarddesign gesendet wurden, unabhängig von der Store- oder Design-Konfiguration. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 installiert ist. Die Patch-ID lautet ACP2E-3753. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p11

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

E-Mails zu Produktwarnungen in einer Multi-Store-Einrichtung werden immer mit dem Standarddesign gesendet, unabhängig von der Store- oder Design-Konfiguration.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Websites, Stores und Store-Ansichten.
1. Erstellen Sie zwei separate Designs und weisen Sie diese verschiedenen Stores zu.
1. Die Einstellung „Warnhinweis für Produkte“ ist der Standardbereich, der jede Minute ausgeführt wird.
1. Überschreiben/Hinzufügen von Inhalt zur `stock.phtml` für beide Designs. Beispiel für den Dateispeicherort:

   ```text
   app\design\frontend\Adobe\Taiwan\Magento_ProductAlert\templates\email\stock.phtml
   app\design\frontend\Adobe\Japan\Magento_ProductAlert\templates\email\stock.phtml
   ```

1. Erstellen Sie für jeden Shop einen Benutzer und abonnieren Sie den Warnhinweis zum Produktbestand.
1. Trigger des Warnhinweises für den Produktbestand, um die E-Mails zu senden.

<u>Erwartete Ergebnisse</u>:

Die E-Mail sollte die Änderungen auf Design-Ebene enthalten.

<u>Tatsächliche Ergebnisse</u>:

Die E-Mails enthalten nicht die Vorlagen, die in der jeweiligen Website/im jeweiligen Store festgelegt wurden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
