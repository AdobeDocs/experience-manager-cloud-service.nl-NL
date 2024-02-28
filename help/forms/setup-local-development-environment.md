---
title: Hoe kan ik een lokale ontwikkelomgeving opzetten voor AEM Forms?
description: Een lokale ontwikkelomgeving instellen voor as a Cloud Service Adobe Experience Manager Forms
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: 12877a77-094f-492a-af58-cffafecf79ae
source-git-commit: 1ec17aebe4eb003b24f5036288a8836aabddb77a
workflow-type: tm+mt
source-wordcount: '2718'
ht-degree: 0%

---

# Lokale ontwikkelomgeving instellen voor AEM Forms {#overview}

Wanneer u opstelling en vormt [!DNL  Adobe Experience Manager Forms] als [!DNL  Cloud Service] omgeving, stelt u ontwikkelings-, staging- en productieomgevingen in op cloud. Daarnaast kunt u ook een lokale ontwikkelomgeving instellen en configureren.

U kunt de lokale ontwikkelomgeving gebruiken om de volgende acties uit te voeren zonder u aan te melden bij de ontwikkelomgeving van de cloud:

* [Formulieren maken](creating-adaptive-form.md) en verwante elementen (thema&#39;s, sjablonen, aangepaste verzendhandelingen, enzovoort)
* [PDF forms converteren naar adaptieve Forms](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/convert-existing-forms-to-adaptive-forms.html)
* Toepassingen maken om te genereren [Klantcommunicatie](aem-forms-cloud-service-communications-introduction.md) op verzoek of in batchmodus.

Nadat een adaptief formulier of verwante elementen gereed zijn voor de lokale ontwikkelingsinstantie of een toepassing om te genereren [Klantcommunicatie] is gereed, kunt u de toepassing Adaptief formulier of Klantcommunicatie van de lokale ontwikkelomgeving naar een Cloud Service-omgeving exporteren voor verdere tests of voor overstap naar productieomgevingen.

U kunt ook aangepaste code zoals aangepaste componenten en vooraf ingevulde service ontwikkelen en testen in de lokale ontwikkelomgeving. Wanneer de aangepaste code is getest en gereed, kunt u de Git-opslagplaats van de ontwikkelomgeving van uw Cloud Service gebruiken om de aangepaste code te implementeren.

Als u een nieuwe lokale ontwikkelomgeving wilt instellen en deze wilt gebruiken voor de ontwikkeling van activiteiten, voert u de volgende acties uit in de aangegeven volgorde:

* [Ontwikkelingshulpmiddelen instellen](#setup-development-tools-for-AEM-projects)

* [Lokale auteur- en publicatieinstanties instellen](#set-up-local-experience-manager-environment-for-development)

* [Forms-archief toevoegen aan lokale ontwikkelingsinstanties en gebruikers configureren](#add-forms-archive-configure-users)

* [Lokale ontwikkelomgeving instellen voor microservices](#docker-microservices)

* [Een ontwikkelingsproject instellen](#forms-cloud-service-local-development-environment)

* [De lokale gereedschappen voor Dispatcher instellen](#setup-local-dispatcher-tools)

<!--
You can use the local development environment to create and test Adaptive Forms without connecting to the Cloud Service. [!DNL AEM Forms] provides an SDK to help test all the cloud-ready functionalities on the local development environment. When your forms and related assets are ready and tested on the local development environment, you can import these forms and related assets to an [!DNL AEM Forms] as a Cloud Service instance for publishing. 

You can also develop and test custom code like custom components and prefill service on the local development environment. When the custom code is tested and ready, you can use the Git repository of your [!DNL AEM Forms] as a Cloud Service development environment to deploy the custom code. 

>[!NOTE]
>
> Pre-pilot release does not support using an [!DNL AEM Forms] as a Cloud Service development instance to create forms. You can create forms, related assets, and custom code only on a local development environment.-->

<!--
You configure two types of development environments:

* **[!DNL AEM Forms] as a Cloud Service development environment:** Use the [[!DNL AEM Forms] as a Cloud Service](setup-forms-cloud-service.md) environment to store, manage, and publish Adaptive Forms and related assets. Do not use an [!DNL AEM Forms] as a Cloud Service environment to create Adaptive Forms and related assets <!--, form-centric workflows, a form data model, or to generate a Document of Record. -->

<!--
* **Local development environment:** You can use the local development environment to create and test Adaptive Forms without connecting to the service. Adobe provides a SDK for the local development to help test all the cloud-ready functionalities. 
Use a local development environment:
    
    * To create forms and related assets (themes, templates, custom Submit Actions, and more) and convert PDF forms to Adaptive Forms. After an Adaptive Form or related assets are ready on the local development instance, you can export the Adaptive Form and related assets from the local development environment to an [!DNL AEM Forms] as a Cloud Service development environment for publishing.  
    
    * To update configuration settings and develop and test custom code like custom components and prefill service. When the custom code is tested and ready, you can use the Git repository of your [!DNL AEM Forms] as a Cloud Service development environment to deploy the custom code.  

You can use the local development environment to create and test Adaptive Forms without connecting to the service. Adobe provides a SDK for the local development to help test all the cloud-ready functionalities. When your forms and related assets are ready and tested on the local development environment, you can import these forms and related assets to an [!DNL AEM Forms] as a Cloud Service instance for publishing. 

You can use the [development tools](https://experienceleague.adobe.com/docs/experience-manager-65/developing/devtools/dev-tools.html) to write custom code, customize or create new Adaptive Forms components, create a custom prefill service, or modify default configurations of an [!DNL AEM Forms] as a Cloud Service instance. 

-->

## Vereisten

U hebt de volgende software nodig om een lokale ontwikkelomgeving in te stellen. Download deze bestanden voordat u de lokale ontwikkelomgeving instelt:

| Software | Beschrijving | Koppelingen downloaden |
|---|---|---|
| ADOBE EXPERIENCE MANAGER AS A CLOUD SERVICE SDK | SDK omvat [!DNL Adobe Experience Manager] Gereedschappen QuickStart en Dispatcher | Download de nieuwste SDK van [Softwaredistributie](#software-distribution) |  |
| Archief met Adobe Experience Manager Forms-functies (AEM Forms-add-on) | Gereedschappen voor het maken, opmaken en optimaliseren van adaptieve Forms- en andere Adobe Experience Manager Forms-functies | Downloaden van [Softwaredistributie](#software-distribution) |
| (Optioneel) Adobe Experience Manager Forms-referentie-inhoud | Gereedschappen voor het maken, opmaken en optimaliseren van adaptieve Forms- en andere Adobe Experience Manager Forms-functies | Downloaden van [Softwaredistributie](#software-distribution) |
| (Optioneel) Adobe Experience Manager Forms Designer | Gereedschappen voor het maken, opmaken en optimaliseren van adaptieve Forms- en andere Adobe Experience Manager Forms-functies | Downloaden van [Softwaredistributie](#software-distribution) |

### Download de nieuwste versie van software van Software Distribution {#software-distribution}

Als u de nieuwste versie van de SDK van Adobe Experience Manager as a Cloud Service, het Experience Manager Forms-functiearchief (AEM Forms-invoegtoepassing), formulieren en referentiebestanden wilt downloaden van Forms Designer [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html):

1. Aanmelden bij <https://experience.adobe.com/#/downloads> met uw Adobe ID

   >[!NOTE]
   >
   > Uw Adobe-organisatie moet zijn ingericht zodat AEM as a Cloud Service de AEM as a Cloud Service SDK kan downloaden.

1. Ga naar het tabblad **[!UICONTROL AEM as a Cloud Service]**.
1. Sorteren op gepubliceerde datum in aflopende volgorde.
1. Klik op de nieuwste Adobe Experience Manager as a Cloud Service SDK, Experience Manager Forms-functiearchief (AEM Forms add-on), formulieren met naslaginformatie of Forms Designer.
1. De EULA evalueren en aanvaarden. Selecteer de **[!UICONTROL Download]** knop.

## Ontwikkelingshulpmiddelen instellen voor AEM projecten {#setup-development-tools-for-AEM-projects}

Het Adobe Experience Manager Forms-project is een aangepaste codebasis. Het bevat code, configuraties en inhoud die via Cloud Manager worden geïmplementeerd op [!DNL Adobe Experience Manager] as a Cloud Service. De [AEM Project Maven Archetype](https://github.com/adobe/aem-project-archetype) verstrekt de basislijnstructuur voor het project.

Stel de volgende ontwikkelingsprogramma&#39;s in die u voor uw [!DNL Adobe Experience Manager] ontwikkelingsproject:

* [Java™](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#local-development-environment-set-up)
* [Git](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#install-git)
* [Node.js (npm)](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#node-js)
* [Maven](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#install-maven)

Voor gedetailleerde instructies voor het instellen van eerder vermelde ontwikkelingsgereedschappen raadpleegt u [Ontwikkelingshulpmiddelen instellen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html).

## Lokale Experience Manager instellen voor ontwikkeling

De Cloud Service SDK biedt een QuickStart-bestand. Er wordt een lokale versie van Experience Manager uitgevoerd. U kunt de instanties Auteur of Publiceren lokaal uitvoeren.

Hoewel QuickStart een lokale ontwikkelervaring biedt, beschikt QuickStart niet over alle functies die beschikbaar zijn in [!DNL Adobe Experience Manager] as a Cloud Service. Test dus altijd uw functies en code met [!DNL Adobe Experience Manager] as a Cloud Service ontwikkelomgeving voordat de functies naar het werkgebied of de productie worden verplaatst.

Voer de volgende stappen uit om de lokale Experience Manager-omgeving te installeren en te configureren:

* [Downloaden en uitpakken](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) de [!DNL Adobe Experience Manager] AS A CLOUD SERVICE SDK
* [Een instantie Auteur instellen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html?lang=en#set-up-local-aem-author-service)
* [Een instantie voor publiceren instellen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html?lang=en#set-up-local-aem-publish-service)

## Forms-archief toevoegen aan lokale instanties voor auteurs en publiceren en Forms-specifieke gebruikers configureren {#add-forms-archive-configure-users}

Voer de volgende stappen in de vermelde volgorde uit om Forms-archief toe te voegen aan instanties van Experience Managers en formulierspecifieke gebruikers te configureren:

### Installeer het nieuwste Forms add-on functiearchief {#add-forms-archive}

Archief met as a Cloud Service functies van Adobe Experience Manager Forms biedt tools voor het maken, opmaken en optimaliseren van Adaptive Forms in de lokale ontwikkelomgeving. Installeer het pakket om een adaptief formulier te maken en gebruik verschillende andere functies van [!DNL AEM Forms]. Het pakket installeren:

1. Download en extraheer de nieuwste [!DNL AEM Forms] archiveren voor uw besturingssysteem vanuit [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

1. Navigeer naar de map crx-quickstart/install. Als de map niet bestaat, maakt u deze.

1. Stop uw AEM instantie, plaats [!DNL AEM Forms] add-on functiearchief, `aem-forms-addon-<version>.far`, in de installatiemap.
1. Ga naar actief opdrachtvenster en druk op `Ctrl + C` om de SDK opnieuw te starten.

   >[!NOTE]
   >
   > Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

### Gebruikers en machtigingen configureren {#configure-users-and-permissions}

Gebruikers maken zoals Form Developer and Form Practice en [deze gebruikers toevoegen aan vooraf gedefinieerde formuliergroepen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?lang=en#accessing) om hun vereiste toestemmingen te verstrekken. In de onderstaande tabel worden alle typen gebruikers en vooraf gedefinieerde groepen voor elk type formuliergebruiker weergegeven:

| Gebruikerstype | AEM |
|---|---|
| Formulierpraktiserer / | [!DNL forms-users] (AEM Forms-gebruikers), [!DNL template-authors], [!DNL workflow-users], [!DNL workflow-editors], en [!DNL fdm-authors] |
| Formulierontwikkelaar | [!DNL forms-users] (AEM Forms-gebruikers), [!DNL template-authors], [!DNL workflow-users], [!DNL workflow-editors], en [!DNL fdm-authors] |
| Klantervaring als leider of UX Designer | [!DNL forms-users], [!DNL template-authors] |
| AEM-beheerder | [!DNL aem-administrators], [!DNL fd-administrators] |
| Eindgebruiker | Wanneer een gebruiker zich moet aanmelden om een adaptief formulier te bekijken en te verzenden, voegt u deze gebruikers toe aan [!DNL forms-users] groep. </br> Wanneer geen gebruikersverificatie is vereist voor toegang tot Adaptive Forms, wijst u geen groep toe aan dergelijke gebruikers. |

<!--  

## Set up a local AEM instance for development

Perform the following steps in the listed order to set up and configure your local development environment:

1. **Set up an AEM author instance:** You require an author instance to create Adaptive Forms. Download and extract the latest AEM SDK archive. Run the quick start file in author run mode to set up an author instance. For detailed instructions, see [default local instance](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html).  

1. **Install the latest [!DNL AEM Forms] add-on feature archive:** [!DNL AEM Forms] add-on feature archive provides tools to create, style, and optimize Adaptive Forms on the local development environment. Install the package to create an Adaptive Form and use various other features of [!DNL AEM Forms]. To install the package:

    1. Download and extract the latest [!DNL AEM Forms] archive for your operating system from [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

    1. Navigate to the crx-quickstart/install directory. If the folder does not exist, create it.

    1. Stop your Cloud ready AEM instance, place the [!DNL AEM Forms] add-on feature archive, `aem-forms-addon-<version>.far`,  in the install folder, and restart the instance.

1. **Configure users and permissions:** Create users like Form Developer and Form Practitioner a nd add these users to pre-defined forms group to provide them required permissions. The table below lists all types of users and pre-defined groups for each type of forms users:
  
    | User Type | AEM Group |
    |---|---|
    | Form Practitioner  | forms-users (AEM Forms Users), template-authors  |
    | Form Developer | forms-users (AEM Forms Users), template-authors |
    | End-User| everyone* |

    `*` When a user should log in to access or submit Adaptive Forms, add such users to the everyone group.  -->

<!--    
### Set up an AEM project for the development tasks related to local AEM 6.5.5 Forms instance

Use this project to update configurations, create overlays, develop custom Adaptive Form components, and custom code using the local development environment. To set up the project:

1. **Install and configure Maven and set up an AEM project based on Apache Maven:** Apache Maven is an open-source tool for managing software projects. It helps automate builds and provides quality project information. It is the recommended build management tool for AEM projects. For detailed instructions to set up an AEM project based on Apache Maven, see [How to Build AEM Projects using Apache Maven](https://experienceleague.adobe.com/docs/experience-manager-65/developing/devtools/ht-projects-maven.html).

1. Configure the project to use [uber-jar](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/release-notes.html?lang=en#install-aem-forms-jee-installer) version 6.5.5 or later and [[!DNL AEM Forms] Client SDK](https://repo1.maven.org/maven2/com/adobe/aemfd/aemfd-client-sdk/) version 6.0.160 or later.  

1. **Set Up an Integrated Development Environment:**  Set up an IDE of your choice for development, see [Set Up an Integrated Development Environment](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment) for detailed instructions.
 -->

## Lokale ontwikkelomgeving instellen voor Document of Record (DoR){#docker-microservices}

AEM Forms als Cloud Servicen biedt een docker-gebaseerde SDK-omgeving voor een eenvoudigere ontwikkeling van Document of Record en voor het gebruik van andere microservices. U kunt hiermee geen handmatig platformspecifieke binaire bestanden en aanpassingen configureren. Omgeving instellen:

1. Docker installeren en configureren:

   * (Voor Microsoft® Windows) Installeren [Docker Desktop](https://www.docker.com/products/docker-desktop). IT-configuraties `Docker Engine` en `docker-compose` op uw computer.

   * (Apple macOS) Installeren [Docker Desktop voor Mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac). Dit omvat Docker Engine, Docker CLI-client, Docker Compose, Docker Content Trust, Kubernetes en Credential Helper.

   * (Voor Linux®) Installeren [Docker Engine](https://docs.docker.com/engine/install/#server) en [Samenstellen dokken](https://docs.docker.com/compose/install/) op uw computer.

   >[!NOTE]
   >
   > * Voor Apple macOS, de omslagen van de lijst van gewenste personen die lokale AEM instanties van de Auteur bevatten.
   >
   > * Docker Desktop voor Windows ondersteunt twee achtergronden, Hyper-V
   > (oud) en WSL2 (modern). Bestanden delen wordt automatisch
   > beheerd door Docker wanneer het gebruiken van WSL2 (modern). U moet
   > Configureer het delen van bestanden expliciet tijdens het gebruik van Hyper-V (verouderd).

1. Maak een map, bijvoorbeeld aem-sdk, parallel aan de auteur en publiceer instanties. Bijvoorbeeld C:\aem-sdk.

1. Het gereedschap `aem-forms-addon-<version>.zip\aem-forms-addon-native-<version>.zip` bestand.

   ![geëxtraheerde naamformulieren toevoegen aan native](assets/microservice-docker.png)

1. Maak een omgevingsvariabele AEM_HOME en wijs naar de lokale installatie van AEM auteur. Bijvoorbeeld C:\aem\author\.

1. Open sdk.bat of sdk.sh voor bewerking. Stel de AEM_HOME in om naar de lokale installatie van AEM auteur te verwijzen. Bijvoorbeeld C:\aem\author\.

1. Opdrachtprompt openen en naar de `aem-forms-addon-native-<version>` map.

1. Zorg ervoor dat uw lokale AEM Author-instantie actief is. Voer de volgende opdracht uit om de SDK te starten:

   * (in Microsoft® Windows) `sdk.bat start`
   * (op Linux® of Apple macOS) `AEM_HOME=[local AEM Author installation] ./sdk.sh start`

   >[!NOTE]
   >
   > Als u de omgevingsvariabele in het bestand sdk.sh hebt gedefinieerd, is het opgeven van deze variabele op de opdrachtregel optioneel. De optie om de omgevingsvariabele op de opdrachtregel te definiëren, wordt opgegeven om de opdracht uit te voeren zonder het shellscript bij te werken.

   ![start-sdk-command](assets/start-sdk.png)

U kunt nu de lokale ontwikkelomgeving gebruiken om Document of Record te renderen. Upload een XDP-bestand naar uw omgeving en geef het weer om het te testen. Bijvoorbeeld: <http://localhost:4502/libs/xfaforms/profiles/default.print.pdf?template=crx:///content/dam/formsanddocuments/cheque-request.xdp> converteert het XDP-bestand naar het PDF-document.

## Een ontwikkelingsproject voor Forms instellen op basis van het archetype Experience Manager {#forms-cloud-service-local-development-environment}

Met dit project kunt u Adaptive Forms maken, configuratie-updates, overlays implementeren, aangepaste componenten voor adaptieve formulieren maken, testen en aangepaste code op lokale [!DNL Experience Manager Forms] SDK. Na het testen plaatselijk, kunt u het project opstellen aan  [!DNL Experience Manager Forms] as a Cloud Service productie- en niet-productieomgevingen. Wanneer u het project opstelt, worden de volgende activa van AEM Forms ook opgesteld:

| Thema&#39;s | Sjablonen | Formuliergegevensmodellen |
---------|----------|---------
| Canvas 3.0 | Basis | Microsoft® Dynamics 365 |
| Tranquil | Leeg | Salesforce |
| Urbane |   |  |
| Ultramarijn |  |  |
| Beryl |  |  |

>[!NOTE]
>
> Stel AEM project Archetype versie 30 of hoger in om Microsoft® Dynamics 365 en Salesforce-modellen van formuliergegevens te verkrijgen en te gebruiken met AEM Forms as a Cloud Service.
> Opstelling AEM Archetype versie 32 of later gebaseerd project om Tranquil, Urbane, en Ultramarine thema&#39;s met AEM Forms as a Cloud Service te krijgen en te gebruiken.

Het project instellen:

1. **Clone Cloud Manager Git-opslagplaats op uw lokale ontwikkelingsinstantie:**  De gegevensopslagruimte van uw cloudbeheerkit bevat een standaard AEM project. Het is gebaseerd op [AEM Archetype](https://github.com/adobe/aem-project-archetype/). Clone your Cloud Manager Git Repository using Self-Service Git Account Management from Cloud Manager UI om het project over te brengen naar uw lokale ontwikkelomgeving. Zie voor meer informatie over toegang tot de gegevensopslagruimte [Toegang tot opslagplaatsen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/accessing-repos.html).

<!-- 1. 
After the repository is cloned, [integrate your Git repo with Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html)

**Make cloned AEM project compatible with [!DNL AEM Forms] as a Cloud Service:** Remove uber-jar and other non-cloud dependencies from the pom.xml files of the project. You can refer the pom.xml files of the [sample AEM project](assets/FaaCSample.zip) for the list of required dependencies and update your AEM project accordingly. You can also refer [AEM Project Structure](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html) to learn changes required to make an AEM project compatible with AEM as a Cloud Service.  -->

1. **Een [!DNL Experience Manager Forms] als [Cloud Service] project:** Een [!DNL Experience Manager Forms] als [Cloud Service] project op basis van [AEM Archetype](https://github.com/adobe/aem-project-archetype) of hoger. De archetype Help-ontwikkelaars beginnen gemakkelijk te ontwikkelen voor [!DNL AEM Forms] as a Cloud Service. Het bevat ook enkele voorbeeldthema&#39;s en sjablonen waarmee u snel aan de slag kunt gaan.

   Open de opdrachtprompt en voer de onderstaande opdracht uit om een [!DNL Experience Manager Forms] as a Cloud Service project.

   ```shell
   mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate -D archetypeGroupId=com.adobe.aem -D archetypeArtifactId=aem-project-archetype -D archetypeVersion="41" -D appTitle=mysite -D appId=mysite -D groupId=com.mysite -D includeFormsenrollment="y" -D aemVersion="cloud"
   ```

   Wijzig de `appTitle`, `appId`, en `groupId` in het bovenstaande bevel om uw milieu te weerspiegelen. Stel ook de waarde voor includeFormsenrollment, includeFormscommunications en includeFormsheadless in op `y` of `n` afhankelijk van uw licentie en vereisten. IncludeFormadless is verplicht om Adaptive Forms te creëren die op de Componenten van de Kern wordt gebaseerd.

   * Gebruik de `includeFormsenrollment=y` voor Forms-specifieke configuraties, -thema&#39;s, -sjablonen, -kerncomponenten en -afhankelijkheden die vereist zijn voor het maken van een adaptieve Forms. Als u Forms Portal gebruikt, stelt u de optie `includeExamples=y` -optie. Ook worden kerncomponenten van Forms Portal aan het project toegevoegd.

   * Gebruik de `includeFormscommunications=y` -optie om Forms Core-componenten en -afhankelijkheden op te nemen die vereist zijn om de functionaliteit voor communicatie van de klant op te nemen.

     >[!WARNING]
     >
     >* Wanneer u een project Archetype maakt met versie 45, [Projectmap Archetype AEM]Met /pom.xml worden de kerncomponenten van formulieren aanvankelijk ingesteld op versie 2.0.64. Voordat u het project Archetype gaat maken of implementeren, moet u de kerncomponentversie van de formulieren bijwerken naar versie 2.0.62.

1. Implementeer het project in uw lokale ontwikkelomgeving. U kunt het volgende bevel gebruiken om aan uw lokale ontwikkelomgeving op te stellen

   `mvn -PautoInstallPackage clean install`

   Zie voor de volledige lijst met opdrachten [Samenstellen en installeren](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=en#building-and-installing)

1. [De code implementeren op uw [!DNL AEM Forms] as a Cloud Service omgeving](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#customer-releases).

## De lokale gereedschappen voor Dispatcher instellen {#setup-local-dispatcher-tools}

Dispatcher is een Apache HTTP Web server module die een veiligheid en prestatieslaag tussen CDN en AEM publiceer rij verstrekt. Dispatcher is een integraal onderdeel van de algehele architectuur van de Experience Manager en moet onderdeel zijn van de lokale ontwikkelomgeving.

Voer de volgende stappen uit om lokale Dispatcher te vormen en dan Forms-specifieke regels aan het toe te voegen:

### Lokale verzender instellen {#setup-local-dispatcher}

De [!DNL Experience Manager] as a Cloud Service SDK bevat de aanbevolen versie van Dispatcher Tools voor het lokaal configureren, valideren en simuleren van Dispatcher. De Hulpmiddelen van de afzender zijn op docker-Gebaseerde en verstrekken bevel-lijn hulpmiddelen om de configuratiedossiers van de Server en van de Verzender van het Web van Apache HTTP in een compatibel formaat te transpileren en hen op Verzender op te stellen die in de container van het Docker lopen.

Caching op Dispatcher staat [!DNL AEM Forms] om Adaptieve Forms vooraf in te vullen op een client. Het verbetert de rendersnelheid van voorgevulde formulieren.

Voor gedetailleerde instructies voor het instellen van Dispatcher raadpleegt u [De lokale gereedschappen voor Dispatcher instellen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html?lang=en#local-development-environment-set-up)

### Specifieke Forms-regels toevoegen aan Dispatcher {#forms-specific-rules-to-dispatcher}

Voer de volgende stappen uit om de Dispatcher-cache voor Experience Manager Forms as a Cloud Service te configureren:

1. Open uw AEM Project en navigeer naar `\src\conf.dispatcher.d\available_farms`
1. Maak een kopie van het dialoogvenster `default.farm` bestand. Bijvoorbeeld: `forms.farm`.
1. Het gemaakte bestand openen `forms.farm` bestand voor bewerken en vervangen van de volgende code:

   ```json
   #/ignoreUrlParams {
   #/0001 { /glob "*" /type "deny" }
   #/0002 { /glob "q" /type "allow" }
   #}
   ```

   with

   ```json
   /ignoreUrlParams {
   /0001 { /glob "*" /type "deny" }
   /0002 { /glob "dataRef" /type "allow" }
   }
   ```

1. Sla het bestand op en sluit het.
1. Ga naar `conf.d/enabled_farms` en een symbolische koppeling naar de `forms.farm` bestand.
1. Compileer en stel het project aan uw op [!DNL AEM Forms] as a Cloud Service omgeving.

### Overwegingen over caching {#considerations-about-caching}

* Door verzending in cache te plaatsen, is [!DNL AEM Forms] om Adaptieve Forms vooraf in te vullen op een client. Het verbetert de rendersnelheid van voorgevulde formulieren.
* Functies voor beveiligde inhoud die in de cache worden geplaatst, zijn standaard uitgeschakeld. Om de functie in te schakelen, kunt u de instructies uitvoeren die worden gegeven in het dialoogvenster [Beveiligde inhoud in cache plaatsen](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=en) artikel
* De Dispatcher kan sommige Adaptive Forms en verwante Adaptive Forms niet valideren. Ga voor het oplossen van dergelijke problemen naar [[!DNL AEM Forms] Caching](troubleshooting-caching-performance.md) in de sectie Problemen oplossen.
* Gelokaliseerde adaptieve Forms in cache plaatsen:
   * URL-indeling gebruiken `http://host:port/content/forms/af/<afName>.<locale>.html` een gelokaliseerde versie van een adaptief formulier aanvragen in plaats van `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`
   * De optie Landinstelling browser is standaard uitgeschakeld. Als u de landinstelling van de browser wilt wijzigen,
* Wanneer u URL-indeling gebruikt `http://host:port/content/forms/af/<adaptivefName>.html`En en Browser gebruiken in configuratiebeheer is uitgeschakeld, wordt de niet-gelokaliseerde versie van het adaptieve formulier weergegeven. De niet-gelokaliseerde taal is de taal die wordt gebruikt bij het ontwikkelen van het adaptieve formulier. De landinstelling die is geconfigureerd voor uw browser (landinstelling browser) wordt niet in overweging genomen en er wordt een niet-gelokaliseerde versie van het Adaptief formulier weergegeven.
* Wanneer u URL-indeling gebruikt `http://host:port/content/forms/af/<adaptivefName>.html`En als Landinstelling browser gebruiken in configuratiebeheer is ingeschakeld, wordt een gelokaliseerde versie van het Adaptief formulier weergegeven, indien beschikbaar. De taal van het gelokaliseerde Adaptieve formulier is gebaseerd op de landinstelling die is geconfigureerd voor uw browser (landinstelling browser). Het kan leiden tot [alleen de eerste instantie van een adaptief formulier in cache plaatsen]. Als u wilt voorkomen dat het probleem op uw exemplaar optreedt, raadpleegt u [alleen de eerste instantie van een adaptief formulier wordt in de cache geplaatst](troubleshooting-caching-performance.md) in de sectie Problemen oplossen.

Uw lokale ontwikkelomgeving is klaar.

## Adaptieve Forms Core-componenten inschakelen in de as a Cloud Service en lokale ontwikkelomgeving van AEM Forms

Als u Adaptive Forms Core Components inschakelt op AEM Forms as a Cloud Service, kunt u beginnen met het maken, publiceren en leveren van Core Components based Adaptive Forms and Headless Forms met uw AEM Forms Cloud Service-instanties naar meerdere kanalen. Voor het gebruik van Headless Adaptive Forms hebt u de omgeving geschikt voor Adaptive Forms Core Components nodig.

Zie voor instructies [Adaptieve Forms Core-componenten inschakelen in de as a Cloud Service en lokale ontwikkelomgeving van AEM Forms](/help/forms/enable-adaptive-forms-core-components.md)


## Upgrade uw lokale ontwikkelomgeving {#upgrade-your-local-development-environment}

Voor het upgraden van de SDK naar een nieuwe versie moet de volledige lokale ontwikkelomgeving worden vervangen. Dit leidt tot verlies van alle code, configuratie en inhoud in de lokale opslagruimten. Zorg ervoor dat om het even welke code, config, of inhoud die niet zou moeten worden vernietigd veilig aan Git wordt begaan, of uit de lokale instanties van de Experience Manager als CRX-Pakketten wordt uitgevoerd.

### Inhoud verliezen bij het upgraden van de SDK voorkomen {#avoid-content-loss-when-upgrading--SDK}

Door de SDK te upgraden, maakt u in feite een geheel nieuwe auteur- en publicatieversie, waaronder een nieuwe opslagplaats ([AEM project instellen](#forms-cloud-service-local-development-environment)), dat wil zeggen dat eventuele wijzigingen in de opslagplaats van een eerdere SDK verloren gaan. Voor levensvatbare strategieën voor het helpen in het voortbestaan van inhoud tussen de verbeteringen van SDK, zie [Hoe te om inhoudsverlies te vermijden wanneer het bevorderen van de AEM SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html?lang=en#optional-local-aem-runtime-set-up-tasks)

<!--When you update any  Forms-specifc configuration, create overlays, develop custom Adaptive Form components, or develop and test any custom code in AEM project for the development tasks related to local development instance, use the AEM project cloned from the Cloud Manager Git repository to [deploy the custom code and other changes to your [!DNL AEM Forms] as a Cloud Service's production or non-production environment](https://video.tv.adobe.com/v/30191?quality=9).

## Upgrade your local development environment {#update-local-setup}

Update the local AEM setup (AEM SDK) to latest version at least monthly on, or shortly after, the last Thursday of each month, which is the release cadence for AEM as a Cloud Service "feature releases". You can download local AEM SDK from [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

Updating the AEM SDK to a new version requires replacing the entire local development environment, resulting in a loss of all code, configuration and content in the local AEM repositories. Ensure that any code, config or content that should not be destroyed is safely committed to Git, or exported from the local AEM instance as AEM Packages.

### How to avoid content loss when upgrading the AEM SDK {#avoid-content-loss-when-upgrading--AEM-SDK}

Upgrading the AEM SDK is effectively creating a brand new AEM runtime ([Set up a local AEM instance](setup-forms-cloud-service.md)), including a new repository ([Set up AEM project](#forms-cloud-service-local-development-environment)), meaning any changes made to a prior AEM SDK's repository are lost. The following are viable strategies for aiding in persisting content between AEM SDK upgrades, and can be used discretely or in concert:

1. Create a content package dedicated to containing the sample content to aid in development and maintain it in Git. Any content that should be persisted through AEM SDK upgrades would be persisted into this package and re-deployed after upgrading the AEM SDK.
1. Use [oak-upgrade](https://jackrabbit.apache.org/oak/docs/migration.html) with the `includepaths` directive, to copy content from the prior AEM SDK repository to the new AEM SDK repository.
1. Back up any content using AEM Package Manager and content packages on the prior AEM SDK and re-install them on the new AEM SDK.

Remember, using the above approaches to maintain code between AEM SDK upgrades, indicates a development anti-pattern. Non-disposable code should originate in your Development IDE and flow into AEM SDK via deployments.

For information about troubleshooting, stopping local AEM environment, run modes, and deployment, see [Set up local AEM Runtime](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html#local-development-environment-set-up).-->

### Een back-up maken van Forms-specifieke inhoud en deze importeren in een nieuwe SDK-omgeving {#backup-and-import-Forms-specific-content-to-new-SDK-environment}

Een back-up maken van bestaande SDK en elementen verplaatsen naar een nieuwe SDK-omgeving:

* Maak een back-up van uw bestaande inhoud.

* Stel een nieuwe SDK-omgeving in.

* Importeer de back-up naar de nieuwe SDK-omgeving.

### Maak een back-up van uw bestaande inhoud {#create-backup-of-your-existing-content}

Maak een back-up van uw Adaptive Forms, sjablonen, formuliergegevensmodel, thema, configuraties en aangepaste code. U kunt de volgende actie uitvoeren om een back-up te maken:

1. [Downloaden](import-export-forms-templates.md#manage-forms-and-related-assets) Adaptieve Forms, thema&#39;s en PDF forms.
1. Aangepaste formuliersjablonen exporteren.

1. Formuliergegevensmodellen downloaden

1. Bewerkbare sjablonen, cloudconfiguraties en workflowmodel exporteren. Als u alle eerder vermelde items vanuit uw bestaande SDK wilt exporteren, maakt u een [CRX-pakket](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html) met de volgende filters:

   * /conf/ReferenceEditableTemplates
   * /conf/global/settings/cloudconfigs
   * /conf/global/settings/wcm
   * /var/workflow/modellen
   * /conf/global/settings/workflow
1. Exporteer e-mailconfiguraties, verzend en vooraf ingevulde actiecode vanuit uw lokale ontwikkelomgeving. Als u deze instellingen en configuratie wilt exporteren, maakt u een kopie van de volgende mappen en bestanden in uw lokale ontwikkelomgeving:

   * `[Archetype Project in Cloud Service Git]/core/src/main/java/com/<program name>/core/service`
   * `[Archetype Project in Cloud Service Git] /core/src/main/java/com/<program name>/core/servlets/FileAttachmentServlet.java`
   * `[Archetype Project in Cloud Service Git]/ui.apps/src/main/content/jcr_root/apps/<program name>/config`

### De back-up importeren in de nieuwe SDK-omgeving {#import-the-backup-to-your-new-SDK-environment}

Importeer Adaptief Forms, sjablonen, formuliergegevensmodel, thema, configuraties en aangepaste code naar uw nieuwe omgeving. U kunt de volgende actie uitvoeren om een back-up te importeren:

1. [Importeren](import-export-forms-templates.md#manage-forms-and-related-assets) Adaptieve Forms, thema&#39;s en PDF forms naar nieuwe SDK-omgevingen.
1. Importeer Aangepaste formuliersjablonen naar de nieuwe SDK-omgeving.

1. Upload modellen van formuliergegevens naar de nieuwe SDK-omgeving.

1. Bewerkbare sjablonen, cloudconfiguraties en workflowmodel importeren. Als u alle eerder vermelde items in uw nieuwe SDK-omgeving wilt importeren, importeert u het CRX-Package met deze items in uw nieuwe SDK-omgeving.

1. Importeer de code voor e-mailconfiguraties, verzenden en vooraf invullen van handelingen vanuit uw lokale ontwikkelomgeving. Om deze montages en configuratie in te voeren, plaats de volgende dossiers van uw oud project Archetype aan uw nieuw project Archetype:

   * `[Archetype Project in Cloud Service Git]/core/src/main/java/com/<program name>/core/service`
   * `[Archetype Project in Cloud Service Git] /core/src/main/java/com/<program name>/core/servlets/FileAttachmentServlet.java`
   * `[Archetype Project in Cloud Service Git]/ui.apps/src/main/content/jcr_root/apps/<program name>/config`

Uw nieuwe omgeving beschikt nu over formulieren en gerelateerde elementen van een oude omgeving.
