---
title: "MDVA-42689: Benutzer erhalten beim Aktualisieren von Produktkategorien während des Imports einen Fehler wegen Integrationsbegrenzung."
description: Der Patch MDVA-42689 behebt das Problem, dass Benutzer beim Aktualisieren von Produktkategorien während des Imports einen Fehler wegen Integrity Constraint Violation erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42689. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: Categories, Data Import/Export, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-42689: Benutzer erhalten beim Aktualisieren von Produktkategorien während des Imports einen Fehler wegen Integrationsbegrenzung.

Der Patch MDVA-42689 behebt das Problem, dass Benutzer beim Aktualisieren von Produktkategorien während des Imports einen Fehler wegen Integrity Constraint Violation erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42689. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Adobe Commerce gibt beim Aktualisieren von Produktkategorien während des Imports einen Fehler wegen Integrationsbegrenzung aus.

<u>Zu reproduzierende Schritte</u>:

1. Richten Sie zwei Websites ein.
1. Erstellen Sie Unterkategorien unter der Stammkategorie bis zu zwei Ebenen auf der Kategorieseite. Beispiel: Stammkategorie > **Fanggerät** > **Watches**.
1. Erstellen Sie zwei einfache Produkte und weisen Sie beide Produkte derselben Kategorie **Zahnrad** > **Watches** zu.
1. Weisen Sie beiden Websites ein einfaches Produkt zu.
1. Speichern Sie das Produkt.
1. Bereiten Sie eine CSV-Datei für den Import vor. Es sollte zwei Produktdatensätze mit unterschiedlichen Store-Ansichten geben. Eines der Produkte sollte zu beiden Store-Ansichten gehören.
1. Importieren Sie nun die CSV-Datei, indem Sie zu &quot;**System**&quot;> &quot;**Import**&quot;> &quot;**Entitätstyp**&quot;(Produkte) navigieren.

<u>Erwartete Ergebnisse</u>:

CSV-Dateien werden ohne Fehler importiert.

<u>Tatsächliche Ergebnisse</u>:

Adobe Commerce gibt den folgenden Fehler aus:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry '1302' for key 'PRIMARY', query was: INSERT INTO `catalog_url_rewrite_product_category` (`url_rewrite_id`,`category_id`,`product_id`) VALUES (?, ?, ?), (?, ?, ?), (?, ?, ?)
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
