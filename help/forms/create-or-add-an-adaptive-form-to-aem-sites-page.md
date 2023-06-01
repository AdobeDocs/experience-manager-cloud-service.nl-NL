---
title: Een adaptief formulier maken of toevoegen aan een AEM Sites-pagina
description: Ontdek hoe u moeiteloos een adaptief formulier kunt maken of toevoegen aan uw AEM Sites-pagina. Leer stapsgewijze technieken en tips en trucs voor het integreren van dynamische en aanpasbare formulieren in uw website en het optimaliseren van uw digitale ervaringen voor maximale impact.
feature: Adaptive Forms
hide: true
hidefromtoc: true
source-git-commit: 7dc36220c1f12177037aaa79d864c1ec2209a301
workflow-type: tm+mt
source-wordcount: '1210'
ht-degree: 0%

---


# Een adaptief formulier maken of toevoegen aan een AEM Sites-pagina {#create-or-add-an-adaptive-form-to-aem-sites-page}

Met AEM Forms kunt u naadloos adaptieve formulieren opnemen in uw webpagina&#39;s. Zo kunnen bezoekers formulieren op een gemakkelijke manier invullen en verzenden zonder de pagina waarop ze staan te verlaten. Op die manier kunnen ze moeiteloos betrokken blijven bij andere elementen van de website terwijl ze actief met het formulier communiceren.

U kunt deze functie optimaal benutten door de volgende opties te gebruiken:

* **Een aangepast formulier toevoegen:** Een geheel nieuw formulier maken, dat speciaal aan uw vereisten en ontwerpvoorkeuren is aangepast.

* **Ervaar fragmenten beter:** Vergroot het bereik van uw formulieren door deze toe te voegen aan AEM Experience Fragments, zodat u ze naadloos kunt hergebruiken op meerdere pagina&#39;s of sites.

* **Goedgekeurde sjablonen gebruiken:** Gebruik vooraf goedgekeurde sjablonen om snel formulieren te maken die zijn afgestemd op de brandingrichtlijnen en ontwerpstandaarden van uw organisatie.

* **Bestaande formulieren toevoegen:** U kunt formulieren die u al hebt gemaakt, eenvoudig integreren in uw websites, zodat bezoekers direct met ze kunnen communiceren.

* **Meerdere formulieren toevoegen:**  Voeg meerdere formulieren aan een pagina toe om gebruikers meerdere keuzes te bieden op basis van hun voorkeuren en vereisten. Dit kan een combinatie van geheel nieuwe formulieren en bestaande formulieren zijn.

Met de AEM Sites Editor kunt u snel meerdere formulieren maken en toevoegen aan uw AEM Sites-pagina&#39;s. Met de AEM Sites-editor kunnen auteurs van inhoud naadloze ervaringen met het vastleggen van gegevens maken op een sitepagina met behulp van de kracht van adaptieve formuliercomponenten, zoals dynamisch gedrag, validaties, gegevensintegratie, het genereren van een document van record- en bedrijfsprocesautomatisering. Bovendien kunt u verschillende functies van AEM Sites-pagina&#39;s gebruiken, zoals versioning, adressering, vertaling en beheer voor meerdere sites.

## Doelstelling

* Leer een adaptief formulier te maken met een AEM Sites-editor en een fragment met experts
* Leer hoe u de lay-out en het thema instelt voor een adaptief formulier dat aan een AEM Sites-pagina is toegevoegd en
* Een adaptief formulier maken met een AEM Sites-editor en een fragment met experts


## Overwegingen {#consideration}

AEM Forms biedt adaptieve formuliercontainer en adaptieve Forms - Embed-componenten. Met de component Adaptief Forms - Insluiten kunt u een bestaand adaptief formulier toevoegen of een nieuw formulier maken met de Adaptief Forms-editor.

