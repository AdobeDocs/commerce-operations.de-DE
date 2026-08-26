---
title: Handbuch zur Fehlerbehebung [!DNL Adobe Commerce Patching Automation]
description: Beheben häufiger Probleme und Fehlermeldungen in [!DNL Adobe Commerce Patching Automation]
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '1710'
ht-degree: 0%

---

# Handbuch zur Fehlerbehebung [!DNL Adobe Commerce Patching Automation]

Wenn Sie [!DNL Patching Automation] für Patch-Vorgänge verwenden, können Fehlermeldungen und Probleme auftreten, die eine erfolgreiche Patch-Anwendung oder eine Rückgängigmachung verhindern können. Dieses Handbuch bietet Lösungen für die häufigsten Probleme.

## Schritte zur schnellen Fehlerbehebung

### Wenn der Patch-Vorgang fehlschlägt

* Überprüfen Sie den Betriebsstatus, um zu verstehen, welche Phase fehlgeschlagen ist
* Überprüfen von Fehlermeldungen auf bestimmte Fehlerursachen
* Technische Details in den Fehlerprotokollen
* Befolgen Sie die in diesem Handbuch bereitgestellten Lösungen

>[!TIP]
>
>In der Cloud-Konsole sind Bereitstellungsprotokolle im Aktivitäts-Feed Ihres Projekts verfügbar - auch nachdem eine temporäre Integrationsumgebung gelöscht wurde.

### Dauer von Patch-Vorgängen

Für die meisten Umgebungen wird in der folgenden Zeitleiste beschrieben, wie lange Patch-Vorgänge dauern sollten. Je nach Größe und Komplexität der Umgebung kann dies jedoch länger dauern:

* **Vorab-Bearbeitung:** 2-5 Minuten
* **Patchen:** 5-15 Minuten
* **Nachbearbeitung:** 10-40 Minuten
* **Gesamt:** 15-60 Minuten

>[!NOTE]
>
>Die Nachbearbeitungszeit wird aus dem Bereitstellungsverlauf Ihrer Umgebung geschätzt, sodass sie bei ungewöhnlich schnell oder langsam bereitstellenden Umgebungen außerhalb des oben genannten Bereichs liegen kann.

### Abbrechen eines laufenden Patches

>[!WARNING]
>
>Sobald ein Patch-Vorgang beginnt, sollte er abgeschlossen sein. Das System umfasst Bereinigungsverfahren, die auch bei fehlgeschlagenen Vorgängen ausgeführt werden. Wenn Sie den Prozess unterbrechen, kann sich Ihre Umgebung in einem inkonsistenten Zustand befinden.

## Häufige Erfolgsmeldungen

* **„Auftrag erfolgreich abgeschlossen“** - Der Patch wurde ohne Probleme erfolgreich angewendet/zurückgesetzt.

* **„Patch wurde angewendet“** - Sie versuchen, einen Patch anzuwenden, der bereits angewendet wurde. Das System hat erkannt, dass der Patch bereits in Ihrer Umgebung vorhanden ist. Es sind keine Maßnahmen erforderlich.

* **„Patch wurde zurückgesetzt“** - Sie versuchen, einen Patch rückgängig zu machen, der bereits rückgängig gemacht wurde. Das System hat erkannt, dass der Patch derzeit nicht angewendet wird. Es sind keine Maßnahmen erforderlich.

## Häufige Fehlermeldungen und Lösungen

>[!NOTE]
>
>Unten finden Sie nicht alle möglichen Fehler. Ein nicht aufgeführter Fehler während der Vorprüfung wird als allgemeiner „Fehler während der Vorprüfung“ angezeigt; ein nicht aufgeführter Fehler während der Validierung wird als allgemeiner „Fehler während der Nachbearbeitung“ angezeigt - wenden Sie sich in beiden Fällen mit dem genauen Fehlertext an den Support. Beim Patchen wird bei einem unerwarteten Fehler die zugrunde liegende rohe Fehlermeldung direkt anstelle eines allgemeinen Fallbacks angezeigt.

### Fehler bei der Umgebungsbereitschaft

#### „Die letzte Bereitstellung war nicht erfolgreich. Bitte stellen Sie sicher, dass die Umgebung stabil ist, bevor Sie Patches anwenden oder zurücksetzen.“

**Wenn er auftritt:** Zu Beginn der Vorprüfung, vor jeder Patch-spezifischen Validierung

**Ursache:** Die letzte Bereitstellung Ihrer Zielumgebung wurde nicht erfolgreich abgeschlossen

**Lösung:** Stellen Sie Ihre Zielumgebung erneut bereit und bestätigen Sie, dass die Bereitstellung erfolgreich abgeschlossen wurde (überprüfen Sie das Bereitstellungsprotokoll in der Cloud-Konsole), bevor Sie den Patch-Vorgang wiederholen.

