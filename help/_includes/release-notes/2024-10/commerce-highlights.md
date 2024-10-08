---
source-git-commit: b30fe4ed4d910ac3a99d3bcf4ff94103bcbd1369
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 0%

---
# Adobe Commerce 2.4.7 - Beta-Highlights im Oktober 2024

## Highlights

Diese Version von Adobe Commerce enthält mehrere wichtige Sicherheitsverbesserungen und Plattformverbesserungen.

### Sicherheit

Die folgenden Sicherheitsverbesserungen in dieser Version verbessern die Kompatibilität mit den neuesten Best Practices für die Sicherheit:

>[!NOTE]
>
>Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

<table style="table-layout-auto">
    <tbody>
        <tr>
            <td><strong>Einstellungen</strong></td>
            <td>Diese Version umfasst die folgenden Verbesserungen der Sicherheitseinstellungen:
              <ul>
                <li><strong>Verschlüsselungsschlüsselrotation</strong>: Es ist jetzt ein neuer CLI-Befehl zum Ändern des Verschlüsselungsschlüssels verfügbar. Weitere Informationen finden Sie im Knowledge Base-Artikel <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102">Fehlerbehebung beim Rotieren des Verschlüsselungsschlüssels: CVE-2024-34102</a> .<!-- AC-12589 --></li>
                <li><strong>Einmalige Kennworteinstellungen (OTP)</strong>: Diese Aktualisierung ist erforderlich, um einen Fehler zu beheben, der durch eine <a href="https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value">rückwärtskompatible Änderung</a> in 2.4.7 verursacht wurde. Die Beschreibung des Felds <strong>[!UICONTROL OTP Window]</strong> bietet jetzt eine genaue Erläuterung der Einstellung, und der Standardwert wurde von <code>1</code> in <code>29</code> geändert.<!-- AC-11762 --></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### Plattform

Die folgenden Plattformaktualisierungen für diese Version stellen sicher, dass Adobe Commerce eine robuste und zuverlässige Plattform bleibt, die den Anforderungen moderner Commerce-Umgebungen gerecht wird:

