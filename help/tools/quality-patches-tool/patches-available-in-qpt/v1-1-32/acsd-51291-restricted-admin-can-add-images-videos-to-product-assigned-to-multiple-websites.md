---
title: 'ACSD-51291: Administratoren mit Zugriffsbeschränkung können Bilder/Videos zu Produkten hinzufügen, die mehreren Websites zugewiesen sind'
description: Wenden Sie den ACSD-51291-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem Administratoren mit beschränktem Zugriff auf eine Website Bilder/Videos zu einem Produkt hinzufügen können, das mehreren Websites zugewiesen ist.
feature: Admin Workspace, Products, Page Content
role: Admin
exl-id: a4edd034-f718-4559-9993-11609f0d0efa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-51291: Administratoren mit Zugriffsbeschränkung können Bilder/Videos zu Produkten hinzufügen, die mehreren Websites zugewiesen sind

Mit dem Patch ACSD-51291 wird das Problem behoben, dass ein Admin mit Zugriffsbeschränkung auf eine Website Bilder/Videos zu einem Produkt hinzufügen kann, das mehreren Websites zugewiesen ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32 installiert ist. Die Patch-ID ist ACSD-51291. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p3, 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein Admin mit Zugriffsbeschränkung auf eine Website kann Bilder/Videos zu einem Produkt hinzufügen, das mehreren Websites zugewiesen ist.

<u>Schritte zur Reproduktion</u>

1. Melden Sie sich als Administrator an.
1. Erstellen Sie eine zweite Website-, Store- und Store-Ansicht.
1. Erstellen Sie eine zweite Administratorrolle mit Ressourcen nur für die zweite Website-, Store- und Store-Ansicht.
1. Erstellen Sie einen zweiten Administrator und weisen Sie ihn der neuen eingeschränkten Administratorrolle zu.
1. Erstellen Sie ein neues Produkt und weisen Sie es sowohl der Standard- als auch der neuen Website zu.
1. Melden Sie sich beim Hauptadministratorprofil ab.
1. Melden Sie sich als neuer eingeschränkter Administrator an.
1. Bearbeiten Sie das erstellte Produkt, das beiden Websites zugewiesen wurde.
1. Öffnen Sie die Registerkarte **[!UICONTROL Images and Videos]** .

<u>Erwartete Ergebnisse</u>:

* Die folgende Meldung wird angezeigt:

  *Ein eingeschränkter Administrator darf Aktionen mit Bildern oder Videos nur dann durchführen, wenn der Administrator über Rechte für alle Websites verfügt, denen das Produkt zugewiesen ist.*

* Die Schaltfläche &quot;**[!UICONTROL Add Video]**&quot; ist nicht aktiv.

<u>Tatsächliche Ergebnisse</u>:

Der Admin mit Zugriffsbeschränkung kann Bilder und Videos hinzufügen, selbst wenn das Produkt einer Website zugewiesen ist, auf die er keinen Zugriff hat.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
