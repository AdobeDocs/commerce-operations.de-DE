---
title: Best Practices für Erweiterungen
description: Erfahren Sie, wie Sie Leistungsprobleme vermeiden können, die durch Adobe Commerce-Erweiterungen von Drittanbietern verursacht werden.
role: Admin
feature: Best Practices, Extensions
exl-id: 95d2c7bf-fd2f-4c98-8293-96d69b86341f
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
    internal-label: Commerce ecosystem
subfeature_v2:
  - id: dad884f1-e840-49a1-970e-2f965bdbc410
    internal-label: Extensions
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%
---
# Best Practices für Erweiterungen

Adobe Commerce-Erweiterungen (Module) von Drittanbietern können verschiedene Probleme verursachen, die sich negativ auf die Leistung der Storefront auswirken können. Sie können diese Probleme vermeiden, indem Sie die folgenden Best Practices befolgen:

- Entwickeln Sie Ihre Commerce-Integrationen und -Anpassungen mit [Out-of-Process-Erweiterbarkeit](https://developer.adobe.com/commerce/extensibility/) wo immer möglich, um die Wartung und Upgrades zu vereinfachen.
- Herunterladen und Kaufen von Drittanbietererweiterungen aus einer vertrauenswürdigen Quelle, z. B. der [Commerce Marketplace](https://commercemarketplace.adobe.com//extensions.html).
- Aktualisieren Sie alle Erweiterungen von Drittanbietern auf die neueste Version.
- Wenn Sie Ihre Drittanbietererweiterungen nicht auf dem neuesten Stand halten können, sollten Sie andere Erweiterungen verwenden.
- Stellen Sie bei der Planung eines Upgrades auf eine neue Version von Adobe Commerce sicher, dass die installierten Erweiterungen von Drittanbietern mit der neuen Version kompatibel sind, und aktualisieren Sie die Erweiterungen, falls erforderlich.

>[!NOTE]
>
> Alle im Adobe Commerce Marketplace verfügbaren Erweiterungen sind erforderlich, um die Kompatibilität mit neuen Commerce-Versionen zu gewährleisten. Siehe [Versionskompatibilität](https://developer.adobe.com/commerce/marketplace/guides/sellers/compatibility/releases).

## Betroffene Produkte und Versionen

[Alle unterstützten &#x200B;](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

## Weitere Informationen

- [Best Practices für die Planung von Upgrades](../../../upgrade/prepare/best-practices.md)
- Verwenden von Erweiterungen von Drittanbietern mit Adobe Commerce in der Cloud-Infrastruktur
  - [Technologien und Anforderungen - Entwicklung und Testen](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/overview#cloud-req-devtest)
  - [Warum sollten Sie in Integration und Staging vollständig testen?](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/launch/overview#why-test-fully-in-integration-staging-and-production)