### Patchen von Anwendungsfehlern

#### „Der Patch kann nicht angewendet werden, da [!DNL Patching Automation] diese Probleme mit Ihrer Codebasis oder der Patch-Datei erkannt hat.“

**Wenn er auftritt:** Während der Vorprüfung

**Ursache:** Der Patch steht in Konflikt mit Ihrer aktuellen Codebasis ODER es gibt ein Problem mit dem Patch selbst

**Lösungen:**

* Überprüfen Sie die bereitgestellten detaillierten Fehlerprotokolle, um festzustellen, ob es sich um eine Code-Basis oder ein Patch-Problem handelt
* Überprüfen auf widersprüchliche Anpassungen im Code
* Überprüfen Sie, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist.
* Erwägen Sie, Konflikte manuell zu lösen, oder wenden Sie sich an den Support

#### „Sie versuchen, einen Patch rückgängig zu machen, der nicht über [!DNL Patching Automation] angewendet wurde. Wahrscheinlich wurde das Patch manuell angewendet.“

**Wenn er auftritt:** Während des Wiederherstellungsvorgangs

**Ursache:** Sie versuchen, einen Patch rückgängig zu machen, der nicht über [!DNL Patching Automation] angewendet wurde

**Lösung:** Verwenden Sie dieselbe Methode, die ursprünglich zum Anwenden des Patches verwendet wurde, oder wenden Sie sich an den Support, um Hilfe zu erhalten

### Umgebung und Validierungsfehler

#### „Umgebung ist nicht mit übergeordneter Umgebung synchronisiert“

**Wenn dies eintritt:** Während der Validierung, in der Prüfung vor der Zusammenführung - vor der Zusammenführung der Integrationsumgebung in Ihrer Zielumgebung

**Ursache:** Ihre Integrationsumgebung unterscheidet sich von der übergeordneten Umgebung, in der Regel deshalb, weil die Zielumgebung während des Patches geändert wurde

**Lösungen:**

* Wiederholen Sie den Patch-Vorgang, sobald die Zielumgebung stabil ist
* Vermeiden Sie Änderungen an der Zielumgebung, während ein Patch-Vorgang ausgeführt wird
* Wenden Sie sich an den Support, wenn Synchronisierungsprobleme weiterhin bestehen

#### „Die Verifizierung nach der Zusammenführung ist fehlgeschlagen: Umgebungen sind nach der Zusammenführung nicht synchronisiert.“

**Wenn dies auftritt:** Während der Validierung, nachdem die Integrationsumgebung bereits in Ihrer Zielumgebung zusammengeführt wurde

**Ursache:** Der Code im Code der beiden Umgebungen stimmt nach dem Zusammenführen nicht überein, normalerweise eine temporäre Platform.sh-API-Übertragungsverzögerung anstelle eines echten Konflikts

**Lösungen:**

* Warten Sie einige Minuten und überprüfen Sie erneut den Umgebungsstatus. Dieses Problem wird häufig von selbst behoben
* Wenn die Umgebungen nach einigen Minuten immer noch nicht übereinstimmen, wenden Sie sich an den Adobe-Support.

#### „Patch-Auftrag kann nicht in der Produktionsumgebung erstellt werden, wenn Cron aktiviert und der Wartungsmodus deaktiviert ist. Bitte aktivieren Sie den Wartungsmodus und deaktivieren Sie Cron-Aufträge, bevor Sie Patches anwenden.“

**Wenn es auftritt:** Während der Vorprüfung für Produktionsumgebungen

**Ursache:** Die Produktionsumgebung erfüllt nicht die erforderlichen Sicherheitsbedingungen

**Lösungen:**

* Aktivieren des Wartungsmodus für den Produktionsspeicher
* Deaktivieren von Cron-Aufträgen in der Produktionsumgebung
* Überprüfen Sie, ob beide Bedingungen erfüllt sind, bevor Sie es erneut versuchen
* Alternativ können Sie in der Benutzeroberfläche das Kontrollkästchen „Überschreiben“ aktivieren, um diese Prüfungen zu überspringen und trotzdem fortzufahren. Verwenden Sie die Option „Überschreiben“ nur, wenn Sie das Risiko des Patchens der Produktion ohne diese Sicherheitsmaßnahmen verstehen

>[!IMPORTANT]
>
> [!DNL Patching Automation] aktiviert nicht automatisch den Wartungsmodus oder deaktiviert Cron-Aufträge - diese müssen extern von Ihnen erledigt werden

#### „Der Patch-Vorgang wurde abgeschlossen, aber die Konsistenzprüfung der Umgebung ist fehlgeschlagen. Dies weist auf potenzielle Probleme bei der Bereitstellung hin. Bitte den Umgebungsstatus überprüfen und erwägen, die Änderung rückgängig zu machen.“

