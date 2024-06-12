---
source-git-commit: 10a6329502bc63ec06bac0652301770bd8e2935a
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---
# 2.4.7 Sicherheitsverbesserungen

Bisher sind keine bestätigten Angriffe im Zusammenhang mit diesen Problemen aufgetreten. Bestimmte Schwachstellen können jedoch potenziell ausgenutzt werden, um auf Kundeninformationen zuzugreifen oder Administratorsitzungen zu übernehmen. Die meisten dieser Probleme erfordern, dass ein Angreifer zunächst Zugriff auf den Admin erhält. Daher möchten wir Sie daran erinnern, alle erforderlichen Schritte zum Schutz Ihres Administrators zu unternehmen, einschließlich, aber nicht beschränkt auf diese Bemühungen:

* IP-auf die Zulassungsliste setz
* [Zweifaktorauthentifizierung](https://developer.adobe.com/commerce/testing/functional-testing-framework/two-factor-authentication/)
* Verwendung eines VPN
* Verwendung eines eindeutigen Standorts anstelle von `/admin`
* Gute Passworthygiene

Verbesserungen der Sicherheit in dieser Version verbessern die Einhaltung der neuesten Best Practices für die Sicherheit.

* **Änderungen am Verhalten nicht generierter Cache-Schlüssel**:

   * Nicht generierte Cache-Schlüssel für Bausteine enthalten jetzt Präfixe, die sich von Präfixen für automatisch generierte Schlüssel unterscheiden. (Nicht generierte Cache-Schlüssel sind Schlüssel, die über die Syntax der Vorlagenanweisung oder die `setCacheKey` oder `setData` Methoden.)
   * Nicht generierte Cache-Schlüssel für Blöcke dürfen jetzt nur Buchstaben, Ziffern, Bindestriche (-) und Unterstriche (_) enthalten.  <!-- AC-9831 -->

* **Einschränkungen bei der Anzahl der automatisch generierten Gutscheincodes**. Commerce beschränkt jetzt die Anzahl der automatisch generierten Couponcodes. Der Standardwert ist maximal 250.000. Händler können die neue **[!UICONTROL Code Quantity Limit]** Konfigurationsoption (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**), um zu verhindern, dass das System mit vielen Coupons überlastet wird. <!-- AC-8753 -->

* **Optimierung des standardmäßigen Prozesses zur URL-Erstellung für Administratoren**. Die Generierung der Standard-Admin-URL ist für eine erhöhte Zufälligkeit optimiert, wodurch generierte URLs weniger vorhersagbar werden. <!-- AC-9028 -->

* **Unterstützung für Subresource Integrity (SRI) hinzugefügt** zur Erfüllung der PCI 4.0-Anforderungen für die Überprüfung der Skriptintegrität auf Zahlungsseiten. Die Unterstützung von Subresource Integrity (SRI) bietet Integrations-Hashes für alle JavaScript-Assets, die sich im lokalen Dateisystem befinden. Die standardmäßige SRI-Funktion wird nur auf den Zahlungsseiten für die Admin- und Storefront-Bereiche implementiert. Händler können die Standardkonfiguration jedoch auf andere Seiten erweitern. Siehe [Subresource Integrity](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) im _Commerce PHP-Entwicklerhandbuch_.<!--AC-1153-->

* **Änderungen an der Content Security Policy (CSP)**—Aktualisierungen und Verbesserungen der Konfiguration von Adobe Commerce Content Security Policies (CSPs) zur Erfüllung von PCI 4.0-Anforderungen. Weitere Informationen finden Sie unter [Inhaltssicherheitsrichtlinien](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) im _Commerce PHP-Entwicklerhandbuch_. <!--AC-11513-->

   * Die standardmäßige CSP-Konfiguration für Zahlungsseiten für Commerce Admin- und Storefront-Bereiche ist jetzt `restrict` -Modus. Für alle anderen Seiten lautet die Standardkonfiguration `report-only` -Modus.  In Versionen vor 2.4.7 wurde CSP in `report-only` -Modus für alle Seiten.

   * Es wurde ein Nonce-Anbieter hinzugefügt, um die Ausführung von Inline-Skripten in einer CSP zu ermöglichen. Der Nonce-Provider erleichtert die Generierung eindeutiger Nonce-Zeichenfolgen für jede Anfrage. Die Zeichenfolgen werden dann an die CSP-Kopfzeile angehängt.

   * Es wurden Optionen hinzugefügt, mit denen benutzerdefinierte URIs konfiguriert werden können, um CSP-Verstöße für die Seite &quot;Auftrag erstellen&quot;in der Admin- und die Seite &quot;Auschecken&quot;im Storefront zu melden. Sie können die Konfiguration vom Administrator hinzufügen oder den URI zum `config.xml` -Datei.

     >[!NOTE]
     >
     >Aktualisieren der CSP-Konfiguration auf `restrict` -Modus kann vorhandene Inline-Skripte auf Zahlungsseiten in der Admin- und Storefront blockieren, was beim Laden einer Seite den folgenden Browserfehler verursacht: `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. Beheben Sie diese Fehler, indem Sie die Konfiguration der Whitelist so aktualisieren, dass erforderliche Skripte zugelassen werden. Siehe [Fehlerbehebung](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) im _Commerce PHP-Entwicklerhandbuch_.

* Eine neue Einstellung für die vollständige Cache-Konfiguration kann dazu beitragen, die mit dem HTTP verbundenen Risiken zu verringern `{BASE-URL}/page_cache/block/esi` -Endpunkt. Dieser Endpunkt unterstützt nicht eingeschränkte, dynamisch geladene Inhaltsfragmente aus Commerce-Layout-Handles und -Blockstrukturen. Die neue **[!UICONTROL Handles params size]** -Konfigurationseinstellung legt den Wert des `handles` -Parameter, der die maximal zulässige Anzahl von Handles pro API bestimmt. Der Standardwert dieser Eigenschaft ist 100. Händler können diesen Wert über Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles params size]**). Siehe [Konfigurieren der Commerce-Anwendung für die Verwendung von Varnish](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/configure-varnish-commerce.html). <!-- AC-9113 -->

* **Nativer Ratenbegrenzung für Zahlungsinformationen, die über REST- und GraphQL-APIs übermittelt werden**. Händler können jetzt [Ratenbegrenzung konfigurieren](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/sales#rate-limiting) für die Zahlungsinformationen, die über REST und GraphQL übermittelt werden. Diese zusätzliche Schutzschicht unterstützt die Vermeidung von Kartenangriffen und verringert möglicherweise das Volumen von Kartenangriffen, bei denen viele Kreditkartennummern gleichzeitig getestet werden. Dies ist eine Änderung des Standardverhaltens eines vorhandenen REST-Endpunkts. Siehe [Begrenzung](https://developer.adobe.com/commerce/webapi/get-started/rate-limiting/).

* Das Standardverhalten der [isEmailAvailable](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL-Abfrage und die ([V1/Customers/isEmailAvailable](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) Der REST-Endpunkt wurde geändert. Standardmäßig geben die APIs jetzt immer `true`. Merchants können das ursprüngliche Verhalten aktivieren, indem Sie die *[Gastauscheckabmeldung aktivieren](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/checkout)* -Option in Admin zu `yes`können jedoch nicht authentifizierte Benutzer mit Kundeninformationen versorgen.
