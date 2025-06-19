---
title: 'ACSD-52041: Beim Rendern von Page Builder werden keine Sperren freigegeben'
description: Wenden Sie den Patch ACSD-52041 an, um das Adobe Commerce-Problem zu beheben, bei dem Page Builder fünf Sekunden lang gerendert wird, ohne Sperren freizugeben.
feature: Page Builder
role: Admin, Developer
exl-id: 48a7fc36-e98a-4a4e-bed3-248d7d73f6cb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-52041: Beim Rendern von Page Builder werden keine Sperren freigegeben

Der Patch ACSD-52041 behebt das Problem, dass Page Builder fünf Sekunden lang gerendert wird, ohne Sperren freizugeben. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.48 installiert ist. Die Patch-ID lautet ACSD-52041-v2. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p5, 2.4.5 - 2.4.5-p4 und 2.4.6 - 2.4.6-p2.



>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.


## Problem

Die **[!DNL Page Builder]** wird für *5 Sekunden gerendert* ohne die Sperren zu lösen.

<u>Schritte zur Reproduktion</u>:

1. Bearbeiten Sie eine CMS-Seite, eine Produktseite oder alles, was **[!DNL Page Builder]** hat.
1. Speichern Sie die Änderungen.
1. Beachten Sie, dass die Seite Zeit spart.

<u>Erwartete Ergebnisse</u>

Der Inhalt wird gespeichert. Im Browser-Protokoll wurden keine Fehler gefunden.

<u>Tatsächliche Ergebnisse</u>

Das Speichern dauert länger als sonst üblich.
Fehler in der Konsole: ``Page Builder was rendering for 5 seconds without releasing locks``

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches für die Versionen **2.4.4 - 2.4.4-p5, 2.4.5 - 2.4.5-p4 und 2.4.6 - 2.4.6-p2** anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de>) im [!DNL Quality Patches Tool].
