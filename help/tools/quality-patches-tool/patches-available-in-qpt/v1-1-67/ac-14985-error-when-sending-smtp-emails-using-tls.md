---
title: 'AC-14985: Fehler beim Senden von SMTP-E-Mails mit TLS'
description: Wenden Sie den AC-14985-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem beim Senden von SMTP-E-Mails (Simple Mail Transfer Protocol) mit Transport Layer Security (TLS) ein Fehler auftritt.
feature: Configuration
role: Admin, Developer
type: Troubleshooting
exl-id: 98d91421-ebfd-4414-ade3-f25d29541874
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
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
source-wordcount: '311'
ht-degree: 0%
---
# AC-14985: Fehler beim Senden von SMTP-E-Mails mit TLS

Der AC-14985 Patch behebt ein Problem, bei dem beim Senden von SMTP-E-Mails (Simple Mail Transfer Protocol) mit Transport Layer Security (TLS) ein Fehler auftritt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 installiert ist. Die Patch-ID ist AC-14985. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Senden von E-Mails über SMTP mit aktiviertem TLS tritt ein Fehler auf.

<u>Schritte zur Reproduktion</u>:

1. Richten Sie die SMTP-Konfiguration wie folgt ein:
* Transport: SMTP
* Host: url.to.smtp.host
* Port: 587
* SSL: TLS

<u>Erwartete Ergebnisse</u>:

Die E-Mail wird fehlerfrei gesendet.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler wird angezeigt:

```text
error:1408F10B:SSL routines:ssl3_get_record:wrong version number [] []
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