Wanneer u een formulier maakt of toevoegt met de container voor adaptieve formulieren, worden de formulieren vertaald en gelokaliseerd via de AEM Sites-vertaalstroom. Voor elke taal wordt een afzonderlijke kopie (taalkopie) van de sitepagina en de bijbehorende formulieren gegenereerd en wanneer een auteur van de inhoud een regel in een formulier op de bovenliggende pagina wijzigt, moeten dezelfde wijzigingen worden aangebracht in alle taalkopieën van het formulier. Met de adaptieve formuliercontainer kunt u ook verschillende functies van AEM Sites-pagina&#39;s gebruiken, zoals versioning, adressering, vertaling en beheer voor meerdere sites.

Wanneer u een formulier maakt of toevoegt met de component Adaptief insluiten van formulieren, worden de formulieren vertaald en gelokaliseerd met behulp van de AEM Forms-vertaalstroom. In dit geval wordt één formulier onderhouden en wordt ernaar verwezen in alle taalkopieën van de sitepagina&#39;s. De adaptieve component Form-embed biedt geen toegang tot verschillende functies van AEM Sites-pagina&#39;s, zoals versioning, adressering, vertaling en beheer voor meerdere sites.


## Voordat u begint {#before-you-start}

+++  Adaptieve Forms Core-componenten inschakelen voor uw omgeving

Zorg ervoor dat de [Adaptieve Forms Core-componenten zijn ingeschakeld voor uw as a Cloud Service AEM Forms-omgeving](enable-adaptive-forms-core-components.md).

+++

+++ ** inschakelen[!UICONTROL Adaptive Forms Container]

Inschakelen [!UICONTROL Adaptive Forms Container] in het sjabloonbeleid voert u de volgende stappen uit:

1. Open de AEM Sites-pagina voor bewerking. Als u de pagina wilt openen om te bewerken, selecteert u de pagina en klikt u op Bewerken.
1. Open de sjabloon van uw sitepagina. Als u de sjabloon wilt openen, gaat u naar de [!UICONTROL Page Information] ![Pagina-informatie](/help/forms/assets/Smock_Properties_18_N.svg) > [!UICONTROL Edit Template]. De bijbehorende sjabloon wordt geopend in de sjablooneditor.
1. Klik in de structuurweergave op de knop **[!UICONTROL Policy]** ![Beleid](/help/forms/assets/Smock_FeedManagement_18_N.svg) in de menubalk. In de **[!UICONTROL Allowed Components]** en selecteer de **[!UICONTROL Adaptive Forms Container]**  selectievakje onder **[Projectnaam AEM] - Adaptief formulier**.
1. Klik op **[!UICONTROL Done]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

+++


+++  Adaptieve Forms-clientbibliotheken toevoegen aan uw AEM Sites-pagina

Om volledige functionaliteit van de Adaptive Forms Container component toe te laten, voeg de Customheaderlibs en Customfooterlibs cliëntbibliotheken aan uw AEM Sites pagina toe gebruikend de plaatsingspijpleiding. De bibliotheken toevoegen:

1. Toegang krijgen tot uw [AEM Cloud Service Git Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/repositories.html).
1. Open de map AEM Cloud Service Git Repository in een planningsteksteditor. Bijvoorbeeld Microsoft Visual Code.
1. Open de `ui.apps/src/main/content/jcr_root/apps/[your-project]/components/page/.content.xml` bestand voor bewerken en noteer de waarde van `sling:resourceSuperType`. Noteer bijvoorbeeld de waarde omlaag `core/wcm/components/page/v3/page`.


   ![slingerbron](/help/forms/assets/slingresource.png)

