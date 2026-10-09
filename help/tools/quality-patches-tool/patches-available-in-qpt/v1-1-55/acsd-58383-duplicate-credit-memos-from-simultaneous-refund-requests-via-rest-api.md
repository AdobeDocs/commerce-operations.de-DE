---
title: 'ACSD-58383: Doppelte Gutschriften von gleichzeitigen Erstattungsanträgen über [!DNL REST API]'
description: Wenden Sie den ACSD-58383 Patch an, um das Problem in Adobe Commerce zu beheben, bei dem die Ausgabe einer Rückerstattung über die [!DNL REST API] mit zwei identischen Anfragen, die gleichzeitig ausgeführt werden, doppelte Gutschriften erzeugt.
feature: REST, Payments, Returns
role: Admin, Developer
exl-id: 962970d5-22e7-4bdc-afa0-70e1fa21ecec
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
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
source-wordcount: '357'
ht-degree: 0%
---
# ACSD-58383: Doppelte Gutschriften von gleichzeitigen Erstattungsanträgen über [!DNL REST API]

Mit dem Patch ACSD-58383 wird das Problem behoben, dass die Ausstellung einer Rückerstattung über die [!DNL REST API] mit zwei identischen Anfragen, die gleichzeitig ausgeführt werden, zu doppelten Gutschriften führt.

Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-58383. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Doppelte Gutschriften resultieren aus zwei gleichzeitig erstellten Rückerstattungen.

<u>Schritte zur Reproduktion</u>:

1. Konfigurieren Sie [!DNL Paypal Express] in der Commerce-[!UICONTROL Admin].
1. Legen Sie die Zahlungsaktion auf &quot;*&quot;*.
1. Konfigurieren Sie die [!DNL PayPal]-IPN (Instant Payment Notification) auf der [!DNL PayPal] Sandbox-Website.
1. Problem-Rückerstattung auf der [!DNL PayPal] Sandbox-Website.
1. Emulieren Sie eine IPN-Nachricht aus [!DNL PayPal] mithilfe von Entwickler-Tools. IPN muss eine Gutschrift erstellen.
1. Erstellen Sie eine zweite Gutschrift mithilfe eines [!DNL API].

<u>Erwartete Ergebnisse</u>:

Für denselben Artikel wird nur eine Gutschrift erstellt.


<u>Tatsächliche Ergebnisse</u>:

Für denselben Artikel werden zwei Gutschriften erstellt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
