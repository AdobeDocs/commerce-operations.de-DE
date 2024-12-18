---
title: Übersicht über die lokale Installation
description: Erfahren Sie mehr über den Installationsprozess für lokale Bereitstellungen von Adobe Commerce.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 7%

---

# Übersicht über die lokale Installation

>[!NOTE]
>
>Das folgende Diagramm bietet einen allgemeinen Überblick über _**On-Premise**_-Installationen von Adobe Commerce:

![Funktionsweise der Installation](../assets/installation/install-diagram-24.svg)

Der allgemeine Installationsablauf ist wie folgt:

1. Richten Sie Ihre Server-Umgebung ein.

   Installieren Sie die erforderliche Software, einschließlich PHP, Apache, MySQL und der Suchmaschine. Weitere Informationen finden Sie [Systemanforderungen](system-requirements.md).

1. Abrufen [Authentifizierungsschlüssel](prerequisites/authentication-keys.md) zum Commerce Composer-Repository.

1. Holen Sie sich die Adobe Commerce-Software.

   * (Empfohlen) Rufen Sie das [Composer-Metapaket](composer.md) ab, um Module und ihre Abhängigkeiten zu verwalten.

   * Wenn Sie einen Beitrag zur Magento Open Source-Code-Basis leisten oder das Programm anpassen möchten, [ Sie das GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)Repository (klonen). Diese Methode erfordert Vertrautheit mit GitHub und Composer.

1. Installieren Sie die Anwendung über die Befehlszeile.

   Wenn der Schritt fehlschlägt, weil die erforderliche Software nicht ordnungsgemäß eingerichtet ist, überprüfen Sie die [Voraussetzungen](prerequisites/overview.md).

1. [Überprüfen](next-steps/verify.md) Sie die Installation, indem Sie Ihre Storefront und den Administrator anzeigen.
