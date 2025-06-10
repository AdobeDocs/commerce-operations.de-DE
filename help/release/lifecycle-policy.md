---
title: Lebenszyklusrichtlinie für Software
description: Erfahren Sie mehr über wichtige Daten für das Ende der Software-Unterstützung für Adobe Commerce-Versionen.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 5a45f2b0ad2485014abd3b807a5797f9fc82388b
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 3%

---


# Adobe Commerce-Lebenszyklusrichtlinie

Für Adobe Commerce 2.4.4 und nachfolgende Versionen:

- Um die Adobe Commerce-Lebenszyklusrichtlinie zu optimieren und die geschäftskritischen Anforderungen von Kunden zu unterstützen, erweiterte Adobe das Support-Fenster für Adobe Commerce 2.4.4 und höher auf drei Jahre ab dem Datum der allgemeinen Verfügbarkeit. Adobe bietet Qualitätskorrekturen für die Versionen 2.4.4 und höher für einen dreijährigen Support-Zeitraum. Kunden können auf Qualitätskorrekturen zugreifen, indem sie sich an den [Adobe Commerce-Support ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) oder über die Self-Service-[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) wenden, wenn ihre Version weiterhin für Qualitätssupport in Frage kommt. In der folgenden Tabelle wurden die Termine für das Ende der Software-Unterstützung für die Adobe Commerce-Versionen beschrieben.

- Adobe bietet Sicherheitskorrekturen durch eine Sicherheits-Patch-Version für den dreijährigen Support-Zeitraum.

- Für kritische Sicherheitsprobleme, z. B. Zero-Day-Schwachstellen, stellt Adobe [Hotfixes](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) für alle Kunden mit einer unterstützten Version bereit, auch wenn sie nicht über den neuesten Patch oder die neueste Version eines Sicherheits-Patches verfügen. Beachten Sie, dass ein Hotfix nicht vollständig ist und nicht alle Sicherheitsprobleme behebt, die durch eine Aktualisierung auf die neueste Version behoben würden.

- Adobe bietet keine Sicherheits- und Qualitätskorrekturen für Services und Software-Abhängigkeiten von Drittanbietern (wie PHP und MySQL), die das Ende des Lebenszyklus erreichen können, während Kunden den dreijährigen Support für Adobe Commerce in Anspruch nehmen. Eine vollständige Liste [ getesteten und unterstützten Technologien ](../installation/system-requirements.md) Drittanbietern finden Sie unter „Systemanforderungen“.

- Für Adobe Commerce on Cloud-Kunden, die die Versionen 2.4.4 und 2.4.5 verwenden, wendet Adobe automatisch lebenslange Sicherheitskorrekturen für PHP 8.1 auf die Infrastruktur an, sodass diese Kunden nicht vom Ende der Unterstützung für PHP 8.1 betroffen sind. On-Premises-Kunden, die Adobe Commerce 2.4.4 und 2.4.5 verwenden, müssen sich an den Adobe-Support wenden, um bei Bedarf Sicherheits-Patches für die gesamte PHP 8.1-Lebensdauer anzufordern.

- Adobe bietet Kompatibilität mit Services und Softwareabhängigkeiten von Drittanbietern, während Kundinnen und Kunden im Rahmen von Patch-Versionen, die nur für die Sicherheit verfügbar sind, eine dreijährige Support-Periode für Adobe Commerce durchlaufen, jedoch nur, wenn dies möglich ist, ohne abwärtsinkompatible Änderungen vorzunehmen.

## Erweiterte Unterstützung

Adobe empfiehlt Kunden, so bald wie möglich ein Upgrade durchzuführen. Um jedoch eine größere Flexibilität bei der Anpassung an Upgrade-Pläne und Geschäftsanforderungen zu bieten, bietet Adobe eine einjährige Support-Verlängerung ohne zusätzliche Kosten für Adobe Commerce-Kunden in den Versionen 2.4.4 und 2.4.5. Die Support-Erweiterung umfasst Qualitäts- und Sicherheits-Patches für die Kernanwendung für bis zu einem Jahr.

>[!NOTE]
>
>Erweiterter Support ist nur für Adobe Commerce-Kunden verfügbar. Sie ist nicht für die Magento Open Source-Code-Basis verfügbar.

## Ende des Software-Supports

| -Version | Allgemeine Verfügbarkeit | Ende der regulären Unterstützung<sup>1</sup> | Ende der erweiterten Unterstützung | Abhängige PHP-Version | Abhängige MariaDB-Version |
|----------------------|----------------------|------------------------------------|-------------------------|-----------------------|---------------------------|
| Adobe Commerce 2.4.8 | &#x200B;8. April 2025 | &#x200B;11. April 2028 | Nicht zutreffend | 8.3 und 8.4 | 11,4 |
| Adobe Commerce 2.4.7 | &#x200B;9. April 2024 | &#x200B;9. April 2027 | Nicht zutreffend | 8.2 und 8.3 | 10.11<sup>3 </sup> |
| Adobe Commerce 2.4.6 | &#x200B;14. März 2023 | &#x200B;11. August 2026<sup>2 </sup> | Nicht zutreffend | 8.1 und 8.2 | 10.11<sup>4 </sup> |
| Adobe Commerce 2.4.5 | &#x200B;9. August 2022 | &#x200B;9. August 2025 | &#x200B;11. August 2026 | 8,1 | 10,6<sup>5 </sup> |
| Adobe Commerce 2.4.4 | &#x200B;12. April 2022 | &#x200B;12. April 2025 | &#x200B;14. April 2026 | 8,1 | 10,6<sup>6 </sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> Das Ende der Softwareunterstützung umfasst sowohl End-of-Quality-Fixes als auch End-of-Security-Fixes.
>- <sup>2</sup> Aktualisiert, um dem Ende der erweiterten Unterstützung für 2.4.5 zu entsprechen.
>- <sup>3</sup> Erste Schritte mit dem 2.4.7-p6 Sicherheits-Patch.
>- <sup>4</sup> Erste Schritte mit dem 2.4.6-p11 Sicherheits-Patch.
>- <sup>5</sup> Erste Schritte mit dem 2.4.5-p11 Sicherheits-Patch.
>- <sup>6</sup> Erste Schritte mit dem 2.4.4-p12 Sicherheits-Patch.
>- Siehe [Software Lifecycle Policy](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="1"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
    <th colspan="4">2025</th>
    <th colspan="4">2026</th>
    <th colspan="4">2027</th>
    <th colspan="4">2028</th>
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
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
  </tr>
  <tr>
    <td>2,4,4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2,4,5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2,4,6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2,4,7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2,4,8</td>
    <td colspan="13"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="2"></td>
  </tr>
</tbody>
</table>

**key**

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td style="background-color:#67ac68;"></td>
   <td>Regelmäßige Unterstützung</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>Erweiterte Unterstützung</td>
  </tr>
 </tbody>
</table>
