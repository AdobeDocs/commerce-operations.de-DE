---
title: "MDVA-41164: Unternehmen mit benutzerdefinierten Kundenattributen kann nicht gespeichert oder bearbeitet werden"
description: Der Patch MDVA-41164 behebt das Problem, dass der Admin-Benutzer ein Unternehmen mit benutzerdefinierten Kundenattributen von Dateien oder Bildern beliebigen Typs nicht speichern oder bearbeiten kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41164. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# MDVA-41164: Unternehmen mit benutzerdefinierten Kundenattributen kann nicht gespeichert oder bearbeitet werden

Der Patch MDVA-41164 behebt das Problem, dass der Admin-Benutzer ein Unternehmen mit benutzerdefinierten Kundenattributen von Dateien oder Bildern beliebigen Typs nicht speichern oder bearbeiten kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41164. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Admin-Benutzer kann ein Unternehmen mit benutzerdefinierten Kundenattributen von Dateien oder Bildern beliebigen Typs nicht speichern oder bearbeiten.

<u>Voraussetzungen</u>:

Das B2B-Modul ist installiert.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie Unternehmen in **Stores** > **Konfiguration** > **B2B-Funktionen**.
1. Erstellen Sie ein Kundenattribut in **Stores** > **Attribute** > **Kunden** > **Neues Attribut hinzufügen**:
   * Eingabetyp: Datei (Anhang)
   * Auf Storefront anzeigen: ja
   * Sortierreihenfolge: Beliebig
   * Forms zur Verwendung in: Wählen Sie alle
1. Erstellen Sie ein neues Unternehmen in **Kunden** > **Unternehmen** > **Neues Unternehmen hinzufügen** und laden Sie eine Datei für das oben erstellte neue Attribut hoch.

<u>Erwartete Ergebnisse</u>:

Der Benutzer kann die Erstellung des Unternehmens abschließen und die Anlage wird ohne Fehler hochgeladen.

<u>Tatsächliche Ergebnisse</u>:

* Sie erhalten eine Fehlermeldung: *Beim Speichern der Datei ist etwas schief gelaufen.*
* Das Ausnahmeprotokoll enthält einen Datensatz wie den folgenden:

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
  ```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
