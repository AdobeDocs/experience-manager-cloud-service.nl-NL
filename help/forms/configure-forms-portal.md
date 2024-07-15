---
title: Hoe maak je een Forms Portal op een Experience Manager Sites-pagina?
description: Leer hoe u een Forms Portal kunt maken en de kerncomponenten van een AEM Sites-pagina kunt gebruiken die niet in de verpakking staan.
feature: Adaptive Forms, Foundation Components
exl-id: 13cfe3ba-2e85-46bf-a029-2673de69c626
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '1706'
ht-degree: 0%

---

# Forms Portal toevoegen aan een AEM Sites-pagina {#publish-forms-on-portal}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/creating-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/publish-process-aem-forms/introduction-publishing-forms.html) |
| AEM as a Cloud Service | Dit artikel |

In een typisch vorm-centric portaalplaatsingsscenario, vormen ontwikkeling en portaalontwikkeling zijn twee gescheiden activiteiten. Terwijl formulierontwerpers formulieren ontwerpen en opslaan in een gegevensopslagruimte, maken webontwikkelaars een webtoepassing om formulieren weer te geven en de verzending van formulieren af te handelen. Forms wordt naar de weblaag gekopieerd omdat er geen communicatie is tussen de formulieropslagplaats en de webtoepassing.

Dergelijke scenario&#39;s leiden vaak tot beheerproblemen en productievertragingen. Als er bijvoorbeeld een nieuwere versie van een formulier beschikbaar is in de gegevensopslagruimte, moet u het formulier op de weblaag vervangen, de webtoepassing wijzigen en het formulier opnieuw distribueren op de openbare site. Als u de webtoepassing opnieuw implementeert, kan dit leiden tot serverdowntime. Doorgaans is de serverdowntime een geplande activiteit en daarom kunnen de wijzigingen niet onmiddellijk naar de openbare site worden doorgevoerd.

AEM Forms biedt portalcomponenten die de beheerkosten en productievertragingen verminderen. Met deze componenten kunnen webontwikkelaars een Forms Portal maken en aanpassen op websites die zijn gemaakt met Adobe Experience Manager (AEM).

Met de componenten Form Portal kunt u de volgende functionaliteit toevoegen:

* Formulieren weergeven in aangepaste indelingen. De lay-outs Lijstweergave en Kaart zijn beschikbaar in het vak. U kunt uw eigen aangepaste lay-outs maken.
* Hiermee kunt u aangepaste metagegevens en aangepaste handelingen weergeven terwijl u deze weergeeft.
* Formulieren weergeven die door de gebruikersinterface van AEM Forms zijn gepubliceerd op de publicatie-instantie waar Forms Portal-componenten worden gebruikt.
* Eindgebruikers toestaan formulieren te genereren in de indeling HTML en PDF.
* U kunt zoeken op formulieren op basis van titel en beschrijving inschakelen.
* Gebruik aangepaste CSS om het uiterlijk van de portal aan te passen.
* Koppelingen naar formulieren maken.
* Hier worden concepten en verzendingen weergegeven die betrekking hebben op Adaptive Forms die door de gebruiker zijn gemaakt.

## Componenten van een Forms Portal-pagina {#forms-portal-components}

AEM Forms biedt de volgende poortcomponenten uit de verpakking:

* Zoeken en registreren: met deze component kunt u formulieren uit de formulieropslagplaats op uw portalpagina weergeven en configuratieopties voor het weergeven van formulieren op basis van opgegeven criteria.

* Concepten en verzenden: terwijl in de component Zoeken en opslaan formulieren worden weergegeven die door de auteur van Forms openbaar zijn gemaakt, worden in de component Concepten en verzendingen formulieren weergegeven die zijn opgeslagen als concept voor het later invullen en verzonden formulieren. Deze component verstrekt gepersonaliseerde ervaring aan om het even welke aangemelde gebruiker.

* Koppeling: met deze component kunt u overal op de pagina een koppeling naar een formulier maken.

