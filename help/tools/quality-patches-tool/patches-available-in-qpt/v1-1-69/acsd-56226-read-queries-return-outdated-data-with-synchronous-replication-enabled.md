---
title: 'ACSD-56226: READ-Abfragen geben veraltete Daten zurück, wenn „synchrone_Replikation“ aktiviert ist'
description: Wenden Sie den Patch ACSD-56226 an, um das Adobe Commerce-Problem zu beheben, bei dem LESEABFRAGEN veraltete Daten zurückgeben, wenn das Flag „synchrone_Replikation“ für die Slave-Verbindung in der Cloud aktiviert ist.
feature: System
role: Admin, Developer
type: Troubleshooting
exl-id: 5ad0e884-decb-4e09-b5b3-b38a9953a4b8
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
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
source-wordcount: '355'
ht-degree: 0%
---
# ACSD-56226: READ-Abfragen geben veraltete Daten zurück, wenn `synchronous_replication` aktiviert ist

Der Patch ACSD-56226 behebt das Problem, dass READ-Abfragen veraltete Daten zurückgeben, wenn das `synchronous_replication`-Flag für die Slave-Verbindung in der Cloud aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 installiert ist. Die Patch-ID ist ACSD-56226. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.7 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

READ-Abfragen geben veraltete Daten zurück, wenn das `synchronous_replication`-Flag aktiviert ist. Dies führt dazu, dass die Slave-Verbindung deaktiviert wird, was zu einer Überlastung der Datenbank führt.

<u>Schritte zur Reproduktion</u>:

1. Setzen Sie `MYSQL_USE_SLAVE_CONNECTION` in den *in Adobe Commerce auf Cloud-Infrastruktur auf* true“.
1. Fügen Sie die folgende Konfiguration zu `.magento.env.yaml` hinzu, um `synchronous_replication` auf &quot;*&quot;*:

   ```text
   DATABASE_CONFIGURATION:
     _merge: true
     slave_connection:
       default:
         synchronous_replication: false
   ```

1. Stellen Sie Frontend-Aktionen erneut bereit und führen Sie sie durch, z. B. beim Anmelden, beim Hinzufügen zum Warenkorb oder bei einer Bestellung.

<u>Erwartete Ergebnisse</u>:

Die Slave-Verbindung bleibt aktiviert, wenn `synchronous_replication` auf &quot;*&quot;*.

<u>Tatsächliche Ergebnisse</u>:

Die Slave-Verbindung ist deaktiviert, wenn `synchronous_replication` auf &quot;*&quot; gesetzt*, was zu einer Datenbanküberlastung führt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
