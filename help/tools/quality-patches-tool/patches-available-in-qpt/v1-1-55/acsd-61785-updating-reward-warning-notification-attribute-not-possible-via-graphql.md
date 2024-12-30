---
title: 'ACSD-61785: Aktualisieren des Attributs reward_warning_notification über GraphQL-Mutation und REST-API-Aufrufe nicht möglich'
description: Wenden Sie den Patch ACSD-61785 an, um das Adobe Commerce-Problem zu beheben, bei dem die Aktualisierung des Attributs „reward_warning_notification“ nicht über GraphQL-Mutation und REST-API-Aufrufe möglich ist.
feature: REST, GraphQL, Rewards
role: Admin, Developer
exl-id: 41f40452-4240-4b4a-b1bc-0da23139f19f
source-git-commit: c1d3d3056d1ee3c33db6c14ed10a1df08f962795
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61785: Aktualisieren des Attributs reward_warning_notification über GraphQL-Mutation und REST-API-Aufrufe nicht möglich

Mit dem Patch „ACSD-61785“ wird das Problem behoben, dass die Aktualisierung des `reward_warning_notification` nicht über GraphQL-Mutations- und REST-API-Aufrufe möglich ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-61785. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Aktualisieren des `reward_warning_notification`-Attributs ist über GraphQL-Mutations- und REST-API-Aufrufe nicht möglich.

<u>Schritte zur Reproduktion</u>:

1. Lesen Sie GraphQL- und REST-API-Schema/-Dokumentation für *Abonnieren von Saldenaktualisierungen* und *Abonnieren von Punkteablaufbenachrichtigungen*.

<u>Erwartete Ergebnisse</u>:

Es ist möglich, *Rewards-Saldo-Updates* und für *Benachrichtigungen zum Ablauf von Punkten* über die GraphQL- und REST-API zu abonnieren.

<u>Tatsächliche Ergebnisse</u>:

Diese Funktionalität fehlt GraphQL und der REST-API.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
