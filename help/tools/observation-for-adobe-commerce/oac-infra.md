---
title: Die Registerkarte [!DNL Infra]
description: Auf der Registerkarte [!DNL Infra] werden Probleme und Ursachen für Infrastrukturprobleme isoliert.
exl-id: 45f24177-3264-4848-99bc-951be32c1f7b
feature: Configuration, Observability
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
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
source-wordcount: '258'
ht-degree: 0%
---
# Die Registerkarte [!DNL Infra]

Auf der Registerkarte **[!DNL Infra]** werden Probleme und Ursachen für Infrastrukturprobleme isoliert. Im Folgenden werden die Frames beschrieben, die Sie auf der Registerkarte sehen können.

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![Service-Warnhinweise](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

Das **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** Diagramm zeigt die Service-Warnhinweise an, die vom [!DNL New Relic] Infrastructure Agent erfasst wurden. Dadurch werden Dienstneustarts angezeigt, von denen viele mit Bereitstellungen verbunden sind.

## [!UICONTROL Inode usage by mount]

![Inode usage by mount](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

Der **[!UICONTROL Inode usage by mount]** zeigt [!DNL inode] Nutzung nach Bereitstellung über den ausgewählten Zeitraum hinweg an. Auch wenn möglicherweise genügend freier Speicher vorhanden ist, zeigt ein Knoten, dessen [!DNL inodes] erschöpft ist, einen Mangel an verfügbarem Speicher an. Durch das Entfernen von Dateien (insbesondere kleinen Dateien) wird Speicherplatz freigegeben und [!DNL inodes] verfügbar gemacht.

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![vCPU-Stufenansicht über die Zeitleiste GRÖSSER 2 Wochen](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

Der **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** zeigt die vCPU-Stufenansicht für den ausgewählten Zeitraum von mehr als zwei Wochen an. In diesem Frame wird die Anzahl der vCPUs angezeigt, die dem angezeigten [!DNL New Relic] zugewiesen wurden.

## [!UICONTROL vCPU tier view over timeline]

![vCPU-Stufenansicht über die Zeitleiste](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

Der **[!UICONTROL vCPU tier view over timeline]** zeigt die vCPU-Stufenansicht für den ausgewählten Zeitraum von mehr als 24 Stunden an. In diesem Frame wird die Anzahl der vCPUs angezeigt, die dem angezeigten [!DNL New Relic] zugewiesen wurden. Es zeigt sowohl Upsizes als auch Downsizes von Clustern an.

## [!UICONTROL vCPU tier view over timeline BY NODE]

![vCPU-Stufenansicht über die Zeitleiste nach KNOTEN](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

Der **[!UICONTROL vCPU tier view over timeline BY NODE]** zeigt die vCPU-Stufenansichten über den ausgewählten Zeitrahmen nach Knoten an. Dieser Frame ist hilfreich, wenn Sie Verlust von Knoten erkennen oder wenn Knoten vergrößert oder verkleinert werden. Die vCPU-Stufenansicht über die Zeitleiste nach Knoten, sollte die Zeitleiste in weniger als 24 Stunden betrachten.

## [!UICONTROL Instance details]

![Details der Instanz](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

Die **[!UICONTROL Instance details]** Tabelle zeigt Instanzdetails der einzelnen [!DNL New Relic] an.

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![Nicht responsiver Knoten](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

Der **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** zeigt nicht responsive Knoten über einen Zeitraum an.
