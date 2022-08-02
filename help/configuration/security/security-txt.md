---
title: Security.txt
description: Erfahren Sie, wie Sie Informationen bereitstellen, die Sicherheitsexperten bei der Meldung von Sicherheitslücken unterstützen.
contributor_name: Kalpesh Mehta from Corra
contributor_link: https://partners.magento.com/portal/details/partner/id/70/
source-git-commit: 27c3914540a0574fa4ff58df50d5cd2c71fb6670
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---


# TXT-Sicherheitsdatei

Wenn von Forschern Sicherheitslücken entdeckt werden, fehlen häufig geeignete Berichtskanäle. Daher werden einige Schwachstellen nicht gemeldet. Der Zweck der `security.txt` [Dateiformat](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) dient dazu, Sicherheitsforschern die Informationen zur Verfügung zu stellen, die sie für die Meldung ihrer Ergebnisse verwenden können.

Händler können ihre Kontaktinformationen für [Sicherheitsfehlerberichterstellung](https://docs.magento.com/user-guide/stores/security-issue-reporting.html) aus dem Handel _Admin_. Für Entwickler wird die Variable `Magento_Securitytxt` -Modul bietet die folgende Funktionalität:

- Ermöglicht das Speichern von Sicherheitskonfigurationen über die _Admin_.
- Enthält einen Router, der der Anwendungsaktionsklasse für Anforderungen an die `.well-known/security.txt` und `.well-known/security.txt.sig` Dateien.
- Stellt den Inhalt der `.well-known/security.txt` und `.well-known/security.txt.sig` Dateien.

Eine gültige `security.txt` -Datei könnte wie folgt aussehen:

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

So erstellen Sie die `security.txt` signature (`security.txt.sig`) Datei:

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

Überprüfen der Signatur:

```bash
gpg --verify security.txt.sig security.txt
```
