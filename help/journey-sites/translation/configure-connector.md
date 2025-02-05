---
title: De vertalingsconnector (AEM Sites) configureren
description: Leer hoe u verbinding AEM maken met een vertaalservice.
index: true
hide: false
hidefromtoc: false
exl-id: d1a3eb42-e9e4-4118-9ff7-7aab5519cf0d
solution: Experience Manager Sites
feature: Translation
role: Admin
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 0%

---

# De vertalingsconnector configureren {#configure-connector}

Leer hoe u verbinding AEM maken met een vertaalservice.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de de vertaalreis van AEM Sites, [ worden begonnen met de vertaling van AEM Sites ](learn-about.md) u leerde hoe te om uw inhoud te organiseren en hoe AEM vertaalhulpmiddelen werken en u zou nu moeten:

* Begrijp het belang van inhoudsstructuur voor vertaling.
* Begrijp hoe AEM inhoud opslaat.
* Wees vertrouwd met AEM vertaalhulpmiddelen.

Dit artikel bouwt op die grondbeginselen voort zodat kunt u de eerste configuratiestap nemen en de vertaaldienst opzetten, die u later in de reis zult gebruiken om uw inhoud te vertalen.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe te opstelling een AEM schakelaar aan uw gekozen vertaaldienst. Na het lezen moet u:

* Begrijp de belangrijke parameters van het Kader van de Integratie van de Vertaling in AEM.
* Uw eigen verbinding met uw vertaalservice instellen.

## Het vertaalintegratieframework {#tif}

AEM TIF (Translation Integration Framework) integreert met vertaalservices van derden om de vertaling van AEM inhoud te ordenen. Het gaat om drie basisstappen.

1. Maak verbinding met uw vertaalserviceprovider.
1. Creeer een configuratie van het Kader van de Integratie van de Vertaling.
1. Koppel de configuratie aan uw inhoud.

In de volgende secties worden deze stappen nader beschreven.

## Verbinding maken met een vertaalserviceprovider {#connect-translation-provider}

