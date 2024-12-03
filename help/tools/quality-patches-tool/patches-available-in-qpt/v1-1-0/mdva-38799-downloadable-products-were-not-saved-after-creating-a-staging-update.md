---
title: 'MDVA-38799: Herunterladbare Produkte, die nach der Erstellung eines Staging-Updates nicht gespeichert wurden'
description: Der Patch MDVA-38799 behebt das Problem, dass herunterladbare Produkte nach der Erstellung eines Staging-Updates nicht gespeichert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-38799. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.
feature: Products, Staging
role: Admin
exl-id: 0ae665a8-cda2-4340-91e7-5b9b969a6607
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# MDVA-38799: Herunterladbare Produkte, die nach der Erstellung eines Staging-Updates nicht gespeichert wurden

Der Patch MDVA-38799 behebt das Problem, dass herunterladbare Produkte nach der Erstellung eines Staging-Updates nicht gespeichert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-38799. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce in Cloud-Infrastruktur 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0-2.4.2-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Herunterladbare Produkte werden nach dem Erstellen eines Staging-Updates nicht gespeichert. Benutzer erhalten die Fehlermeldung: *Das herunterladbare Beispiel ist nicht mit dem Produkt verknüpft. Überprüfen Sie den Link und versuchen Sie es erneut*.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Katalog** > **Produkte**.
1. Klicken Sie auf das Dropdown-Menü neben Produkt hinzufügen und wählen Sie Herunterladbares Produkt aus.
   * Geben Sie den Namen, die SKU, den Preis und die Menge des Produkts an.
1. Scrollen Sie nach unten zur Seite &quot;Download-Informationen&quot;.
1. Klicken Sie unter &quot;Beispiele&quot;auf **Link hinzufügen**.
   * Füllen Sie den Titel und die Upload-Datei aus (der Dateityp spielt keine Rolle).
1. Klicken Sie auf **Speichern**. Sie erhalten die folgende Meldung: *Sie haben das Produkt gespeichert*.
1. Klicken Sie oben auf der Seite auf **Neues Update planen** .
   * Geben Sie den Aktualisierungsnamen sowie ein gültiges Start- und Enddatum ein.
1. Klicken Sie beim Staging-Update auf **Speichern** .
1. Klicken Sie auf **Speichern** für das Produkt.

<u>Erwartete Ergebnisse</u>:

Das Produkt wird ohne Fehler gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten die Fehlermeldung: *Das herunterladbare Beispiel ist nicht mit dem Produkt verknüpft. Überprüfen Sie den Link und versuchen Sie es erneut*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
