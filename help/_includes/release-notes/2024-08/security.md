---
source-git-commit: 07947c20ef49d1b3ad5df441c0a47982216ff36f
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---
# Sicherheits-Patch vom August 2024 - Highlights

Diese Version umfasst die folgenden Highlights:

* **Ratenbegrenzung für[!DNL one-time passwords]** - Die folgenden neuen Systemkonfigurationsoptionen sind jetzt verfügbar, um die Ratenbegrenzung bei der Validierung von [!DNL two-factor authentication (2FA)] [!DNL one-time password (OTP)] zu aktivieren:

   * [!UICONTROL **Versuchslimit für Zweifaktorauthentifizierung wiederholen**]
   * [!UICONTROL **Sperrzeit für die Authentifizierung mit zwei Faktoren (Sekunden)**]

  Adobe rät, einen Schwellenwert für die 2FA OTP-Validierung festzulegen, um die Anzahl der Wiederholungsversuche zur Abmilderung von Brute-Force-Angriffen zu begrenzen. Weitere Informationen finden Sie unter [Sicherheit > 2FA](https://experienceleague.adobe.com/en/docs/commerce-admin/config/security/2fa) im _Konfigurationshandbuch_. <!-- AC-12095 -->

* **Verschlüsselungsschlüsselrotation**: Ein neuer CLI-Befehl ist jetzt zum Ändern des Verschlüsselungsschlüssels verfügbar. Weitere Informationen finden Sie im Knowledge Base-Artikel [Fehlerbehebung beim Rotieren des Verschlüsselungsschlüssels: CVE-2024-34102](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102) .

* **Korrektur für [CVE-2020-27511](https://nvd.nist.gov/vuln/detail/CVE-2020-27511)** - Löst eine [!DNL Prototype.js] Sicherheitslücke auf.<!-- AC-11936 -->

* **Fehlerbehebung für [CVE-2024-39397](https://nvd.nist.gov/vuln/detail/CVE-2024-39397)** - Löst eine Sicherheitslücke bei der Ausführung von Remote-Code auf. Diese Sicherheitslücke betrifft Händler, die den Apache-Webserver für lokale oder selbstgehostete Bereitstellungen verwenden. Diese Fehlerbehebung ist auch als separater Patch verfügbar. Weitere Informationen finden Sie im Artikel [Sicherheitsupdate für Adobe Commerce - APSB24-61](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-61) Knowledge Base .<!-- ACSD-60551 -->
