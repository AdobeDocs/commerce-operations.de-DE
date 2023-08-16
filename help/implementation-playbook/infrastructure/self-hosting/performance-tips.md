---
title: Tipps zur Leistung des Self-Hosting-Adobe Commerce
description: Erfahren Sie mehr über Tipps und Konzepte und Best Practices zum selbstständigen Hosting.
landing-page-description: Hier erhalten Sie Tipps und Hinweise zur Leistung, die Sie beim Hosten von Adobe Commerce selbst beachten sollten.
short-description: Erfahren Sie mehr über Strategien und Leistungstipps für das Hosting von Adobe Commerce selbst.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 95ff0c79-21d0-4514-991c-d88f616db68f
feature: Install
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 0%

---

# Tipps zur Leistung von Adobe Commerce selbst hosten

Die Verwendung einer flexiblen und leistungsstarken E-Commerce-Plattform bedeutet nicht, dass Sie die Leistung opfern müssen. Seit der Einführung von Adobe Commerce wurden zahlreiche Verbesserungen an der Kernanwendung vorgenommen. In Version 2.5.4 führte das Adobe Commerce-Technikerteam einen festgelegten Test durch, um die Anwendung zu bewerten. Die Testergebnisse haben gezeigt, dass Adobe Commerce in der Lage ist, einen großen Katalog mit über 240 Millionen SKUs zu verarbeiten. API-Anfragezeiten sind außergewöhnlich hoch 300 ms, und die Anzahl der Seitenansichten und Bestellungen pro Stunde ist mit 2 Millionen Seitenansichten und 208.000 Bestellungen pro Stunde phänomenal.

Anzeigen der neuesten Benchmark-Ergebnisse durch Umstieg auf [Experience League - Adobe Commerce - Implementierungs-Playbook - Benchmarks](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}.

Um die Dinge so optimal wie möglich zu halten, befolgen Sie diese Standards beim Hinzufügen von Anpassungen und zusätzlicher Komplexität zu Ihrem Projekt.

In den folgenden Abschnitten werden Themen behandelt, die Sie beachten sollten, und Tipps zur Optimierung Ihrer Self-Hosting-Implementierung gegeben.

## Varnisch

Varnish ist ein HTTP-Reverse-Proxy mit Cache. So kompliziert dies auch erscheinen mag, das Ergebnis sind schnelle Antworten, um sicherzustellen, dass die Anfragen schneller zurückgegeben werden, als wenn das Element aus der Quelle abgerufen werden müsste. Das Ausführen einer Adobe Commerce-Site ohne eine Version von &quot;Varnish&quot;führt zu langsameren Seitenladevorgängen und anderen Schlüsselmetriken. Es kann schwierig sein, sich selbst einzurichten und zu verwalten, aber wir haben dieses Thema im Experience League [Konfigurieren von Varnish](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} , um ein besseres Verständnis für die Verwendung mit Adobe Commerce zu erhalten. Eine Alternative besteht darin, eine Cloud-basierte Lösung zu verwenden. Obwohl viele zu berücksichtigen sind, wurde Fastly als Lösung für die Adobe Commerce on Cloud ausgewählt. Es ist eine Version von Fastly, Cloud-basiert, die VCLs und viele Facetten von Lacken verwendet.

Es ist schwierig, eine Lösung zu finden, die am besten zu Ihrer Anwendung, Konfiguration, Ihrem Budget und Ihren technischen Fähigkeiten passt. Die Verwendung einer Cloud-basierten Option führt dazu, dass alle harten Teile verschwinden, soweit Management, Konfiguration, Server und andere Infrastrukturkomponenten berücksichtigt werden. Es wurde von der Adobe Commerce im Cloud-Team aufgrund seiner Leistung, Skalierbarkeit, Durchsatz und vielen anderen Schlüsselmetriken als Lösung ausgewählt.

Indem Sie eine gute Lösung für Ihr Projekt bezüglich Varnish auswählen, richten Sie sich für die beste Leistung für Ihre Kunden ein und sparen Sie, dass die Commerce-Anwendung härter arbeitet als sie muss.

## CDN

Neben Varnish als einem wertvollen Asset für Ihr Adobe Commerce-Projekt ist als Nächstes ein CDN verfügbar. Zusammen mit Ihrem Varnish kann ein CDN zwischengespeicherte Instanzen für Ihr CSS bereitstellen, Seitenassets wie Bilder, um die Bandbreite Ihrer Adobe Commerce-Anwendung zu reduzieren. Sie kann GraphQL-Antworten zwischenspeichern, um die Vorteile einer Headless-Adobe Commerce-Site zu nutzen. Einige CDNs bieten Bildoptimierung, eine Firewall für Webanwendungen und andere Funktionen.

Adobe Commerce on Cloud entschied sich für Fastly für seinen &quot;Varnish&quot;-Cache, aber auch als CDN. Diese Einzellösung bietet eine Vielzahl von Funktionen, die der Adobe Commerce bei Cloud-Kunden ein großartiges Erlebnis bieten. Sie können die Übersicht über Fastly Services unter Experience League lesen. [Übersicht über Fastly Services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}

Ein CDN bietet optimierte und sichere Bereitstellungsinhalte für das Adobe Commerce-Projekt. Wenn dies möglicherweise keine erforderliche Komponente für Ihr Projekt ist, sollte dies berücksichtigt werden, da Ihre Site ausgereift ist und die Anzahl der Besucher zunimmt. Durch Bereitstellung eines CDN können Sie das Hinzufügen zusätzlicher Hardware zur Infrastruktur verzögern oder die vorhandene Infrastruktur skalieren, da die Last aus jeder Anfrage entfernt wird.

