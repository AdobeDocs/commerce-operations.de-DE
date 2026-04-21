---
title: Patch-Veröffentlichungszeitplan
description: Erfahren Sie, wann Adobe die Veröffentlichung neuer Patches und Sicherheitsfehlerbehebungen für Adobe Commerce plant.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: 0f46bdfd0afbca07e0d60e995ee9426f5408671d
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 4%

---


# Patch-Veröffentlichungszeitplan

Adobe ist stets bestrebt, ein ausgewogenes Verhältnis zwischen einfachen und vorhersehbaren Produktaktualisierungen und einer schnelleren Bereitstellung von Verbesserungen für frühzeitige Anwender zu finden (siehe [Versionierungsrichtlinie](versioning-policy.md)).

Dieser Zeitplan enthält Termine für die Ankündigung der Veröffentlichung von [patches](versioning-policy.md#patch-release) für jede unterstützte Versionszeile der Adobe Commerce PHP-Kernanwendung durch Adobe. Patch-Versionen bieten die Möglichkeit, die Kern-Code-Basis zu aktualisieren, um Ihre Plattform sicher, zuverlässig und leistungsfähig zu halten.

>[!NOTE]
>
>Weitere Informationen zu neuen Funktionen, zur Cloud-Infrastruktur und zu Erweiterbarkeitsversionen finden Sie in der [Adobe Commerce Services](https://experienceleague.adobe.com/en/docs/commerce/user-guides/release-information/release-notes-all)-Versionsdokumentation.

Zusätzlich zu den auf dieser Seite aufgelisteten geplanten Qualitäts-, Sicherheits- und Beta-Patches bietet Adobe über das [Quality Patches Tool](versioning-policy.md#individual-patch) Zugriff auf [einzelne Patches](../tools/quality-patches-tool/usage.md). Mit dem Tool können Sie allgemeine Informationen über alle einzelnen Patches, die für die installierte Version von Adobe Commerce verfügbar sind, anwenden, zurücksetzen und anzeigen.

Adobe Commerce-Patch-Versionen werden auf der Grundlage der folgenden Richtlinien veröffentlicht:

- **Isolierte Sicherheits-Patch** Datei: Einzelne, nicht kumulative [Sicherheits-Patch-Dateien](versioning-policy.md#isolated-security-patch-file) werden unabhängig voneinander veröffentlicht, um eine schnellere Behebung zu ermöglichen, und werden in den nächsten vollständigen Sicherheits-Patch integriert. Um eine isolierte Sicherheits-Patch-Datei anwenden zu können, müssen Kunden für ihre unterstützte Version die neueste Patch-Version verwenden (die neueste -p-Version), da isolierte Sicherheits-Fehlerbehebungen ausschließlich mit dieser Version getestet werden.

- **Sicherheits-Patches** - [Sicherheits-Patches](versioning-policy.md#security-patch-release) werden jährlich für alle [unterstützten &#x200B;](lifecycle-policy.md) veröffentlicht. Diese Patches enthalten alle zuvor veröffentlichten Sicherheits-, Compliance- und Qualitäts-Hotfixes.  Adobe veröffentlicht möglicherweise zusätzliche Sicherheits-Patches, dies ist jedoch nicht garantiert.

- **Patch** - Ein vollständiger [Patch](versioning-policy.md#patch-release) für die Adobe Commerce 2.4.x LTS-Version (3 Jahre Support) wird jährlich (Mai) veröffentlicht.

- **Alpha Patches**-One [Alpha Patch](versioning-policy.md#alpha-patch-release) für Adobe Commerce 2.4.x LTS wird jährlich veröffentlicht.

- **Beta-Patches** - Ein [Beta-Patches](versioning-policy.md#beta-patch-release) für die Adobe Commerce 2.4.x LTS-Release-Reihe wird jährlich veröffentlicht.

Weitere Informationen finden Sie in der folgenden Abbildung:

<!-- The SVG source for the following image is located here: /help/assets/release/release-calendar.drawio.svg -->

![Adobe Commerce-Veröffentlichungskalender 2026](../assets/release/release-calendar.png)


## Benachrichtigungskanäle für Veröffentlichung

Adobe benachrichtigt Kunden über neue Patch-Versionen über die folgenden Kanäle:

- [Adobe-Sicherheitsbulletins und -beratungen](https://helpx.adobe.com/security/security-bulletin.html#magento)
- E-Mail
- Warnhinweise im Produkt

>[!NOTE]
>
> Die Veröffentlichungstermine für alle Minor-, Patch- und Sicherheits-Versionen sowie das Ende des regulären Supports finden Sie unter [Veröffentlichte Versionen](https://experienceleague.adobe.com/en/docs/commerce-operations/release/versions).
