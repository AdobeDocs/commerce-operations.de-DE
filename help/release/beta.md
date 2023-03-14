---
title: Beta-Versionen
description: Erfahren Sie mehr über die Beta-Versionen von Adobe Commerce und wie Sie teilnehmen können.
source-git-commit: 1ce0ff87291c5c3f0fd130aa351bc975f42501e3
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# Beta-Versionen von Adobe Commerce

Ab Juni 2023 und in Zukunft wird Adobe öffentliche Betas für Patch-Versionen (&quot;Beta-Versionen&quot;) veröffentlichen. Beta-Versionen sind für alle Adobe Commerce-Kunden und -Partner vor der allgemeinen Verfügbarkeit (GA) verfügbar und umfassen Sicherheits-, Compliance-, Leistungs- und Qualitätsverbesserungen mit hoher Priorität.

>[!IMPORTANT]
>
>Beta-Versionen können Mängel enthalten und werden ohne Gewährleistung jeglicher Art &quot;AS IS&quot; bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern, zu ändern oder anderweitig zu unterstützen (über Adobe Support Services oder anderweitig). Kunden wird empfohlen, Vorsicht walten zu lassen und sich nicht auf die korrekte Funktionsweise oder Leistung der Beta-Versionen und/oder der zugehörigen Dokumentation oder Materialien zu verlassen. Dementsprechend erfolgt die Verwendung der Beta-Versionen ausschließlich auf eigenes Risiko des Kunden.

## Inhalte freigeben

Jede Adobe Commerce Beta-Version enthält alle Änderungen, die bis zum geplanten Veröffentlichungsdatum an den Adobe Commerce-Core-Code gesendet werden, einschließlich, aber nicht beschränkt auf die folgenden Funktionsbereiche:

- Neueste Sicherheitskorrekturen
- Leistungsverbesserungen
- Verbesserungen bei GraphQL
- Allgemeine Fehlerbehebungen für Qualität
- Gemeinschaftsbeiträge
- Erforderliche Änderungen zur Unterstützung der Kompatibilität mit [Adobe Commerce-Dienste](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

## Namenskonvention und -zeitplan

Adobe wird zweimal jährlich Beta-Patches veröffentlichen. Das erste Beta-Patch wird in der Regel drei Monate nach der allgemeinen Verfügbarkeit einer neuen Patch-Version der Kernanwendung veröffentlicht.

Beta-Release-Pakete haben eine `-betaX` Suffix. Die Beta-Release-Pakete von Adobe Commerce 2.4.7 verwenden beispielsweise die folgende Benennungskonvention:

- `2.4.7-beta1`
- `2.4.7-beta2`

Siehe [Release-Zeitplan](schedule.md) für die Liste der anstehenden öffentlichen Beta-Veröffentlichungstermine.

## Vorteile der Teilnahme

Je früher Sie den Code sehen, den wir entwickeln, desto eher können Sie Ihre Technologie und Ihre Händler auf das bevorstehende Upgrade vorbereiten.

Während sich die Dinge ändern können, können Sie durch die Verwendung der Beta-Versionen verstehen, wo sich die Codebase-Änderungen befinden, und mit der Vorbereitung vor dem GA-Veröffentlichungsdatum beginnen.

## Beta-Release-Zugriff

Beta-Versionen von Adobe Commerce werden auf dieselbe Weise wie andere Adobe Commerce-Patch-Versionen bereitgestellt: as Composer-Metapakete in `https://repo.magento.com`. Der Quellcode ist verfügbar unter [GitHub](https://github.com/magento/magento2).

Siehe [Schnellstart für die Installation von Composer](../installation/composer.md) für weitere Details.

## Problemberichte

Adobe bietet für Beta-Versionen keinen standardmäßigen Support-Service für Adoben.

Um Feedback zu Beta-Versionen einzureichen, folgen Sie unserem [regelmäßig auftretender Berichtsfluss](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) on [GitHub](https://github.com/magento/magento2).

Unsere internen Teams werden alle kritischen Probleme überwachen, die im Zusammenhang mit der neuesten Beta-Version gemeldet werden, und sie priorisieren, dass sie vor dem GA-Veröffentlichungsdatum gelöst werden.
