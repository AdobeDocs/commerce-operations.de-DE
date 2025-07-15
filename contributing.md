---
source-git-commit: 4dd926ca7014c9e007a8c2c847e076064eb8d170
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 1%

---
# Beiträge

Vielen Dank, dass Sie sich für einen Beitrag entschieden haben!

Im Folgenden finden Sie eine Reihe von Richtlinien, die beim Mitwirken an diesem Projekt befolgt werden müssen.

## Verhaltenskodex

Dieses Projekt unterliegt dem [Verhaltenskodex](code-of-conduct.md) von Adobe. Durch die Teilnahme
Von Ihnen wird erwartet, dass Sie diesen Kodex einhalten. Bitte melden Sie inakzeptables Verhalten an
[Grp-opensourceoffice@adobe.com](mailto:Grp-opensourceoffice@adobe.com).

## Dokumentation zum Contributor Guide

Siehe das [Handbuch für Mitwirkende](https://experienceleague.adobe.com/de/docs/contributor/contributor-guide/introduction).

## Haben Sie eine Frage?

Melden Sie zunächst ein Problem. Die vorhandenen Verantwortlichen für dieses Projekt arbeiten daran, Folgendes zu erreichen
Konsens über die Projektausrichtung und Problemlösungen in Problem-Threads
(falls zutreffend)

## Lizenzvereinbarung für Mitarbeiter

Alle Drittanbieter-Beiträge zu diesem Projekt müssen von einem unterzeichneten Mitwirkenden begleitet werden
Lizenzvereinbarung. Dadurch erhält Adobe die Berechtigung, Ihre Beiträge zu verteilen
als Teil des Projekts. [Unterschreiben Sie unsere Lizenzvereinbarung für Mitwirkende](https://opensource.adobe.com/cla.html). Sie
Sie müssen nur einmal eine Adobe-Lizenzvereinbarung für Mitwirkende übermitteln. Wenn Sie also bereits eine gesendet haben,
Du bist gut zu gehen!

## Code-Überprüfungen

Alle Einreichungen sollten in Form von Pull-Anfragen erfolgen und müssen überprüft werden
durch Projektverantwortliche. Lesen [ Dokumentation zu Pull Requests von GitHub](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)
Weitere Informationen zum Senden von Pull-Anforderungen finden Sie unter.

<!--
Lastly, please follow the [pull request template](PULL_REQUEST_TEMPLATE.md) when
submitting a pull request!
-->

## Von den Mitwirkenden zu den Verantwortlichen

Wir lieben Beiträge von unserer Community! Wenn Sie einen Schritt über die Rolle als Mitwirkender hinausgehen möchten
Und um ein Verantwortlicher mit uneingeschränktem Schreibzugriff und Mitsprache am Projekt zu werden, müssen Sie
Sie werden zum Projekt eingeladen. Die vorhandenen Verantwortlichen verwenden eine interne Nominierung
Prozess, der vor Einladungen einen Konsens erreichen muss (Schweigen bedeutet Zustimmung)
werden ausgegeben. Wenn Sie glauben, dass Sie qualifiziert sind und stärker involviert werden möchten,
Wenden Sie sich an bestehende Verantwortliche, um darüber zu sprechen.

## Sicherheitsprobleme

Sicherheitsprobleme sollten nicht in dieser Problemverfolgung gemeldet werden. Stattdessen [ein Problem an unsere Sicherheitsexperten ](https://helpx.adobe.com/de/security/alertus.html).

## Neue Highlights

Wenn Ihre Änderungen neue Themen, wichtige Aktualisierungen oder Korrekturen mit sich bringen, die hervorgehoben werden müssen, können Sie direkt im Hauptteil Ihrer Pull[Anfrage eine kurze Beschreibung ](https://experienceleague.adobe.com/de/docs/commerce-operations/operational-guides/home#whats-new) Abschnitt „Neue Funktionen“ hinzufügen.

So fügen Sie eine Hervorhebung Neue Funktionen hinzu:

1. Fügen Sie das `whatsnew`-Tag mit der entsprechenden Beschreibung am Ende in den Textkörper Ihrer Pull-Anfrage ein. Die Beschreibung sollte Kontext über die Änderung und einen Link zum Zielthema oder zu den Zielthemen enthalten. Verwenden Sie das folgende Format (Code-Blockanführungszeichen dienen nur der Darstellung, schließen Sie sie nicht in Ihren Pull-Anfragetext ein):

   ```text
   whatsnew
   Short description of the change in the [target topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/target-topic.html).
   ```

   Oder wenn es mehrere Themen gibt:

   ```text
   whatsnew
   Short description of the changes in the [first target topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/target-topic.html), [second target topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/second-target-topic.html), and [third target topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/third-target-topic.html).
   ```

   Sie können auch Listen für mehrere Highlights verwenden:

   ```text
   whatsnew
   - Short description of the first change in the [first topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/first-topic.html).
   - Short description of the second change in the [second topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/second-topic.html).
   ```

   ```text
   whatsnew
   The following changes were made to the documentation:
   - Short description of the first change in the [first topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/first-topic.html).
   - Short description of the second change in the [second topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/second-topic.html).
   ```

1. Fügen Sie unterstützte Beschriftungen hinzu, die den Typ der Änderung angeben. Unterstützte Kennzeichnungen enthalten Kennzeichnungen für jeden Änderungstyp, z. B.:

   - `new-topic` - für neue Themen
   - `major-update` - Für umfangreiche Aktualisierungen, die erhebliche Änderungen an Inhalt, Struktur oder Funktionalität enthalten können
   - `technical` - für technische Änderungen, die nicht als wichtige Updates gelten, aber dennoch beachtet werden müssen

   und optional Beschriftungen für den Änderungsbereich, z. B.:

   - `qpt` - für Änderungen im Zusammenhang mit dem Quality Patch-Tool

**Wichtig:**

1. Der `whatsnew` Teil muss vom `whatsnew`-Tag beginnen und sich ganz am Ende des Pull-Anfragetexts befinden.
1. Die Beschreibungen der Änderungen müssen funktionierende Links enthalten. Bitte vergewissern Sie sich, dass die Links korrekt sind und zu den gewünschten Themen führen. Wenn das Thema neu ist, überprüfen Sie, ob die Links funktionieren, nachdem Sie die Pull-Anfrage zusammengeführt und das neue Thema veröffentlicht haben. Es ist in Ordnung, die Links zu beheben, nachdem die Pull-Anfrage zusammengeführt wurde.

Suchen Sie beispielsweise in geschlossenen Pull-Anfragen im Repository, um zu sehen, wie vorhandene Highlights formatiert sind, und vergleichen Sie sie mit dem Abschnitt [Neue Funktionen](https://experienceleague.adobe.com/de/docs/commerce-operations/operational-guides/home#whats-new), um zu sehen, wie sie in der Dokumentation angezeigt werden.