De eerste stap bestaat uit het kiezen van de vertaalservice die u wilt gebruiken. Er zijn vele keuzen voor mensen en machine vertaaldiensten beschikbaar aan AEM. De meeste providers bieden een vertaalpakket aan dat moet worden geïnstalleerd. Zie de [ Extra sectie van Middelen ](#additional-resources) voor een selectie van beschikbare opties.

>[!NOTE]
>
>De vertaalspecialist is over het algemeen verantwoordelijk voor het kiezen van welke vertaaldienst aan gebruik, maar de beheerder is typisch verantwoordelijk voor het installeren van het vereiste pakket van de vertaalschakelaar.

Voor deze reis gebruiken we de Microsoft-vertaler die een proeflicentie AEM aanbieden. Zie de [ Extra sectie van Middelen ](#additional-resources) voor meer informatie over deze leverancier.

Als u een andere leverancier kiest, moet uw beheerder het aansluitingspakket installeren volgens de instructies van de vertaalservice.

>[!NOTE]
>
>Het gebruik van de uit-van-de-doos Microsoft Vertaler in AEM vereist geen extra opstelling en werkt zoals-is zonder extra schakelaarconfiguratie.
>
>Als u verkiest om de Vertaalschakelaar van Microsoft voor het testen doeleinden te gebruiken, te hoeven u niet om de stappen in de volgende twee secties uit te voeren: [ Creërend een Configuratie van de Integratie van de Vertaling ](#create-config) en [ associeer de Configuratie met Uw Inhoud ](#associate). Nochtans wordt u geadviseerd om hen te lezen zodat u met de stappen vertrouwd bent voor wanneer u uw aangewezen schakelaar moet vormen.
>
>De proefvergunning van de Vertaalschakelaar van Microsoft is niet voorgenomen voor productiedoeleinden en als u besluit om het vergunning te geven, moet de systeembeheerder de stappen volgen die in de [ Extra sectie van Middelen ](#additional-resources) aan het eind van dit document worden gedetailleerd om die vergunning te vormen.

## Een configuratie voor vertaalintegratie maken {#create-config}

Nadat het schakelaarpakket voor uw aangewezen vertaaldienst wordt geïnstalleerd, moet u een configuratie van het Kader van de Integratie van de Vertaling voor die dienst tot stand brengen. De configuratie bevat de volgende informatie:

* Welke vertaalserviceprovider moet worden gebruikt?
* Of het vertalen van mensen of machines moet worden uitgevoerd
* Of andere inhoud die aan de pagina&#39;s is gekoppeld, zoals codes, moet worden vertaald

Een vertaalconfiguratie maken:

1. In het globale navigatiemenu, uitgezochte **Hulpmiddelen** > **Cloud Servicen** > **Cloud Servicen van de Vertaling**.
1. Navigeer naar de plaats waar u de configuratie in uw inhoudsstructuur wilt creëren. Dit is vaak gebaseerd op een bepaald project of kan globaal zijn.
   * In dit geval zou een configuratie globaal kunnen worden gemaakt om op alle inhoud, of enkel voor het WKND project van toepassing te zijn.

   {de configuratielocatie van 0} Vertaling ](assets/translation-configuration-location.png)![

1. Selecteer **creeer** in de toolbar om de nieuwe configuratie tot stand te brengen.
1. Verstrek de volgende informatie op de gebieden en selecteer dan **creeer**.
   1. Selecteer **Type van Configuratie** in drop-down. Selecteer **Integratie van de Vertaling** van de lijst.
   1. Ga a **Titel** voor uw configuratie in. De **Titel** identificeert de configuratie in de **Cloud Servicen** console en in pagina bezit drop-down lijsten.
   1. Naar keuze, typ a **Naam** om voor de opslagplaats knoop te gebruiken die de configuratie opslaat.

   ![ creeer vertaalconfiguratie ](assets/create-translation-configuration.png)

1. Selecteer **creeer** en **geef het venster van de Configuratie** uit verschijnt waar u de configuratieeigenschappen kunt vormen.

1. Omdat uw inhoud als plaatsen beheert, selecteer de **Plaatsen** tabel.

![ de configuratieeigenschappen van de Vertaling ](assets/translation-configuration.png)

1. Geef de volgende informatie op.

   1. **Vertaalmethode** - selecteer **Vertaling van de Machine** of **Menselijke Vertaling** afhankelijk van uw vertaalleverancier. In het kader van deze reis gaan we uit van machinevertaling.
   1. **Vertaalleveranciers** - selecteer de schakelaar u voor uw vertaaldienst van de lijst installeerde.
   1. **Categorie van de Inhoud** - selecteer de meest aangewezen categorie om de vertaling (slechts voor machinevertaling) beter te richten.
   1. **Vertaal de Pagina Assets** - selecteer **Gebruikend het Werkschema van de Vertaling van Plaatsen** om de activa te vertalen verbonden aan de plaatspagina&#39;s.
   1. **vertaalde Koorden van de Component** - controleer dit om componenteninformatie te vertalen.
   1. **vertaalde Markeringen** - controleer dit om markeringen te vertalen die met de pagina worden geassocieerd.
   1. **Auto-Uitvoer Vertaling** - controleer dit bezit als u vertalingen automatisch naar uw vertaaldienst wilt worden verzonden.

1. Selecteer **sparen &amp; Sluiten**.

U hebt nu de schakelaar aan uw vertaaldienst gevormd.

## De configuratie koppelen aan uw inhoud {#associate}

AEM is een flexibel en krachtig hulpmiddel en steunt veelvoudige, gelijktijdige vertaaldiensten via veelvoudige schakelaars en veelvoudige configuraties. Het opzetten van een dergelijke configuratie valt buiten het bereik van deze reis. Nochtans betekent deze flexibiliteit dat u moet specificeren welke schakelaars en configuratie zouden moeten worden gebruikt om uw inhoud te vertalen door deze configuratie met uw inhoud te associëren.

Navigeer hiertoe naar de hoofdtaalmap van de inhoud. Voor ons voorbeelddoel is dit

```text
/content/<your-project>/en
```

1. Ga naar de globale navigatie en ga naar **Navigatie** > **Assets** > **Dossiers**.
1. In de activa console, selecteer de taalwortel om **Eigenschappen** te vormen en te selecteren.
1. Selecteer de **Cloud Servicen** tabel.
1. Onder **Configuraties van de Cloud Service** in **voeg de drop-down lijst van de Configuratie** toe, selecteer uw schakelaar. Het zou in de drop-down lijst moeten verschijnen wanneer u zijn pakket zoals [ eerder beschreven ](#connect-translation-provider) hebt geïnstalleerd.
1. Onder **Configuraties van de Cloud Service** in **voeg de drop-down lijst van de Configuratie** toe, ook uw configuratie.
1. Selecteer **sparen &amp; Sluiten**.

![ Uitgezochte configuraties van de wolkendienst ](assets/select-cloud-service-configurations.png)

## Volgende functies {#what-is-next}

Nu u dit deel van de AEM Sites-vertaalreis hebt voltooid, moet u:

* Begrijp de belangrijke parameters van het Kader van de Integratie van de Vertaling in AEM.
* Uw eigen verbinding met uw vertaalservice instellen.

Bouw op deze kennis voort en ga uw de vertaalreis van AEM Sites door het document [ opnieuw te bekijken vorm vertaalregels ](translation-rules.md), waar u leert hoe te om te bepalen welke inhoud te vertalen.

## Aanvullende bronnen {#additional-resources}

Terwijl wordt geadviseerd dat u zich op het volgende deel van de vertaalreis door het document [ te herzien vormt vertaalregels ](translation-rules.md) beweegt is het volgende wat extra, facultatieve middelen die een diepere duik op sommige die concepten doen in dit document worden vermeld, maar zij worden niet vereist om op de reis verder te gaan.

* [ Vormend het Kader van de Integratie van de Vertaling ](/help/sites-cloud/administering/translation/integration-framework.md) - herzie een lijst van geselecteerde vertaalschakelaars en leer hoe te om het Kader van de Integratie van de Vertaling te vormen om met derdevertaaldiensten te integreren.
* [ Verbonden met de Vertaler van Microsoft ](/help/sites-cloud/administering/translation/connect-ms-translator.md) - AEM verstrekt een proefrekening van de Vertaling van Microsoft voor het testen doeleinden.
