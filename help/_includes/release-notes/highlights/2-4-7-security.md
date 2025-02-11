---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---
# 2.4.7 Sicherheitsverbesserungen

* **Unterstützung für Subresource Integrity (SRI) wurde hinzugefügt** um die PCI 4.0-Anforderungen für die Überprüfung der Skriptintegrität auf Zahlungsseiten zu erfüllen. Die Unterstützung von Subresource Integrity (SRI) bietet Integritäts-Hashes für alle JavaScript-Assets im lokalen Dateisystem. Die standardmäßige SRI-Funktion wird nur auf den Zahlungsseiten für die Bereiche Admin und Storefront implementiert. Händler können die Standardkonfiguration jedoch auf andere Seiten erweitern. Siehe [Subresource-Integrität](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) im _Commerce PHP-Entwicklerhandbuch_.<!--AC-1153-->

* **Änderungen an der Content Security Policy (CSP)** - Konfigurationsaktualisierungen und -verbesserungen an den Adobe Commerce Content Security Policies (CSPs) zur Erfüllung der PCI 4.0-Anforderungen. Weitere Informationen finden Sie unter [Inhaltssicherheitsrichtlinien](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) im _Commerce PHP-_<!--AC-11513-->

   * Die standardmäßige CSP-Konfiguration für Zahlungsseiten für Commerce Admin- und Storefront-Bereiche ist jetzt `restrict`. Für alle anderen Seiten ist die Standardkonfiguration `report-only`.  In Versionen vor 2.4.7 wurde CSP für alle Seiten im `report-only` konfiguriert.

   * Es wurde ein Nonce-Provider hinzugefügt, der die Ausführung von Inline-Skripten in einer CSP ermöglicht. Der Nonce-Anbieter erleichtert die Erstellung eindeutiger Nonce-Zeichenfolgen für jede Anfrage. Die Zeichenfolgen werden dann an den CSP-Header angehängt.

   * Es wurden Optionen zum Konfigurieren von benutzerdefinierten URIs hinzugefügt, um CSP-Verletzungen für die Seite „Auftrag erstellen“ in der Admin- und die Checkout-Seite im Storefront zu melden. Sie können die Konfiguration über den Administrator oder durch Hinzufügen des URI zur `config.xml`-Datei hinzufügen.

     >[!NOTE]
     >
     >Wenn Sie die CSP-Konfiguration auf den `restrict`-Modus aktualisieren, werden möglicherweise vorhandene Inline-Skripte auf Zahlungsseiten in der Admin- und Storefront blockiert, was beim Laden einer Seite den folgenden Browser-Fehler verursacht: `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. Beheben Sie diese Fehler, indem Sie die Konfiguration der Zulassungsliste aktualisieren, um die erforderlichen Skripte zuzulassen. Siehe [Fehlerbehebung](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) im _Commerce PHP-_.
