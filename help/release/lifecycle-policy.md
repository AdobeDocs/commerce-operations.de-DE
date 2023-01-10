---
title: Software Lifecycle Policy
description: Erfahren Sie mehr über wichtige Daten für das Ende der Softwareunterstützung für Adobe Commerce-Versionen.
source-git-commit: ffa8b957828833d2c3f9bc79c31dc3fa2c6035a5
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 8%

---


# Adobe Commerce-Lebenszyklusrichtlinie

Für Adobe Commerce 2.4 und nachfolgende Versionen:

- Um unsere Lebenszyklusrichtlinie besser zu vereinfachen, bietet Adobe Qualitätsverbesserungen für die Version 2.4 bis zum Ende des Supportzeitraums der PHP-Version, auf der sie basiert. Ein Kunde kann über [Adobe Commerce-Support](https://developer.adobe.com/commerce/contributor/community/support/) oder über den Self-Service [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;} , wenn ihre Version weiterhin Qualitätsunterstützung erhält. Die Daten zum Ende der Software-Unterstützung für Adobe Commerce-Release-Zeilen finden Sie in der folgenden Tabelle.

- Adobe bietet nur die neueste Patch- oder Sicherheits-Patch-Version mit Sicherheitskorrekturen, auch wenn die Version eines Kunden weiterhin Qualitätsunterstützung in Anspruch nimmt. Im Gegensatz zu Qualitätskorrekturen können Sicherheitskorrekturen nicht in früheren Nebenversionen oder früheren Patch-Versionen innerhalb unterstützter Nebenversionen rückportiert werden.

- Bei kritischen Sicherheitsproblemen, wie z. B. Schwachstellen ohne Tage, bietet Adobe [Hotfixes](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) für alle Kunden, die eine unterstützte Version verwenden, auch wenn sie nicht mit der neuesten Patch- oder Sicherheits-Patch-Version arbeiten. Es ist wichtig zu beachten, dass ein Hotfix kein Auffangbehälter ist und nicht alle Sicherheitsprobleme behebt, die durch ein Upgrade auf die neueste Version behoben würden.

## Ende der Software-Unterstützung

| Version | Veröffentlichungsdatum | Ende der Software-Unterstützung<sup>1</sup> | Abhängige PHP-Version |
| -------------------------------- | ----------------- | ----------------------------------- | --------------------------- |
| Adobe Commerce 2.3 | 28. November 2018 | 8. September 2022<sup>2</sup> | PHP 7.3 und 7.4<sup>3</sup> |
| Adobe Commerce 2.4.0-2.4.3 | 28. Juli 2020 | 28. November 2022 | PHP 7.4 |
| Adobe Commerce 2.4.4-2.4.6 | 12. April 2022 | 25. November 2024 | PHP 8.1 |

<sup>1 Das Ende der Software-Unterstützung umfasst sowohl das Ende von Qualitätsverbesserungen als auch das Ende von Sicherheitskorrekturen.</sup><br>
<sup>2 Das Datum des Auslaufens der Software-Unterstützung für 2.3 wurde auf den 8. September 2022 erweitert, um Kunden mehr Zeit für das Upgrade auf die Version 2.4.4 zu geben, die am 8. März 2022 allgemein verfügbar sein wird.</sup><br>
<sup>3 2.3.0-2.3.6 ist von PHP 7.3 abhängig; 2.3.7 ist abhängig von PHP 7.4.</sup>

>[!NOTE]
>
>Siehe [Software Lifecycle Policy](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

<table>
<thead>
  <tr>
    <th colspan="2"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Handel</td>
    <td>PHP</td>
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
    <td>2.4.0 - 2.4.3</td>
    <td style="text-align:center">7.4</td>
    <td colspan="3" style="background-color:#67ac68;"></td>
    <td style="background-color:#cd3c3c;">Nov</td>
    <td colspan="8" ></td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td rowspan="2" style="text-align:center">8.1</td>
    <td></td>
    <td colspan="10" style="background-color:#67ac68;">Mar</td>
    <td rowspan="2" style="background-color:#cd3c3c;">Nov</td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="9" style="background-color:#67ac68;">Aug</td>
  </tr>
</tbody>
</table>

## Schlüssel

<table>
  <thead>
   <tr>
    <th></th>
    <th></th>
   </tr>
  </thead>
 <tbody>
  <tr>
   <td style="background-color:#67ac68;">Unterstützt</td>
   <td>Version, die von Adobe vollständig getestet und unterstützt wurde.</td>
  </tr>
  <tr>
   <td style="background-color:#cd3c3c;">Ende der Software-Unterstützung</td>
   <td>Version, die das Ende der Software-Unterstützung erreicht hat.</td>
  </tr>
 </tbody>
</table>