<table style="table-layout-auto">
    <tbody>
        <tr>
            <td><strong>Datenbank</strong></td>
            <td>In Übereinstimmung mit unserer <a href="/help/release/lifecycle-policy.md">Lebenszyklusrichtlinie unterstützen</a> ist Adobe Commerce jetzt mit den folgenden LTS-Versionen (Long Term Support) der folgenden Datenbanktechnologien kompatibel:
              <ul>
                <li><strong>MariaDB 11.4 LTS</strong> <em>_(bis 2029 unterstützt)_</em>: Die vorherige Version (MariaDB 10.6) erreicht das Ende der Lebensdauer im Jahr 2026, wodurch diese Aktualisierung für die Wahrung der Systemintegrität und -leistung unerlässlich ist. MariaDB 10.6 wird weiterhin unterstützt, aber Adobe empfiehlt beim Upgrade auf Adobe Commerce 2.4.8 ein Upgrade auf MariaDB 11.4.</li>
                <li><strong>MySQL 8.4 LTS</strong> <em>_(bis 2032 unterstützt)_</em>: Die vorherige Version (MySQL 8.0) endet 2026, wodurch diese Aktualisierung für die Aufrechterhaltung der Systemintegrität und -leistung unerlässlich ist. MySQL 8.0 wird weiterhin unterstützt, aber Adobe empfiehlt beim Upgrade auf Adobe Commerce 2.4.8 ein Upgrade auf MySQL 8.4</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>PHP</strong></td>
            <td>Diese Version umfasst die folgenden PHP-Verbesserungen:
            <ul>
              <li><strong>PHP 8.1</strong>: Mit dieser Version wird die Kompatibilität von PHP 8.1 mit Adobe Commerce 2.4.8 entfernt. Sie müssen auf PHP 8.3 aktualisieren, bevor Sie auf Adobe Commerce 2.4.8 aktualisieren.</li>
              <li><strong>PHP 8.2</strong>: Eine der wesentlichen Änderungen in PHP 8.2 beinhaltet die Einstellung der Übergabe von null an nicht nullbare interne Funktionsparameter. Diese Version behandelt veraltete PHP 8.1-Funktionen in Kernplattformkomponenten und stellt die Kompatibilität mit PHP 8.2 sicher.</li>
              <li><strong>PHPUnit 10</strong>: Diese Version behandelt verschiedene wichtige Probleme, verbessert die Kompatibilität und stellt sicher, dass das Adobe Commerce-Test-Framework mit den neuesten Branchenstandards übereinstimmt. Adobe empfiehlt allen Commerce Marketplace-Anbietern und -Kunden mit Anpassungen zu überprüfen, ob ihre Geräte- und Integrationstests auf PHPUnit 10 statt auf 9 ausgeführt werden.</li>
            </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Komponenten</strong></td>
            <td>Die folgenden Drittanbieter-Komponenten und -Abhängigkeiten </a> wurden auf die neuesten stabilen Versionen aktualisiert, um die Plattformstabilität und -leistung zu verbessern:<a href="/help/release/packages/adobe-commerce.md">
              <ul>
                <li>jquery/validate 1.20.x</li>
                <li>moment.js 2.30.1</li>
                <li>monolog/monolog 3.x</li>
                <li>monolog/Require.js 2.3.7</li>
                <li>TinyMCE 7.x</li>
                <li>wikimedia/less.php 5.x</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Suche</strong></td>
            <td>Adobe Commerce ist jetzt für OpenSearch 2.x optimiert und nicht mehr mit Elasticsearch kompatibel. Alle Elasticsearch 7- und 8-Module und -Klassen werden in der Codebase nicht mehr unterstützt. Adobe empfiehlt dringend, die Umstellung auf OpenSearch für lokale und Cloud-Infrastrukturbereitstellungen durchzuführen, um die kontinuierliche Unterstützung und Kompatibilität sicherzustellen. Siehe <a href="/help/upgrade/prepare/opensearch-migration.md">Migration zu OpenSearch</a>.
              <ul>
                <li>Die Optionen für Elasticsearch 7 und Elasticsearch 8 sind in der Admin-Konfiguration jetzt mit "(nicht mehr unterstützt)"beschriftet.</li>
                <li>Wenn ein Benutzer in der Admin-Konfiguration Elasticsearch als Suchmaschine auswählt, zeigt Commerce eine Benachrichtigung mit dem Hinweis "<em>"Diese Suchmaschinenoption wird von Adobe nicht mehr unterstützt. Wir empfehlen stattdessen die Verwendung von OpenSearch als Suchmaschine."</em></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### Leistung

Diese Version umfasst die folgenden Leistungsverbesserungen:

<table style="table-layout-auto">
    <tbody>
        <tr>
            <td><strong>Indexer</strong></td>
            <td>Der standardmäßige <a href="/help/implementation-playbook/best-practices/maintenance/indexer-configuration.md#set-indexers-to-update-on-schedule">Indexmodus</a> für alle Indexer ist jetzt [!UICONTROL **Update by Schedule**] bei der Installation einer neuen Version von Adobe Commerce oder der Aktualisierung von einer früheren Version. Der neue Standard stellt sicher, dass Indexer in der empfohlenen Konfiguration sind, was die Systemleistung verbessert und potenzielle Probleme verringert.</td>
        </tr>
    </tbody>
</table>

### Qualität

Diese Version umfasst die folgenden Qualitätsverbesserungen:

<table style="table-layout-auto">
    <tbody>
        <tr>
           <td><strong>Bestand</strong></td>
           <td>Das System funktioniert jetzt ohne die zuvor ausgeblendete Abhängigkeit vom Katalog, die vom InventoryIndexer eingeführt wurde, und stellt sicher, dass die Produkterstellung, der Anzeigemodus-Wechsel, die Änderung des Lagerstatus und andere zugehörige Funktionen erwartungsgemäß funktionieren. Zuvor führte diese versteckte Abhängigkeit zu Inkonsistenzen, da verschiedene Entitäten synchronisiert und der Indexer verschiedene Entitäten verwendete.</td>
        </tr>
        <tr>
            <td><strong>Bestellungen</strong></td>
            <td>Um Verwirrung zu minimieren, wurde die Schaltflächenbeschriftung [!UICONTROL **Submit Comment**] auf der Seite <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing#notes-for-this-order">Bestelldetails</a> in [!UICONTROL **Update**] geändert.</td>
        </tr>
    </tbody>
