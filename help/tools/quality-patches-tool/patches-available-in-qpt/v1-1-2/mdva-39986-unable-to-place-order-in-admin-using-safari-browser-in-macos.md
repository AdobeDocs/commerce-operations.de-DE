---
title: 'MDVA-39986: Im Safari-Browser auf macOS können keine Bestellungen unter „Admin“ aufgegeben werden.'
description: Mit dem Patch MDVA-39986 wird das Problem behoben, dass Benutzende keine Bestellungen unter Verwendung des Safari-Browsers in macOS bei Admin aufgeben können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39986. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
feature: Admin Workspace, Orders
role: Admin
exl-id: bd4e72fe-278d-40ae-98d3-1eeca0a0e70c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# MDVA-39986: Im Safari-Browser auf macOS können keine Bestellungen unter „Admin“ aufgegeben werden.

Mit dem Patch MDVA-39986 wird das Problem behoben, dass Benutzende keine Bestellungen unter Verwendung des Safari-Browsers in macOS bei Admin aufgeben können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39986. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzende können in macOS keine Bestellungen über den Safari-Browser bei Admin aufgeben.

<u>Schritte zur Reproduktion</u>:

1. Bestellung aufgeben.
1. Rufen Sie über den Safari-Browser in macOS den Admin auf und öffnen Sie die zuvor erstellte Bestellung.
1. Klicken Sie auf **Neu**.
1. Versuchen Sie, &quot;**&quot;** aktualisieren.

<u>Erwartete Ergebnisse</u>:

Benutzende sollten in der Lage sein, unter Verwendung des Safari-Browsers in macOS neu zu bestellen.

<u>Tatsächliche Ergebnisse</u>:

Benutzer erhalten einen JS-Fehler, bei dem das Spinnrad angezeigt wird und endlos läuft.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch [!DNL Quality Patches Tool] Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
