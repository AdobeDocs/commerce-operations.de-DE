---
title: 'ACSD-51358: Zeitplanaktualisierungen fehlen'
description: Wenden Sie den Patch ACSD-51358 an, um das Adobe Commerce-Problem zu beheben, bei dem Änderungen bei der geplanten Aktualisierung ohne Enddatum dazu führen, dass andere geplante Aktualisierungen für dieselbe Entität entfernt werden.
feature: Staging
role: Admin, Developer
exl-id: 6e2e598b-72f1-4f00-a989-3f75bf65f8f0
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51358: Zeitplanaktualisierungen fehlen

Der Patch ACSD-51358 behebt das Problem, dass Änderungen bei geplanten Aktualisierungen ohne Enddatum dazu führen, dass andere geplante Aktualisierungen für dieselbe Entität entfernt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.35 installiert ist. Die Patch-ID ist ACSD-51358. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Änderungen bei der geplanten Aktualisierung ohne Enddatum führen dazu, dass andere geplante Aktualisierungen für dieselbe Entität entfernt werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen **[!UICONTROL scheduled update]** -Wert ohne Enddatum (*update 1*).
1. Erstellen Sie einen neuen **[!UICONTROL scheduled update]** -Wert mit demselben Startdatum wie das erste Update, fügen Sie jedoch den nächsten Tag und das Enddatum hinzu (*update 2*).
1. Bearbeiten Sie **[!UICONTROL scheduled update]** , der für Schritt 1 (*update 1*) erstellt wurde, und die Speicheränderungen.

<u>Erwartete Ergebnisse</u>

Das (*Update 2*) sollte in der Liste **[!UICONTROL schedule update]** verbleiben, wenn (*Update 1*) bearbeitet wird.

<u>Tatsächliche Ergebnisse</u>

(*update 2*) wurde aus der Liste **[!UICONTROL schedule update]** entfernt, wenn (*update 1*) bearbeitet wird.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](</help/tools/quality-patches-tool/usage.md>) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] -Handbuch.
