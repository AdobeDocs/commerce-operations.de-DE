---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---
# Sensible Daten

Adobe Commerce und Magento Open Source verwenden Ihren Verschlüsselungsschlüssel, um Folgendes zu verschlüsseln:

* Kreditkarteninformationen
* Benutzernamen und Kennwörter, die in der Admin-Konfiguration angegeben sind (z. B. Anmeldungen bei Payment Gateways)
* CAPTCHA-Werte, die über das Netzwerk gesendet werden

Adobe Commerce und Magento Open Source *not* encrypt:

* Administrations- und Kundenbenutzernamen und -kennwörter (diese Kennwörter werden gehasht)
* Adresse
* Telefonnummer
* Sonstige Arten von persönlich identifizierbaren Informationen außer Kreditkartennummern
