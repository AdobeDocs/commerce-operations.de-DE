---
title: Best Practices für Erweiterungen
description: Erfahren Sie, wie Sie Leistungsprobleme vermeiden können, die durch Adobe Commerce-Erweiterungen von Drittanbietern verursacht werden.
role: Admin
feature: Best Practices, Extensions
exl-id: 95d2c7bf-fd2f-4c98-8293-96d69b86341f
source-git-commit: 1fdbded7738365593ef7da64f4dbe6713984bff3
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---

# Best Practices für Erweiterungen

Adobe Commerce-Erweiterungen (Module) von Drittanbietern können verschiedene Probleme verursachen, die sich negativ auf die Leistung der Storefront auswirken können. Sie können diese Probleme vermeiden, indem Sie die folgenden Best Practices befolgen:

- Entwickeln Sie Ihre Commerce-Integrationen und -Anpassungen mit [Out-of-Process-Erweiterbarkeit](https://developer.adobe.com/commerce/extensibility/) wo immer möglich, um die Wartung und Upgrades zu vereinfachen.
- Herunterladen und Kaufen von Drittanbietererweiterungen von einer vertrauenswürdigen Quelle, z. B. der [Commerce Marketplace](https://marketplace.magento.com/extensions.html).
- Aktualisieren Sie alle Erweiterungen von Drittanbietern auf die neueste Version.
- Wenn Sie Ihre Drittanbietererweiterungen nicht auf dem neuesten Stand halten können, sollten Sie andere Erweiterungen verwenden.
- Stellen Sie bei der Planung eines Upgrades auf eine neue Version von Adobe Commerce sicher, dass die installierten Erweiterungen von Drittanbietern mit der neuen Version kompatibel sind, und aktualisieren Sie die Erweiterungen, falls erforderlich.

>[!NOTE]
>
> Alle im Adobe Commerce Marketplace verfügbaren Erweiterungen sind erforderlich, um die Kompatibilität mit neuen Commerce-Versionen zu gewährleisten. Siehe [Versionskompatibilität](https://developer.adobe.com/commerce/marketplace/guides/sellers/compatibility/releases/).

## Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

## Weitere Informationen

- [Best Practices für die Planung von Upgrades](../../../upgrade/prepare/best-practices.md)
- Verwenden von Erweiterungen von Drittanbietern mit Adobe Commerce in der Cloud-Infrastruktur
   - [Technologien und Anforderungen - Entwicklung und Testen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-devtest)
   - [Warum sollten Sie die Integration und das Staging vollständig testen?](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/launch/overview#why-test-fully-in-integration-staging-and-production)
