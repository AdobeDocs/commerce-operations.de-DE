---
source-git-commit: 33debd1c742698e8242faaef1ff83bb2a9e5ee58
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---
# Sicherheits-Patch-Highlights vom Juni 2025

Diese Version umfasst die folgenden Highlights:

* **API-Leistungsverbesserung**: Behebt die Leistungsbeeinträchtigung bei asynchronen Web-API-Endpunkten, die nach dem vorherigen Sicherheits-Patch eingeführt wurden.<!-- AC-14078 -->

* **CMS blockiert den Zugriff** - Löst ein Problem, bei dem Admin-Benutzer mit eingeschränkten Berechtigungen (z. B. Nur-Merchandising-Zugriff) die [!UICONTROL CMS Blocks] nicht anzeigen konnten.

  Zuvor trat bei diesen Benutzern ein Fehler aufgrund fehlender Konfigurationsparameter nach der Installation früherer Sicherheits-Patches auf.<!-- AC-14087 -->

* **Cookie-Kompatibilität** - Löst eine abwärtsinkompatible Änderung auf, die die `MAX_NUM_COOKIES` im Framework betrifft. Diese Aktualisierung stellt das erwartete Verhalten wieder her und stellt die Kompatibilität für Erweiterungen oder Anpassungen sicher, die mit Cookie-Beschränkungen interagieren.<!-- AC-14475 -->

* **Async-Vorgänge** - Eingeschränkte asynchrone Vorgänge zum Überschreiben früherer Kundenbestellungen.<!-- AC-13917 -->

* **Behebung für CVE-2025-47110** - Behebt eine Sicherheitslücke bei E-Mail-Vorlagen.<!-- AC-14695 -->

>[!BEGINSHADEBOX]

Die Fehlerbehebung für CVE-2025-47110 ist auch als isolierter Patch verfügbar. Weitere Informationen finden [ im Artikel ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50)Wissensdatenbank“.

>[!ENDSHADEBOX]