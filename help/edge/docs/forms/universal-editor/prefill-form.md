---
title: Procedure voor het vooraf invullen van adaptieve formuliervelden
description: Bestaande gegevens gebruiken om velden van een adaptief formulier vooraf in te vullen. Gebruikers kunnen basisgegevens vooraf invullen in een formulier door zich aan te melden met hun sociale profielen.
feature: Adaptive Forms, Edge Delivery Services
role: User, Developer
level: Beginner, Intermediate
time: 45-60 minutes
keywords: vooraf instelbaar adaptief formulier, adaptieve services voor randweergave van formulieren, adaptief automatisch invullen van formulier
source-git-commit: 6c93af923e600dbb20add6c5f1053c832d5a5ca0
workflow-type: tm+mt
source-wordcount: '1829'
ht-degree: 0%

---


# Prefill-service configureren in Adaptive Forms met Edge Delivery Services

Het vooraf invullen van formulieren is het automatisch invullen van formuliervelden met relevante gegevens uit externe bronnen zodra een gebruiker het formulier opent. Door gebruik te maken van gegevens uit gebruikersprofielen, databases, opgeslagen concepten of andere back-endsystemen, stroomlijnt de prefilling de functionaliteit voor het invullen van formulieren: handmatige invoer wordt verminderd, fouten worden geminimaliseerd en voltooiing wordt versneld. Dit verhoogt niet alleen de tevredenheid van de gebruiker, maar verhoogt ook de kans op het succesvol verzenden van formulieren.

## Voordelen van het vooraf invullen van formulieren

| Voordeel | Beschrijving |
|---------|-------------|
| **snellere Voltooiing** | Vermindert het handmatig invoeren van gegevens, waardoor gebruikers formulieren snel kunnen invullen |
| **Verbeterde Ervaring van de Gebruiker** | Forms voelt zich gepersonaliseerd en handiger, vooral voor terugkerende gebruikers |
| **de Hogere Tarieven van de Omzetting** | Vermindert het verlaten van formulieren door vereiste gebruikersinspanning te minimaliseren |
| **Verminderde de Fouten van de Input** | Gegevens uit vertrouwde bronnen verlagen typos en onjuiste items |
| **betere Kwaliteit van Gegevens** | Zorgt voor gestructureerde, nauwkeurige en consistente gegevens voor back-endsystemen |

## Hoe Prefilling werkt

In het volgende diagram ziet u het automatische vooraf ingevulde proces dat plaatsvindt wanneer een gebruiker een adaptief formulier opent:

![ de Prefilling Stroom van het Proces van de Vorm ](/help/edge/docs/forms/universal-editor/assets/prefill-process-flow.svg)

Het vooraf ingevulde proces omvat vier belangrijke stappen:

1. **Gebruiker opent Vorm**: De gebruiker heeft toegang tot een AanpassingsVorm door URL of navigatie
2. **identificeer Gegevens Source**: De vooraf ingevulde dienst bepaalt de gevormde gegevensbron (het Model van Gegevens van de Vorm of de dienst van het Ontwerp)
3. **wint Gegevens** terug: Het systeem haalt relevante gebruikersgegevens die op context, parameters, of gebruikersidentificatie worden gebaseerd
4. **Kaart en Vertoning**: De gegevens worden in kaart gebracht aan vormgebieden gebruikend `bindRef` eigenschappen en de bevolkte vorm wordt getoond aan de gebruiker

Dit geautomatiseerde proces zorgt ervoor dat gebruikers een formulier zien dat vooraf is ingevuld met hun relevante informatie, wat de gebruikerservaring aanzienlijk verbetert en het voltooiingspercentage van het formulier aanzienlijk verbetert.

## Gegevensstructuur voor vooraf invullen

Adaptieve Forms ondersteunt twee typen velden:

- **Gebonden gebieden**: Gebieden die met een gegevensbron met een niet leeg `bindRef` bezit worden verbonden
- **Niet verbindende gebieden**: Standalone gebieden met lege `bindRef` waarden

De vooraf ingevulde gegevensstructuur omvat:

- **afBoundData**: Bevat gegevens voor verbindende gebieden en panelen
- **afUnBoundData**: Bevat gegevens voor ongebonden gebieden

De gegevensindeling moet overeenkomen met uw formuliermodel:

- **XFA vormen**: Volgzaam XML met het malplaatjeschema XFA
- **het schemavormen van XML**: XML die de schemastructuur aanpassen
- **JSON schemavormen**: JSON volgzaam met het schema
- **het Model van Gegevens van de Vorm (FDM) vormen**: JSON die de structuur FDM aanpassen
- **schema-less vormen**: Alle gebieden zijn niet verbindend en gebruiken ongebonden XML


