---
title: Adobe Experience Manager as a Cloud Service Prerelease-kanaal
description: Leer hoe u het pre-releasekanaal gebruikt om een voorvertoning van aanstaande functies naar AEM as a Cloud Service te bekijken.
exl-id: cfc91699-0087-40fa-a76c-0e5e1e03a5bd
feature: Release Information
role: Admin
source-git-commit: 36da09746f02daad82875329b0aa53ee4eb7c074
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 0%

---


# Adobe Experience Manager as a Cloud Service Prerelease-kanaal {#prerelease-channel}

Leer hoe u het pre-releasekanaal gebruikt om een voorvertoning van aanstaande functies naar AEM as a Cloud Service te bekijken.

## Inleiding {#introduction}

Adobe Experience Manager as a Cloud Service biedt regelmatig nieuwe functies. De lijst van nieuwe en aanstaande eigenschappen voor een bepaalde eigenschapversie wordt gepost binnen de [ versienota&#39;s.](/help/release-notes/release-notes-cloud/release-notes-current.md)

De volgende functies worden doorgaans op twee manieren beschikbaar gesteld:

* In het kader van een programma voor vroegtijdige adoptie
* Als onderdeel van het prereleasekanaal

In dit document wordt beschreven hoe u het prereleasekanaal kunt inschakelen. Het pre-releasekanaal verleent toegang tot vroege eigenschappen die een toekomstige eigenschapversie van AEM zullen worden geïntroduceerd. Dit geeft u de kans om nieuwe eigenschappen te bevestigen en voor hun goedkeuring vóór hun toekomstige versie te plannen. Gelieve te zien de document [ Nota&#39;s van de Versie voor Adobe Experience Manager (AEM) as a Cloud Service ](/help/release-notes/home.md) voor details op het de versieschema van AEM.

## Laat het Kanaal van de Prerelease toe om tot Aankomende Eigenschappen toegang te hebben en uit te proberen {#enable-prerelease}

Het pre-releasekanaal kan op om het even welke ontwikkeling of zandbakmilieu worden toegelaten. Het prereleasekanaal kan niet op het opvoeren of productiemilieu&#39;s worden toegelaten.

U hebt op twee verschillende manieren toegang tot het pre-releasekanaal:

* [Cloud-omgevingen](#cloud-environments)
* [Lokale SDK](#local-sdk)

### Cloud-omgevingen {#cloud-environments}

Als u een wolkenomgeving wilt bijwerken om het pre-releasekanaal te gebruiken, moet u een nieuwe omgevingsvariabele toevoegen. U kunt dit doen of gebruikend de UI van Cloud Manager of via CLI.

#### Omgevingsvariabele toevoegen met behulp van de gebruikersinterface {#add-with-ui}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Navigeer naar het programma waar u het prereleasekanaal wilt inschakelen.

1. Selecteer het milieu waar u het prereleasekanaal wilt toelaten en tot zijn configuratie via **Programma** toegang hebben > **Milieu** > **Configuratie van het Milieu**.

1. Voeg een nieuwe [ milieuvariabele ](/help/implementing/cloud-manager/environment-variables.md) toe

   | Naam | Waarde | Toegepaste service | Type |
   |------|-------|-----------------|------|
   | `AEM_RELEASE_CHANNEL` | `prerelease` | Alles | Variabele |

1. Sla de wijzigingen op en vernieuw de omgeving met het prereleasekanaal ingeschakeld.

   ![ Nieuwe omgevingsvariabele ](assets/env-configuration-prerelease.png)

#### Omgevingsvariabele toevoegen met CLI {#add-with-cli}

U kunt de Cloud Manager API en CLI ook gebruiken om de omgevingsvariabelen bij te werken.

* Gebruikend [ Cloud Manager API het milieu variabelen eindpunt ](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchEnvironmentVariables), plaats de `AEM_RELEASE_CHANNEL` milieuvariabele aan de waarde `prerelease`.

  ```text
  PATCH /program/{programId}/environment/{environmentId}/variables
  [
          {
                  "name" : "AEM_RELEASE_CHANNEL",
                  "value" : "prerelease",
                  "type" : "string"
          }
  ]
  ```

* [ CLI van Cloud Manager ](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) kan ook worden gebruikt

  ```shell
  aio cloudmanager:environment:set-variables <ENVIRONMENT_ID> --programId=<PROGRAM_ID> --variable AEM_RELEASE_CHANNEL "prerelease
  ```

De variabele kan worden verwijderd als u het standaardgedrag van de omgeving wilt herstellen (niet-pre-releasekanaal).

### Lokale SDK {#local-sdk}

U hebt toegang tot de volgende functies in het pre-releasekanaal in uw lokale Quickstart-SDK en tot code met nieuwe API&#39;s door uw Maven-project te configureren om te verwijzen naar het pre-releasekanaal `API Jar` in Maven Central. U kunt toegang tot het prereleasekanaal in uw lokale ontwikkelomgeving ook zien door de regelmatige SDK van QuickStart op prereleasemodus te beginnen.

#### Quickstart SDK starten in pre-releasemodus {#prerelease-mode}

1. Download SDK van softwaredistributie en installeer zoals die in [ wordt beschreven Toegang tot AEM as a Cloud Service SDK.](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
1. Neem het argument `-r prerelease` op wanneer u de SDK Quickstart start start.

De waarde blijft behouden, zodat deze alleen bij het eerste opstarten kan worden geselecteerd. Installeer de SDK opnieuw om de opdrachtregeloptie te wijzigen.

Aangezien er tussen de maandelijkse versies van functies meerdere AEM-onderhoudsreleases kunnen zijn, kunt u deze nieuwe SDK&#39;s downloaden en verwijzen naar de nieuwe Jar-versies van de SDK API in bepaalde projecten. De onderhoudsversies zullen geen extra prereleasefuncties toevoegen, maar zouden andere kleinere veranderingen zoals insectenmoeilijke situaties, veiligheidsmoeilijke situaties, en prestatiesverhogingen kunnen omvatten.
JavaDocs wordt gepubliceerd aan Centrale Maven.

#### Build Against the Prerelease SDK {#build-sdk}

1. Wijzig de inhoud `pom.xml` van het gemaakte project om te verwijzen naar een specifieke prerelease SDK API-jar, die wordt gepubliceerd naar Maven Central. Deze bevat een nieuwe Java API voor de prereleasefuncties en is afhankelijk van de SDK API-jar. Dezelfde versie wordt gebruikt.

   Hier ziet u bijvoorbeeld een fragment uit de sectie voor het beheer van afhankelijkheden van de bovenliggende pom dat verwijst naar de gewone API-jar:

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

   Als u wilt overschakelen op de pre-releaseversie van SDK, wijzigt u gewoon de afhankelijkheid van `com.adobe.aem:aem-sdk-api` in `com.adobe.aem:aem-prerelease-sdk-api` , zoals hieronder wordt aangegeven:

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

1. Distribueren naar uw lokale server.

1. Als tevreden bevonden dat het zoals plaatselijk verwacht werkt, wijs code aan een ontwikkelingstak toe en gebruik een Cloud Manager niet-productiepijplijn om aan een [ milieu op te stellen dat het pre-releasekanaal toegelaten heeft.](#cloud-environments)

>[!CAUTION]
> 
> De `aem-prerelease-sdk-api` artifactId mag nooit worden gebruikt bij de implementatie naar het werkgebied of de productie. Gebruikt altijd `aem-sdk-api` wanneer het opstellen via de productiepijplijn. Ook de code die verwijzingen prerelease APIs niet via de productiepijplijn zou moeten worden opgesteld.

De [ AEM CS SDK bouwt Analysator die stop in v1.0 wordt gemaakt en hoger ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=nl-NL#developing) zal ontdekken als prerelease API in een project door de gebiedsdelen te inspecteren wordt gebruikt. Als de analysator het vindt, zal het pre-versie SDK API gebruiken om het project te analyseren.

## Overwegingen {#considerations}

Er zijn een paar punten om van nota te nemen wanneer het gebruiken van het prereleasekanaal.

* Het pre-releasekanaal bevat niet noodzakelijkerwijs alle nieuwe functies die in de volgende versie moeten worden geïmplementeerd.
* Functies in de prerelease worden onderworpen aan strenge kwaliteitsborging en zijn bedoeld om volledig te zijn in plaats van bètakwaliteit. Als u problemen opmerkt, rapporteert u deze op dezelfde manier als wanneer u vermoedt dat er fouten zijn in functies in een gewone AEM-release.
* Om te bepalen als een milieu voor het prereleasekanaal wordt gevormd, ga **ongeveer** pagina van de console van AEM en controleer als het de versieaantal van AEM a `PRERELEASE` achtervoegsel zoals `Adobe Experience Manager 2021.4.5226.20210427T070726Z-210429-PRERELEASE` omvat.

![ Ongeveer ](/help/release-notes/assets/about.png)
