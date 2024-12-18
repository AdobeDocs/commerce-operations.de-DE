---
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 1%

---
# Sensible Daten

Adobe Commerce verwendet Ihren Verschlüsselungsschlüssel, um Folgendes zu verschlüsseln:

* Kreditkartenangaben
* In der Admin-Konfiguration angegebene Benutzernamen und Kennwörter (z. B. Anmeldungen bei Zahlungs-Gateways)
* Über das Netzwerk gesendete CAPTCHA-Werte

Adobe Commerce *Folgendes nicht*:

* Administrative und kundenspezifische Benutzernamen und Kennwörter (diese Kennwörter werden gehasht)
* Adresse
* Telefonnummer
* Andere Arten von personenbezogenen Daten außer Kreditkartennummern
