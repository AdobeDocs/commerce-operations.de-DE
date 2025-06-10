---
title: Versionshinweise zum Sicherheits-Patch für Adobe Commerce 2.4.8
description: Erfahren Sie mehr über Fehlerbehebungen, Sicherheitsverbesserungen und andere sicherheitsbezogene Updates in den Sicherheits-Patch-Versionen für Adobe Commerce 2.4.7.
source-git-commit: cbf41054a2a8ffefa38049e1bf6e4a2f09e06ce1
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# Versionshinweise für Adobe Commerce 2.4.8-Sicherheits-Patches

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8-p1

Die Adobe Commerce-Version 2.4.8-p1 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.8 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB25-50](https://helpx.adobe.com/de/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Highlights

Diese Version umfasst die folgenden Highlights:

* **API-Leistungsverbesserung**: Behebt die Leistungsbeeinträchtigung bei asynchronen Web-API-Endpunkten, die nach dem vorherigen Sicherheits-Patch eingeführt wurden.<!-- AC-14078 -->

* **CMS blockiert den Zugriff** - Löst ein Problem, bei dem Admin-Benutzer mit eingeschränkten Berechtigungen (z. B. Nur-Merchandising-Zugriff) die [!UICONTROL CMS Blocks] nicht anzeigen konnten.

  Zuvor trat bei diesen Benutzern ein Fehler aufgrund fehlender Konfigurationsparameter nach der Installation früherer Sicherheits-Patches auf.<!-- AC-14087 -->

* **Cookie-Kompatibilität** - Löst eine abwärtsinkompatible Änderung auf, die die `MAX_NUM_COOKIES` im Framework betrifft. Diese Aktualisierung stellt das erwartete Verhalten wieder her und stellt die Kompatibilität für Erweiterungen oder Anpassungen sicher, die mit Cookie-Beschränkungen interagieren.<!-- AC-14475 -->

* **Behebung für CVE-2024-34104** - Behebt eine unsachgemäße Autorisierungs-Schwachstelle.<!-- AC-13917 -->

* **Behebung für CVE-2025-47110** - Behebt eine Sicherheitslücke bei E-Mail-Vorlagen.<!-- AC-14695 -->

* **Fehlerbehebung für VULN-31547** - Behebt eine Schwachstelle bei kanonischen Links der Kategorie.<!-- AC-14713 -->

>[!BEGINSHADEBOX]

Die Fehlerbehebung für CVE-2025-47110 ist auch als isolierter Patch verfügbar. Weitere Informationen finden [ im Artikel ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50)Wissensdatenbank“.

>[!ENDSHADEBOX]
