---
title: 'ACSD-61785: Die Aktualisierung des Attributs reward_warning_notification über GraphQL-Mutation und REST-API-Aufrufe ist nicht möglich'
description: Wenden Sie den Patch ACSD-61785 an, um das Adobe Commerce-Problem zu beheben, bei dem eine Aktualisierung des Attributs "reward_warning_notification"über GraphQL-Mutation- und REST-API-Aufrufe nicht möglich ist.
feature: REST, GraphQL, Rewards
role: Admin, Developer
source-git-commit: 87ce6004a632f860447d55c13c08f78533ab093e
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61785: Die Aktualisierung des Attributs reward_warning_notification über GraphQL-Mutation und REST-API-Aufrufe ist nicht möglich

Der Patch ACSD-61785 behebt das Problem, dass eine Aktualisierung des `reward_warning_notification` -Attributs über GraphQL-Mutation und REST-API-Aufrufe nicht möglich ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-61785. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Aktualisierung des Attributs `reward_warning_notification` ist über GraphQL-Mutation und REST-API-Aufrufe nicht möglich.

<u>Zu reproduzierende Schritte</u>:

1. Überprüfen Sie das GraphQL- und REST-API-Schema/-Dokumentation für *Abonnieren von Statusaktualisierungen* und *Abonnieren von Benachrichtigungen zum Ablauf von Punkten*.

<u>Erwartete Ergebnisse</u>:

Es ist möglich, über GraphQL und die REST-API für *Bonusbilanzaktualisierungen* und für *Punkteablaufbenachrichtigungen* zu Abonnement zu gehen.

<u>Tatsächliche Ergebnisse</u>:

GraphQL und REST API verfügen nicht über diese Funktionalität.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
