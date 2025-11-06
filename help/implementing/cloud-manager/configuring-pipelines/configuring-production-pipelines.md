---
title: Een productiepijpleiding toevoegen
description: Leer hoe te om een productiepijpleiding toe te voegen om uw code aan productiemilieu's te bouwen en op te stellen.
index: true
exl-id: 67edca16-159e-469f-815e-d55cf9063aa4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1398'
ht-degree: 0%

---


# Een productiepijplijn toevoegen {#configure-production-pipeline}

Leer hoe te om productiepijpleidingen te vormen om uw code aan productiemilieu&#39;s te bouwen en op te stellen. Een productiepijpleiding stelt code eerst aan het werkgebiedmilieu op. Bij goedkeuring, stelt het de zelfde code aan het productiemilieu op.

Een gebruiker moet de **[rol hebben van de Manager van de Plaatsing 0} om productiepijpleidingen te vormen.](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)**

>[!NOTE]
>
>Een productiepijplijn kan pas worden aangelegd nadat het volgende is gebeurd:
>
>* Het programma wordt gemaakt.
>* De Git-opslagplaats heeft minstens één vertakking.
>* De productie- en staging-omgevingen worden gemaakt.

Alvorens u begint om uw code op te stellen, vorm uw pijpleidingsmontages van [!UICONTROL Cloud Manager].

>[!NOTE]
>
>U kunt [ pijpleidingsmontages ](managing-pipelines.md) na de aanvankelijke opstelling uitgeven.

## Een nieuwe productiepijplijn toevoegen {#adding-production-pipeline}

Nadat u uw programma hebt opgezet en minstens één milieu gebruikend [!UICONTROL Cloud Manager] UI hebt, bent u bereid om een productiepijplijn toe te voegen door deze stappen te volgen.

>[!TIP]
>
>Alvorens u een front-end pijpleiding vormt, zie de [ Reis van de Aanmaak van de Plaats van AEM Snelle ](/help/journey-sites/quick-site/overview.md) voor een gids van begin tot eind door het makkelijk te gebruiken hulpmiddel van de Aanmaak van de Plaats van AEM Snelle. Deze reis kan u helpen de front-end ontwikkeling van uw Plaats van AEM stroomlijnen, die u uw plaats met geen AEM achterste-eindkennis laat snel aanpassen.

