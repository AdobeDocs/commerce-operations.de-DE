---
title: 'Verwaltete Warnhinweise für Adobe Commerce: Kritischer Warnhinweis auf Festplatte'
description: Dieser Artikel enthält Schritte zur Fehlerbehebung bei kritischen Festplattenwarnungen für Adobe Commerce in [!DNL New Relic]. Sofortiges Handeln ist erforderlich, um das Problem zu beheben.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: c1757dee33b22b5dae3c7f0eab9c1efe20d0a9a8
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---


# Verwaltete Warnhinweise für Adobe Commerce: Kritischer Warnhinweis auf Festplatte

Dieser Artikel enthält Schritte zur Fehlerbehebung bei kritischen Datenträgerwarnungen für Adobe Commerce in [!DNL New Relic]. Sofortiges Handeln ist erforderlich, um das Problem zu beheben. Je nach ausgewähltem Benachrichtigungskanal für Warnhinweise sieht der Warnhinweis etwa wie folgt aus.

![Kritischer Warnhinweis auf Festplatte](../../assets/managed-alerts/disk-critical-magento-managed.png){width="500"}

## Betroffene Produkte und Versionen

Adobe Commerce-Cloud-Infrastruktur auf Pro-Planarchitektur

## Problem

Sie erhalten einen Warnhinweis in [!DNL New Relic], wenn Sie sich für [Verwaltete Warnhinweise für Adobe Commerce](managed-alerts-for-magento-commerce.md) angemeldet haben und einer oder mehrere der Warnhinweisschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe entwickelt, um Kundinnen und Kunden mithilfe von Einblicken aus Support und Engineering einen Standardsatz zu bieten.

<u> **DO!** </u>

* Bricht jede geplante Bereitstellung ab, bis dieser Warnhinweis gelöscht wird.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site nicht mehr reagiert oder überhaupt nicht mehr reagiert. Anweisungen hierzu finden Sie [Aktivieren oder Deaktivieren des ](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/maintenance-mode). Fügen Sie Ihre IP-Adresse der Liste der von der Steuer befreiten IP-Adressen hinzu, um sicherzustellen, dass Sie weiterhin zur Fehlerbehebung auf Ihre Website zugreifen können. Anweisungen hierzu finden Sie unter [Liste der ausgenommenen IP-Adressen verwalten](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses).

**Tu&#39;s nicht!**

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten auf Ihre Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, was zu zusätzlichen Belastungen für CPU oder die Festplatte führen kann.
* Führen Sie alle wichtigen administrativen Aufgaben aus (z. B. Commerce-Admin, Datenimporte/-exporte).
* Leeren Sie den Cache.

Ihre Site kann nicht mehr reagieren (wenn Sie noch keinen Ausfall der Site feststellen), wenn Sie eine der „Nicht reagieren“-Aktionen durchführen, bevor Sie die Ursache des Warnhinweises untersucht und behoben haben.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

>[!WARNING]
>
>Da es sich um einen kritischen Warnhinweis handelt, wird dringend empfohlen, **Schritt 1** auszuführen, bevor Sie versuchen, das Problem zu beheben (Schritt 2 ab).

1. Überprüfen, ob ein Adobe Commerce-Support-Ticket vorhanden ist. Anweisungen hierzu finden Sie unter [Support-Tickets nachverfolgen](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) in der Commerce Support Knowledge Base. Möglicherweise hat der Support einen Warnhinweis für einen [!DNL New Relic] Schwellenwert erhalten, ein Ticket erstellt und die Arbeit an dem Problem begonnen. Wenn kein Ticket vorhanden ist, erstellen Sie eines. Das Ticket sollte die folgenden Informationen enthalten:
   * Grund des Kontakts: Wählen Sie **[!UICONTROL New Relic CRITICAL alert received]**.
   * Beschreibung des Warnhinweises
   * [[!DNL New Relic] Link zum Vorfall](https://docs.newrelic.com/docs/alerts/incident-management/view-event-details-incidents/). Dies ist in Ihren [Verwaltete Warnhinweise für Adobe Commerce](managed-alerts-for-magento-commerce.md) enthalten.
1. Überprüfen Sie [!DNL New Relic] Festplatten auf ihre höchste Verwendung. Die einzelnen Schritte finden Sie auf **[!UICONTROL Storage]** Registerkarte auf [[!DNL New Relic]  Seite „Überwachung der Infrastruktur - Hosts: Registerkarte [!UICONTROL Storage]&quot;](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage):
   * Wenn Sie in [!DNL New Relic] einen langsamen Anstieg der Speichernutzung feststellen, versuchen Sie die folgenden Optionen:
      * Optimierung des Festplattenspeichers durch Anpassung der Speicherplatzzuweisung Anweisungen hierzu finden Sie unter [Speicherplatz verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html?lang=de) im Handbuch zu Commerce on Cloud. Möglicherweise benötigen Sie auch mehr Speicherplatz (wenden Sie sich an Ihr Adobe-Accountteam).
      * Löschen Sie Speicherplatz für MySQL. Anweisungen hierzu finden Sie [MySQL-](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud) in der Wissensdatenbank für den Commerce-Support.
      * Wenn [!DNL New Relic] eine schnell zunehmende Festplattenauslastung zeigt, kann dies darauf hindeuten, dass ein Problem vorliegt, das dazu geführt hat, dass eine Datei in einem Verzeichnis sehr schnell angestiegen ist. Führen Sie die folgenden Prüfungen durch:
         1. Überprüfen Sie den gesamten Speicherplatz, um das Problem zu identifizieren, indem Sie den folgenden Befehl in der CLI/Terminal ausführen: `df -h`
         1. Nachdem Sie ein Verzeichnis mit unerwartet großer und zunehmender Festplattenauslastung identifiziert haben, müssen Sie das betroffene Dateisystem überprüfen. Das folgende Beispiel zeigt, wie die `pub/media/` des Dateiverzeichnisses überprüft wird. Dies ist der Ordner, den Commerce zum Speichern von Protokollen und großen Mediendateien verwendet. Sie sollten diesen Befehl jedoch für jedes Verzeichnis ausführen, das eine unerwartete Festplattenauslastung zeigt: `du -sch ~/pub/media/*`

Wenn die Ausgabe vom Terminal zeigt, dass eine Datei in einem dieser Verzeichnisse schnell ansteigt und Sie wissen, dass der Inhalt der Datei nicht benötigt wird, sollten Sie die Datei entfernen. Wenn Sie mit dieser Aktion nicht vertraut sind, [ Sie ein Adobe Commerce-Support-Ticket ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).
