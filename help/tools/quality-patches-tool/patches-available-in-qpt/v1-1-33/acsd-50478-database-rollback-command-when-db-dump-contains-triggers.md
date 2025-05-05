---
title: 'ACSD-50478: JS-Problem bei Rollback-Aktion im Sicherungsraster und im Rollback-Befehl der Datenbank'
description: Wenden Sie den ACSD-50478-Patch an, um das JS-Problem für die Rollback-Aktion im Sicherungsraster und den Datenbankrollback-Befehl für einen Fall zu beheben, in dem der DB-Dump Trigger und einen SQL-Befehl zum *Trennzeichen* enthält.
exl-id: 2f47fbf6-44fc-487c-91fe-6e2e52fcdb2b
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-50478: JS-Problem bei Rollback-Aktion im Sicherungsraster und im Rollback-Befehl der Datenbank

Der Patch ACSD-50478 behebt das JS-Problem für die Rollback-Aktion im Sicherungsraster und den Datenbank-Rollback-Befehl für einen Fall, dass der DB-Dump Trigger und einen SQL-Befehl *Trennzeichen* enthält. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 installiert ist. Die Patch-ID ist ACSD-50478. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.4-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

JS-Problem für die Rollback-Aktion im Sicherungsraster und den Datenbankrollback-Befehl für einen Fall, wenn der DB-Dump Trigger und einen SQL-Befehl *Trennzeichen* enthält.

<u>Schritte zur Reproduktion</u>:

1. Setzen Sie die Indexer auf den [!UICONTROL Update on Schedule], damit Trigger in der Datenbank erstellt werden.
1. Aktivieren Sie die Backup-Funktion über die Befehlszeile:

   `bin/magento config:set system/backup/functionality_enabled 1`

1. Wechseln Sie zu **System** > **Tools** > **Backups** und generieren Sie ein DB-Backup.
1. Öffnen Sie die Browser-Konsole; Sie sehen den folgenden Fehler:

   ```
   Uncaught SyntaxError: Unexpected token '&' (at (index):606:32)
   
   function eventListener8jtGaqtgG2 () {
   
           return backup.rollback(&#039;db&#039;, &#039;1678391644&#039;);
   ```

1. Versuchen Sie, die DB von der Befehlszeile zu importieren:

   `bin/magento setup:rollback --db-file="<filename>"`

1. Der folgende Fehler wird angezeigt:

   ```
   Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'delimiter' at line 1, query was: delimiter ;;
   ```

<u>Erwartete Ergebnisse</u>:

Die Datenbankwiederherstellung ist sowohl über die Admin- als auch über die Befehlszeile erfolgreich.

<u>Tatsächliche Ergebnisse</u>:

Sie haben die in Schritt 4 und Schritt 6 genannten Fehler beobachtet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