U kunt [ de uit-van-de-doos componenten van Forms Portal ](#import-forms-portal-components-aem-archetype) van het AEM Archetype van het Project invoeren. Voer na het importeren de volgende configuraties uit:

* [Een externe opslag configureren](#configure-azure-storage-adaptive-forms)

* [ laat de Poortcomponenten van Forms ](#enable-forms-portal-components) toe

* [De Forms Portal-componenten configureren](#configure-forms-portal-components)

## Forms Portal-componenten importeren {#import-forms-portal-components-aem-archetype}

Ga als volgt te werk om Forms Portal-componenten die zich niet in de verpakking bevinden, te importeren op AEM Forms as a Cloud Service:

1. **de bewaarplaats van de Git van Cloud Manager van de Kloon op uw lokale ontwikkelingsinstantie:** Uw bewaarplaats van de Git van Cloud Manager bevat een standaard AEM project. Het is gebaseerd op [ AEM Archetype ](https://github.com/adobe/aem-project-archetype/). Clone your Cloud Manager Git Repository using Self-Service Git Account Management from Cloud Manager UI to bring the project on your local development environment. Voor details bij de toegang tot van de bewaarplaats, zie [ Toegang hebbend tot Bewaarplaatsen ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/accessing-repos.html).

1. **creeer [!DNL Experience Manager Forms] als project van de a [ Cloud Service ]:** creeer [!DNL Experience Manager Forms] als project van de a [ Cloud Service ] dat op [ wordt gebaseerd AEM Archetype 27 ](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-27) of later. De ontwikkelaars van de archetype Help kunnen eenvoudig beginnen met het ontwikkelen voor [!DNL AEM Forms] as a Cloud Service. Het bevat ook enkele voorbeeldthema&#39;s en sjablonen waarmee u snel aan de slag kunt gaan.

   Als u [!DNL Experience Manager Forms] as a Cloud Service project wilt maken, opent u de opdrachtregel en voert u de onderstaande opdracht uit. Stel `includeForms=y` in om [!DNL Forms] -specifieke configuraties, -thema&#39;s en -sjablonen op te nemen.

   ```shell
   mvn -B archetype:generate -DarchetypeGroupId=com.adobe.aem -DarchetypeArtifactId=aem-project-archetype -DarchetypeVersion=30 -DaemVersion="cloud" -DappTitle="My Site" -DappId="mysite" -DgroupId="com.mysite" -DincludeForms="y"
   ```

   Wijzig ook `appTitle` , `appId` en `groupId` in de bovenstaande opdracht om uw omgeving te weerspiegelen.

   Nadat het project klaar is, werk het `<core.forms.components.version>x.y.z</core.forms.components.version>` bezit in het top-level `pom.xml` van het project Archetype bij om op de recentste versie van [ kern-vormen-componenten ](https://github.com/adobe/aem-core-forms-components) in uw `AEM Archetype` project te wijzen.

1. **stel het project aan uw lokale ontwikkelomgeving op:** u kunt het volgende bevel gebruiken om aan uw lokale ontwikkelomgeving op te stellen

   `mvn -PautoInstallPackage clean install`

   Voor de volledige lijst van bevelen, zie [ Bouw en het Installeren ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=en#building-and-installing)

1. [ stel de code aan uw  [!DNL AEM Forms]  as a Cloud Service milieu ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html#embeddeds) op.


## Azure-opslag voor adaptieve Forms configureren {#configure-azure-storage-adaptive-forms}

[[!DNL Experience Manager Forms]  de Integratie van Gegevens ](data-integration.md) verstrekt [!DNL Azure] opslagconfiguratie om vormen met [!DNL Azure] opslagdiensten te integreren. Met FDM (Form Data Model) kunt u Adaptive Forms maken dat met [!DNL Azure] Server werkt om bedrijfsworkflows in te schakelen.

### Azure Storage Configuration maken {#create-azure-storage-configuration}

Voordat u deze stappen uitvoert, moet u controleren of u beschikt over een Azure-opslagaccount en een toegangssleutel waarmee u toegang tot de [!DNL Azure] -opslagaccount kunt toestaan.

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure Storage]** .
1. Selecteer een map om de configuratie te maken en selecteer **[!UICONTROL Create]** .
1. Geef een titel voor de configuratie op in het veld **[!UICONTROL Title]** .
1. Geef de naam van de [!DNL Azure] -opslagaccount op in het veld **[!UICONTROL Azure Storage Account]** .

### Unified Storage-connector configureren voor Forms Portal {#configure-usc-forms-portal}

Voer de volgende stappen uit om de Verenigde Verbinding van de Opslag voor AEM Workflows te vormen:

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Forms]** > **[!UICONTROL Unified Storage Connector]** .
1. Selecteer **[!UICONTROL Azure]** in de vervolgkeuzelijst **[!UICONTROL Storage]** in de sectie **[!UICONTROL Forms Portal]** .
1. Specificeer de [ configuratieweg voor de Azure opslagconfiguratie ](#create-azure-storage-configuration) op het **[!UICONTROL Storage Configuration Path]** gebied.
1. Selecteer **[!UICONTROL Publish]** en selecteer vervolgens **[!UICONTROL Save]** om de configuratie op te slaan.

## Forms Portal-componenten inschakelen {#enable-forms-portal-components}

Als u een kerncomponent (inclusief de onderdelen van de out-of-the-box portal) op een Adobe Experience Manager-site (AEM) wilt gebruiken, moet u een proxycomponent maken en deze inschakelen voor uw site. Voor het creëren van een volmachtscomponent en het toelaten van poortcomponenten, zie [ Gebruikend de Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/using.html?lang=en#create-proxy-components).

Zodra een poortcomponent wordt toegelaten, kunt u het in de auteursinstantie van uw plaatspagina gebruiken.

## Forms Portal-componenten toevoegen en configureren {#configure-forms-portal-components}

U kunt Forms Portal maken en aanpassen op websites die zijn gemaakt met AEM door de portalcomponenten toe te voegen en te configureren. Zorg ervoor dat de [ componenten ](#enable-forms-portal-components) worden toegelaten alvorens hen in het Portaal van Forms te gebruiken.

Als u een component wilt toevoegen, sleept u de component van het deelvenster Componenten naar de container voor de layout op de pagina of selecteert u het pictogram Toevoegen op de container voor de layout en voegt u de component toe vanuit het dialoogvenster [!UICONTROL Insert New Component] .

### Concepten en verzendingen configureren {#configure-drafts-submissions-component}

In het onderdeel Concepten en verzendingen worden formulieren weergegeven die zijn opgeslagen als concept voor het later invullen van formulieren en die zijn verzonden. Om te vormen, selecteer de component en selecteer dan ![ pictogram ](assets/configure_icon.png) vormen. Geef in het dialoogvenster [!UICONTROL Drafts and Submissions] de titel op waarmee de formulierlijst wordt weergegeven als concept of als verzonden formulier. Selecteer ook of de component concepten of verzonden formulieren in kaart- of lijstindeling moet vermelden.

![ pictogram Concepten ](assets/drafts-component.png)

![ het pictogram van Verzending ](assets/submission-listing.png)

### Zoekopdracht &amp; listercomponent configureren {#configure-search-lister-component}

Met de component Zoeken en register kunt u adaptieve formulieren op een pagina weergeven en zoeken op de weergegeven formulieren implementeren.

![ Onderzoek en het pictogram van de Registratie ](assets/search-and-lister-component.png)

Om te vormen, selecteer de component en selecteer dan ![ pictogram ](assets/configure_icon.png) vormen. Het dialoogvenster [!UICONTROL Search and Lister] wordt geopend.

1. Configureer op het tabblad [!UICONTROL Display] het volgende:
   * Geef in **[!UICONTROL Title]** de titel op voor de component Zoeken &amp; register. Aan de hand van een indicatieve titel kunnen gebruikers snel zoeken in de formulierlijst.
   * Selecteer in de lijst **[!UICONTROL Layout]** de indeling die u wilt gebruiken voor de formulieren in kaart- of lijstindeling.
   * Selecteer **[!UICONTROL Hide Search]** en **[!UICONTROL Hide Sorting]** om de zoekopdracht te verbergen en op functies te sorteren.
   * Geef in **[!UICONTROL Tooltip]** de knopinfo op die wordt weergegeven wanneer u de muisaanwijzer op de component plaatst.
1. Geef op het tabblad [!UICONTROL Asset Folder] de locatie op vanwaar de formulieren worden opgehaald en weergegeven op de pagina. U kunt meerdere maplocaties configureren.
1. Configureer op het tabblad [!UICONTROL Results] het maximum aantal formulieren dat per pagina wordt weergegeven. Standaard zijn dit acht formulieren per pagina.

### Koppelingscomponent configureren {#configure-link-component}

Met de koppelingscomponent kunt u koppelingen naar een adaptief formulier op de pagina maken. Om te vormen, selecteer de component en selecteer dan ![ pictogram ](assets/configure_icon.png) vormen. Het dialoogvenster [!UICONTROL Edit Link Component] wordt geopend.

1. Geef op het tabblad [!UICONTROL Display] het bijschrift en de knopinfo voor koppelingen op om de formulieren die door de koppeling worden vertegenwoordigd, gemakkelijker te kunnen identificeren.
1. Geef op het tabblad [!UICONTROL Asset Info] het pad naar de opslagplaats op waar het element wordt opgeslagen.
1. Geef op het tabblad [!UICONTROL Query Params] de aanvullende parameters op in de indeling sleutelwaardepaar. Wanneer op de koppeling wordt geklikt, worden deze aanvullende parameters doorgegeven en samen met het formulier doorgegeven.

## Asynchrone formulierverzending configureren met Adobe Sign {#configure-asynchronous-form-submission-using-adobe-sign}

U kunt configureren om alleen een adaptief formulier te verzenden wanneer alle ontvangers de ondertekeningsceremonie hebben voltooid. Voer de onderstaande stappen uit om de instelling te configureren met Adobe Sign.

1. Open in de auteur een adaptief formulier in de bewerkingsmodus.
1. Selecteer in het linkerdeelvenster het pictogram Eigenschappen en vouw de optie **[!UICONTROL ELECTRONIC SIGNTATURE]** uit.
1. Selecteer **[!UICONTROL Enable Adobe Sign]**. Verschillende configuratieopties worden weergegeven.
1. Selecteer in de sectie [!UICONTROL Submit the form] de optie **[!UICONTROL after every recipient completes signing ceremony]** om de handeling Formulier verzenden te configureren. Hierbij wordt het formulier eerst naar alle ontvangers verzonden voor ondertekening. Nadat alle ontvangers het formulier hebben ondertekend, wordt het formulier alleen verzonden.

## Aangepaste Forms opslaan als concepten {#save-adaptive-forms-as-drafts}

U kunt formulieren opslaan als concepten en deze later invullen. Er zijn twee manieren waarop een formulier wordt opgeslagen als concept:

* Maak bijvoorbeeld een regel voor Formulier opslaan op een formuliercomponent. Als u op de knop klikt, wordt de regel geactiveerd en wordt het formulier opgeslagen in een concept.
* Schakel de functie Automatisch opslaan in, die het formulier opslaat volgens de opgegeven gebeurtenis of na een geconfigureerd tijdsinterval.

### Regels maken om een adaptief formulier op te slaan als concept {#rule-to-save-adaptive-form-as-draft}

Als u bijvoorbeeld een knop wilt gebruiken om de regel Formulier opslaan op een formuliercomponent toe te passen, volgt u de onderstaande stappen:

1. Open in de auteur een adaptief formulier in de bewerkingsmodus.
1. Van de linkerruit, uitgezochte ![ pictogram van Componenten ](assets/components_icon.png) en sleep de [!UICONTROL Button] component aan de vorm.
1. Selecteer de [!UICONTROL Button] component en selecteer dan ![ Configure pictogram ](assets/configure_icon.png).
1. Selecteer het pictogram [!UICONTROL Edit Rules] om de Regeleditor te openen.
1. Selecteer **[!UICONTROL Create]** om de regel te configureren en te maken.
1. Selecteer in de sectie [!UICONTROL When] de optie &quot;wordt geklikt&quot; en selecteer in de sectie [!UICONTROL Then] de optie &quot;Formulier opslaan&quot;.
1. Selecteer **[!UICONTROL Done]** om de regel op te slaan.

### Automatisch opslaan inschakelen {#enable-auto-save}

U kunt de functie voor automatisch opslaan als volgt configureren voor een adaptief formulier:

1. Open in de auteur een adaptief formulier in de bewerkingsmodus.
1. Van de linkerruit, selecteer het ![ pictogram van Eigenschappen ](assets/configure_icon.png) en breid de [!UICONTROL AUTO-SAVE] optie uit.
1. Schakel het selectievakje **[!UICONTROL Enable]** in om het formulier automatisch op te slaan. U kunt het volgende configureren:
* Standaard is de waarde van [!UICONTROL Adaptive Form Event] ingesteld op &quot;true&quot;, wat betekent dat het formulier na elke gebeurtenis automatisch wordt opgeslagen.
* In [!UICONTROL Trigger], vorm om auto-sparen teweeg te brengen gebaseerd op het voorkomen van een gebeurtenis of na een specifiek tijdsinterval.

## Zie ook {#see-also}

{{see-also}}



<!--

>[!MORELIKETHIS]
>
>* [Configure data sources for AEM Forms](/help/forms/configure-data-sources.md)
>* [Configure Azure storage for AEM Forms](/help/forms/configure-azure-storage.md)
>* [Integrate Microsoft Dynamics 365 and Salesforce with Adaptive Forms](/help/forms/configure-msdynamics-salesforce.md)

-->