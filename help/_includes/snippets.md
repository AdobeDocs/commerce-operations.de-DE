---
source-git-commit: e625670e741c0669050ab758d4f87c5ca06fe3df
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---
# Snippets

## Nur Commerce {#commerce-only}

>[!NOTE]
>
>Die [!DNL Upgrade Compatibility Tool] ist nur für Adobe Commerce-Instanzen verfügbar.

<!-- Configuration guide snippets -->

## Dateisystembesitzer {#file-system-owner}

>[!WARNING]
>
>Alle Magento-CLI-Befehle müssen vom [Dateisystembesitzer“ ausgeführt ](/help/configuration/cli/config-cli.md#prerequisites).

## Sicherungsbefehle {#tip-backup-command}

>[!TIP]
>
>Der `support:backup` Befehl ist _nicht_ derselbe Code-Backup, der vom `setup:backup` Befehl ausgeführt wird. Der Befehl `support:backup` dient zum Sichern des Codes, der vom Adobe Commerce-Support geprüft werden soll.

## B2B-Patches {#b2b-patches}

>[!NOTE]
>
>Nach der Installation dieses Sicherheits-Patches müssen Adobe Commerce B2B-Händler auch auf die neueste kompatible Version des B2B-Sicherheits-Patches aktualisieren. Siehe [B2B-](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes).

## Nur Adobe Commerce {#ee-only}

>[!NOTE]
>
>Diese Funktion ist nur für Adobe Commerce-Instanzen verfügbar.

## Aufspaltung der DB veraltet {#deprecate-split-db}

>[!IMPORTANT]
>
>Die Funktion „Split Database[ wurde in ](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) 2.4.2 von Adobe Commerce als veraltet gekennzeichnet. Siehe [Von einer geteilten Datenbank auf eine einzelne Datenbank zurücksetzen](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Abwärtsinkompatible Änderungen {#bics}

>[!NOTE]
>
>Adobe Commerce-Versionen können abwärtsinkompatible Änderungen (BICs) enthalten. Informationen zu abwärtsinkompatiblen Änderungen finden Sie unter [BIC-Referenz](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). Die wichtigsten abwärtsinkompatiblen Probleme werden in [BIC-Highlights](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/) beschrieben. Nicht alle Versionen enthalten wichtige BICs.

## Alpha-Haftungsausschluss {#alpha}

>[!IMPORTANT]
>
>[Alpha](/help/release/versioning-policy.md#alpha-patch-release) Versionen können unvollständig sein und enthalten wahrscheinlich Fehler. Sie werden „WIE BESEHEN“ und ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, Alpha-Versionen (über Adobe Support Services oder anderweitig) zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen. Kunden sollten sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung von Alpha-Versionen oder Begleitdokumenten oder -materialien verlassen. Die Verwendung von Alpha-Versionen erfolgt vollständig auf eigene Gefahr des Kunden.

## Beta-Haftungsausschluss {#beta}

>[!IMPORTANT]
>
>Beta-Versionen können Mängel enthalten und werden ohne Mängelgewähr und ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen (über Adobe Support Services oder andere Services). Kunden sollten Vorsicht walten lassen und sich in keiner Weise auf die korrekte Funktionsweise oder Leistung von Beta-Versionen und/oder Begleitdokumenten oder -materialien verlassen. Jede Nutzung der Beta-Versionen erfolgt daher ausschließlich auf eigene Gefahr des Kunden.

## CVE-Mitteilung {#cve-notice}

>[!NOTE]
>
>Ab Version 2.3.2 werden wir indexierte Common Vulnerabilities and Expositions (CVE)-Nummern mit jedem Sicherheitsfehler zuweisen und veröffentlichen, der uns von externen Parteien gemeldet wurde. Auf diese Weise können Benutzer nicht adressierte Schwachstellen in ihrer Bereitstellung leichter identifizieren. Weitere Informationen zu CVE-Kennungen finden Sie unter [CVE](https://cve.mitre.org/).

## Weitere Versionsinformationen {#other-release-info}

>[!NOTE]
>
>Obwohl der Code für Verbesserungen und Fehlerbehebungen in diesen Versionshinweisen mit Adobe Commerce gebündelt ist, werden mehrere dieser Projekte (z. B. B2B, Page Builder und Progressive Web Applications (PWA) Studio) ebenfalls unabhängig voneinander veröffentlicht. Fehlerbehebungen für diese Projekte werden in den separaten, projektspezifischen Versionsinformationen dokumentiert, die in der Dokumentation für jedes Projekt verfügbar sind. Siehe [Produktversionsübersicht](/help/release/release-notes/overview.md).

## PHP-Prozesssteuerung {#php-process-control}

Bevor Sie Indexer im parallelen Modus ausführen können, müssen Sie Process Control Support (`pcntl`) in PHP aktivieren. Siehe [Installation](https://www.php.net/manual/en/pcntl.installation.php) in der PHP-Dokumentation.

## Benutzerdefinierte Patches {#custom-patches-disclaimer}

>[!IMPORTANT]
>
>Adobe unterstützt nicht die Anwendung offizieller, von Adobe bereitgestellter Patches mit dieser Methode. Verwenden Sie die folgende Methode auf eigene Gefahr. Verwenden Sie die [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, um offizielle Patches anzuwenden. Führen Sie immer umfassende Tests durch, bevor Sie einen benutzerdefinierten Patch bereitstellen.

## Sicherheits-Patch-Backports Oktober 2025 {#oct-2025-backports}

<!--These fixes were backported to 2.4.8-pe, 2.4.7-p8, and 2.4.6-p13-->

* **Migration von TinyMCE zu Hugerte.org**

  Aufgrund des Auslaufens der Unterstützung für TinyMCE 5 und 6 und der Lizenzierungsinkompatibilitäten mit TinyMCE 7 wird die aktuelle Implementierung des Adobe Commerce WYSIWYG Editors von TinyMCE in den Open-Source-Editor [HugeRTE Editor](https://hugerte.org/) migriert.

  Diese Migration stellt sicher, dass Adobe Commerce weiterhin mit der Open-Source-Lizenzierung konform ist, bekannte TinyMCE 6-Schwachstellen vermeidet und Händlern und Entwicklern ein modernes, unterstütztes Bearbeitungserlebnis bietet.

* **Unterstützung für das Apache ActiveMQ Artemis STOMP-Protokoll wurde hinzugefügt**

  Unterstützung für ActiveMQ Artemis Open-Source-Nachrichtenbroker durch das Simple Text Oriented Messaging Protocol (STOMP) wurde hinzugefügt. Es bietet ein zuverlässiges und skalierbares Messaging-System, das Flexibilität für STOMP-basierte Integrationen bietet. Siehe [Apache ActiveMQ Artemis](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework#apache-activemq-artemis-stomp) im *Commerce-Konfigurationshandbuch*.

## Die Checkout-Seite kann static.min.js und mixins.min.js nicht laden. {#checkout-page-fails-to-load-static-min-js-and-mixins-min-js}

Nach den letzten CSP-/SRI-Änderungen werden static.min.js und mixins.min.js nicht auf der Checkout-Seite geladen, wenn sowohl die JavaScript-Bündelung als auch die Minimierung im Produktionsmodus aktiviert sind. Daher werden RequireJS-Mixins nicht ausgeführt und Checkout-Knockout-Vorlagen können nicht aufgelöst werden (z. B. `"Failed to load the 'Magento_Checkout/shipping' template requested by 'checkout.steps.shipping-step.shippingAddress'"`).

**Workaround**:

* JavaScript-Bundle deaktivieren oder
* Wenn Sie die JavaScript-Bündelung aktiviert lassen, deaktivieren Sie die JavaScript-Minimierung.

>[!IMPORTANT]
>
>Deaktivieren Sie CSP nicht und entfernen Sie den SRI-Schutz in der Produktion nicht. Jeder Bypass auf Plug-in-Ebene sollte nur als letztes Mittel für einen Hotfix verwendet werden und muss vom Sicherheits-Team überprüft werden.

**Hotfix**:

Ein Hotfix zu diesem Problem wird so bald wie möglich veröffentlicht. Bitte die Seite mit den Versionshinweisen auf Aktualisierungen überwachen.
