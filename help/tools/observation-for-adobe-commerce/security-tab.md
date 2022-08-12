---
title: '"Die [!UICONTROL Security] tab"'
description: Erfahren Sie mehr über die [!UICONTROL Security] Tab von [!DNL Observation for Adobe Commerce].
source-git-commit: 5e4babd14bb918db7f894b7ca6a0344a4652704c
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# Die [!UICONTROL Security] tab

Die **[!UICONTROL Security]** -Tab erklärt Sicherheitsprobleme und isoliert deren potenzielle Ursachen. Außerdem werden die Frames der Registerkarte beschrieben.

## [!UICONTROL API calls by IP, details by URL]

Die **[!UICONTROL API calls by IP, details by URL]** frame zeigt eine Reihe von API-Aufrufen nach IP-Adressen über einen ausgewählten Zeitraum an. In diesem Frame werden die IP-Adresse und die API-URL angezeigt, auf die diese IP-Adresse zugegriffen hat.

![API-Aufrufe nach IP](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

Die **[!UICONTROL Forgot Password]** Der Zugriffframe zeigt die Anzahl der vergessenen Kennwortversuche über einen ausgewählten Zeitraum an. Eine hohe Aktivität gegen eine IP-Adresse kann ein Angriff auf die Site sein.

![Kennwort vergessen](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

Die **[!UICONTROL Create Account access]** frame zeigt die Anzahl neuer Kontoaktivitäten über einen ausgewählten Zeitraum hinweg an. Eine hohe Aktivität von einer einzelnen IP-Adresse kann auf einen Angriff hinweisen.

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

Die **[!UICONTROL POST activities]** frame zeigt die Aktivitäten der POST für die Site, facettiert auf client_ip aus der [!DNL Fastly] Protokolle. Er zeigt auch die URL an, auf die die IP-Adresse zugreift.

![POST-Aktivitäten](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

Die **Übersichtstabelle der POST-Aktivitäten** frame zeigt die zusammengefassten Aktivitäten zur POST der Site, facettiert auf client_ip aus der [!DNL Fastly] Protokolle. Er zeigt auch die Anzahl der URLs an, auf die die IP-Adresse zugreift. Die Anzahl bezieht sich auf den ausgewählten Zeitraum.

![POST-activities-summary](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

Die **[!UICONTROL POST activities details table]** frame zeigt die POST für die Site von der [!DNL Fastly] Protokolle. Außerdem werden alle Details aus dem [!DNL Fastly] protokollieren. Sie ist auf die letzten Anfragen aus dem Jahr 2000 beschränkt.
![POST-activities-details](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

Die **[!UICONTROL Guest Carts activities]** frame zeigt die Anzahl der Warenkorbaktivitäten in einem ausgewählten Zeitraum, facettiert nach IP-Adresse und aufgerufener URL. Der Warenkorb kann bei einem Warenkorbattest verwendet werden. Dieser Rahmen zeigt die Gesamtzahl der Anfragen, bei denen auf die URLs des Gastwagens zugegriffen wird.

![Guest-Warenkorb-activities](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

Die **[!UICONTROL API – forgot password, create account by Countries]** frame zeigt die Anzahl der erstellten Konten und Anforderungen zum Zurücksetzen eines vergessenen Kennworts über einen ausgewählten Zeitraum an. Es wird auch das Ursprungsland des Antrags angezeigt. Dieser Rahmen konzentriert sich auf das Ursprungsland des Antrags.

![api-forgot-countries](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

Die **[!UICONTROL API - forgot password, create account by Countries and IP address]** frame zeigt die Anzahl der erstellten Konten und Anforderungen zum Zurücksetzen eines vergessenen Kennworts über einen ausgewählten Zeitraum an. Sie zeigt auch die IP-Adresse, die aufgerufene URL und das Herkunftsland der Anfrage an. Dieser Frame konzentriert sich auf die Anzahl der IP-Adressen.

![api-forgot-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

Die **[!UICONTROL Guest cart activities by IP]** frame zeigt Aktivitäten des Warenkorbs nach IP über einen ausgewählten Zeitraum an.

![Guest-Warenkorb-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

Die **[!UICONTROL Guest cart activities by Countries]** frame zeigt Aktivitäten im Warenkorb nach Ländern über einen ausgewählten Zeitraum an.

![Gastland](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
