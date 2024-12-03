---
title: 'ACSD-48318: Fehler bei der Verschachtelung der Umgebungsemulation in "system.log"'
description: Wenden Sie den Patch ACSD-48318 an, um das Adobe Commerce-Problem zu beheben, bei dem jedes Mal, wenn eine Rechnungs-E-Mail gesendet wird, eine Fehlermeldung angezeigt wird, dass die Verschachtelung der Umgebung "main.ERROR:Environment"nicht zulässig ist*.
feature: System, Orders
role: Admin, Developer
exl-id: 24af18de-80dd-4e0a-bdf9-5b9c075fc608
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-48318: Fehler bei der Verschachtelung der Umgebungsemulation in `system.log`

Der Patch ACSD-48318 behebt das Problem, bei dem in `system.log` jedes Mal, wenn eine Rechnungsemail gesendet wird, eine Fehlermeldung *main.ERROR:Environment emulation nesting is not allowed* angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 installiert ist. Die Patch-ID lautet ACSD-48318. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Fehlermeldung *Verschachtelung der Umgebung ist nicht zulässig* wird in `system.log` jedes Mal angezeigt, wenn eine E-Mail zur Rechnung gesendet wird.

<u>Zu reproduzierende Schritte</u>:

1. Bestellung aufgeben und Rechnung generieren.
1. Öffnen Sie die Rechnung über Admin und klicken Sie auf **[!UICONTROL Send Email]**.
1. Führen Sie denselben Schritt für *Credit Memo* und *Sendung* durch, indem Sie auf **[!UICONTROL Send Email]** klicken.

<u>Erwartete Ergebnisse</u>:

Keine Fehler in `system.log`.

<u>Tatsächliche Ergebnisse</u>:

`system.log` wird mit dem Fehler *main.ERROR: Die Verschachtelung der Umgebung ist nicht zulässig* überflutet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

[[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
