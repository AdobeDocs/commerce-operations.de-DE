---
title: "MDVA-42326: Kunden erhalten beim Checkout nach Sitzungs-Timeout einen Fehler."
description: Der Patch MDVA-42326 behebt das Problem, dass Kunden nach dem Sitzungs-Timeout beim Checkout einen Fehler beim Checkout erhalten, selbst wenn der beständige Warenkorb aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-42326. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
feature: Checkout, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# MDVA-42326: Kunden erhalten beim Checkout nach Sitzungs-Timeout einen Fehler

Der Patch MDVA-42326 behebt das Problem, dass Kunden nach dem Sitzungs-Timeout beim Checkout einen Fehler beim Checkout erhalten, selbst wenn der beständige Warenkorb aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-42326. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Kunden erhalten nach dem Sitzungs-Timeout beim Checkout einen Fehler, selbst wenn der beständige Warenkorb aktiviert ist.

<u>Voraussetzungen</u>:

1. Wechseln Sie zu **Konfiguration** > **Allgemein** > **Web** > **Standard-Cookie-Einstellungen** > **Cookie-Lebensdauer** und legen Sie den Wert auf **120** fest.
1. Wechseln Sie zu **Konfiguration** > **Kunden** > **Kundenkonfiguration** > **Online-Kundenoptionen** und legen Sie beide Werte auf **2** fest.
1. Wechseln Sie zu **Konfiguration** > **Kunden** > **Warenkorb für beständige Käufe** und legen Sie **Aktivieren** fest.
1. Wechseln Sie zu **Konfiguration** > **Verkauf** > **Zahlungsmethoden** und deaktivieren Sie alle Zahlungsmethoden mit Ausnahme von **Bestellung prüfen/bestellen** (es sollte aktiviert sein).

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich als Kunde an und fügen Sie einige Produkte zum Warenkorb hinzu.
1. Überprüfen Sie den Warenkorb.
1. Warten Sie zwei Minuten (in Vorbedingung gesetzt); die Sitzung sollte mit einem Timeout beendet werden.
1. Klicken Sie auf **Zum Checkout wechseln** und aktualisieren Sie die Seite nicht.
1. Checkout als Gast, füllen Sie die Lieferadresse aus und wählen Sie eine Versandmethode.
1. Klicken Sie auf **Weiter**.
1. Klicken Sie auf der Seite **Überprüfen und Zahlungen** auf **Bestellung platzieren**. Da nur eine Zahlungsmethode zulässig ist, sollte der Kunde die Bestellung aufgeben können, ohne die Zahlungsmethode auszuwählen.

<u>Erwartete Ergebnisse</u>:

Der Kunde sollte die Bestellung aufgeben können.

<u>Tatsächliche Ergebnisse</u>:

Der Kunde erhält den folgenden Fehler: *Validierung der fehlgeschlagenen Adresse: E-Mail hat ein falsches Format*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
