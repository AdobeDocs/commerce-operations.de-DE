---
title: 'MDVA-42645: Der Administrator kann keine Prämienpunkte für Gutschriften für ein deaktiviertes Geschäft zurückerstatten'
description: Der MDVA-42645 Patch löst das Problem, dass der Administrator Prämienpunkte nicht zurückerstatten kann, wenn die Funktion „Gutschrift speichern“ deaktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42645. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
exl-id: 8053fcc7-d30c-424a-9494-df6e8630b095
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-42645: Der Administrator kann keine Prämienpunkte für Gutschriften für ein deaktiviertes Geschäft zurückerstatten

Der MDVA-42645 Patch löst das Problem, dass der Administrator Prämienpunkte nicht zurückerstatten kann, wenn die Funktion „Gutschrift speichern“ deaktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42645. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Administrator kann Prämienpunkte nicht zurückerstatten, wenn die Funktion „Gutschrift speichern“ deaktiviert ist.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Erstellen Sie ein neues Kundenkonto und fügen Sie einige Prämienpunkte hinzu.
1. Deaktivieren Sie die Funktion „Gutschrift speichern“, indem Sie **Store** > Einstellungen > **Konfiguration** > **Kunde** > **Kundenkonfiguration** > **Gutschriftsoptionen speichern**.
1. Melden Sie sich als Kunde an, dem die Prämienpunkte zugewiesen werden.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und navigieren Sie zur Kasse.
1. Verwenden Sie die Belohnungspunkte im Zahlungsbereich und geben Sie die Bestellung auf.
1. Öffnen Sie die Bestellung im Administrator und fakturieren Sie die Bestellung.
1. Klicken Sie auf den **Gutschrift**, um eine neue Gutschrift zu erstellen.
1. Markieren Sie unten die Option Rewards Reward Points und klicken Sie auf **Refund Offline**.

<u>Erwartete Ergebnisse</u>:

* Die Gutschrift wurde erfolgreich erstellt.
* Die Prämienpunkte werden erfolgreich zurückerstattet.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten die folgende Fehlermeldung: *Sie können nicht mehr Warenkorb-Guthaben als den Bestellbetrag verwenden.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
