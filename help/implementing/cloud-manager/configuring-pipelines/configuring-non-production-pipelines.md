---
title: Niet-productiepijpleidingen configureren
description: Leer hoe te om niet-productiepijpleidingen te vormen om de kwaliteit van uw code te testen alvorens aan productiemilieu's op te stellen.
index: true
exl-id: eba608eb-a19e-4bff-82ff-05860ceabe6e
source-git-commit: 9804d9b71f082c3d4788667fdc3993af3b673588
workflow-type: tm+mt
source-wordcount: '1119'
ht-degree: 0%

---

# Niet-productiepijpleidingen configureren {#configuring-non-production-pipelines}

Leer hoe te om niet-productiepijpleidingen te vormen om de kwaliteit van uw code te testen alvorens aan productiemilieu&#39;s op te stellen.

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

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Toegang krijgen tot **Pijpleidingen** kaart van het startscherm van Cloud Manager. Klikken op **+Toevoegen** en selecteert u **Niet-productiepijpleiding toevoegen**.

   ![Niet-productiepijpleiding toevoegen](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. Op de **Configuratie** tabblad van het dialoogvenster **Niet-productiepijpleiding toevoegen** selecteert u het type niet-productiepijplijn dat u wilt toevoegen, of **Codekwaliteit, pijplijn** of **Implementatiepijp**.

   ![Dialoogvenster Niet-productiepijplijn toevoegen](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Een **Naam niet-productiepijpleiding** om uw pijpleiding samen met de volgende extra informatie te identificeren.

   * **Implementatieactivering** - U hebt de volgende opties wanneer het bepalen van de plaatsingstrekkers om de pijpleiding te beginnen.

      * **Handmatig** - Gebruik deze optie om de pijpleiding manueel te beginnen.
      * **Wijzigingen in Git** - Deze opties beginnen de pijpleiding CI/CD wanneer de bemoeienis aan de gevormde git tak wordt toegevoegd. Met deze optie, kunt u de pijpleiding nog manueel zoals vereist beginnen.

1. Klikken **Doorgaan**.

1. Op de **Broncode** tabblad van het dialoogvenster **Niet-productiepijpleiding toevoegen** moet u selecteren welk type code de pijplijn moet verwerken.

   * **[Code frontend](#front-end-code)**
   * **[Volledige stapelcode](#full-stack-code)**
   * **[Config. web](#web-tier-config)**

De stappen om de verwezenlijking van uw niet productiepijplijn te voltooien variëren afhankelijk van de optie voor **Broncode** geselecteerd. Volg de verbindingen hierboven om aan de volgende sectie van dit document te springen om de configuratie van uw pijpleiding te voltooien.

### Code frontend {#front-end-code}

Een front-end codepijpleiding stelt front-end code op bouwt die één of meerdere cliënt-kant toepassingen UI bevatten. Zie het document [CI/CD-pijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) voor meer informatie over dit type pijpleiding .

Om de configuratie van de front-end code non-production pijpleiding te beëindigen, volg deze stappen.

1. Op de **Broncode** moet u de volgende opties definiëren.

   * **In aanmerking komende implementatieomgevingen** - Als uw pijpleiding een plaatsingspijpleiding is, moet u selecteren aan welke milieu&#39;s het zou moeten opstellen.
   * **Bewaarplaats** - Deze optie bepaalt waarvan git repo de pijpleiding de code zou moeten terugwinnen.

   >[!TIP]
   > 
   >Zie het document [Opslagplaatsen toevoegen en beheren](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) voor meer informatie over het toevoegen en beheren van opslagruimten in Cloud Manager.

   * **Git Branch** - Deze optie bepaalt van welke tak in de geselecteerde pijpleiding de code zou moeten terugwinnen.
      * Voer de eerste paar tekens van de naam van de vertakking in en met de functie voor automatisch aanvullen van dit veld kunt u de overeenkomende vertakkingen vinden om u te helpen selecteren.
   * **Codelocatie** - Deze optie bepaalt de weg in de tak van de geselecteerde repo waarvan de pijpleiding de code zou moeten terugwinnen.

   ![Pijpleiding aan de voorzijde](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-front-end.png)

1. Klikken **Opslaan**.

De pijpleiding wordt bewaard en u kunt nu [beheren van uw pijpleidingen](managing-pipelines.md) op de **Pijpleidingen** kaart op **Programmaoverzicht** pagina.

### Volledige stapelcode {#full-stack-code}

Een full-stack codepijpleiding stelt gelijktijdig achterste en front-end codebouwstijlen op die één of meerdere AEM servertoepassingen samen met configuratie HTTPD/Dispatcher bevatten. Zie het document [CI/CD-pijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline) voor meer informatie over dit type pijpleiding .

>[!NOTE]
>
>Als er al een &#39;full-stack&#39;-codepijplijn voor de geselecteerde omgeving bestaat, wordt deze selectie uitgeschakeld.

Om de configuratie van de full-stack code non-production pijpleiding te beëindigen, volg deze stappen.

1. Op de **Broncode** moet u de volgende opties definiëren.

   * **In aanmerking komende implementatieomgevingen** - Als uw pijpleiding een plaatsingspijpleiding is, moet u selecteren aan welke milieu&#39;s het zou moeten opstellen.
   * **Bewaarplaats** - Deze opties bepalen waarvan de git repo de pijpleiding de code zou moeten terugwinnen.

   >[!TIP]
   > 
   >Zie het document [Opslagplaatsen toevoegen en beheren](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) voor meer informatie over het toevoegen en beheren van opslagruimten in Cloud Manager.

   * **Git Branch** - Deze optie bepaalt van welke tak in de geselecteerde pijpleiding de code zou moeten terugwinnen.
      * Voer de eerste paar tekens van de naam van de vertakking in en met de functie voor automatisch aanvullen van dit veld kunt u de overeenkomende vertakkingen vinden om u te helpen selecteren.
   * **Configuratie van web-Tier negeren** - Wanneer gecontroleerd, zal de pijpleiding niet uw configuratie van de Webrij opstellen.

   ![Volledige pijplijn](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Klikken **Opslaan**.

De pijpleiding wordt bewaard en u kunt nu [beheren van uw pijpleidingen](managing-pipelines.md) op de **Pijpleidingen** kaart op **Programmaoverzicht** pagina.

### Config. web {#web-tier-config}

Een configuratiepijplijn van de Webrij stelt configuraties HTTPD/Dispatcher op. Zie het document [CI/CD-pijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipeline) voor meer informatie over dit type pijpleiding .

>[!NOTE]
>
>Als er voor de geselecteerde omgeving al een pijpleiding voor code in de weblaag bestaat, wordt deze selectie uitgeschakeld.

Voer de volgende stappen uit om de configuratie van de niet-productiepijplijn voor code op het web te voltooien.

1. Op de **Broncode** moet u de volgende opties definiëren.

   * **In aanmerking komende implementatieomgevingen** - Als uw pijpleiding een plaatsingspijpleiding is, moet u selecteren aan welke milieu&#39;s het zou moeten opstellen.
   * **Bewaarplaats** - Deze optie bepaalt waarvan git repo de pijpleiding de code zou moeten terugwinnen.

   >[!TIP]
   > 
   >Zie het document [Opslagplaatsen toevoegen en beheren](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) voor meer informatie over het toevoegen en beheren van opslagruimten in Cloud Manager.

   * **Git Branch** - Deze optie bepaalt van welke tak in de geselecteerde pijpleiding de code zou moeten terugwinnen.
   * **Codelocatie** - Deze optie bepaalt de weg in de tak van de geselecteerde repo waarvan de pijpleiding de code zou moeten terugwinnen.
      * Voor configuratieleidingen voor het web is dit meestal het pad dat `conf.d`, `conf.dispatcher.d`, en `opt-in` directory&#39;s.
      * Als de projectstructuur bijvoorbeeld is gegenereerd op basis van de [Projectarchetype AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=en) het pad zou `/dispatcher/src`.

   ![Gasleiding op de weblijst](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-web-tier.png)

1. Klikken **Opslaan**.

>[!NOTE]
>
>Als u een bestaande full-stack pijpleiding die aan een milieu opstelt hebt, die tot een Web rij config pijpleiding voor het zelfde milieu leidt zal de bestaande configuratie van de Webrij in de full-stack pijpleiding worden genegeerd.

De pijpleiding wordt bewaard en u kunt nu [beheren van uw pijpleidingen](managing-pipelines.md) op de **Pijpleidingen** kaart op **Programmaoverzicht** pagina.

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
