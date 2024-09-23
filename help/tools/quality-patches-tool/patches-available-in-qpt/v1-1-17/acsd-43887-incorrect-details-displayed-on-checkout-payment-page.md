---
title: "ACSD-43887: Falsche Details auf der Zahlungsseite für den Checkout angezeigt"
description: Der Patch ACSD-43887 behebt das Problem, dass falsche Details auf der Zahlungsseite für den Kassengang angezeigt werden, wenn die Option Bestellung für Unternehmen aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 installiert ist. Die Patch-ID lautet ACSD-43887. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# ACSD-43887: Falsche Details auf der Zahlungsseite für den Checkout angezeigt

Der Patch ACSD-43887 behebt das Problem, dass falsche Details auf der Zahlungsseite für den Kassengang angezeigt werden, wenn die Option Bestellung für Unternehmen aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 installiert ist. Die Patch-ID lautet ACSD-43887. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Falsche Details werden auf der Zahlungsseite angezeigt, wenn die Option Bestellungen für Unternehmen kaufen aktiviert ist.

<u>Voraussetzungen</u>:

1. B2B-Module sind installiert.
1. &quot;Unternehmen aktivieren&quot;ist auf _Ja_ eingestellt. Wechseln Sie zu **Stores** > **Konfigurationen** > **Allgemein** > **B2B-Funktionen** > **Unternehmen aktivieren** > **Ja**.
1. &quot;Kaufaufträge aktivieren&quot;ist auf _Ja_ eingestellt. Gehen Sie zu **Konfiguration der Bestellbestätigung** > **Bestellungen aktivieren** > **Ja**.
1. PayPal Express wird als Zahlungsmethode konfiguriert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen eines virtuellen Produkts.
1. Registrieren Sie ein Unternehmenskonto über das Frontend bei einem Unternehmensadministrator.
1. Genehmigen Sie das Unternehmenskonto vom Backend und setzen Sie **Bestellungen aktivieren** bei der Genehmigung des Unternehmens auf _Ja_ .
1. Gehen Sie zum Frontend und melden Sie sich mit dem in Schritt 2 erstellten Unternehmensadministratorkonto an.
1. Erstellen Sie einen &quot;Standardbenutzer&quot;für das Unternehmen. Navigieren Sie zu **Firmenbenutzer** > **Neuen Benutzer hinzufügen**.
1. Erstellen Sie eine &quot;Validierungsregel&quot;für das Unternehmen. Navigieren Sie zu **Validierungsregeln** > **Neue Regel hinzufügen**.

   * Regeltyp: Bestellsumme
   * Bestellsumme: ist größer als oder gleich 1 USD
   * Genehmigung erforderlich von: Unternehmensadministrator

1. Melden Sie sich mit dem Konto &quot;Standardbenutzer&quot;ab und melden Sie sich an.
1. Fügen Sie das in Schritt 1 erstellte virtuelle Produkt zum Warenkorb hinzu und fahren Sie mit dem Checkout fort.
1. Wählen Sie PayPal Express als Zahlungsmethode aus und klicken Sie auf **Bestellung aufgeben**.
1. Melden Sie sich mit dem Unternehmensadministratorkonto ab und an.
1. Wechseln Sie zu **Meine Kaufaufträge** und klicken Sie in **Bestellung des Unternehmens** auf **Anzeigen** für die in Schritt 9 erstellte Bestellung.
1. Validieren Sie die Bestellung. Der Bestellstatus sollte &quot;Genehmigt: Ausstehende Zahlung&quot;lauten.
1. Melden Sie sich mit dem Konto &quot;Standardbenutzer&quot; ab und melden Sie sich an.
1. Wechseln Sie zu **Meine Kaufaufträge** > **Ansicht** > **Bestellung aufgeben**.
1. Überprüfen Sie die **Bestellzusammenfassung**.

<u>Erwartete Ergebnisse</u>:

Die Bestellübersicht zeigt korrekte Werte ungleich null an.

<u>Tatsächliche Ergebnisse</u>:

Der Gesamtwert der Bestellzusammenfassung ist null.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
