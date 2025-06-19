---
title: 'ACSD-48318: Verschachtelungsfehler bei der Umgebungsemulation in „system.log“'
description: Wenden Sie den Patch ACSD-48318 an, um das Adobe Commerce-Problem zu beheben, bei dem jedes Mal, wenn eine Rechnungs-E-Mail gesendet wird, eine Fehlermeldung in „system.log“ angezeigt wird, in der die Verschachtelung der Umgebungsemulation *main.ERROR:Environment nicht zulässig* ist.
feature: System, Orders
role: Admin, Developer
exl-id: 24af18de-80dd-4e0a-bdf9-5b9c075fc608
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-48318: Verschachtelungsfehler bei der Umgebungsemulation in `system.log`

Der Patch ACSD-48318 behebt das Problem, dass eine Fehlermeldung *main.ERROR:Environment emulation nesting is not allowed* jedes Mal, wenn eine Rechnungs-E-Mail gesendet wird, in `system.log` angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 installiert ist. Die Patch-ID ist ACSD-48318. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Fehlermeldung *Verschachtelung der Umgebungsemulation ist nicht zulässig* wird bei jedem Versand einer Rechnungs-E-Mail in `system.log` angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Bestellung aufgeben und Rechnung generieren.
1. Öffnen Sie die Rechnung vom Administrator aus und klicken Sie auf **[!UICONTROL Send Email]**.
1. Führen Sie denselben Schritt für *Gutschrift* und *Versand* durch Klicken auf **[!UICONTROL Send Email]** aus.

<u>Erwartete Ergebnisse</u>:

Keine Fehler in `system.log`.

<u>Tatsächliche Ergebnisse</u>:

`system.log` ist mit *main.ERROR: Die Verschachtelung der Umgebungsemulation ist nicht zulässig* Fehler.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

[[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
