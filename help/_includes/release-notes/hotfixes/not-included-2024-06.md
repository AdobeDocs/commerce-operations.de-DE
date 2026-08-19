---
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---
# Hotfixes, die nicht in den Sicherheits-Patches vom Juni 2024 enthalten sind

>[!IMPORTANT]
>
>Dies ist eine dringende Aktualisierung unserer letzten Mitteilung zu [CVE-2024-34102](https://nvd.nist.gov/vuln/detail/CVE-2024-34102). Adobe ist sich bewusst, dass CVE-2024-34102 in der Wildnis in sehr begrenzten Angriffen auf Adobe Commerce-Händler ausgebeutet wurde. Ergreifen Sie sofort Maßnahmen, um die Sicherheitslücke zu schließen, falls Sie dies noch nicht getan haben.

**Für Kunden, die den Sicherheits-Patch vom 11. Juni 2024 oder den isolierten Patch vom 28. Juni 2024 nicht angewendet haben:**

Option 1:

1. Wenden Sie eines der Sicherheits-Patches an, die am 11. Juni 2024 veröffentlicht wurden:

   * [2.4.7-p1](/help/release/release-notes/security/2-4-7-patches.md#adobe-commerce-247-p1)

   * [2.4.6-p6](/help/release/release-notes/security/2-4-6-patches.md#adobe-commerce-246-p6)

   * [2.4.5-p8](/help/release/release-notes/security/2-4-5-patches.md#adobe-commerce-245-p8)

   * [2.4.4-p9](/help/release/release-notes/security/2-4-4-patches.md#adobe-commerce-244-p9)

1. Wenden Sie den [Hotfix](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-27136) an, der am 17. Juli 2024 veröffentlicht wurde.

1. [Drehen](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/security/encryption-key) Verschlüsselungsschlüssel.

Option 2:

1. Aufkleben [isolierten Pflasters](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-27136).

1. [Drehen](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/security/encryption-key) Verschlüsselungsschlüssel.

**Für Kunden, die bereits einen Sicherheits-Patch vom 11. Juni 2024 oder einen isolierten Patch vom 28. Juni 2024 angewendet haben:**

1. Wenden Sie den [Hotfix](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-27136) an, der am 17. Juli 2024 veröffentlicht wurde.

1. [Drehen](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/security/encryption-key) Verschlüsselungsschlüssel.

**Für Kunden, die bereits 1) einen Sicherheits-Patch vom 11. Juni 2024 oder 2) einen isolierten Patch vom 28. Juni 2024 angewendet haben, und 3) rotierten ihre Verschlüsselungsschlüssel:**
 
1. Wenden Sie den [Hotfix](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-27136) an, der am 17. Juli 2024 veröffentlicht wurde.
