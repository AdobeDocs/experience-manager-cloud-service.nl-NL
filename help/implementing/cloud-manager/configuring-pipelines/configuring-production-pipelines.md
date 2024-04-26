---
title: Productiepijpleidingen configureren
description: Leer hoe te om productiepijpleidingen te vormen om uw code aan productiemilieu's te bouwen en op te stellen.
index: true
exl-id: 67edca16-159e-469f-815e-d55cf9063aa4
source-git-commit: d1b2226a1deec2e71056c43c84672cb4a358bc8c
workflow-type: tm+mt
source-wordcount: '1334'
ht-degree: 0%

---


# Een productiepijpleiding configureren {#configure-production-pipeline}

Leer hoe te om productiepijpleidingen te vormen om uw code aan productiemilieu&#39;s te bouwen en op te stellen. Een productiepijpleiding stelt code eerst aan werkgebiedmilieu op, en bij goedkeuring stelt de zelfde code aan het productiemilieu op.

Een gebruiker moet beschikken over **[Implementatiebeheer](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** rol om productiepijpleidingen te configureren.

>[!NOTE]
>
>Een productiepijplijn kan pas worden ingesteld wanneer de programma&#39;s zijn gemaakt, een opslagplaats voor kompas ten minste één tak heeft en er een productie- en parkeeromgeving is ingesteld.

Alvorens u begint uw code op te stellen, moet u uw pijpleidingsmontages van vormen [!UICONTROL Cloud Manager].

>[!NOTE]
>
>U kunt [pijpleidingsinstellingen bewerken](managing-pipelines.md) na de eerste installatie.

## Een nieuwe productiepijpleiding toevoegen {#adding-production-pipeline}

Als u uw programma hebt ingesteld en ten minste één omgeving hebt die de [!UICONTROL Cloud Manager] UI, bent u bereid om een productiepijplijn toe te voegen door deze stappen te volgen.

>[!TIP]
>
>Alvorens u een front-end pijpleiding vormt, zie [Reis voor snel maken van site AEM](/help/journey-sites/quick-site/overview.md) voor een end-to-end handleiding met het gebruiksvriendelijke AEM gereedschap Snel site maken. Deze reis zal u helpen de front-end ontwikkeling van uw AEM Plaats stroomlijnen, die u toestaat om uw plaats snel aan te passen zonder AEM achterste-eindkennis.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie

1. Op de **[Mijn programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)** -console, selecteert u het programma.

1. Ga naar de **Pijpleidingen** kaart van **Programmaoverzicht** pagina en klik op **Toevoegen** om **Productiepijpleiding toevoegen**.

   ![De pijplijnkaart op het overzicht van de Manager van het Programma](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. De **Productiepijpleiding toevoegen** wordt weergegeven. Geef een **Naam pijpleiding** om uw pijpleiding samen met de volgende opties te identificeren. Klikken **Doorgaan**.

   **Implementatieactivering** - U hebt de volgende opties wanneer het bepalen van de plaatsingstrekkers om de pijpleiding te beginnen.

   * **Handmatig** - Gebruik deze optie om de pijpleiding manueel te beginnen.
   * **Wijzigingen in Git** - Deze opties beginnen de pijpleiding CI/CD wanneer de bemoeienis aan de gevormde git tak wordt toegevoegd. Met deze optie, kunt u de pijpleiding nog manueel zoals vereist beginnen.

   **Belangrijk gedrag metrische fouten** - Tijdens het instellen of bewerken van pijpleidingen **Implementatiebeheer** heeft de optie om het gedrag van de pijpleiding te bepalen wanneer een belangrijke mislukking in om het even welke kwaliteitspoorten wordt ontmoet. De beschikbare opties zijn:

   * **Telkens vragen** - Dit is de standaardinstelling en u moet handmatig ingrijpen als een belangrijke fout optreedt.
   * **Direct mislukken** - Indien geselecteerd, wordt de pijpleiding geannuleerd wanneer een belangrijke mislukking voorkomt. Dit is in feite het emuleren van een gebruiker die elke fout handmatig afwijst.
   * **Direct doorgaan** - Indien geselecteerd, zal de pijpleiding automatisch te werk gaan wanneer een belangrijke mislukking voorkomt. Dit emuleert hoofdzakelijk een gebruiker manueel goedkeurend elke mislukking.

   ![Configuratie productiepijplijn](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-configuration.png)

1. Op de **Broncode** lusje u moet selecteren welk type van code de pijpleiding zou moeten verwerken.

   * **[Volledige stapelcode](#full-stack-code)**
   * **[Gerichte implementatie](#targeted-deployment)**

Zie [CI/CD-pijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) voor meer informatie over de soorten pijpleidingen .

De stappen om de verwezenlijking van uw productiepijplijn te voltooien variëren afhankelijk van het type van broncode u selecteerde. Volg de verbindingen hierboven om aan de volgende sectie van dit document te springen zodat kunt u de configuratie van uw pijpleiding voltooien.

### Volledige stapelcode {#full-stack-code}

Een full-stack codepijpleiding stelt gelijktijdig achterste en front-end codebouwstijlen op die één of meerdere AEM servertoepassingen samen met configuratie HTTPD/Dispatcher bevatten.

>[!NOTE]
>
>Als er al een &#39;full-stack&#39;-codepijplijn voor de geselecteerde omgeving bestaat, is deze selectie uitgeschakeld.

Om de configuratie van de full-stack de productiepijplijn van de codeproductie te beëindigen, volg deze stappen.

1. Op de **Broncode** moet u de volgende opties definiëren.

   * **Bewaarplaats** - Deze optie bepaalt waarvan git repo de pijpleiding de code zou moeten terugwinnen.

   >[!TIP]
   > 
   >Zie het document [Opslagplaatsen toevoegen en beheren](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) voor meer informatie over het toevoegen en beheren van opslagruimten in Cloud Manager.

   * **Git Branch** - Deze optie bepaalt van welke tak in de geselecteerde pijpleiding de code zou moeten terugwinnen.
      * Voer de eerste paar tekens van de naam van de vertakking in en met de functie voor automatisch aanvullen van dit veld kunt u de overeenkomende vertakkingen vinden om u te helpen selecteren.
   * **Configuratie van web-Tier negeren** - Als deze optie is ingeschakeld, implementeert de pijpleiding uw configuratie van de weblaag niet.
   * **Pauzeren vóór implementatie naar productie** - Deze optie pauzeert de pijpleiding alvorens aan productie op te stellen.
   * **Gepland** - Met deze optie kan de gebruiker de geplande implementatie van de productie inschakelen.

   ![Volledige stapelcode](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-fullstack.png)

1. Tik of klik op **Doorgaan** aan de **Experience Audit** kunt u de paden definiëren die altijd moeten worden opgenomen in de controle van de ervaring.

   ![Erviteitscontrole toevoegen](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

1. Verstrek wegen die in de Controle van de Ervaring moeten worden omvat.

   * Zie het document [Ervaring controleren testen](/help/implementing/cloud-manager/experience-audit-testing.md#configuration) voor meer informatie.

1. Klikken **Opslaan** om uw pijpleiding te redden.

De wegen die voor de Controle van de Ervaring worden gevormd worden voorgelegd aan de dienst en worden geëvalueerd volgens de prestaties, de toegankelijkheid, SEO (de Optimalisering van de Motor van het Onderzoek), beste praktijken, en PWA (Progressieve App van het Web) tests wanneer de pijpleiding loopt. Zie [Werken met de resultaten van Experience Audit](/help/implementing/cloud-manager/experience-audit-testing.md) voor meer informatie .

De pijpleiding wordt bewaard en u kunt nu [beheren van uw pijpleidingen](managing-pipelines.md) op de **Pijpleidingen** kaart op **Programmaoverzicht** pagina.

### Gerichte implementatie {#targeted-deployment}

Een gerichte plaatsing stelt code slechts voor geselecteerde delen van uw AEM toepassing op. In een dergelijke implementatie kunt u ervoor kiezen **Inclusief** een van de volgende typen code:

* **Config** - Vorm montages voor de regels van de verkeersfilter op uw AEM milieu.
   * Zie het document [Verkeersfilterregels inclusief WAF-regels](/help/security/traffic-filter-rules-including-waf.md) om te leren hoe u de configuraties in uw opslagplaats kunt beheren, zodat deze correct worden geïmplementeerd.
   * Wanneer het runnen van een gerichte plaatsingspijpleiding, [WAF-configuraties](/help/security/traffic-filter-rules-including-waf.md) zal worden opgesteld, op voorwaarde dat zij aan milieu, bewaarplaats, en tak worden bewaard u in de pijpleiding bepaalde.
   * Op elk ogenblik, kan er slechts één config pijpleiding per milieu zijn.
* **Code frontend** - Configureer JavaScript en CSS voor de voorzijde van de AEM toepassing.
   * Met frontend pijpleidingen wordt meer onafhankelijkheid gegeven aan front-end ontwikkelaars en kan het ontwikkelingsproces worden versneld.
   * Zie het document [Sites ontwikkelen met behulp van de voorste pijplijn](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) hoe dit proces samen met een aantal overwegingen werkt , moet u zich ervan bewust zijn dat dit proces alle mogelijkheden biedt .
* **Config. web** - Configureer de eigenschappen van de dispatcher voor het opslaan, verwerken en leveren van webpagina&#39;s aan de client.
   * Zie het document [CI/CD-pijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) voor meer informatie .
   * Als er voor de geselecteerde omgeving een pijpleiding voor code in de weblaag bestaat, is deze selectie uitgeschakeld.
   * Als u een bestaande full-stack pijpleiding die aan een milieu opstelt hebt, die tot een Web rij config pijpleiding voor het zelfde milieu leidt zal de bestaande configuratie van de Webrij in de full-stack pijpleiding worden genegeerd.

De stappen om de verwezenlijking van uw productie te voltooien, zijn de gerichte plaatsingspijpleiding het zelfde zodra u een plaatsingstype kiest.

1. Kies welk implementatietype u nodig hebt.

![Gerichte implementatieopties](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-targeted-deployment.png)

1. Definieer de **In aanmerking komende implementatieomgevingen**.

   * Als uw pijpleiding een plaatsingspijpleiding is, moet u selecteren aan welke milieu&#39;s het zou moeten opstellen.

1. Onder **Broncode** Definieer de volgende opties:

   * **Bewaarplaats** - Deze optie bepaalt waarvan git repo dat de pijpleiding de code zou moeten terugwinnen.

   >[!TIP]
   > 
   >Zie [Opslagplaatsen toevoegen en beheren](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) zodat u kunt leren om opslagruimten toe te voegen en te beheren in Cloud Manager.

   * **Git Branch** - Deze optie bepaalt waarvan de tak in de geselecteerde pijpleiding de code zou moeten terugwinnen.
      * Voer de eerste paar tekens in van de naam van de vertakking en de functie voor automatisch aanvullen van dit veld. U vindt de overeenkomende vertakkingen die u kunt selecteren.
   * **Codelocatie** - Deze optie bepaalt de weg in de tak van de geselecteerde repo waarvan de pijpleiding de code zou moeten terugwinnen.
   * **Pauzeren vóór implementatie naar productie** - Deze optie pauzeert de pijpleiding alvorens aan productie op te stellen.
   * **Gepland** - Met deze optie kan de gebruiker de geplande implementatie van de productie inschakelen. Alleen beschikbaar voor doelgerichte webimplementaties.

   ![Config-pijplijn](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-config-deployment.png)

1. Klikken **Opslaan**.

De pijpleiding wordt bewaard en u kunt nu [beheren van uw pijpleidingen](managing-pipelines.md) op de **Pijpleidingen** kaart op **Programmaoverzicht** pagina.

## Verzendingspakketten overslaan {#skip-dispatcher-packages}

Als u de pakketten wilt die van de dispatcher als deel van uw pijpleiding worden gebouwd, maar hen niet willen worden gepubliceerd om opslag te bouwen, kunt u het publiceren van hen onbruikbaar maken, die pijpleidingsloopduur kunnen verminderen.

De volgende configuratie om het publiceren van de pakketten van dispatcher onbruikbaar te maken moet via uw project worden toegevoegd `pom.xml` bestand. De variabele is gebaseerd op een omgevingsvariabele die fungeert als een vlag die u in de builcontainer van Cloud Manager kunt instellen om te bepalen wanneer verzenderpakketten moeten worden genegeerd.

```xml
<profile>
  <id>only-include-dispatcher-when-it-isnt-ignored</id>
  <activation>
    <property>
      <name>env.IGNORE_DISPATCHER_PACKAGES</name>
      <value>!true</value>
    </property>
  </activation>
  <modules>
    <module>dispatcher</module>
  </modules>
</profile>
```
