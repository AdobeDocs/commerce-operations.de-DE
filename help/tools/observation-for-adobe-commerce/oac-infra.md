---
title: Registerkarte [!DNL Infra]
description: Die Registerkarte [!DNL Infra] isoliert Probleme und Ursachen von Infrastrukturproblemen.
exl-id: 45f24177-3264-4848-99bc-951be32c1f7b
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# Registerkarte [!DNL Infra]

Die Registerkarte **[!DNL Infra]** isoliert Probleme und Ursachen von Infrastrukturproblemen. Weitere Informationen zu den Frames, die Sie auf der Registerkarte sehen können.

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![Dienstwarnungen](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

Das Diagramm **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** zeigt die vom [!DNL New Relic]-Infrastrukturagenten erfassten Service-Warnhinweise. Dadurch werden Dienstneustarts angezeigt, von denen viele mit -Implementierungen verbunden sind.

## [!UICONTROL Inode usage by mount]

![Inode usage by mounten](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

Der Frame &quot;**[!UICONTROL Inode usage by mount]**&quot;zeigt die Verwendung von [!DNL inode] durch die Bereitstellung über den ausgewählten Zeitraum hinweg. Auch wenn ausreichend Speicherplatz frei ist, zeigt ein Knoten, wenn er nicht mehr über [!DNL inodes] verfügt, einen Mangel an verfügbarem Speicher. Durch das Entfernen von Dateien (insbesondere kleinen) wird sowohl Speicherplatz freigesetzt als auch [!DNL inodes] verfügbar gemacht.

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![vCPU-Stufenansicht im Zeitleistensegment GRÖSSER 2 Wochen](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

Der Frame **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** zeigt die vCPU-Tier-Ansicht über den ausgewählten Zeitraum von mehr als zwei Wochen. Dieser Frame betrachtet die Anzahl der vCPUs, die dem angezeigten [!DNL New Relic] Anwendungsnamen zugewiesen sind.

## [!UICONTROL vCPU tier view over timeline]

![vCPU-Stufenansicht über Timeline](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

Der Frame **[!UICONTROL vCPU tier view over timeline]** zeigt die vCPU-Tier-Ansicht über den ausgewählten Zeitraum von mehr als 24 Stunden an. Dieser Frame betrachtet die Anzahl der vCPUs, die dem angezeigten [!DNL New Relic] Anwendungsnamen zugewiesen sind. Es werden sowohl Cluster-Uploads als auch -Downloads angezeigt.

## [!UICONTROL vCPU tier view over timeline BY NODE]

![vCPU-Stufenansicht über die Timeline durch NODE](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

Der Frame **[!UICONTROL vCPU tier view over timeline BY NODE]** zeigt vCPU-Tier-Ansichten über den ausgewählten Zeitraum nach Knoten an. Dieser Frame ist hilfreich, um den Verlust von Knoten zu erkennen oder Knoten zu vergrößern oder zu verkleinern. vCPU-Stufenansicht über Timeline BY NODE sollte sich die Timeline weniger als 24 Stunden ansehen.

## [!UICONTROL Instance details]

![Details der Instanz](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

Die Tabelle **[!UICONTROL Instance details]** enthält Details zur Instanz jeder [!DNL New Relic] -Anwendung.

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![non-responsive-node](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

Der Frame **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** zeigt nicht responsive Knoten über einen Zeitraum hinweg.
