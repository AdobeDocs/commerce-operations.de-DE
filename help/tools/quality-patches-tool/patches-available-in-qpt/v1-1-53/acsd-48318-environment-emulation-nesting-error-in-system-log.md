---
title: 'ACSD-48318: Verschachtelungsfehler bei der Umgebungsemulation in „system.log“'
description: Wenden Sie den Patch ACSD-48318 an, um das Adobe Commerce-Problem zu beheben, bei dem jedes Mal, wenn eine Rechnungs-E-Mail gesendet wird, eine Fehlermeldung in „system.log“ angezeigt wird, in der die Verschachtelung der Umgebungsemulation *main.ERROR:Environment nicht zulässig* ist.
feature: System, Orders
role: Admin, Developer
exl-id: 24af18de-80dd-4e0a-bdf9-5b9c075fc608
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
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
source-wordcount: '329'
ht-degree: 0%
---
# ACSD-48318: Verschachtelungsfehler bei der Umgebungsemulation in `system.log`

Der Patch ACSD-48318 behebt das Problem, dass eine Fehlermeldung *main.ERROR:Environment Emulationsverschachtelung nicht zulässig ist* jedes Mal in `system.log` angezeigt wird, wenn eine Rechnung per E-Mail gesendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 installiert ist. Die Patch-ID ist ACSD-48318. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

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
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

[[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
