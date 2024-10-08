---
source-git-commit: 5ef5c2dedbbef2858a6bbc6c0aca13fd9adae0c8
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---
# In Sicherheits-Patches vom Oktober enthaltene Hotfixes (außer 2.4.4)

Diese Version enthält einen Hotfix, um ein Problem mit dem Braintree Payment Gateway zu beheben.

Das System enthält jetzt die erforderlichen Felder, um die Anforderungen an das 3DS VISA-Mandat bei Verwendung von Braintree als Zahlungs-Gateway zu erfüllen. Dadurch wird sichergestellt, dass alle Transaktionen den neuesten von VISA festgelegten Sicherheitsstandards entsprechen. Zuvor waren diese zusätzlichen Felder nicht in den gesendeten Zahlungsinformationen enthalten, was zu einer Nichteinhaltung der neuen VISA-Anforderungen hätte führen können.

<!--
BUNDLE-3360
-->