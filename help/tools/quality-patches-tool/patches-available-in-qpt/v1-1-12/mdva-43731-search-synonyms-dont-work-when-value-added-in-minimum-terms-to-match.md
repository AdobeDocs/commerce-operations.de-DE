---
title: 'MDVA-43731: Suchsynonyme funktionieren nicht, wenn ein Wert in „Mindestbegriffe für Übereinstimmung“ hinzugefügt wird'
description: Der Patch MDVA-43731 behebt das Problem, dass Suchsynonyme nicht mehr funktionieren, wenn ein Wert in „Minimale übereinstimmende Begriffe“ hinzugefügt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43731. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Cache, Marketing Tools, Search
role: Admin
exl-id: 1eada0cd-c0ab-4f0f-b6bf-7c10e1df07ce
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# MDVA-43731: Suchsynonyme funktionieren nicht, wenn ein Wert in „Mindestbegriffe für Übereinstimmung“ hinzugefügt wird

Der Patch MDVA-43731 behebt das Problem, dass Suchsynonyme nicht mehr funktionieren, wenn ein Wert in „Minimale übereinstimmende Begriffe“ hinzugefügt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43731. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Suchsynonyme funktionieren nicht mehr, wenn ein Wert in „Abzugleichende Mindestbegriffe“ hinzugefügt wird.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie Adobe Commerce mit Beispieldaten.
1. Konfigurieren Sie Elasticsearch7 als Suchmaschine.
1. Suchen Sie nach dem Wort „Jacke“. Eine Liste mit Produkten wird angezeigt.
1. Fügen Sie den Parameter [4&lt;60%] in **Konfiguration** > **Katalog** > **Katalogsuche** > **Mindestanzahl an übereinstimmenden Begriffen**.
1. Löschen Sie den Konfigurations-Cache und führen Sie eine Neuindizierung durch.
1. Suchen Sie erneut nach dem Wort „Jacke“ und beachten Sie, dass eine Liste von Produkten angezeigt wird.
1. Gehen Sie zu **Marketing** > **SEO &amp; Search** > **Suchsynonyme**.
1. Erstellen Sie Suchsynonyme, indem Sie die folgenden Synonyme hinzufügen: jacke, bagtecs, express plus.
1. Führen Sie eine Neuindizierung durch.
1. Führen Sie eine Produktsuche unter Verwendung eines der Synonyme durch. z. B. Jacke.

<u>Erwartete Ergebnisse</u>:

Sie erhalten in den Suchergebnissen dieselbe Produktliste wie zuvor.

<u>Tatsächliche Ergebnisse</u>:

In den Suchergebnissen wird kein Produkt angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
