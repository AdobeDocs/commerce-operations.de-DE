---
title: 'ACSD-62671: [!DNL GraphQL]  gibt beim ersten Versuch keine aktualisierte Adresse zurück'
description: Wenden Sie den ACSD-62671-Patch an, um das Adobe Commerce-Problem zu beheben [!DNL GraphQL]  bei dem eine -Anfrage beim ersten Versuch keine aktuellen Adressinformationen zurückgibt.
feature: GraphQL
role: Admin, Developer
source-git-commit: 697b0e3d7789b0324866d2192f56613f5526e4df
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-62671: [!DNL GraphQL] gibt beim ersten Versuch keine aktualisierte Adresse zurück

Mit dem Patch ACSD-62671 wird das Problem behoben, dass eine [!DNL GraphQL] beim ersten Versuch keine aktuellen Adressinformationen zurückgibt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) 1.1.57 installiert ist. Die Patch-ID ist ACSD-62671. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bei Verwendung der [!DNL GraphQL Application Server] gibt die Kundenadressanfrage nicht die neuesten Daten zurück.

<u>Schritte zur Reproduktion</u>:

1. Installieren und starten Sie [!DNL GraphQL Application Server].
1. Stellen Sie sicher, dass `graphQL_query_resolver_result` Cache-Typ aktiviert ist.
1. Verwenden Sie [!DNL GraphQL] für:

   * Erstellen Sie einen Kunden.
   * Erstellen eines Tokens.
   * Verwenden Sie das Token, um mehrere Adressen für den oben genannten Kunden zu erstellen.

1. Senden Sie [!DNL GraphQL] Anfrage, um die Adressen des Kunden zu erhalten.
1. Fügen Sie dem Kunden eine neue Adresse hinzu.
1. Wiederholen Sie die Anfrage aus Schritt #4 mehrmals, während Sie die Anzahl der zurückgegebenen Adressen in der Antwort überwachen.

<u>Erwartete Ergebnisse</u>:

[!DNL GraphQL] Antwort enthält die richtige Anzahl von Kundenadressen.

<u>Tatsächliche Ergebnisse</u>:

Gelegentlich wird in der [!DNL GraphQL] Antwort eine falsche Anzahl von Adressen zurückgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
