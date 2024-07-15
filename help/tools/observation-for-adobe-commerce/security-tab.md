---
title: Registerkarte [!UICONTROL Security]
description: Erfahren Sie mehr über die Registerkarte [!UICONTROL Security] von  [!DNL Observation for Adobe Commerce].
exl-id: b567e4a4-534e-4151-b6f6-bf59b1bd4028
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Registerkarte [!UICONTROL Security]

Auf der Registerkarte **[!UICONTROL Security]** werden Sicherheitsprobleme erläutert und ihre potenziellen Ursachen isoliert. Außerdem werden die Frames der Registerkarte beschrieben.

## [!UICONTROL API calls by IP, details by URL]

Der Frame **[!UICONTROL API calls by IP, details by URL]** zeigt eine Anzahl von API-Aufrufen nach IP-Adressen über einen ausgewählten Zeitraum an. In diesem Frame werden die IP-Adresse und die API-URL angezeigt, auf die diese IP-Adresse zugegriffen hat.

![API-Aufrufe nach IP](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

Der Zugriffsrahmen &quot;**[!UICONTROL Forgot Password]**&quot; zeigt die Anzahl der vergessenen Kennwortversuche über einen ausgewählten Zeitraum an. Eine hohe Aktivität gegen eine IP-Adresse kann ein Angriff auf die Site sein.

![Kennwort vergessen](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

Der Frame **[!UICONTROL Create Account access]** zeigt die Anzahl neuer Kontoaktivitäten über einen ausgewählten Zeitraum an. Eine hohe Aktivität von einer einzelnen IP-Adresse kann auf einen Angriff hinweisen.

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

Der Frame **[!UICONTROL POST activities]** zeigt die `POST` -Aktivitäten für die Site an, die in `client_ip` aus den [!DNL Fastly] -Protokollen facettiert sind. Er zeigt auch die URL an, auf die die IP-Adresse zugreift.

![POST-activities](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

Der Frame **[!UICONTROL POST activities summary table]** zeigt die zusammengefassten `POST` Aktivitäten für die Site, die in `client_ip` aus den [!DNL Fastly] -Protokollen facettiert sind. Er zeigt auch die Anzahl der URLs an, auf die die IP-Adresse zugreift. Die Anzahl bezieht sich auf den ausgewählten Zeitraum.

![POST-activities-summary](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

Der Frame **[!UICONTROL POST activities details table]** zeigt die `POST` -Aktivitäten für die Site aus den [!DNL Fastly] -Protokollen an. Außerdem werden alle Details aus dem [!DNL Fastly]-Protokoll für diese Anfragen angezeigt. Sie ist auf die letzten Anfragen aus dem Jahr 2000 beschränkt.
![POST-activities-details](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

Der Frame &quot;**[!UICONTROL Guest Carts activities]**&quot;zeigt die Anzahl der Warenkorbaktivitäten über einen ausgewählten Zeitraum hinweg, facettiert nach IP-Adresse und URL, auf die zugegriffen wird. Der Warenkorb kann bei einem Warenkorbattest verwendet werden. Dieser Rahmen zeigt die Gesamtzahl der Anfragen, bei denen auf die URLs der Warenkorb zugegriffen wird.

![Gastwarenkorb-Aktivitäten](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

Der Frame &quot;**[!UICONTROL API – forgot password, create account by Countries]**&quot;zeigt die Anzahl der erstellten Konten und Anforderungen zum Zurücksetzen eines vergessenen Kennworts über einen ausgewählten Zeitraum an. Es wird auch das Ursprungsland des Antrags angezeigt. Dieser Rahmen konzentriert sich auf das Ursprungsland des Antrags.

![api-forgot-countries](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

Der Frame &quot;**[!UICONTROL API - forgot password, create account by Countries and IP address]**&quot;zeigt die Anzahl der erstellten Konten und Anforderungen zum Zurücksetzen eines vergessenen Kennworts über einen ausgewählten Zeitraum an. Sie zeigt auch die IP-Adresse, die aufgerufene URL und das Herkunftsland der Anfrage an. Dieser Frame konzentriert sich auf die Anzahl der IP-Adressen.

![api-forgot-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

Der Frame &quot;**[!UICONTROL Guest cart activities by IP]**&quot;zeigt Aktivitäten des Warenkorbs nach IP über einen ausgewählten Zeitraum an.

![gast-cart-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

Der Frame &quot;**[!UICONTROL Guest cart activities by Countries]**&quot;zeigt Aktivitäten des Warenkorbs nach Ländern über einen ausgewählten Zeitraum an.

![Gastland-Warenkorb-Land](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
