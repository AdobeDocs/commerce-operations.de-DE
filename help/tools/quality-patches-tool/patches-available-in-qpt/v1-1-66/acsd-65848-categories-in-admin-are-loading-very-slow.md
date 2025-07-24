---
title: 'ACSD-65848: Kategorien in Admin werden sehr langsam geladen'
description: Wenden Sie den Patch ACSD-65848 an, um das Adobe Commerce-Problem zu beheben, bei dem die Gesamtproduktzahl in einer Kategorie mithilfe einer Unterauswahl berechnet wurde, die die Ladezeit der Kategorie verzögerte.
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8a614c40a1c0134a0528b74cbd434e7ca96c933a
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---


# ACSD-65848: Kategorien in Admin werden sehr langsam geladen

Mit dem Patch ACSD-65848 wird das Problem behoben, dass die Gesamtproduktzahl in einer Kategorie mithilfe einer Unterauswahl berechnet wurde, was die Ladezeit der Kategorie verzögerte. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 installiert ist. Die Patch-ID ist ACSD-65848. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bei der Ansicht/Bearbeitung der Admin-Kategorieseite treten beim Laden erhebliche Verzögerungen auf. Die Verzögerung wird durch die Methode verursacht, die zur Berechnung der Gesamtproduktzahl in einer Kategorie verwendet wird und die auf einer Unterauswahlabfrage beruht. Wenn Sie diese Logik überarbeiten und stattdessen einen Join verwenden, wird die Leistung verbessert und die Ladezeit reduziert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie mit Version 2.4.8 eine neue Adobe Commerce Cloud-Instanz.
1. Erstellen Sie 2.500 Kategorien und mindestens 10.000 Produkte:
   1. Kopieren Sie das `setup/performance-toolkit` Verzeichnis nach `./var`, damit Sie die Profile bearbeiten können.
   1. Öffnen Sie das `small.xml` und aktualisieren Sie es, um 2.500 Kategorien und 250.000 Produkte einzuschließen (entsprechend der Einrichtung des Händlers).
   1. Führen Sie den folgenden Befehl aus, um die Vorrichtungen zu erzeugen:

      ```bash
      bin/magento 
      setup:performance:generate-fixtures var/setup/performance-toolkit/profiles/ce/small.xml
      ```

1. Nachdem die Produkte und Kategorien erstellt wurden, stellen Sie sicher, dass alle Kategorien als Anker festgelegt sind. Diese SQL-Abfrage ausführen:

   ```sql
   UPDATE catalog_category_entity_int 
   SET value = 1 
   WHERE attribute_id = (
   SELECT attribute_id 
   FROM eav_attribute 
   WHERE attribute_code = 'is_anchor'
   );
   ```

1. Erstellen Sie im Admin-Bedienfeld eine tiefere Kategoriestruktur:
   * Verschieben Sie Kategorie 2 unter Kategorie 1, um sie tiefer im Baum zu verschachteln.
1. Versuchen Sie, eine Kategorieseite im Admin-Bedienfeld mithilfe einer URL wie der folgenden zu öffnen:
   ```/admin/catalog/category/edit/id/xx/```

<u>Erwartete Ergebnisse</u>:

Jede Kategorieseite wird beim ersten Versuch innerhalb weniger Sekunden geöffnet.

<u>Tatsächliche Ergebnisse</u>:

Das Öffnen von Kategorieseiten dauert mehr als eine Minute.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
