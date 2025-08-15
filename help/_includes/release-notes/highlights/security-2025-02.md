---
source-git-commit: 6ca34e8713f4f138961786de206cd360f0bc1be7
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---
# Sicherheitspatch-Highlights vom Februar 2025

Diese Version umfasst die folgenden Highlights:

* **Verwalten von Verschlüsselungsschlüsseln und erneutes Verschlüsseln von Daten** - Neu konzipiertes Verwalten von Verschlüsselungsschlüsseln, um die Benutzerfreundlichkeit zu verbessern und frühere Einschränkungen und Fehler zu beseitigen.<!-- AC-12679 -->

  Neue CLI-Befehle sind jetzt für [Ändern](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/security/encryption-key) von Schlüsseln und [Neuverschlüsseln](https://developer.adobe.com/commerce/php/development/security/data-encryption/) bestimmter Systemkonfigurations-, Zahlungs- und benutzerdefinierter Felddaten verfügbar. Das Ändern von Schlüsseln in der Admin-Benutzeroberfläche wird in dieser Version nicht mehr unterstützt. Sie müssen die CLI-Befehle verwenden.

* **Behebung für [CVE-2025-24434](https://nvd.nist.gov/vuln/detail/CVE-2025-24434)** - Behebt eine Autorisierungslücke.

  Diese Fehlerbehebung ist auch als isolierter Patch verfügbar. Weitere Informationen finden Sie [ „Knowledge](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08)Base-Artikel“<!-- AC-12755 -->

* **TinyMCE-**: Die TinyMCE-Abhängigkeit wurde von Version 7 auf 6.8.5 heruntergestuft, um Probleme mit der Lizenzkompatibilität zu beheben.

  Durch diese Änderung wird die kontinuierliche Konformität sichergestellt, während Adobe einen alternativen Open-Source-WYSIWYG-Editor evaluiert.
