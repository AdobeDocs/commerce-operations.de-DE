---
title: 'ACSD-53414: Eingeschränkte Administratoren können CMS-Seiten außerhalb ihres Berechtigungsbereichs anzeigen.'
description: Wenden Sie den Patch ACSD-53414 an, um das Adobe Commerce-Problem zu beheben, bei dem ein eingeschränkter Administrator CMS-Seiten außerhalb des Berechtigungsbereichs anzeigen kann.
feature: CMS
role: Admin, Developer
exl-id: 86658336-679b-4fe0-9d26-56064ff0c604
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-53414: Eingeschränkte Administratoren können CMS-Seiten außerhalb ihres Berechtigungsbereichs anzeigen.

Der Patch ACSD-53414 behebt das Problem, dass ein eingeschränkter Administrator CMS-Seiten außerhalb des Berechtigungsbereichs anzeigen kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 installiert ist. Die Patch-ID ist ACSD-53414. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eingeschränkte Admin-Benutzer können CMS-Seiten über ihren Berechtigungsbereich hinaus anzeigen.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue Website (sub_website), speichern Sie (sub_store) und speichern Sie die Vorschau (sub_storeview).
1. Erstellen Sie eine Rolle &quot;sub_experte&quot;, die den Umfang von sub_website und sub_store zulässt. Weisen Sie nur die folgenden Berechtigungen zu: [!UICONTROL Dashboard] und [!UICONTROL Pages].
1. Erstellen Sie einen neuen Admin-Benutzer und weisen Sie ihn der Rolle sub_experte zu.
1. Weisen Sie die folgenden CSM-Seiten zu &quot;sub_storeview&quot;und &quot;default storeview&quot;zu.

   * [!UICONTROL 404 Not Found] > Unterspeicher
   * [!UICONTROL 503 Service Unavailable] > Standardmäßige Storeübersicht

1. Melden Sie sich mit dem in Schritt 3 erstellten Admin-Benutzer bei Admin an.
1. Überprüfen Sie das CMS-Seitenraster.

<u>Erwartete Ergebnisse</u>:

Die Seite &quot;*[!UICONTROL 503 Service Unavailable]*&quot; ist für den Webadministrator nicht sichtbar.

<u>Tatsächliche Ergebnisse</u>:

*[!UICONTROL 503 Service Unavailable]* ist für den Webadministrator sichtbar.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
