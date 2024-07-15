---
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 1%

---
# Sensible Daten

Adobe Commerce verschlüsselt Folgendes mit Ihrem Verschlüsselungsschlüssel:

* Kreditkarteninformationen
* Benutzernamen und Kennwörter, die in der Admin-Konfiguration angegeben sind (z. B. Anmeldungen bei Payment Gateways)
* CAPTCHA-Werte, die über das Netzwerk gesendet werden

Adobe Commerce verschlüsselt *nicht*:

* Administrations- und Kundenbenutzernamen und -kennwörter (diese Kennwörter werden gehasht)
* Adresse
* Telefonnummer
* Sonstige Arten von persönlich identifizierbaren Informationen außer Kreditkartennummern
