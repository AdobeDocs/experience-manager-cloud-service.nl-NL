---
title: Hoe kunt u een adaptief formulier toevoegen aan de AEM Sites-pagina?
description: Ontdek hoe u een adaptief formulier kunt maken of toevoegen aan uw AEM Sites-pagina. Leer ook de voordelen en verschillende manieren om formulieren te integreren in uw website.
feature: Adaptive Forms, Foundation Components
Keywords: AF in Sites editor, af in aem sites, aem sites af, add af to a sites page, af aem sites, af sites, create af in a sites page, adaptive form in aem sites, forms aem sites, add form to a sites page, adaptive forms aem sites, add adaptive forms to aem page, create forms in an aem sites page
exl-id: a1846c5d-7b0f-4f48-9d15-96b2a8836a9d
role: User, Developer
source-git-commit: 5b55a280c5b445d366c7bf189b54b51e961f6ec2
workflow-type: tm+mt
source-wordcount: '3206'
ht-degree: 0%

---

# Een adaptief formulier toevoegen aan een AEM Sites-pagina of Ervaar fragment {#create-or-add-an-adaptive-form-to-aem-sites-page}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/create-or-add-an-adaptive-form-to-aem-sites-page.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |

## Overzicht {#overview}

Met AEM Forms kunt u naadloos een formulier toevoegen aan uw AEM Sites-pagina. Zo kunnen bezoekers formulieren op een gemakkelijke manier invullen en verzenden zonder de pagina waarop ze staan te verlaten. Op die manier kunnen ze moeiteloos betrokken blijven bij andere elementen van de website terwijl ze actief met het formulier communiceren.

Met de AEM Page Editor kunt u snel meerdere formulieren maken en toevoegen aan uw AEM Sites-pagina&#39;s. Met de AEM Page Editor kunnen auteurs van inhoud naadloze ervaringen maken met het vastleggen van gegevens op een sitepagina. Hierbij worden adaptieve formuliercomponenten gebruikt, zoals dynamisch gedrag, validaties, gegevensintegratie, het genereren van een document van records en de automatisering van bedrijfsprocessen. Met deze functie kunt u ook verschillende functies van AEM Sites-pagina&#39;s gebruiken, zoals versioning, adressering, vertaling en beheer voor meerdere sites.

AEM Forms Cloud Service biedt adaptieve Form Container en Adaptive Forms - Embed-componenten. Met de component Adaptief Forms - Insluiten kunt u een bestaand adaptief formulier toevoegen of een formulier maken met de Adaptief Forms Editor.

