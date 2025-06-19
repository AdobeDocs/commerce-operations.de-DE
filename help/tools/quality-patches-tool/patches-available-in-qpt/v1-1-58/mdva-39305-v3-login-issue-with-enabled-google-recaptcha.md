---
title: 'MDVA-39305-V3: Anmeldeproblem mit aktiviert [!DNL Google reCAPTCHA]'
description: Wenden Sie den MDVA-39305-V3-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem sich registrierte Kunden nicht anmelden können, wenn  [!DNL Google reCAPTCHA]  aktiviert ist. Dieser Patch behebt auch das Problem, dass ein Formular gesendet werden kann, bevor  [!DNL Google reCAPTCHA]  vollständig geladen ist. Außerdem wird der Fehler *Aufruf einer Memberfunktion isDisabled() auf null* behoben, wenn Blöcke an nicht standardmäßigen Stellen auf einer CMS-Seite verwendet werden.
feature: Console
role: Admin
exl-id: 63e880aa-9a2e-4c34-9ead-20bfc5204f2c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-39305-V3: Anmeldeproblem mit aktiviertem [!DNL Google reCAPTCHA]

>[!NOTE]
>
>Dieser Patch ist ein Update des [MDVA-39305](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-1/mdva-39305-login-issues-with-enabled-google-recaptcha.md) Patches.

Der Patch MDVA-39305-V3 behebt das Problem, dass sich registrierte Kunden nicht anmelden können, wenn [!DNL Google reCAPTCHA] aktiviert ist. Dieser Patch behebt auch das Problem, dass ein Formular gesendet werden kann, bevor [!DNL Google reCAPTCHA] vollständig geladen ist. Darüber hinaus wird der Fehler *Aufruf einer Memberfunktion isDisabled() auf null)*, wenn Blöcke an nicht standardmäßigen Speicherorten auf einer CMS-Seite verwendet werden.

Dieser Patch wurde in der Version [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48 hinzugefügt. In der Version QPT 1.1.58 wurde sie aktualisiert, um die neuen Adobe Commerce-Versionen 2.4.7 - 2.4.7-p4 einzuschließen. Die Patch-ID lautet MDVA-39305-V3. Beachten Sie, dass das Problem in den Adobe Commerce-Versionen 2.4.4, 2.4.5-p2 und 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4, 2.4.5-p2, 2.4.7

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Probleme

### Fall I

1. Registrierte Kunden können sich nicht mit dem aktivierten [!DNL Google reCAPTCHA] anmelden.
1. Ein Formular kann gesendet werden, bevor [!DNL Google reCAPTCHA] vollständig geladen ist.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]** > **[!DNL Google reCAPTCHA Storefront]** und aktivieren Sie ***[!DNL Google reCAPTCHA]***.
1. Zum Frontend gehen.
1. Öffnen Sie **[!UICONTROL Developer Tool Console]** im Browser.

<u>Erwartete Ergebnisse</u>:

Keine CSP-Warnungen in der Konsole.

<u>Tatsächliche Ergebnisse</u>:

CSP-Warnungen in der Konsole.

### Fall II

Es wird ein Fehler *Aufruf einer Memberfunktion isDisabled() auf null* ausgelöst, wenn Blöcke an nicht standardmäßigen Speicherorten auf einer CMS-Seite verwendet werden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einen statischen Block mit folgendem Inhalt:

   ```
   {{block class="Magento\Newsletter\Block\Subscribe" name="home.form.subscribe"
   template="Magento_Newsletter::subscribe.phtml"}}
   ```

1. Fügen Sie einen statischen Block zu einer CMS-Seite über **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** > **[!UICONTROL Add/Edit CMS page]** > **[!UICONTROL Content]** hinzu.
1. Speichern Sie die Seite.

<u>Erwartete Ergebnisse</u>:

Die Seite wird fehlerfrei geladen.

<u>Tatsächliche Ergebnisse</u>:

Auf der Seite in der Storefront tritt ein 500-Fehler auf.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
