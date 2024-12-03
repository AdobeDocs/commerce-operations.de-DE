---
title: 'MDVA-43983: Produkte, die als "Nicht einzeln sichtbar"festgelegt sind, werden in den Suchergebnissen angezeigt'
description: Der Patch MDVA-43983 behebt das Problem, dass die Produkte, die als "Nicht sichtbar individuell"festgelegt sind, weiterhin in den erweiterten Suchergebnissen des Katalogs angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43983. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: Catalog Management, Products, Search
role: Admin
exl-id: d494d263-016b-43fd-aa87-0d74eadc4a6a
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-43983: Produkte, die als &quot;Nicht einzeln sichtbar&quot;festgelegt sind, werden in den Suchergebnissen angezeigt

Der Patch MDVA-43983 behebt das Problem, dass die Produkte, die als &quot;Nicht sichtbar individuell&quot;festgelegt sind, weiterhin in den erweiterten Suchergebnissen des Katalogs angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43983. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Produkte, die als &quot;Nicht einzeln sichtbar&quot;festgelegt sind, werden weiterhin in den erweiterten Suchergebnissen des Katalogs angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Attribut mit dem Eingabetyp &quot;Katalog&quot;für Store Owner **als** Dropdown **oder** visuelles Muster **(z. B. Farbe).**
1. Stellen Sie **In der Suche** auf **Ja** und **In der erweiterten Suche anzeigen** auf **Ja** ein.
1. Fügen Sie einige Attributoptionen hinzu.
1. Erstellen Sie Produkte mit **Sichtbarkeit** als **Nicht einzeln sichtbar**.
1. Farbattribute zuweisen - Optionen.
1. Rufen Sie die Seite **Erweiterte Katalogsuche** auf der Storefront auf.
1. Wählen Sie im Feld Farbattribut nur die Option Farbattribut aus und lassen Sie die übrigen Felder leer oder so, wie es ist.
1. Senden Sie ein erweitertes Suchformular.
1. Beobachten Sie die Suchergebnisse.

<u>Erwartete Ergebnisse</u>:

Produkte, die als &quot;Nicht einzeln sichtbar&quot;festgelegt sind, werden nicht in den erweiterten Suchergebnissen des Katalogs angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Produkte, die als &quot;Nicht einzeln sichtbar&quot;festgelegt sind, werden in den erweiterten Suchergebnissen des Katalogs angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
