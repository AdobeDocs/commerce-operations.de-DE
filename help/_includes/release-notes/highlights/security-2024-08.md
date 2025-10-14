---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---
# Sicherheits-Patch-Highlights vom August 2024

Diese Version umfasst die folgenden Highlights:

* **Ratenbegrenzung für[!DNL one-time passwords]** - Die folgenden neuen Systemkonfigurationsoptionen sind jetzt verfügbar, um die Ratenbegrenzung für [!DNL two-factor authentication (2FA)] [!DNL one-time password (OTP)] zu aktivieren:

   * [!UICONTROL **Limit für Wiederholungsversuche für Zwei-Faktor-Authentifizierung**]
   * [!UICONTROL **Sperrzeit für Zwei-Faktor-Authentifizierung (Sekunden)**]

  Adobe empfiehlt, einen Schwellenwert für die 2FA-OTP-Validierung festzulegen, um die Anzahl der Wiederholungsversuche zu begrenzen und Brute-Force-Angriffe abzuschwächen. Weitere Informationen finden [&#x200B; unter &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-admin/config/security/2fa) > 2FA _Konfigurationshandbuch_. <!-- AC-12095 -->

* **Rotation des Verschlüsselungsschlüssels** - Ein neuer CLI-Befehl ist jetzt verfügbar, um den Verschlüsselungsschlüssel zu ändern. Weitere Informationen finden Sie [&#x200B; Knowledgebase-Artikel „Fehlerbehebung bei der Rotation von Verschlüsselungsschlüsseln: CVE-2024-34102](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102)&quot;.

* **Behebung für [CVE-2020-27511](https://nvd.nist.gov/vuln/detail/CVE-2020-27511)** - Behebt eine [!DNL Prototype.js] Sicherheitslücke.<!-- AC-11936 -->

* **Behebung für [CVE-2024-39397](https://nvd.nist.gov/vuln/detail/CVE-2024-39397)** - Löst eine Sicherheitslücke bei der Remote-Codeausführung. Diese Sicherheitslücke betrifft Händler, die den Apache-Webserver für lokale oder selbst gehostete Bereitstellungen verwenden. Diese Fehlerbehebung ist auch als isolierter Patch verfügbar. Weitere Informationen finden Sie [&#x200B; Knowledgebase-Artikel „Sicherheitsupdate für Adobe Commerce verfügbar - APSB](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-61)-61“<!-- ACSD-60551 -->
