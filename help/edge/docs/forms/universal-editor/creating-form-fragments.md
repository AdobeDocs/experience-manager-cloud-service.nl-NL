---
title: Formulierfragmenten maken voor op WYSIWYG gebaseerde authoring
description: Leer hoe u formulierfragmenten maakt in de Universal Editor en deze toevoegt aan formulieren.
feature: Edge Delivery Services
role: Admin, User, Developer
exl-id: 7b0d4c7f-f82f-407b-8e25-b725108f8455
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '1386'
ht-degree: 0%

---

# Formulierfragmenten maken in Universal Editor

<span class="preview"> Deze functie is beschikbaar via het programma voor vroege toegang. Om toegang te verzoeken, verzend een e-mail met uw GitHub organisatienaam en bewaarplaatsnaam van uw officieel adres aan <a href="mailto:aem-forms-ea@adobe.com"> aem-forms-ea@adobe.com </a>. Bijvoorbeeld, als de bewaarplaats URL https://github.com/adobe/abc is, is de organisatienaam adobe en de bewaarplaatsnaam abc.</span>

<span class="preview"> Dit is een pre-versieeigenschap en toegankelijk door ons [ pre-vrijgavekanaal ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features). </span>

Forms bevat vaak algemene secties zoals contactgegevens, identificatiegegevens of toestemmingsovereenkomsten. De formulierontwikkelaars maken deze secties telkens wanneer ze een nieuw formulier maken. Dit is een herhalend en tijdrovend formulier.
Om deze dubbele inspanning te elimineren, verstrekt de Universele Redacteur een manier om herbruikbare vormsegmenten, zoals panelen of groepen gebieden, slechts eenmaal tot stand te brengen en hen over diverse vormen opnieuw te gebruiken. Deze herbruikbare, modulaire en standalone segmenten worden formulierfragmenten genoemd. Hetzelfde fragment voor noodcontact kan bijvoorbeeld worden gebruikt in verschillende secties van een formulier, zoals voor de contactgegevens van de werknemer en de toezichthouder.

Aan het einde van het artikel leert u hoe u fragmenten kunt maken en gebruiken in formulieren met de Universal Editor.

## Functies van Edge Delivery Services-formulierfragmenten

- **Behoud consistentie met vormfragmenten**
U kunt fragmenten in verschillende formulieren integreren, zodat u consistente indelingen en gestandaardiseerde inhoud kunt behouden.

  >[!NOTE]
  >
  > Met de aanpak &#39;Eenmaal wijzigen, Overal spiegelen&#39; wordt elke update die in een fragment wordt uitgevoerd, automatisch toegepast op alle formulieren in de voorbeeldmodus. In de modus Publiceren moet u het fragment echter publiceren of het formulier opnieuw publiceren om de wijzigingen door te voeren.

- **Toevoegend vormfragmenten veelvoudige tijden binnen vorm**
U kunt een formulierfragment meerdere keren toevoegen in een formulier en de eigenschappen voor de gegevensbinding ervan configureren voor gegevensbronnen of schema&#39;s.

- **Gebruikend fragmenten binnen fragmenten**
U kunt geneste formulierfragmenten maken, wat betekent dat u een fragment kunt toevoegen aan een ander fragment en dat u een geneste fragmentstructuur kunt hebben.

  >[!NOTE]
  >
  > U kunt een fragment niet nesten binnen zichzelf, omdat dit recursieve verwijzingen en onbedoeld gedrag kan veroorzaken, wat tot fouten of renderingproblemen kan leiden.

## Overwegingen bij het gebruik van Edge Delivery Services-formulierfragmenten

- U moet dezelfde GitHub-URL toevoegen in zowel het fragment als het formulier waar u het fragment wilt gebruiken.
- U kunt een formulierfragment niet bewerken in een formulier. Als u wijzigingen wilt aanbrengen, wijzigt u het zelfstandige formulierfragment.

## Vereisten

