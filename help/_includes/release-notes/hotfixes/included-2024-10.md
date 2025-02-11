---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---
# In Sicherheits-Patches vom Oktober enthaltene Hotfixes (außer 2.4.4)

Diese Version enthält einen Hotfix, um ein Problem mit dem Braintree Payment Gateway zu beheben.

Das System enthält jetzt die erforderlichen Felder, um die Anforderungen des 3DS-VISA-Mandats zu erfüllen, wenn Braintree als Zahlungs-Gateway verwendet wird. Dadurch wird sichergestellt, dass alle Transaktionen den neuesten von VISA festgelegten Sicherheitsstandards entsprechen. Zuvor waren diese zusätzlichen Felder nicht in den übermittelten Zahlungsinformationen enthalten, was zur Nichteinhaltung der neuen VISA-Anforderungen hätte führen können.

<!--
BUNDLE-3360
-->