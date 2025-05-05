---
title: 'ACSD-47497: fehlende ACL für Speicher/Konfiguration/Services-[!UICONTROL OAuth]'
description: Wenden Sie den Patch ACSD-47497 an, um das Adobe Commerce-Problem zu beheben, wenn Berechtigungen für eine bestimmte Rolle festgelegt sind und Sie keinen Zugriff auf den Konfigurationsabschnitt definieren können.
feature: Configuration, Identity Management, Services
role: Admin
exl-id: 4dbbd7df-f34b-4db8-a207-3de40fb39c6f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-47497: fehlende ACL für Speicher/Konfiguration/Services-[!UICONTROL OAuth]

Mit dem Patch ACSD-47497 wird das Problem behoben, dass die Registerkarte **[!UICONTROL Services]** im Abschnitt **[!UICONTROL Configuration]** in Adobe Commerce Admin nicht angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23 installiert ist. Die Patch-ID ist ACSD-47497. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn Berechtigungen für eine bestimmte Rolle festgelegt sind, können Sie den Zugriff auf **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]** nicht definieren.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich beim Adobe Commerce Admin an. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**.
1. Wählen Sie **[!UICONTROL Role Resources]** in der Rolle Administratoren aus, setzen Sie **[!UICONTROL Resource Access]** unter **[!UICONTROL Roles Resources]** auf _Benutzerdefiniert_ und aktivieren Sie dann alle Kontrollkästchen. Wählen Sie **[!UICONTROL Save Role]** aus.
1. Wählen Sie **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** aus. Der Abschnitt **[!UICONTROL OAuth]** ist nicht verfügbar.

<u>Erwartete Ergebnisse</u>:

In **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]** ist der Konfigurationsabschnitt sichtbar.

<u>Tatsächliche Ergebnisse</u>:

In **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]** fehlt der Konfigurationsabschnitt .

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