**Wenn dies auftritt:** Nach der Patch-Anwendung oder Rückwärtsentwicklung, während der Validierung

**Ursache:** Der Patch wurde erfolgreich angewendet oder zurückgesetzt, aber die nachfolgende Konsistenzprüfung ist fehlgeschlagen

**Lösungen:**

* Testen Sie die Storefront und kritische Checkout- und Admin-Workflows, um zu überprüfen, ob Kunden tatsächlich betroffen sind
* Überprüfen Sie in der Cloud-Konsole den Umgebungsstatus und die Anwendungs- und Bereitstellungsprotokolle im Projekt-(**)** Feed. Suchen Sie nach Fehlern im Zusammenhang mit Patch-Vorgängen oder der Bereitstellung.
* Trigger : Manuelle erneute Bereitstellung, um festzustellen, ob der Fehler bei der Konsistenzprüfung durch eine vorübergehende Bereitstellung oder ein Infrastrukturproblem verursacht wurde.
* Wenn das Problem weiterhin besteht, stellen Sie das Patch wieder her. Wenn der Patch von [!DNL Patching Automation] verwaltet wird und der Vorgang verfügbar ist, wählen Sie [!UICONTROL Revert] aus. Wenn es sich bei dem Patch um einen benutzerdefinierten Patch im `m2-hotfixes` handelt, löschen Sie die Patch-Datei aus dem Projekt-Repository. Bestätigen Sie die Änderung, übertragen Sie sie und stellen Sie sie dann erneut bereit.
* Wenn das Problem weiterhin besteht, wenden Sie sich an den Adobe-Support. Fügen Sie in Ihre Support-Anfrage die folgenden Informationen ein: Support-Projekt-ID, Umgebungs-ID und genau diese Nachricht: Der letzte Vorgang wurde nicht sauber abgeschlossen, sodass der Support den Status der Umgebung möglicherweise bestätigen muss.

### Authentifizierungs- und Zugriffsfehler

#### „Zugriff verweigert“

**Wenn dies auftritt:** Wenn Ihrem Konto während der Erstellung oder des Zugriffs auf die Umgebung die erforderlichen Berechtigungen fehlen

**Ursache:** Ihrem Benutzerkonto fehlen die erforderlichen Berechtigungen

**Lösungen:**

* Benutzerrolle und Berechtigungen überprüfen
* Wenden Sie sich an Ihren Systemadministrator
* Vergewissern Sie sich, dass Sie über Berechtigungen zur Umgebungsverwaltung verfügen
* Stellen Sie sicher, dass Sie über Bereitstellungsberechtigungen verfügen

### GitHub-Integrationsfehler

#### „Keine Git-Anmeldeinformationen für Anbieter „GitHub“ verfügbar. Installieren Sie die GitHub-App zur Patch-Automatisierung für dieses Repository.“

**Wenn dies auftritt:** Während Patch-Vorgängen für Projekte, die mit GitHub verbunden sind

**Ursache:** Die [!DNL Patching Automation] GitHub-App ist nicht in Ihrem Repository installiert

**Lösung:** Führen Sie die Schritte unter [Einrichten der GitHub-Integration für [!DNL Patching Automation]](github-integration.md) aus

#### „GitHub-API-Anfrage fehlgeschlagen“

**Wenn dies auftritt:** Während Patch-Vorgängen für mit GitHub verbundene Projekte

**Ursache:** Ein temporäres Problem hat verhindert, dass der Service eine Verbindung zu GitHub herstellt

