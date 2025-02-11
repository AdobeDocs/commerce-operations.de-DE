---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---
# Sicherheits-Patch-Highlights vom Oktober 2024

Diese Version umfasst die folgenden Highlights:

* **TinyMCE-Upgrade** - Der [WYSIWYG-](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/wysiwyg/editor)Editor) im Admin verwendet jetzt die neueste Version der TinyMCE-Abhängigkeit (7.3&#x200B;).

   * TinyMCE 7.3 bietet ein verbessertes Benutzererlebnis, bessere Zusammenarbeit und erhöhte Effizienz. TinyMCE 5 wurde in der Release-Zeile 2.4.8 entfernt&#x200B;

   * Da in TinyMCE 5.10 eine Sicherheitslücke ([CVE-2024-38357](https://nvd.nist.gov/vuln/detail/CVE-2024-38357)) gemeldet wurde, wurde die Abhängigkeit auch für alle derzeit unterstützten Versionszeilen aktualisiert und in alle Sicherheits-Patches vom Oktober 2024 aufgenommen:

      * 2.4.7-p3
      * 2.4.6-p8
      * 2.4.5-P10
      * 2.4.4-P11

* **Require.js-**: Adobe Commerce verwendet jetzt die neueste Version von Require.js (2.3.7).

   * Da in Require.js 2.3.6 eine Sicherheitslücke ([CVE-2024-38999](https://nvd.nist.gov/vuln/detail/CVE-2024-38999)) gemeldet wurde, wurde die Abhängigkeit auch für alle derzeit unterstützten Versionszeilen aktualisiert und in alle Sicherheits-Patches vom Oktober 2024 aufgenommen:

      * 2.4.7-p3
      * 2.4.6-p8
      * 2.4.5-P10
      * 2.4.4-P11

>[!NOTE]
>
>Diese Aktualisierungen sind abwärtskompatibel und sollten sich nicht auf Anpassungen und Erweiterungen auswirken&#x200B;
