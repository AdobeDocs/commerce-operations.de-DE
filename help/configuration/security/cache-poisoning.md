---
title: Cache-Vergiftung verhindern
description: Erfahren Sie, wie Sie eine Vergiftung des Seiten-Cache für Ihre Commerce-Storefront verhindern können.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---


# Cache-Vergiftung verhindern

In diesem Thema wird erläutert, wie Sie eine Cache-Vergiftung verhindern können, wenn Sie den Microsoft Internet Information Server (IIS)-Webserver verwenden. _Cache-Vergiftung_ ist eine Methode zum Ändern des Cache-Inhalts, um verschiedene Seiten von derselben Site einzuschließen. Beispielsweise ist es möglich, anstelle einer gutartigen Seite (z. B. der Storefront-Startseite) eine HTTP 404 (Not Found)-Fehlerseite einzufügen, was zu einer potenziellen DoS (Denial-of-Service) führen kann. Die bösartigen Seiten-URLs werden von Varnish oder Redis zwischengespeichert, daher der Name _Seitencache-Vergiftung_.

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

Wir bieten die Option, die Werte aller vorhergehenden Header basierend auf der IIS-Servereinstellung für zu entfernen. `Enable_IIS_Rewrites`.

- Wenn `Enable_IIS_Rewrites` auf `0`, werden die Werte der Header entfernt.
- Wenn `Enable_IIS_Rewrites` auf `1`festgelegt ist, bleiben die Werte der Kopfzeilen intakt.

>[!WARNING]
>
>Wenn Sie `Enable_IIS_Rewrites` nach `1`dürfen Sie nicht zulassen, dass die Werte der vorhergehenden Header geändert werden, bevor die Anfrage den IIS-Webserver erreicht.
