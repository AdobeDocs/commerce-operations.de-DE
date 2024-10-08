---
source-git-commit: cb4f388c90902c2fe1df4a5d84841280fa740104
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---
# Sicherheitspatch von Oktober 2024 - Highlights

Diese Version umfasst die folgenden Highlights:

* **TinyMCE-Upgrade** - Der [WYSIWYG-Editor](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/wysiwyg/editor) im Admin verwendet jetzt die neueste Version der TinyMCE-Abhängigkeit (7.3 &#x200B;).

   * TinyMCE 7.3 bietet eine verbesserte Benutzererfahrung, bessere Zusammenarbeit und höhere Effizienz. TinyMCE 5 wurde in der Release-Zeile 2.4.8 entfernt. &#x200B;

   * Da eine Sicherheitslücke ([CVE-2024-38357](https://nvd.nist.gov/vuln/detail/CVE-2024-38357)) aufgetreten ist, die in TinyMCE 5.10 gemeldet wurde, wurde die Abhängigkeit auch für alle derzeit unterstützten Release-Zeilen aktualisiert und in alle Sicherheits-Patches vom Oktober 2024 aufgenommen:

      * 2.4.7-p3
      * 2.4.6-p8
      * 2.4.5-p10
      * 2.4.4-p11

* **Require.js upgrade** - Adobe Commerce verwendet jetzt die neueste Version von Require.js (2.3.7).

   * Da eine Sicherheitslücke ([CVE-2024-38999](https://nvd.nist.gov/vuln/detail/CVE-2024-38999)) aufgetreten ist, die in Require.js 2.3.6 gemeldet wurde, wurde die Abhängigkeit auch für alle derzeit unterstützten Release-Zeilen aktualisiert und in alle Sicherheits-Patches vom Oktober 2024 aufgenommen:

      * 2.4.7-p3
      * 2.4.6-p8
      * 2.4.5-p10
      * 2.4.4-p11

>[!NOTE]
>
>Diese Aktualisierungen sind abwärtskompatibel und sollten sich nicht auf Anpassungen und Erweiterungen auswirken. &#x200B;
