---
title: Best Practices für die Bereitstellung statischer Inhalte
description: Erfahren Sie, wie Sie Probleme mit statischen Inhalten vermeiden können, die nicht in Ihrer Adobe Commerce-Storefront angezeigt werden.
role: Developer
feature: Best Practices
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Best Practices für die Bereitstellung statischer Inhalte

In diesem Artikel werden Best Practices für die Bereitstellung statischer Inhalte (SCD) in Adobe Commerce vorgestellt, um Probleme zu vermeiden, bei denen statische Inhalte nicht auf Ihrer Website verfügbar sind.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

* Adobe Commerce auf Cloud-Infrastruktur
* Adobe Commerce vor Ort

## Best Practices

Um zu vermeiden, dass statische Inhalte auf Ihrer Website nicht verfügbar sind, befolgen Sie die folgenden Best Practices, um sicherzustellen, dass Ihre statischen Inhalte richtig konfiguriert und bereitgestellt werden:

1. Beachten Sie dabei die Implementierungsrichtlinien:
   * Informationen zu Adobe Commerce vor Ort (alle Versionen) finden Sie unter [Übersicht über die Bereitstellung](../../../configuration/deployment/overview.md) in unserer Entwicklerdokumentation.
   * Informationen zu Adobe Commerce in der Cloud-Infrastruktur (alle Versionen) finden Sie unter [Cloud-Implementierungsprozess](https://devdocs.magento.com/cloud/deploy/cloud-deployment-process.html) und [Strategien zur Bereitstellung statischer Inhalte](https://devdocs.magento.com/cloud/deploy/static-content-deployment.html) in unserer Entwicklerdokumentation.

1. Stellen Sie für Adobe Commerce in der Cloud-Infrastruktur (alle Versionen) sicher, dass die Eece-Tools in der neuesten Version verfügbar sind. Siehe: [Aktualisieren der ece-tools-Version](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) in unserer Entwicklerdokumentation.
1. Stellen Sie bei Adobe Commerce in der Cloud-Infrastruktur (alle Versionen) sicher, dass statische Inhalte während der Build-Phase und nicht in der Bereitstellungsphase bereitgestellt werden. Siehe: [Konfigurationsverwaltung für Speichereinstellungen - Leistung bei der Bereitstellung statischer Inhalte](https://devdocs.magento.com/cloud/live/sens-data-over.html#cloud-confman-scd-over) in unserer Entwicklerdokumentation.
1. Vergewissern Sie sich, dass Sie keine langwierigen Cron-Aufträge haben und langwierige Cron-Prozesse beenden. Lange laufende Cron-Aufträge können CPU-Ressourcen in Anspruch nehmen und die Bereitstellungszeit möglicherweise erheblich verkürzen.
1. Überprüfen Sie bei lokalen Adobe Commerce-Versionen (alle Versionen), ob der `php`-Prozess in der CLI Zugriff auf den Ordner &quot;`pub/static`&quot;hat. Andernfalls kann es zu einem Problem kommen, bei dem eine Bereitstellung statischer Inhalte keine Dateien in diesen Ordner schreiben kann. Weitere Informationen: [Zugriffsberechtigungen für Dateisysteme](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) in unserer Entwicklerdokumentation.
1. Stellen Sie sicher, dass der Ordner &quot;`generated`&quot;kein freigegebener Ordner ist, da Builds andernfalls zufällig fehlschlagen könnten. Weitere Informationen:
   * Adobe Commerce vor Ort (alle Versionen): [Technische Details](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) in unserer Entwicklerdokumentation.
   * Adobe Commerce on Cloud Infrastructure (alle Versionen): [Implementierungsprozess - Phase 2: Build](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) in unserer Entwicklerdokumentation.

1. Überprüfen Sie Ihre SCD-Strategie. Die Strategie *quick* ist die Standardstrategie. Weitere Informationen:
   * Adobe Commerce vor Ort (alle Versionen): [Bereitstellungsstrategien für statische Dateien](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) in unserer Entwicklerdokumentation.
   * Adobe Commerce für Cloud-Infrastruktur (alle Versionen): [Bereitstellen von Variablen - SCD\_STRATEGY](https://devdocs.magento.com/cloud/env/variables-deploy.html#scd_strategy) in unserer Entwicklerdokumentation.

## Weitere Informationen

In unserer Entwicklerdokumentation:

* [Statischer Inhaltsbehälter](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [Statische Inhaltssignierung](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [Bereitstellen von Variablen - STATIC\_CONTENT\_SYMLINK](https://devdocs.magento.com/cloud/env/variables-deploy.html#static_content_symlink)
* [Implementierungsfluss](../../../performance/deployment-flow.md)
* [Keine Ausfallzeitbereitstellung](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html)
* [Optimieren der Cloud-Implementierung](https://devdocs.magento.com/cloud/deploy/optimize-cloud-deployment.html)
