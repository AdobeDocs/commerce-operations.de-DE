---
title: Patch auf Adobe Commerce-Probleme mit dem Quality Patches Tool überprüfen
description: Dieser Artikel bietet einen Überblick über das Quality Patches Tool (QPT) und Links zu Ressourcen, die seine Verwendung erklären.
feature: Tools and External Services
role: Admin
exl-id: 4d651c3c-95ad-4b53-bf77-92758acb795d
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Patch auf Adobe Commerce-Probleme mit dem Quality Patches Tool überprüfen

Dieser Artikel bietet einen Überblick über das Quality Patches Tool (QPT) und Links zu Ressourcen, die seine Verwendung erklären.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premise, alle [unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce auf Cloud-Infrastruktur, alle [unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Was sind Quality Patches Tool?

Das [Quality Patches Tool](https://github.com/magento/quality-patches) (QPT) sind individuelle Patches, die von Adobe und der Magento Open Source-Community entwickelt wurden.

Damit können Sie:

* Anwenden von Qualitäts-Patches, die im Paket enthalten sind
* Zuvor angewendete Patches wiederherstellen
* Sehen Sie sich die allgemeinen Informationen über Qualitäts-Patches an, die für die installierte Version von Adobe Commerce verfügbar sind.

Im Folgenden finden Sie ein Beispiel für die Statustabelle, die Sie erhalten können, um die verfügbaren Patches anzuzeigen:

![Magento_PATCHES_LIST](/help/assets/tools/status_table.png)

Das Tool soll Ihnen die Möglichkeit geben, selbst Patches für Probleme zu erstellen, die möglicherweise bei Adobe Commerce auftreten, oder einfach Patches anzuwenden, die vom Adobe Commerce-Support vorgeschlagen werden.

>[!NOTE]
>
>QPT ist nur für qualitativ hochwertige Patches. Sicherheits-Patches sind im [Magento-Sicherheitscenter](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview) verfügbar.

## Im Quality Patches Tool verfügbare Patches

Eine Liste der verfügbaren Patches finden Sie [Quality Patches Tool](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.

## Installieren und Verwenden des Quality Patches Tools

Die Installations- und Verwendungsbefehle für Adobe Commerce On-Premise und Adobe Commerce On Cloud Infrastructure unterscheiden sich, da das QPT-Cloud-Paket im Paket ece-tools enthalten ist.

### Installieren und Verwenden von QPT für Adobe Commerce On-Premise

Weitere Informationen [ Installation und Verwendung von QPT zum Anwenden und Zurücksetzen von Patches finden Sie unter ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)Software-Update-Handbuch > Patching“ in unserer Entwicklerdokumentation.

### Installieren und Verwenden von QPT für Adobe Commerce in der Cloud-Infrastruktur

Weitere Informationen zur Installation und Verwendung von QPT zum Anwenden und Zurücksetzen von Patches auf [ Cloud-Infrastruktur finden Sie unter „Cloud ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) für Adobe Commerce Adobe Commerce > Patches anwenden in unserer Entwicklerdokumentation.

## Verwandtes Lesen

* [Versionshinweise zum Quality Patches Tool](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/release-notes) in unserer Entwicklerdokumentation.
* [Anwenden von Composer-Patches von Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento) in der Support-Wissensdatenbank.
