---
title: 'ACSD-58383: Doppelte Gutschriften von gleichzeitigen Erstattungsanträgen über [!DNL REST API]'
description: Wenden Sie den Patch ACSD-58383 an, um das Problem in Adobe Commerce zu beheben, bei dem die Ausgabe einer Rückerstattung über die  [!DNL REST API]  mit zwei identischen Anfragen, die gleichzeitig ausgeführt werden, zu doppelten Gutschriften führt.
feature: REST, Payments, Returns
role: Admin, Developer
exl-id: 962970d5-22e7-4bdc-afa0-70e1fa21ecec
source-git-commit: 28390659fe180180c9b2c8d16239008a1f8a510b
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-58383 Adobe Commerce Patch: Doppelte Gutschriften von gleichzeitigen Erstattungsanträgen über [!DNL REST API]

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
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
