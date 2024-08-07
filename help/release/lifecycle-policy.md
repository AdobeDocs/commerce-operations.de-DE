---
title: Software Lifecycle Policy
description: Erfahren Sie mehr über wichtige Daten für das Ende der Software-Unterstützung für Adobe Commerce-Versionen.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 7df5edf2acba706fb01f58cc3749c4a2bf136fc5
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 5%

---


# Adobe Commerce-Lebenszyklusrichtlinie

Für Adobe Commerce 2.4.4 und nachfolgende Versionen:

- Um die Adobe Commerce-Lebenszyklusrichtlinie zu optimieren und die unternehmenskritischen Anforderungen von Kunden zu unterstützen, wurde das Support-Fenster von Adobe auf drei Jahre ab dem Datum der allgemeinen Verfügbarkeit (GA) für Adobe Commerce 2.4.4 und höher erweitert. Adobe bietet Qualitätsverbesserungen für die Versionen 2.4.4 und höher für einen Zeitraum von drei Jahren an. Kunden können auf Qualitätsverbesserungen zugreifen, indem sie sich an den [Adobe Commerce-Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) oder den Self-Service [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) wenden, wenn ihre Version weiterhin Qualitätsunterstützung erhält. In der folgenden Tabelle finden Sie die Daten zum Ende der Software-Unterstützung für Adobe Commerce-Release-Zeilen.

- Adobe bietet über eine Sicherheits-Patch-Version für die dreijährige Supportzeit Sicherheits-Korrekturen.

- Bei kritischen Sicherheitsproblemen, wie z. B. null Tage-Sicherheitslücken, stellt Adobe [Hotfixes](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) für alle Kunden bereit, die eine unterstützte Version verwenden, selbst wenn sie nicht auf der neuesten Patch- oder Sicherheits-Patch-Version stehen. Es ist wichtig zu beachten, dass ein Hotfix kein Auffangbehälter ist und nicht alle Sicherheitsprobleme behebt, die durch ein Upgrade auf die neueste Version behoben würden.

- Adobe bietet keine Sicherheits- und Qualitätskorrekturen für Dienste und Softwareabhängigkeiten von Drittanbietern (wie PHP und MySQL), die das Ende des Lebenszyklus erreichen können, während Kunden die dreijährige Supportzeit für Adobe Commerce nutzen. Eine vollständige Liste der getesteten und unterstützten Drittanbietertechnologien finden Sie unter [Systemanforderungen](../installation/system-requirements.md) .

- Adobe bietet Kompatibilität mit Drittanbieterdiensten und Softwareabhängigkeiten, während Kunden die dreijährige Supportzeit für Adobe Commerce im Rahmen von reinen Sicherheits-Patch-Versionen nutzen, jedoch nur, wenn dies möglich ist, ohne dass rückwärtskompatible Änderungen vorgenommen werden.

## Ende der Software-Unterstützung

| Version | Allgemeine Verfügbarkeit | Ende der Softwareunterstützung<sup>1</sup> | Abhängige PHP-Version | Abhängige MariaDB-Version |
|----------------------|----------------------|-------------------------------------|-----------------------|------------------------------|
| Adobe Commerce 2.4.7 | 9. April 2024 | 9. April 2027 | 8.2 und 8.3 | 10,6 |
| Adobe Commerce 2.4.6 | 14. März 2023 | 14. März 2026 | 8.1 und 8.2 | 10,6 |
| Adobe Commerce 2.4.5 | 9. August 2022 | 9. August 2025 | 8,1 | 10,5<sup>2</sup> |
| Adobe Commerce 2.4.4 | 12. April 2022 | 24. April 2025 | 8,1 | 10,5<sup>3</sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> Das Ende der Softwareunterstützung umfasst sowohl das Ende von Qualitätsverbesserungen als auch das Ende von Sicherheitskorrekturen.
>- <sup>2</sup> Beginnend mit dem 2.4.5-p8-Sicherheits-Patch.
>- <sup>3</sup> Beginnend mit dem 2.4.4-p9-Sicherheits-Patch.
>- Siehe [Software-Lebenszyklusrichtlinie](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="2"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
    <th colspan="4">2025</th>
    <th colspan="4">2026</th>
    <th colspan="4">2027</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Commerce</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
  </tr>
  <tr>
    <td>2,4,4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2,4,5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2,4,6</td>
    <td colspan="4"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="8"></td>
  </tr>
  <tr>
    <td>2,4,7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="2"></td>
  </tr>
</tbody>
</table>

**key**

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td style="background-color:#67ac68;">Unterstützt</td>
   <td>Sicherheits- und Qualitätspatches für Adobe Commerce</td>
  </tr>
  <!-- <tr>
   <td style="background-color:#cd3c3c;">End of software support</td>
   <td>Version that has reached end of software support.</td>
  </tr>
 </tbody> -->
</table>
