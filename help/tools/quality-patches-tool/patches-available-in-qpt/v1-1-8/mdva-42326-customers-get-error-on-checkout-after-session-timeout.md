---
title: 'MDVA-42326: Kunden erhalten nach Sitzungs-Timeout einen Fehler beim Auschecken'
description: Der Patch MDVA-42326 löst das Problem, dass Kunden nach dem Sitzungs-Timeout einen Fehler beim Checkout erhalten, auch wenn der persistente Warenkorb aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-42326. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: Checkout, Orders
role: Admin
exl-id: f9ef6778-298b-4ff9-9c4b-b3f47bb04b67
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# MDVA-42326: Kunden erhalten nach Sitzungs-Timeout einen Fehler beim Auschecken

Der Patch MDVA-42326 löst das Problem, dass Kunden nach dem Sitzungs-Timeout einen Fehler beim Checkout erhalten, auch wenn der persistente Warenkorb aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-42326. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Kunden erhalten nach der Sitzungs-Zeitüberschreitung einen Fehler beim Auschecken, auch wenn der persistente Warenkorb aktiviert ist.

<u>Voraussetzungen</u>:

1. Gehen Sie zu **Konfiguration** > **Allgemein** > **Web** > **Standard-Cookie-Einstellungen** > **Cookie Lifetime** und setzen Sie auf **120**.
1. Gehen Sie zu **Konfiguration** > **Kunden** > **Kundenkonfiguration** > **Online-Kundenoptionen** und setzen Sie beide Werte auf **2**.
1. Wechseln Sie zu **Konfiguration** > **Kunden** > **Persistenter Warenkorb** und setzen Sie auf **Aktivieren**.
1. Gehen Sie zu **Konfiguration** > **Verkauf** > **Zahlungsmethoden** und deaktivieren Sie alle Zahlungsmethoden außer **Scheck/Zahlungsanweisung** (sie sollte aktiviert sein).

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich als Kunde an und fügen Sie einige Produkte zum Warenkorb hinzu.
1. Überprüfen Sie den Warenkorb.
1. Warten Sie zwei Minuten (in der Voraussetzung festgelegt). Die Sitzung sollte eine Zeitüberschreitung aufweisen.
1. Klicken Sie **Zum Auschecken gehen** und aktualisieren Sie die Seite nicht.
1. Checken Sie als Gast aus, geben Sie die Lieferadresse ein und wählen Sie eine Versandart.
1. Klicken Sie **Weiter**.
1. Klicken Sie auf **Seite &quot;** &amp; Zahlungen **auf „Bestellung**. Da nur eine Zahlungsmethode zulässig ist, sollte der Kunde die Bestellung aufgeben können, ohne die Zahlungsmethode auszuwählen.

<u>Erwartete Ergebnisse</u>:

Der Kunde sollte in der Lage sein, die Bestellung aufzugeben.

<u>Tatsächliche Ergebnisse</u>:

Der Kunde erhält die folgende Fehlermeldung: *Fehlgeschlagene Adressvalidierung: E-Mail hat ein falsches Format*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