- [ opstelling uw bewaarplaats GitHub ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template) om een verbinding tussen uw milieu van AEM en de bewaarplaats te vestigen GitHub.
- Als u reeds Edge Delivery Services gebruikt, voeg de recentste versie van het [ Aangepaste blok van Forms ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) aan uw bewaarplaats GitHub toe.
- De AEM Forms Author-instantie bevat een sjabloon op basis van Edge Delivery Services.
- Houd de URL van uw AEM Forms as a Cloud Service-auteurinstantie en uw GitHub Repository handig.

## Werken met Edge Delivery Services-formulierfragmenten

U kunt Edge Delivery Services-formulierfragmenten maken in de Universal Editor en de gemaakte fragmenten toevoegen aan Edge Delivery Services-formulieren. U kunt de volgende handelingen uitvoeren met Edge Delivery Services-formulierfragmenten:

- [Formulierfragmenten maken](#creating-form-fragments)
- [Formulierfragmenten toevoegen aan een formulier](#adding-form-fragments-to-a-form)
- [Formulierfragmenten beheren](#managing-form-fragments)

### Formulierfragmenten maken

Voer de volgende stappen uit om een formulierfragment te maken in de Universal Editor:

1. Meld u aan bij uw AEM Forms as a Cloud Service-auteur-exemplaar.
1. Selecteer **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .
1. Klik **creëren > het AanpassingsFragment van de Vorm**.

   ![ creeer fragment ](/help/edge/docs/forms/universal-editor/assets/create-fragment.png)

   De **Create Aangepaste tovenaar van het Fragment van de Vorm** verschijnt.
1. Selecteer het op Edge Delivery Services gebaseerde malplaatje van het **Uitgezochte Malplaatje** lusje en klik **[!UICONTROL Next]**.
   ![ Uitgezochte het malplaatje van Edge Delivery Services ](/help/edge/docs/forms/universal-editor/assets/create-form-fragment.png)

1. Geef een titel, naam, beschrijving en tags voor het fragment op. Zorg ervoor dat u een unieke naam voor het fragment opgeeft. Als een ander fragment met dezelfde naam bestaat, kan het fragment niet worden gemaakt.
1. Specificeer **GitHub URL**. Als uw GitHub-opslagplaats bijvoorbeeld de naam `edsforms` heeft, bevindt deze zich onder de account `wkndforms` , is de URL `https://github.com/wkndforms/edsforms` .

   ![ basiseigenschappen ](/help/edge/docs/forms/universal-editor/assets/fragment-basic-properties.png)

1. (Facultatief) klik om het **Model van de Vorm** lusje te openen, en van **Uitgezocht van** drop-down menu, selecteer één van de volgende modellen voor het fragment:

   ![ modeltype van vertoningen in het Modellusje van de Vorm ](/help/edge/docs/forms/universal-editor/assets/select-fdm-for-fragment.png)

   - **Model van de Gegevens van de Vorm (FDM)**: Integreer de voorwerpen en de diensten van het gegevensmodel van gegevensbronnen in uw fragment. Kies FDM (Form Data Model) als in uw formulier gegevens uit meerdere bronnen moeten worden gelezen en geschreven.

   - **JSON Schema**: Integreer uw vorm met een achterste deelsysteem door een schema te associëren JSON dat de gegevensstructuur bepaalt. Hiermee kunt u dynamische inhoud toevoegen met behulp van de schema-elementen.
   - **niets**: Specificeert om het fragment van kras tot stand te brengen zonder enig vormmodel te gebruiken.

   >[!NOTE]
   >
   > Leren hoe te om vormen of fragmenten met een Model van de Gegevens van de Vorm (FDM) in de Universele Redacteur te integreren om diverse achterste gegevensbronnen te gebruiken, zie [ vormen met het Model van de Gegevens van de Vorm in Universele Redacteur ](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md) integreren.

1. (Facultatief) specificeer **publiceer Datum** of **publiceer Datum** voor het fragment in het **Geavanceerde** lusje.

   ![ Geavanceerd lusje ](/help/edge/docs/forms/universal-editor/assets/advanced-properties-fragment.png)
1. Klik **creëren** en een tovenaar verschijnt.

   ![ geef fragment ](/help/edge/docs/forms/universal-editor/assets/edit-fragment.png) uit

1. Klik **uitgeven** en het gecreeerde fragment met een standaardmalplaatje opent in Universele Redacteur voor creatie.

   ![ Fragment in Universele Redacteur voor creatie ](/help/edge/docs/forms/universal-editor/assets/fragment-in-ue.png)

   In de bewerkingsmodus kunt u alle formuliercomponenten aan het fragment toevoegen. Leren hoe te om een fragment in de Universele Redacteur tot stand te brengen, verwijs naar [ Begonnen het Worden met Edge Delivery Services voor AEM Forms gebruikend Universeel artikel van de Redacteur ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg).

   In de onderstaande schermafbeelding wordt de `contact fragment` weergegeven die in de Universal Editor is gemaakt.

   ![ Schermafbeelding van een voltooid fragment van de de vorm van contactdetails in de Universele Redacteur, die gebieden voor naam, telefoon, e-mail, en adres tonen die over veelvoudige vormen kunnen worden opnieuw gebruikt ](/help/edge/docs/forms/universal-editor/assets/contact-fragment.png)

   Zodra u het fragment hebt gecreeerd, kunt u [ toevoegen het gecreeerd fragment in Edge Delivery Services Forms ](#adding-form-fragments-in-forms).

### Formulierfragmenten toevoegen aan een formulier

Laten we een eenvoudig `Employee Details` formulier maken dat zowel werknemers- als supervisorinformatie bevat. U kunt het fragment `Contact Details` gebruiken in zowel de deelvensters Medewerker als Supervisor. Voer de volgende stappen uit om het formulierfragment in het formulier te gebruiken:

1. Open het formulier in de bewerkingsmodus.
1. Voeg de component Formulierfragment toe aan het formulier.
1. Open Inhoudsbrowser, en navigeer aan de **[!UICONTROL Adaptive Form]** component in de **boom van de Inhoud**.
1. Navigeer naar de sectie waar u een fragment wilt toevoegen. Bijvoorbeeld, navigeer aan het **paneel van de Details van de Werknemer**.

   ![ ga aan sectie ](/help/edge/docs/forms/universal-editor/assets/navigate-to-section.png)

1. Klik het **[!UICONTROL Add]** pictogram en voeg de **[!UICONTROL Form Fragment]** component van de **Aangepaste lijst van de Componenten van de Vorm** toe.
   ![ voeg het Fragment van de Vorm ](/help/edge/docs/forms/universal-editor/assets/add-fragment.png) toe

   Wanneer u de component **[!UICONTROL Form Fragment]** selecteert, wordt het fragment aan het formulier toegevoegd. U kunt de eigenschappen van het toegevoegde fragment vormen door zijn **Eigenschappen** te openen. Bijvoorbeeld, verberg de titel van het fragment van zijn **Eigenschappen**.

   ![ Vormend eigenschappen van fragment ](/help/edge/docs/forms/universal-editor/assets/fragment-properties.png)

1. Selecteer de **verwijzing van het Fragment** in **Basis** tabel. Alle fragmenten die beschikbaar zijn voor het formulier, worden weergegeven, afhankelijk van het formuliermodel.

   Navigeer bijvoorbeeld naar `/content/forms/af` en selecteer het `Contact Details` -fragment.

   ![ Uitgezochte Fragment ](/help/edge/docs/forms/universal-editor/assets/select-fragment.png)

1. Klik op **[!UICONTROL Select]**.

   Het formulierfragment wordt toegevoegd ten opzichte van het formulier en blijft gesynchroniseerd met het zelfstandige formulierfragment.

   ![ Schermschot die het fragment van contactdetails tonen met succes in een werknemersvorm binnen de Universele Redacteur wordt geïntegreerd, die aantoont hoe de fragmenten hun structuur handhaven wanneer hergebruikt ](/help/edge/docs/forms/universal-editor/assets/fragment-in-form.png)

   U kunt voorproef de vorm zien hoe de vorm op de **wijze van de Voorproef** verschijnt.

   ![ Voorproef ](/help/edge/docs/forms/universal-editor/assets/preview-form-with-fragment.png)

   Op dezelfde manier kunt u stap 3 tot en met 7 herhalen om het fragment `Contact Details` in te voegen voor het deelvenster `Supervisor Details` .

   ![ Vorm van de Details van de Werknemer ](/help/edge/docs/forms/universal-editor/assets/employee-detail-form-with-fragments.png)

### Formulierfragmenten beheren

U kunt verschillende bewerkingen uitvoeren op formulierfragmenten via de gebruikersinterface van AEM Forms.

1. Meld u aan bij uw AEM Forms as a Cloud Service-auteur-exemplaar.
1. Selecteer **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .

1. Selecteer een formulierfragment en op de werkbalk worden de volgende bewerkingen weergegeven die u op het geselecteerde fragment kunt uitvoeren.

   ![ beheert fragment ](/help/edge/docs/forms/universal-editor/assets/manage-fragment.png)

   <table>
    <tbody>
    <tr>
   <td><p><strong>Bewerking</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
    </tr>
    <tr>
   <td><p>Bewerken</p> </td>
   <td><p>Hiermee opent u het formulierfragment in de bewerkingsmodus. <br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Eigenschappen</p> </td>
   <td><p>Bevat opties voor het wijzigen van de eigenschappen van het formulierfragment. <br /> <br /> </p> </td>
    </tr>
    <td><p>Kopiëren</p> </td>
   <td><p> Hier vindt u opties waarmee u het formulierfragment kunt kopiëren en op de gewenste locatie kunt plakken. <br /> <br /> </p> </td>
    </tr>
   <tr>
   <td><p>Voorvertoning</p> </td>
   <td><p>Hiermee kunt u een voorvertoning van het fragment weergeven als HTML of een aangepaste voorvertoning uitvoeren door gegevens uit een XML-bestand samen te voegen met het fragment. <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Downloaden</p> </td>
   <td><p>Hiermee downloadt u het geselecteerde fragment. <br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Revisie starten/Revisie beheren</p> </td>
   <td><p>Hiermee kunt u een revisie van het geselecteerde fragment starten en beheren. <br /> <br /> </p> </td>
    </tr>
    <!--<tr>
   <td><p>Add Dictionary</p> </td>
   <td><p>Generates a dictionary for localizing the selected fragment. For more information, see <a>Localizing Adaptive Forms</a>.<br /> <br /> </p> </td>
    </tr>-->
    <tr>
   <td><p>Publiceren/Publiceren ongedaan maken</p> </td>
   <td><p>Hiermee publiceert u het geselecteerde fragment of maakt u de publicatie ervan ongedaan. <br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Verwijderen</p> </td>
   <td><p>Hiermee verwijdert u het geselecteerde fragment. <br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Ververgelijken</p> </td>
   <td><p>Vergelijkt twee verschillende formulierfragmenten voor voorvertoningen. <br /> <br /> </p> </td>
    </tr>
    </tbody>
    </table>

## Aanbevolen procedures

- Zorg ervoor dat de fragmentnaam uniek is. Het fragment kan niet worden gemaakt als er een bestaand fragment met dezelfde naam bestaat.
- Expressies, scripts of stijlen in een zelfstandig formulierfragment blijven behouden wanneer deze via verwijzing worden ingevoegd of in een formulier worden ingesloten.
- Wanneer u een formulier publiceert, worden de formulierfragmenten die door verwijzing in het formulier zijn ingevoegd, automatisch gepubliceerd.


