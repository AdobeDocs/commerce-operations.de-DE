---
title: "ACSD-49513: Remote-Speichersynchronisation schlägt fehl"
description: Wenden Sie den Patch ACSD-49513 an, um das Adobe Commerce-Problem zu beheben, bei dem die Remote-Speichersynchronisierung aufgrund von 0-Byte-Dateien fehlschlägt.
feature: Iaas, Storage
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-49513: Die Remote-Speichersynchronisierung schlägt aufgrund von 0-Byte-Dateien fehl

Der Patch ACSD-49513 behebt das Problem, bei dem die Remote-Speichersynchronisierung aufgrund von 0-Byte-Dateien fehlschlägt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 installiert ist. Die Patch-ID lautet ACSD-49513. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Remote-Speichersynchronisierung schlägt aufgrund von 0-Byte-Dateien fehl.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie AWS S3 als Remote-Speicher.
1. Führen Sie `[bin/magento remote-storage:sync]` aus, um sicherzustellen, dass die Synchronisierung am Anfang ordnungsgemäß funktioniert.
1. Erstellen Sie eine 0-Byte-Datei innerhalb von `[pub/media]`.
1. Führen Sie `[bin/magento remote-storage:sync]` erneut aus.

<u>Erwartete Ergebnisse</u>:

Da das AWS S3 0-Byte-Dateien für die direkte Push-Benachrichtigung des S3 akzeptiert, gibt es keinen Fehler.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler tritt auf:

```PHP
Uploading media files to remote storage.
In File.php line 387:
  The file or directory "pub/media/xxxx.file" cannot be copied to "*.amazonaws.com/media/xxxx.file"
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Zusätzliche Schritte, die nach der Patch-Installation erforderlich sind

(Dieser Abschnitt ist optional. Möglicherweise sind nach dem Anwenden des Patches einige Schritte erforderlich, um das Problem zu beheben.) 

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
