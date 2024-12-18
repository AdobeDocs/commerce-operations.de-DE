---
title: 'ACSD-47669: Interner Server-Fehler beim Importieren von Produkten mit anpassbaren Optionen'
description: Wenden Sie den Patch ACSD-47669 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Importieren von Produkten mit anpassbaren Optionen ein interner Server-Fehler auftritt.
feature: Products
role: Admin, Developer
exl-id: e1a3b3b4-0392-4325-9766-a83276c1a593
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-47669: Interner Server-Fehler beim Importieren von Produkten mit anpassbaren Optionen

Der Patch ACSD-47669 behebt das Problem, dass beim Importieren von Produkten mit anpassbaren Optionen ein interner Server-Fehler auftritt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.38 installiert ist. Die Patch-ID ist ACSD-47669. Beachten Sie, dass das Problem bereits in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Importieren von Produkten mit anpassbaren Optionen tritt ein interner Server-Fehler auf.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine zusätzliche Store-Ansicht. Stellen Sie sicher, dass Sie 2 Shop-Ansichten haben, z. B. en, UK.
1. Erstellen Sie zwei einfache Produkte, z. B. prod1 und prod2.
1. Bereiten Sie eine CSV-Datei vor, die benutzerdefinierte Optionen für beide Produkte in jeder Store-Ansicht und für den Bereich **Alle Store-Ansicht** hinzufügt. CSV-Datei importieren.
1. Bereiten Sie eine weitere CSV-Datei mit zwei Datensätzen vor. Der erste Datensatz sollte darin bestehen, die benutzerdefinierten Optionen von „prod1“ speziell für den UK-Store-Ansichtsbereich zu aktualisieren, und der zweite Datensatz sollte darin bestehen, die benutzerdefinierten Optionen von „prod2“ für den **All Store-Ansicht**-Bereich zu aktualisieren. Diese zweite CSV-Datei importieren.

<u>Erwartete Ergebnisse</u>:

Sie sollten in der Lage sein, Optionen ohne Fehler anzupassen.

<u>Tatsächliche Ergebnisse</u>:

Es tritt ein Fehler wegen einer Integritätsbeschränkung auf.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