## Vereisten

Voordat u de vooraf ingevulde services configureert, moet u ervoor zorgen dat:

### Vereiste instelling

- [GitHub-opslagplaats geconfigureerd voor Edge Delivery Services](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block)
- [Aangepast Forms-blok toegevoegd aan uw project](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project)
- [Gegevensbron geconfigureerd](/help/forms/configure-data-sources.md)
- [FDM (Form Data Model) gemaakt](/help/forms/create-form-data-models.md)

### Toegangsvereisten

- Toegang tot AEM Forms as a Cloud Service
- Machtigingen om formulieren te maken en te bewerken
- Universal Editor-toegang met de vereiste extensies ingeschakeld

>[!TIP]
>
> U kunt formulieren ook bewerken om het formuliergegevensmodel (FDM) te integreren in de Universal Editor om gegevens van verschillende bronnen op te halen. Voor details, verwijs naar [ vormen met het Model van de Gegevens van de Vorm in Universeel artikel van de Redacteur ](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md) integreren.

## Opties voor vooraf ingevulde service

De Universal Editor biedt twee vooraf ingevulde serviceopties:

| Servicetype | Doel | Data Source | Best voor |
|--------------|---------|-------------|----------|
| **Prefill van het Ontwerp van het Portaal van de Vorm** | Hiermee hervat u gedeeltelijk ingevulde formulieren | Opgeslagen concepten in Forms Portal | Doorgaan met onvolledige toepassingen |
| **het Model van Gegevens van de Vorm vooraf invullen** | Vult velden van externe systemen | Databases back-end via FDM | Gebruikersprofielgegevens automatisch invullen |

### Gedetailleerde vergelijking

| Functie | Conceptvoorgevulde service | FDM Prefill-service |
|---------|----------------------|---------------------|
| **Authentificatie** | Gebruikersaanmelding vereist voor concepttoegang | Configureerbaar op basis van gegevensbron |
| **Complexiteit van de Opstelling** | Minimale configuratie | Vereist FDM instellen en toewijzen |
| **Type van Gegevens** | Statische opgeslagen gegevens | Dynamische gegevens in realtime |
| **Geval van het Gebruik** | Opgeslagen toepassingen hervatten | Vooraf invullen vanuit gebruikersprofielen of databases |


## Prefill-service voor een formulier configureren


+++fase 1: Formuliergegevensmodel instellen

### Stap 1: Formuliergegevensmodel maken

1. Aanmelden bij uw AEM Forms as a Cloud Service-exemplaar
2. Ga aan **Adobe Experience Manager** > **Forms** > **Integraties van Gegevens**
3. Selecteer **creëren** > **Model van de Gegevens van de Vorm**
4. Kies uw **Configuratie van Source van Gegevens** en selecteer gevormde **Source van Gegevens**

   ![ Gemaakt Model van de Gegevens van de Vorm ](/help/edge/docs/forms/universal-editor/assets/create-fdm.png)

   >[!TIP]
   >
   > Voor gedetailleerde instructies bij het creëren van de Modellen van Gegevens van de Vorm, zie [ het Model van de Gegevens van de Vorm ](/help/forms/create-form-data-models.md) creëren.

### Stap 2: FDM-services configureren

1. Ga naar **Adobe Experience Manager** > **Forms** > **Integraties van Gegevens**
2. Het formuliergegevensmodel openen in de bewerkingsmodus
3. Selecteer een gegevensmodelvoorwerp en klik **uitgeven Eigenschappen**
4. Vorm **Gelezen** en **schrijven** diensten voor de geselecteerde voorwerpen van het gegevensmodel

   ![ vormen lees schrijven de dienst ](/help/edge/docs/forms/universal-editor/assets/configure-reda-write-service.png)

5. Serviceargumenten configureren:
   - Klik op het bewerkingspictogram voor het argument van de leesservice
   - Bind het argument aan a **Attribuut van het Profiel van de Gebruiker**, **Attribuut van het Verzoek**, of **Letterlijke waarde**
   - Geef de bindingswaarde op (bijvoorbeeld `petid` voor een registratieformulier voor gezelschapsdieren)

   ![ vorm het argument van huisidentiteitskaart ](/help/edge/docs/forms/universal-editor/assets/pet-id-arguments.png)

6. Klik **Gedaan** om het argument en **sparen** te bewaren om FDM te bewaren

   >[!NOTE]
   >
   > Leer meer over het vormen van de diensten FDM in [ Werk met het Model van de Gegevens van de Vorm (FDM) ](/help/forms/work-with-form-data-model.md).

