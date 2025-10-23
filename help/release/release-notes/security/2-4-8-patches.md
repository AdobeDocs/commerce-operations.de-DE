---
title: Versionshinweise zum Sicherheits-Patch für Adobe Commerce 2.4.8
description: Erfahren Sie mehr über Fehlerbehebungen, Sicherheitsverbesserungen und andere sicherheitsbezogene Updates in den Sicherheits-Patch-Versionen für Adobe Commerce 2.4.7.
exl-id: 5f8866ed-9215-4b2e-9c77-b2d474f6c1f9
source-git-commit: 4cf6f81ce43ddcccf20db12b8735f29a151d420d
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# Versionshinweise für Adobe Commerce 2.4.8-Sicherheits-Patches

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8-p3

Die Adobe Commerce-Version 2.4.8-p3 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.8 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB25-94](https://helpx.adobe.com/security/products/magento/apsb25-94.html).

{{b2b-patches}}

### Highlights

Diese Version umfasst die folgenden Highlights:

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

* Fehlerbehebung für ACP2E-3874: Die REST-API-Antwort für Auftragsdetails enthält jetzt korrekte Werte für `base_row_total`- und `row_total`-Attribute, falls mehrere gleiche Artikel bestellt wurden.

* Fehlerbehebung für -AC-15446: Es wurde ein Fehler in `Magento\Framework\Mail\EmailMessage` behoben, bei dem `getBodyText()` versuchte, eine nicht vorhandene `getTextBody()` Methode in `Symfony\Component\Mime\Message` aufzurufen, um die Kompatibilität mit Magento 2.4.8-p2 und `magento/framework` 103.0.8-p2 sicherzustellen.

{{oct-2025-backports}}

## 2.4.8-p2

Die Adobe Commerce-Version 2.4.8-p2 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.8 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.8-p1

Die Adobe Commerce-Version 2.4.8-p1 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.8 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Highlights

Diese Version umfasst die folgenden Highlights:

* **API-Leistungsverbesserung**: Behebt die Leistungsbeeinträchtigung bei asynchronen Web-API-Endpunkten, die nach dem vorherigen Sicherheits-Patch eingeführt wurden.<!-- AC-14078 -->

* **CMS blockiert den Zugriff** - Löst ein Problem, bei dem Admin-Benutzer mit eingeschränkten Berechtigungen (z. B. Nur-Merchandising-Zugriff) die [!UICONTROL CMS Blocks] nicht anzeigen konnten.

  Zuvor trat bei diesen Benutzern ein Fehler aufgrund fehlender Konfigurationsparameter nach der Installation früherer Sicherheits-Patches auf.<!-- AC-14087 -->

* **Cookie-Kompatibilität** - Löst eine abwärtsinkompatible Änderung auf, die die `MAX_NUM_COOKIES` im Framework betrifft. Diese Aktualisierung stellt das erwartete Verhalten wieder her und stellt die Kompatibilität für Erweiterungen oder Anpassungen sicher, die mit Cookie-Beschränkungen interagieren.<!-- AC-14475 -->

* **Async-Vorgänge** - Eingeschränkte asynchrone Vorgänge zum Überschreiben früherer Kundenbestellungen.<!-- AC-13917 -->

* **Behebung für CVE-2025-47110** - Behebt eine Sicherheitslücke bei E-Mail-Vorlagen.<!-- AC-14695 -->

* **Fehlerbehebung für VULN-31547** - Behebt eine Schwachstelle bei kanonischen Links der Kategorie.<!-- AC-14713 -->

>[!BEGINSHADEBOX]

Die Fehlerbehebungen für CVE-2025-47110 und VULN-31547 sind auch als isolierter Patch verfügbar. Weitere Informationen finden [&#x200B; im Artikel &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50)Wissensdatenbank“.

>[!ENDSHADEBOX]

<!-- Last updated from includes: 2025-10-22 11:16:25 -->
