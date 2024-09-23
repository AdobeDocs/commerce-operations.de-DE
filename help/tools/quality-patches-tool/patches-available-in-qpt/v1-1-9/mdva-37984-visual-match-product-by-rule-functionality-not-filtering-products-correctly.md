---
title: "MDVA-37984: Visual Merchandiser funktioniert nicht ordnungsgemäß, wenn Staging-Updates angewendet werden"
description: Der Patch MDVA-37984 behebt das Problem, dass die Funktion "Produkt nach Regel abgleichen"des Visual Merchandiser die Produkte bei Anwendung von Staging-Updates nicht korrekt filtert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-37984. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: Categories, Merchandising, Products, Staging
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-37984: Visual Merchandiser funktioniert nicht ordnungsgemäß, wenn Staging-Updates angewendet werden

Der Patch MDVA-37984 behebt das Problem, dass die Funktion &quot;Produkt nach Regel abgleichen&quot;des Visual Merchandiser die Produkte bei Anwendung von Staging-Updates nicht korrekt filtert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-37984. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Funktion &quot;Produkt nach Regel abgleichen&quot;des Visual Merchandiser filtert Produkte nicht richtig, wenn Staging-Updates angewendet werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Zeitplanupdate für jedes vorhandene Produkt.
   * Legen Sie unterschiedliche Werte für `entity_id` und `row_id` fest.
1. Erstellen Sie ein neues konfigurierbares Produkt und dann ein einfaches Produkt (also unterscheiden sich auch das neue Produkt `entity_id` und `row_ids`).
   * Um das Replizieren des Problems zu vereinfachen, legen Sie einen aussagekräftigen Qty-Wert für das einfache Produkt fest, z. B. 5000.
1. Gehen Sie zu einer Kategorie > **Produkte in Kategorie** und aktivieren Sie die Option **Produkte nach Regel abgleichen**.
1. Wählen Sie nun &quot;Menge&quot;als Attribut, &quot;Größer&quot;als Operator und &quot;4500&quot;als Wert aus.
1. Klicken Sie auf **save**.

<u>Erwartete Ergebnisse</u>:

Das neu erstellte konfigurierbare Produkt wird aufgelistet.

<u>Tatsächliche Ergebnisse</u>:

Das neu erstellte konfigurierbare Produkt wird nicht aufgeführt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
