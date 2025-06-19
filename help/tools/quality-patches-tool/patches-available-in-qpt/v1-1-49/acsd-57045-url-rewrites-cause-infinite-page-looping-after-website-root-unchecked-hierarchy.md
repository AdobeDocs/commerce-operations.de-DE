---
title: 'ACSD-57045: URL-Neuschreibungen führen zu unendlicher Seitenschleife, nachdem [!UICONTROL Website Root] von [!UICONTROL Hierarchy] deaktiviert wurde'
description: Wenden Sie den Patch ACSD-57045 an, um das Adobe Commerce-Problem zu beheben, bei dem URL-Neuschreibungen zu unendlicher Seitenschleife führen, nachdem [!UICONTROL Website Root] in der [!UICONTROL Hierarchy] deaktiviert wurde.
feature: CMS
role: Admin, Developer
exl-id: 7beaee40-a392-4644-917e-c507e79bddcc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# ACSD-57045: URL-Neuschreibungen führen zu unendlicher Seitenschleife, nachdem [!UICONTROL Website Root] von [!UICONTROL Hierarchy] deaktiviert wurde

Der Patch ACSD-57045 behebt das Problem, dass URL-Neuschreibungen zu unendlicher Seitenschleife führen, nachdem **[!UICONTROL Website Root]** für **[!UICONTROL Hierarchy]** deaktiviert wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49 installiert ist. Die Patch-ID ist ACSD-57045. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.5.0 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

URL-Neuschreibungen führen zu einer unendlichen Seitenschleife, nachdem **[!UICONTROL Website Root]** für die **[!UICONTROL Hierarchy]** deaktiviert wurde.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine CMS-Seite mit dem Namen *Test-Parent*.
1. Erstellen Sie eine Seite mit *Namen „Test* Child“ und wählen Sie im Abschnitt **[!UICONTROL Hierarchy]** die Option **[!UICONTROL Website Root]** > **[!UICONTROL Parent]** aus.
1. Navigieren Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**.
1. Beachten Sie, dass es zwei neue Neuschreibungen gibt:
   * Anfragepfad an *Test-Parent*, der auf *cms/page/view/page_id/ID_NUMBER_FOR_PAGE verweist*
   * Anfragepfad an *Test-Child*, der auf *cms/page/view/page_id/ID_NUMBER_FOR_PAGE verweist*
1. Besuchen Sie die Storefront und fügen Sie *test-child* zur URL hinzu. Sie sollten die untergeordnete Seite sehen.
1. Tun Sie dasselbe, fügen Sie jedoch *test-parent/test-child/* zur URL hinzu und sehen Sie dieselbe Seite.
1. Navigieren Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]** und wählen Sie **[!UICONTROL Add URL Rewrite]**. Wählen Sie die folgenden Einstellungen aus:
   * Typ: *custom*
   * Anfragepfad: *test-parent/test-child*
   * Zielpfad: *test-child*
   * Umleitungstyp: *permanent (301)*
1. Besuchen Sie den *test-parent/test-child* Pfad und Sie sollten zu &quot;*-child“*.
1. Bearbeiten Sie die untergeordnete Seite (**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** > Untergeordnetes Element auswählen und **[!UICONTROL Edit]** auswählen).
1. Lassen Sie im Abschnitt **[!UICONTROL Hierarchy]** die Option *Test-Parent* ausgewählt, heben Sie jedoch die Auswahl **[!UICONTROL Website Root]** auf und speichern Sie.
1. Wechseln Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]** und beachten Sie, dass das ursprüngliche *test-child*-to-*cms/page/view/page_id*-redirect fehlt. An diesem Punkt wird es durch einen Pfad ersetzt, der *test-child* auf *test-parent/test-child* verweist.
1. Besuchen Sie die Storefront und versuchen Sie, die Seite *Test-Child* aufzurufen.

<u>Erwartete Ergebnisse</u>:

Die Seite *Test-Child* wird geöffnet.

<u>Tatsächliche Ergebnisse</u>:

Die *Test-Child*-Seite wird nicht geöffnet. Der Browser versucht, die Seite *test-parent/test-child* in einer Endlosschleife zu öffnen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
