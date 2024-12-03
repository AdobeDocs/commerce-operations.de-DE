---
title: 'ACSD-53722: Preisänderungen bei gebündelten Produktoptionen auf 0 USD'
description: Wenden Sie den Patch ACSD-53722 an, um das Adobe Commerce-Problem zu beheben, bei dem sich der Preis der gebündelten Produktoptionen auf 0 USD ändert, wenn geplante Aktualisierungen für verschiedene Bereiche aktiv werden.
feature: Products
role: Admin, Developer
exl-id: 2e974a6a-0c79-442f-9b45-b4edf831a052
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-53722: Preisänderungen bei gebündelten Produktoptionen auf 0 USD

Der Patch ACSD-53722 behebt das Problem, dass der Preis der gebündelten Produktoptionen auf 0 USD geändert wird, wenn geplante Aktualisierungen für verschiedene Bereiche aktiv werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41 installiert ist. Die Patch-ID ist ACSD-53722. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Preis für gebündelte Produktoptionen ändert sich in 0 USD, wenn geplante Updates für verschiedene Bereiche aktiv werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei Websites, A und B.
1. Legen Sie die Konfiguration unter **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]** = **[!UICONTROL Website]** fest.
1. Erstellen Sie ein gebündeltes Produkt mit einem Festpreis auf den Websites A und B:

   * Gebündelter Produktpreis = Fester Wert = *0*

1. Fügen Sie ein einfaches Produkt als Dropdownoption für das Bundle hinzu. Legen Sie die folgenden Preise fest:

   * Der Preis für alle Store-Ansichten des einfachen Produkts innerhalb der gebündelten Option = *120*
   * Website des einfachen Produkts Ein Preis innerhalb der gebündelten Option = *130*
   * Website-Preis B des einfachen Produkts innerhalb der gebündelten Option = *140*

1. Planen Sie ein Update, um das gebündelte Produkt auf Website A zu deaktivieren.

<u>Erwartete Ergebnisse</u>:

Geplantes Update für Website A hat keine Auswirkungen auf den Preis von Website B.

<u>Tatsächliche Ergebnisse</u>:

Nach der geplanten Aktualisierung wird der Preis der gebündelten Produktoption auf Website B in **$0** geändert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
