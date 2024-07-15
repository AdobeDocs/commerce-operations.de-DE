---
source-git-commit: 4ed23e2a8319ff97f8206f752cf1cbe2e73ea5c5
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---
# 2.4.7 Sicherheitsverbesserungen

* **Subresource Integrity (SRI)-Unterstützung** wurde hinzugefügt, um PCI 4.0-Anforderungen für die Überprüfung der Skriptintegrität auf Zahlungsseiten zu erfüllen. Die Unterstützung von Subresource Integrity (SRI) bietet Integrations-Hashes für alle JavaScript-Assets, die sich im lokalen Dateisystem befinden. Die standardmäßige SRI-Funktion wird nur auf den Zahlungsseiten für die Admin- und Storefront-Bereiche implementiert. Händler können die Standardkonfiguration jedoch auf andere Seiten erweitern. Siehe [Subresource Integrity](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) im _Commerce PHP Developer Guide_.<!--AC-1153-->

* **Änderungen an der Content Security Policy (CSP)** - Konfigurationsaktualisierungen und -verbesserungen für Adobe Commerce Content Security Policies (CSPs), um die Anforderungen von PCI 4.0 zu erfüllen. Weitere Informationen finden Sie unter [Inhaltssicherheitsrichtlinien](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) im _Commerce PHP Developer Guide_. <!--AC-11513-->

   * Die standardmäßige CSP-Konfiguration für Zahlungsseiten für Commerce-Admin- und Storefront-Bereiche ist jetzt `restrict` -Modus. Für alle anderen Seiten ist die Standardkonfiguration der Modus &quot;`report-only`&quot;.  In Versionen vor 2.4.7 wurde CSP für alle Seiten im `report-only` -Modus konfiguriert.

   * Es wurde ein Nonce-Anbieter hinzugefügt, um die Ausführung von Inline-Skripten in einer CSP zu ermöglichen. Der Nonce-Provider erleichtert die Generierung eindeutiger Nonce-Zeichenfolgen für jede Anfrage. Die Zeichenfolgen werden dann an die CSP-Kopfzeile angehängt.

   * Es wurden Optionen hinzugefügt, mit denen benutzerdefinierte URIs konfiguriert werden können, um CSP-Verstöße für die Seite &quot;Auftrag erstellen&quot;in der Admin- und die Seite &quot;Auschecken&quot;im Storefront zu melden. Sie können die Konfiguration vom Administrator hinzufügen oder den URI zur Datei `config.xml` hinzufügen.

     >[!NOTE]
     >
     >Die Aktualisierung der CSP-Konfiguration auf den Modus &quot;`restrict`&quot;kann vorhandene Inline-Skripte auf Zahlungsseiten in Admin und Storefront blockieren, was beim Laden einer Seite den folgenden Browserfehler verursacht: `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. Beheben Sie diese Fehler, indem Sie die Konfiguration der Whitelist so aktualisieren, dass erforderliche Skripte zugelassen werden. Siehe [Fehlerbehebung](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) im _Commerce PHP Developer Guide_.
