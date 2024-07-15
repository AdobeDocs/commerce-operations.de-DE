---
title: Tipps zum Leistungstest
description: Erfahren Sie, wie Sie KPIs für den Start Ihrer Adobe Commerce- und Adobe Experience Manager-Lösung festlegen.
exl-id: 4b0d9c4f-e611-452d-a80f-27f82705935d
topic: Commerce, Performance
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 0%

---

# Tipps zu Leistungstests

Um die Effektivität aller oben genannten Änderungen zu bewerten, sollten vor der Live-Schaltung und vor künftigen umfangreichen Bereitstellungen in Ihren Produktionsumgebungen gründliche Leistungstests durchgeführt werden. Bei der Planung Ihrer Belastungstests ist es wichtig, den realen Traffic von Verbrauchern so weit wie möglich zu simulieren.

Die ressourcenintensivsten Bereiche der AEM/CIF/Adobe Commerce-Site sind diejenigen, die nicht zwischenspeicherbar sind, wie der Checkout-Prozess und die Site-Suche. Statische und daher zwischenspeicherbare Seiten wie Produktdetailseiten (PDPs) und Produktlistingseiten (PLPs) bilden den Großteil des Traffics auf einer E-Commerce-Site im Allgemeinen. Daher sollten die Skripte und Szenarien im Test dies widerspiegeln, um die Grenzen der Plattform zu messen.

Wenn für Ihren Belastungstest ein einzelnes Skript ausgeführt wird, das zwischen den Schritten ohne Wartezeit durch die Site navigiert und auch immer den Checkout-Prozess jedes Mal abschließt, wird kein zuverlässiger Hinweis auf die Grenzen der Plattform gegeben, da dies nicht das ist, was ein Echtzeit-Szenario wäre.

Die Definition von KPIs sollte der erste Schritt in Ihrem Leistungstestplan sein: Definieren Sie Metriken, die Sie während des ersten Tests testen können, dann aber in Zukunft erneut messen können, und auf wiederkehrender Basis, nachdem die Site live ist. Auf diese Weise können Sie die Leistung Ihrer Site im Zeitverlauf - vor und nach dem Start - verfolgen. Beispiele für zu definierende KPIs:

- Durchschnittliche Antwortzeit - Zeit bis zum ersten Byte oder letzten Byte
- Latenz
- Bytes/s (Througput)
- Fehlerrate
- Bestellungen pro Stunde
- Seitenansichten pro Stunde
- Unique Users pro Stunde (gleichzeitige Käufer)

## JMeter-Richtlinien

Bei der Entwicklung Ihrer AEM/CIF/Adobe Commerce-Belastungstests sollten die folgenden Jmeter-Richtlinien berücksichtigt werden:

- Teilen Sie Ihr Skript in konfigurierbare Szenarien auf, die beispielsweise Folgendes abdecken sollten:
   - Startseite öffnen
   - Seite Kategorie öffnen (PLP)
   - Einfache Produkte anzeigen (PDP) - 2 Schleifen innerhalb jeder Iteration
   - Konfigurierbare Produkte anzeigen - 2 Schleifen innerhalb jeder Iteration
      - Setzen Sie die obigen Schritte beispielsweise auf 60 % des Traffics
   - Produktsuche
      - Setzen Sie beispielsweise die Suche im Katalog auf 37 % des Traffics
   - Warenkorb und Checkout
      - Beispiel: Ein Benutzer, der den Warenkorb und den Kassenbereich des Skripts ausfüllt, sollte standardmäßig eine standardmäßige E-Commerce-Site-Konversionsrate von rund 3 % verwenden.
      - Da der Checkout-Fluss nicht zwischengespeichert ist und normalerweise ein ressourcenintensiver Vorgang ist, würde die Festlegung einer unrealistisch hohen Zahl für die Anzahl der Personen, die Bestellungen abschließen, im Vergleich zur Anzahl der Site-Browser zu einem unzuverlässigen Ergebnis für das Traffic-Volumen führen, das Ihre Site verarbeiten könnte.
- Bereinigen Sie alle Caches vor jedem Testlauf:
   - Der AEM Dispatcher-Cache sollte vollständig bereinigt werden.
   - Der schnelle und interne Cache von Adobe Commerce sollte vollständig geleert und bereinigt werden - dies kann über das Cache-Steuerelement in Adobe Commerce Admin erfolgen.
