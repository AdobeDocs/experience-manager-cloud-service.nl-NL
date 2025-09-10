---
title: Formulierfragmenten maken voor op WYSIWYG gebaseerde authoring
description: Leer hoe u formulierfragmenten maakt in de Universal Editor en deze toevoegt aan formulieren.
feature: Edge Delivery Services
role: Admin, User, Developer
exl-id: 7b0d4c7f-f82f-407b-8e25-b725108f8455
source-git-commit: fd3c53cf5a6d1c097a5ea114a831ff626ae7ad7e
workflow-type: tm+mt
source-wordcount: '1672'
ht-degree: 0%

---

# Formulierfragmenten maken in Universal Editor

Formulierfragmenten zijn herbruikbare componenten die herhalende ontwikkelingswerkzaamheden elimineren en zorgen voor consistentie in alle formulieren van uw organisatie. In plaats van gemeenschappelijke secties zoals contactinformatie, adresdetails, of toestemmingsovereenkomsten voor elk formulier opnieuw te maken, kunt u deze elementen één keer als fragmenten bouwen en ze in meerdere formulieren opnieuw gebruiken.

**wat u in dit artikel zult verwezenlijken:**

- Begrijp de bedrijfswaarde en de technische mogelijkheden van vormfragmenten
- Herbruikbare formulierfragmenten maken met de universele editor
- Fragmenten in bestaande formulieren integreren met de juiste configuratie
- De levenscyclus van fragmenten beheren en consistentie in verschillende formulieren behouden

**Bedrijfs voordelen:**

- **Verminderde ontwikkelingstijd**: Bouw gemeenschappelijke vormsecties eens, hergebruik overal
- **Verbeterde consistentie**: Gestandaardiseerde lay-outs en inhoud over alle vormen
- **Vereenvoudigd onderhoud**: Werk een fragment eens bij om veranderingen over alle vormen te wijzen die het gebruiken
- **Verbeterde naleving**: Verzeker regelgevende secties verenigbaar en bijgewerkt blijven

Formulierfragmenten in Edge Delivery Services bieden ondersteuning voor geavanceerde functies, zoals geneste fragmenten, meerdere exemplaren in één formulier en naadloze integratie met gegevensbronnen.

## Werken met formulierfragmenten

Formulierfragmenten in Edge Delivery Services bieden krachtige mogelijkheden voor de ontwikkeling van modulaire formulieren:

**mogelijkheden van de Kern:**

- **beheer van de Consistentie**: De fragmenten handhaven identieke lay-outs en inhoud over veelvoudige vormen. Met de methode &quot;Eenmaal wijzigen, Overal spiegelen&quot; worden updates van een fragment automatisch toegepast op alle formulieren in de voorbeeldmodus.
- **Veelvoudig gebruik**: Voeg het zelfde fragment veelvoudige tijden binnen één enkele vorm toe, elk met onafhankelijke gegevensband aan verschillende gegevensbronnen of schemaelementen.
- **Geneste structuren**: Creeer complexe hiërarchieën door fragmenten binnen andere fragmenten voor verfijnde vormarchitectuur in te bedden.

**Technische vereisten:**

- **consistentie van GitHub URL**: Zowel moeten het fragment als om het even welke vorm gebruiken het zelfde GitHub bewaarplaats URL specificeren
- **Standalone het uitgeven**: De fragmenten kunnen slechts in hun standalone vorm worden gewijzigd; de veranderingen kunnen niet binnen de gastheervorm worden aangebracht

**Publicatie gedrag:**

>[!IMPORTANT]
>
>In de modus Voorbeeld worden fragmentwijzigingen direct in alle formulieren doorgevoerd. In de modus Publiceren moet u zowel het fragment als alle formulieren die het gebruiken opnieuw publiceren om updates te kunnen zien.

>[!CAUTION]
>
>Vermijd recursieve fragmentverwijzingen (het nesten van een fragment binnen zich) aangezien dit teruggevende fouten en onverwacht gedrag veroorzaakt.

## Vereisten

**Technische opstellingsvereisten:**

