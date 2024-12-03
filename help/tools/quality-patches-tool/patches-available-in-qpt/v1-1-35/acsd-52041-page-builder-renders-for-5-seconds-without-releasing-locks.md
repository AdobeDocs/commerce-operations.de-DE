---
title: 'ACSD-52041: Beim Rendern von Seiten-Builder werden keine Sperren veröffentlicht'
description: Wenden Sie den Patch ACSD-52041 an, um das Adobe Commerce-Problem zu beheben, bei dem der Seitenaufbau fünf Sekunden lang gerendert wird, ohne Sperren zu veröffentlichen.
feature: Page Builder
role: Admin, Developer
exl-id: 48a7fc36-e98a-4a4e-bed3-248d7d73f6cb
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-52041: Beim Rendern von Seiten-Builder werden keine Sperren veröffentlicht

Der Patch ACSD-52041 behebt das Problem, bei dem der Seitenaufbau fünf Sekunden lang gerendert wird, ohne Sperren freizugeben. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.48 installiert ist. Die Patch-ID ist ACSD-52041-v2. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p5, 2.4.5 - 2.4.5-p4 und 2.4.6 - 2.4.6-p2.



>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.


## Problem

Der **[!DNL Page Builder]** rendert für *5* Sekunden, ohne die Sperren zu lösen.

<u>Zu reproduzierende Schritte</u>:

1. Bearbeiten Sie eine CMS-Seite, Produktseite oder alles, was über **[!DNL Page Builder]** verfügt.
1. Speichern Sie die Änderungen.
1. Beachten Sie die Seitenspeicherzeit.

<u>Erwartete Ergebnisse</u>

Der Inhalt wird gespeichert. Im Browserprotokoll werden keine Fehler gefunden.

<u>Tatsächliche Ergebnisse</u>

Das Speichern dauert länger als die übliche Zeit.
Fehler in Konsole: ``Page Builder was rendering for 5 seconds without releasing locks``

## Wenden Sie den Patch an

Um einzelne Patches für die Versionen **2.4.4 - 2.4.4-p5, 2.4.5 - 2.4.5-p4 und 2.4.6 - 2.4.6-p2** anzuwenden, verwenden Sie je nach Bereitstellungsmethode die folgenden Links:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](</help/tools/quality-patches-tool/usage.md>) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] -Handbuch.
