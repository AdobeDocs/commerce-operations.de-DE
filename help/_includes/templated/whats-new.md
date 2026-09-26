---
source-git-commit: 076f76112159204c0f23d3ddfbb606e274c406eb
workflow-type: tm+mt
source-wordcount: '1538'
ht-degree: 1%
---
# Neue Vorlage

## Neue Funktionen

Diese Seite enthält die Änderungen, die in den letzten 60 Tagen vorgenommen wurden. Wir schließen alle kleineren Aktualisierungen, wie z. B. die Bearbeitung von Kopien, von dieser Liste aus.

### &#x200B;18. September 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Beschreibung</th>
      <th>Typ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Es wurde <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/release/planning/monthly-isolated-security-patches">Monthly Isolated Security Patching Policy</a> hinzugefügt, die erklärt, wie Adobe Commerce gezielte, isolierte CVE-Fehlerbehebungen am Patch-Dienstag zwischen den vollständigen Sicherheits-Patch-Versionen bereitstellt und wie sie angewendet und überprüft werden.</p>
</td>
      <td>
        Neues Thema
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/681f7f0589aed8787aaf165d36ac00f670d751ce">verpflichten</a></td>
    </tr>
  </tbody>
</table>

### &#x200B;15. September 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Beschreibung</th>
      <th>Typ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Der Leitfaden <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration">Redis/Valkey-Service-</a> wurde korrigiert, um klarzustellen, dass die Bereitstellungsvariablen <code>VALKEY_BACKEND</code> und <code>REDIS_BACKEND</code> nicht bestimmen, welcher Cache-Service von Adobe Commerce tatsächlich verwendet wird, und dass <code>VALKEY_USE_SLAVE_CONNECTION</code>/<code>REDIS_USE_SLAVE_CONNECTION</code> mit dem tatsächlich in der Umgebung verfügbaren Service übereinstimmen müssen.</p>
</td>
      <td>
        Technisch
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/49781ad38a266fffa1be080b5a093327a28cf6a6">verpflichten</a></td>
    </tr>
  </tbody>
</table>

### &#x200B;8. September 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Beschreibung</th>
      <th>Typ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Adobe Commerce Patching Automation ist jetzt allgemein verfügbar. Weitere Informationen finden <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/tools/caps-tool/intro"> in </a> Dokumentation .</p>
</td>
      <td>
        Größere Aktualisierung, neues Thema
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/a88bfea449616c0b79c5bd3380bec74c68687052">verpflichten</a></td>
    </tr>
  </tbody>
</table>

### &#x200B;26. August 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Beschreibung</th>
      <th>Typ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Eine detaillierte Beschreibung der QPT 1.1.82-Fehlerbehebung für <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4840">ACP2E-4840: GraphQL-Produktabfrage gibt für vorrätige Produkte in benutzerdefinierten Lagerbeständen keine Menge zurück</a> wurde hinzugefügt.</p>
</td>
      <td>
        Neues Thema, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/edfc38af34925749c5acb36d2c0bcfc5d16a577a">verpflichten</a></td>
    </tr>
  </tbody>
</table>

### &#x200B;19. August 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Beschreibung</th>
      <th>Typ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Die Dokumentation zur Zwischenspeicherung in Commerce wurde aktualisiert mit klareren On-Premise- vs. Cloud-Anleitungen und neuen Migrationsanleitungen für die Umstellung mit Symfony L2-Cache auf Valkey:<br />- Aktualisierte <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cache/caching-overview">Übersicht über Zwischenspeicher und Konfigurationsoptionen</a>.<br />- Aktualisierte <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cache/cache-types">Konfigurieren von Cache-Frontends und -Typen</a>.<br />- Aktualisierte <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cache/cache-options">Cache-Backend-Optionen und Speicherreferenz</a>.<br />- Aktualisierte <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cache/level-two-cache">L2-Cache-Konfiguration zur Leistungsoptimierung</a> mit Anleitungen für die Migration von <code>RemoteSynchronizedCache</code> zu Symfony L2-Cache.<br />- Aktualisierte <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration"></a> Best Practices für Valkey und Redis mit Cloud-spezifischen Migrationsschritten zu Symfony L2-Cache.</p>
