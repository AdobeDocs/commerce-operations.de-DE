---
title: 'ACSD-62671: [!DNL GraphQL] gibt beim ersten Versuch keine aktualisierte Adresse zurück'
description: Wenden Sie den ACSD-62671-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem eine [!DNL GraphQL] beim ersten Versuch keine aktuellen Adressinformationen zurückgibt.
feature: GraphQL
role: Admin, Developer
exl-id: afd75ad2-e801-4f8a-b68f-526ca5168413
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%
---
# ACSD-62671: [!DNL GraphQL] gibt beim ersten Versuch keine aktualisierte Adresse zurück

Mit dem Patch ACSD-62671 wird das Problem behoben, dass eine [!DNL GraphQL] beim ersten Versuch keine aktuellen Adressinformationen zurückgibt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57 installiert ist. Die Patch-ID ist ACSD-62671. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

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
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
