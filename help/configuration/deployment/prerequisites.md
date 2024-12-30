---
title: Voraussetzungen für die Bereitstellung
description: Hier finden Sie eine Liste der Voraussetzungen für die Bereitstellung von Commerce in einem Entwicklungs-, Build- oder Produktionssystem.
feature: Configuration, Deploy
exl-id: 9ea0eeff-e0f8-4532-887c-5d7f07d89ddd
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Voraussetzungen für Entwicklungs-, Build- und Produktionssysteme

Dateiberechtigungen und -eigentümerschaft müssen in allen Entwicklungs-, Build- und Produktionssystemen konsistent sein. Damit dies funktioniert, müssen Sie entweder:

- mit allen folgenden Eigenschaften:

   - Einrichten desselben Benutzernamens für Dateisystembesitzer auf allen Systemen
   - Stellen Sie sicher, dass der Webserver auf allen Systemen als derselbe Benutzer ausgeführt wird
   - Stellen Sie sicher, dass sich der Dateisystembesitzer auf allen Systemen in der Webservergruppe befindet.

- Ändern Sie nach Bedarf die Berechtigungen und Eigentümerrechte für das Commerce-Dateisystem auf jedem System gemäß den folgenden Richtlinien:

   - Entwicklung und Build: [Legen Sie die Eigentümerschaft und Berechtigungen vor der Installation fest (zwei Benutzer)](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
   - Produktion: [Commerce-Eigentümerschaft und -Berechtigungen in Entwicklung und Produktion](file-system-permissions.md)

>[!INFO]
>
>Wenn Sie diesen Ansatz wählen, müssen Sie die Dateisystemberechtigungen und den Besitz jedes Mal festlegen, wenn Sie Code aus Ihrem Build-System abrufen (wenn der Eigentümer des Dateisystems oder der Webserver-Benutzer auf Ihrem Build-System anders ist).
