---
title: 'ACSD-66965: [!UICONTROL Print] Option auf [!UICONTROL Requisition List] Seite verursacht einen Fehler'
description: Wenden Sie den Patch ACSD-66965 an, um ein Problem in Adobe Commerce zu beheben, bei dem die Option [!UICONTROL Print] auf der [!UICONTROL Requisition List] einen Fehler verursacht.
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7682a326a6c703a08dd6d0fac5319ac38e1bc3c8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# ACSD-66965: **[!UICONTROL Print]** Option auf **[!UICONTROL Requisition List]** Seite verursacht einen Fehler

Der Patch ACSD-66965 behebt das Problem, dass die Option **[!UICONTROL Print]** auf der Seite **[!UICONTROL Requisition List]** einen Fehler verursacht. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 installiert ist. Die Patch-ID ist ACSD-66965. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

**[!UICONTROL Print]** Option auf der Seite **[!UICONTROL Requisition List]** verursacht einen Fehler aufgrund eines Null-Objektverweises in `Grid.php`.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Legen Sie **[!UICONTROL Enable Company]**, **[!UICONTROL Enable Shared Catalog]** und **[!UICONTROL Enable Requisition List]** auf `Yes` fest.
1. Erstellen Sie zwei einfache Produkte.
1. Melden Sie sich bei der Storefront an und öffnen Sie die **[!UICONTROL My Account]**.
1. Anforderungsliste erstellen.
1. Beide Produkte der Anforderungsliste zuweisen.
1. Rufen Sie die Anforderungsliste auf und listen Sie die Produkte auf.
1. Klicken Sie auf **[!UICONTROL Print]**.

<u>Erwartete Ergebnisse</u>:

Mit der Option **[!UICONTROL Print]** auf der Seite **[!UICONTROL Requisition List]** wird die Druckvorschau ohne Fehler angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die folgende Fehlermeldung wird angezeigt: *Während der Ausführung der Anwendung ist ein Fehler aufgetreten. Weitere Informationen finden Sie im Ausnahmenprotokoll.*

```
Call to a member function setCollection() on null in /vendor/magento/module-requisition-list/Block/Requisition/View/Items/Grid.php:146
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