- Schließen Sie eine Ramp-Phase in den JMeter-Test ein: Wenn keine Ramp-Periode festgelegt ist, bedeutet dies, dass der Traffic nicht schrittweise erhöht wird und die Site keine der häufig besuchten Seiten und Komponenten der Seite zwischenspeichert. Im realen Leben wäre es ungewöhnlich, dass der gesamte Traffic-Spitzenwert genau zur gleichen Zeit auf eine vollständig nicht zwischengespeicherte Site gelangt. Daher sollte eine Ramp-Periode in Jmeter-Testskripts enthalten sein, damit der Cache so aufgebaut werden kann, wie es auf einer echten E-Commerce-Site der Fall wäre.
- Eine &quot;Wartezeit&quot;zwischen jedem Schritt innerhalb einer Iteration sollte verwendet werden - in Wirklichkeit würde ein Benutzer dies nicht tun
sofort auf die nächste Seite auf der Website während der Journey springen - es würde eine Wartezeit geben, während der Benutzer die Seite liest und über die nächste Aktion entscheidet.
- Wenn Sie die Thread-Gruppen so einstellen, dass sie unbegrenzt, aber für eine bestimmte Zeit von x (z. B. 60 Minuten) laufen, wird ein wiederholbarer Test durchgeführt, wobei die mediane Reaktionszeit mit der vorherigen Testläufe vergleichbar ist. Das bedeutet, dass nach der festgelegten Startzeit die Zielanzahl der gleichzeitig ausgeführten virtuellen Benutzer vorhanden ist, was für die festgelegte Loopzeit gilt.
- Die mittlere Zeit sollte verwendet werden, um eine Verbesserung/Abnahme der durchschnittlichen Reaktionszeit zu erzielen, nicht der Durchschnitt. Wenn
Es gibt mehrere Edge-Ergebnisse, die viel länger dauern als die anderen Ergebnisse, würde dies dieses durchschnittliche Ergebnis verfälschen, aber was wir daran interessiert sind, dass der Endnutzer die Antwortzeit für die Mehrheit der Benutzer erhält, was für die mediane Maßnahme besser geeignet ist.
- Eingebettete Ressourcen werden nicht standardmäßig in JMS erfasst (z. B. JS, CSS und andere Ressourcen, die heruntergeladen werden, wenn ein echter Benutzer die Seite besucht). Dies kann aktiviert werden, jedoch nur für die Domäne, die Sie testen - externe Ressourcenaufrufe sollten weiterhin ausgeschlossen werden (z. B. möchten wir keine Antwortzeiten von extern gehosteten Diensten einbeziehen, z. B. Google Analytics-Code, da wir keine Kontrolle über sie haben).
- HTTP Cache Manager sollte aktiviert sein. Dadurch kann JMeter Seitenelemente während einer Journey zwischenspeichern als
ein echter Journey eines Benutzers während des Browsings der Website in seinem eigenen Browser. Während der Journey über die Website lädt der Browser des Benutzers die zugehörige eingebettete Ressource nur einmal herunter und diese wird dann vom Browser des Benutzers zwischengespeichert. Wenn derselbe Benutzer einige Zeit nach seinem ursprünglichen Besuch auf die Site zurückkehrt, kann es weiterhin der Cache sein, dass diese Assets zwischengespeichert werden.
- Listener sollten innerhalb der tatsächlichen Lasttestläufe (z. B. &quot;Ergebnisstruktur anzeigen&quot;und &quot;Aggregatbericht&quot;) aufbewahrt werden. Die Aufnahme dieser Funktion in den Nicht-GUI-Test-Lade-Test kann sich auf die von Jmeter gemeldeten Leistungsergebnisse auswirken, da Ressourcen während des echten Testlaufs zum Generieren der Berichte verwendet werden. Diese Listener wurden aus dem Testskript entfernt, um sie durch eine JTL-Ergebnisdatei zu ersetzen, die dann mithilfe der Jmeter-Funktion für Bericht-Dashboard verarbeitet werden kann.
- Eine Zielantwortzeit für die Auswertung, sodass der &quot;Apdex-Wert&quot;des Dashboard-Berichts als schnelle Methode verwendet werden kann, um die Auswirkungen von Leistungsänderungen zwischen Testläufen zu messen. Der Apdex-Wert basiert auf einer bestimmten Anzahl von Personen, die in einer akzeptablen Zeit auf die Site zugreifen können. Wenn die Antwortzeit über einen bestimmten &quot;frustrierenden&quot;Wert liegt, wird der Wert dadurch reduziert. Die Zeiten können mit den Parametern &quot;apdex_completed_threshold&quot;und &quot;apdex_tolerated_threshold&quot;festgelegt werden.
- Legen Sie eine Zielmetrik &quot;Bestellungen pro Stunde&quot;fest, die für Geschäftsbenutzer angezeigt wird, nicht für die Anzahl virtueller Benutzer. &quot;Virtuelle Benutzer&quot;kann ein komplexes Thema sein, um zu verstehen, was der Test im realen Leben misst. Durch Berechnung der Site-Konversionsrate, der Bestellungen pro Stunde, der durchschnittlichen Besuchszeit pro Site und der Denkzeit zwischen den einzelnen Seitenladevorgängen können branchenübliche Berechnungen verwendet werden, um verschiedene Lasttestszenarien basierend auf den zu erreichenden Bestellungen pro Stunde darzustellen.
- Schließlich sollte Ihr Jmeter-Testserver auf einem Server ausgeführt werden, der geografisch nahe dem Standort des größten Teils Ihres Benutzerverkehrs liegt und wo Ihre Cloud-Infrastruktur gehostet wird - hoffentlich wären dies die gleichen.
