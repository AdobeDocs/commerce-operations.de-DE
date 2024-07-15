---
title: Cache-Vergiftung verhindern
description: Erfahren Sie, wie Sie eine Vergiftung des Seiten-Cache für Ihre Commerce-Storefront verhindern können.
feature: Configuration, Cache, Security
exl-id: 947024dd-d59d-480d-bb6c-8e0065054bb6
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Cache-Vergiftung verhindern

In diesem Thema wird erläutert, wie Sie eine Cache-Vergiftung verhindern können, wenn Sie den Microsoft Internet Information Server (IIS)-Webserver verwenden. _Cache-Vergiftung_ ist eine Methode zum Ändern des Cache-Inhalts, um verschiedene Seiten von derselben Site einzuschließen. Beispielsweise ist es möglich, anstelle einer gutartigen Seite (z. B. der Storefront-Startseite) eine HTTP 404 (Not Found)-Fehlerseite einzufügen, was zu einer potenziellen DoS (Denial-of-Service) führen kann. Die bösartigen Seiten-URLs werden von Varnish oder Redis zwischengespeichert. Daher wird der Name _Seiten-Cache-Vergiftung_ verwendet.

Diese Arten von Angriffen können schwierig zu erkennen sein, da sie nicht zu Fehlern in Webserver-Protokollen führen.

Diese Lösung gilt für die folgenden Commerce-Versionen:

- 2.0.10 und höher
- 2.1.2 und höher

>[!INFO]
>
>Dieses Thema ist für erfahrene IIS-Administratoren gedacht.

## Beschreibung

Das Problem tritt auf, wenn URL-Neuschreibungen auf dem IIS-Server aktiviert sind und eine der folgenden HTTP-Header geändert wird, bevor die Anforderung den Varnish- oder Redis-Caching-Dienst erreicht:

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

Wenn diese Header geändert werden, werden die resultierende URL und der Inhalt zwischengespeichert, was zu potenziellen Sicherheitslücken führt.

## Lösung

Wir bieten die Option, die Werte aller vorhergehenden Header basierend auf der IIS-Servereinstellung für `Enable_IIS_Rewrites` zu entfernen.

- Wenn `Enable_IIS_Rewrites` auf `0` gesetzt ist, werden die Werte der Kopfzeilen entfernt.
- Wenn `Enable_IIS_Rewrites` auf `1` gesetzt ist, bleiben die Werte der Kopfzeilen unverändert.

>[!WARNING]
>
>Wenn Sie `Enable_IIS_Rewrites` auf `1` setzen, dürfen Sie nicht zulassen, dass die Werte der vorhergehenden Header geändert werden, bevor die Anforderung den IIS-Webserver erreicht.
