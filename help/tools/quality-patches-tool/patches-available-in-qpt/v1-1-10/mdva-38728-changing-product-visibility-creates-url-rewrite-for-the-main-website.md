---
title: "MDVA-38728: Durch Ändern der Produktsichtbarkeit wird URL-Neufassung für die Haupt-Website erstellt"
description: Der Patch MDVA-38728 behebt das Problem, bei dem durch die Änderung der Produktsichtbarkeit der zweiten Website ein URL-Neuschreiben für die Haupt-Website erstellt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-38728. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-38728: Durch Ändern der Produktsichtbarkeit wird eine URL-Neufassung für die Haupt-Website erstellt.

Der Patch MDVA-38728 behebt das Problem, bei dem durch die Änderung der Produktsichtbarkeit der zweiten Website ein URL-Neuschreiben für die Haupt-Website erstellt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-38728. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn Sie die Produktsichtbarkeit der zweiten Website ändern, wird eine URL-Umschreibung für die Haupt-Website erstellt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine zusätzliche Website, einen Store und eine Storeinstanz.
1. Erstellen Sie ein einfaches Produkt.
1. Stellen Sie die Sichtbarkeit auf **Nicht einzeln sichtbar** ein.
1. Weisen Sie das Produkt nur der zweiten Website zu.
1. Füllen Sie alle anderen erforderlichen Felder aus.
1. Speichern Sie das Produkt.
1. MySQL-Warteschlangen starten:

   ```mysql
   bin/magento queue:consumers:start product_action_attribute.update &
   bin/magento queue:consumers:start product_action_attribute.website.update &
   ```

1. Navigieren Sie zur Produktliste.
1. Wählen Sie das erstellte Produkt aus und aktualisieren Sie das Sichtbarkeitsattribut mithilfe des gebündelten Updates für Katalog und Suche.
1. Überprüfen Sie die URL-Neufassung.

<u>Erwartete Ergebnisse</u>:

Die Neufassung wird für die zweite Website erstellt, der das Produkt zugewiesen ist.

<u>Tatsächliche Ergebnisse</u>:

Die Neufassung wird für die Haupt-Website erstellt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
