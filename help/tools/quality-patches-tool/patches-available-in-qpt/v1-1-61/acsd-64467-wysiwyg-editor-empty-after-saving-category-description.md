---
title: 'ACSD-64467: WYSIWYG-Editor nach dem Speichern der Kategoriebeschreibung auf Store-Ansichtsebene leer'
description: Wenden Sie den Patch ACSD-64467 an, um das Adobe Commerce-Problem zu beheben, bei dem der WYSIWYG-Editor nach dem Speichern einer Kategoriebeschreibung auf Store-Ansichtsebene leer erscheint.
feature: Page Content
role: Admin, Developer
exl-id: 8bc1794f-ace1-4719-9fff-194dbd701ab6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# ACSD-64467: WYSIWYG-Editor nach dem Speichern der Kategoriebeschreibung auf Store-Ansichtsebene leer

Mit dem Patch ACSD-64467 wird das Problem behoben, dass der WYSIWYG-Editor nach dem Speichern einer Kategoriebeschreibung auf Store-Ansichtsebene leer erscheint. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 installiert ist. Die Patch-ID ist ACSD-64467. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der WYSIWYG-Editor wird nach dem Speichern einer Kategoriebeschreibung auf Store-Ansichtsebene leer angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Bearbeiten Sie eine Kategorie in der Commerce Admin auf Store-Ansichtsebene.
1. Deaktivieren Sie das Kontrollkästchen *[!UICONTROL Use default value]* neben der Kategoriebeschreibung.
1. Geben Sie im WYSIWYG-Editor eine Beschreibung ein.
1. Klicken Sie auf **[!UICONTROL Save]**.

<u>Erwartete Ergebnisse</u>:

Die Beschreibung wird gespeichert und ordnungsgemäß angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die Beschreibung ist nach dem Neuladen der Seite leer.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
