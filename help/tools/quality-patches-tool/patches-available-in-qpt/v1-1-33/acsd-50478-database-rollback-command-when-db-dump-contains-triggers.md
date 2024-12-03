---
title: 'ACSD-50478: JS-Problem für Rollback-Aktionen im Sicherungsraster und Datenbank-Rollback-Befehl'
description: Wenden Sie den Patch ACSD-50478 an, um das JS-Problem für die Rollback-Aktion im Sicherungsraster und den Datenbank-Rollback-Befehl zu beheben, wenn der DB-Dump Trigger und einen SQL-Befehl *delimiter* enthält.
exl-id: 2f47fbf6-44fc-487c-91fe-6e2e52fcdb2b
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-50478: JS-Problem für Rollback-Aktionen im Sicherungsraster und Datenbank-Rollback-Befehl

Der Patch ACSD-50478 behebt das JS-Problem für die Rollback-Aktion im Sicherungsraster und den Datenbank-Rollback-Befehl für einen Fall, in dem der DB-Dump Trigger und einen SQL-Befehl mit dem Trennzeichen ** enthält. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 installiert ist. Die Patch-ID ist ACSD-50478. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.4 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

JS-Problem für die Rollback-Aktion im Sicherungsraster und den Datenbank-Rollback-Befehl für einen Fall, wenn der DB-Dump Trigger und einen SQL-Befehl *delimiter* enthält.

<u>Zu reproduzierende Schritte</u>:

1. Setzen Sie die Indexer auf den Modus &quot;[!UICONTROL Update on Schedule]&quot;, damit Trigger in der Datenbank erstellt werden.
1. Aktivieren Sie die Sicherungsfunktion über die Befehlszeile:

   `bin/magento config:set system/backup/functionality_enabled 1`

1. Wechseln Sie zu **System** > **Tools** > **Sicherungen** und generieren Sie eine DB-Sicherung.
1. Öffnen Sie die Browser-Konsole. Der folgende Fehler wird angezeigt:

   ```
   Uncaught SyntaxError: Unexpected token '&' (at (index):606:32)
   
   function eventListener8jtGaqtgG2 () {
   
           return backup.rollback(&#039;db&#039;, &#039;1678391644&#039;);
   ```

1. Versuchen Sie, die DB über die Befehlszeile zu importieren:

   `bin/magento setup:rollback --db-file="<filename>"`

1. Der folgende Fehler wird angezeigt:

   ```
   Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'delimiter' at line 1, query was: delimiter ;;
   ```

<u>Erwartete Ergebnisse</u>:

Die Datenbankwiederherstellung kann sowohl vom Administrator als auch von der Befehlszeile erfolgreich durchgeführt werden.

<u>Tatsächliche Ergebnisse</u>:

Sie haben die in Schritt 4 und Schritt 6 genannten Fehler beobachtet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
