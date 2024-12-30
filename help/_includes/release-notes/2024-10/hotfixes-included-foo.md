---
source-git-commit: 5ef5c2dedbbef2858a6bbc6c0aca13fd9adae0c8
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---
# In Sicherheits-Patches vom Oktober enthaltene Hotfixes (außer 2.4.4)

Diese Version enthält einen Hotfix zur Behebung eines Problems mit dem Braintree Payment Gateway.

Das System enthält nun die notwendigen Felder, um die Anforderungen des 3DS VISA Mandats bei der Nutzung von Braintree als Zahlungs-Gateway zu erfüllen. Dadurch wird sichergestellt, dass alle Transaktionen den neuesten von VISA festgelegten Sicherheitsstandards entsprechen. Zuvor waren diese zusätzlichen Felder nicht in den übermittelten Zahlungsinformationen enthalten, was zur Nichteinhaltung der neuen VISA-Anforderungen hätte führen können.

<!--
BUNDLE-3360
-->