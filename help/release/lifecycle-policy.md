---
title: Lebenszyklusrichtlinie für Software
description: Erfahren Sie mehr über wichtige Daten für das Ende der Software-Unterstützung für Adobe Commerce-Versionen.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 3e7cef954a2be506c6f72e704710d16ed1d9b7a3
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 2%

---


# Adobe Commerce-Lebenszyklusrichtlinie

Um die Adobe Commerce-Lebenszyklusrichtlinie zu optimieren und die geschäftskritischen Anforderungen von Kunden zu unterstützen, bietet Adobe für jede Version ein dreijähriges Support-Fenster ab dem allgemeinen Verfügbarkeitsdatum an und veröffentlicht in diesem Zeitraum Qualitätskorrekturen. Daten und Einzelheiten zum Ende des Software-Supports für jede Version finden Sie in der Tabelle [Ende des Software-Supports](#end-of-software-support).

Während des dreijährigen Support-Fensters haben Kunden Zugriff auf:

- **Qualitätskorrekturen**-Kunden können auf Qualitätskorrekturen zugreifen, indem sie sich an den [Adobe Commerce Support](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) oder über die Self-Service-[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) wenden. In der folgenden Tabelle wurden die Termine für das Ende der Software-Unterstützung für die Adobe Commerce-Versionen beschrieben.

- **Sicherheitskorrekturen**-Adobe bietet Sicherheitskorrekturen durch kumulative Sicherheits-Patches und nicht kumulative [isolierte Sicherheits-Patch](versioning-policy.md#isolated-security-fixes)Dateien) für den dreijährigen Support-Zeitraum.

- **Hotfixes**-Bei kritischen Sicherheitsproblemen wie z. B. Zero-Day-Sicherheitslücken bietet Adobe [Hotfixes](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) für alle Kunden mit einer unterstützten Version, auch wenn sie nicht auf dem neuesten Patch oder der neuesten Sicherheits-Patch-Version sind. Beachten Sie, dass ein Hotfix nicht vollständig ist und nicht alle Sicherheitsprobleme behebt, die durch eine Aktualisierung auf die neueste Version behoben würden.

Adobe bietet keine Sicherheits- und Qualitätskorrekturen für Services und Software-Abhängigkeiten von Drittanbietern (wie PHP und MySQL), die das Ende des Lebenszyklus erreichen können, während sich Kunden in der dreijährigen oder verlängerten Support-Periode für Adobe Commerce befinden. Eine vollständige Liste [&#x200B; getesteten und unterstützten Technologien &#x200B;](../installation/system-requirements.md) Drittanbietern finden Sie unter „Systemanforderungen“.

## Erweiterte Unterstützung

Adobe empfiehlt Kunden, so bald wie möglich ein Upgrade durchzuführen. Um jedoch eine größere Flexibilität bei der Anpassung an Upgrade-Pläne und Geschäftsanforderungen zu bieten, bietet Adobe eine einjährige Support-Verlängerung ohne zusätzliche Kosten für Adobe Commerce-Kunden unter der Version 2.4.6. Die Support-Erweiterung umfasst Qualitäts- und Sicherheits-Patches für die Kernanwendung für bis zu einem Jahr. Die erweiterte Unterstützung für die Versionen Adobe Commerce 2.4.4 und 2.4.5 endet wie geplant im April und August 2026.

>[!NOTE]
>
>Erweiterter Support ist nur für Adobe Commerce-Kunden verfügbar. Sie ist nicht für die Magento Open Source-Code-Basis verfügbar.

## Ende des Software-Supports

| -Version | Allgemeine Verfügbarkeit | Ende der regulären Unterstützung<sup>1</sup> | Ende der erweiterten Unterstützung |
|----------------------|----------------------|------------------------------------|-------------------------|
| Adobe Commerce 2.4.8 | &#x200B;8. April 2025 | &#x200B;31. Mai 2028 | TBD |
| Adobe Commerce 2.4.7 | &#x200B;9. April 2024 | &#x200B;31. Mai 2027 | TBD |
| Adobe Commerce 2.4.6 | &#x200B;14. März 2023 | &#x200B;11. August 2026 | &#x200B;30. August 2027 |
| Adobe Commerce 2.4.5 | &#x200B;9. August 2022 | &#x200B;12. August 2025 | &#x200B;11. August 2026 |
| Adobe Commerce 2.4.4 | &#x200B;12. April 2022 | &#x200B;12. April 2025 | &#x200B;14. April 2026 |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> Wenn Sie Adobe Commerce-Kunde sind, können Sie während des verlängerten Support-Zeitraums für ein weiteres Jahr Sicherheits- und Qualitätskorrekturen erhalten.
>- Siehe [Software Lifecycle Policy](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Zusätzliche Sicherheitskorrekturen bei der Bereitstellung für Adobe Commerce 2.4.4 und 2.4.5

Als einmalige Ausnahme bietet Adobe eine verlängerte Bereitstellungsdauer für Sicherheitskorrekturen für die Adobe Commerce-Versionen 2.4.4 und 2.4.5, um Kunden zusätzliche Zeit für die Migration auf Adobe Commerce as a Cloud Service oder das Upgrade auf eine unterstützte Versionslinie zu geben.

Beachten Sie während dieses Bereitstellungszeitraums für Sicherheitskorrekturen Folgendes:

- **Nur isolierte Sicherheits-Patch** Datei - Für diese Versionen wird entsprechend dem Veröffentlichungszeitplan eine isolierte Sicherheits-Patch-Datei veröffentlicht. Während dieses Zeitraums werden keine Sicherheits-Patch-Versionen (keine neuen -p-Versionen) bereitgestellt.

  Um eine isolierte Sicherheits-Patch-Datei anwenden zu können, müssen Kunden für ihre unterstützte Version die neueste Patch-Version verwenden (die neueste -p-Version), da isolierte Sicherheits-Fehlerbehebungen ausschließlich mit dieser Version getestet werden.

- **Keine Qualitätskorrekturen oder technische Unterstützung**-Keine Fehlerbehebungen, Qualitätsaktualisierungen ([Quality Patches Tool](../tools/quality-patches-tool/usage.md)) oder technische Unterstützung ([Adobe Commerce Support](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)) werden für die Versionen 2.4.4 oder 2.4.5 in diesem Zeitraum bereitgestellt.

- **PCI-Konformität ist nicht garantiert:**-Da 2.4.4 und 2.4.5 PHP-Versionen verwenden, die das Ende des Lebenszyklus erreicht haben, kann für Händler in diesen Versionen die PCI-Konformität nicht garantiert werden. Wenn Sie diese Versionen weiterhin ausführen, kann dies die PCI-Compliance gefährden.

Um die vollständige Sicherheitsabdeckung aufrechtzuerhalten und die PCI-Compliance sicherzustellen, müssen Kunden so bald wie möglich ein Upgrade auf eine derzeit unterstützte Version von Adobe Commerce durchführen oder zu [Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/de/docs/commerce/cloud-service/overview) migrieren.

| -Version | Allgemeine Verfügbarkeit | Ende der erweiterten Unterstützung | Ende der Bereitstellung von Sicherheitskorrekturen |
|----------------------|----------------------|-------------------------|------------------------------------|
| Adobe Commerce 2.4.5 | &#x200B;9. August 2022 | &#x200B;11. August 2026 | Mai 2027 |
| Adobe Commerce 2.4.4 | &#x200B;12. April 2022 | &#x200B;14. April 2026 | Mai 2027 |

{style="table-layout:auto"}

>[!NOTE]
>
>Zusätzliche Sicherheitskorrekturen sind nur für Adobe Commerce-Kunden verfügbar und nicht für die Magento Open Source-Code-Basis.


## Support-Zeitleiste

Die Support-Zeitleiste ordnet für jede Adobe Commerce-Release-Reihe die Support-Zeiträume vierteljährlich zu. Verwenden Sie die zuvor in diesem Thema bereitgestellten Tabellen für genaue Enddaten.

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
    <td colspan="5" style="background-color:#FFBF00"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2,4,5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="4" style="background-color:#FFBF00"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2,4,6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
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
    <tr>
   <td style="background-color:#FFBF00;"> </td>
   <td>Erweiterte Sicherheitskorrekturen</td>
  </tr>
 </tbody>
</table>
