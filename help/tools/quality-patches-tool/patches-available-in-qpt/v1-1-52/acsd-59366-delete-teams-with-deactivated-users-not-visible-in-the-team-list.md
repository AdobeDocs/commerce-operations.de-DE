---
title: "ACSD-59366: Löschen von Teams mit deaktivierten Benutzern, die nicht in der Teamliste angezeigt werden"
description: Wenden Sie den Patch ACSD-59366 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Versuch, ein Team zu löschen, das deaktivierte Benutzer enthält, die nicht in der Teamliste angezeigt werden, ein Fehler auftritt.
feature: GraphQL, Companies
role: Admin, Developer
source-git-commit: 8037db7a89cd850385dc88750e881f68ae62172f
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-59366: Löschen von Teams mit deaktivierten Benutzern, die nicht in der Teamliste angezeigt werden

Der Patch ACSD-59366 behebt das Problem, bei dem ein Fehler auftritt, wenn Sie versuchen, ein Team zu löschen, das deaktivierte Benutzer enthält, die nicht in der Teamliste sichtbar sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52 installiert ist. Die Patch-ID ist ACSD-59366. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.4.8 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein Fehler tritt auf, wenn Sie ein Team löschen, das deaktivierte Benutzer enthält, die nicht in der Teamliste angezeigt werden.

<u>Voraussetzungen</u>:

Adobe Commerce-B2B-Module werden installiert und Unternehmen sind aktiviert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen und melden Sie sich mit einem Unternehmensbenutzer an.
1. Erstellen Sie unter Unternehmensstruktur ein neues Team.
1. Erstellen Sie unter dem neuen Team einen neuen Benutzer.
1. Bearbeiten und deaktivieren Sie den neuen Benutzer.
1. Wählen Sie das Team aus und löschen Sie es.

<u>Erwartete Ergebnisse</u>:

Das Team hat einen oder mehrere inaktive Benutzer. Durch das Löschen des Teams wird die Zuweisung dieser Benutzer aufgehoben. Inaktive Benutzer finden Sie im Abschnitt [!UICONTROL Company Users] .

<u>Tatsächliche Ergebnisse</u>:

Ein Fehler tritt auf, wenn Sie versuchen, ein Team mit einem deaktivierten Benutzer zu löschen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.


