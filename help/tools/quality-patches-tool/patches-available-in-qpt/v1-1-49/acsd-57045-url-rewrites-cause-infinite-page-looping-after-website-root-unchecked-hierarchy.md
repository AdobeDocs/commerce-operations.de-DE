---
title: 'ACSD-57045: URL-Neuschreibungen verursachen unendliche Seitenschleifen, nachdem [!UICONTROL Website Root] von [!UICONTROL Hierarchy] deaktiviert wurde.'
description: Wenden Sie den Patch ACSD-57045 an, um das Adobe Commerce-Problem zu beheben, bei dem URL-Neuschreibungen zu unendlichen Seitenschleifen führen, nachdem [!UICONTROL Website Root] von [!UICONTROL Hierarchy] deaktiviert wurde.
feature: CMS
role: Admin, Developer
source-git-commit: 52742cbc2098958f8e4cddf8534e0c2bf79d5c3e
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---


# ACSD-57045: URL-Neuschreibungen verursachen unendliche Seitenschleife, nachdem [!UICONTROL Website Root] von [!UICONTROL Hierarchy] deaktiviert wurde

Der Patch ACSD-57045 behebt das Problem, dass URL-Neuschreibungen dazu führen, dass unendliche Seitenschleifen nach **[!UICONTROL Website Root]** von **[!UICONTROL Hierarchy]** deaktiviert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49 installiert ist. Die Patch-ID ist ACSD-57045. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.5.0 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

URL-Neuschreibungen führen dazu, dass unendliche Seitenschleifen nach **[!UICONTROL Website Root]** von **[!UICONTROL Hierarchy]** deaktiviert wird.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine CMS-Seite mit dem Namen *Test-Parent*.
1. Erstellen Sie eine Seite mit dem Namen *Test-Child*, wählen Sie im Abschnitt **[!UICONTROL Hierarchy]** **[!UICONTROL Website Root]** > **[!UICONTROL Parent]** aus und speichern Sie.
1. Gehen Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**.
1. Beachten Sie, dass es zwei neue Neuschreibungen gibt:
   * Anfragepfad zu *Test-Parent* , der auf *cms/page/view/page_id/ID_NUMBER_FOR_PAGE* verweist
   * Anfragepfad zu *Test-Child* , der auf *cms/page/view/page_id/ID_NUMBER_FOR_PAGE* verweist
1. Besuchen Sie die Storefront und fügen Sie *test-child* zur URL hinzu. Sie sollten die untergeordnete Seite sehen.
1. Tun Sie dasselbe, aber fügen Sie *test-parent/test-child/* zur URL hinzu und sehen Sie dieselbe Seite.
1. Gehen Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]** und wählen Sie **[!UICONTROL Add URL Rewrite]** aus. Wählen Sie die folgenden Einstellungen aus:
   * Typ: *Benutzerdefiniert*
   * Anfragepfad: *test-parent/test-child*
   * Zielpfad: *test-child*
   * Umleitungstyp: *Dauerhaft (301)*
1. Besuchen Sie den Pfad *test-parent/test-child* und Sie sollten zu *test-child* umgeleitet werden.
1. Bearbeiten Sie die untergeordnete Seite (**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** > Untergeordnetes Element auswählen und wählen Sie **[!UICONTROL Edit]**).
1. Behalten Sie unter dem Abschnitt **[!UICONTROL Hierarchy]** die Option *Test-Parent* bei, heben Sie jedoch die Auswahl von **[!UICONTROL Website Root]** auf und speichern Sie.
1. Navigieren Sie zu &quot;**[!UICONTROL Marketing]**&quot;> &quot;**[!UICONTROL URL Rewrites]**&quot; und beachten Sie, dass die ursprüngliche Umleitung &quot;*test-child*&quot;zu &quot;*cms/page/view/page_id*&quot;fehlt und an dieser Stelle durch einen Pfad ersetzt wird, der den Pfad &quot;*test-child*&quot;auf &quot;*test-parent/test-child*&quot;verweist.
1. Besuchen Sie die Storefront und versuchen Sie, die Seite *Test-Child* zu besuchen.

<u>Erwartete Ergebnisse</u>:

Die Seite *Test-Child* wird geöffnet.

<u>Tatsächliche Ergebnisse</u>:

Die Seite *Test-Child* wird nicht geöffnet. Der Browser versucht, die Seite *test-parent/test-child* in einer Endlosschleife zu öffnen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
