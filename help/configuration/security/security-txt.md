---
title: Security.txt
description: Erfahren Sie, wie Sie Informationen bereitstellen, um Sicherheitsforscher bei der Meldung von Sicherheitslücken zu unterstützen.
feature: Configuration, Security
badge: label="Ein Beitrag von Kalpesh Mehta aus Corra" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# TXT-Sicherheitsdatei

Wenn Sicherheitslücken von Forschern entdeckt werden, fehlen oft geeignete Berichtskanäle. Daher werden einige Sicherheitslücken nicht gemeldet. Der Zweck der Datei `security.txt`[Dateiformat](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) ist es, Sicherheitsforschern die Informationen bereitzustellen, die sie verwenden können, um ihre Ergebnisse zu melden.

Händler können ihre Kontaktinformationen für die [Meldung von Sicherheitsproblemen](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-issue-reporting) über Commerce _Admin_ eingeben. Für Entwickler bietet das `Magento_Securitytxt`-Modul die folgenden Funktionen:

- Ermöglicht das Speichern von Sicherheitskonfigurationen unter &quot;_&quot;_.
- Enthält einen Router für die Anwendungsaktionsklasse für Anfragen an die `.well-known/security.txt`- und `.well-known/security.txt.sig`.
- Stellt den Inhalt der `.well-known/security.txt`- und `.well-known/security.txt.sig` bereit.

Eine gültige `security.txt`-Datei könnte wie folgt aussehen:

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

So erstellen Sie die `security.txt` Signaturdatei (`security.txt.sig`):

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

So überprüfen Sie die Signatur:

```bash
gpg --verify security.txt.sig security.txt
```
