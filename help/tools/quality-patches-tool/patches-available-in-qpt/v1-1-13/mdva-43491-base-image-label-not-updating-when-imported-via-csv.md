---
title: "MDVA-43491: Grundlegende Bildbeschriftung wird beim Import über CSV nicht aktualisiert."
description: Der Patch MDVA-43491 behebt das Problem, dass das "base_image_label"nicht aktualisiert wird, wenn es über eine CSV-Datei für eine Website mit mehreren Stores importiert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43491. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: Data Import/Export
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-43491: Grundlegende Bildbeschriftung wird beim Import über CSV nicht aktualisiert

Der Patch MDVA-43491 behebt das Problem, dass der `base_image_label` nicht aktualisiert wird, wenn er über eine CSV-Datei für eine Multi-Store-Website importiert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43491. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der `base_image_label` wird nicht aktualisiert, wenn er mit einer CSV-Datei für eine Website mit mehreren Stores importiert wird.

<u>Voraussetzungen</u>:

Eine oder mehrere vorhandene nicht standardmäßige Websites, Stores und Store-Ansichten.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein neues Produkt.

   * Laden Sie ein Bild hoch.
   * Weisen Sie das Produkt den neu erstellten Websites zu.

1. Exportieren Sie das Produkt als CSV.
1. Aktualisieren Sie die `base_image_label` für jede Store-Ansicht, indem Sie die Standardzeile der CSV-Datei duplizieren.
1. Importieren Sie die CSV-Datei. Dadurch werden die Beschriftungen für jeden Store korrekt aktualisiert, was auf der Seite zur Produktbearbeitung auf der Registerkarte **Bilder und Videos** überprüft werden kann.
1. Exportieren Sie die CSV-Datei erneut und aktualisieren Sie die Spalte `base_image_label` mit unterschiedlichen Werten.
1. Importieren Sie die CSV-Datei erneut.
1. Öffnen Sie das Produkt in der Admin-Konsole und überprüfen Sie, ob die Bezeichnung für jede Store-Ansicht aktualisiert wurde.

<u>Erwartete Ergebnisse</u>:

Alternativtext (Bildbezeichnung) wird mit dem speicherspezifischen Wert gemäß der CSV-Datei aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Alternativtext (Bildbezeichnung) wird nicht mit dem Wert `base_image_label` in der CSV-Datei aktualisiert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
