---
title: Programma- en programmatypen
description: Programma- en programmatypen begrijpen - Cloud Services
exl-id: 507df619-a5b5-419a-9e38-db77541425a2
source-git-commit: 7e51fb98c76a5913ef237aca3b66c73a8263f4ff
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 2%

---

# Inzicht in programma&#39;s en programmatypen {#understanding-programs}

In Cloud Manager hebt u de entiteit Tenant helemaal bovenaan, die meerdere programma&#39;s kan bevatten. Elk programma kan niet meer dan één milieu van de Productie, en veelvoudige niet-productiemilieu&#39;s bevatten.

In het volgende diagram ziet u de hiërarchie van entiteiten in Cloud Manager.

![afbeelding](assets/program-types1.png)

## Broncodeopslagplaats {#source-code-repository}

Cloud Manager-programma wordt automatisch ingericht met de eigen git-opslagruimte.

Gebruikers kunnen alleen toegang krijgen tot de gegevensopslagruimte van Cloud Manager als ze een Git-client gebruiken met een opdrachtregelprogramma, een zelfstandige visuele Git-client of de IDE van de gebruiker, zoals Eclipse, IntelliJ, NetBeans.

Zodra een Git-client is ingesteld, kunt u de git-opslagplaats beheren vanuit de interface van Cloud Manager. Raadpleeg [Toegang tot Git](/help/implementing/cloud-manager/managing-code/accessing-repos.md) voor meer informatie over het beheren van Git met de interface van Cloud Manager.

Als u de AEM Cloud-toepassing wilt gaan ontwikkelen, moet u een lokale kopie van de toepassingscode maken door deze uit te checken van de opslagplaats van Cloud Manager naar een locatie op de lokale computer waar ze hun opslagplaats willen maken.

```java
$ git clone {URL}
```

>[!NOTE]
>Een gebruiker kan een kopie van de code uitchecken en wijzigingen aanbrengen in de lokale gegevensopslagruimte. Als de gebruiker klaar is, kan hij of zij de wijzigingen in de code doorvoeren naar de externe opslagplaats voor code in Cloud Manager.

## Programmatypen {#program-types}

Een gebruiker kan een **Sandbox** of een **Production** programma tot stand brengen.

* Een *Productieprogramma* wordt gecreeerd om levend verkeer op het aangewezen tijdstip in de toekomst toe te laten.
Raadpleeg [Inleiding tot productieprogramma&#39;s](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/production-programs/introduction-production-programs.html?lang=en) voor meer informatie.


* Een *Sandbox-programma* wordt doorgaans gemaakt voor trainingsdoeleinden, het uitvoeren van demo&#39;s, activering, concepttest of documentatie. Het is niet de bedoeling om levend verkeer te vervoeren en zal beperkingen hebben die een productieprogramma niet zal hebben. Het zal Plaatsen en Activa omvatten en zal met een tak van het Git worden geleverd die steekproefcode, een Dev milieu, en een niet productiepijplijn omvat.
Raadpleeg [Inleiding tot Sandbox-programma&#39;s](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sandbox-programs/introduction-sandbox-programs.html?lang=en) voor meer informatie.
