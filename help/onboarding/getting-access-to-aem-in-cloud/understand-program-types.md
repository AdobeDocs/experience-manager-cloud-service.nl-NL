---
title: Programma- en programmatypen
description: Programma- en programmatypen begrijpen - Cloud Services
translation-type: tm+mt
source-git-commit: 5a4353cb31337882a1c13b0ed830ea64f617181a
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 3%

---


# Inzicht in programma&#39;s en programmatypen {#understanding-programs}

In Cloud Manager hebt u de entiteit Tenant helemaal bovenaan, die meerdere programma&#39;s kan bevatten. Elk programma kan niet meer dan één milieu van de Productie, en veelvoudige niet-productiemilieu&#39;s bevatten.

In het volgende diagram ziet u de hiërarchie van entiteiten in Cloud Manager.

![afbeelding](assets/program-types1.png)

## Programmatypen {#program-types}

Een gebruiker kan een **Sandbox** of een **Production** programma tot stand brengen.

* Een *Productieprogramma* wordt gecreeerd om levend verkeer op het aangewezen tijdstip in de toekomst toe te laten.
Raadpleeg [Inleiding tot productieprogramma&#39;s](/help/onboarding/getting-access-to-aem-in-cloud/introduction-production-programs.md) voor meer informatie.


* Een *Sandbox-programma* wordt doorgaans gemaakt voor trainingsdoeleinden, het uitvoeren van demo&#39;s, activering, concepttest of documentatie. Het is niet de bedoeling om levend verkeer te vervoeren en zal beperkingen hebben die een productieprogramma niet zal hebben. Het zal Plaatsen en Activa omvatten en zal met een tak van het Git worden geleverd die steekproefcode, een Dev milieu, en een niet productiepijplijn omvat.
Raadpleeg [Inleiding tot Sandbox-programma&#39;s](/help/onboarding/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md) voor meer informatie.