</td>
      <td>
        Größere Aktualisierung
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/3a840b544de95a4bb17ef49d0325b16d461aecaa">verpflichten</a></td>
    </tr>
  </tbody>
</table>

### &#x200B;14. August 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Beschreibung</th>
      <th>Typ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Die Schritte zum Überprüfen der Version der Service-Abhängigkeiten in der Cloud-Benutzeroberfläche wurden aktualisiert. Außerdem wurde der Link zum Handbuch zum Generieren eines Berichts zur Upgrade-Kompatibilität für den Store unter <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/release/planning/security-enforcement-policy#action-1-verify-and-upgrade-third-party-software-dependencies">Überprüfen und Aktualisieren von Software-Abhängigkeiten von Drittanbietern</a> aktualisiert.</p>
</td>
      <td>
        Technisch
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/54ac98c35e1f161f390587601484db4e3294b6af">verpflichten</a></td>
    </tr>
  </tbody>
</table>

### &#x200B;13. August 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Beschreibung</th>
      <th>Typ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Es wurde eine detaillierte Beschreibung der QPT 1.1.82-Fehlerbehebung für <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4194">ACP2E-4194: GraphQL-Anfragen mit unbekannten Filternamen verursachen PHP-Ausnahmeprotokolle</a> hinzugefügt.</p>
</td>
      <td>
        Neues Thema, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/d4202395c5b7bb5e8c4a95d8fb353ec0fc523fcb">verpflichten</a></td>
    </tr>
    <tr>
      <td><p>Es wurde eine detaillierte Beschreibung der Fehlerbehebung für QPT 1.1.82 für <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4695">ACP2E-4695: Fehler bei der Katalogregelindizierung wegen unzureichendem Arbeitsspeicher aufgrund übermäßiger Speichernutzung</a> hinzugefügt.</p>
</td>
      <td>
        Neues Thema, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/dc891435d573c4c333e58e25b2dbe003ffa08f27">verpflichten</a></td>
    </tr>
    <tr>
      <td><p>Fehlerkorrekturen in den EOS-Datumsangaben für Adobe Commerce 2.4.5 und 2.4.6.</p>
</td>
      <td>
        Technisch
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/8de65d309dcd4158627910ce5c0b87966db5c948">verpflichten</a></td>
    </tr>
  </tbody>
</table>

### &#x200B;12. August 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Beschreibung</th>
      <th>Typ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>PHP 8.4 wurde in den <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/release/notes/adobe-commerce/2-4-9#php-and-composer">2.4.9-Versionshinweisen als unterstützte PHP-Version entfernt</a> da diese für die Verwendung in der Produktion nicht empfohlen wird und nur aus Gründen der Upgrade-Kompatibilität vorhanden ist.</p>
</td>
      <td>
        Versionshinweise, technische
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/603bb70012a2f92ceeaad644d5252c4677a1a47c">verpflichten</a></td>
    </tr>
    <tr>
      <td><p>Es wurde eine detaillierte Beschreibung der Fehlerbehebung für QPT 1.1.82 für <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4894">ACP2E-4894: Neue Bestellungen werden im Admin-Bestellungsraster mit einer Verzögerung angezeigt, wenn die asynchrone Indizierung aktiviert ist</a>.</p>
</td>
      <td>
        Neues Thema, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/ad40d94c1618f7e423fd6a773185b8fba48c2c72">verpflichten</a></td>
    </tr>
    <tr>
      <td><p>Eine detaillierte Beschreibung der QPT 1.1.82 -Fehlerbehebung für <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4698">ACP2E-4698 wurde hinzugefügt: Page Builder-Text-Inline-Bearbeitung speichert absolute Medien-URLs anstelle der portablen -Direktive</a>.</p>
