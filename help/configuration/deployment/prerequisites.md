---
title: Voraussetzungen für die Bereitstellung
description: Sehen Sie sich eine Liste der Voraussetzungen für die Bereitstellung von Commerce in einem Entwicklungs-, Build- oder Produktionssystem an.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# Voraussetzungen für Entwicklungs-, Build- und Produktionssysteme

Dateiberechtigungen und -besitz müssen in Entwicklungs-, Build- und Produktionssystemen konsistent sein. Dazu müssen Sie entweder:

- Folgendes:

   - Richten Sie dasselbe ein [Dateisysteminhaber](https://glossary.magento.com/magento-file-system-owner) Benutzername auf allen Systemen
   - Stellen Sie sicher, dass der Webserver auf allen Systemen als derselbe Benutzer ausgeführt wird.
   - Stellen Sie sicher, dass sich der Eigentümer des Dateisystems in der Gruppe der Webserver auf allen Systemen befindet.

- Ändern Sie bei Bedarf die Berechtigungen und das Eigentum für Commerce-Dateisysteme auf jedem System mithilfe der folgenden Richtlinien:

   - Entwicklung und Erstellung: [Legen Sie die Eigentumsrechte und Berechtigungen für die Vorinstallation fest (zwei Benutzer)](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
   - Produktion: [Eigentum und Berechtigungen für Entwicklung und Produktion im Handel](file-system-permissions.md)

>[!INFO]
>
>Wenn Sie diesen Ansatz wählen, müssen Sie bei jedem Abruf von Code aus Ihrem Build-System Dateisystemberechtigungen und -eigentum festlegen (wenn der Eigentümer des Dateisystems oder der Webserver-Benutzer in Ihrem Build-System unterschiedlich ist).
