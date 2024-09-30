---
title: "ACSD-47669: Interner Server-Fehler beim Importieren von Produkten mit anpassbaren Optionen"
description: Wenden Sie den Patch ACSD-47669 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Importieren von Produkten mit anpassbaren Optionen ein interner Serverfehler auftritt.
feature: Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-47669: Interner Server-Fehler beim Importieren von Produkten mit anpassbaren Optionen

Der Patch ACSD-47669 behebt das Problem, bei dem während des Produktimports mit anpassbaren Optionen ein interner Server-Fehler auftritt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.38 installiert ist. Die Patch-ID ist ACSD-47669. Bitte beachten Sie, dass das Problem bereits in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Importieren von Produkten mit anpassbaren Optionen tritt ein interner Server-Fehler auf.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine zusätzliche Store-Ansicht. Stellen Sie sicher, dass Sie über 2 Store-Ansichten verfügen, z. B. en, UK.
1. Erstellen Sie zwei einfache Produkte, z. B. prod1 und prod2.
1. Bereiten Sie eine CSV-Datei vor, die benutzerdefinierte Optionen für beide Produkte in jeder Store-Ansicht und für den Bereich **Alle Store-Ansicht** hinzufügt. Importieren Sie diese CSV-Datei.
1. Bereiten Sie eine weitere CSV-Datei vor, die zwei Datensätze enthält. Der erste Datensatz sollte darin bestehen, die benutzerdefinierten Optionen von &quot;prod1&quot;speziell für den Umfang der britischen Store-Ansicht zu aktualisieren, und der zweite Datensatz sollte darin bestehen, die benutzerdefinierten Optionen von &quot;prod2&quot;für den Bereich **Alle Store-Ansicht** zu aktualisieren. Importieren Sie diese zweite CSV-Datei.

<u>Erwartete Ergebnisse</u>:

Sie sollten in der Lage sein, die Optionen ohne Fehler anzupassen.

<u>Tatsächliche Ergebnisse</u>:

Ein Fehler wegen Verletzung der Integritätseinschränkung tritt auf.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
