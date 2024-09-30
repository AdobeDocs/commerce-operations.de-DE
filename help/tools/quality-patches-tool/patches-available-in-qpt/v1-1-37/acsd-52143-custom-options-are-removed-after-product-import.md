---
title: "ACSD-52143: Benutzerdefinierte Optionen werden nach dem Produktimport entfernt"
description: Wenden Sie den Patch ACSD-52143 an, um das Adobe Commerce-Problem zu beheben, bei dem die Anpassungsoptionen nach dem Produktimport entfernt werden.
feature: Data Import/Export
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-52143: Benutzerdefinierte Optionen werden nach dem Produktimport entfernt

Der Patch ACSD-52143 behebt das Problem, dass die benutzerdefinierten Optionen nach dem Produktimport entfernt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.37 installiert ist. Die Patch-ID ist ACSD-52143. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die benutzerdefinierten Optionen werden nach dem Produktimport entfernt.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu &quot;**[!UICONTROL Store]**&quot;> &quot;**[!UICONTROL All Stores]**&quot;und richten Sie eine Instanz mit mehreren Stores ein (eine Website mit zwei Store-Ansichten).
1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und erstellen Sie zwei Produkte mit [!UICONTROL Customizable Options].
1. Fügen Sie jedem Produkt den Wert [!UICONTROL Customizable Option] hinzu.
1. Wechseln Sie zur zweiten Store-Ansicht und ändern Sie den Produktnamen für jedes Produkt.
1. Gehen Sie zu **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** und exportieren Sie die beiden von Ihnen erstellten Produkte.
1. Laden Sie die CSV-Datei herunter.
1. Gehen Sie zu **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** und importieren Sie die Datei erneut.
1. Überprüfen Sie beide Produkte.

<u>Erwartete Ergebnisse</u>:

Die benutzerdefinierten Optionen werden nach dem Produktimport nicht entfernt.

<u>Tatsächliche Ergebnisse</u>:

Die Zolloptionen werden nach der Einfuhr des Erzeugnisses entfernt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