+++

+++Fase 2: Het Aangepaste formulier maken en configureren

### Stap 3: Een adaptief formulier maken

1. Navigeer aan **Adobe Experience Manager** > **Forms** > **Forms &amp; Documenten**
1. Selecteer **creeer** > **Aangepaste Forms**
1. In het **Source** lusje, selecteer een malplaatje van Edge Delivery Services:

   ![ malplaatje van Edge Delivery Services ](/help/edge/assets/create-eds-forms.png)

1. Klik **creëren** om **te openen creeer de 3 tovenaar van de Vorm {**
1. Geef de formulierdetails op:

   - **Naam**: Ga een beschrijvende naam voor uw vorm in
   - **Titel**: Verstrek een gebruikersvriendelijke titel
   - **GitHub URL**: Ga uw bewaarplaats URL (b.v., `https://github.com/wkndforms/edsforms`) in

1. Klik **creëren**

   ![ creeer schema-gebaseerde vorm ](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form1.png)

Het formulier wordt geopend in de Universal Editor voor ontwerpen.

### Stap 4: Formuliergegevens configureren, Source

1. Selecteer uw vorm en klik **Eigenschappen**

   ![ Uitgezochte Eigenschappen van de Vorm ](/help/edge/docs/forms/universal-editor/assets/select-form-properties1.png)

2. Open het **Model van de Vorm** lusje
3. Van **Uitgezocht van** dropdown, kies **Model van de Gegevens van de Vorm (FDM)**
4. Selecteer het gemaakte formuliergegevensmodel (bijvoorbeeld PetFDM) in de vervolgkeuzelijst

   ![ Uitgezochte het modellusje van het Vorm ](/help/edge/docs/forms/universal-editor/assets/select-form-model1.png)

5. Klik **sparen &amp; Sluiten**
6. Het formulier openen voor bewerking in de Universal Editor

De vormelementen van uw FDM verschijnen in het **Datasource** lusje van **Browser van de Inhoud**.

### Stap 5: Gegevensbinding toevoegen aan formuliervelden

1. Selecteer gegevenselementen van het **lusje van 0} Gegevensbron {**
2. Klik **toevoegen** of belemmering-en-dalingselementen om uw vorm te bouwen

   ![ Schermafbeelding van Universele Redacteur die op schema-gebaseerde vorm ](/help/edge/docs/forms/universal-editor/assets/ue-form.png) tonen

3. Gegevensbinding toevoegen aan formuliervelden:

   - Een formulierveld selecteren
   - In het **paneel van Eigenschappen**, vind het **Bind bezit van de Verwijzing**
   - Selecteer de juiste gegevensbindingsverwijzing

     ![ Gegevens die ](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding1.png) binden

+++

+++Fase 3: Het vormen Prefill Dienst

### Stap 6: Vereiste extensies inschakelen

Zorg ervoor dat deze extensies zijn ingeschakeld in de Universal Editor:

1. **de Uitbreiding van de Eigenschappen van de Vorm van AEM**

   - Open **Extension Manager** in Universele Redacteur
   - Laat de **uitbreiding van de Eigenschappen van de Vorm van 0} AEM toe**

   ![ de eigenschappen van de Vorm pictogram ](/help/edge/docs/forms/universal-editor/assets/form-edit-properties.png)

1. **de Uitbreiding van Source van Gegevens**

   - Laat de **bron van Gegevens** uitbreiding toe als u niet het **pictogram van Gegevensbronnen** ziet

   ![ Schermafbeelding van Universal Editor Extension Manager ](/help/edge/docs/forms/universal-editor/assets/extension-manager.png)

   >[!TIP]
   >
   > Voor gedetailleerde instructies bij het beheren van uitbreidingen, zie {de Hoogtepunten van de Eigenschap van 0} Extension Manager [.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)

### Stap 7: Prefill-service configureren

1. Het adaptieve formulier openen in de Universal Editor
2. Klik het **de uitbreidingspictogram van de Eigenschappen van de Vorm van AEM**

   ![ Uitgezochte Pictogram van de Eigenschappen van de Vorm ](/help/edge/docs/forms/universal-editor/assets/select-fdm-properties-icon.png)

3. Klik **vooraf ingevulde** tabel
4. Selecteer **Model van de Gegevens van de Vorm vooraf ingevulde Dienst**

   ![ Uitgezochte Vooraf ingevulde dienst ](/help/edge/docs/forms/universal-editor/assets/select-fdm-prefill.png)

5. Klik **sparen &amp; Sluiten**

+++

