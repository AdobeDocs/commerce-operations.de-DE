---
title: 'ACSD-51358: Zeitplanaktualisierungen fehlen'
description: Wenden Sie den ACSD-51358 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem Änderungen an der geplanten Aktualisierung ohne Enddatum dazu führen, dass andere geplante Aktualisierungen in derselben Entität entfernt werden.
feature: Staging
role: Admin, Developer
exl-id: 6e2e598b-72f1-4f00-a989-3f75bf65f8f0
source-git-commit: 1a78b2afa6e751d430700e72f512f7d82d1c1bdd
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51358: Zeitplanaktualisierungen fehlen

Mit dem Patch „ACSD-51358“ wird das Problem behoben, dass Änderungen an der geplanten Aktualisierung ohne Enddatum dazu führen, dass andere geplante Aktualisierungen in derselben Entität entfernt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.35 installiert ist. Die Patch-ID ist ACSD-51358. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Änderungen an geplanten Aktualisierungen ohne Enddatum führen dazu, dass andere geplante Aktualisierungen in derselben Entität entfernt werden.

<u>Schritte zur Reproduktion</u>:

1. **[!UICONTROL scheduled update]** ohne Enddatum erstellen (*aktualisieren 1*).
1. Erstellen Sie eine neue **[!UICONTROL scheduled update]** mit demselben Startdatum wie bei der ersten Aktualisierung, fügen Sie jedoch den nächsten Tag und das Enddatum hinzu (*2*).
1. Bearbeiten Sie **[!UICONTROL scheduled update]**, die in Schritt 1 (*Update 1*) erstellt wurden, und speichern Sie die Änderungen.

<u>Erwartete Ergebnisse</u>

(*Update 2*) sollte in der **[!UICONTROL schedule update]** bleiben, wenn (*Update 1*) bearbeitet wird.

<u>Tatsächliche Ergebnisse</u>

Das (*Update 2*) wurde aus der **[!UICONTROL schedule update]** entfernt, wenn (*Update 1*) bearbeitet wird.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de>) im [!DNL Quality Patches Tool].
