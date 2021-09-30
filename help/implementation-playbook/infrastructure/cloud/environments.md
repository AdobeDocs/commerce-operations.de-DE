---
title: Cloud-Infrastruktur-Umgebungen
description: Verwenden Sie die richtigen Umgebungen für die richtigen Anwendungsfälle.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Umgebungen

Die Architektur von Adobe Commerce in Cloud Infrastructure Pro unterstützt Umgebungen, mit denen Sie Ihren Store entwickeln, testen und starten können. Jede Umgebung enthält eine Datenbank und einen Webserver. Die vier von Adobe Commerce verwendeten Umgebungen sind:

- **Integration** - Bietet eine einzige Umgebungsverzweigung und Sie können bis zu vier weitere Umgebungsverzweigungen erstellen. Dies ermöglicht maximal fünf aktive Verzweigungen, die in Platform-as-a-Service-Containern (PageS) bereitgestellt werden.

- **Staging**: Bietet eine einzige Umgebungsverzweigung, die für dedizierte Infrastruktur-as-a-Service-Container (IAAs) bereitgestellt wird.

- **Produktion** - Bietet eine einzige Umgebungsverzweigung, die für dedizierte Infrastruktur-as-a-Service-Container (IAAs) bereitgestellt wird.

- **Globales Übergeordnetes** - Bietet eine Übergeordnete Verzweigung, die in Platform-as-a-Service-Containern (PageS) bereitgestellt wird.

![Abbildung der Beziehung zwischen Adobe Commerce-Cloud-Umgebungen](../../../assets/playbooks/environment-diagram.svg)

## Git-Verzweigungen

Die Integrationsumgebung bietet eine zentrale Integrationsverzweigung, die Ihren Adobe Commerce-Code enthält, der in Platform-as-a-Service-Containern (PageS) bereitgestellt wird.

Der Adobe Commerce in Cloud-Infrastrukturumgebungen unterstützt einen flexiblen, kontinuierlichen Integrationsprozess. Beginnen Sie mit dem Klonen der Integrationsverzweigung in Ihrem lokalen Projektordner. Erstellen Sie eine neue Verzweigung oder mehrere Zweige, um neue Funktionen zu entwickeln, Änderungen zu konfigurieren und Erweiterungen hinzuzufügen. Mit einer entwickelten Codeverzweigung und den entsprechenden Konfigurationsdateien können Ihre Codeänderungen mit der Integrationsverzweigung zusammengeführt werden, um umfassendere Tests zu ermöglichen.

![Abbildung der Git-basierten Verzweigungsstrategie für Adobe Commerce-Cloud-Umgebungen](../../../assets/playbooks/branching-diagram.svg)
