---
title: Anwendungsinitialisierung und Bootstrap
description: Erfahren Sie mehr über die Initialisierung und Bootstrap-Logik für die Commerce-Anwendung.
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 0%

---


# Übersicht über Initialisierung und Bootstrap

Um die Commerce-Anwendung auszuführen, werden die folgenden Aktionen in implementiert [pub/index.php][index]:

- Einschließen [app/bootstrap.php][bootinitial], das wichtige Initialisierungsroutinen wie die Fehlerbehandlung, die Initialisierung des Autoloaders, die Festlegung von Profilerstellungsoptionen und die Festlegung der standardmäßigen Zeitzone durchführt.
- Erstellen Sie eine Instanz von [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- Erstellen Sie eine Commerce-Anwendungsinstanz: [\Magento\Framework\AppInterface][app-face]
- Commerce ausführen

## Bootstrap-Ausführungslogik

[Das Bootstrap-Objekt][bootinitial] verwendet den folgenden Algorithmus, um die Commerce-Anwendung auszuführen:

1. Initialisiert den Fehler-Handler.
1. Erstellt die [Objektmanager][object] und allgemeine gemeinsame Dienste, die überall verwendet werden und von der Umgebung betroffen sind. Die Umgebungsparameter werden ordnungsgemäß in diese Objekte eingefügt.
1. Stellt fest, dass der Wartungsmodus _not_ aktiviert; andernfalls wird beendet.
1. Stellt sicher, dass die Commerce-Anwendung installiert ist; andernfalls wird beendet.
1. Startet die Commerce-Anwendung.

   Jede nicht abgefangene Ausnahme während des Anwendungsstarts wird automatisch an Commerce im Abschnitt `catchException()` -Methode, die Sie zur Verarbeitung der Ausnahme verwenden können. Letztere müssen entweder `true` oder `false`:

   - Wenn `true`: Der Handel hat Ausnahmefehler erfolgreich gehandhabt. Es ist nicht notwendig, etwas Anderes zu tun.
   - Wenn `false`: (oder ein anderes leeres Ergebnis) Commerce hat die Ausnahme nicht behandelt. Das Bootstrap-Objekt führt die standardmäßige UnterRoutine für die Ausnahmebehandlung aus.

1. Sendet die Antwort, die vom Anwendungsobjekt bereitgestellt wird.

   >[!INFO]
   >
   >Die Behauptung, dass die Commerce-Anwendung installiert ist und sich nicht im Wartungsmodus befindet, ist das Standardverhalten der `\Magento\Framework\App\Bootstrap` -Klasse. Sie können sie beim Erstellen des Bootstrap-Objekts mithilfe eines Einstiegspunktskripts ändern.

   Beispieleinstiegspunktskript, das das Bootstrap-Objekt ändert:

   ```php
   <?php
   use Magento\Framework\App\Bootstrap;
   require __DIR__ . '/app/bootstrap.php';
   
   $params = $_SERVER;
   $params[Bootstrap::PARAM_REQUIRE_MAINTENANCE] = true; // default false
   $params[Bootstrap::PARAM_REQUIRE_IS_INSTALLED] = false; // default true
   $bootstrap = Bootstrap::create(BP, $params);
   
   /** @var \Magento\Framework\App\Http $app */
   $app = $bootstrap->createApplication('Magento\Framework\App\Http');
   $bootstrap->run($app);
   ```

## Standardmäßige Ausnahmebehandlung

Das bootstrap -Objekt gibt an, wie die Commerce-Anwendung nicht abgefangene Ausnahmen wie folgt handhabt:

- In [Entwicklermodus](../bootstrap/application-modes.md#developer-mode), zeigt die Ausnahme unverändert an.
- In jedem anderen Modus versucht, eine Ausnahme zu protokollieren und eine allgemeine Fehlermeldung anzuzeigen.
- Beendet Commerce mit Fehlercode `1`

## Einstiegspunktanwendungen

Wir verfügen über die folgenden Einstiegspunktanwendungen (d. h. von Commerce definierte Anwendungen, die vom Webserver als Ordnerindex verwendet werden):

### HTTP-Einstiegspunkt

[\Magento\Framework\App\Http][http] funktioniert wie folgt:

1. Bestimmt die [Anwendungsgebiet](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. Startet die Front-Controller- und Routing-Systeme, um eine Controller-Aktion zu finden und auszuführen.
1. Verwendet ein HTTP-Antwortobjekt, um ein Ergebnis zurückzugeben, das von der Controller-Aktion abgerufen wurde.
1. Umgang mit Fehlern (in der folgenden Prioritätsreihenfolge):

   1. Wenn Sie [Entwicklermodus](../bootstrap/application-modes.md#developer-mode):
      - Wenn die Commerce-Anwendung nicht installiert ist, führen Sie eine Umleitung zum Einrichtungs-Assistenten durch.
      - Wenn die Commerce-Anwendung installiert ist, zeigen Sie einen Fehler und den HTTP-Status-Code 500 (Interner Server-Fehler) an.
   1. Wenn sich die Commerce-Anwendung im Wartungsmodus befindet, zeigen Sie eine benutzerfreundliche Landingpage mit dem HTTP-Status-Code 503 (Dienst nicht verfügbar) &quot;Dienst nicht verfügbar&quot;an.
   1. Wenn die Commerce-Anwendung _not_ installiert ist, führen Sie eine Umleitung zum Einrichtungs-Assistenten durch.
   1. Wenn die Sitzung ungültig ist, führen Sie eine Umleitung zur Startseite durch.
   1. Wenn ein anderer Anwendungsinitialisierungsfehler auftritt, zeigen Sie eine benutzerfreundliche Seite &quot;Seite nicht gefunden&quot;mit dem HTTP-Status-Code 404 (Nicht gefunden) an.
   1. Zeigen Sie bei jedem anderen Fehler eine benutzerfreundliche Seite &quot;Dienst nicht verfügbar&quot;mit HTTP-Antwort 503 an, generieren Sie einen Fehlerbericht und zeigen Sie dessen ID auf der Seite an.

### Einstiegspunkt für statische Ressourcen

[\Magento\Framework\App\StaticResource][static-resource] ist eine Anwendung zum Abrufen von statischen Ressourcen (z. B. CSS, JavaScript und Bildern). Dadurch werden alle Aktionen mit einer statischen Ressource verschoben, bis die Ressource angefordert wird.

>[!INFO]
>
>Der Einstiegspunkt für statische Ansichtsdateien wird nicht in [Produktionsmodus](application-modes.md#production-mode) um potenzielle Exploits auf dem Server zu vermeiden. Im Produktionsmodus erwartet die Commerce-Anwendung, dass alle erforderlichen Ressourcen im `<your Commerce install dir>/pub/static` Verzeichnis.

Im Standard- oder Entwicklermodus wird eine Anforderung für eine nicht vorhandene statische Ressource gemäß den von der entsprechenden `.htaccess`.
Wenn die Anfrage an den Einstiegspunkt umgeleitet wird, analysiert die Commerce-Anwendung die angeforderte URL anhand der abgerufenen Parameter und sucht die angeforderte Ressource.

- In [Entwickler](application-modes.md#developer-mode) -Modus wird der Inhalt der Datei zurückgegeben, sodass der zurückgegebene Inhalt bei jeder Anforderung der Ressource auf dem neuesten Stand ist.
- In [default](application-modes.md#default-mode) -Modus wird die abgerufene Ressource veröffentlicht, sodass sie über die zuvor angeforderte URL zugänglich ist.

   Alle zukünftigen Anforderungen für die statische Ressource werden vom Server genauso verarbeitet wie statische Dateien. das heißt, ohne den Einstiegspunkt einzubeziehen. Wenn es erforderlich ist, veröffentlichte Dateien mit Original-Dateien zu synchronisieren, wird die `pub/static` -Verzeichnis entfernt werden; Daher werden Dateien mit der nächsten Anfrage automatisch erneut veröffentlicht.

### Einstiegspunkt für Medienressourcen

[Magento\MediaStorage\App\Media][media] ruft Medienressourcen (d. h. alle Dateien, die in den Medienspeicher hochgeladen wurden) aus der Datenbank ab. Sie wird immer dann verwendet, wenn die Datenbank als [Medienspeicher](https://glossary.magento.com/media-storage).

`\Magento\Core\App\Media` versucht, die Mediendatei im konfigurierten Datenbankspeicher zu finden und in die `pub/static` und geben dann seinen Inhalt zurück. Bei Fehler wird ein HTTP-Statuscode 404 (Nicht gefunden) im Header ohne Inhalt zurückgegeben.

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
