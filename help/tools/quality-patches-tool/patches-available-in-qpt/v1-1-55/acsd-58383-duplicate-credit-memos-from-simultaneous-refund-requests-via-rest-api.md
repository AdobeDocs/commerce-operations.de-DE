---
title: "ACSD-58383: Duplizierte Kreditkarten aus gleichzeitigen Erstattungsanträgen via [!DNL REST API]"
description: Wenden Sie den Patch ACSD-58383 an, um das Adobe Commerce-Problem zu beheben, bei dem die Ausgabe einer Rückerstattung über den  [!DNL REST API] mit zwei identischen Anforderungen, die gleichzeitig ausgeführt werden, doppelte Kreditmemos erzeugt.
feature: REST, Payments, Returns
role: Admin, Developer
source-git-commit: ce3faa5dfc05500dcd672498761b48307064614e
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---


# Patch ACSD-58383 Adobe Commerce: Duplizierte Kreditkarten aus gleichzeitigen Erstattungsanträgen über [!DNL REST API]

Der Patch ACSD-58383 behebt das Problem, dass die Ausgabe einer Rückerstattung über den [!DNL REST API] mit zwei identischen Anforderungen, die gleichzeitig ausgeführt werden, zu doppelten Kreditkarten führt.

Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-58383. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Doppelte Kreditkarten ergeben sich aus zwei gleichzeitig erstellten Erstattungen.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie [!DNL Paypal Express] in der Commerce [!UICONTROL Admin].
1. Stellen Sie die Zahlungsaktion auf *Verkauf* ein.
1. Konfigurieren Sie die [!DNL PayPal] IPN (Sofortige Zahlungsbenachrichtigung) auf der Sandbox-Website [!DNL PayPal] .
1. Ausgabe der Rückerstattung auf der [!DNL PayPal] Sandbox-Website.
1. Emulieren Sie eine IPN-Nachricht von [!DNL PayPal] mithilfe von Entwicklertools. IPN muss ein Kreditmemo erstellen.
1. Erstellen Sie ein zweites Kreditmemo mit einem [!DNL API] -Aufruf.

<u>Erwartete Ergebnisse</u>:

Für dasselbe Element wird nur ein Kreditmemo erstellt.


<u>Tatsächliche Ergebnisse</u>:

Für dasselbe Element werden zwei Kreditkarten erstellt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
