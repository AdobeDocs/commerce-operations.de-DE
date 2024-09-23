---
title: "ACSD-51291: Eingeschränkte Administratoren können Bildern/Videos zu Produkten hinzufügen, die mehreren Websites zugewiesen sind"
description: Wenden Sie den Patch ACSD-51291 an, um das Adobe Commerce-Problem zu beheben, bei dem eingeschränkte Administratoren mit Zugriff auf eine Website Bilder/Videos zu einem Produkt hinzufügen können, das mehreren Websites zugewiesen ist.
feature: Admin Workspace, Products, Page Content
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# ACSD-51291: Eingeschränkte Administratoren können Bildern/Videos zu Produkten hinzufügen, die mehreren Websites zugewiesen sind

Der Patch ACSD-51291 behebt das Problem, dass ein eingeschränkter Administrator mit Zugriff auf eine Website Bilder/Videos zu einem Produkt hinzufügen kann, das mehreren Websites zugewiesen ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.32 installiert ist. Die Patch-ID ist ACSD-51291. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p3, 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein eingeschränkter Administrator mit Zugriff auf eine Website kann einem Produkt, das mehreren Websites zugewiesen ist, Bilder/Videos hinzufügen.

<u>Zu reproduzierende Schritte</u>

1. Melden Sie sich als Administrator an.
1. Erstellen Sie eine zweite Website-, Store- und Store-Ansicht.
1. Erstellen Sie eine zweite Administratorrolle mit Ressourcen, die nur für die zweite Website-, Store- und Store-Ansicht verwendet werden.
1. Erstellen Sie einen zweiten Administrator und weisen Sie ihn der neuen eingeschränkten Administratorrolle zu.
1. Erstellen Sie ein neues Produkt und weisen Sie es sowohl den standardmäßigen als auch den neuen Websites zu.
1. Melden Sie sich vom Hauptadministrator ab.
1. Melden Sie sich als neuer eingeschränkter Administrator an.
1. Bearbeiten Sie das erstellte Produkt, das beiden Websites zugewiesen wurde.
1. Öffnen Sie die Registerkarte **[!UICONTROL Images and Videos]** .

<u>Erwartete Ergebnisse</u>:

* Die folgende Meldung wird angezeigt:

  *Der eingeschränkte Administrator darf nur dann Aktionen mit Bildern oder Videos durchführen, wenn der Administrator über Berechtigungen für alle Websites verfügt, denen das Produkt zugewiesen ist.*

* Die Schaltfläche **[!UICONTROL Add Video]** ist nicht aktiv.

<u>Tatsächliche Ergebnisse</u>:

Der eingeschränkte Administrator kann Bilder und Videos hinzufügen, selbst wenn das Produkt einer Website zugewiesen ist, auf die er keinen Zugriff hat.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
