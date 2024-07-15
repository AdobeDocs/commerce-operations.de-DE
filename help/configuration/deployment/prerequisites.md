---
title: Voraussetzungen für die Bereitstellung
description: Sehen Sie sich eine Liste der Voraussetzungen für die Bereitstellung von Commerce in einem Entwicklungs-, Build- oder Produktionssystem an.
feature: Configuration, Deploy
exl-id: 9ea0eeff-e0f8-4532-887c-5d7f07d89ddd
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Voraussetzungen für Entwicklungs-, Build- und Produktionssysteme

Dateiberechtigungen und -besitz müssen in Entwicklungs-, Build- und Produktionssystemen konsistent sein. Dazu müssen Sie entweder:

- Folgendes:

   - Richten Sie auf allen Systemen denselben Benutzernamen des Dateisysteminhabers ein.
   - Stellen Sie sicher, dass der Webserver auf allen Systemen als derselbe Benutzer ausgeführt wird.
   - Stellen Sie sicher, dass sich der Eigentümer des Dateisystems in der Gruppe der Webserver auf allen Systemen befindet.

- Ändern Sie bei Bedarf die Berechtigungen und das Eigentum des Commerce-Dateisystems für jedes System mithilfe der folgenden Richtlinien:

   - Entwicklung und Build: [Legen Sie die Eigentumsrechte und Berechtigungen vor der Installation (zwei Benutzer) fest](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
   - Produktion: [Eigentum und Berechtigungen der Commerce in Entwicklung und Produktion](file-system-permissions.md)

>[!INFO]
>
>Wenn Sie diesen Ansatz wählen, müssen Sie bei jedem Abruf von Code aus Ihrem Build-System Dateisystemberechtigungen und -eigentum festlegen (wenn der Eigentümer des Dateisystems oder der Webserver-Benutzer in Ihrem Build-System unterschiedlich ist).
