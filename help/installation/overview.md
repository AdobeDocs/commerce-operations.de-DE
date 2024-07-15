---
title: Übersicht über die Vor-Ort-Installation
description: Erfahren Sie mehr über den Installationsprozess für lokale Bereitstellungen von Adobe Commerce.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 7%

---

# Übersicht über die Vor-Ort-Installation

>[!NOTE]
>
>Das folgende Diagramm bietet einen allgemeinen Überblick über die _**Vor-Ort**_-Installationen von Adobe Commerce:

![Funktionsweise der Installation](../assets/installation/install-diagram-24.svg)

Der allgemeine Installationsfluss sieht wie folgt aus:

1. Richten Sie Ihre Serverumgebung ein.

   Installieren Sie die erforderliche Software, einschließlich PHP, Apache, MySQL und der Suchmaschine. Weitere Informationen finden Sie unter [Systemanforderungen](system-requirements.md) .

1. Rufen Sie [Authentifizierungsschlüssel](prerequisites/authentication-keys.md) in das Commerce Composer-Repository ab.

1. Holen Sie sich die Adobe Commerce-Software.

   * (Empfohlen) Rufen Sie das [Composer-Metapaket](composer.md) ab, um Module und deren Abhängigkeiten zu verwalten.

   * Wenn Sie zur Magento Open Source-Codebase beitragen oder die Anwendung anpassen möchten, [klonen](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) Sie das GitHub-Repository. Diese Methode erfordert die Vertrautheit mit GitHub und Composer.

1. Installieren Sie das Programm über die Befehlszeile.

   Wenn der Schritt fehlschlägt, weil die erforderliche Software nicht richtig eingerichtet ist, überprüfen Sie die [Voraussetzungen](prerequisites/overview.md).

1. [Überprüfen Sie die Installation, indem Sie Ihre Storefront und den Administrator anzeigen.](next-steps/verify.md)
