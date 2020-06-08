---
title: Programma- en programmatypen
description: Programma- en programmatypen begrijpen - Cloud Services
translation-type: tm+mt
source-git-commit: 14da491cf09ed46ea425a8d65670d8b851aef388
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 3%

---


# Inzicht in programma&#39;s en programmatypen {#understanding-programs}

In Cloud Manager hebt u de entiteit Tenant helemaal bovenaan, die meerdere programma&#39;s kan bevatten.  Elk programma kan niet meer dan één milieu van de Productie, en veelvoudige niet-productiemilieu&#39;s bevatten.

In het volgende diagram ziet u de hiërarchie van entiteiten in Cloud Manager.

![image](assets/program-types1.png)

## Programmatypen {#program-types}

Een gebruiker kan een **Sandbox** of een **Regular** programma tot stand brengen.

Een *zandbak* wordt typisch gecreeerd om ten behoeve van opleiding, lopende demo&#39;s, enablement, POC&#39;s, of documentatie te dienen. Het is niet de bedoeling om het verkeer van personen te vervoeren en er zullen beperkingen zijn die een regulier programma niet zal hebben. Het zal Plaatsen en Activa omvatten en zal met een tak van het Git worden geleverd die steekproefcode, een Dev milieu, en een niet productiepijplijn omvat.

Er wordt een *regulier programma* gemaakt om live verkeer op het juiste tijdstip in de toekomst mogelijk te maken.