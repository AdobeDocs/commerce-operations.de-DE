---
title: Patch auf Adobe Commerce-Probleme mit dem Quality Patches Tool überprüfen
description: Dieser Artikel bietet einen Überblick über das Quality Patches Tool (QPT) und Links zu Ressourcen, die seine Verwendung erklären.
feature: Tools and External Services
role: Admin
exl-id: 4d651c3c-95ad-4b53-bf77-92758acb795d
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%
---
# Patch auf Adobe Commerce-Probleme mit dem Quality Patches Tool überprüfen

Dieser Artikel bietet einen Überblick über das Quality Patches Tool (QPT) und Links zu Ressourcen, die seine Verwendung erklären.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premise, alle [unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce auf Cloud-Infrastruktur, alle [unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Was ist das Quality Patches Tool?

Das [Quality Patches Tool](https://github.com/magento/quality-patches) (QPT) sind einzelne Patches, die von Adobe und der Magento Open Source-Community entwickelt wurden.

Damit können Sie:

* Anwenden von Qualitäts-Patches, die im Paket enthalten sind
* Zuvor angewendete Patches wiederherstellen
* Sehen Sie sich die allgemeinen Informationen über Qualitäts-Patches an, die für die installierte Version von Adobe Commerce verfügbar sind.

Im Folgenden finden Sie ein Beispiel für die Statustabelle, die Sie erhalten können, um die verfügbaren Patches anzuzeigen:

![Quality Patches Tool-Statustabelle mit verfügbaren Patches und deren Installationsstatus](/help/assets/tools/status_table.png)

Das Tool soll Ihnen die Möglichkeit geben, selbst Patches für Probleme zu erstellen, die möglicherweise bei Adobe Commerce auftreten, oder einfach Patches anzuwenden, die vom Adobe Commerce-Support vorgeschlagen werden.

>[!NOTE]
>
>QPT ist nur für qualitativ hochwertige Patches. Sicherheits-Patches sind im [Magento Security Center](/help/release/release-notes/overview.md) verfügbar.

## Im Quality Patches Tool verfügbare Patches

Eine Liste der verfügbaren Patches finden Sie [Quality Patches Tool](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.

## Installieren und Verwenden des Quality Patches Tools

Die Installations- und Verwendungsbefehle für Adobe Commerce On-Premise und Adobe Commerce On Cloud Infrastructure unterscheiden sich, da das QPT-Cloud-Paket im Paket ece-tools enthalten ist.

### Installieren und Verwenden von QPT für Adobe Commerce On-Premise

Weitere Informationen [ Installation und Verwendung von QPT zum Anwenden und Zurücksetzen von Patches finden Sie unter ](/help/tools/quality-patches-tool/usage.md)Software-Update-Handbuch > Patching“ in unserer Entwicklerdokumentation.

### Installieren und Verwenden von QPT für Adobe Commerce in der Cloud-Infrastruktur

Weitere Informationen zur Installation und Verwendung von QPT zum Anwenden und Zurücksetzen von Patches auf [ Cloud-Infrastruktur finden Sie unter „Cloud ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) für Adobe Commerce > Patches anwenden in unserer Entwicklerdokumentation.

## Verwandtes Lesen

* [Versionshinweise zum Quality Patches Tool](/help/tools/quality-patches-tool/release-notes.md) in unserer Entwicklerdokumentation.
* [Anwenden von Composer-Patches, die von Adobe bereitgestellt werden](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) in der Support-Wissensdatenbank.
