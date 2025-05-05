---
title: 'ACSD-61534: Die Design-Konfiguration kann nicht mit bin/magento config:set festgelegt werden und gesperrte Werte können über die Formularbearbeitung geändert werden'
description: Wenden Sie den Patch ACSD-61534 an, um das Adobe Commerce-Problem zu beheben, bei dem die Design-Konfiguration nicht mit dem Befehl „bin/magento config:set“ festgelegt werden kann und gesperrte Werte durch Formularbearbeitung geändert werden können.
feature: Configuration
role: Admin, Developer
exl-id: 5bba3f05-e017-42b2-8a89-5471afb84ff3
source-git-commit: bbf7df7fdca4c11f6f268344db00e2c8643b5dce
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-61534: Die Design-Konfiguration kann nicht mit `bin/magento config:set` festgelegt werden und gesperrte Werte können über die Formularbearbeitung geändert werden

Der Patch ACSD-61534 behebt das Problem, dass die Design-Konfiguration nicht mit dem Befehl `bin/magento config:set` festgelegt werden kann und gesperrte Werte durch Formularbearbeitung geändert werden können. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-61534. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Design-Konfiguration kann nicht mit dem Befehl `bin/magento config:set` festgelegt werden und gesperrte Werte können durch Formularbearbeitung geändert werden. Mit diesem Patch können gesperrte Werte, die über das Befehlszeilen-Tool (Command Line Tool, CLI) mit `--lock-env` oder `--lock-conf` festgelegt wurden, nicht aktualisiert werden.

<u>Schritte zur Reproduktion</u>:

1. Sperren Sie einen Konfigurationswert mithilfe einer Cloud-Umgebungsvariablen, z. B. `CONFIG_WEBSITESBASEDESIGNHEAD_INCLUDES`.
1. Navigieren Sie zum Bedienfeld *[!UICONTROL Admin]* .
1. Navigieren Sie zu **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**.
1. Klicken Sie **[!UICONTROL Edit]** neben dem **[!UICONTROL Global/Main website]** in der zweiten Zeile.
1. Design für eine Store-Ansicht bearbeiten.
1. Öffnen Sie den HTML-Kopf.
1. Aktivieren Sie das Feld Deaktivierte **[!UICONTROL Scripts and Style Sheets]** mithilfe von Entwickler-Tools.
1. Ändern Sie den Wert und speichern Sie ihn.

<u>Erwartete Ergebnisse</u>:

Ein gesperrter Wert kann nicht gespeichert werden.

<u>Tatsächliche Ergebnisse</u>:

Tabelle `core_config_data` enthält einen aktualisierten Wert für `design/head/includes`.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