**Lösung:** Warten Sie einige Minuten und wiederholen Sie den Vorgang. Wenn der Fehler weiterhin auftritt, wenden Sie sich an den [Adobe Commerce Cloud-Support](https://experienceleague.adobe.com/home#support)

#### „Umgebung wurde nicht innerhalb der maximalen Wartezeit erstellt“ (mit GitHub verbundenes Projekt)

**Wenn er auftritt:** Während der Erstellung der Integrationsumgebung

**Ursache:** Die `fetch-branches` Option ist für die GitHub-Integration des Projekts deaktiviert. Daher werden die vom Service übertragenen temporären Verzweigungen nicht synchronisiert, und die Integrationsumgebung wird nie erstellt.

**Lösung:** Aktivieren Sie die Option [`fetch-branches` der Integration](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration) und wiederholen Sie dann den Vorgang. Siehe [Einrichten der GitHub-Integration für [!DNL Patching Automation]](github-integration.md).

### Fehler bei der Umgebungsaktivierung

#### „Integrationsumgebung kann nicht aktiviert werden.“

**Wenn er auftritt:** Wenn [!DNL Patching Automation] die temporäre Integrationsumgebung, die zum sicheren Testen des Patches erforderlich ist, nicht aktivieren können.

**Ursache:** Hängt von den zusätzlichen Details ab, die zusammen mit dem Fehler angezeigt werden:

**Wenn in den Details die Composer- oder Adobe Commerce-Pakete erwähnt werden:**

* Melden Sie sich bei [https://account.magento.com/](https://account.magento.com/) an (oder bitten Sie Ihren Kontoinhaber, dies zu tun) und bestätigen Sie, dass Ihr Konto Zugriff auf die Commerce Enterprise-Code-Basis hat.
* Überprüfen Sie, ob das Composer-Schlüsselpaar aus öffentlichem/privatem Schlüssel Ihres Projekts korrekt ist - siehe [Authentifizierungsschlüssel](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/authentication-keys).
* Melden Sie sich bei [https://account.magento.com/](https://account.magento.com/) an (oder bitten Sie Ihren Kontoinhaber, dies zu tun) und bestätigen Sie, dass Ihr Konto Zugriff auf die Commerce Enterprise-Code-Basis hat.
* Stellen Sie sicher, dass die öffentlichen und privaten Composer-Authentifizierungsschlüssel Ihres Projekts korrekt sind. Siehe [Authentifizierungsschlüssel](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/authentication-keys).
* Vergewissern Sie sich, dass das in der Fehlermeldung benannte Paket für Ihre Commerce-Version verfügbar ist. Siehe [Adobe Commerce-Pakete](https://experienceleague.adobe.com/en/docs/commerce-operations/release/packages/adobe-commerce).

**Wenn in den Details Umgebungssteckplätze oder Ressourcen erwähnt werden:**

* Öffnen Sie in der Cloud-Konsole die Projektübersicht und überprüfen Sie die Umgebungen und ihre Status. Nicht verwendete Integrationsumgebungen deaktivieren oder löschen: Wählen Sie die Umgebung aus. Navigieren Sie zu **[!UICONTROL Settings]>[!UICONTROL General]**. Setzen Sie den Umgebungsstatus auf Inaktiv.

  Alternativ können Sie die CLI verwenden: `magento-cloud environment:list` / `magento-cloud environment:deactivate <environment-name>`
* Stellen Sie sicher, dass Ihr Projekt über ausreichende Ressourcen verfügt, z. B. Speicherplatz.
* Stellen Sie sicher, dass die übergeordnete Umgebung zum Zeitpunkt des Vorgangs stabil ist (keine aktive Bereitstellung).
* Wenden Sie sich an den Adobe-Support, wenn Sie Ihr Umgebungslimit erhöhen müssen.

**Für jede andere Ursache:** Sie die detaillierten Fehlerprotokolle in der Benutzeroberfläche zur Patching-Automatisierung oder wenden Sie sich mit dem genauen Fehlertext an den Support.

## Hilfe wird abgerufen

**Kontaktaufnahme mit dem Support:**

Wenden Sie sich an den Adobe Commerce Cloud-Support, wenn:

* Fehlermeldungen sind unklar oder nicht detailliert genug
* Patch-Vorgänge schlagen durchgängig fehl
* Sie benötigen Hilfe bei der manuellen Konfliktbewältigung
* Konsistenzprüfungen schlagen fehl, aber die Ursache ist nicht ersichtlich
* Sie benötigen Hilfe bei Synchronisierungsproblemen mit der Umgebung

**Zu liefernde Informationen:**

Geben Sie bei der Kontaktaufnahme mit dem Support Folgendes an:

* **Projekt-ID** - Ihre Adobe Commerce Cloud-Projektkennung
* **Umgebungs-ID** - Die spezifische Umgebung, in der das Problem aufgetreten ist
* **Vorgangs-ID** - Die Kennung des [!DNL Patching Automation] Vorgangs
* **Fehlerdetails** - Vollständige Fehlermeldungen und -protokolle
* **Schritte zur Reproduktion** - Was Sie bei Auftreten des Fehlers getan haben
* **Frühere Versuche** - Was Sie bereits versucht haben, um das Problem zu beheben

### Zusätzliche Ressourcen

Ausführlichere technische Informationen:

* Überprüfen Sie die vollständigen Fehlerprotokolle zu fehlgeschlagenen Vorgängen
* Informationen zu patchspezifischen Anleitungen finden Sie in der Adobe Commerce-Dokumentation .
* Wenden Sie sich bei umgebungsspezifischen Problemen an den Adobe Commerce Cloud-Support

### Verwandte Themen

* [Dokumentation zu Adobe Commerce Cloud](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/overview)
* [Adobe Commerce-Installationshandbuch](/help/installation/overview.md)
* [Einführung in die Patch-Automatisierung](intro.md)
* [Zugriff](access.md)
* [Workflow-Übersicht](workflow.md)
* [GitHub-Integration](github-integration.md)
* [Best Practices](best-practices.md)
