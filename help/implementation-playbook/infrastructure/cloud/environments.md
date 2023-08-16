---
title: Cloud-Infrastruktur-Umgebungen
description: Verwenden Sie die richtigen Umgebungen für die richtigen Anwendungsfälle.
exl-id: 0c36145f-8de2-45e5-9050-9acbc9fb6100
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Umgebungen

Die Architektur von Adobe Commerce on Cloud Infrastructure Pro unterstützt Umgebungen, mit denen Sie Ihren Store entwickeln, testen und starten können. Jede Umgebung enthält eine Datenbank und einen Webserver. Die vier von Adobe Commerce verwendeten Umgebungen sind:

- **Integration**—Stellt eine einzige Umgebungsverzweigung bereit und Sie können bis zu vier weitere Umgebungsverzweigungen erstellen. Dies ermöglicht maximal fünf aktive Verzweigungen, die in Platform-as-a-Service-Containern (PageS) bereitgestellt werden.

- **Staging**—Bietet eine einzige Umgebungsverzweigung, die für dedizierte Infrastruktur-as-a-Service-Container (IAAs) bereitgestellt wird.

- **Produktion**—Bietet eine einzige Umgebungsverzweigung, die für dedizierte Infrastruktur-as-a-Service-Container (IAAs) bereitgestellt wird.

- **Globaler Master**—Stellt eine Masterverzweigung bereit, die in Platform-as-a-Service-Containern (PageS) bereitgestellt wird.

![Abbildung der Beziehung zwischen Adobe Commerce-Cloud-Umgebungen](../../../assets/playbooks/environment-diagram.svg)

## Git-Verzweigungen

Die Integrationsumgebung bietet eine zentrale Integrationsverzweigung, die Ihren Adobe Commerce-Code enthält, der in Platform-as-a-Service-Containern (PageS) bereitgestellt wird.

Die Adobe Commerce zu Cloud-Infrastrukturumgebungen unterstützen einen flexiblen, kontinuierlichen Integrationsprozess. Beginnen Sie mit dem Klonen der Integrationsverzweigung in Ihrem lokalen Projektordner. Erstellen Sie eine neue Verzweigung oder mehrere Zweige, um neue Funktionen zu entwickeln, Änderungen zu konfigurieren und Erweiterungen hinzuzufügen. Mit einer entwickelten Codeverzweigung und den entsprechenden Konfigurationsdateien können Ihre Codeänderungen mit der Integrationsverzweigung zusammengeführt werden, um umfassendere Tests zu ermöglichen.

![Abbildung der Git-basierten Verzweigungsstrategie für Adobe Commerce-Cloud-Umgebungen](../../../assets/playbooks/branching-diagram.svg)
