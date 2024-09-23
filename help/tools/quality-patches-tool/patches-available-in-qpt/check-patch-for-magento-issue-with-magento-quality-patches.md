---
title: Überprüfen Sie den Patch auf Adobe Commerce-Problem mit dem Tool für Qualitätsmuster .
description: Dieser Artikel bietet einen Überblick über das Quality Patches Tool (QPT) und Links zu Ressourcen, die erklären, wie es verwendet wird.
feature: Tools and External Services
role: Admin
source-git-commit: 6f311fc4c20caca8b98d4c3c06642e5f61dc614f
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Überprüfen Sie den Patch auf Adobe Commerce-Problem mit dem Tool für Qualitätsmuster .

Dieser Artikel bietet einen Überblick über das Quality Patches Tool (QPT) und Links zu Ressourcen, die erklären, wie es verwendet wird.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort, alle [unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce in der Cloud-Infrastruktur, alle [unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Qualitätsmuster-Werkzeug

Das [Quality Patches Tool](https://github.com/magento/quality-patches) (QPT) sind individuelle Patches, die von Adobe und der Magento Open Source Community entwickelt wurden.

Damit können Sie:

* Anwendung von Qualitätspatches, die im Paket enthalten sind
* Zurücksetzen zuvor angewendeter Patches
* Hier finden Sie allgemeine Informationen zu Qualitätspatches, die für die installierte Version von Adobe Commerce verfügbar sind.

Im Folgenden finden Sie ein Beispiel für die Statustabelle, die Sie aufrufen können, um die verfügbaren Patches anzuzeigen:

![Magento_patches_list](/help/assets/tools/status_table.png)

Das Tool soll Ihnen die Möglichkeit geben, Patches für Probleme, die mit Adobe Commerce auftreten können, selbst zu bedienen oder einfach durch den Adobe Commerce-Support vorgeschlagene Patches anzuwenden.

>[!NOTE]
>
>QPT ist nur für Qualitäts-Patches geeignet. Sicherheits-Patches sind im [Magento Security Center](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview) verfügbar.

## Im Werkzeug für Qualitätsmuster verfügbare Patches

Eine Liste der verfügbaren Patches finden Sie in der Entwicklerdokumentation unter [Qualitätsmuster-Tool](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) .

## Installieren und Verwenden des Tools &quot;Qualitätsmuster&quot;

Die Installations- und Nutzungsbefehle unterscheiden sich für Adobe Commerce On-Premise und Adobe Commerce in der Cloud-Infrastruktur, da für Cloud das QPT-Paket im ece-Tools-Paket enthalten ist.

### Installation und Verwendung von QPT für Adobe Commerce vor Ort

Weitere Informationen zur Installation und Verwendung von QPT zum Anwenden und Wiederherstellen von Patches finden Sie in der Entwicklerdokumentation unter [Handbuch für Software-Aktualisierung > Patchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) .

### Installieren und Verwenden von QPT für Adobe Commerce in der Cloud-Infrastruktur

Weitere Informationen zum Installieren und Verwenden von QPT für das Anwenden und Wiederherstellen von Patches auf Adobe Commerce in der Cloud-Infrastruktur finden Sie unter [Cloud für Adobe Commerce > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

* [Versionshinweise zum Qualitätsmuster-Tool](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/release-notes) in unserer Entwicklerdokumentation.
* [Anwenden von Composer-Patches, die von Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento) in der Support-Wissensdatenbank bereitgestellt werden.
