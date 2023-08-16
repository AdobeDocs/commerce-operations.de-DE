---
title: Übersicht über die Vor-Ort-Installation
description: Erfahren Sie mehr über den Installationsprozess für lokale Bereitstellungen von Adobe Commerce und Magento Open Source.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# Übersicht über die Vor-Ort-Installation

>[!NOTE]
>
>Das folgende Diagramm bietet einen allgemeinen Überblick über _**vor Ort**_ Installationen von Adobe Commerce und Magento Open Source:

![Funktionsweise der Installation](../assets/installation/install-diagram-24.svg)

Der allgemeine Installationsfluss sieht wie folgt aus:

1. Richten Sie Ihre Serverumgebung ein.

   Installieren Sie die erforderliche Software, einschließlich PHP, Apache, MySQL und der Suchmaschine. Siehe [Systemanforderungen](system-requirements.md) für weitere Informationen.

1. Get [Authentifizierungsschlüssel](prerequisites/authentication-keys.md) zum Commerce Composer-Repository hinzufügen.

1. Rufen Sie die Adobe Commerce- oder Magento Open Source-Software ab.

   * (Empfohlen) Rufen Sie die [Composer-Metapaket](composer.md) um Module und ihre Abhängigkeiten zu verwalten.

   * Wenn Sie zur Magento Open Source-Codebase beitragen oder die Anwendung anpassen möchten, [clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) das GitHub-Repository. Diese Methode erfordert die Vertrautheit mit GitHub und Composer.

1. Installieren Sie das Programm über die Befehlszeile.

   Wenn der Schritt fehlschlägt, weil die erforderliche Software nicht richtig eingerichtet ist, überprüfen Sie die [Voraussetzungen](prerequisites/overview.md).

1. [Überprüfen](next-steps/verify.md) die Installation durch Anzeige Ihrer Storefront und des Administrators.
