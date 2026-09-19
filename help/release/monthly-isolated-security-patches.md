---
title: Monatliche Patching-Richtlinie für isolierte Sicherheit
description: Erfahren Sie mehr über die monatlichen isolierten Sicherheits-Patches von Adobe Commerce, die am Patch-Dienstag bereitgestellt werden, um gezielte CVE-Fehlerbehebungen zwischen Sicherheits-Patch-Versionen bereitzustellen.
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: f2261633-201d-46c5-8a66-999e70527a83
    internal-label: PCI
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 66d7c9fd19785e791635d8e8bdf3d6ff3aa27a20
workflow-type: tm+mt
source-wordcount: '1553'
ht-degree: 0%
---
# Monatliche Patching-Richtlinie für isolierte Sicherheit

Um Kunden von Adobe Commerce dabei zu unterstützen, wichtige Sicherheitskorrekturen früher anzuwenden, stellt Adobe Commerce jetzt monatliche isolierte Sicherheits-Patches am Patch-Dienstag (dem zweiten Dienstag im Monat) bereit. Termine finden Sie im [Veröffentlichungszeitplan &#x200B;](schedule.md) Adobe Commerce. Diese Patches sind für Adobe Commerce on Cloud, lokale Adobe Commerce- und Magento Open Source-Installationen verfügbar.

Eine isolierte Sicherheits-Patch-Datei enthält nur den Code, der benötigt wird, um eine oder mehrere spezifische Sicherheitslücken zu beheben, und wird als eng gefasste Code-Diff-Datei bereitgestellt statt als vollständiges Composer-Paket. Da die Änderungen spezifisch für Sicherheitslücken sind, können sie schneller überprüft, getestet und angewendet werden als eine Sicherheits-Patch-Version, ohne dass die umfassendere Abhängigkeitsauflösung und Regressionstests ausgelöst werden, die für ein Sicherheits-Patch-Versionsupgrade erforderlich sind. Jede monatliche isolierte Sicherheits-Patch-Datei wird in die nächste vollständige Sicherheits-Patch-Version integriert, sodass Kunden alle veröffentlichten isolierten Patch-Dateien über die nächste Sicherheits-Patch-Version (`-pN`) erhalten können.

## So passen isolierte Patches zu anderen Patch-Typen

Isolierte Sicherheits-Patches sind eine von mehreren Patches, die Adobe Commerce bereitstellt, um Kunden sicher und auf dem neuesten Stand zu halten.

| **Patch-Typ** | **Zweck** | **Kumulatives Verhalten** | **Typischer Versand** | **Rolle** |
| --- | --- | --- | --- | --- |
| Sicherheits-Patch-Version (-pN) | Sicherheits- und Compliance-Update für eine unterstützte Versionszeile | Kumulativ - Legt die aktuelle Sicherheitsbasislinie fest | Komponentenpaket | Primäre unterstützte Sicherheitsgrundlinie |
| Isolierte Sicherheits-Patch-Datei | Zielgerichtete Fehlerbehebung für einen oder mehrere CVEs | Nicht kumulativ - nacheinander anwenden | Eigenständige Patch-Datei, normalerweise eine ZIP-Datei. Einige Fehlerbehebungen können auch in Cloud-Patches für Commerce enthalten sein | Schnellere Zwischenbehebung zwischen Sicherheits-Patch-Versionen |
| Cloud-Patches für Commerce | Erforderliche, kritische Fehlerbehebungen (einschließlich Sicherheitskorrekturen) und Cloud-spezifische Änderungen | Paketversionsabhängig | Cloud-Patches für das Commerce-Paket, verwaltet durch ECE-Tools | Während der Cloud-Bereitstellung automatisch angewendet |
| Patch für Quality Patches Tool (QPT) | Optionale, zielgerichtete Qualitäts- oder Kompatibilitätskorrektur für ein bestimmtes Problem | Patch-Kettenabhängig | QPT-Paket | Liefert zielgerichtete Qualitätskorrekturen |
| Hotfix | Dringende Lösung mit engem Umfang (z. B. ein Zero-Day) | fallspezifisch | ZIP/Diff oder eigenständiges Paket über QPT | Dringende Probleme mit hoher Auswirkung |

Die beiden Arten von Sicherheits-Patches spielen unterschiedliche Rollen:

* **Isolierte Patches** enthalten nur Schwachstellenkorrekturen und sind nicht kumulativ. Sie bündeln keine zuvor veröffentlichten isolierten Patch-Dateien. Händler müssen Patches in der richtigen Reihenfolge anwenden, da bei jedem neuen Patch davon ausgegangen wird, dass frühere Patches vorhanden sind. Um einen isolierten Sicherheits-Patch anzuwenden, muss die Installation auf dem neuesten Nur-Sicherheit-Patch-Release für die unterstützte Zeile erfolgen, da isolierte Fehlerbehebungen ausschließlich mit dieser Version getestet werden.

* **Sicherheits-Patches (`-pN`)** werden jährlich für alle unterstützten Versionszeilen veröffentlicht und über Composer bereitgestellt. Sie enthalten alle zuvor veröffentlichten Sicherheits-, Compliance- und Qualitäts-Hotfixes. Adobe veröffentlicht bei Bedarf möglicherweise zusätzliche Sicherheits-Patches.

## Monatliche isolierte Patch-Vorteile

Die Entdeckung von Schwachstellen hat sich in der gesamten Branche beschleunigt. KI-gestützte Analyse-Tools können jetzt große Code-Basen scannen und Fehler viel schneller aufdecken als manuelle Überprüfungen, wodurch das Zeitfenster zwischen der Offenlegung und der Nutzung immer kleiner wird. Eine monatliche isolierte Patch-Kadenz schließt diese Lücke, indem Korrekturen bereitgestellt werden, sobald sie bereit sind, anstatt auf die nächste geplante Sicherheits-Patch-Version zu warten.

Das Ziel ist Geschwindigkeit ohne unnötigen Aufwand. Eine fertige Fehlerbehebung steht erst bei der nächsten Version eines Sicherheits-Patches in der Warteschlange, und Händler patchen nicht öfter als nötig. Isolierte Sicherheits-Patch-Dateien lösen diese Spannung: Jede ist ein enger, nur auf Sicherheit basierender Unterschied - viel einfacher zu überprüfen und anzuwenden als eine Sicherheits-Patch-Version, da ihr Umfang absichtlich begrenzt ist.

Dieser Ansatz funktioniert, da Single-Purpose-Patches die für Composer-Versionen erforderlichen Abhängigkeitsauflösungen und vollständigen Regressionstests überspringen, sodass sie erstellt, anhand einer bekannten Baseline validiert und schnell bereitgestellt werden können. In der Cloud-Infrastruktur werden diese Fehlerbehebungen in Cloud-Patches für Commerce gebündelt - einem Package, das von Händlern im Rahmen ihres Composer- und Bereitstellungs-Workflows aktualisiert wird. Nach der Aktualisierung wird die Fehlerbehebung automatisch während der Bereitstellung angewendet, ohne dass eine separate Patch-Datei gefunden oder angewendet werden muss. Der in Sicherheitsbulletins beschriebene manuelle Patch-Datei-Workflow gilt für lokale und Magento Open Source-Installationen, bei denen die Cloud-Pipeline nicht ausgeführt wird.

## Anwenden monatlicher isolierter Patches

Gehen Sie wie folgt vor, um die monatliche isolierte Sicherheits-Patch-Datei anzuwenden und die neuesten Fehlerbehebungen auf dem neuesten Stand zu halten:

1. **Überprüfen Sie den [Veröffentlichungszeitplan](schedule.md).**

   Neue monatliche, isolierte Patch-Dateien werden gemäß dem Veröffentlichungszeitplan bereitgestellt. Überprüfen Sie das entsprechende Sicherheitsbulletin für betroffene Komponenten und CVEs. Jedes Bulletin enthält Links zu Versionshinweisen mit schrittweisen Anweisungen zur Installation der isolierten Patch-Datei für diesen Monat.

1. **Überprüfen Sie den Sicherheitsstatus Ihrer Commerce-Installation mithilfe des [Commerce-Versionstools](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/commerce-version-tool/intro).**

   Das Tool meldet, welche monatlichen Patches derzeit installiert sind, welche fehlen und welchen CVEs die Installation weiterhin ausgesetzt ist. Dies bietet eine endgültige Einschätzung, welche Maßnahmen erforderlich sind, anstatt sich allein auf die Versionsnummer zu verlassen.

1. **Bestätigen Sie Ihre Baseline-Version.**

   Isolierte Patches werden nur gegen die neueste reine Sicherheits-`-p`-Version für Ihre Produktlinie getestet. Wenn Sie auf dieser Grundlinie zurückliegen, wenden Sie sie zuerst an.

1. **Alle fehlenden Patches in der richtigen Reihenfolge anwenden.**

   Da sie nicht kumulativ sind, können Sie nicht zur neuesten Datei springen.

   >[!NOTE]
   >
   >**Cloud-Kunden:** Überprüfen Sie zuerst Ihre installierten Cloud-Patches für [Version](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest). Die Fehlerbehebung ist möglicherweise bereits enthalten und eine manuelle Anwendung kann zu einem Konflikt führen oder die Fehlerbehebung duplizieren.

1. **Dateien an die installierten Komponenten anpassen.**

   Wenden Sie nur die Datei an, die Ihrer CE-, EE-, B2B- oder anderen Komponentenversion entspricht.

1. **Führen Sie das Commerce-Versionstool zur Bestätigung erneut aus.**

   Stellen Sie sicher, dass der neue Patch als installiert angezeigt wird und die entsprechenden CVEs jetzt als geschützt gemeldet werden.

1. **Testen und dann bereitstellen.**

   Validieren Sie in der Staging-Umgebung, bevor Sie zur Produktion weiterleiten, gemäß Ihrem normalen Änderungsprozess.

Cloud-Kunden können auch die [Adobe Commerce Patching Automation](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/caps-tool/intro) verwenden, um Patches über das Admin-Bedienfeld anstelle der manuellen Git- und Composer-Schritte oben anzuwenden oder rückgängig zu machen.

## Patch-Aktionen nach Bereitstellungstyp

| **Sie laufen…** | **Was ändert sich für Sie** |
| --- | --- |
| Adobe Commerce in Cloud Manager | Cloud-Patches für Commerce, die über ECE-Tools bereitgestellt werden, wenden die erforderlichen Fehlerbehebungen bei Ihrer nächsten Bereitstellung automatisch an. Sie steuern weiterhin die Verzweigungs-, Zusammenführungs- und Validierungsschritte und sollten die Versionshinweise zu Cloud Patches auf Commerce überprüfen, bevor Sie dieselbe Fehlerbehebung manuell anwenden. |
| Adobe Commerce On-Premises | Bestätigen Sie Ihre `-p`, laden Sie die Datei herunter, die jeder installierten Komponente entspricht, wenden Sie sie nacheinander an und überprüfen Sie sie mit dem Commerce-Versionstool. |

## FAQs

Das monatliche Patchen der isolierten Sicherheit ist eine neue Versionsrichtlinie. Die folgenden Fragen betreffen gemeinsame Anliegen.

### Muss ich alle bisherigen isolierten Patches oder nur die neueste Version des Sicherheits-Patches anwenden?

Sie brauchen beides. Bevor Sie einen isolierten Patch anwenden, aktualisieren Sie auf die neueste Baseline der Nur-Sicherheit-`-p`. Jedes Pflaster wird nur an dieser Baseline getestet. Isolierte Patches sind nicht kumulativ, daher müssen alle übergangenen Patches nacheinander angewendet werden.

Wenn Sie beispielsweise die aktuelle Baseline der `-p`-Version verwenden, aber die isolierten Patches von Juli und August verpasst haben, wenden Sie erst Juli, dann August und dann September an. In der nächsten `-p` wird die Sequenz zurückgesetzt, da sie alle zuvor herausgegebenen Einzelkorrekturen enthält.

### Warum wird nicht einfach ein Composer-Paket anstelle separater Patch-Dateien bereitgestellt?

Bei einer Installation mit mehreren Komponenten - CE, EE, B2B und Page Builder - kann eine monatliche Version separate Patch-Dateien erfordern, da jede Datei auf eine bestimmte installierte Komponentenversion abzielt. Die Kombination aller Korrekturen in einem Composer-Paket würde Probleme mit der Abhängigkeitsauflösung erneut verursachen und vollständige Regressionstests erfordern - die Risiken, die isolierte Patches vermeiden sollen. Cloud-Kunden müssen Patches nicht manuell anwenden. Cloud-Patches für Commerce liefern dieselben Fehlerbehebungen über die vorhandene Bereitstellungs-Pipeline.

### Wie weiß ich, in welchem Sicherheitszustand sich meine Installation befindet, wenn Patches auf Patches aufgespielt sind?

Mit der Veröffentlichung der monatlichen Sicherheits-Patches führte Adobe Commerce das [Commerce Version Tool](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/commerce-version-tool/intro) ein, ein eigenständiges Dienstprogramm, das meldet, welche Patches installiert sind oder fehlen und vor welchen CVEs Ihre Installation geschützt ist. Statt sich auf Versionsnummern zu verlassen, liest das Tool Patch-Metadaten und stellt maschinenlesbare Ausgaben für das Reporting und die kontinuierliche Integration (CI) bereit.

### Bedeutet dies, dass Adobe sich von kumulativen, versionierten Sicherheitsversionen zurückgezogen hat?

Anzahl Die jährliche `-p`-Version bleibt der primäre, kumulative Sicherheits-Checkpoint. Isolierte Patches ergänzen diese Kadenz für CVEs, die nicht sicher darauf warten können. Sie ersetzen `-p` Versionen nicht. Wenn Sie jedes Jahr die geplante Sicherheits-Patch-Version für Ihre Zeile anwenden, bleiben Sie auf einem vollständig unterstützten Pfad und erhalten jede Fehlerbehebung, die jemals als isolierte Datei dazwischen ausgegeben wurde.

### Macht das Versenden von Fehlerbehebungen außerhalb von Composer eine Standardinstallation nicht weniger sicher?

Anzahl Der Bereitstellungsmechanismus wirkt sich nicht auf das Sicherheitsergebnis der Fehlerbehebung aus. Ein isolierter Patch wendet dieselbe Codeänderung an, die später in einer vollständigen Patch-Version (`-p`) enthalten ist. Ob die Fehlerbehebung als Composer-Paket oder als eigenständige Datei bereitgestellt wird, hat keinen Einfluss auf die Effektivität. Händler, die den Patch nicht anwenden, behalten die bestehende Sicherheitsbasis bis zur nächsten geplanten Sicherheitsveröffentlichung bei. Durch das Anwenden isolierter Patches kann die Verfügbarkeit reduziert werden, indem Fehlerbehebungen früher bereitgestellt werden, anstatt auf einen vollständigen Versionszyklus zu warten.

## Weitere Hilfe zu diesem Thema

>[!MORELIKETHIS]
>
>* [Software-Lebenszyklusrichtlinie](lifecycle-policy.md)
>* [Veröffentlichungsrichtlinie](versioning-policy.md)
>* [Patch-Veröffentlichungszeitplan](schedule.md)
>* [Commerce-Versionstool](../tools/commerce-version-tool/intro.md)
>* [Adobe-Sicherheitsbulletins und -beratungen](https://helpx.adobe.com/de/security/security-bulletin.html)
