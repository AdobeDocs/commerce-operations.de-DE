---
title: Best Practices für die Bereitstellung statischer Inhalte
description: Erfahren Sie, wie Sie vermeiden können, dass Probleme mit statischen Inhalten nicht in Ihrer Adobe Commerce-Storefront angezeigt werden.
role: Developer
feature: Best Practices
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Best Practices für die Bereitstellung statischer Inhalte

In diesem Artikel wird über Best Practices zur Bereitstellung statischer Inhalte (SCD) in Adobe Commerce gesprochen, um Probleme zu vermeiden, bei denen der statische Inhalt nicht auf Ihrer Website verfügbar wäre.

## Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

* Adobe Commerce auf Cloud-Infrastruktur
* Adobe Commerce On-Premises

## Best Practices

Um ein Problem zu vermeiden, bei dem statischer Inhalt nicht auf Ihrer Website verfügbar ist, befolgen Sie die folgenden Best Practices, um sicherzustellen, dass Ihr statischer Inhalt ordnungsgemäß konfiguriert und bereitgestellt wird:

1. Stellen Sie sicher, dass Sie die Bereitstellungsrichtlinien befolgen:
   * Informationen zu Adobe Commerce On-Premise (alle Versionen) finden Sie unter [Bereitstellungsübersicht](../../../configuration/deployment/overview.md) in unserer Entwicklerdokumentation.
   * Informationen zu Adobe Commerce in Cloud-Infrastrukturen (alle Versionen) finden Sie [Cloud-Bereitstellungsprozess](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/deploy/process) und [Statische Strategien zur Bereitstellung von Inhalten](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/deploy/static-content) in unserer Entwicklerdokumentation.

1. Stellen Sie bei Adobe Commerce on Cloud Infrastructure (alle Versionen) sicher, dass es sich bei ECE-Tools um die neueste Version handelt. Siehe: [ECE-Tools Version aktualisieren](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package) in unserer Entwicklerdokumentation.
1. Stellen Sie bei Adobe Commerce in der Cloud-Infrastruktur (alle Versionen) sicher, dass statische Inhalte während der Build- und nicht während der Bereitstellungsphase bereitgestellt werden. Siehe: [Konfigurationsverwaltung für Store-Einstellungen - Leistung bei der Bereitstellung statischer Inhalte](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure-store/store-settings#cloud-confman-scd-over) in unserer Entwicklerdokumentation.
1. Stellen Sie sicher, dass Sie keine lang laufenden Cron-Aufträge haben, und beenden Sie alle lang laufenden Cron-Prozesse. Lang laufende Cron-Aufträge können CPU-Ressourcen beanspruchen und möglicherweise die Bereitstellungszeit erheblich verlängern.
1. Überprüfen Sie bei Adobe Commerce On-Premise (alle Versionen), ob der `php` in CLI Zugriff auf das `pub/static` hat. Andernfalls könnten Sie auf ein Problem stoßen, bei dem eine statische Inhaltsbereitstellung keine Dateien in dieses Verzeichnis schreiben kann. Weitere Informationen finden Sie unter [Zugriffsberechtigungen für Dateisysteme](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html?lang=de) in unserer Entwicklerdokumentation.
1. Stellen Sie sicher, dass der `generated` Ordner kein freigegebener Ordner ist. Andernfalls können Builds nach dem Zufallsprinzip fehlschlagen. Weitere Informationen:
   * Adobe Commerce On-Premise (alle Versionen): [Technische Details](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html?lang=de) in unserer Entwicklerdokumentation.
   * Adobe Commerce auf Cloud-Infrastruktur (alle Versionen): [Bereitstellungsprozess - Phase 2: ](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#cloud-deploy-over-phases-build) in unserer Entwicklerdokumentation.

1. Überprüfen Sie Ihre SCD-Strategie. Die *Quick*-Strategie ist die Standardstrategie. Weitere Informationen:
   * Adobe Commerce On-Premise (alle Versionen): [Strategien zur Bereitstellung statischer Dateien](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html?lang=de) in unserer Entwicklerdokumentation.
   * Adobe Commerce auf Cloud-Infrastruktur (alle Versionen): [Variablen bereitstellen - SCD\_](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#scd_strategy)) in unserer Entwicklerdokumentation.

## Weitere Informationen

In unserer Entwicklerdokumentation:

* [Statischer Inhalts-Container](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [Statische Inhaltssignierung](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html?lang=de)
* [Variablen bereitstellen - STATIC\_CONTENT\_SYMLINK](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#static_content_symlink)
* [Bereitstellungsfluss](../../../performance/deployment-flow.md)
* [Keine Ausfallzeiten bei der Bereitstellung](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/deploy/reduce-downtime)
* [Optimieren der Cloud-Bereitstellung](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/deploy/optimization)
