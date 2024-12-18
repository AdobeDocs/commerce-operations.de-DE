---
title: Cache-Vergiftung verhindern
description: Erfahren Sie, wie Sie eine Vergiftung des Seiten-Caches für Ihre Commerce-Storefront verhindern.
feature: Configuration, Cache, Security
exl-id: 947024dd-d59d-480d-bb6c-8e0065054bb6
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Cache-Vergiftung verhindern

In diesem Abschnitt wird beschrieben, wie Sie eine Cache-Vergiftung verhindern, wenn Sie den Microsoft Internet Information Server (IIS)-Webserver verwenden. _Cache-Vergiftung_ ist eine Methode zum Ändern des Cache-Inhalts, um verschiedene Seiten von derselben Site einzuschließen. Beispielsweise ist es möglich, eine HTTP 404-Fehlerseite (Nicht gefunden) anstelle einer gutartigen Seite (z. B. der Storefront-Startseite) einzufügen, was zu einem potenziellen Denial-of-Service (DoS) führen kann. Die bösartigen Seiten-URLs werden von Varnish oder Redis zwischengespeichert, daher der Name _Seitencache-Vergiftung_.

Diese Arten von Angriffen können schwer zu erkennen sein, da sie nicht zu Fehlern in Webserver-Protokollen führen.

Diese Lösung gilt für die folgenden Commerce-Versionen:

- 2.0.10 und höher
- 2.1.2 und höher

>[!INFO]
>
>Dieses Thema richtet sich an erfahrene IIS-Administratoren.

## Beschreibung

Das Problem tritt auf, wenn URL-Neuschreibungen auf dem IIS-Server aktiviert sind und eine der folgenden HTTP-Kopfzeilen geändert wird, bevor die Anfrage den Varnish- oder Redis-Caching-Service erreicht:

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

Wenn diese Header geändert werden, werden die resultierende URL und der Inhalt zwischengespeichert, was zu potenziellen Sicherheitslücken führt.

## Lösung

Wir bieten die Möglichkeit, die Werte aller vorangehenden Kopfzeilen basierend auf der IIS-Servereinstellung für `Enable_IIS_Rewrites` zu entfernen.

- Wenn `Enable_IIS_Rewrites` auf `0` gesetzt ist, werden die Werte der -Kopfzeilen entfernt.
- Wenn `Enable_IIS_Rewrites` auf `1` gesetzt ist, bleiben die Werte der -Kopfzeilen intakt.

>[!WARNING]
>
>Wenn Sie `Enable_IIS_Rewrites` auf `1` setzen, dürfen Sie nicht zulassen, dass die Werte der vorangehenden Header geändert werden, bevor die Anforderung den IIS-Webserver erreicht.
