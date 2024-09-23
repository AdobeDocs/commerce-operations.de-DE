---
title: 'ACSD-52815: Eingabefeld für das Mengenfeld von nicht standardmäßigen Quellen unterstützt nur bis zu sechs Stellen.'
description: Wenden Sie den Patch ACSD-52815 an, um das Adobe Commerce-Leistungsproblem zu beheben, bei dem das Eingabefeld für das Mengenfeld einer nicht standardmäßigen Quelle nur bis zu sechs Stellen unterstützt, im Gegensatz zu 8 für ein Standardstock.
feature: Inventory, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-52815: Eingabefeld für das Mengenfeld von nicht standardmäßigen Quellen unterstützt nur bis zu sechs Stellen

Der Patch ACSD-52815 behebt das Problem, dass das Eingabefeld für das Mengenfeld einer nicht standardmäßigen Quelle nur bis zu sechs Stellen unterstützt, im Gegensatz zu 8 für ein Standardstock. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID lautet ACSD-52815. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Eingabefeld für das Mengenfeld einer nicht standardmäßigen Quelle unterstützt nur bis zu sechs Stellen, im Gegensatz zu 8 für ein Standardlager.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein neues Lager und eine neue Quelle.
1. Erstellen Sie ein Produkt, bei dem der neue Quellbestand auf 123 eingestellt ist.
1. Überprüfen Sie die Verkaufsmenge (123).
1. Quellmenge auf 12345678 aktualisieren.
1. Überprüfen Sie die verkaufbare Menge erneut.

<u>Erwartete Ergebnisse</u>:

Die Verkaufsmenge zeigt den korrekten Betrag an.

<u>Tatsächliche Ergebnisse</u>:

Die Verkaufsmenge beträgt 999999.999.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
