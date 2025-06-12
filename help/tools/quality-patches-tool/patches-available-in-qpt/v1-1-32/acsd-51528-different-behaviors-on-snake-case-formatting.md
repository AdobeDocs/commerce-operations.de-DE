---
title: 'ACSD-51528: Unterschiedliches Verhalten bei der Formatierung von snake_case'
description: Wenden Sie den Patch ACSD-51528 an, um das Adobe Commerce-Problem zu beheben, bei dem es unterschiedliche Verhaltensweisen bei der Formatierung von snake_case gibt.
feature: Variables
role: Admin
exl-id: 5f2add4b-8209-47a7-bfbd-cc434a050f0f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-51528: Unterschiedliches Verhalten bei der Formatierung von snake_case

Der Patch ACSD-51528 behebt unterschiedliche Verhaltensweisen bei der Formatierung von snake_case. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.32 installiert ist. Die Patch-ID ist ACSD-51528. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die verschiedenen Verhaltensweisen bei der Formatierung von snake_case.

<u>Schritte zur Reproduktion</u>:

1. Testen Sie die `\Magento\Framework\Api\DataObjectHelper::populateWithArray` mit einer Vielzahl verschiedener Eigenschaftsnamen.
1. Eigenschaften mit Namen wie *NewPName* sollten in *new_p_name* umgewandelt werden, stattdessen werden sie in *new_pname* umgewandelt.
1. Außerdem wird bei Verwendung der Funktion *getNewPName* im Objekt *null* zurückgegeben, da das *Abstrakte Modell* den Aufruf an *new_p_name* transformiert, sodass beide Funktionen miteinander inkompatibel sind.

<u>Erwartete Ergebnisse</u>

Die Funktion **[!UICONTROL populateWithArray]** sollte die Objekteigenschaften korrekt in snake_case umwandeln, sodass sie mit dem **[!DNL AbstractModel's]** `Getters` und der `Setters` kompatibel ist.

<u>Tatsächliche Ergebnisse</u>

Bei Verwendung der Funktion **[!UICONTROL populateWithArray]** führen alle Objekteigenschaften, die zwei oder mehr Großbuchstaben in einer Zeile im Namen enthalten, dazu, dass die Transformation „snake_case“ im endgültigen Daten-Array falsch ist.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
