---
title: Niet-productiepijpleidingen configureren
description: Leer hoe u niet-productiepijpleidingen configureert om de kwaliteit van uw code te testen voordat u deze implementeert in productieomgevingen.
index: true
exl-id: eba608eb-a19e-4bff-82ff-05860ceabe6e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1371'
ht-degree: 0%

---


# Niet-productiepijpleidingen configureren {#configuring-non-production-pipelines}

Leer hoe u niet-productiepijpleidingen configureert om de kwaliteit van uw code te testen voordat u deze implementeert in productieomgevingen.

Een gebruiker moet beschikken over **[Implementatiebeheer](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** rol voor het configureren van niet-productiepijpleidingen.

## Niet-productiepijpleidingen {#non-production-pipelines}

Naast [productiepijpleidingen](#configuring-production-pipelines.md) die zich aan stagings en productiemilieu&#39;s opstelt, kunt u ook niet-productiepijpleidingen opzetten om uw code te bevestigen.

Er zijn twee soorten niet-productiepijpleidingen:

* **Codekwaliteitspijplijnen** - Deze looppas codekwaliteit scant op de code in een git tak en voert de bouw en de stappen van de codekwaliteit uit.
* **Implementatiepijpleidingen** - Naast het uitvoeren van de bouw en de stappen van de codekwaliteit zoals de pijpleidingen van de codekwaliteit, stellen deze pijpleidingen de code in een non-production milieu op.

>[!NOTE]
>
>U kunt [pijpleidingsinstellingen bewerken](managing-pipelines.md) na de eerste installatie.

## Een nieuwe niet-productiepijplijn toevoegen {#adding-non-production-pipeline}

Nadat u uw programma hebt ingesteld en minstens één omgeving hebt gebruikt met de interface van Cloud Manager, kunt u een niet-productiepijplijn toevoegen door deze stappen uit te voeren.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Op de **[Mijn programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)** -console, selecteert u het programma.

1. Toegang krijgen tot de **Pijpleidingen** kaart van het startscherm van Cloud Manager. Klikken **+Toevoegen** en selecteert u **Niet-productiepijpleiding toevoegen**.

   ![Niet-productiepijpleiding toevoegen](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. Op de **Configuratie** tabblad van het **Niet-productiepijpleiding toevoegen** selecteert u het type niet-productiepijplijn dat u wilt toevoegen.

   * **Codekwaliteit, pijplijn** - Creeer een pijpleiding die uw code bouwt, eenheidstests in werking stelt, en codekwaliteit evalueert maar NIET opstelt.
   * **Implementatiepijp** - Creeer een pijpleiding die uw code bouwt, eenheidstests in werking stelt, codekwaliteit evalueert, en aan een milieu opstelt.

   ![Dialoogvenster Niet-productiepijplijn toevoegen](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Geef een **Naam niet-productiepijpleiding** om uw pijpleiding samen met de volgende extra informatie te identificeren.

   * **Implementatieactivering** - U hebt de volgende opties wanneer het bepalen van de plaatsingstrekkers om de pijpleiding te beginnen.

      * **Handmatig** - Gebruik deze optie om de pijpleiding manueel te beginnen.
      * **Wijzigingen in Git** - Deze optie begint de pijpleiding CI/CD wanneer de bemoeienis aan de gevormde git tak wordt toegevoegd. Met deze optie, kunt u de pijpleiding nog manueel zoals vereist beginnen.

1. Als u ervoor kiest een **Implementatiepijp** moet u ook de **Belangrijk gedrag metrische fouten**.

   * **Telkens vragen** - Dit gedrag is de standaardinstelling en vereist handmatige interventie bij belangrijke fouten.
   * **Direct mislukken** - Indien geselecteerd, wordt de pijpleiding geannuleerd wanneer een belangrijke mislukking voorkomt. In feite emuleert het een gebruiker handmatig elke fout af.
   * **Direct doorgaan** - Als deze optie is geselecteerd, wordt de pijplijn automatisch uitgevoerd wanneer een belangrijke fout optreedt. Het emuleert hoofdzakelijk een gebruiker manueel goedkeurend elke mislukking.

1. Klikken **Doorgaan**.

1. Op de **Broncode** tabblad van het **Niet-productiepijpleiding toevoegen** moet u selecteren welk type code de pijplijn moet verwerken.

   * **[Volledige stapelcode](#full-stack-code)**
   * **[Gerichte implementatie](#targeted-deployment)**

Zie [CI/CD-pijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) voor meer informatie over de soorten pijpleidingen .

De stappen om de verwezenlijking van uw niet productiepijplijn te voltooien variëren afhankelijk van het type van broncode u selecteerde. Volg de verbindingen hierboven om aan de volgende sectie van dit document te springen zodat kunt u de configuratie van uw pijpleiding voltooien.

### Volledige stapelcode {#full-stack-code}

Een full-stack codepijpleiding stelt gelijktijdig achterste en front-end codebouwstijlen op die één of meerdere AEM servertoepassingen samen met configuratie HTTPD/Dispatcher bevatten.

>[!NOTE]
>
>Als er al een &#39;full-stack&#39;-codepijplijn voor de geselecteerde omgeving bestaat, is deze selectie uitgeschakeld.

Om de configuratie van de full-stack code non-production pijpleiding te beëindigen, volg deze stappen.

1. Op de **Broncode** moet u de volgende opties definiëren.

   * **In aanmerking komende implementatieomgevingen** - Als uw pijpleiding een plaatsingspijpleiding is, moet u selecteren aan welke milieu&#39;s het zou moeten opstellen.
   * **Bewaarplaats** - Deze optie bepaalt waarvan git repo dat de pijpleiding de code zou moeten terugwinnen.

   >[!TIP]
   > 
   >Zie [Opslagplaatsen toevoegen en beheren](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) zodat u kunt leren om opslagruimten toe te voegen en te beheren in Cloud Manager.

   * **Git Branch** - Deze optie bepaalt waarvan de tak in de geselecteerde pijpleiding de code zou moeten terugwinnen.
      * Voer de eerste paar tekens in van de naam van de vertakking en de functie voor automatisch aanvullen van dit veld. Hiermee kunt u de overeenkomende vertakkingen zoeken die u kunt selecteren.
   * **Configuratie van web-Tier negeren** - Als deze optie is ingeschakeld, implementeert de pijpleiding uw configuratie van de weblaag niet.
   * **Pijpleiding** - Als uw pijpleiding een plaatsingspijpleiding is, kunt u verkiezen om een het testen fase in werking te stellen. Controleer de opties die u in deze fase wilt inschakelen. Als geen van de opties wordt geselecteerd, wordt de het testen fase niet getoond tijdens de looppas van de pijpleiding.

      * **Functioneel testen van producten** - Uitvoeren [functionele producttests](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing) tegen de ontwikkelomgeving.
      * **Aangepaste functionele tests** - Uitvoeren [aangepaste functionele tests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) tegen de ontwikkelomgeving.
      * **Aangepaste UI-tests** - Uitvoeren [aangepaste UI-tests](/help/implementing/cloud-manager/ui-testing.md) voor aangepaste toepassingen.
      * **Experience Audit** - Uitvoeren [Experience Audit](/help/implementing/cloud-manager/experience-audit-testing.md)

   ![Volledige pijplijn](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Klikken **Opslaan**.

De pijpleiding wordt bewaard en u kunt nu [beheren van uw pijpleidingen](managing-pipelines.md) op de **Pijpleidingen** kaart op **Programmaoverzicht** pagina.

### Gerichte implementatie {#targeted-deployment}

Een gerichte plaatsing stelt code slechts voor geselecteerde delen van uw AEM toepassing op. In een dergelijke implementatie kunt u ervoor kiezen **Inclusief** een van de volgende typen code:

* **Config** - Vorm montages voor de regels van de verkeersfilter op uw AEM milieu.
   * Zie het document [Verkeersfilterregels inclusief WAF-regels](/help/security/traffic-filter-rules-including-waf.md) om te leren hoe te om de regels van de verkeersfilter in uw bewaarplaats te beheren zodat zij behoorlijk worden opgesteld.
   * Wanneer het runnen van een gerichte plaatsingspijpleiding, configuraties [zoals WAF-configuraties](/help/security/traffic-filter-rules-including-waf.md) zal worden opgesteld, op voorwaarde dat zij aan milieu, bewaarplaats, en tak worden bewaard u in de pijpleiding bepaalde.
   * Op elk ogenblik, kan er slechts één config pijpleiding per milieu zijn.
* **Code frontend** - Configureer JavaScript en CSS voor de voorzijde van de AEM toepassing.
   * Met frontend pijpleidingen wordt meer onafhankelijkheid gegeven aan front-end ontwikkelaars en kan het ontwikkelingsproces worden versneld.
   * Zie het document [Sites ontwikkelen met behulp van de voorste pijplijn](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) hoe dit proces samen met een aantal overwegingen werkt , moet u zich ervan bewust zijn dat dit proces alle mogelijkheden biedt .
* **Config. web** - Configureer de eigenschappen van de dispatcher voor het opslaan, verwerken en leveren van webpagina&#39;s aan de client.
   * Zie het document [CI/CD-pijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) voor meer informatie .
   * Als er voor de geselecteerde omgeving een pijpleiding voor code in de weblaag bestaat, is deze selectie uitgeschakeld.
   * Als u een bestaande full-stack pijpleiding die aan een milieu opstelt hebt, die tot een Web rij config pijpleiding voor het zelfde milieu leidt zal de bestaande configuratie van de Webrij in de full-stack pijpleiding worden genegeerd.

De stappen om de verwezenlijking van uw niet-productie, gerichte plaatsingspijpleiding te voltooien zijn het zelfde zodra u een plaatsingstype kiest.

1. Kies welk implementatietype u nodig hebt.

![Gerichte implementatieopties](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-targeted-deployment.png)

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
   * **Pijpleiding** - Voor niet-productiepijpleidingen aan de voorzijde hebt u de mogelijkheid om **[Ervaar controle.](/help/implementing/cloud-manager/experience-audit-testing.md)**

   ![Config-pijplijn](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config-deployment-experience-audit.png)

1. Tik of klik op **Doorgaan** aan de **Experience Audit** kunt u de paden definiëren die altijd moeten worden opgenomen in de controle van de ervaring.

   * Als u **Experience Audit**, raadpleeg het document [Experience Audit](/help/implementing/cloud-manager/experience-audit-testing.md#configuration) voor details over hoe te te vormen.
   * Als u dit niet hebt gedaan, slaat u deze stap over.

1. Tik of klik op **Opslaan** om de pijpleiding te redden.

De pijpleiding wordt bewaard en u kunt nu [beheren van uw pijpleidingen](managing-pipelines.md) op de **Pijpleidingen** kaart op **Programmaoverzicht** pagina.

## Verzendingspakketten overslaan {#skip-dispatcher-packages}

Als u de pakketten van de Ontvanger wilt die als deel van uw pijpleiding worden gebouwd, maar hen niet gepubliceerd om opslag te bouwen, kunt u het publiceren van hen onbruikbaar maken, die pijpleidingsloopduur kunnen verminderen.

De volgende configuratie om het publiceren van de pakketten van de Verzender onbruikbaar te maken moet via uw project worden toegevoegd `pom.xml` bestand. De variabele is gebaseerd op een omgevingsvariabele die fungeert als een vlag die u in de builcontainer van Cloud Manager kunt instellen om te bepalen wanneer de Dispatcher-pakketten moeten worden genegeerd.

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
