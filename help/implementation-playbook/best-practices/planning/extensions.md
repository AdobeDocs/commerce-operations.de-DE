---
title: Best Practices für Erweiterungen
description: Erfahren Sie, wie Sie Leistungsprobleme vermeiden, die durch Adobe Commerce-Erweiterungen von Drittanbietern verursacht werden.
role: Admin
feature: Best Practices, Extensions
exl-id: 95d2c7bf-fd2f-4c98-8293-96d69b86341f
source-git-commit: 1fdbded7738365593ef7da64f4dbe6713984bff3
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---

# Best Practices für Erweiterungen

Adobe Commerce-Erweiterungen von Drittanbietern (Module) können verschiedene Probleme verursachen, die sich negativ auf die Storefront-Leistung auswirken können. Sie können diese Probleme vermeiden, indem Sie die folgenden Best Practices befolgen:

- Entwickeln Sie Ihre Commerce-Integrationen und -Anpassungen nach Möglichkeit mit der Out-of-Process-Erweiterbarkeit](https://developer.adobe.com/commerce/extensibility/) von [, um die Wartung und Upgradefähigkeit zu vereinfachen.
- Laden Sie Erweiterungen von Drittanbietern von einer vertrauenswürdigen Quelle herunter und kaufen Sie sie, z. B. [Commerce Marketplace](https://marketplace.magento.com/extensions.html).
- Aktualisieren Sie alle Drittanbietererweiterungen auf die neueste Version.
- Wenn Sie die Erweiterungen von Drittanbietern nicht aktualisieren können, sollten Sie verschiedene Erweiterungen in Erwägung ziehen.
- Überprüfen Sie bei der Planung eines Upgrades auf eine neue Version von Adobe Commerce, ob installierte Drittanbietererweiterungen mit der neuen Version kompatibel sind, und aktualisieren Sie die Erweiterungen bei Bedarf.

>[!NOTE]
>
> Alle im Adobe Commerce Marketplace verfügbaren Erweiterungen sind erforderlich, um die Kompatibilität mit neuen Commerce-Versionen zu gewährleisten. Siehe [Release-Kompatibilität](https://developer.adobe.com/commerce/marketplace/guides/sellers/compatibility/releases/).

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Weitere Informationen

- [Best Practices für die Planung von Upgrades](../../../upgrade/prepare/best-practices.md)
- Verwenden von Drittanbietererweiterungen mit Adobe Commerce in der Cloud-Infrastruktur
   - [Technologien und Anforderungen - Entwicklung und Tests](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-devtest)
   - [Warum vollständig in Integration und Staging testen?](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/launch/overview#why-test-fully-in-integration-staging-and-production)