![&#x200B; een voorbeeld van een AanpassingsVorm in een pagina van AEM Sites &#x200B;](/help/forms/assets/adaptive-form-in-sites-page.png)

## Waarom gebruik Adaptive Forms Core Components om een adaptief formulier te maken op een AEM Sites-pagina of Experience Fragment?

Als u in het verleden adaptieve Forms Foundation Component of gewone HTML-formulieren voor uw sites hebt gemaakt, raadt Adobe u aan om Adaptive Forms Core Components te gebruiken om een adaptief formulier te maken op de AEM Sites-pagina of in een fragment met experts. Hiermee kunt u verschillende functies van AEM Sites-pagina&#39;s gebruiken, zoals versioning, doelgericht maken, vertalen en beheer op meerdere sites, waardoor de algehele ervaring met het maken en beheren van formulieren voor Adaptive Forms wordt verbeterd. Hieronder volgen enkele voorbeelden:

* **Versioning:** de pagina&#39;s van AEM Sites bieden [&#x200B; robuuste versieringsmogelijkheden &#x200B;](/help/sites-cloud/authoring/sites-console/page-versions.md) aan, toestaand u om verschillende versies van uw vormen te volgen en te beheren. Op deze manier kunt u wijzigingen aanbrengen en formulieren verbeteren terwijl u de mogelijkheid behoudt om indien nodig terug te draaien naar vorige versies. Versioning zorgt voor een beheerste en georganiseerde benadering van formulierontwikkeling en -ontwikkeling.
* **het richten (Integratie met Adobe Target):** met de pagina&#39;s van AEM Sites die mogelijkheden richten, kunt u de vormervaring voor verschillend publiek [&#x200B; ook &#x200B;](/help/sites-cloud/integrating/integrating-adobe-target.md) personaliseren. Door gebruikerssegmenten en doelcriteria te gebruiken, kunt u de inhoud, het ontwerp of het gedrag van het formulier aanpassen aan specifieke groepen gebruikers. Hierdoor kunt u een gepersonaliseerde en relevante formulierervaring bieden, waardoor de betrokkenheid en conversiesnelheden toenemen.
* **Vertaling:** AEM Sites [&#x200B; naadloze integratie met de vertaaldiensten &#x200B;](/help/sites-cloud/administering/translation/overview.md), toestaand u om vormen in veelvoudige talen gemakkelijk te vertalen. Deze functie vereenvoudigt het lokalisatieproces, zodat uw formulieren toegankelijk zijn voor een wereldwijd publiek. U kunt vertalingen efficiënt beheren in AEM-vertaalprojecten, waardoor u minder tijd en moeite nodig hebt voor meertalige formulierondersteuning. Zie de sectie Overwegingen voor meer informatie over vertaling.
* **Beheer van meerdere plaatsen en Levend Exemplaar:** AEM Sites verstrekt robuust [&#x200B; Multisite Beheer en Levende mogelijkheden van het Exemplaar &#x200B;](/help/sites-cloud/administering/msm/overview.md), toelatend u om veelvoudige websites binnen één enkel milieu tot stand te brengen en te beheren. Met deze functie kunt u nu formulieren hergebruiken op verschillende sites, zodat u consistent bent en dubbel werk kunt voorkomen. Met gecentraliseerde controle en beheer kunt u formulieren efficiënt onderhouden en bijwerken op meerdere websites.
* **Thema&#39;s:** de pagina&#39;s van AEM Sites verstrekken een kader voor het ontwerpen van en het handhaven van verenigbare visuele stijlen over veelvoudige Web-pagina&#39;s. Met deze opties definieert u kleuren, lettertypen, stijlpagina&#39;s en andere visuele elementen die een bijdrage leveren aan het algehele uiterlijk van de website. [&#x200B; u kunt de thema&#39;s gebruiken die voor een pagina van AEM Sites voor een Aanpassings vorm worden ontworpen, die tijd en inspanning besparen &#x200B;](/help/sites-cloud/administering/site-creation/site-themes.md#using-site-themes-using-themes).
* **het Tags toevoegen:** de pagina&#39;s van AEM Sites staan u toe [&#x200B; markeringen of etiketten aan een pagina, een activa, of andere inhoud &#x200B;](/help/implementing/developing/introduction/tagging-framework.md) toe. Tags zijn trefwoorden of metagegevenslabels waarmee u inhoud kunt indelen en indelen op basis van specifieke criteria. U kunt een of meer tags toewijzen aan pagina&#39;s, elementen of andere inhoud in AEM om de zoekopdracht te verbeteren en de elementen te categoriseren.
* **het Vergrendelen en Ontgrendelen van inhoud:** AEM Sites staat gebruikers toe om [&#x200B; toegang en wijzigingen aan pagina&#39;s &#x200B;](/help/sites-cloud/authoring/page-editor/edit-content.md) binnen het milieu van AEM Sites te controleren. Wanneer een pagina is vergrendeld, betekent dit dat deze is beveiligd tegen onbevoegde wijzigingen of bewerkingen door andere gebruikers. Alleen de gebruiker die de inhoud heeft vergrendeld of een aangewezen beheerder kan deze ontgrendelen om wijzigingen toe te staan.

Bovendien gebruikt de Aanpassings Forms in de Redacteur van de Pagina van AEM [&#x200B; Aangepaste Componenten van de Kern van Forms &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL#features). Deze Componenten van Kern verstrekken een standaard en gemakkelijkere methodes om de componenten te stileren en aan te passen, identiek aan [&#x200B; de Componenten van AEM Sites WCM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=nl-NL).


## Hoe maakt u een adaptief formulier of voegt u dit toe aan een AEM Sites-pagina of AEM Experience-fragment? {#various-options-to-creat-or-add-an-adaptive-form-in-aem-sites-page-or-aem-experience-fragment}

U kunt deze functie optimaal benutten door de volgende opties te gebruiken:

* **[creeer en voeg een douane Aangepaste Vorm aan een pagina van AEM Sites toe &#x200B;](#create-an-adaptive-form-in-sites-editor-or-experience-fragment):** u kunt de Aangepaste component van de Container van de Vorm gebruiken om een gloednieuwe vorm van kras te bouwen, die het specifiek aan uw vereisten en ontwerpvoorkeur aanpast.

* **[creeer en voeg een douane Aangepaste Vorm aan een Fragmenten van de Ervaring toe &#x200B;](#create-an-adaptive-form-in-sites-editor):** u kunt het bereik van uw vormen uitbreiden door hen aan de Fragmenten van de Ervaring van AEM toe te voegen, die voor naadloos hergebruik over veelvoudige pagina&#39;s of plaatsen toestaan.

* **[zet een Aangepast die Vorm in het Fragment van de Ervaring &#x200B;](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment) om:** zet een Aangepast die Vorm aan een pagina van AEM Sites aan een Fragment van de Ervaring wordt toegevoegd om de vorm over veelvoudige pagina&#39;s van AEM Sites opnieuw te gebruiken.

* **[creeer en voeg vormen toe die op goedgekeurde malplaatjes aan een pagina van AEM Sites worden gebaseerd:](/help/forms/embed-adaptive-form-aem-sites.md#embed-form-using-adaptive-form-wizzard-aem-sites)** u kunt vooraf goedgekeurde malplaatjes gebruiken om Adaptief Forms snel tot stand te brengen die zich aan de brandende richtlijnen en ontwerpnormen van uw organisatie richten. Deze optie is alleen beschikbaar voor Adaptive Forms die is gemaakt met de Adaptive Forms Editor of de Adaptive Forms - Embed-component.

* **[voeg bestaande vormen aan een pagina van AEM Sites toe:](/help/forms/embed-adaptive-form-aem-sites.md#embed-an-adaptive-form-in-sites-editor)** u kunt vormen gemakkelijk integreren die u reeds in uw websites hebt gecreeerd, toelatend bezoekers om met hen direct in wisselwerking te staan. Deze optie is alleen beschikbaar voor Adaptive Forms die is gemaakt met de Adaptive Forms Editor of de Adaptive Forms - Embed-component.


* **voeg veelvoudige vormen aan een de pagina of Fragment van de Ervaring van AEM Sites toe:** u kunt veelvoudige AanpassingsForms tot stand brengen of toevoegen aan een pagina van AEM Sites om veelvoudige keuzen aan gebruikers te verstrekken die op hun voorkeur en vereisten worden gebaseerd. Dit kan een combinatie van geheel nieuwe formulieren en bestaande formulieren zijn. U kunt de component **[!UICONTROL Adaptive Form Container]** meerdere keren gebruiken om Adaptieve Forms toe te voegen aan een AEM Sites-pagina. U kunt de component **[!UICONTROL Adaptive Forms - Embed]** meerdere keren gebruiken op een AEM Sites-pagina, alleen als de optie **[!UICONTROL Form covers entire width of the frame]** is geselecteerd. Als de optie **[!UICONTROL Form covers entire width of the frame]** niet is ingeschakeld, ondersteunt de AEM Sites-pagina slechts één adaptief formulier dat zonder iframe kan worden gebruikt. Als u meer Adaptieve Forms wilt toevoegen met de component **[!UICONTROL Adaptive Forms - Embed]** , selecteert u de optie **[!UICONTROL Form covers entire width of the frame]** .

## Overwegingen bij het maken van een adaptief formulier in AEM Sites-pagina of AEM Experience Fragment {#consideration}

* Wanneer u een formulier maakt of toevoegt met de container voor adaptieve formulieren, worden de formulieren vertaald en gelokaliseerd via de AEM Sites-vertaalstroom. Voor elke taal wordt een afzonderlijke kopie (taalkopie) van de sitepagina en de bijbehorende formulieren gegenereerd en wanneer een auteur van de inhoud een regel in een formulier op de bovenliggende pagina wijzigt, moeten dezelfde wijzigingen worden aangebracht in alle taalkopieën van het formulier. Met de adaptieve formuliercontainer kunt u ook verschillende functies van AEM Sites-pagina&#39;s gebruiken, zoals versioning, adressering, vertaling en beheer voor meerdere sites.

* Wanneer u een formulier maakt of toevoegt met de component Adaptief insluiten van formulieren, worden de formulieren vertaald en gelokaliseerd met behulp van de AEM Forms-vertaalstroom. In dit geval wordt één formulier onderhouden en wordt ernaar verwezen in alle taalkopieën van de sitepagina&#39;s. De adaptieve component Form-embed biedt geen toegang tot verschillende functies van AEM Sites-pagina&#39;s, zoals versioning, adressering, vertaling en beheer voor meerdere sites.


## Vereisten voor het maken of toevoegen van een adaptief formulier in een AEM Sites-pagina of AEM Experience-fragment {#before-you-start-creating-an-adaptive-form}

Voordat u begint met het maken of een adaptief formulier, voegt u Adaptive Forms Client Libraries toe aan uw AEM Sites-pagina:


### Adaptieve Forms-clientbibliotheken toevoegen aan uw AEM Sites-pagina of -ervaring

**Geval 1: Het gebruiken van Afzonderlijke Componenten van de Pagina van Plaatsen**

Om volledige functionaliteit van de Adaptive Forms Container component toe te laten, voeg de Customheaderlibs en Customfooterlibs cliëntbibliotheken aan uw AEM Sites pagina toe gebruikend de plaatsingspijpleiding. De bibliotheken toevoegen:

1. De toegang en kloon uw [&#x200B; Bewaarplaats van de Bewaarplaats van het Bezit van de Bedieningsruimte van de Dienst van de Wolk van AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/repositories.html?lang=nl-NL).
1. Open de map AEM Cloud Service Git Repository in een abonnementsteksteditor. Bijvoorbeeld Microsoft Visual Code.
1. Open het bestand `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\customheaderlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //Customheaderlibs.html
   
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

1. Open het bestand `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\customfooterlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

1. Open het bestand `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\xfpage\customheaderlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //Customheaderlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

1. Open het bestand `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\xfpage\customfooterlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

1. [&#x200B; stel de plaatsingspijpleiding &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html?lang=nl-NL) in werking om de cliëntbibliotheken aan uw milieu van AEM as a Cloud Service op te stellen.

>[!NOTE]
>
> Hardcode de clientbibliotheek van de aangepaste functie alleen wanneer dit voor alle formulieren is vereist. Voor bibliotheken die verschillen op basis van het formuliertype, voegt u deze toe via sjabloonpaginabeleid, zoals wordt uitgelegd in de volgende sectie.

**Geval 2: Gebruikend de Zelfde Component van de Pagina van Plaatsen**

Neem de runtimeclientbibliotheken of aangepaste functiebibliotheken op in het paginabeleid van de sjabloon die wordt gebruikt voor het maken van pagina&#39;s met formulieren.

1. Open de AEM Sites-pagina of Experience Fragment om te bewerken. Als u de pagina wilt openen om te bewerken, selecteert u de pagina en klikt u op **[!UICONTROL Edit]** .
2. Open de sjabloon van de pagina Sites of Experience Fragment. Om het malplaatje te openen, ga naar **[!UICONTROL Page Information]** ![&#x200B; de Informatie van de Pagina &#x200B;](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Edit Template]**. De bijbehorende sjabloon wordt geopend in de sjablooneditor.
3. Ga naar de **[!UICONTROL Page Information]** ![&#x200B; sectie van de Informatie van de Pagina &#x200B;](/help/forms/assets/Smock_Properties_18_N.svg) van het malplaatje en selecteer de **[!UICONTROL Page Policy]** optie. Hierdoor worden de eigenschappen van de AEM Sites-sjabloon geopend, waarin u aangepaste functies of clientbibliotheken bij uitvoering kunt definiëren.
4. Klik op de knop **[!UICONTROL Add]** op het tabblad **[!UICONTROL Properties]** om nieuwe aangepaste functiebibliotheken of runtimebibliotheken toe te voegen.
5. Klik **[Gedaan]**.

>[!VIDEO](https://video.tv.adobe.com/v/3476178?quality=12&learn=on)

### Adaptieve Forms-container inschakelen voor uw AEM Sites-pagina of Experience-fragment

Voer de volgende stappen uit om [!UICONTROL Adaptive Forms Container] -component in sjabloonbeleid in te schakelen:

1. Open de AEM Sites-pagina of Experience Fragment om te bewerken. Als u de pagina wilt openen om te bewerken, selecteert u de pagina en klikt u op Bewerken.
1. Open de sjabloon van de pagina Sites of Experience Fragment. Om het malplaatje te openen, ga naar [!UICONTROL Page Information] ![&#x200B; de Informatie van de Pagina &#x200B;](/help/forms/assets/Smock_Properties_18_N.svg) > [!UICONTROL Edit Template]. De bijbehorende sjabloon wordt geopend in de sjablooneditor.
1. In de mening van de Structuur, klik het **[!UICONTROL Policy]** ![&#x200B; Beleid &#x200B;](/help/forms/assets/Smock_FeedManagement_18_N.svg) pictogram in de menubar. In de **[!UICONTROL Allowed Components]** lijst en selecteer **[!UICONTROL Adaptive Forms Container]** checkbox onder de **[Naam van het Project van de Archetype van AEM ] - Aangepaste Vorm**.
1. Klik op **[!UICONTROL Done]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

## Een adaptief formulier maken {#create-an-adaptive-form-in-sites-editor-or-experience-fragment}

U kunt een geheel nieuw formulier maken en dit aanpassen aan uw vereisten en ontwerpvoorkeuren, rechtstreeks op een AEM Sites-pagina of in Experience Fragment. Voor formulieren voor eenmalig gebruik wordt direct schrijven naar een AEM Sites-pagina aanbevolen, terwijl Experience Fragments ideaal zijn voor formulieren die opnieuw moeten worden gebruikt op meerdere pagina&#39;s op uw website.

* [Een formulier maken op een AEM Sites-pagina](#create-an-adaptive-form-in-sites-editor)
* [&#x200B; creeer een vorm in een Fragment van de Ervaring &#x200B;](#create-an-adaptive-form-in-experience-fragment)
* [&#x200B; zet een Aangepast Vorm in de pagina van AEM Sites in een Fragment van de Ervaring om &#x200B;](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment)

### Een formulier maken op een AEM Sites-pagina {#create-an-adaptive-form-in-sites-editor}

Met de component Adaptief formuliercontainer in de AEM Page Editor kunt u een aangepast formulier maken. Met de component kunt u een formulier maken door de formuliercomponenten te slepen en neer te zetten. De formuliercomponenten zijn gebaseerd op kerncomponenten. U kunt deze instellingen eenvoudig aanpassen aan de vereisten van uw organisatie.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

Een adaptief formulier maken op een sitepagina:

1. Open de AEM Sites-pagina in de bewerkingsmodus.
1. Sleep de component **[!UICONTROL Adaptive Forms Container]** van de Componentbrowser naar de pagina Sites. Er wordt een spatie op de pagina voor het formulier gemaakt. U kunt de lay-outmodus gebruiken om de grootte van de containerruimte te wijzigen.
1. Sleep Adaptieve componenten van Form Core naar de containerruimte om het formulier te maken.
1. Voeg de knop Verzenden toe.

Daarna, plaatst u [&#x200B; de Submit Actie &#x200B;](#configure-submit-action-for-form) en geavanceerde eigenschappen.

### Een formulier maken in een ervaringsfragment {#create-an-adaptive-form-in-experience-fragment}

U kunt het bereik van uw formulieren uitbreiden door ze toe te voegen aan AEM Experience Fragments, zodat u ze naadloos kunt hergebruiken op meerdere pagina&#39;s of sites. U kunt bijvoorbeeld een inschrijvingsformulier voor een nieuwsbrief opnemen in een Experience-fragment. Zo kunt u het fragment op meerdere pagina&#39;s van uw website opnieuw gebruiken, zodat u het formulier niet herhaaldelijk opnieuw hoeft te maken. Alle updates of wijzigingen die worden aangebracht in het inschrijvingsformulier voor nieuwsbrieven binnen het Experience Fragment, worden automatisch doorgegeven aan alle pagina&#39;s waar het wordt gebruikt. Dit stroomlijnt het proces en zorgt voor een naadloze gebruikerservaring en vereenvoudigt het beheer van de formulieren van uw website.

Een adaptief formulier maken in een ervaringsfragment:

1. Open een ervaringsfragment.
1. Sleep de component **[!UICONTROL Adaptive Forms Container]** van de Componentbrowser naar het fragment van de Experience.
1. Sleep Adaptieve componenten van Form Core naar de containerruimte in het Experience Fragment om het formulier te maken.
1. Voeg de knop Verzenden toe.

Daarna, plaatst u [&#x200B; de Submit Actie &#x200B;](#configure-submit-action-for-form) en geavanceerde eigenschappen.

### Een formulier in een AEM Sites-pagina converteren naar een Experience-fragment {#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment}

U kunt een bestaand adaptief formulier in een sitepagina-editor converteren naar een ervaringsfragment om het formulier te hergebruiken op meerdere pagina&#39;s of sites.

Een adaptief formulier in AEM Sites-pagina converteren naar een Experience-fragment:

1. Open de AEM Sites-pagina met het adaptieve formulier (in de Adaptive Forms Container-component) in de bewerkingsmodus.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Adaptive Forms Container]** die als host fungeert voor het adaptieve formulier. Een AEM Sites-pagina kan meerdere Adaptive Forms hosten. Selecteer dus zorgvuldig de juiste adaptieve Forms-container.
1. Voor de menubar, selecteer ![&#x200B; Bekeerling aan het pictogram van het Ervingspictogram &#x200B;](/help/forms/assets/Smock_FilingCabinet_18_N.svg) Omzetten in het de variatiepictogram van het Fragment van de Ervaring.
   ![&#x200B; klik het embleem van het dossierkabinet om een Aangepast Vorm in de pagina van AEM Sites in een Fragment van de Ervaring om te zetten &#x200B;](/help/forms/assets/convert-form-in-sites-page-to-an-experience-fragment.png)

   Er wordt een dialoogvenster weergegeven waarin u de container Adaptief formulier kunt converteren naar een nieuw Ervaringsfragment of een bestaand Erviteitsfragment kunt uitbreiden
1. Stel in het dialoogvenster Converteren naar ervaringsfragmentvariatie waarden in voor de volgende opties:

   * **Actie:** Uitgezocht om een Fragment van de Ervaring tot stand te brengen of aan een bestaand Fragment van de Ervaring toe te voegen.
   * **de weg van de Ouder:** specificeer weg van de omslag om het Fragment van de Ervaring binnen te ontvangen. De optie is alleen beschikbaar voor het maken van een ervaringsfragment.
   * **Malplaatje:** specificeer weg van het malplaatje van het Fragment van de Ervaring. Als u geen malplaatje van het Fragment van de Ervaring hebt, [&#x200B; creeer het &#x200B;](/help/implementing/developing/extending/experience-fragments.md). De optie is alleen beschikbaar als u een adaptief formulier toevoegt aan een bestaand ervaringsfragment.
   * **titel van het Fragment:** specificeer titel van het Fragment van de Ervaring. De titel identificeert op unieke wijze een ervaringsfragment


## Verzendhandeling voor een formulier configureren in AEM Sites-pagina of Expereinfragment {#configure-submit-action-for-form}

Met een handeling Verzenden kunt u de bestemming kiezen van gegevens die zijn vastgelegd via een adaptief formulier. Deze wordt geactiveerd wanneer een gebruiker op de knop Verzenden klikt op een adaptief formulier. Aangepaste formulieren bevatten enkele van de verzendacties. U kunt ook een standaardverzendactie uitbreiden om uw eigen aangepaste verzendactie te maken. Een handeling verzenden voor uw formulier configureren:

1. Open de AEM Page Editor of Experience Fragment dat het adaptieve formulier bevat.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Adaptive Forms Container]** die als host fungeert voor het adaptieve formulier. Een AEM Sites-pagina kan meerdere Adaptive Forms hosten. Selecteer dus zorgvuldig de juiste adaptieve Forms-container.
1. Klik het AanpassingsEigenschappen van de Container van de Vorm ![&#x200B; AanpassingsContainer eigenschappen &#x200B;](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer voor het configureren van verzendacties wordt geopend.
   ![&#x200B; klik het pictogram van de Sleutel om de Aangepaste de dialoogdoos van de Container van de Vorm te openen om Submit Actie voor een Aangepaste Vorm te vormen &#x200B;](/help/forms/assets/adaptive-forms-container.png)
1. Selecteer en vorm een Submit actie, die op uw vereisten wordt gebaseerd. Voor gedetailleerde informatie over Submit Acties, zie [&#x200B; Aangepaste Vorm verzenden Actie &#x200B;](/help/forms/configuring-submit-actions.md)


## Een schema of formuliergegevensmodel (FDM) configureren voor een formulier in een AEM Sites-pagina of -fragment met experts {#configure-schema-or-data-model-for-form}

Met het FDM (Form Data Model) kunt u een formulier verbinden met een Data Source om gegevens te verzenden en te ontvangen op basis van gebruikersacties. U kunt een formulier ook verbinden met een JSON-schema om de verzonden gegevens in een vooraf gedefinieerde indeling te ontvangen. Gebaseerd op het vereiste, verbind uw vorm met een schema JSON of het model van de Gegevens van de Vorm (FDM):

* [&#x200B; creeer een Schema JSON en upload aan uw milieu &#x200B;](/help/forms/adaptive-form-json-schema-form-model.md) of,
* [Een formuliergegevensmodel (FDM) maken](/help/forms/create-form-data-models.md)

Een JSON-schema of FDM (Form Data Model) voor uw formulier configureren:

1. Open de AEM Page Editor of Experience Fragment dat het adaptieve formulier bevat.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Adaptive Forms Container]** die als host fungeert voor het adaptieve formulier. Een AEM Sites-pagina kan meerdere Adaptive Forms hosten. Selecteer dus zorgvuldig de juiste adaptieve Forms-container.
1. Klik het AanpassingsEigenschappen van de Container van de Vorm ![&#x200B; AanpassingsContainer eigenschappen &#x200B;](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer voor het configureren van gegevensmodellen wordt geopend.
   ![&#x200B; klik het pictogram van de Sleutel om een Modellen van Gegevens voor de Aangepaste Vorm &#x200B;](/help/forms/assets/form-data-model-adaptive-forms-container.png) te vormen
1. Selecteer en configureer een JSON-schema of formuliergegevensmodel (FDM) op basis van uw vereisten. Voor gedetailleerde informatie over Submit Acties, zie [&#x200B; Aangepaste Vorm verzenden Actie &#x200B;](/help/forms/configuring-submit-actions.md).

   * Als u de optie **[!UICONTROL Form Model]** selecteert, gebruikt u de optie **[!UICONTROL Select Form Data Model]** om een vooraf geconfigureerd formuliergegevensmodel (FDM) te selecteren.
   * Als u de optie **[!UICONTROL Schema]** selecteert, gebruikt u de optie **[!UICONTROL Schema]** om een JSON-schema voor uw formulier te selecteren.

1. Klik op **[!UICONTROL Done]**.

## Een vooraf ingevulde service voor een formulier configureren in AEM Sites-pagina of fragment met experts {#configure-prefill-service-for-form}

U kunt de Prefill-service gebruiken om automatisch velden van een adaptief formulier in te vullen met bestaande gegevens. Wanneer een gebruiker een formulier opent, worden de waarden voor die velden vooraf ingevuld. U kunt:

* [Een aangepaste prefill-service maken](/help/forms/prepopulate-adaptive-form-fields.md)
* [Vooraf ingevulde service Formuliergegevensmodel gebruiken](#fdm-prefill-service)

### De service Vooraf invullen van formuliergegevensmodel gebruiken om velden van een formulier vooraf in te vullen op een AEM Sites-pagina of een fragment van een expert {#fdm-prefill-service}

U kunt de service Vooraf invullen van formuliergegevensmodel gebruiken om velden van een adaptief formulier vooraf in te vullen in AEM Sites-pagina of fragment van een expert met behulp van een formuliergegevensmodel of een aangepaste pre-fill-service. Het model van Gegevens van de Vorm Prefill de dienst gebruikt [&#x200B; krijgt Dienst van het gevormde Model van Gegevens van de Vorm &#x200B;](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) om gegevens terug te winnen. Als u de service Vooraf invullen van formuliergegevensmodel wilt gebruiken voor een adaptief formulier:

1. Open de AEM Page Editor of Experience Fragment dat het adaptieve formulier bevat.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Adaptive Forms Container]** die als host fungeert voor het adaptieve formulier. Een AEM Sites-pagina kan meerdere Adaptive Forms hosten. Selecteer dus zorgvuldig de juiste adaptieve Forms-container.
1. Klik het AanpassingsEigenschappen van de Container van de Vorm ![&#x200B; AanpassingsContainer eigenschappen &#x200B;](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer voor het configureren van gegevensmodellen wordt geopend.
   ![&#x200B; klik het pictogram van de Sleutel om de Aangepaste de dialoogdoos van de Container van de Vorm te openen om de prefill dienst voor de Aangepaste Vorm te vormen &#x200B;](/help/forms/assets/adaptive-forms-container.png)
1. Selecteer een formuliergegevensmodel. Open de tab **[!UICONTROL Basic]** . Selecteer **[!UICONTROL Form Data Model Prefill Service]** in de service Prefill.
1. Klik op **[!UICONTROL Done]**. Uw adaptieve formulier is nu geconfigureerd voor vooraf invullen van formuliergegevensmodel. U kunt nu, de [&#x200B; regelredacteur &#x200B;](rule-editor.md) gebruiken om regels tot stand te brengen om gebieden van de vorm vooraf in te vullen.


## Leid de gebruiker om naar een pagina of toon een dank u bericht bij de vormverzending

Bij het verzenden van een formulier kunt u de gebruiker omleiden naar een andere webpagina of een bericht. Om de gebruiker om te leiden of het dank u bericht te vormen:

1. Open de AEM Page Editor of Experience Fragment dat het adaptieve formulier bevat.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Adaptive Forms Container]** die als host fungeert voor het adaptieve formulier. Een AEM Sites-pagina kan meerdere Adaptive Forms hosten. Selecteer dus zorgvuldig de juiste adaptieve Forms-container.

1. Open de tab **[!UICONTROL Submission]** .

   * Als u een omleidings-URL wilt configureren, bijvoorbeeld bij Verzenden, selecteert u de optie **[!UICONTROL Redirect to URL]** en bladert en selecteert u een AEM Sites-pagina of geeft u de URL van een externe pagina op.
   * Als u een aangepast bericht of een bedankbericht wilt configureren, bijvoorbeeld bij Verzenden, selecteert u de optie **[!UICONTROL Show Message]** en geeft u een bericht op in het vak **[!UICONTROL Message content]** . Het is een tekstvak met tekstopmaak. U kunt de optie Volledig scherm gebruiken om alle beschikbare tekstitems weer te geven.


