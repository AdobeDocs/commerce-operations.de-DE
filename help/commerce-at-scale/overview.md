---
title: Erlebnisse skaliert bereitstellen
description: Erfahren Sie, wie Sie mit Adobe Commerce und Adobe Experience Manager Erlebnisse bedarfsgerecht bereitstellen können.
source-git-commit: 6ad72d5110ae3e3a7cf341282f2af9b700874f09
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---


# Skalierte Bereitstellung von Erlebnissen mit Adobe Commerce, Commerce Integration Framework und Adobe Experience Manager

Ein empfohlenes Integrationsmuster zwischen AEM und Adobe Commerce, das CIF als Connector verwendet, besteht darin, dass AEM Eigentümer der Präsentationsschicht (das &quot;Glas&quot;) und Adobe Commerce ist, um das Commerce-Backend als Headless-Backend zu nutzen. Dieser Integrationsansatz nutzt die Stärken jeder Anwendung: die Authoring-, Personalisierungs- und Omnichannel-Funktionen für AEM- und E-Commerce-Vorgänge von Adobe Commerce.

In einer AEM/CIF/Adobe Commerce-Umgebung gelangen die Besucher der E-Commerce-Site zunächst zu AEM. AEM prüft, ob die angeforderte Seite im Dispatcher-Cache verfügbar ist. Wenn die Seite vorhanden ist, wird diese zwischengespeicherte Seite dem Besucher bereitgestellt und es ist keine weitere Verarbeitung erforderlich. Wenn der Dispatcher die angeforderte Seite nicht enthält oder abgelaufen ist, fordert der Dispatcher den AEM-Herausgeber auf, die Seite zu erstellen, wobei der Herausgeber bei Bedarf Adobe Commerce für E-Commerce-Daten aufruft, um die Seite zu erstellen. Die erstellte Seite wird dann an den Dispatcher weitergeleitet, um für den Besucher bereitzustellen. Anschließend wird sie zwischengespeichert, was verhindert, dass weitere Ladevorgänge von anderen Besuchern auf den Servern bei nachfolgenden Anfragen an dieselbe Seite platziert werden.

![Übersichtsdiagramm zur Adobe Experience Manager- und Adobe Commerce-Architektur](../assets/commerce-at-scale/overview.png)

Eine Kombination aus Server-seitigem Rendering und Client-seitigem Rendering kann im Commerce-Modell AEM/CIF/Adobe verwendet werden: Serverseitiges Rendering zur Bereitstellung von statischen Inhalten und Client-seitigem Rendering, um häufig wechselnde oder personenbezogene dynamische Inhalte bereitzustellen, indem für bestimmte Komponenten direkt Adobe Commerce aufgerufen wird
im Browser des Benutzers aus.

Ein Beispiel für die verschiedenen Komponenten auf einer Produktdetailseite in einem Beispiel AEM E-Commerce-Storefront finden Sie im folgenden Beispiel:

![Übersichtsdiagramm zur Adobe Experience Manager- und Adobe Commerce-Architektur](../assets/commerce-at-scale/product-details-page.svg)

## Serverseitiges Rendering

E-Commerce-Seiten wie Produktdetailseiten (PDPs) und Produktlistenseiten (PLPs) werden sich wahrscheinlich nicht häufig ändern und können nach der Wiedergabe serverseitig mit AEM CIF-Kernkomponenten vollständig zwischengespeichert werden. Die Seiten sollten mithilfe von in AEM erstellten generischen Vorlagen im AEM Publisher gerendert werden. Diese Komponenten erhalten Daten aus Adobe Commerce über GraphQL-APIs. Diese Seiten werden dynamisch erstellt, auf dem Server gerendert, auf dem AEM Dispatcher zwischengespeichert und dann an den Browser gesendet. Beispiele dafür finden Sie in den lilafarbenen Feldern des obigen Beispiels.

## Client-seitiges Rendering

Wenn dynamischere Attribute wie Lagerbestände, Verfügbarkeit oder Preis angezeigt werden, z. B. auf Produktdetailseiten (Produktdetailseiten, PDPs), können clientseitige Komponenten verwendet werden. Während die Vorlagenseite mithilfe des oben beschriebenen serverseitigen Rendering-Ansatzes erstellt und im Dispatcher zwischengespeichert werden kann, kann es auf der statischen Seite selbst dynamische Client-seitige Webkomponenten geben. Diese dynamischen Komponenten können Daten direkt im Client-Browser aus Adobe Commerce über GraphQL-APIs abrufen, um z. B. den aktuellen Preis oder das Lagerbestand in Echtzeit auf der Produktdetailseite zu überprüfen. Dadurch wird sichergestellt, dass Inhalte, die normalerweise in Echtzeit angezeigt werden müssen, beim Laden der Seite immer abgerufen werden. Beispiele dafür finden Sie in den roten Feldern des obigen Beispiels.

Während des Checkout-Prozesses kann auch eine Kombination aus AEM Vorlagen und Client-seitigem Rendering verwendet werden: Client-seitige Warenkorbkomponenten rendern den Warenkorb, das Kassenformular und die Integration mit dem Zahlungsdienstleister. Dieser Hybridansatz kann auch für die Kontoverwaltungsfunktionen von Adobe Commerce verwendet werden, z. B. zum Erstellen von Konten, zum Anmelden von Konten und für vergessene Passwörter.
