---
title: "MDVA-39923: Bei der Suche nach SKU in der B2B-Schnellbestellfunktion wird zwischen Groß- und Kleinschreibung unterschieden"
description: Der Patch MDVA-39923 behebt das Problem, dass Kunden einen Fehler erhalten, wenn sie die Bestellung durch SKU in der B2B-Schnellbestellfunktion durchsuchen, wobei der Fall anders ist als der, mit dem der Name gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39923. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
feature: B2B, Catalog Management, Orders, Search
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-39923: Bei der Suche nach SKU in der B2B-Schnellbestellfunktion wird zwischen Groß- und Kleinschreibung unterschieden

Der Patch MDVA-39923 behebt das Problem, dass Kunden einen Fehler erhalten, wenn sie die Bestellung durch SKU in der B2B-Schnellbestellfunktion durchsuchen, wobei der Fall anders ist als der, mit dem der Name gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39923. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Bei der Suche nach der SKU in der Funktion für die schnelle B2B-Bestellung wird zwischen Groß- und Kleinschreibung unterschieden und es wird ein Fehler angezeigt, wenn eine andere Groß-/Kleinschreibung verwendet wird als die, mit der die SKU gespeichert wird.

<u>Voraussetzungen</u>:

B2B-Module sind installiert.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Administrator an und gehen Sie zu &quot;**Stores**&quot;> &quot;**Konfiguration**&quot;> &quot;**B2B**&quot;.
1. Aktivieren Sie **Freigegebener Katalog** und **Quick Order**.
1. Erstellen Sie ein Produkt mit SKU in Großbuchstaben, z. B. TEST20-1234
1. Zuweisen eines erstellten Produkts zum **freigegebenen Katalog**.
1. Melden Sie sich als Kunde an und klicken Sie auf **Quick Order**.
1. Geben Sie die SKU in Kleinbuchstaben ein, z. B. test20-1234.

<u>Erwartete Ergebnisse</u>:

Das Produkt sollte unabhängig vom verwendeten Fall gefunden werden.

<u>Tatsächliche Ergebnisse</u>:

Die folgende Fehlermeldung wird empfangen: *1 Produkt(e) erfordert(n) Ihre Aufmerksamkeit*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
