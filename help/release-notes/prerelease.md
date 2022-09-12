---
title: "[!DNL Adobe Experience Manager] as a Cloud Service prerelease-kanaal"
description: "[!DNL Adobe Experience Manager] as a Cloud Service prerelease-kanaal"
exl-id: cfc91699-0087-40fa-a76c-0e5e1e03a5bd
source-git-commit: c2f0b9c904374b5e59ce2b2f268fdd73dfdbfd21
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] as a Cloud Service prerelease-kanaal {#prerelease-channel}


## Inleiding {#introduction}

[!DNL Adobe Experience Manager] as a Cloud Service biedt elke maand nieuwe functies, volgens het schema van [Routekaart voor release van Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=en#aem-as-cloud-service). Om vertrouwd te worden met de eigenschappen die gepland zijn om de volgende maand levend te gaan, kunnen de klanten aan het prereleasekanaal intekenen, dat door geschikt te vormen in de milieu&#39;s van de standaardprogrammaontwikkeling of om het even welke milieu&#39;s van het zandbakprogramma toegankelijk is. De klanten kunnen voorproef veranderingen in de console van Plaatsen, evenals code tegen om het even welke nieuwe prerelease APIs bouwen.

De lijst met pre-releasefuncties voor een bepaalde maand wordt geplaatst in het dialoogvenster [Opmerkingen bij maandelijkse release](/help/release-notes/release-notes-cloud/release-notes-current.md).

>[!VIDEO](/help/release-notes/assets/prerelease-overview.mp4)

## Hoe te om Prerelease toe te laten {#enable-prerelease}

De pre-releasefuncties kunnen op verschillende manieren worden ervaren:

* Cloud-omgevingen (standaardprogramma-ontwikkelomgevingen of elk ander type sandboxprogramma)
* Lokale SDK

### Cloud-omgevingen {#cloud-environments}

Als u een Cloud-omgeving wilt bijwerken zodat deze de prerelease kan gebruiken, voegt u een nieuwe [omgevingsvariabele](../implementing/cloud-manager/environment-variables.md) met de interface Environment Configuration in Cloud Manager:

1. Ga naar de **Programma** > **Omgeving** > **Omgevingsconfiguratie** wilt bijwerken.
1. Een nieuwe toevoegen [omgevingsvariabele](../implementing/cloud-manager/environment-variables.md):

   | Naam | Waarde | Toegepaste service | Type |
   |------|-------|-----------------|------|
   | `AEM_RELEASE_CHANNEL` | `prerelease` | Alles | Variabele |

1. Sla de wijzigingen op en vernieuw de omgeving met ingeschakelde prerelease-functieschakelingen.

   ![Nieuwe omgevingsvariabele](assets/env-configuration-prerelease.png)


**Alternatief** u kunt de API en CLI van de Manager van de Wolk gebruiken om de milieuvariabelen bij te werken:

* Gebruiken [Het eindpunt van de omgevingsvariabelen van de API voor cloudbeheer](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchEnvironmentVariables)stelt u de **AEM_RELEASE_CHANNEL** omgevingsvariabele voor de waarde **prerelease**.

   ```
   PATCH /program/{programId}/environment/{environmentId}/variables
   [
           {
                   "name" : "AEM_RELEASE_CHANNEL",
                   "value" : "prerelease",
                   "type" : "string"
           }
   ]
   ```

* De CLI van Cloud Manager kan ook worden gebruikt, volgens de instructies op [https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid)

   ```aio cloudmanager:environment:set-variables <ENVIRONMENT_ID> --programId=<PROGRAM_ID> --variable AEM_RELEASE_CHANNEL “prerelease”```


De variabele kan worden verwijderd of op een andere waarde worden ingesteld als u wilt dat de omgeving wordt hersteld naar het gedrag van het gewone (niet-pre-)releasekanaal.

### Lokale SDK {#local-sdk}

U kunt nieuwe eigenschappen in de console van Plaatsen in lokale QuickStart SDK en code tegen nieuwe APIs in pre-uitgave zien door uw beproefde project te hebben verwijzen naar prerelease `API Jar` gevestigd in Maven Central. U kunt deze prereleasefuncties op uw lokale computer ook zien door de regelmatige SDK van QuickStart op prereleasemodus te beginnen:

* Download de SDK van de portal voor softwaredistributie en installeer de SDK zoals beschreven in [Toegang tot de AEM as a Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).
* Neem het argument op wanneer u de SDK Quickstart start `-r prerelease`.
* De waarde is *kleverig* zodat deze alleen bij het eerste opstarten kan worden geselecteerd. Installeer de SDK opnieuw om de opdrachtregeloptie te wijzigen.

Aangezien er meerdere AEM onderhoudsreleases tussen maandelijkse functiereleases kunnen zijn, kunt u deze nieuwe SDK&#39;s downloaden en verwijzen naar de nieuwe Jar-versies van SDK API in bepaalde projecten. De onderhoudsversies zullen geen extra prereleasefuncties toevoegen, maar zouden andere kleinere veranderingen zoals insectenmoeilijke situaties, veiligheidsmoeilijke situaties, en prestatiesverhogingen kunnen omvatten.
JavaDocs wordt gepubliceerd aan Centrale Maven.

Samenstellen op basis van de prerelease SDK:

1. wijzig de pom.xml van uw beproefde project om naar een verschillende prerelease sdk api jar te verwijzen, die aan Maven central wordt gepubliceerd. Het bevat nieuwe Java api voor de pre-releasefuncties en is afhankelijk van de sdk api jar. Dezelfde versie wordt gebruikt.

   Hier ziet u bijvoorbeeld een fragment uit de sectie voor het beheer van afhankelijkheden van de bovenliggende pom dat verwijst naar de gewone API Jar:

   ```
   <dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>com.adobe.aem</groupId>
            <artifactId>aem-sdk-api</artifactId>
            <version>${aem.sdk.api}</version>
            <scope>provided</scope>
        </dependency>
   ```

   En dan het gebruik in een module:

   ```
    <dependencies>
     <dependency>
         <groupId>com.adobe.aem</groupId>
         <artifactId>aem-sdk-api</artifactId>
     </dependency>
   ```

   Als u wilt overstappen op de prerelease SDK, wijzigt u eenvoudig de afhankelijkheid van `com.adobe.aem:aem-sdk-api` tot `com.adobe.aem:aem-prerelease-sdk-api` zoals hieronder vermeld :

   ```
   <dependencyManagement>
    <dependencies>
      <dependency>
            <groupId>com.adobe.aem</groupId>
            <artifactId>aem-prerelease-sdk-api</artifactId>
            <version>${aem.sdk.api}</version>
            <scope>provided</scope>
      </dependency>
   <dependencies>
      <dependency>
         <groupId>com.adobe.aem</groupId>
         <artifactId>aem-prerelease-sdk-api</artifactId>
      </dependency>
   ```

   Zoals gebruikelijk, kunnen de individuele projecten de afhankelijkheid gebruiken.

1. Distribueren naar uw lokale server
1. Als tevreden bevestigend dat het zoals verwacht plaatselijk werkt, wijs code aan een ontwikkelingstak toe en gebruik een niet productiepijplijn van de Manager van de Wolk om aan een milieu op te stellen dat aan het prereleasekanaal intekent

>[!CAUTION]
> 
> De `aem-prerelease-sdk-api` artifactId mag nooit worden gebruikt bij het implementeren naar werkgebied of productie. Gebruikt altijd aem-sdk-api wanneer het opstellen via de Pijpleiding van de Productie. Ook code die verwijst naar pre-releaseAPI&#39;s mag niet worden geïmplementeerd via de productiepijpleiding.

De [AEM CS SDK-build Analysemodus plug-in v1.0 en hoger](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=en#developing) zal ontdekken als pre api in een project door de gebiedsdelen te inspecteren wordt gebruikt. Als de analysator het vindt, zal het prerelease sdk api gebruiken om het project te analyseren.

## Overwegingen {#considerations}

Er zijn een paar dingen om op te merken wanneer het over het prereleasekanaal komt:

* Sommige functies die worden geïmplementeerd in de release van de volgende maand, worden mogelijk niet opgenomen in het prereleasekanaal.
* Functies in de prerelease worden onderworpen aan strenge kwaliteitsborging en zijn bedoeld om volledig te zijn in plaats van bètakwaliteit. Als u om het even welke kwesties opmerkt, rapporteer hen, enkel zoals u zou doen als u insecten in eigenschappen in een regelmatige AEM versie verdacht.
* Om te bepalen als een milieu voor het prereleasekanaal wordt gevormd, ga naar AEM Console **Info** pagina en controleer of het AEM versienummer een *prerelease* achtervoegsel zoals ```Adobe Experience Manager 2021.4.5226.20210427T070726Z-210429-PRERELEASE```.

![info](/help/release-notes/assets/about.png)
