---
title: 'MDVA-41136: Ablaufdatum von image-cache-sessid wird nicht verlängert'
description: Der Patch MDVA-41136 löst das Problem, dass das Ablaufdatum des Cookies „mage-cache-sessid“ nicht verlängert wird, was zu einer Bereinigung der Kundendaten führt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-41136. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Cache
role: Admin
exl-id: f9fbbbdb-b440-4e94-a5b0-c03cdad9f010
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# MDVA-41136: Ablaufdatum von image-cache-sessid wird nicht verlängert

Der MDVA-41136 Patch löst das Problem, dass das Ablaufdatum des `mage-cache-sessid`-Cookies nicht verlängert wird, was zu einer Bereinigung der Kundendaten führt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-41136. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Ablaufdatum der `mage-cache-sessid` wird nicht verlängert, was zu einer Bereinigung der Kundendaten führt.

<u>Schritte zur Reproduktion</u>:

1. Wechseln Sie in der Commerce-Admin zu **Stores** > **Configuration** > **Web** > **Standard-Cookie-Einstellungen** > und setzen Sie **Cookie Lifetime** auf 60.
1. Melden Sie sich als Kunde in der Storefront an.
1. Gehen Sie zu **Mein Konto**.
1. Laden Sie die Seite nach 30 Sekunden neu.

<u>Erwartete Ergebnisse</u>:

Der Name des Kunden wird in der Kopfzeile angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Der Kundenname in der Kopfzeile fehlt und die *Standard-Begrüßungsnachricht!* Meldung wird angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