</table>

### GraphQL

Diese Version umfasst die folgenden GraphQL-Verbesserungen:

<table style="table-layout-auto">
    <tbody>
        <tr>
           <td><strong>Allgemeine Verbesserungen</strong></td>
           <td>Diese Version umfasst die folgenden allgemeinen GraphQL API-Verbesserungen:
             <ul>
               <li><!--LYNX-401--><strong>StoreConfig</strong>: Die Felder <code>grouped_product_image</code> und <code>configurable_product_image</code> wurden zum Typ <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-StoreConfig"><code>StoreConfig</code></a> hinzugefügt.</li>
              <li><!--LYNX-387--><strong>CartItemPrices</strong>: Dem Typ <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a> wurden die folgenden neuen Felder hinzugefügt, um eine genaue Anzeige der Preise und Discount-Berechnungen zu unterstützen:
                <ul>
                  <li><code>original_item_price</code></li>
                  <li><code>original_row_total</code></li>
                  <li><code>row_total_including_catalog_discounts_only</code></li>
                </ul>
              </li>
              <li><!--LYNX-451--><strong>WarenkorbPreise</strong>: Das Feld <code>grand_total_excluding_tax</code> wurde zum Typ <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartPrices"><code>CartPrices</code></a> hinzugefügt und bietet klare steuerinklusive Preise.</li>
              <li><!--LYNX-542--><strong>updateCartItems mutation</strong>: Die <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-updateCartItems"><code>updateCartItems</code></a> -Mutation wurde aktualisiert, um Erfolgsantworten mit Fehlerdetails anstelle von Ausnahmen zurückzugeben. Verbesserte Fehlerzuordnung zur besseren Übersichtlichkeit von Benutzerbenachrichtigungen.</li>
              <li><!--LYNX-522--><strong>recaptchaV3Config query</strong>: Es wurde ein <code>theme</code> -Feld zur <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-recaptchaV3Config"><code>recaptchaV3Config</code></a> -Abfrage hinzugefügt. In diesem Feld können Sie den Namen des Designs angeben, das zum Rendern des reCaptcha verwendet werden soll.</li>
              <li><!--LYNX-540--><strong>ProductInterface</strong>: Es wurde ein <code>quantity</code> -Feld in das <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-ProductInterface"><code>ProductInterface</code></a> eingeführt, um Details auf der Lagerebene anzugeben. Er zeigt den verfügbaren Bestand oder null basierend auf den Admin-Einstellungen an.</li>
               <li><!--LYNX-460--><strong>Bundle-Produkte</strong>: Die Preisanzeige für Bundle-Produkte wurde korrigiert, sodass korrekte Preis- und Währungsinformationen gewährleistet sind.</li>
               <li><!--LYNX-547--><strong>Menge</strong>: Verfeinerte Nachrichten für unzureichende und nicht verfügbare Mengenbenachrichtigungen.</li>
               <li><!--LYNX-541--><strong>UngenügenderStockError-Typ</strong>: Es wurde ein neuer <code>InsufficientStockError</code>-Typ hinzugefügt, um Fälle zu verarbeiten, in denen die Lagerbestände unzureichend sind. Das Schema wurde angepasst, um neue Fehlertypen zu unterstützen und so die Funktionen für die Fehlerberichterstellung zu verbessern.</li>
               <li><!--LYNX-476--><strong>Lagerbestandsbetrag</strong>: Verbesserte Fehlermeldungen, die verfügbare Lagerbestandsmengen enthalten. Bietet Benutzern klarere Einblicke in die Lagerbestände bei Bestellaktualisierungen.</li>
               <li><!--LYNX-377--><strong>Angeforderte Menge</strong>: Der <code>not_available_message</code> wurde zum <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemInterface"><code>CartItemInterface</code></a> hinzugefügt.</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>Kundenverwaltung</strong></td>
           <td>Diese Version umfasst die folgenden Verbesserungen der Kundenverwaltung:
             <ul>
               <li><!--LYNX-391--><strong>generateCustomerToken mutation</strong>: Die Fehlerbehandlung in der <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-generateCustomerToken"><code>generateCustomerToken</code></a> -Mutation wurde verbessert, um bestimmte Meldungen für nicht bestätigte E-Mails bereitzustellen. Unterstützt eine bessere Benutzerführung und Fehlerbehebung.</li>
               <li><!--LYNX-390--><strong>resendConfirmationEmail mutation</strong>: Es wurde eine neue <code>resendConfirmationEmail</code>-Mutation für die erneute E-Mail-Bestätigung hinzugefügt.</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>Auftragsverwaltung</strong></td>
           <td>Diese Version umfasst die folgenden Verbesserungen der Verwaltung von Benutzeraufträgen:
             <ul>
              <li><!--LYNX-470--><strong>Datum der ersten Bestellung</strong>: Dem Typ <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrders"><code>CustomerOrders</code></a> wurde ein neues Feld <code>date_of_first_order</code> hinzugefügt.</li>
              <li><!--LYNX-468--><strong>OrderAddress</strong>: Der Typ <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderAddress"><code>OrderAddress</code></a> wurde um benutzerdefinierte Attribute erweitert, wodurch die Sichtbarkeit der Bestelldetails verbessert wird. Unterstützt die Anzeige zusätzlicher Informationen auf Bestellbestätigungsseiten.</li>
              <li><!--LYNX-458--><strong>GuestOrder- und GuestOrderByToken-Abfragen</strong>: Die Abfragen <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrder"><code>guestOrder</code></a> und <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrderByToken"><code>guestOrderByToken</code></a> wurden dahingehend aktualisiert, dass sie benutzerdefinierte Adressattribute enthalten, sodass vollständige Adressinformationen für neue Konten sichergestellt sind.</li>
              <li><!--LYNX-450--><strong>CustomerOrder type</strong>: Das Feld<code>is_virtual</code> wurde zum Typ <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a> hinzugefügt und unterstützt die virtuelle Produktidentifizierung. Verbessert die Auftragsverarbeitung durch die Unterscheidung von virtuellen und physischen Produkten.</li>
              <li><!--LYNX-449--><strong>orderItemPrices</strong>: Es wurde ein <code>OrderItemPrices</code>-Typ ähnlich <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a> zu <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderItemInterface"><code>OrderItemInterface</code></a> mit mehreren neuen Preisfeldern hinzugefügt.</li>
              <li><!--LYNX-448--><strong>Zusammenführen von Gastaufträgen</strong>: Verbesserte API-Funktion zum Zusammenführen von Gastaufträgen mit Kundenkonten basierend auf E-Mail-Übereinstimmung. Optimiert die Auftragsverwaltung für Bestandskunden.</li>
              <li><!-- LYNX-523: --><strong>available_actions-Feld</strong>: Der Typ <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a> wurde um ein Feld <code>available_actions</code> erweitert, um eine bessere Auftragsverwaltung zu ermöglichen. Das Feld "available_actions"wird einer Auflistung zugeordnet, in der die möglichen Aktionen aufgelistet sind, die für die Reihenfolge ausgeführt werden können.</li>
              <li><!-- LYNX-524 --><strong>CustomerOrder type</strong>: Das Feld <code>customer_info</code> wurde zum Typ <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a> hinzugefügt. Dieses Feld erfordert und <code>OrderCustomerInfo</code>, die Details zum Kundennamen definieren.</li>
              <li><!--LYNX-519--><strong>Fehlercodes für die Auftragsabbruch</strong>: Es wurden detaillierte Fehlercodes zum Typ <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CancelOrderOutput"><code>CancelOrderOutput</code></a> hinzugefügt. Verbesserte Fehlerbehebung und Benutzerfeedback für die Abbruchsvorgänge von Bestellungen.</li>
              <li><!--LYNX-515--><strong>Gastbenutzer konnten Rückgaben für Bestellungen erstellen</strong>: Die <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-requestReturn"><code>requestReturn</code></a> -Mutation wurde angepasst, um die Rückgabe von Gastbestellungen zu unterstützen.</li>
              <li><!--LYNX-505--><strong>confirmCancelOrder mutation</strong>: Es wurde eine neue <code>confirmCancelOrder</code> -Mutation hinzugefügt, um die Stornierung von Bestellungen für Gastbenutzer zu erleichtern.</li>
             </ul>
           </td>
        </tr>
    </tbody>
</table>