</td>
      <td>
        Neues Thema, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/68e5e99ac0717b0e358acd6acf9934044a917a82">verpflichten</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/de/docs/commerce-operations/release/versions"> Auf der Seite „Veröffentlichte Versionen“ wurden die Bereitstellungstermine für mehrere Adobe Commerce-Versionen korrigiert und abgeschlossen (Ende der Unterstützung, erweiterte Unterstützung und zusätzliche Sicherheitskorrekturen</a>.</p>
</td>
      <td>
        Technisch
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/fc5a7f7a466e6419a3e712bcbec4224f98f8c480">verpflichten</a></td>
    </tr>
  </tbody>
</table>

### &#x200B;11. August 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Beschreibung</th>
      <th>Typ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Es wurde <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/system-requirements">Systemanforderungen</a> aktualisiert, um RabbitMQ 3.13 als unterstützte Version für Adobe Commerce 2.4.4-p18 (neueste Version) hinzuzufügen, wodurch ein Blocker für den Debian-OS-Aktualisierungspfad aufgelöst wird.</p>
</td>
      <td>
        Technisch
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/046d641dc45b269c6495bef0c06c53bdc500227b">verpflichten</a></td>
    </tr>
  </tbody>
</table>

### &#x200B;10. August 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Beschreibung</th>
      <th>Typ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Eine detaillierte Beschreibung der Fehlerbehebung für QPT 1.1.82 wurde hinzugefügt <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4797">ACP2E-4797: Admin WYSIWYG Editor und Page Builder blockieren 4-Byte-Unicode-Zeichen, wenn utf8mb4 unterstützt wird</a>.</p>
</td>
      <td>
        Neues Thema, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/c97bb9c77eb0ec4bbc92d042cfa9fd440e970ca7">verpflichten</a></td>
    </tr>
    <tr>
      <td><p>Es wurde eine detaillierte Beschreibung der Fehlerbehebung für QPT 1.1.82 für <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4682">ACP2E-4682: Storefront-Seiten, die Zitate überprüfen, hinzugefügtActiveCreate empty quote records</a>.</p>
</td>
      <td>
        Neues Thema, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/ceac870e3ccb9eeee64e3b574aaccd33c6ab69d0">verpflichten</a></td>
    </tr>
    <tr>
      <td><p>Es wurde eine detaillierte Beschreibung der Fehlerbehebung von QPT 1.1.82 für <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4799">ACP2E-4799: GraphQL Query Requisition_lists gibt eine falsche total_count mit Paginierung </a>.</p>
</td>
      <td>
        Neues Thema, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/19f854db1a0ff78d0a6dca070b4b6db09d3de83e">verpflichten</a></td>
    </tr>
    <tr>
      <td><p>Es wurde eine detaillierte Beschreibung der Fehlerbehebung von QPT 1.1.82 für <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4870">ACP2E-4870: E-Mails von Produktanwarnungen ignorieren die E-Mail-Einstellungen der Store-Ansicht</a> hinzugefügt.</p>
</td>
      <td>
        Neues Thema, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/907df07e641ab7124353f89ca799f92d097aa54f">verpflichten</a></td>
    </tr>
    <tr>
      <td><p>Die Tabelle <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/release/product-availability">Produktverfügbarkeit</a> wurde mit Unterstützung für Adobe Commerce 2.4.9 aktualisiert und der Page Builder-Eintrag, der seit 2.4.3 Teil des Kernprodukts ist, wurde entfernt.</p>
</td>
      <td>
        Größere Aktualisierung
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/a5120adab9f624677447889722359951e775c3f3">verpflichten</a></td>
    </tr>
  </tbody>
</table>

### &#x200B;9. August 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Beschreibung</th>
      <th>Typ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Es wurde eine detaillierte Beschreibung der Fehlerbehebung für QPT 1.1.82 für <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4593">ACP2E-4593: Falsche Website-Einschränkung CMS auf der sekundären Website in Storefronts mit mehreren Websites hinzugefügt</a>.</p>
</td>
      <td>
        Neues Thema, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/86c85db0098192092241b680d38b882f1a52b578">verpflichten</a></td>
    </tr>
  </tbody>
</table>

### &#x200B;6. August 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Beschreibung</th>
      <th>Typ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Die Unterstützungsmatrix für die B2B-Erweiterungsversion in <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/release/product-availability">Produktverfügbarkeit</a> für Adobe Commerce 2.4.6, 2.4.7 und 2.4.8 wurde korrigiert.</p>
</td>
      <td>
        Technisch
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/50fb71aa968abf1302e86ffeb3d3b3a66b3c33d5">verpflichten</a></td>
    </tr>
  </tbody>
</table>

### &#x200B;31. Juli 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Beschreibung</th>
      <th>Typ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Eine detaillierte Beschreibung der Fehlerbehebung für QPT 1.1.82 wurde hinzugefügt <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4547">ACP2E-4547: Der Administrator kann einem Angebot kein Standardkatalogprodukt hinzufügen, wenn es nicht dem freigegebenen Katalog des Benutzers zugewiesen ist</a>.</p>
</td>
      <td>
        Neues Thema, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/6d0313c01e979d3d4bd3e781e2f0e9c336bbd8c5">verpflichten</a></td>
    </tr>
  </tbody>
</table>

### &#x200B;30. Juli 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Beschreibung</th>
      <th>Typ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Es wurde <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/release/planning/security-enforcement-policy">Sicherheitsrichtlinie: Erforderliche Aktionen und Fristen</a> hinzugefügt, damit Adobe Commerce on Cloud-Kunden die Anforderungen, Zeitpläne und Anweisungen für das Upgrade von Adobe Commerce auf Cloud-Bereitstellungen mit nicht unterstützten Versionen oder Softwareabhängigkeiten von Drittanbietern erläutern.</p>
</td>
      <td>
        Neues Thema
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/b7649aae1f8cab020c1081db2b2363bca22adfed">verpflichten</a></td>
    </tr>
  </tbody>
</table>

### &#x200B;28. Juli 2026

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>Beschreibung</th>
      <th>Typ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>Es wurde eine detaillierte Beschreibung der Fehlerbehebung für QPT 1.1.82 für <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4805">ACP2E-4805: Checkout-Anfragen werden für konfigurierbare Produkte verlangsamt, wenn das erste verkaufbare untergeordnete Element später in der Liste angezeigt wird</a>.</p>
</td>
      <td>
        Neues Thema, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/1b5fb4826f6599d7b7609dedfeb545f29454ba4d">verpflichten</a></td>
    </tr>
    <tr>
      <td><p>Eine detaillierte Beschreibung der QPT 1.1.82-Fehlerbehebung für <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4748">ACP2E-4748: Ablauf von Belohnungspunkten wird in Stores mit einem großen Belohnungspunktverlauf langsam ausgeführt</a>.</p>
</td>
      <td>
        Neues Thema, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/30fe149f9743ceca7f40374246b4fc9b9503c590">verpflichten</a></td>
    </tr>
    <tr>
      <td><p>Eine detaillierte Beschreibung der Fehlerbehebung für QPT 1.1.82 wurde hinzugefügt <a href="https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4875">ACP2E-4875: Admin-Benutzer haben sich beim Öffnen von Kundenkonten mit großen Adressbüchern abgemeldet</a>.</p>
</td>
      <td>
        Neues Thema, qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/3174f84e0a8c64aaed50cc075a9287bc011778ef">verpflichten</a></td>
    </tr>
  </tbody>
</table>
