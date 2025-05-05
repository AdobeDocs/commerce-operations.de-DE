---
title: 'ACSD-43887: Falsche Details auf der Kasse Zahlungsseite angezeigt'
description: Mit dem Patch ACSD-43887 wird das Problem behoben, dass falsche Details auf der Kaufbestätigungsseite angezeigt werden, wenn Bestellungen für Unternehmen aktiviert sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 installiert ist. Die Patch-ID ist ACSD-43887. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
exl-id: e150f093-9f1a-4ba5-bdcf-90e7f42a29c3
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# ACSD-43887: Falsche Details auf der Kasse Zahlungsseite angezeigt

Mit dem Patch ACSD-43887 wird das Problem behoben, dass falsche Details auf der Kaufbestätigungsseite angezeigt werden, wenn Bestellungen für Unternehmen aktiviert sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 installiert ist. Die Patch-ID ist ACSD-43887. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn Bestellungen für Unternehmen aktiviert sind, werden auf der Zahlungsseite der Kasse falsche Details angezeigt.

<u>Voraussetzungen</u>:

1. B2B-Module werden installiert.
1. Firma aktivieren ist auf &quot;_&quot;_. Gehen Sie zu **Stores** > **Konfigurationen** > **Allgemein** > **B2B-Funktionen** > **Firma aktivieren** > **Ja**.
1. „Bestellungen aktivieren“ ist auf &quot;_&quot;_. Navigieren Sie **Konfiguration der Bestellgenehmigung** > **Bestellungen aktivieren** > **Ja**.
1. PayPal Express ist als Zahlungsmethode konfiguriert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen eines virtuellen Produkts.
1. Registrieren Sie ein Unternehmenskonto über das Frontend bei einem Unternehmensadministrator.
1. Genehmigen Sie das Unternehmenskonto über das Backend und setzen Sie **Bestellungen aktivieren** bei der Genehmigung _Unternehmens auf Ja_.
1. Gehen Sie zum Frontend und melden Sie sich mit dem in Schritt zwei erstellten Unternehmensadministratorkonto an.
1. Erstellen Sie einen „Standardbenutzer“ für das Unternehmen. Navigieren Sie **Firmenbenutzer** > **Neuen Benutzer hinzufügen**.
1. Erstellen Sie eine „Genehmigungsregel“ für das Unternehmen. Navigieren Sie **Genehmigungsregeln** > **Neue Regel hinzufügen**.

   * Regeltyp: Bestellsumme
   * Bestellsumme: ist größer oder gleich $1
   * Erfordert Genehmigung von: Unternehmensadministrator

1. Melden Sie sich ab und melden Sie sich mit dem Konto „Standardbenutzer“ an.
1. Fügen Sie das in Schritt 1 erstellte virtuelle Produkt zum Warenkorb hinzu und fahren Sie mit dem Checkout fort.
1. Wählen Sie PayPal Express als Zahlungsmethode und klicken Sie auf **Bestellung aufgeben**.
1. Melden Sie sich ab und melden Sie sich mit dem Unternehmensadministratorkonto an.
1. Gehen Sie zu **Meine Bestellungen** und klicken Sie **Firmenbestellungen** für die in Schritt **erstellte Bestellung auf** Anzeigen“.
1. Validieren Sie die Bestellung. Der Bestellstatus muss „Genehmigt: Zahlung ausstehend“ lauten.
1. Melden Sie sich ab und melden Sie sich mit dem Firmenkonto „Standardbenutzer“ an.
1. Gehen Sie **Meine Bestellungen** > **Anzeigen** > **Bestellung aufgeben**.
1. Überprüfen Sie die **Bestellzusammenfassung**.

<u>Erwartete Ergebnisse</u>:

Die Bestellzusammenfassung zeigt korrekte Werte ungleich null an.

<u>Tatsächliche Ergebnisse</u>:

Der Gesamtwert für die Bestellzusammenfassung ist null.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
