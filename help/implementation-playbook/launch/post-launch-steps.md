---
title: Schritte nach dem Start
description: Verwenden Sie unsere Checkliste nach dem Start, um eine reibungslose Implementierung der Adobe Commerce-Site sicherzustellen.
exl-id: 0c3162d9-6475-4b34-9278-e5aea39bd0f9
feature: Deploy
source-git-commit: ce41158f900fad27e3e7b8157f5c64ac988bbabf
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Schritte nach dem Start

Sobald die Website live ist, werden diese Aktivitäten so bald wie möglich durchgeführt, um sicherzustellen, dass die Website ordnungsgemäß gestartet wurde:

- Aktivieren Sie das Tool für die Zeitüberwachung (New Relic), aktivieren Sie Prüfungen und überwachen Sie die Site, um sicherzustellen, dass alle Dienste und der Zugriff in Grün sind.
- Adobe Commerce-Sicherheitsprüfung regelmäßig aktivieren
- Taggen Sie den Cluster als live und erstellen Sie ein Support-Ticket, um die High SLA-Überwachung zu aktivieren.
- Der CSE (Customer Success Engineer) und TAM (Technical Account Manager) führen nach Abschluss der Umstellung die folgenden Aufgaben aus:
   - Taggen Sie den Cluster als High SLA für den Adobe Commerce-Client und erstellen Sie ein Support-Ticket, um ihn zu aktivieren.
   - Aktivieren Sie die **intern** Pingdom-Prüfungen auf Domänennamen (der öffentliche Zugriff auf Pingdom ist nicht verfügbar)
   - Überprüfen Sie den Überwachungsstatus und stellen Sie sicher, dass alle Elemente grün sind.
   - Halten Sie die Interessenträger per E-Mail über die Garantiedauer und -parameter am Wochentag auf dem Laufenden.

![Abbildung der Phase 4 des Startvorgangs](../../assets/playbooks/launch-steps-4.svg)
