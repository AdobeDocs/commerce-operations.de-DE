---
title: 'ACSD-63139: Der Produktexport schlägt fehl, wenn Produktattribute Tausende von Optionswerten enthalten'
description: Wenden Sie den Patch ACSD-63139 an, um das Adobe Commerce-Problem zu beheben, bei dem der Produktexport fehlschlägt, wenn Produktattribute Tausende von Optionswerten enthalten.
feature: Data Import/Export
role: Admin, Developer
exl-id: 785907dc-aa3f-49e2-bd52-c3afe4393456
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%
---
# ACSD-63139: Der Produktexport schlägt fehl, wenn Produktattribute Tausende von Optionswerten enthalten

Der Patch ACSD-63139 behebt das Problem, dass der Produktexport fehlschlägt, wenn Produktattribute Tausende von Optionswerten enthalten. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 installiert ist. Die Patch-ID ist ACSD-63139. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p10

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Produktexport schlägt fehl, wenn Produktattribute Tausende von Optionswerten enthalten.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie Adobe Commerce mit dem B2B-Modul.
1. Importieren Sie einen großen Datenbank-Dump mit:
   - ~7.000 Produkte
   - ~450 Produktattribute
   - Einige Attribute mit mehr als 100 Optionen
1. Führen Sie den folgenden Befehl aus, um cron zu installieren (falls noch nicht installiert):

   ```shell
   bin/magento cron:install
   ```

1. Konfigurieren Sie [!DNL RabbitMQ], indem Sie die Anweisungen in [[!DNL RabbitMQ] Voraussetzungen](/help/installation/prerequisites/rabbitmq.md) befolgen.
1. Öffnen Sie die `php.ini`-Datei, setzen Sie die Speicherbegrenzung auf 4G und starten Sie den PHP-Service neu.
1. Navigieren Sie im Admin-Bedienfeld zu **[!UICONTROL System]** > *[!UICONTROL Data Transfer]* > **[!UICONTROL Export]**.
1. Legen Sie im Abschnitt *[!UICONTROL Export Settings]* den Wert **[!UICONTROL Entity Type]** auf *Produkte* fest, scrollen Sie nach unten und klicken Sie auf **[!UICONTROL Continue]**.
1. Führen Sie den folgenden Befehl aus, um den Exportprozessor zu starten:

   ```shell
   bin/magento queue:consumers:start exportProcessor --max-messages=1
   ```

<u>Erwartete Ergebnisse</u>:

Der Produktexport sollte erfolgreich abgeschlossen werden.

<u>Tatsächliche Ergebnisse</u>:

Der Produktexportvorgang schlägt fehl und gibt den folgenden schwerwiegenden Fehler zurück:

```text
Fatal error: Allowed memory size of 4294967296 bytes exhausted (tried to allocate 12288 bytes) in /var/www/html/app/code/Magento/Catalog/Model/ResourceModel/Product/Collection.php on line 597
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
