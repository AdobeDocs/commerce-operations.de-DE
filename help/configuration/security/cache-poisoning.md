---
title: Cache-Vergiftung verhindern
description: Erfahren Sie, wie Sie eine Vergiftung des Seiten-Caches für Ihre Commerce-Storefront verhindern.
feature: Configuration, Cache, Security
exl-id: 947024dd-d59d-480d-bb6c-8e0065054bb6
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
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
