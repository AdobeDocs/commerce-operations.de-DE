---
title: "MDVA-43201: Fehler bei Verwendung des DOB-Felds mit dem Gebietsschema PT"
description: Der Patch MDVA-43201 behebt das Problem, dass bei der Verwendung des DOB-Kundenattributs im Formular zur Kundenregistrierung für das portugiesische Gebietsschema ein Fehler auftritt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-43201. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
feature: B2B, Cache
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-43201: Fehler bei Verwendung des DOB-Felds mit dem Gebietsschema PT

Der Patch MDVA-43201 behebt das Problem, dass bei der Verwendung des DOB-Kundenattributs im Formular zur Kundenregistrierung für das portugiesische Gebietsschema ein Fehler auftritt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-43201. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn das DOB-Kundenattribut dem Formular zur Kundenregistrierung für das portugiesische Gebietsschema hinzugefügt wird, gibt das Formular den Fehler *Argument 1, das an iterator_to_array() übergeben wird, muss das übergebene &quot;interface&quot;implementieren, null, angegeben*.

<u>Voraussetzungen</u>:

B2B-Module sind installiert.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu Admin > **Stores** > **Konfiguration** > **Allgemein** > **Gebietsschemaoptionen**, setzen Sie Locale auf **Portugiesisch (Portugal)** und klicken Sie auf **Speichern**.
1. Neuindizieren und leeren Sie den Cache.
1. Gehen Sie zu **Stores** > **Attribut** > **Kunde**.
1. Öffnen Sie das DOB-Kundenattribut und legen Sie **Auf Storefront anzeigen** auf **Ja** fest.
1. Wählen Sie alle aus **Formular zur Verwendung in**.
1. Speichern Sie das Attribut.
1. Rufen Sie im Frontend die Seite Neues Konto erstellen auf.

<u>Erwartete Ergebnisse</u>:

Das Formular zur Kundenregistrierung für den portugiesischen Store gibt keinen Fehler beim Hinzufügen des DOB-Attributs.

<u>Tatsächliche Ergebnisse</u>:

Das Formular zur Kundenregistrierung für den portugiesischen Store gibt beim Hinzufügen des DOB-Attributs einen Fehler aus.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
