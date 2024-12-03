---
title: 'MDVA-43731: Suchsynonyme funktionieren nicht, wenn unter "Mindestbegriffe"ein Wert hinzugefügt wird.'
description: Der Patch MDVA-43731 behebt das Problem, dass Suchsynonyme nicht mehr funktionieren, wenn ein Wert unter "Mindestbegriffe"hinzugefügt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43731. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: Cache, Marketing Tools, Search
role: Admin
exl-id: 1eada0cd-c0ab-4f0f-b6bf-7c10e1df07ce
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# MDVA-43731: Suchsynonyme funktionieren nicht, wenn unter &quot;Mindestbegriffe&quot;ein Wert hinzugefügt wird.

Der Patch MDVA-43731 behebt das Problem, dass Suchsynonyme nicht mehr funktionieren, wenn ein Wert unter &quot;Mindestbegriffe&quot;hinzugefügt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43731. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Suchsynonyme funktionieren nicht mehr, wenn unter &quot;Mindestbegriffe&quot;ein Wert hinzugefügt wird.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce mit Beispieldaten.
1. Konfigurieren Sie Elasticsearch7 als Suchmaschine.
1. Suchen Sie nach &quot;Jacket&quot;. Eine Liste der Produkte wird angezeigt.
1. Fügen Sie den Parameter &quot;[4&lt;60%]&quot;in &quot;**Konfiguration**&quot;> &quot;**Katalog**&quot;> &quot;**Katalogsuche**&quot;> &quot;**Mindestbegriffe, die übereinstimmen**&quot; hinzu.
1. Löschen Sie den Konfigurationscache und führen Sie eine Neuindizierung durch.
1. Suchen Sie erneut nach dem Wort &quot;Jacket&quot; und beachten Sie, dass eine Liste von Produkten angezeigt wird.
1. Navigieren Sie zu **Marketing** > **SEO &amp; Suche** > **Suchsynonyme**.
1. Erstellen Sie Synonyme für die Suche, indem Sie die folgenden Synonyme hinzufügen: Jacke, Bagtecs, Express plus.
1. Führen Sie eine Neuindizierung durch.
1. Führen Sie eine Produktsuche mit einem der Synonyme durch. Beispiel: Jacke.

<u>Erwartete Ergebnisse</u>:

Sie erhalten dieselbe Produktliste wie zuvor in den Suchergebnissen.

<u>Tatsächliche Ergebnisse</u>:

In den Suchergebnissen wird kein Produkt angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
