---
title: "ACSD-56515: Admin mit Berechtigungen auf Website-Ebene kann [!UICONTROL Dynamic Block] nicht bearbeiten."
description: Wenden Sie den Patch ACSD-56515 an, um das Adobe Commerce-Problem zu beheben, bei dem der Administrator mit Berechtigungen auf Website-Ebene die [!UICONTROL Dynamic Block] nicht hinzufügen oder bearbeiten kann.
feature: Roles/Permissions, Admin Workspace
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-56515: Administrator mit Berechtigungen auf Website-Ebene kann [!UICONTROL Dynamic Block] nicht bearbeiten

Der Patch ACSD-56515 behebt das Problem, dass der Administrator mit Berechtigungen auf Website-Ebene die [!UICONTROL Dynamic Block] nicht hinzufügen oder bearbeiten kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45 installiert ist. Die Patch-ID ist ACSD-56515. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Administrator mit Berechtigungen auf Website-Ebene kann die [!UICONTROL Dynamic Block] nicht hinzufügen oder bearbeiten.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine sekundäre Website mit Store und Store-Überprüfung.
1. Gehen Sie zu **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]** und erstellen Sie eine Benutzerrolle, die auf den sekundären Website-Bereich beschränkt ist und alle verfügbaren Ressourcen enthält.
1. Erstellen Sie einen Admin-Benutzer mit der oben erstellten Rolle.
1. Melden Sie sich mit dem eingeschränkten Administratorbenutzer an und erstellen Sie einen [!UICONTROL Dynamic Block].

<u>Erwartete Ergebnisse</u>:

Der Admin-Benutzer mit Einschränkungen für die Website kann einen [!UICONTROL Dynamic Block] erstellen.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den folgenden Fehler: *Mehr Berechtigungen sind erforderlich, um dieses Element anzuzeigen*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
