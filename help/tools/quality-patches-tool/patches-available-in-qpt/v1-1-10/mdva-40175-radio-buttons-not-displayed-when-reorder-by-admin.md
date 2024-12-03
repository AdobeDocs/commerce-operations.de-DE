---
title: 'MDVA-40175: Optionsfelder werden bei Neuanordnung nicht angezeigt'
description: Der Patch MDVA-40175 löst das Problem, dass die Optionsfelder nicht angezeigt werden, wenn Benutzer versuchen, eine Neuanordnung vorzunehmen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-40175. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
feature: Admin Workspace, Orders
role: Admin
exl-id: e84ff581-13ba-4f9f-9247-519b0b54807a
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-40175: Optionsfelder werden bei Neuanordnung nicht angezeigt

Der Patch MDVA-40175 löst das Problem, dass die Optionsfelder nicht angezeigt werden, wenn Benutzer versuchen, eine Neuanordnung vorzunehmen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-40175. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Optionsfelder werden nicht im Bereich Zahlungs- und Versandinformationen angezeigt, wenn Benutzer versuchen, eine Neuanordnung vorzunehmen.

<u>Voraussetzungen</u>:

1. Ein Kundenkonto mit einer Lieferadresse und einer Rechnungsadresse wird erstellt.
1. Ein einfaches Produkt wird erstellt.
1. Verschiedene Versandmethoden sind konfiguriert.
1. Es wird mindestens eine Bestellung erstellt.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zum Admin-Bedienfeld > **Verkauf** > **Bestellungen**.
1. Wählen Sie die erstellte Reihenfolge aus.
1. Klicken Sie auf den Link **Anzeigen** .
1. Klicken Sie auf die Schaltfläche **Neu anordnen** .
1. Scrollen Sie auf der Seite nach unten zum Abschnitt **Zahlungs- und Versandinformationen** .
1. Klicken Sie auf **Klicken, um die Versandmethode zu ändern**.

<u>Erwartete Ergebnisse</u>:

Die Liste der Versandmethoden mit Optionsfeldern wird angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die Liste der Versandmethoden ohne Optionsfelder wird angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