- [ GitHub bewaarplaats die ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template) met verbinding wordt gevormd tussen uw milieu van AEM en bewaarplaats GitHub
- [ Latest Aangepast Forms blok ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) toegevoegd aan uw bewaarplaats GitHub (voor bestaande projecten van Edge Delivery Services)
- AEM Forms Author-instantie met Edge Delivery Services-sjabloon beschikbaar
- Toegang tot de URL van de AEM Forms as a Cloud Service-auteurinstantie en de GitHub-opslagplaats

**Vereiste kennis en toestemmingen:**

- Basiskennis van concepten van formulierontwerpen en componenthiërarchie
- Vertrouwdheid met de interface van de Universal Editor en workflows voor het maken van formulieren
- Machtigingen op auteurniveau in AEM Forms voor het maken en beheren van formulierelementen
- Inzicht in de formulierstandaarden van uw organisatie en herbruikbare componentvereisten

## Werken met Edge Delivery Services-formulierfragmenten

U kunt Edge Delivery Services-formulierfragmenten maken in de Universal Editor en de gemaakte fragmenten toevoegen aan Edge Delivery Services-formulieren. U kunt de volgende handelingen uitvoeren met Edge Delivery Services-formulierfragmenten:

- [Formulierfragmenten maken in Universal Editor](#creating-form-fragments-in-universal-editor)
   - [Werken met formulierfragmenten](#understanding-form-fragments)
   - [Vereisten](#prerequisites)
   - [Werken met Edge Delivery Services-formulierfragmenten](#working-with-edge-delivery-services-form-fragments)
   - [Aanbevolen procedures](#best-practices)
   - [Samenvatting](#summary)

+++ Formulierfragmenten maken

Voer de volgende stappen uit om een formulierfragment te maken in de Universal Editor:

1. Meld u aan bij de AEM Forms as a Cloud Service-auteur.
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
1. Klik **creëren** om het fragment te produceren. Er wordt een dialoogvenster weergegeven met bewerkingsopties.

   ![ geef fragment ](/help/edge/docs/forms/universal-editor/assets/edit-fragment.png) uit

1. Klik **uitgeven** om het fragment in Universele Redacteur met het toegepaste standaardmalplaatje te openen.

   ![ Fragment in Universele Redacteur voor creatie ](/help/edge/docs/forms/universal-editor/assets/fragment-in-ue.png)

1. **Ontwerp uw fragmentinhoud**: voeg vormcomponenten (tekstgebieden, dropdowns, checkboxes) toe om de herbruikbare sectie te bouwen. Voor gedetailleerde componentenbegeleiding, zie [ Begonnen het Worden met Edge Delivery Services voor AEM Forms gebruikend Universele Redacteur ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg).

1. **vorm componenteneigenschappen**: Plaats gebiedsnamen, bevestigingsregels, en standaardwaarden zoals nodig voor uw gebruiksgeval.

1. **sparen en voorproef**: Sparen uw fragment en gebruik de wijze van de Voorproef om de lay-out en de functionaliteit te verifiëren.

   ![ Schermafbeelding van een voltooid fragment van de de vorm van contactdetails in de Universele Redacteur, die gebieden voor naam, telefoon, e-mail, en adres tonen die over veelvoudige vormen kunnen worden opnieuw gebruikt ](/help/edge/docs/forms/universal-editor/assets/contact-fragment.png)

**controlepunt van de Bevestiging:**

- Fragmentlasten zonder fouten in de Universal Editor
- Alle formuliercomponenten worden correct weergegeven
- Veldeigenschappen en validatieregels werken zoals verwacht
- Fragment wordt opgeslagen en beschikbaar in de Forms &amp; Documents-console

Zodra uw fragment volledig is, kunt u het [ integreren in om het even welke vorm van Edge Delivery Services ](#adding-form-fragments-to-a-form).

+++


+++ Formulierfragmenten toevoegen aan een formulier

In dit voorbeeld ziet u hoe u een `Employee Details` -formulier maakt waarin het `Contact Details` -fragment wordt gebruikt voor de informatiesecties voor zowel werknemers als supervisors. Deze aanpak zorgt voor een consistente gegevensverzameling en vermindert tegelijkertijd de ontwikkelingsinspanningen.

Een formulierfragment integreren in uw formulier:

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

   >[!NOTE]
   >
   > De **geeft de knoop van het Fragment** uit staat gebruikers toe om rechtstreeks aan het vormfragment voor het uitgeven te navigeren.

   U kunt voorproef de vorm zien hoe de vorm op de **wijze van de Voorproef** verschijnt.

   ![ Voorproef ](/help/edge/docs/forms/universal-editor/assets/preview-form-with-fragment.png)

   Op dezelfde manier kunt u stap 3 tot en met 7 herhalen om het fragment `Contact Details` in te voegen voor het deelvenster `Supervisor Details` .

   ![ vorm van de Details van de Werknemer ](/help/edge/docs/forms/universal-editor/assets/employee-detail-form-with-fragments.png)

+++



+++ Formulierfragmenten beheren

U kunt verschillende bewerkingen uitvoeren op formulierfragmenten via de gebruikersinterface van AEM Forms.

1. Meld u aan bij de AEM Forms as a Cloud Service-auteur.
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

+++ 

## Aanbevolen procedures

**het ontwerp en het noemen van het fragment:**

- **Gebruik beschrijvende, unieke namen**: Kies namen die duidelijk het doel van het fragment aangeven (bijvoorbeeld, &quot;contact-details-met-bevestiging&quot;eerder dan &quot;fragment1&quot;)
- **Plan voor herbruikbaarheid**: De fragmenten van het ontwerp om context-onafhankelijk te zijn zodat werken zij over verschillende vormtypes
- **houd gefocuste fragmenten**: Creeer enig-doelfragmenten eerder dan complexe, multifunctionele componenten

**het werkschema van de Ontwikkeling:**

- **fragmenten van de Test onafhankelijk**: Verifieer fragmentfunctionaliteit alvorens in vormen te integreren
- **handhaaf verenigbare URLs GitHub**: Verzeker de zelfde bewaarplaats URL over alle verwante fragmenten en vormen wordt gebruikt
- **het fragmentdoel van het Document**: Omvat duidelijke beschrijvingen en markeringen om teamleden te helpen begrijpen wanneer om elk fragment te gebruiken

**Publicatie en onderhoud:**

- **gecoördineerde publicatie**: Wanneer het bijwerken van fragmenten, van plan om alle afhankelijke vormen gelijktijdig opnieuw te publiceren
- **de controle van de Versie**: Het gebruik verbindt betekenisvolle berichten wanneer het bijwerken van fragmenten aan spoorveranderingen in tijd
- **gebiedsdelen van de Monitor**: Houd spoor waarvan de vormen elk fragment gebruiken om updateeffect te beoordelen

>[!TIP]
>
>Fragmentstijlen, scripts en expressies blijven behouden wanneer ze worden ingesloten. Ontwerp daarom met deze overerving.

## Samenvatting

U hebt geleerd hoe u in Edge Delivery Services formulierfragmenten kunt gebruiken om de efficiëntie van de ontwikkeling te verbeteren en consistentie in de verschillende formulieren van uw organisatie te behouden.

**Zeer belangrijke verwezenlijkingen:**

- **Begrijpend**: Grasped de bedrijfswaarde en de technische mogelijkheden van vormfragmenten
- **Creatie**: Bouw herbruikbare vormfragmenten gebruikend Universele Redacteur met juiste configuratie
- **Integratie**: Toegevoegde fragmenten aan vormen met correcte verwijzingsopstelling en bezitsconfiguratie
- **Beheer**: Verkennende verrichtingen van de de levenscyclus van het fragment en onderhoudswerkschema&#39;s

**Volgende stappen:**

- Maak een bibliotheek met veelgebruikte fragmenten voor uw organisatie.
- Vaststellen van naamconventies en beheerbeleid voor fragmentgebruik.
- Onderzoek geavanceerde integratie met [ Modellen van de Gegevens van de Vorm ](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md) voor dynamische gegeven-gedreven fragmenten
- Op fragment gebaseerde formuliersjablonen implementeren voor consistente gebruikerservaring.

Uw formulieren profiteren nu van modulaire, onderhoudsbare architectuur die efficiënt over projecten kan worden geschaald en tegelijkertijd een consistente gebruikerservaring garandeert.


