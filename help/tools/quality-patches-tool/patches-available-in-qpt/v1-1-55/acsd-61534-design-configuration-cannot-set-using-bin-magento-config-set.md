---
title: 'ACSD-61534: Die Designkonfiguration kann nicht mit bin/magento config:set festgelegt werden und gesperrte Werte können über die Formularbearbeitung geändert werden'
description: Wenden Sie den Patch ACSD-61534 an, um das Adobe Commerce-Problem zu beheben, bei dem die Designkonfiguration nicht mit dem Befehl "bin/magento config:set"festgelegt werden kann und gesperrte Werte durch die Formularbearbeitung geändert werden können.
feature: Configuration
role: Admin, Developer
exl-id: 5bba3f05-e017-42b2-8a89-5471afb84ff3
source-git-commit: bbf7df7fdca4c11f6f268344db00e2c8643b5dce
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-61534: Die Designkonfiguration kann nicht mit `bin/magento config:set` festgelegt werden und gesperrte Werte können über die Formularbearbeitung geändert werden

Der Patch ACSD-61534 behebt das Problem, dass die Designkonfiguration nicht mit dem Befehl `bin/magento config:set` festgelegt werden kann und gesperrte Werte durch die Bearbeitung des Formulars geändert werden können. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-61534. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Designkonfiguration kann nicht mit dem Befehl `bin/magento config:set` festgelegt werden und gesperrte Werte können durch die Bearbeitung des Formulars geändert werden. Mit diesem Patch können gesperrte Werte, die über das Befehlszeilen-Tool (CLI) mit `--lock-env` oder `--lock-conf` festgelegt wurden, nicht aktualisiert werden.

<u>Zu reproduzierende Schritte</u>:

1. Sperren Sie einen Konfigurationswert mithilfe einer Cloud-Umgebungsvariablen wie `CONFIG_WEBSITESBASEDESIGNHEAD_INCLUDES`.
1. Wechseln Sie zum Bedienfeld &quot;*[!UICONTROL Admin]*&quot;.
1. Gehen Sie zu **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**.
1. Klicken Sie in der zweiten Zeile neben dem Wert **[!UICONTROL Global/Main website]** auf **[!UICONTROL Edit]**.
1. Design bearbeiten für eine Store-Ansicht.
1. Öffnen Sie den HTML-Kopf.
1. Aktivieren Sie das deaktivierte Feld **[!UICONTROL Scripts and Style Sheets]** mit Entwicklertools.
1. Ändern Sie den Wert und speichern Sie ihn.

<u>Erwartete Ergebnisse</u>:

Ein gesperrter Wert kann nicht gespeichert werden.

<u>Tatsächliche Ergebnisse</u>:

Tabelle `core_config_data` enthält einen aktualisierten Wert für `design/head/includes`.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
