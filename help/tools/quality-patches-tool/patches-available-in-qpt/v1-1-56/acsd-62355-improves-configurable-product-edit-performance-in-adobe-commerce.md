---
title: 'ACSD-62355: Verbessert die konfigurierbare Leistung bei der Produktbearbeitung in Adobe Commerce'
description: Wenden Sie den ACSD-62355-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die konfigurierbare Produktbearbeitungsseite langsam geladen wird, wenn das Produkt auf vielen Attributen mit vielen Werten basiert.
feature: Admin Workspace
role: Admin, Developer
source-git-commit: e8694744c8a2411a8e966148860f43fb56b48772
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# ACSD-62355: Verbessert die konfigurierbare Leistung bei der Produktbearbeitung in Adobe Commerce

Mit dem Patch ACSD-62355 wird das Problem langsamer Ladezeiten und hoher Speicherbelegung auf der konfigurierbaren Produktbearbeitungsseite behoben, wenn das Produkt viele Attribute mit zahlreichen Werten aufweist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 installiert ist. Die Patch-ID ist ACSD-62355. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Laden der konfigurierbaren Produktbearbeitungsseite dauert lange, wenn das konfigurierbare Produkt auf mehreren Attributen mit vielen Werten basiert, was zu Verzögerungen und möglichen Problemen mit Timeouts oder Speicherbeschränkungen führt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie im Standardattributsatz neun neue Attribute, von denen jedes [!UICONTROL Filterable] ist und [!UICONTROL Scope]: [!UICONTROL Global] aufweist.
   * Attribut 1: 50 Optionen
   * Attribut 2: 20 Optionen
   * Attribut 3: 10 Optionen
   * Attribut 4: 5 Optionen
   * Attribut 5: 5 Optionen
   * Attribut 6: 5 Optionen
   * Attribut 7: 5 Optionen
   * Attribut 8: 3 Optionen
   * Attribut 9: 2 Optionen

1. Erstellen Sie 9 einfache Produkte mit Kombinationen von Optionen aus den neu erstellten Attributen.
   * Produkt 1: Erste Option für jedes Attribut
   * Produkt 2: Zweite Option für jedes Attribut
   * Produkt 3: Dritte Option für jedes Attribut
   * Produkt 4: Vierte Option für jedes Attribut
   * Wenn ein Attribut weniger Optionen als die Anzahl der Produkte hat, weisen Sie die verbleibenden Produkte den zufälligen Optionen innerhalb dieses Attributs zu.

1. Erstellen Sie ein konfigurierbares Produkt, das die neu erstellten Attribute verwendet:
   * Fügen Sie ein untergeordnetes Produkt mit der folgenden Konfiguration hinzu:
      * Verwenden Sie die letzte Option aus Attribut 1 und die erste Option aus Attribute 2 bis 9.
      * Dies führt zu einem konfigurierbaren Produkt und einem untergeordneten Produkt.
1. Wechseln Sie zur Registerkarte **[!UICONTROL Configurations]** des konfigurierbaren Produkts.
1. Klicken Sie auf Manuell **[!UICONTROL Add Products]** und beginnen Sie mit dem Hinzufügen der zuvor erstellten einfachen Produkte einzeln.
1. Speichern Sie die Änderungen nach jedem Hinzufügen.
1. Beachten Sie beim Hinzufügen von Produkten die Ladezeit der Seite „Konfigurierbares Produkt bearbeiten“.
1. Nach dem Hinzufügen von 7 Produkten sollten Sie einen deutlichen Anstieg des RAM-Verbrauchs und der Seitenladezeit feststellen

<u>Erwartete Ergebnisse</u>:

Das Formular zur Produktbearbeitung sollte schnell und effizient geladen werden, ohne dass zu viel Speicher verbraucht wird.

<u>Tatsächliche Ergebnisse</u>:

Das Bearbeiten des konfigurierbaren Produkts dauert lange, bis es geladen wird, und kann Speicherbeschränkungen oder Zeitüberschreitungsfehler erreichen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
