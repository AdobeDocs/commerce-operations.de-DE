---
title: Die [!DNL Infra] tab
description: Die [!DNL Infra] -Registerkarte isoliert Probleme und Ursachen von Infrastrukturproblemen.
exl-id: 45f24177-3264-4848-99bc-951be32c1f7b
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Die [!DNL Infra] tab

Die **[!DNL Infra]** -Registerkarte isoliert Probleme und Ursachen von Infrastrukturproblemen. Weitere Informationen zu den Frames, die Sie auf der Registerkarte sehen können.

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![Dienstwarnungen](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

Die **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** zeigt die von der [!DNL New Relic] Infrastrukturagent. Dadurch werden Dienstneustarts angezeigt, von denen viele mit -Implementierungen verbunden sind.

## [!UICONTROL Inode usage by mount]

![Verwendung des Knotens durch Bereinigung](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

Die **[!UICONTROL Inode usage by mount]** Frame-Displays [!DNL inode] Verwendung durch Einhängung über den ausgewählten Zeitrahmen hinweg. Auch wenn ausreichend Speicherplatz zur Verfügung steht, wenn einem Knoten die [!DNL inodes], wird es einen Mangel an verfügbarem Speicher zeigen. Durch das Entfernen von Dateien (insbesondere kleinen) wird sowohl Speicherplatz freigesetzt als auch [!DNL inodes] verfügbar.

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![vCPU-Stufenansicht im Zeitleistensegment GRÖSSER 2 Wochen](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

Die **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** frame zeigt die vCPU-Tier-Ansicht über den ausgewählten Zeitraum von mehr als zwei Wochen an. In diesem Frame wird die Anzahl der vCPUs untersucht, die dem [!DNL New Relic] Anwendungsname angezeigt.

## [!UICONTROL vCPU tier view over timeline]

![vCPU-Stufenansicht über Timeline](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

Die **[!UICONTROL vCPU tier view over timeline]** frame zeigt die vCPU-Tier-Ansicht über den ausgewählten Zeitraum von mehr als 24 Stunden an. In diesem Frame wird die Anzahl der vCPUs untersucht, die dem [!DNL New Relic] Anwendungsname angezeigt. Es werden sowohl Cluster-Uploads als auch -Downloads angezeigt.

## [!UICONTROL vCPU tier view over timeline BY NODE]

![vCPU-Stufenansicht über Timeline nach NODE](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

Die **[!UICONTROL vCPU tier view over timeline BY NODE]** frame zeigt Ansichten der vCPU-Ebene über den ausgewählten Zeitrahmen nach Knoten an. Dieser Frame ist hilfreich, um den Verlust von Knoten zu erkennen oder Knoten zu vergrößern oder zu verkleinern. vCPU-Stufenansicht über Timeline BY NODE sollte sich die Timeline weniger als 24 Stunden ansehen.

## [!UICONTROL Instance details]

![Details der Instanz](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

Die **[!UICONTROL Instance details]** -Tabelle zeigt die Instanzdetails jedes [!DNL New Relic] Anwendung.

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![non-responsive-node](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

Die **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** frame zeigt nicht responsive Knoten über einen Zeitraum hinweg an.
