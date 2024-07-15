---
title: Niet-productiepijpleidingen configureren
description: Leer hoe u niet-productiepijpleidingen configureert om de kwaliteit van uw code te testen voordat u deze implementeert in productieomgevingen.
index: true
exl-id: eba608eb-a19e-4bff-82ff-05860ceabe6e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: a5179851af8ec88e23d79a74265b10cbce2d50f1
workflow-type: tm+mt
source-wordcount: '1400'
ht-degree: 0%

---


# Niet-productiepijpleidingen configureren {#configuring-non-production-pipelines}

Leer hoe u niet-productiepijpleidingen configureert om de kwaliteit van uw code te testen voordat u deze implementeert in productieomgevingen.

Een gebruiker moet de ](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)**rol hebben van de Manager van de Plaatsing 0} om niet-productiepijpleidingen te vormen.**[

## Niet-productiepijpleidingen {#non-production-pipelines}

Naast [ productiepijpleidingen ](#configuring-production-pipelines.md) die aan stagings en productiemilieu&#39;s opstelt, kunt u niet-productiepijpleidingen ook opstelling om uw code te bevestigen.

Er zijn twee soorten niet-productiepijpleidingen:

* **Pijpleidingen van de Kwaliteit van de Code** - Deze in werking gestelde codekwaliteit scant op de code in een git tak en voert de bouw en de stappen van de codekwaliteit uit.
* **Pijpleidingen van de Plaatsing** - naast het uitvoeren van de bouw en de stappen van de codekwaliteit zoals de pijpleidingen van de codekwaliteit, stellen deze pijpleidingen de code aan een niet productiemilieu op.

>[!NOTE]
>
>U kunt [ pijpleidingsmontages ](managing-pipelines.md) na de aanvankelijke opstelling uitgeven.

## Een nieuwe niet-productiepijplijn toevoegen {#adding-non-production-pipeline}

Zodra u opstelling uw programma hebt en minstens één milieu gebruikend Cloud Manager UI, bent u bereid om een niet productiepijplijn toe te voegen door deze stappen te volgen.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Heb toegang tot **Pijpleidingen** kaart van het het huisscherm van Cloud Manager. Klik **+ voeg** toe en selecteer **toevoegen niet-Productiepijpleiding**.

   ![ voeg niet-productiepijpleiding ](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png) toe

1. Op het **lusje van de Configuratie** van **voeg de dialoog van de Pijl van de Niet-Productie** toe, selecteer het type van niet-productiepijplijn u met toe te voegen.

   * **Pijpleiding van de Kwaliteit van de Code** - creeer een pijpleiding die uw code bouwt, eenheidstests in werking stelt, en codekwaliteit evalueert maar niet opstelt.
   * **Pijpleiding van de Plaatsing** - creeer een pijpleiding die uw code bouwt, eenheidstests in werking stelt, codekwaliteit evalueert, en aan een milieu opstelt.

   ![ toevoegen de pijpleidingsdialoog van de Niet-Productie ](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Verstrek de Naam van de Pijpleiding van de a **Niet-Productie** om uw pijpleiding samen met de volgende extra informatie te identificeren.

   * **Trigger van de Plaatsing** - u hebt de volgende opties wanneer het bepalen van de plaatsingstrekkers om de pijpleiding te beginnen.

      * **Handboek** - gebruik deze optie om de pijpleiding manueel te beginnen.
      * **op de Veranderingen van het Git** - Deze optie begint de pijpleiding CI/CD wanneer de bemoeienis aan de gevormde git tak wordt toegevoegd. Met deze optie, kunt u de pijpleiding nog manueel zoals vereist beginnen.

1. Als u verkiest om a **Pijpleiding van de Plaatsing te creëren**, moet u het **Belangrijke Metrische Gedrag van Mislukt** ook bepalen.

   * **vraag telkens als** - dit gedrag is het gebrek plaatsend en vereist handinterventie op om het even welke belangrijke mislukking.
   * **onmiddellijk het Eindigen** - als geselecteerd, wordt de pijpleiding geannuleerd wanneer een belangrijke mislukking voorkomt. In feite emuleert het een gebruiker handmatig elke fout af.
   * **gaat onmiddellijk** - als geselecteerd, de pijpleidingsprocedures automatisch wanneer een belangrijke mislukking voorkomt. Het emuleert hoofdzakelijk een gebruiker manueel goedkeurend elke mislukking.

1. Klik **verdergaan**.

1. Op het **lusje van de Code van Source** van **voeg niet-Productie pijplijn** dialoog toe, moet u selecteren welk type van code de pijpleiding zou moeten verwerken.

   * **[Volledige Code van de Stapel](#full-stack-code)**
   * **[gerichte plaatsing](#targeted-deployment)**

Zie [ CI/CD Pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) voor meer informatie over de types van pijpleidingen.

De stappen om de verwezenlijking van uw niet productiepijplijn te voltooien variëren afhankelijk van het type van broncode u selecteerde. Volg de verbindingen hierboven om aan de volgende sectie van dit document te springen zodat kunt u de configuratie van uw pijpleiding voltooien.

### Volledige stapelcode {#full-stack-code}

Een full-stack codepijplijn implementeert tegelijkertijd back-end en front-end code builds die een of meer AEM servertoepassingen bevatten samen met de configuratie HTTPD/Dispatcher.

>[!NOTE]
>
>Als er al een &#39;full-stack&#39;-codepijplijn voor de geselecteerde omgeving bestaat, is deze selectie uitgeschakeld.

Om de configuratie van de full-stack code non-production pijpleiding te beëindigen, volg deze stappen.

1. Op het **lusje van de Code van Source**, moet u de volgende opties bepalen.

   * **In aanmerking komende Milieu&#39;s van de Plaatsing** - als uw pijpleiding een plaatsingspijpleiding is, moet u selecteren aan welke milieu&#39;s het zou moeten opstellen.
   * **Bewaarplaats** - Deze optie bepaalt waarvan git repo dat de pijpleiding de code zou moeten terugwinnen.

   >[!TIP]
   > 
   >Zie [ Toevoegend en het Leiden Bewaarplaatsen ](/help/implementing/cloud-manager/managing-code/managing-repositories.md) zodat kunt u leren om bewaarplaatsen in Cloud Manager toe te voegen en te beheren.

   * **Tak van het Git** - Deze optie bepaalt waarvan de tak in de geselecteerde pijpleiding de code zou moeten terugwinnen.
      * Voer de eerste paar tekens in van de naam van de vertakking en de functie voor automatisch aanvullen van dit veld. Hiermee kunt u de overeenkomende vertakkingen zoeken die u kunt selecteren.
   * **negeert de Configuratie van de Rij van het Web** - wanneer gecontroleerd, stelt de pijpleiding uw configuratie van de Webrij niet op.
   * **Pijpleiding** - als uw pijpleiding een plaatsingspijpleiding is, kunt u verkiezen om een het testen fase in werking te stellen. Controleer de opties die u in deze fase wilt inschakelen. Als geen van de opties wordt geselecteerd, wordt de het testen fase niet getoond tijdens de looppas van de pijpleiding.

      * **Functionele het Testen van het Product** - voer [ product functionele tests ](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing) tegen het ontwikkelmilieu uit.
      * **Functionele het Testen van de Douane** - voer [ douane functionele tests ](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) tegen het ontwikkelmilieu uit.
      * **het Testen van de Douane UI** - voer [ tests van douaneUI ](/help/implementing/cloud-manager/ui-testing.md) voor douanetoepassingen uit.
      * **Controle van de Ervaring** - voer [ Controle van de Ervaring uit ](/help/implementing/cloud-manager/experience-audit-testing.md)

   ![ volledig-stapelpijpleiding ](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Klik **sparen**.

De pijpleiding wordt bewaard en u kunt uw pijpleidingen ](managing-pipelines.md) op de **Pijpleidingen** kaart op de **pagina van het Overzicht van het Programma** nu beheren.[

### Gerichte implementatie {#targeted-deployment}

Een gerichte plaatsing stelt code slechts voor geselecteerde delen van uw AEM toepassing op. In zulk een plaatsing kunt u verkiezen om **** één van de volgende soorten code te omvatten:

* **Config** - vorm montages voor de regels van de verkeersfilter op uw AEM milieu.
   * Zie de regels van de Filter van het document [ Verkeer met inbegrip van de Regels van WAF ](/help/security/traffic-filter-rules-including-waf.md) leren hoe te om de regels van de verkeersfilter in uw bewaarplaats te beheren zodat worden zij behoorlijk opgesteld.
   * Wanneer het runnen van een gerichte plaatsingspijpleiding, configuraties [ zoals configuraties WAF ](/help/security/traffic-filter-rules-including-waf.md) zullen worden opgesteld, op voorwaarde dat zij aan milieu, bewaarplaats, en tak worden bewaard u in de pijpleiding bepaalde.
   * Op elk ogenblik, kan er slechts één config pijpleiding per milieu zijn.
* **Voorste Code van het Eind** - vorm JavaScript en CSS voor het vooreind van uw AEM toepassing.
   * Met frontend pijpleidingen wordt meer onafhankelijkheid gegeven aan front-end ontwikkelaars en kan het ontwikkelingsproces worden versneld.
   * Zie het document [ Ontwikkelend Plaatsen met de Voorste-Eind Pijpleiding ](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) voor hoe dit proces samen met sommige overwegingen werkt om zich bewust te zijn van om het volledige potentieel uit dit proces te krijgen.
* **Config van de Rij van het Web** - vorm dispatcheigenschappen om, Web-pagina&#39;s op te slaan, te verwerken en te leveren aan de cliënt.
   * Zie het document [ CI/CD Pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) voor meer details.
   * Als er voor de geselecteerde omgeving een pijpleiding voor code in de weblaag bestaat, is deze selectie uitgeschakeld.
   * Als u een bestaande full-stack pijpleiding die aan een milieu opstelt hebt, die tot een Web rij config pijpleiding voor het zelfde milieu leidt zal de bestaande configuratie van de Webrij in de full-stack pijpleiding worden genegeerd.

>[!NOTE]
>
>De de rij en config van het Web pijpleidingen worden niet gesteund met privé bewaarplaatsen. Gelieve te zien het document [ Toevoegend Privé Bewaarplaatsen in Cloud Manager ](/help/implementing/cloud-manager/managing-code/private-repositories.md) voor details en de volledige lijst van beperkingen.

De stappen om de verwezenlijking van uw niet-productie, gerichte plaatsingspijpleiding te voltooien zijn het zelfde zodra u een plaatsingstype kiest.

1. Kies welk implementatietype u nodig hebt.

![ gerichte plaatsingsopties ](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-targeted-deployment.png)

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
   * **Pijpleiding** - voor front-end niet productiepijpleidingen, hebt u de optie om **[Controle van de Ervaring toe te laten.](/help/implementing/cloud-manager/experience-audit-testing.md)**

   ![ Config pijpleiding ](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config-deployment-experience-audit.png)

1. Als u de Controle van de Ervaring toeliet, blijf of klik **** {om aan de **Controle van de Ervaring** tabel verder te gaan waar u de wegen kunt bepalen die altijd in de Controle van de Ervaring zouden moeten worden omvat.

   * Als u **de Controle van de Ervaring** toeliet, gelieve de controle van de de 2} Ervaring van het document ](/help/implementing/cloud-manager/experience-audit-testing.md#configuration) voor details op te zien hoe te vormen.[
   * Als u dit niet hebt gedaan, slaat u deze stap over.

1. Tik of klik **sparen** om de pijpleiding te bewaren.

De pijpleiding wordt bewaard en u kunt uw pijpleidingen ](managing-pipelines.md) op de **Pijpleidingen** kaart op de **pagina van het Overzicht van het Programma** nu beheren.[

## Dispatcher-pakketten overslaan {#skip-dispatcher-packages}

Als u de pakketten van Dispatcher als deel van uw pijpleiding wilt worden gebouwd, maar hen niet wilt publiceren om opslag te bouwen, kunt u het publiceren van hen onbruikbaar maken, die pijpleidingsloopduur kunnen verminderen.

De volgende configuratie om het publiceren van Dispatcher-pakketten uit te schakelen, moet via het `pom.xml` -projectbestand worden toegevoegd. Het is gebaseerd op een omgevingsvariabele, die fungeert als een markering die u in de Cloud Manager-constructiecontainer kunt instellen om te bepalen wanneer Dispatcher-pakketten moeten worden genegeerd.

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
