---
source-git-commit: 8be75548a939008057fb5fdf37ba5b5a0345f6d4
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---
# Über Adobe Commerce-Sicherheits-Patch-Versionen

**Sicherheits-Fehlerbehebung**: Eine Software-Code-Änderung, die ein identifiziertes Sicherheitsproblem behebt und erwartete Ergebnisse in einem betroffenen Produktbereich liefert. Diese Korrekturen sind im Allgemeinen abwärtskompatibel.

**Sicherheitsverbesserung**: Eine Softwareverbesserung oder Konfigurationsänderung, um die Sicherheit innerhalb der Anwendung proaktiv zu verbessern. Mit diesen Sicherheitsverbesserungen werden Sicherheitsrisiken behoben, die sich auf den Sicherheitszustand der Adobe Commerce-Anwendung auswirken, aber möglicherweise abwärtsinkompatibel sind.

Mit Sicherheits-Patch-Versionen können Sie Ihre Site sicherer halten, ohne zusätzliche Qualitätskorrekturen und Verbesserungen anzuwenden, die in einer vollständigen Patch-Version enthalten sind. Sicherheits-Patch-Versionen werden mit &quot;-pN“ angehängt, wobei N die inkrementelle Patch-Version ist, die mit 1 beginnt (z. B. 2.3.5-p1). Sicherheits-Patch-Versionen können auch Hotfixes enthalten, die zur Behebung kritischer Probleme erforderlich sind, die die Adobe Commerce-Anwendung betreffen.

Sicherheits-Patch-Versionen können auch Compliance-bezogene Änderungen enthalten, die erforderlich sind, um sicherzustellen, dass die Adobe Commerce-Anwendung die Compliance-Anforderungen erfüllen kann. Diese Änderungen können abwärtsinkompatible Änderungen mit sich bringen und sind erforderlich, um sicherzustellen, dass alle unterstützten Release-Zeilen konform bleiben.

Jede Sicherheits-Patch-Version basiert auf der vorherigen vollständigen Patch-Version. Es enthält Qualitäts- und Sicherheitskorrekturen aus früheren Patch-Versionen sowie Sicherheitskorrekturen, die zwischen der vorherigen vollständigen Patch-Version und der Sicherheits-Patch-Version erstellt wurden.

Anweisungen zum Herunterladen und Anwenden von Sicherheits-Patches finden Sie unter [So rufen Sie Sicherheits-Patches ab und wenden](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches) in der _Adobe Commerce Knowledgebase_.

{{$include /help/_includes/release-notes/extended-support-policy-note.md}}

## Isolierte Sicherheits-Patch-Datei

Isolierte Sicherheits-Patch-Dateien sind nicht kumulative, eigenständige Patch-Dateien, die Fehlerbehebungen nur für eine oder mehrere Sicherheitslücken enthalten, ohne zusätzliche Funktionsaktualisierungen oder Sicherheitsänderungen. Diese Patches werden unabhängig voneinander veröffentlicht, um eine schnellere Behebung zu ermöglichen, und werden in den nächsten vollständigen Sicherheits-Patch integriert. Details zu den Sicherheitslücken finden Sie im zugehörigen Sicherheitsbulletin, das auf einen Knowledgebase-Artikel (KB) mit Anleitungen zur Anwendung des Patches und zusätzlichen Informationen verweist.

Um eine isolierte Sicherheits-Patch-Datei anwenden zu können, müssen Kunden für ihre unterstützte Version die neueste Patch-Version verwenden (die neueste -p-Version), da isolierte Sicherheits-Patch-Dateien ausschließlich mit dieser Version getestet werden.

Im [Sicherheitscenter](https://helpx.adobe.com/de/security/products/magento.html) finden Sie die neuesten Sicherheitsupdates für Adobe Commerce.