+++Fase 4: Uw vooraf ingevulde configuratie testen

### Stap 8: Voorvertonen en testen

1. Ga naar **Forms** > **Forms en Documenten**
2. Selecteer uw adaptieve formulier
3. Kies **Voorproef als HTML**
4. Test prefilling door parameters aan URL toe te voegen:

   https://your-preview-url.com?<bindreferencefield>=<value>

   **Voorbeeld:**

   https://your-preview-url.com?petid=12345

   ![ vooraf ingevulde Vorm ](/help/edge/docs/forms/universal-editor/assets/prefill-form.png)

Het formulier moet automatisch gegevens vullen op basis van de opgegeven parameter.

+++

## Voorbeelden

### Voorbeeld van vooraf ingevulde gegevensstructuren

**JSON Voorbeeld voor FDM-Gebaseerde Vorm:**

    &quot;
    
    {
     &quot;afBoundData&quot;: 
     &quot;user&quot;: 
     &quot;firstName&quot;: &quot;John&quot;, 
     &quot;lastName&quot;: &quot;Doe&quot;, 
     &quot;email&quot;: &quot;john.doe@example.com&quot;, 
     &quot;phone&quot;: &quot;+1-555-0123&quot;
     
    , 
     &quot;afUnBoundData&quot;: 
     &quot;additionalInfo&quot;: &quot;Voorkeuren van de Gebruiker geladen&quot;
     
     
    
    &quot;

**Voorbeeld van XML voor op XFA-Gebaseerde Vorm:**

    &quot;
    
    &lt;?xml version=&quot;1.0&quot; encoding=&quot;UTF-8&quot;?>
     &lt;afData> 
     &lt;afBoundData> 
     &lt;user> 
     &lt;firstName>John&lt;/firstName> 
     &lt;lastName>Doe&lt;/lastName> 
     &lt;email>john.doe@example.com&lt;/email>
     user>
    &lt;/afBoundData> 
    &lt;/afData> 
    
    &quot;

### Vooraf ingevulde URL&#39;s

De URL&#39;s hieronder dienen alleen ter illustratie en werken niet zoals ze zijn. Vervang de host en parameters door de parameters die relevant zijn voor uw eigen omgeving tijdens het testen van de vooraf ingevulde functionaliteit.

**Basis vooraf ingevulde test:**

`https://preview.example.com/form.html?userId=12345`

**Veelvoudige parametertest:**

`https://preview.example.com/form.html?userId=12345&category=premium`


## Problemen oplossen

+++Algemene problemen en oplossingen

| Probleem | Mogelijke oorzaak | Oplossing |
|-------|----------------|----------|
| **de gebieden van de Vorm niet prefilling** | Onjuiste waarden `bindRef` | Controleren of `bindRef` precies overeenkomt met FDM-veldnamen |
| **de formaatfouten van Gegevens** | Gegevensstructuur komt niet overeen | Preflight-gegevens afstemmen op formuliermodelschema |
| **niet gevonden de Dienst** | FDM-configuratieproblemen | Controleer of FDM-services correct zijn geconfigureerd en opgeslagen |
| **de fouten van de Authentificatie** | Gegevensbronconnectiviteit | Verifieer gegevensbrongeloofsbrieven en connectiviteit |
| **Gedeeltelijke gegevens die** laden | Ontbrekende veldtoewijzingen | Ervoor zorgen dat alle vereiste velden de juiste gegevensbindingen hebben |

+++

+++Foutopsporingsstappen

1. **verifieer configuratie FDM:**

   - Controleren of services correct zijn geconfigureerd
   - FDM-services onafhankelijk testen
   - Gegevensbronconnectiviteit valideren

2. **de Configuratie van de Vorm van de Controle:**

   - Bevestigen dat formulier is gekoppeld aan juiste FDM
   - `bindRef` waarden van veld verifiëren
   - Formulier testen zonder voorvoegsel eerst

3. **Stroom van Gegevens van de Test:**

   - Gebruik de browsergereedschappen voor ontwikkelaars om netwerkaanvragen te inspecteren
   - Console controleren op JavaScript-fouten
   - Gegevensindeling van reactie valideren

4. **Gemeenschappelijke Berichten van de Fout:**

   - &quot;Prefill service not found&quot;: serviceconfiguratie controleren
   - &quot;Gegevensbinding mislukt&quot;: controleer `bindRef` nauwkeurigheid
   - &quot;Ongeldige gegevensindeling&quot;: zorg ervoor dat de gegevens overeenkomen met het schema

+++

## Aanbevolen procedures

+++Best practices voor configuratie

- **beschrijvende noemende van het Gebruik**: Noem uw FDMs en de diensten duidelijk
- **bevestigt gegevensschema&#39;s**: Verzeker gegevensstructuur vormvereisten aanpast
- **Test incrementeel**: Vorm en test één gebied tegelijkertijd
- **Toewijzingen van het Document**: Houd spoor van gebied-aan-gegevens afbeeldingen

+++

+++Optimalisatie van prestaties

- **minimaliseer gegevensvolume**: Slechts vooraf ingevulde noodzakelijke gebieden
- **Gebruik caching**: Vorm aangewezen caching voor vaak betreden gegevens
- **optimaliseer vragen**: Verzeker gegevensbestandvragen efficiënt zijn
- **prestaties van de Monitor**: De tijden van de vormlading van het spoor met toegelaten prefill

+++

+++Overwegingen voor beveiliging

- **bevestigt inputparameters**: Bevestig altijd parameters URL
- **Sanitize gegevens**: Reinig gegevens alvorens vormen vooraf in te vullen
- **voert toegangscontroles** uit: Verzeker gebruikers tot hun eigen gegevens slechts kunnen toegang hebben
- **HTTPS van het Gebruik**: Gebruik altijd veilige verbindingen voor gegevenstransmissie

+++

+++Richtlijnen voor gebruikerservaring

- **verstrekken terugkoppelt**: Toon ladingsindicatoren tijdens gegevenshaal
- **elegant de fouten van het 0} Handvat {: De nuttige foutenmeldingen van de vertoning**
- **staat met voeten treedt** toe: Laat gebruikers vooraf ingevulde gegevens wijzigen
- **handhaaf consistentie**: Gebruik verenigbaar prefill gedrag over vormen

+++

## Veelgestelde vragen

+++Hoe kan ik testen of de prefilling correct werkt?

Geef een voorbeeld van het formulier weer en voeg vooraf ingevulde parameters toe aan de URL met de volgende notatie: `?<bindreferencefield>=<value>` . Zorg ervoor dat het veld een geldige `bindRef` heeft die overeenkomt met de gegevensstructuur. Gebruik de browserontwikkelaarsgereedschappen om netwerkaanvragen te inspecteren en te controleren of gegevens correct worden opgehaald.

+++

+++Welke gegevensindelingen worden ondersteund voor het vooraf invullen van een adaptieve Forms?

Adaptieve Forms ondersteunt meerdere indelingen, afhankelijk van uw formuliermodel:

- **XFA vormen**: XML die het schema XFA aanpassen
- **JSON schemavormen**: Gegevens JSON volgzaam met het schema
- **FDM vormen**: JSON die aan de structuur van het gegevensmodel in kaart brengt
- **het schemavormen van XML**: XML die de schemastructuur aanpassen

+++

+++Kan ik zowel gebonden als niet-gebonden velden vooraf invullen?

Ja, u kunt beide typen velden vooraf invullen. Gebonden velden gebruiken de sectie `afBoundData` en moeten overeenkomen met het formuliermodelschema. Niet-gebonden velden gebruiken de sectie `afUnBoundData` en kunnen aanvullende gegevens bevatten.

+++

+++Wat zou ik moeten doen als slechts sommige gebieden prefilling zijn?

Controleer of alle velden juiste `bindRef` waarden hebben die exact overeenkomen met uw FDM. Controleer of de gegevensbron alle vereiste velden bevat en of de gegevensstructuur overeenkomt met het formuliermodelschema.

+++

+++Hoe kan ik verificatie voor vooraf ingevulde services afhandelen?

Verificatie is afhankelijk van de configuratie van de gegevensbron. Voor op FDM-Gebaseerde prefilling, vorm authentificatie in uw gegevensbronmontages. Voor concept prefilling moeten gebruikers doorgaans zijn aangemeld om toegang te krijgen tot hun opgeslagen concepten.

+++

+++Kan ik meerdere vooraf ingevulde services in één formulier gebruiken?

U kunt per formulier één primaire vooraf ingevulde service configureren. U kunt echter verschillende gegevensbronnen in één formuliergegevensmodel combineren voor een vergelijkbare functionaliteit.

+++

## Verwante onderwerpen

- [Formulieren integreren met formuliergegevensmodel in de universele editor](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md)
- [Formuliergegevensmodellen maken](/help/forms/create-form-data-models.md)
- [Werken met FDM (Form Data Model)](/help/forms/work-with-form-data-model.md)
- [Gegevensbronnen configureren](/help/forms/configure-data-sources.md)
- [Aan de slag met Edge Delivery Services voor AEM Forms](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