1. Teken in Cloud Manager bij [ experience.adobe.com ](https://experience.adobe.com).
1. In de **Snelle toegang** sectie, klik **Experience Manager**.
1. In het linkerzijpaneel, klik **Cloud Manager**.
1. Selecteer de gewenste organisatie.
1. Op de **Mijn console van Programma&#39;s**, klik een programma.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma** en klik **toevoegen** om **te selecteren voeg de Pijpleiding van de Productie** toe.

   ![ de kaart van Pijpleidingen op het overzicht van de Manager van het Programma ](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. **voegt de vertoningen van de de dialoogdoos van de Pijpleiding van de Productie** toe. Verstrek de Naam van de a **Pijpleiding** om uw pijpleiding samen met de volgende opties te identificeren. Klik **verdergaan**.

   **Trigger van de Plaatsing** - u hebt de volgende opties wanneer het bepalen van de plaatsingstrekkers om de pijpleiding te beginnen.

   * **Handboek** - Begin manueel de pijpleiding.
   * **op de Veranderingen van het Git** - begint de pijpleiding CI/CD wanneer de bemoeienis aan de gevormde tak van het Git wordt toegevoegd. Met deze optie, kunt u de pijpleiding nog manueel zoals vereist beginnen.

   **Belangrijk Metrisch Gedrag van Mislukt** - tijdens pijpleidingsopstelling of geef uit, heeft de **Manager van de Plaatsing** de optie om het gedrag van de pijpleiding te bepalen wanneer een belangrijke mislukking in om het even welke kwaliteitspoorten wordt ontmoet. De beschikbare opties zijn:

   * **vraag telkens als** - Gebrek het plaatsen. Het vereist handmatige ingrepen in elke belangrijke mislukking.
   * **onmiddellijk het Eindigen** - als geselecteerd, wordt de pijpleiding geannuleerd wanneer een belangrijke mislukking voorkomt. Dit proces emuleert in wezen een gebruiker manueel die elke mislukking verwerpt.
   * **gaat onmiddellijk** - als geselecteerd voort, gaat de pijpleiding automatisch wanneer een belangrijke mislukking voorkomt. Dit proces emuleert hoofdzakelijk een gebruiker manueel goedkeurend elke mislukking.

   ![ de pijpleidingsconfiguratie van de Productie ](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-configuration.png)

1. Op het **lusje van de Code van Source**, selecteer welk type van code de pijpleiding zou moeten verwerken.

   * **[vorm een volledige pijpleiding van de stapelcode](#full-stack-code)**
   * **[vorm een gerichte plaatsingspijpleiding](#targeted-deployment)**

Zie [ CI/CD Pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) voor meer informatie over de types van pijpleidingen.

De stappen om de verwezenlijking van uw productiepijplijn te voltooien variëren afhankelijk van het type van broncode u selecteerde. Volg de verbindingen hierboven om aan de volgende sectie van dit document te springen zodat kunt u de configuratie van uw pijpleiding voltooien.

### Vorm een volledige pijpleiding van de stapelcode {#full-stack-code}

Een full-stack codepijplijn implementeert tegelijkertijd back-end en front-end code builds die een of meer AEM-servertoepassingen bevatten samen met de configuratie HTTPD/Dispatcher.

>[!NOTE]
>
>Als er al een &#39;full-stack&#39;-codepijplijn voor de geselecteerde omgeving bestaat, is deze selectie uitgeschakeld.

**om een volledige pijpleiding van de stapelcode te vormen:**

1. Voor het **lusje van de Code van Source**, bepaal de volgende opties.

   * **Bewaarplaats** - bepaalt waarvan de bewaarplaats van het Git dat de pijpleiding de code zou moeten terugwinnen.

   >[!TIP]
   > 
   >Zie [ Opslagplaatsen ](/help/implementing/cloud-manager/managing-code/managing-repositories.md) toevoegen en beheren om te leren hoe te om bewaarplaatsen in Cloud Manager toe te voegen en te beheren.

   * **Tak van het Git** - bepaalt van welke tak de geselecteerde pijpleiding de code zou moeten terugwinnen.
Voer de eerste paar tekens van de naam van de vertakking in en met de functie voor automatisch aanvullen van dit veld zoekt u de overeenkomende vertakkingen om u te helpen selecteren.
   * **negeert de Configuratie van de Rij van het Web** - wanneer gecontroleerd, stelt de pijpleiding uw configuratie van de Webrij niet op.
   * **Pauze alvorens aan Productie** op te stellen - pauzeert de pijpleiding alvorens aan productie op te stellen.
   * **Gepland** - laat de gebruiker de geplande productieplaatsing toelaten.

   ![ Volledige stapelcode ](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-fullstack.png)

1. Klik **verdergaan** om aan het **lusje van de Controle van de Ervaring** te voorschijn te komen waar u de wegen kunt bepalen die altijd in de Controle van de Ervaring zouden moeten worden omvat.

   ![ voeg de Controle van de Ervaring toe ](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

1. Verstrek wegen die in de Controle van de Ervaring moeten worden omvat.

   * Zie [ het Testen van de Controle van de Ervaring ](/help/implementing/cloud-manager/reports/report-experience-audit.md#configuration) voor details.

1. Klik **sparen** om uw pijpleiding te bewaren.

Wanneer de pijpleiding loopt, worden de wegen die voor de Controle van de Ervaring worden gevormd voorgelegd en worden geëvalueerd gebaseerd op prestaties, toegankelijkheid, SEO, beste praktijken, en de tests van PWA. Voor meer details, zie [ Begrijpingsresultaten van de Controle van de Ervaring ](/help/implementing/cloud-manager/reports/report-experience-audit.md).

De pijpleiding wordt bewaard en u kunt uw pijpleidingen [ op de ](managing-pipelines.md) Pijpleidingen **kaart op de** pagina van het Overzicht van het Programma **nu beheren.**

### Vorm een gerichte plaatsingspijpleiding {#targeted-deployment}

Een gerichte implementatie implementeert alleen code voor geselecteerde onderdelen van uw AEM-toepassing. In zulk een plaatsing, kunt u verkiezen om **** één van de volgende soorten code te omvatten:

* **Config** - vorm montages voor diverse eigenschappen in uw milieu van AEM.
   * Zie [ Gebruikend Pijpleidingen Config ](/help/operations/config-pipeline.md) voor een lijst van gesteunde configuraties, die logboek het door:sturen, zuivert-verwante onderhoudstaken, en diverse configuraties CDN omvatten, en om hen in uw bewaarplaats te beheren zodat worden zij behoorlijk opgesteld.
   * Wanneer het runnen van een gerichte plaatsingspijpleiding, worden de configuraties opgesteld, mits zij aan het milieu, de bewaarplaats, en de tak worden bewaard die in de pijpleiding wordt bepaald.
   * Op elk ogenblik, kan er slechts één config pijpleiding per milieu zijn.
* **vorm Edge Delivery Services config pijpleiding** - de Pijpleidingen van de Configuratie van Edge Delivery hebben geen afzonderlijke ontwikkeling, het opvoeren, en productiemilieu&#39;s. In AEM as a Cloud Service worden wijzigingen doorgevoerd in ontwikkelings-, fase- en productieniveaus. Een Edge Delivery Configuration Pipeline past daarentegen zijn configuratie rechtstreeks toe op alle Edge Delivery Sites-domeinen die in Cloud Manager zijn geregistreerd. Meer leren, zie [ een Pijpleiding van Edge Delivery ](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md) toevoegen.
* **Voorste Code van het Eind** - vorm JavaScript en CSS voor het vooreind van uw toepassing van AEM.
   * Met frontend pijpleidingen wordt meer onafhankelijkheid gegeven aan front-end ontwikkelaars en kan het ontwikkelingsproces worden versneld.
   * Zie het document [ Ontwikkelend Plaatsen met de Voorste-Eind Pijpleiding ](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) voor hoe dit proces samen met sommige overwegingen werkt om zich bewust te zijn van om het volledige potentieel uit dit proces te krijgen.
* **Config van de Rij van het Web** - Vorm de eigenschappen van Dispatcher om, Web-pagina&#39;s op te slaan te verwerken en te leveren aan de cliënt.
   * Zie het document [ CI/CD Pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) voor meer details.
   * Als er voor de geselecteerde omgeving een pijpleiding voor code in de weblaag bestaat, is deze selectie uitgeschakeld.
   * Als u een Web rij config pijpleiding voor een milieu met een bestaande full-stack pijpleiding creeert, wordt de configuratie van de Webrij in de full-stack pijpleiding genegeerd. Deze wijziging heeft alleen invloed op de configuratie van de weblaag in die omgeving.

>[!NOTE]
>
>De de rij en config van het Web pijpleidingen worden niet gesteund met privé bewaarplaatsen. Zie [ Toevoegend Privé Bewaarplaatsen in Cloud Manager ](/help/implementing/cloud-manager/managing-code/private-repositories.md) voor details en de volledige lijst van beperkingen.

**om een gerichte plaatsingspijpleiding te vormen:**

1. Kies welk implementatietype u nodig hebt.

![ gerichte plaatsingsopties ](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-targeted-deployment.png)

1. Bepaal de **In aanmerking komende Milieu&#39;s van de Plaatsing**.

   * Als uw pijpleiding een plaatsingspijpleiding is, moet u selecteren aan welke milieu&#39;s het zou moeten opstellen.

1. Onder **Code van Source**, bepaal de volgende opties:

   * **Bewaarplaats** - Deze optie bepaalt waarvan git repo dat de pijpleiding de code zou moeten terugwinnen.

   >[!TIP]
   > 
   >Zie [ Toevoegend en het Leiden Bewaarplaatsen ](/help/implementing/cloud-manager/managing-code/managing-repositories.md) zodat kunt u leren om bewaarplaatsen in Cloud Manager toe te voegen en te beheren.

   * **Tak van het Git** - Deze optie bepaalt waarvan de tak in de geselecteerde pijpleiding de code zou moeten terugwinnen.
      * Voer de eerste paar tekens in van de naam van de vertakking en de functie voor automatisch aanvullen van dit veld. U vindt de overeenkomende vertakkingen die u kunt selecteren.
   * **Plaats van de Code** - Deze optie bepaalt de weg in de tak van de geselecteerde repo waarvan de pijpleiding de code zou moeten terugwinnen.
   * **Pauze alvorens aan Productie** op te stellen - deze optie pauzeert de pijpleiding alvorens aan productie op te stellen.
   * **Gepland** - laat de gebruiker de geplande productieplaatsing toelaten. Alleen beschikbaar voor doelgerichte webimplementaties.

   ![ Config pijpleiding ](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-config-deployment.png)

1. Klik **sparen**.

De pijpleiding wordt bewaard en u kunt uw pijpleidingen [ op de ](managing-pipelines.md) Pijpleidingen **kaart op de** pagina van het Overzicht van het Programma **nu beheren.**

## Dispatcher-pakketten overslaan {#skip-dispatcher-packages}

Als u Dispatcher-pakketten in uw pijplijn wilt bouwen zonder deze te publiceren om opslag te maken, kunt u de publicatieoptie uitschakelen. Dit kan helpen de runtime van de pijpleiding verminderen.

De volgende configuratie om het publiceren van Dispatcher-pakketten uit te schakelen, moet via het `pom.xml` -projectbestand worden toegevoegd. Een omgevingsvariabele dient als een vlag die u instelt in de Cloud Manager-constructiecontainer om te bepalen wanneer Dispatcher-pakketten moeten worden genegeerd.

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
