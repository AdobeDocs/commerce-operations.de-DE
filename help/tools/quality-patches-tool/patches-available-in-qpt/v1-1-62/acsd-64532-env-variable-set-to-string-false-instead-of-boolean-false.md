---
title: 'ACSD-64532: Die ENV-Variable *false* wird als Zeichenfolge *false* anstelle eines BOOLESCHEN *FALSE* behandelt.'
description: Wenden Sie den Patch ACSD-64532 an, um das Adobe Commerce-Problem zu beheben, bei dem eine auf *false* gesetzte Variable „ENV“ als Zeichenfolge *false* anstelle von „BOOLEAN“ *FALSE* behandelt wird.
feature: Variables
role: Admin, Developer
source-git-commit: 603b4f92ab3bbf4702d5373bd02dfdd770f57d5b
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# ACSD-64532: Die ENV-Variable, die auf „false“ gesetzt ist, wird als Zeichenfolge „false“ anstelle von „BOOLEAN FALSE“ behandelt.

Mit dem Patch ACSD-64532 wird das Problem behoben, dass die `ENV` Variable *false* als Zeichenfolge *false* anstelle von `BOOLEAN` *FALSE* behandelt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 installiert ist. Die Patch-ID ist ACSD-64532. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p8

**Kompatibel mit Adobe Commerce-Versionen:**
Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

`ENV` Variable, die auf *false* gesetzt ist, wird als Zeichenfolge *false* anstelle einer `BOOLEAN` *FALSE* behandelt.

<u>Schritte zur Reproduktion</u>:
1. Fügen Sie `env:MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK` mit dem Wert *false* zu den Umgebungsvariablen in Adobe Commerce in der Cloud-Infrastruktur hinzu.
1. Auf erneute Bereitstellung warten.
1. Führen Sie das Skript zur Überprüfung des Werts aus:

   ```php
   <?php
   require '../app/bootstrap.php';
   $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
   $objectManager = $bootstrap->getObjectManager();
   $deploymentConfig = $objectManager->get('Magento\Framework\App\DeploymentConfig');
   $useAppLock = $deploymentConfig->get('indexer/use_application_lock');
   
   var_dump($useAppLock);
   
   $configParsedValue = $deploymentConfig->get('indexer/use_application_lock') ?: false;
   
   var_dump($configParsedValue); 
   ```

<u>Erwartete Ergebnisse</u>:
`$configParsedValue`, das Ergebnis der Methode `isUseApplicationLock()`, muss einen negativen Wert zurückgeben, damit er innerhalb der Methode `\Magento\Indexer\Model\Mview\View\State::getStatus()` korrekt interpretiert wird.

<u>Tatsächliche Ergebnisse</u>:
`$configParsedValue` hat den Wert *`string(5) false`*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:
* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
