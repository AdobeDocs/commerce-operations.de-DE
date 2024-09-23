---
title: "MDVA-32776: Lagerstatus nicht mit Bestellplatzierung aktualisiert"
description: Der Patch MDVA-32776 behebt das Problem, dass der Lagerstatus nicht aktualisiert wird, wenn eine Bestellung aufgegeben, aber nicht versandt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-32776. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
feature: Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-32776: Lagerstatus nicht mit Bestellplatzierung aktualisiert

Der Patch MDVA-32776 behebt das Problem, dass der Lagerstatus nicht aktualisiert wird, wenn eine Bestellung aufgegeben, aber nicht versandt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-32776. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Lagerstatus wird nicht aktualisiert, wenn eine Bestellung aufgegeben, aber nicht versandt wird.

<u>Voraussetzungen</u>:

1. Das Lagerbestandsmodul ist installiert.
1. &quot;Nicht vorrätige Produkte anzeigen&quot;ist auf *Ja* eingestellt.

   Gehen Sie dazu zu **Stores** > **Konfiguration** > **Katalog** > **Bestand** > **Nicht vorrätige Produkte anzeigen** = *Ja*.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei einfache Produkte mit qty = 11 und 22.
1. Erstellen Sie ein gruppiertes Produkt mit den einfachen Produkten, die Sie in Schritt 1 erstellt haben.
1. Fügen Sie gruppierte Produkte zum Warenkorb hinzu, indem Sie eine der Produktmengen auf 11 setzen und das andere einfache Produkt aus dem Lager holen.
1. Führen Sie den Checkout aus und geben Sie die Bestellung auf.

<u>Erwartete Ergebnisse</u>:

Gruppierte Produkte zeigen `out-of-stock` -Beschriftungen an, wenn verknüpfte einfache Produkte nicht mehr vorrätig sind.

<u>Tatsächliche Ergebnisse</u>:

1. Das einfache Produkt mit qty = 11 wird nicht vorrätig angezeigt.
1. Das gruppierte Produkt zeigt keine *Nicht vorrätig* -Meldung für das Produkt mit qty = 11 an. Wenn Sie dieses Produkt jedoch zum Warenkorb hinzufügen, wird der Fehler *nicht vorrätig* angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html-) verfügbare Patches.