## Deaktivieren von Modulen

Die Deaktivierung eines nicht verwendeten Moduls sollte in Betracht gezogen, aber nicht leicht durchgeführt werden. Diese Technik reduziert bei einigen Anforderungen den Verwaltungsaufwand und die Verarbeitungszeit, es gibt jedoch Nebenwirkungen, die berücksichtigt werden sollten. Es gibt oft Fälle, in denen ein Entwickler davon ausgeht, dass beim Erstellen von Funktionen ein Modul verfügbar ist. Dies ist oft sicher, es sei denn, sie haben sich entschieden, einige Klassen in einem deaktivierten Modul zu verwenden.

Die Deaktivierung eines Moduls wie des nativen &quot;Newsletters&quot;ist ein ziemlich häufiges Ereignis. Dies gilt insbesondere dann, wenn der Eigentümer des Stores über ein Drittanbieterunternehmen verfügt, das seinen Newsletter verwaltet. Dabei kann es sich um ein Problem handeln, wenn ein Drittanbietermodul installiert wird und aus irgendeinem Grund beschlossen wurde, eine Klasse aus dem Newsletter zu verwenden. Diese zufällige Abhängigkeit wird wahrscheinlich während der ersten Installation und Tests erfasst. Dann müssen Sie jedoch entscheiden, ob Sie dieses Drittanbietermodul beibehalten, den Newsletter aktivieren und dann die Website mit Regressionstests nach eigenem Verhalten testen möchten, das eingeführt wird. Oder finden Sie einen Ersatz für dieses Drittanbietermodul. Beide Entscheidungen sind mit Risiko, Zeit und möglicherweise mit Fehlern behaftet.

Bevor Sie nicht verwendete Module deaktivieren, stellen Sie sicher, dass Sie keine Tests wie Einheiten haben. [MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}, [Codeception testing](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe="_blank"} Belastungstests oder API-Anfragen, die möglicherweise betroffen sind.

## Adobe Commerce- und PHP-Codierungsstandards für jede Pull-Anforderung einhalten

Adobe Commerce verfügt über eine Reihe von [Kodierungsstandards](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}. Diese helfen sicherzustellen, dass ein ähnliches Muster, Stil und erwartetes Design unabhängig von der Art der Softwareentwicklung befolgt werden. Wenn Sie zur Adobe Commerce-Codebase beitragen, ist dies eine Anforderung. Sollten Sie sich jedoch dafür entscheiden, diese Methode für die benutzerdefinierte Entwicklung zu befolgen, wird ein solider Eckpfeiler für alle Entwickler, sowohl aktuelle als auch zukünftige, geschaffen. Wenn alle Pull-Anforderungen dazu angehalten werden, einen Code-Standard zu übergeben, hilft dies sicherzustellen, dass alle die gleichen konsistenten Entwicklungsmuster verstehen und erwarten können.

Um die Adobe Commerce-Kodierungsstandards zu begleiten, wird als weiteres Fundament PHP-Basis verwendet. Es sollte in Ihren Entwicklerhandbüchern klar definiert sein, welche Standards Sie einhalten müssen und welche Abweichungen akzeptabel sind. Ein Fallback sollte jedoch dem öffentlich gepflegten Leitfaden unter [PHP-FIG](https://www.php-fig.org){target="_blank"}.

Eine entschiedene Haltung gegenüber PSR-1 und PSR-12. Wenn sichergestellt wird, dass die Entwickler, die zum Projekt beitragen, diesen folgen, wird sichergestellt, dass es keine merkwürdig strukturierten Dateien und Muster gibt. Dies hilft auch sicherzustellen, dass künftige Entwickler den Code, den sie überprüfen, schnell lesen und verstehen können. Je näher Sie diesen Mustern und Kodierungsstandards folgen, desto einfacher sollten zukünftige Entwicklungsbemühungen gelesen und schneller implementiert werden.

## Ausführen von Belastungstests nach jeder Bereitstellung

Die Durchführung eines Belastungstests nach jeder Bereitstellung kann übertrieben erscheinen. Wenn diese Methode angewendet wird, kann die Möglichkeit für neu eingeführte Funktionen, die zu einer Leistungsminderung führen, verfolgt und verringert werden.

Neben der Erkennung der Leistungsbeeinträchtigung durch neuen Code kann eine historische Referenz zu Schlüsselmetriken Ihrer Site auch dazu beitragen, Einblicke in die Aktivierung eines neuen Tools oder einer neuen Infrastruktur zu erhalten. Bevor Sie beispielsweise das Hosting-Unternehmen bezahlen, um Ihre Umgebung zu vergrößern, und hoffen, dass Sie die erwartete Leistungssteigerung erhalten, können Sie eine Staging-Umgebung mit den neuen Konfigurationen einrichten und einen Belastungstest durchführen, um zu sehen, wie das tatsächliche Ergebnis aussehen würde.

Diese Tests können automatisiert und Teil Ihrer CI/CD-Pipeline sein. Daher können Sie auch Regeln einrichten, die die Ergebnisse aufnehmen und die Zusammenführung von Funktionen blockieren, wenn zu viel Abweichung von der Norm auftritt. Die Anzahl der Anwendungsfälle für diese Daten ist unbegrenzt, aber ohne diesen Prozess zu starten, können Sie sein Potenzial möglicherweise nie erkennen.

Adobe Commerce hat eine gute Schreibweise zu diesem Thema in Experience League. [Tipps zum Leistungstest](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} and in [Testing guidance](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
