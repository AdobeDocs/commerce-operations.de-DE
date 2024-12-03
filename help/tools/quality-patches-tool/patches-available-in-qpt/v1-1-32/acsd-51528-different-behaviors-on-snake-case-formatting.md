---
title: 'ACSD-51528: Verschiedene Verhaltensweisen bei der Formatierung von Schlangen-Groß- und Kleinschreibung'
description: Wenden Sie den Patch ACSD-51528 an, um das Adobe Commerce-Problem zu beheben, bei dem es unterschiedliche Verhaltensweisen bei der snake_case-Formatierung gibt.
feature: Variables
role: Admin
exl-id: 5f2add4b-8209-47a7-bfbd-cc434a050f0f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-51528: Verschiedene Verhaltensweisen bei der Formatierung von Schlangen-Groß- und Kleinschreibung

Der Patch ACSD-51528 behebt unterschiedliche Verhaltensweisen bei der Formatierung von snake_case. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.32 installiert ist. Die Patch-ID ist ACSD-51528. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das unterschiedliche Verhalten bei der Formatierung von snake_case.

<u>Zu reproduzierende Schritte</u>:

1. Testen Sie die Funktion `\Magento\Framework\Api\DataObjectHelper::populateWithArray` mit einer Vielzahl verschiedener Eigenschaftsnamen.
1. Die Eigenschaften mit Namen wie *NewPName* sollten in *new_p_name* umgewandelt werden, stattdessen werden sie in *new_pname* umgewandelt.
1. Außerdem wird bei Verwendung der Funktion *getNewPName* im Objekt *null* zurückgegeben, da das *Abstract-Modell* den Aufruf korrekt in *new_p_name* umwandelt, wodurch beide Funktionen inkompatibel miteinander sind.

<u>Erwartete Ergebnisse</u>

Die Funktion **[!UICONTROL populateWithArray]** sollte die Objekteigenschaften korrekt in snake_case umwandeln, sodass sie mit den **[!DNL AbstractModel's]** `Getters` und `Setters` kompatibel sind.

<u>Tatsächliche Ergebnisse</u>

Bei Verwendung der Funktion &quot;**[!UICONTROL populateWithArray]**&quot;führen alle Objekteigenschaften, die zwei oder mehr Großbuchstaben in einer Zeile im Namen enthalten, dazu, dass die Umwandlung von &quot;snake_case&quot;im endgültigen Daten-Array falsch ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
