---
title: Een niet-productiepijplijn toevoegen
description: Leer hoe te om een niet productiepijplijn toe te voegen om de kwaliteit van uw code te testen alvorens aan productiemilieu's op te stellen.
index: true
exl-id: eba608eb-a19e-4bff-82ff-05860ceabe6e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 07ed9bd6d9830bc9120b59cab43f834ef8620709
workflow-type: tm+mt
source-wordcount: '1466'
ht-degree: 0%

---


# Een niet-productiepijpleiding toevoegen {#configuring-non-production-pipelines}

Leer hoe u niet-productiepijpleidingen configureert om de kwaliteit van uw code te testen voordat u deze implementeert in productieomgevingen.

Een gebruiker moet de **[rol hebben van de Manager van de Plaatsing 0&rbrace; om niet-productiepijpleidingen te vormen.](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)**

## Niet-productiepijpleidingen {#non-production-pipelines}

Naast [&#x200B; productiepijpleidingen &#x200B;](#configuring-production-pipelines.md) die aan stagings en productiemilieu&#39;s opstelt, kunt u niet-productiepijpleidingen ook opstelling om uw code te bevestigen.

Er zijn twee soorten niet-productiepijpleidingen:

* **Pijpleidingen van de Kwaliteit van de Code** - Deze in werking gestelde codekwaliteit scant op de code in een tak van het Git en voert de bouw en de stappen van de codekwaliteit uit.
* **Pijpleidingen van de Plaatsing** - Naast het uitvoeren van de bouw en de stappen van de codekwaliteit zoals de pijpleidingen van de codekwaliteit, stellen deze pijpleidingen de code aan een niet productiemilieu op.

>[!NOTE]
>
>U kunt [&#x200B; pijpleidingsmontages &#x200B;](managing-pipelines.md) na de aanvankelijke opstelling uitgeven.

## Een nieuwe niet-productiepijplijn toevoegen {#adding-non-production-pipeline}

Zodra u opstelling uw programma hebt en minstens één milieu gebruikend Cloud Manager UI, bent u bereid om een niet productiepijplijn toe te voegen door deze stappen te volgen.

1. Teken in Cloud Manager bij [&#x200B; experience.adobe.com &#x200B;](https://experience.adobe.com).
1. In de **Snelle toegang** sectie, klik **Experience Manager**.
1. In het linkerzijpaneel, klik **Cloud Manager**.
1. Selecteer de gewenste organisatie.
1. Op de **Mijn console van Programma&#39;s**, klik een programma.

1. Heb toegang tot **Pijpleidingen** kaart van het het huisscherm van Cloud Manager. Klik **+ voeg** toe en selecteer **toevoegen niet-Productiepijpleiding**.

   ![&#x200B; voeg niet-productiepijpleiding &#x200B;](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png) toe

1. Op het **lusje van de Configuratie** van **voeg de dialoog van de Pijl van de Niet-Productie** toe, selecteer het type van niet-productiepijplijn u met toe te voegen.

   * **Pijpleiding van de Kwaliteit van de Code** - creeer een pijpleiding die uw code bouwt, eenheidstests in werking stelt, en codekwaliteit evalueert maar niet opstelt.
   * **Pijpleiding van de Plaatsing** - creeer een pijpleiding die uw code bouwt, eenheidstests in werking stelt, codekwaliteit evalueert, en aan een milieu opstelt.

   ![&#x200B; toevoegen de pijpleidingsdialoog van de Niet-Productie &#x200B;](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Verstrek de Naam van de Pijpleiding van de a **Niet-Productie** om uw pijpleiding samen met de volgende extra informatie te identificeren.

   * **Trigger van de Plaatsing** - u hebt de volgende opties wanneer het bepalen van de plaatsingstrekkers om de pijpleiding te beginnen.

      * **Handboek** - gebruik deze optie om de pijpleiding manueel te beginnen.
      * **op de Veranderingen van het Git** - Deze optie begint de pijpleiding CI/CD wanneer de bemoeienis aan de gevormde tak van het Git wordt toegevoegd. Met deze optie, kunt u de pijpleiding nog manueel zoals vereist beginnen.

1. Als u verkiest om a **Pijpleiding van de Plaatsing te creëren**, moet u het **Belangrijke Metrische Gedrag van Mislukt** ook bepalen.

   * **vraag telkens als** - dit gedrag is het gebrek plaatsend en vereist handinterventie op om het even welke belangrijke mislukking.
   * **onmiddellijk het Eindigen** - als geselecteerd, wordt de pijpleiding geannuleerd wanneer een belangrijke mislukking voorkomt. In feite emuleert het een gebruiker handmatig elke fout af.
   * **gaat onmiddellijk** - als geselecteerd, de pijpleidingsprocedures automatisch wanneer een belangrijke mislukking voorkomt. Het emuleert hoofdzakelijk een gebruiker manueel goedkeurend elke mislukking.

1. Klik **verdergaan**.

1. Op het **lusje van de Code van Source** van **voeg niet-Productie pijplijn** dialoog toe, moet u selecteren welk type van code de pijpleiding zou moeten verwerken.

   * **[Volledige Code van de Stapel](#full-stack-code)**
   * **[gerichte plaatsing](#targeted-deployment)**

Zie [&#x200B; CI/CD Pijpleidingen &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) voor meer informatie over de types van pijpleidingen.

De stappen om de verwezenlijking van uw niet productiepijplijn te voltooien variëren afhankelijk van het type van broncode u selecteerde. Volg de verbindingen hierboven om aan de volgende sectie van dit document te springen zodat kunt u de configuratie van uw pijpleiding voltooien.

### Volledige stapelcode {#full-stack-code}

Een full-stack codepijplijn implementeert tegelijkertijd back-end en front-end code builds die een of meer AEM-servertoepassingen bevatten samen met de configuratie HTTPD/Dispatcher.

>[!NOTE]
>
>Als er al een &#39;full-stack&#39;-codepijplijn voor de geselecteerde omgeving bestaat, is deze selectie uitgeschakeld.

Om de configuratie van de full-stack code non-production pijpleiding te beëindigen, volg deze stappen.

1. Op het **lusje van de Code van Source**, moet u de volgende opties bepalen.

   * **In aanmerking komende Milieu&#39;s van de Plaatsing** - als uw pijpleiding een plaatsingspijpleiding is, moet u selecteren aan welke milieu&#39;s het zou moeten opstellen.
   * **Bewaarplaats** - Deze optie bepaalt waarvan git repo dat de pijpleiding de code zou moeten terugwinnen.

   >[!TIP]
   > 
   >Zie [&#x200B; Toevoegend en het Leiden Bewaarplaatsen &#x200B;](/help/implementing/cloud-manager/managing-code/managing-repositories.md) zodat kunt u leren om bewaarplaatsen in Cloud Manager toe te voegen en te beheren.

   * **Tak van het Git** - Deze optie bepaalt waarvan de tak in de geselecteerde pijpleiding de code zou moeten terugwinnen.
      * Voer de eerste paar tekens in van de naam van de vertakking en de functie voor automatisch aanvullen van dit veld. Hiermee kunt u de overeenkomende vertakkingen zoeken die u kunt selecteren.
   * **negeert de Configuratie van de Rij van het Web** - wanneer gecontroleerd, stelt de pijpleiding uw configuratie van de Webrij niet op.
   * **Pijpleiding** - als uw pijpleiding een plaatsingspijpleiding is, kunt u verkiezen om een het testen fase in werking te stellen. Controleer de opties die u in deze fase wilt inschakelen. Als geen van de opties wordt geselecteerd, wordt de het testen fase niet getoond tijdens de looppas van de pijpleiding.

      * **Functionele het Testen van het Product** - voer [&#x200B; product functionele tests &#x200B;](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing) tegen het ontwikkelmilieu uit.
      * **Functionele het Testen van de Douane** - voer [&#x200B; douane functionele tests &#x200B;](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) tegen het ontwikkelmilieu uit.
      * **het Testen van de Douane UI** - voer [&#x200B; tests van douaneUI &#x200B;](/help/implementing/cloud-manager/ui-testing.md) voor douanetoepassingen uit.
      * **Controle van de Ervaring** - voer [&#x200B; Controle van de Ervaring uit &#x200B;](/help/implementing/cloud-manager/reports/report-experience-audit.md)

   ![&#x200B; volledig-stapelpijpleiding &#x200B;](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Klik **sparen**.

De pijpleiding wordt bewaard en u kunt uw pijpleidingen [&#x200B; op de &#x200B;](managing-pipelines.md) Pijpleidingen **kaart op de** pagina van het Overzicht van het Programma **nu beheren.**

### Gerichte implementatie {#targeted-deployment}

Een gerichte implementatie implementeert alleen code voor geselecteerde onderdelen van uw AEM-toepassing. In zulk een plaatsing kunt u verkiezen om **&#x200B;**&#x200B;één van de volgende soorten code te omvatten:

* **Config** - vorm montages voor diverse eigenschappen in uw milieu van AEM.
   * Zie [&#x200B; Gebruikend Pijpleidingen Config &#x200B;](/help/operations/config-pipeline.md) voor een lijst van gesteunde configuraties, die logboek het door:sturen, zuivert-verwante onderhoudstaken, en diverse configuraties CDN omvatten, en om hen in uw bewaarplaats te beheren zodat worden zij behoorlijk opgesteld.
   * Wanneer het runnen van een gerichte plaatsingspijpleiding, worden de configuraties opgesteld, mits zij aan het milieu, de bewaarplaats, en de tak worden bewaard u in de pijpleiding bepaalde.
   * Op elk ogenblik, kan er slechts één config pijpleiding per milieu zijn.
* **vorm Edge Delivery Services config pijpleiding** - de Pijpleidingen van de Configuratie van Edge Delivery hebben geen afzonderlijke ontwikkeling, het opvoeren, en productiemilieu&#39;s. In AEM as a Cloud Service worden wijzigingen doorgevoerd in ontwikkelings-, fase- en productieniveaus. Een Edge Delivery Configuration Pipeline past daarentegen zijn configuratie rechtstreeks toe op alle Edge Delivery Sites-domeinen die in Cloud Manager zijn geregistreerd. Meer leren, zie [&#x200B; een Pijpleiding van Edge Delivery &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md) toevoegen.
* **Voorste Code van het Eind** - vorm JavaScript en CSS voor het vooreind van uw toepassing van AEM.
   * Met frontend pijpleidingen wordt meer onafhankelijkheid gegeven aan front-end ontwikkelaars en kan het ontwikkelingsproces worden versneld.
   * Zie het document [&#x200B; Ontwikkelend Plaatsen met de Voorste-Eind Pijpleiding &#x200B;](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) voor hoe dit proces samen met sommige overwegingen werkt om zich bewust te zijn van om het volledige potentieel uit dit proces te krijgen.
* **Config van de Rij van het Web** - Vorm de eigenschappen van Dispatcher om, Web-pagina&#39;s op te slaan te verwerken en te leveren aan de cliënt.
   * Zie het document [&#x200B; CI/CD Pijpleidingen &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) voor meer details.
   * Als er voor de geselecteerde omgeving een pijpleiding voor code in de weblaag bestaat, is deze selectie uitgeschakeld.
   * Als een volledig-stapelpijpleiding reeds aan een milieu opstelt, kunt u nog een Web-rij configuratiepijplijn voor dat zelfde milieu tot stand brengen. Als u dat doet, negeert Cloud Manager de configuratie op de web-tier in de full-stack pijplijn.


>[!NOTE]
>
>De de rij en config van het Web pijpleidingen worden niet gesteund met privé bewaarplaatsen. Zie [&#x200B; Toevoegend Privé Bewaarplaatsen in Cloud Manager &#x200B;](/help/implementing/cloud-manager/managing-code/private-repositories.md) voor details en de volledige lijst van beperkingen.

De stappen om de verwezenlijking van uw niet-productie, gerichte plaatsingspijpleiding te voltooien zijn het zelfde zodra u een plaatsingstype kiest.

1. Kies welk implementatietype u nodig hebt.

![&#x200B; gerichte plaatsingsopties &#x200B;](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-targeted-deployment.png)

1. Bepaal de **In aanmerking komende Milieu&#39;s van de Plaatsing**.

   * Als uw pijpleiding een plaatsingspijpleiding is, moet u selecteren aan welke milieu&#39;s het zou moeten opstellen.

1. Onder **Code van Source**, bepaal de volgende opties:

   * **Bewaarplaats** - Deze optie bepaalt waarvan git repo dat de pijpleiding de code zou moeten terugwinnen.

   >[!TIP]
   > 
   >Zie [&#x200B; Toevoegend en het Leiden Bewaarplaatsen &#x200B;](/help/implementing/cloud-manager/managing-code/managing-repositories.md) zodat kunt u leren om bewaarplaatsen in Cloud Manager toe te voegen en te beheren.

   * **Tak van het Git** - Deze optie bepaalt waarvan de tak in de geselecteerde pijpleiding de code zou moeten terugwinnen.
      * Voer de eerste paar tekens in van de naam van de vertakking en de functie voor automatisch aanvullen van dit veld. U vindt de overeenkomende vertakkingen die u kunt selecteren.
   * **Plaats van de Code** - Deze optie bepaalt de weg in de tak van de geselecteerde repo waarvan de pijpleiding de code zou moeten terugwinnen.
   * **Pijpleiding** - voor front-end niet productiepijpleidingen, hebt u de optie om **[Controle van de Ervaring](/help/implementing/cloud-manager/reports/report-experience-audit.md)** toe te laten.

   ![&#x200B; Config pijpleiding &#x200B;](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config-deployment-experience-audit.png)

1. Als u de Controle van de Ervaring toeliet, ga **&#x200B;**&#x200B;**lusje van de Controle van de Ervaring verder &lbrace;waar u de wegen kunt bepalen die altijd in de Controle van de Ervaring zouden moeten worden omvat.**

   * Als u **de Controle van de Ervaring** toeliet, zie de controle van de de 2&rbrace; Ervaring van het document [&#x200B; voor details op hoe te vormen.](/help/implementing/cloud-manager/reports/report-experience-audit.md)
   * Als u dit niet hebt gedaan, slaat u deze stap over.

1. Klik **sparen** om de pijpleiding te bewaren.

De pijpleiding wordt bewaard en u kunt uw pijpleidingen [&#x200B; op de &#x200B;](managing-pipelines.md) Pijpleidingen **kaart op de** pagina van het Overzicht van het Programma **nu beheren.**

## Dispatcher-pakketten overslaan {#skip-dispatcher-packages}

Schakel het publiceren uit als u wilt dat Dispatcher-pakketten in uw pijplijn zijn ingebouwd, maar niet zijn geüpload om opslag te maken. Dit kan de runtime van de pijpleiding verkorten.

De volgende configuratie om het publiceren van Dispatcher-pakketten uit te schakelen, moet via het `pom.xml` -projectbestand worden toegevoegd. Stel een omgevingsvariabele in de Cloud Manager-constructiecontainer in om te markeren wanneer Dispatcher-pakketten moeten worden genegeerd. De pijpleiding leest deze vlag en negeert hen dienovereenkomstig.

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
