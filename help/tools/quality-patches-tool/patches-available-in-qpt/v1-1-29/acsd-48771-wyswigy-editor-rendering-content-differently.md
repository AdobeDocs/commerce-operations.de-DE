---
title: "ACSD-48771: Der WYSIWYG-Editor rendert Inhalte unterschiedlich"
description: Wenden Sie den Patch ACSD-48771 an, um das Adobe Commerce-Problem zu beheben, bei dem der WYSIWYG-Editor Inhalte anders rendert.
feature: Cache, Page Content
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-48771: WYSIWYG-Editor rendert Inhalte unterschiedlich

Der Patch ACSD-48771 behebt das Problem, dass der WYSIWYG-Editor Inhalte anders rendert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 installiert ist. Die Patch-ID ist ACSD-48771. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der WYSIWYG-Editor rendert Inhalte unterschiedlich.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zum Adobe Commerce-Administrator, erstellen Sie eine neue Seite mit einer Zeile mit drei Spalten und speichern Sie die Seite.
1. Aktualisieren Sie Adobe Commerce auf eine der neuesten Versionen.
1. Setzen Sie den Browser [!DNL Chrome] , um Cache und Geschwindigkeit auf *Fast 3G* zu deaktivieren.
1. Gehen Sie erneut zur Bearbeitungsseite und aktualisieren Sie sie, bis die Spalten Zeilen werden.
1. Speichern Sie die Seite, während sich die Spalten in Zeilen befinden.

<u>Erwartete Ergebnisse</u>:

Der Admin-Seiten-Builder sollte keine Spalten in Zeilen anzeigen.

<u>Tatsächliche Ergebnisse</u>:

Spalten werden in verschiedenen Zeilen angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