1. Navigeren naar `  ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\` `ui.apps/src/main/content/jcr_root/apps` en maak een mapstructuur die identiek is aan de waarde die in de vorige stap is genoteerd. Als de waarde bijvoorbeeld in de vorige stap vergelijkbaar is met die in de vorige stap, is de uiteindelijke knooppuntstructuur `ui.apps/src/main/content/jcr_root/apps/core/wcm/components/page/v3/page`

   ![bedekkingsstructuur](/help/forms/assets/overlaystructure.png)

1. Maken `customheaderlibs.html` en `customfooterlibs.html` bestanden bij de knooppuntstructuur die in de vorige stap zijn gemaakt en voeg de volgende inhoud toe aan de bestanden:

   ```
        //Customheaderlibs.html
        <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
        <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
        </sly> 
   
        //customfooterlibs.html
        <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
        <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
        </sly> 
   ```

1. [De implementatiepijplijn uitvoeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) om de cliëntbibliotheken aan uw AEM as a Cloud Service milieu op te stellen.

+++

## Een adaptief formulier maken {#create-an-adaptive-form-in-sites-editor-or-experience-fragment}

U kunt een geheel nieuw nieuw formulier maken, dat u specifiek aanpast aan uw vereisten en ontwerpvoorkeuren, rechtstreeks op een pagina met AEM sites of in Experience Fragment. Voor formulieren voor eenmalig gebruik wordt het aanbevolen om rechtstreeks naar een pagina met AEM sites te schrijven, terwijl Experience Fragments ideaal is voor formulieren die opnieuw moeten worden gebruikt op meerdere pagina&#39;s op uw website.

* [Een formulier maken op een AEM Sites-pagina](#create-an-adaptive-form-in-sites-editor)
* [Een formulier maken in een ervaringsfragment](#create-an-adaptive-form-in-experience-fragment)

### Een formulier maken op een AEM Sites-pagina {#create-an-adaptive-form-in-sites-editor}

U kunt de component Adaptief formuliercontainer in de AEM Sites-editor gebruiken om een aangepast formulier te maken. Met deze component kunt u een formulier maken door de formuliercomponenten te slepen en neer te zetten. De formuliercomponenten zijn gebaseerd op kerncomponenten. U kunt deze instellingen eenvoudig aanpassen aan de vereisten van uw organisatie.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

Een adaptief formulier maken op een sitepagina:

1. Open de AEM Sites-pagina in de bewerkingsmodus.
1. Sleep de **[!UICONTROL Adaptive Forms Container]** van de Browser van de Component aan de pagina van Plaatsen. Er wordt een spatie op de pagina voor het formulier gemaakt. U kunt de lay-outmodus gebruiken om de grootte van de containerruimte te wijzigen.
1. Sleep Adaptieve componenten van Form Core naar de containerruimte om het formulier te maken.
1. Voeg de knop Verzenden toe.

Vervolgens stelt u de handeling Verzenden en de geavanceerde eigenschappen in.

### Een formulier maken in een ervaringsfragment {#create-an-adaptive-form-in-experience-fragment}

U kunt het bereik van uw formulieren uitbreiden door ze toe te voegen aan AEM Experience Fragments, zodat u ze naadloos kunt hergebruiken op meerdere pagina&#39;s of sites. U kunt bijvoorbeeld een inschrijvingsformulier voor een nieuwsbrief opnemen in een Experience-fragment. Zo kunt u het fragment op meerdere pagina&#39;s van uw website opnieuw gebruiken, zodat u het formulier niet herhaaldelijk opnieuw hoeft te maken. Alle updates of wijzigingen die worden aangebracht in het inschrijvingsformulier voor nieuwsbrieven binnen het Experience Fragment, worden automatisch doorgegeven aan alle pagina&#39;s waar het wordt gebruikt. Dit stroomlijnt het proces en zorgt voor een naadloze gebruikerservaring en vereenvoudigt het beheer van de formulieren van uw website.

Een adaptief formulier maken in een ervaringsfragment:

## Lay-out van een adaptief formulier wijzigen {#change-layout-of-an-adaptive-form}

In AEM Sites gebruikt u de [Lay-outmodus](/help/sites-cloud/authoring/features/responsive-layout.md) Hiermee wijzigt u de grootte van een adaptieve formuliercontainer die aan een AEM Sites-pagina wordt toegevoegd.
