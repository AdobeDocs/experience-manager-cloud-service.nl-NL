---
title: Productiepijpleidingen configureren
description: Leer hoe te om productiepijpleidingen te vormen om uw code aan productiemilieu's te bouwen en op te stellen.
index: true
exl-id: 67edca16-159e-469f-815e-d55cf9063aa4
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '1509'
ht-degree: 0%

---


# Een productiepijpleiding configureren {#configure-production-pipeline}

Leer hoe te om de pijpleidingen van de Productie te vormen om uw code aan de milieu&#39;s van de Productie te bouwen en op te stellen. Een productiepijpleiding stelt code eerst aan het milieu van het Stadium op, en op goedkeuring stelt de zelfde code aan het milieu van de Productie op.

Een gebruiker moet beschikken over de **[Implementatiebeheer](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** rol om productiepijpleidingen te configureren.

>[!NOTE]
>
>Een productiepijpleiding kan niet worden opgezet tot de programmaverwezenlijking volledig is, heeft een git bewaarplaats minstens één tak, en een productie en het opvoeren milieu wordt geplaatst.

Alvorens u begint uw code op te stellen, moet u uw pijpleidingsmontages van vormen [!UICONTROL Cloud Manager].

>[!NOTE]
>
>U kunt [pijpleidingsinstellingen bewerken](managing-pipelines.md) na de eerste installatie.

## Een nieuwe productiepijpleiding toevoegen {#adding-production-pipeline}

Als u uw programma hebt ingesteld en ten minste één omgeving hebt die de [!UICONTROL Cloud Manager] UI, bent u bereid om een productiepijplijn toe te voegen door deze stappen te volgen.

>[!TIP]
>
>Alvorens u een front-end pijpleiding vormt, zie [Reis voor snel maken van site AEM](/help/journey-sites/quick-site/overview.md) voor een end-to-end handleiding met het gebruiksvriendelijke AEM gereedschap Snel site maken. Deze reis zal u helpen de front-end ontwikkeling van uw AEM Plaats stroomlijnen, die u toestaat om uw plaats snel aan te passen zonder AEM achterste-eindkennis.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Pijpleidingen** kaart van **Programmaoverzicht** pagina en klik op **Toevoegen** om **Productiepijpleiding toevoegen**.

   ![De pijplijnkaart op het overzicht van de Manager van het Programma](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. De **Productiepijpleiding toevoegen** wordt weergegeven. Een **Naam pijpleiding** om uw pijpleiding samen met de volgende opties te identificeren. Klikken **Doorgaan**.

   **Implementatieactivering** - U hebt de volgende opties wanneer het bepalen van de plaatsingstrekkers om de pijpleiding te beginnen.

   * **Handmatig** - Gebruik deze optie om de pijpleiding manueel te beginnen.
   * **Wijzigingen in Git** - Deze opties beginnen de pijpleiding CI/CD wanneer de bemoeienis aan de gevormde git tak wordt toegevoegd. Met deze optie, kunt u de pijpleiding nog manueel zoals vereist beginnen.

   **Belangrijk gedrag metrische fouten** - Tijdens het instellen of bewerken van pijpleidingen **Implementatiebeheer** heeft de optie om het gedrag van de pijpleiding te bepalen wanneer een belangrijke mislukking in om het even welke kwaliteitspoorten wordt ontmoet. De beschikbare opties zijn:

   * **Telkens vragen** - Dit is de standaardinstelling en u moet handmatig ingrijpen bij belangrijke fouten.
   * **Direct mislukken** - Indien geselecteerd, wordt de pijpleiding geannuleerd wanneer een belangrijke mislukking voorkomt. Dit is in feite het emuleren van een gebruiker die elke fout handmatig afwijst.
   * **Direct doorgaan** - Indien geselecteerd, zal de pijpleiding automatisch te werk gaan wanneer een belangrijke mislukking voorkomt. Dit emuleert hoofdzakelijk een gebruiker manueel goedkeurend elke mislukking.

   ![Configuratie productiepijplijn](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-configuration.png)

1. Op de **Broncode** tabblad moet u bepalen waar de pijplijn zijn code moet terugwinnen en welk type code het is.

   * **[Code frontend](#front-end-code)**
   * **[Volledige stapelcode](#full-stack-code)**
   * **[Config. web](#web-tier-config)**

De stappen om de verwezenlijking van uw productiepijplijn te voltooien variëren afhankelijk van de optie voor **Broncode** geselecteerd. Volg de verbindingen hierboven om aan de volgende sectie van dit document te springen om de configuratie van uw pijpleiding te voltooien.

### Code frontend {#front-end-code}

Een front-end codepijpleiding stelt front-end code op bouwt die één of meerdere cliënt-kant toepassingen UI bevatten. Zie het document [CI/CD-pijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) voor meer informatie over dit type pijpleiding .

Om de configuratie van de front eind codeproductiepijplijn te beëindigen, volg deze stappen.

1. Op de **Broncode** moet u de volgende opties definiëren.

   * **Bewaarplaats** - Deze optie bepaalt waarvan git repo de pijpleiding de code zou moeten terugwinnen.

   >[!TIP]
   > 
   >Zie het document [Opslagplaatsen toevoegen en beheren](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) voor meer informatie over het toevoegen en beheren van opslagruimten in Cloud Manager.

   * **Git Branch** - Deze optie bepaalt van welke tak in de geselecteerde pijpleiding de code zou moeten terugwinnen.
      * Voer de eerste paar tekens van de naam van de vertakking in en met de functie voor automatisch aanvullen van dit veld kunt u de overeenkomende vertakkingen vinden om u te helpen selecteren.
   * **Codelocatie** - Deze optie bepaalt de weg in de tak van de geselecteerde repo waarvan de pijpleiding de code zou moeten terugwinnen.
   * **Pauzeren vóór implementatie naar productie** - Deze optie pauzeert de pijpleiding alvorens aan productie op te stellen.

   ![Voorste eindcode](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-frontend.png)

1. Klikken **Opslaan** om uw pijpleiding te redden.

De pijpleiding wordt bewaard en u kunt nu [beheren van uw pijpleidingen](managing-pipelines.md) op de **Pijpleidingen** kaart op **Programmaoverzicht** pagina.

### Volledige stapelcode {#full-stack-code}

Een full-stack codepijpleiding stelt gelijktijdig achterste en front-end codebouwstijlen op die één of meerdere AEM servertoepassingen samen met configuratie HTTPD/Dispatcher bevatten. Zie het document [CI/CD-pijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline) voor meer informatie over dit type pijpleiding .

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
   * **Codelocatie** - Deze optie bepaalt de weg in de tak van de geselecteerde repo waarvan de pijpleiding de code zou moeten terugwinnen.
   * **Pauzeren vóór implementatie naar productie** - Deze optie pauzeert de pijpleiding alvorens aan productie op te stellen.
   * **Gepland** - Met deze optie kan de gebruiker de geplande implementatie van de productie inschakelen.

   ![Volledige stapelcode](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-fullstack.png)

1. Klikken **Doorgaan** aan **Experience Audit** kunt u de paden definiëren die altijd moeten worden opgenomen in de controle van de ervaring.

   ![Erviteitscontrole toevoegen](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

1. Geef een pad op dat moet worden opgenomen in de Experience Audit.

   * Pagina-paden moeten beginnen met `/`.
   * Als u bijvoorbeeld `https://wknd.site/us/en/about-us.html` in de Controle van de Ervaring, ga de weg in `/us/en/about-us.html`.

   ![Een pad definiëren voor de Experience Audit](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit3.png)

1. Klikken **Pagina toevoegen** en het pad wordt automatisch ingevuld met het adres van de omgeving en toegevoegd aan de padlijst.

   ![Pad naar tabel opslaan](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit4.png)

1. U kunt paden naar wens toevoegen door de vorige twee stappen te herhalen.

   * U kunt maximaal 25 paden toevoegen.
   * Als u geen paden definieert, wordt de homepage van de site standaard opgenomen in de Experience Audit.

1. Klikken op **Opslaan** om uw pijpleiding te redden.

De wegen die voor de Controle van de Ervaring worden gevormd worden voorgelegd aan de dienst en worden geëvalueerd volgens de prestaties, de toegankelijkheid, SEO (de Optimalisering van de Motor van het Onderzoek), beste praktijken, en PWA (Progressieve App van het Web) tests wanneer de pijpleiding loopt. Zie [Werken met de resultaten van Experience Audit](/help/implementing/cloud-manager/experience-audit-testing.md) voor meer informatie .

De pijpleiding wordt bewaard en u kunt nu [beheren van uw pijpleidingen](managing-pipelines.md) op de **Pijpleidingen** kaart op **Programmaoverzicht** pagina.

### Config. web {#web-tier-config}

Een configuratiepijplijn van de Webrij stelt configuraties HTTPD/Dispatcher op. Zie het document [CI/CD-pijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipeline) voor meer informatie over dit type pijpleiding .

Om de configuratie van de full-stack de productiepijplijn van de codeproductie te beëindigen, volg deze stappen.

1. Op de **Broncode** moet u de volgende opties definiëren.

   * **Bewaarplaats** - Deze optie bepaalt waarvan git repo de pijpleiding de code zou moeten terugwinnen.

   >[!TIP]
   > 
   >Zie het document [Opslagplaatsen toevoegen en beheren](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) voor meer informatie over het toevoegen en beheren van opslagruimten in Cloud Manager.

   * **Git Branch** - Deze optie bepaalt van welke tak in de geselecteerde pijpleiding de code zou moeten terugwinnen.
      * Voer de eerste paar tekens van de naam van de vertakking in en met de functie voor automatisch aanvullen van dit veld kunt u de overeenkomende vertakkingen vinden om u te helpen selecteren.
   * **Codelocatie** - Deze optie bepaalt de weg in de tak van de geselecteerde repo waarvan de pijpleiding de code zou moeten terugwinnen.
      * Voor configuratieleidingen voor het web is dit meestal het pad dat `conf.d`, `conf.dispatcher.d`, en `opt-in` directory&#39;s.
      * Als de projectstructuur bijvoorbeeld is gegenereerd op basis van de [Projectarchetype AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=en) het pad zou `/dispatcher/src`.
   * **Pauzeren vóór implementatie naar productie** - Deze optie pauzeert de pijpleiding alvorens aan productie op te stellen.
   * **Gepland** - Met deze optie kan de gebruiker de geplande implementatie van de productie inschakelen.

   ![Code op de weblijst](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-webtier.png)

1. Klikken **Opslaan** om uw pijpleiding te redden.

>[!NOTE]
>
>Als u een bestaande full-stack pijpleiding die aan een milieu opstelt hebt, die tot een Web rij config pijpleiding voor het zelfde milieu leidt zal de bestaande configuratie van de Webrij in de full-stack pijpleiding worden genegeerd.

De pijpleiding wordt bewaard en u kunt nu [beheren van uw pijpleidingen](managing-pipelines.md) op de **Pijpleidingen** kaart op **Programmaoverzicht** pagina.

## Sites ontwikkelen met behulp van de voorste pijplijn {#developing-with-front-end-pipeline}

Met frontend pijpleidingen wordt meer onafhankelijkheid gegeven aan front-end ontwikkelaars en kan het ontwikkelingsproces worden versneld.

Raadpleeg het document [Sites ontwikkelen met behulp van de voorste pijplijn](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) hoe dit proces samen met enkele overwegingen werkt , moet u zich ervan bewust zijn dat dit proces alle mogelijkheden biedt .

## Verzendpakketten overslaan {#skip-dispatcher-packages}

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
