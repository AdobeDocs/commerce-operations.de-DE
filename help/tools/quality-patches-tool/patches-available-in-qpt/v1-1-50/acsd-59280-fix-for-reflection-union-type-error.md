---
title: 'ACSD-59280: Fehler „ReflectionUnionType::getName()“ in 2.4.4-pX-Installationen'
description: Wenden Sie den Patch ACSD-59280 an, um das Adobe Commerce-Problem zu beheben, bei dem der Fehler „call to undefined method ReflectionUnionType::getName()“ während der Installation von 2.4.4-pX-Versionen auftritt.
feature: Install, Upgrade
role: Admin, Developer
exl-id: 5a47dad4-4490-4e3d-93f2-9b176fb144d9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# ACSD-59280: `ReflectionUnionType::getName()` Fehler in 2.4.4-pX-Installationen

Mit dem Patch ACSD-59280 wird das Problem behoben, dass der `call to undefined method ReflectionUnionType::getName()` Fehler während der Installation von 2.4.4-pX-Versionen auftritt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 installiert ist. Die Patch-ID ist ACSD-59280. Beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

`ReflectionUnionType::getName()` während der Installation von 2.4.4-pX.

<u>Schritte zur Reproduktion</u>:

Führen Sie mit *[!UICONTROL Composer]* eine Neuinstallation durch.

<u>Erwartete Ergebnisse</u>:

Der Installationsprozess wird fehlerfrei abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

Während des `setup:upgrade` wird die folgende Fehlermeldung angezeigt:

`Call to undefined method ReflectionUnionType::getName()`

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
