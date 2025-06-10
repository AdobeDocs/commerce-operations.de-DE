---
source-git-commit: f9cc5ab0cb1b64455e12081ffbf719e0f2a791ad
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---
# Sicherheits-Patch-Highlights vom Juni 2025

Diese Version umfasst die folgenden Highlights:

* **API-Leistungsverbesserung**: Behebt die Leistungsbeeinträchtigung bei asynchronen Web-API-Endpunkten, die nach dem vorherigen Sicherheits-Patch eingeführt wurden.<!-- AC-14078 -->

* **CMS blockiert den Zugriff** - Löst ein Problem, bei dem Admin-Benutzer mit eingeschränkten Berechtigungen (z. B. Nur-Merchandising-Zugriff) die [!UICONTROL CMS Blocks] nicht anzeigen konnten.

  Zuvor trat bei diesen Benutzern ein Fehler aufgrund fehlender Konfigurationsparameter nach der Installation früherer Sicherheits-Patches auf.<!-- AC-14087 -->

* **Cookie-Kompatibilität** - Löst eine abwärtsinkompatible Änderung auf, die die `MAX_NUM_COOKIES` im Framework betrifft. Diese Aktualisierung stellt das erwartete Verhalten wieder her und stellt die Kompatibilität für Erweiterungen oder Anpassungen sicher, die mit Cookie-Beschränkungen interagieren.<!-- AC-14475 -->

* **Behebung für CVE-2024-34104** - Behebt eine unsachgemäße Autorisierungs-Schwachstelle.<!-- AC-13917 -->

* **Behebung für CVE-2025-47110** - Behebt eine Sicherheitslücke bei E-Mail-Vorlagen.<!-- AC-14695 -->

* **Fehlerbehebung für VULN-31547** - Behebt eine Schwachstelle bei kanonischen Links der Kategorie.<!-- AC-14713 -->

>[!BEGINSHADEBOX]

Fehlerbehebungen für CVE-2025-47110 VULN-31547 sind auch als isolierter Patch verfügbar. Weitere Informationen finden [ im Artikel ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50)Wissensdatenbank“.

>[!ENDSHADEBOX]
