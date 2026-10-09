---
title: Voraussetzungen für die Bereitstellung
description: Hier finden Sie eine Liste der Voraussetzungen für die Bereitstellung von Commerce in einem Entwicklungs-, Build- oder Produktionssystem.
feature: Configuration, Deploy
exl-id: 9ea0eeff-e0f8-4532-887c-5d7f07d89ddd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '162'
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
