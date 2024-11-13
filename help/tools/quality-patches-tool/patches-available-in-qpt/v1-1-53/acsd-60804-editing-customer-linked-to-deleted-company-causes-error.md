---
title: "ACSD-60804: Das Bearbeiten eines mit einem gelöschten Unternehmen verknüpften Kunden führt zu einem Fehler."
description: Wenden Sie den Patch ACSD-60804 an, um das Adobe Commerce-Problem zu beheben, bei dem die Bearbeitung eines mit einem gelöschten Unternehmen verknüpften Kunden den Fehler *Aufruf an die Mitgliederfunktion getSuperUserId() auf null* verursacht.
feature: Companies, Customers, B2B
role: Admin, Developer
source-git-commit: 1231dac065565ff636424673a15ae4148a5f84dd
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-60804: Das Bearbeiten eines Kunden, der einem gelöschten Unternehmen zugeordnet ist, führt zu einem Fehler

Der Patch ACSD-60804 behebt das Problem, dass das Bearbeiten eines mit einem gelöschten Unternehmen verknüpften Kunden einen Fehler verursacht, *Aufruf an die Mitgliederfunktion getSuperUserId() auf null*. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 installiert ist. Die Patch-ID ist ACSD-60804. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.4.8 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn ein Kunde bearbeitet wird, der einem gelöschten Unternehmen zugeordnet ist, wird der Fehler *Aufrufen der Mitgliederfunktion getSuperUserId() auf null* ausgelöst.

<u>Voraussetzungen:</u>:

Installieren und aktivieren Sie die Adobe Commerce B2B-Module.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Settings]** > **[!UICONTROL B2B]** > **[!UICONTROL Enable Company]**.
1. Gehen Sie zu **[!UICONTROL Customers]** > **[!UICONTROL Company]** > **[!UICONTROL Create New Company]**.
1. Melden Sie sich bei `mysql` für die Instanz an.
1. Löschen Sie das Unternehmen, bei dem `entity_id` = *1* ist.
1. Gehen Sie zu **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Bearbeiten Sie den Kunden, der beim Erstellen des Unternehmens automatisch erstellt wurde.

<u>Erwartete Ergebnisse</u>:

Der Kunde wird ohne Ausnahmefehler bearbeitet.

<u>Tatsächliche Ergebnisse</u>:

Es tritt ein Fehler auf: *Aufrufen einer Mitgliedsfunktion getSuperUserId() auf null*, wenn dem Kunden kein Unternehmen zugeordnet ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
