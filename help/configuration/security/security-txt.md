---
title: security.txt
description: Erfahren Sie, wie Sie Informationen bereitstellen, um Sicherheitsforscher bei der Meldung von Sicherheitslücken zu unterstützen.
feature: Configuration, Security
badge: label="Ein Beitrag von Kalpesh Mehta aus Corra" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%
---
# TXT-Sicherheitsdatei

Wenn Sicherheitslücken von Forschern entdeckt werden, fehlen oft geeignete Berichtskanäle. Daher werden einige Sicherheitslücken nicht gemeldet. Der Zweck der Datei `security.txt`[Dateiformat](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) ist es, Sicherheitsforschern die Informationen bereitzustellen, die sie verwenden können, um ihre Ergebnisse zu melden.

Händler können ihre Kontaktinformationen für die [Meldung von Sicherheitsproblemen](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/security/security-issue-reporting) über Commerce _Admin_ eingeben. Für Entwickler bietet das `Magento_Securitytxt`-Modul die folgenden Funktionen:

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

```shell
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

So überprüfen Sie die Signatur:

```shell
gpg --verify security.txt.sig security.txt
```
