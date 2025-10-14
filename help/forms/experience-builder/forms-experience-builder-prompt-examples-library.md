---
title: Forms Experience Builder - Snelle bibliotheek
description: Verzameling van bewezen snelle patronen en voorbeelden voor het bouwen van formulieren met AI-hulp in de gebruikersinterface van Forms Management, de Adaptive Forms Editor en de Universal Editor.
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: c8f64082-a23f-4919-ad66-042faad77d31
source-git-commit: de524aeddd5f53cbd713ff0523222966752ebbc0
workflow-type: tm+mt
source-wordcount: '2193'
ht-degree: 0%

---


# Forms Experience Builder - Snelle bibliotheek

Verzameling herbruikbare snelle patronen en voorbeelden die zijn geoptimaliseerd voor Forms Experience Builder. Deze gestroomlijnde bibliotheek richt zich op de twee belangrijkste aanmaakmethoden: Maken van werkschijf en importeren en converteren, met verbeterde ondersteuning voor slimme velden met LLM-voeding en consistentie van merken.

>[!NOTE]
>
> De Forms Experience Builder is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

## Deze Promptbibliotheek gebruiken

Deze bibliotheek verstrekt herbruikbare snelle patronen voor gemeenschappelijke vorm-bouwende scenario&#39;s. Voor uitvoerige beste praktijken, zie de [&#x200B; Begonnen Gids van de Bouwer van de Ervaring van Forms &#x200B;](/help/forms/experience-builder/forms-experience-builder-getting-started.md).

### Snelle tips voor deze bibliotheek

- **Begin met voorbeelden** - Gebruik verstrekte herinneringen als malplaatjes en pas aan uw behoeften aan
- **Twee creatiemethodes** - kies creeer van Scratch of de Invoer &amp; zet benaderingen om
- **ben specifiek** - voeg uw eigen details aan generische voorbeelden toe
- **Test grondig** - bevestigt altijd resultaten in uw specifiek milieu

### Merksjablonen en -stijlen

**bereidt merkactiva vooraf voor verenigbare vormverwezenlijking voor:**

- **Malplaatjes van het Merk** - bereidt gestandaardiseerde vormmalplaatjes met de kleuren, de doopvonten, en lay-outpatronen van uw organisatie voor
- **de Richtlijnen van de Stijl** - bepalen verenigbaar gebied het stileren, knoopontwerpen, en het uit elkaar plaatsen normen die de Bouwer van de Ervaring van Forms kan toepassen
- **Bibliotheek van de Component** - het werk met uw ontwikkelingsteam om herbruikbare vormcomponenten voor te bereiden die uw merkidentiteit aanpassen
- **Visuele Assets** - bereidt logo&#39;s, pictogrammen, en achtergrondelementen voor vormintegratie voor


## Voorbeelden van incrementele ontwikkeling

In deze voorbeelden ziet u hoe u stapsgewijs formulieren maakt, eenvoudig begint en geleidelijk complexiteit toevoegt:

### Voorbeeld 1: Een contactformulier stapsgewijs samenstellen

**Stap 1 - Begin Eenvoudig:**

     creeer een basiscontactvorm met naam, e-mail, en berichtgebieden 

**Stap 2 - voeg Bevestiging toe:**

     maak @name en @email verplichte gebieden met aangewezen bevestiging 

**Stap 3 - verbeter de Ervaring van de Gebruiker:**

     voegt placeholder tekst toe: @name &quot;Uw volledige naam&quot;, @email &quot;your.email@company.com&quot;, @message &quot;vertelt ons hoe wij kunnen helpen&quot;

**Stap 4 - voeg Geavanceerde Eigenschappen toe:**

     voegt een dropdown vraagType met opties toe: &quot;Algemene Vraag&quot;, &quot;Verzoek van de Steun&quot;, &quot;Onderzoek van de Verkoop&quot;, &quot;Partnerschap&quot;

**Stap 5 - voer Voorwaardelijke Logica uit:**

    /create-rule toon @priorityLevel dropdown (Laag, Medium, Hoog) slechts wanneer @vraagType &quot;Verzoek van de Steun&quot;evenaart 

### Voorbeeld 2: Een registratieformulier stapsgewijs samenstellen

**Stap 1 - Basisstructuur:**

     creeer een vorm van de gebruikersregistratie met persoonlijk informatiepaneel 

**Stap 2 - voeg Vereiste Gebieden toe:**

     voegt gebieden voor @firstName, @lastName, @email, @phoneNumber met aangewezen bevestiging 
 toe
**Stap 3 - voeg BedrijfsLogica toe:**

     creeer een regel: als @age onder 18 is, toon ouder/de sectie van de de informatieinformatie van de hoedster 

**Stap 4 - verbeter met Voorkeur:**

     voeg een voorkeurenpaneel met @newsletterSubscription, @marketingConsent, @termsAccepted 
 toe
**Stap 5 - voeg Dossier toe uploadt:**

     omvat een dossier uploadt gebied voor @profilePicture met groottelimiet van 5MB 

## Formulier maken en beheren

**wanneer te gebruiken:** wanneer u nieuwe vormen moet creëren of bestaande degenen wijzigen.

**hoe te gebruiken:** kies één van twee benaderingen: creeer van Scratch of de Invoer &amp; zet (zie [&#x200B; Begonnen Gids &#x200B;](/help/forms/experience-builder/forms-experience-builder-getting-started.md).

**Vragen van het Voorbeeld - Eenvoudige Making van de Vorm:**

     creeer een klant terugkoppelt vorm met:
     - de Rating van het Product (1-5 sterren) 
     - het gebied van de Commentaar voor gedetailleerde terugkoppelt 
     - de e-mail van de Klant (facultatief) 
     - voorlegt aan e-mailbericht 

**Vraag van het Voorbeeld - de Complexe Making van de Vorm:**

     creeer een uitvoerige werknemer op het instappen vorm met:
    
    **Persoonlijke Sectie van de Informatie:** 
     - Volledige naam (eerst, midden, laatste) 
     - Datum van geboorte met leeftijdsbevestiging 
     - de informatie van het contact (e-mail, telefoon, adres) 
     - Noodcontactdetails 
    
    **Werkgelegenheidsdetails:** 
     - Positie en afdelingsselectie 
     - de datum van het begin met de bevestiging van de dag 
     salaris Aanvullende informatie met vertrouwelijkheidskennisgeving 
     - Rapportagestructuur 
    
    **Document uploaden:**
     - Hervatten/CV uploaden (PDF, DOC, DOCX) 
     - ID-verificatiedocumenten 
     - Belastingformulieren en bankgegevens 
     - Ondertekende arbeidsovereenkomst 
    
    **Voorkeuren:*
     - Berekende voordelen De maker 
     - de voorkeur van het werkschema 
     - de vereisten van de Opleiding 
     - de behoeften van het Materiaal 
    
     **de Regels van de Bevestiging:* 
     - De de formaatbevestiging van het E-mail 
     - de formaatbevestiging van het aantal van de telefoon 
     - de Leeftijd moet 18 zijn of ouder 
     - Alle vereiste documenten moeten worden geupload 
     - de Algemene voorwaarden worden goedgekeurd 27&rbrace;**Submit Acties:** 
    
     - verzend bevestigingsmail naar nieuwe werknemer 
     - de afdeling van u op de hoogte brengen 
     - creeer werknemersverslag in het systeem van u 
     - de vergadering van de de oriëntatie van het Programma 
    

**Prompts van het Beheer van de Vorm:**

     de Invoer dit de toepassingsvorm van PDF en zet het in een adaptieve vorm met verbeterde bevestiging 
    
     bij Werk de bestaande contactvorm om sociale media handvatten en aangewezen contactmethode te omvatten 
    
     reorganize de registratieformulier in een 3-stap tovenaar: persoonlijke info, voorkeur, bevestiging 

## Veld beheren en configureren

**wanneer te gebruiken:** wanneer u, vormgebieden moet toevoegen wijzigen of vormen.

**hoe te gebruiken:** ben specifiek over gebiedstypes, bevestigingsregels, en gebruikerservaringsvereisten.

**Vraag van het Voorbeeld - de Basis Toevoeging van het Gebied:**

     voeg een gebied van de tekstinput voor &quot;Naam van het Bedrijf&quot;met placeholder toe &quot;ga uw bedrijfnaam in&quot;

**Vraag van het Voorbeeld - Geavanceerde Configuratie van het Gebied:**

     voeg een uitvoerige adressectie met toe:
    
    **Adres:** 
     - de lijn van het Adres 1 (vereist, maximum 100 karakters) 
     - de lijn van het Adres 2 (facultatief, maximum 100 karakters) 
     - Stad (vereist, dropdown met gemeenschappelijke steden) 
     - Staat/Provincie (vereist, drop-down) 
     - Postal code (vereiste, formaatbevestiging) 
     
    
     - Land (vereist, gebrek aan &quot;Verenigde Staten&quot;) 
     **de Regels van de Bevestiging:** 
     - de Postcode moet staatsselectie aanpassen 
     - de Lijn van het Adres 1 kan niet leeg zijn 
    
     - Stad moet een geldige stad voor geselecteerde staat zijn 
    **Ervaring van de Gebruiker:** 
     - auto-volledig voor adresgebieden 
     - Duidelijke etiketten en hulptekst {11 5} - Mobiele-vriendelijke invoervelden 
     - Compatibiliteit met toegankelijkheid 

**Vragen van de Configuratie van het Gebied:**

     maak @email gebied met bevestiging in real time en douanefoutenmelding 
    
     wordt vereist een drop-down voor @country met opties voor V.S., Canada, VK, Duitsland, Frankrijk, en &quot;Andere&quot;
    
     vorm @phoneNumber gebied met formaat (XXX) XXX-XXXX en bevestiging 
    
     voeg een dossier toe uploadt gebied voor @resume met PDF en DOC beperkingen, maximum 5MB 

## Verbeterde slimme velden in LLM

**wanneer te gebruiken:** wanneer u gebieden met pre-bevolkte opties nodig hebt die hefboomwerking de kennisbasis van AI.

**hoe te gebruiken:** gebieden van het Verzoek die uitvoerige gegevensreeksen vereisen - AI kan opties automatisch bevolken gebruikend zijn ingebouwde kennis.

### Geografische en locatievelden

**Luchthavens en Vervoer:**

     voeg een drop-down voor vertrekluchthavens met alle belangrijke internationale luchthavens 
     toe toevoegt het gebied van de aankomstLuchthaven met IATA codes en volledige namen 
     creeer een gebied voor dichtstbijzijnde luchthaven aan gebruikersplaats 
     voeg een selectie van treinstations voor Europese steden 
 toe
**Administratieve Gebieden:**

     voeg een volledige lijst van de staten van de V.S. met afkortingen 
     tot een landdrop-down met de codes van ISO en volledige namen 
     toe voeg een gebied voor grote wereldsteden met tijdzones 
     omvat een daling van Canadese provincies en gebieden 
     een gebied voor de districten van het VK en postgebieden 
 toe

### Gegevens voor bedrijven en de industrie

**Classificaties van het Bedrijf:**

     voeg een gebied voor de industrieclassificatie met de codes van NAICS 
     toe leidt tot een daling van bedrijfentiteit types (LLC, Bedrijf, Partnerschap, enz.)
     voeg een gebied voor de categorieën van de bedrijfgrootte (opstarten, KMO, onderneming) toe 
     omvat afdelingsselectie voor grote organisaties 
     een gebied voor de professionele diensttypes 
 toevoegen
**Professionele classificaties:**

     voeg een gebied voor baantitels met gemeenschappelijke industriefollen 
     toe leidt tot een daling van professionele certificatie door gebied 
     omvat onderwijsniveaus met gradentypen 
     voeg een gebied voor jaren van ervaringswaaiers 
     tot een selectie voor programmeertalen en kaders 

### Normen en regelgeving

**Financiële en Juridische:**

     voeg een gebied voor muntcodes met symbolen en wisselkoersen 
     toe leidt tot een daling van de types van fiscale identiteitskaart door land 
     omvat een gebied voor wettelijke documenttypes 
     toevoegt de opties van de betalingsmethode met veiligheidseigenschappen 
     tot een selectie voor bancaire instellingen door land 

**Technische Normen:**

     voeg een daling van dossierformaattypes met uitbreidingen 
     toe omvat netwerkprotocolopties 
     een gebied voor gegevensbestandtypes en versies 
     creeer een selectie voor API authentificatiemethodes 

### Gezondheidszorg en medische zorg

**Medische Classificaties:**

     voeg een gebied voor medische specialiteiten 
     toe leidt tot een daling van gemeenschappelijke geneesmiddelen met generische namen 
     omvat een gebied voor de types van verzekeringsleverancier 
     toevoegen een selectie voor de medische verhoudingen van het noodcontact 
     tot een gebied voor dieetbeperkingen en allergieën 

### Intelligentie tijd en kalender

**Datum en de Gebieden van de Tijd:**

     voeg een gebied voor kantooruren met tijdzone behandeling 
     toe creeert een daling van openbare vakanties door land 
     seizoensgebonden opties met datumwaaiers 
     voegt een gebied voor conferentiezaal het boeken met beschikbaarheid 
     tot een selectie voor terugkomende vergaderingspatronen 
 toe

### Product- en servicecategorieën

**E-commerce Classificaties:**

     voeg een gebied voor productcategorieën met subcategorieën 
     toe leidt tot een daling van het verschepen methodes met leveringsramingen 
     omvat een gebied voor de opties van het terugkeerbeleid 
     een selectie voor klant prioritaire niveaus 
     tot een gebied voor het factureren van abonnementen cycli 

**Prompts van het Voorbeeld Slimme Gebied:**

     &quot;voeg een gebied van de vertrekluchthaven met alle belangrijke luchthavens wereldwijd met inbegrip van IATA- codes en stadsnamen&quot;toe 
    
     &quot;creeer een uitvoerig industrieterrein gebruikend standaardNAICS classificatie met technologiesubcategorieën&quot;
    
     &quot;omvat een professionele certificatiestrijdvervolgkeuzelijst die op het geselecteerde baangebied&quot;wordt gebaseerd 
    
     &quot;voeg een internationaal telefoonnummergebied toe dat formaten die op het geselecteerde land worden gebaseerd&quot;
    
     &quot;creeer een universitair selectieveld 

## Regels maken en bedrijfslogica

**wanneer te gebruiken:** wanneer u voorwaardelijke logica, bevestigingsregels, of bedrijfsprocessen moet uitvoeren.

**hoe te gebruiken:** beschrijf duidelijk de bedrijfslogica, specificerend voorwaarden en acties.

**Vragen van het Voorbeeld - Eenvoudige Voorwaardelijke Logische:**

     creeer een regel die @spouseInformation paneel toont slechts wanneer @maritalStatus &quot;Gehuwd&quot;evenaart 

**Vraag van het Voorbeeld - Complexe BedrijfsRegels:**

     voer uitvoerige de toepassingsbevestiging van de leningstoepassing uit:
    
    **Inkomensbevestiging:** 
     - als @annualIncome minder dan 30000 is:
     - toon waarschuwingsbericht: &quot;Inkomsten kunnen voor gevraagd leningsbedrag ontoereikend zijn&quot;
     - Vereis extra inkomensdocumentatie 
     - Vertoning bericht: &quot;De extra documentatie kan worden vereist&quot;
     - als @annualIncome groter is 100000:
     - toon de opties van de premieservices 
     - laat prioritaire verwerkingscontroledoos 
    
    **Leeftijd-Gebaseerde Bevestiging toe:** 
     - als @age minder dan 18 is:
     - toon de sectie van ouder/van de Bewaakzame informatie 
     - maak ouder handtekeningupload verplicht 
     - vervang- Verzenden de Verandert de tekst aan &quot;Voorlegt knooptekst voor Overzicht&quot; 14&rbrace; - als @age 65 of ouder is:
     - toon senior kortingsopties 
     - voeg de sectie van toegankelijkheidsvoorkeuren toe 
    

**regel-Specifieke herinneringen:**

     creeer a **zichtregel** die @spouseInformation paneel toont slechts wanneer @maritalStatus &quot;Gehuwd&quot;of &quot;Binnenlands Partnerschap&quot;evenaart 
    
     **progressieve onthulling** toevoegt waar de extra vragen gebaseerd op vorige antwoorden verschijnen. Begin met basisinfo, dan toon relevante follow-ups 
    
     voert **smart gebreken** uit waar @country selectie verwante gebieden automatisch-plaatst. Handmatige overschrijving toestaan 

## Gegevensintegratie en -verzending

**wanneer te gebruiken:** wanneer u vormen met achterste deelsystemen, gegevensbestanden, of de externe diensten moet verbinden.

**hoe te gebruiken:** Begin met basisvoorleggingsopstelling, dan voeg extra integratie incrementeel toe. Geef het integratietype, de vereisten voor de gegevensindeling en de voorkeuren voor foutafhandeling op.

**Vragen van het Voorbeeld - Begin met BasisVerzending:**

     vorm basisvormvoorlegging voor @applicationForm:
    
    **Primaire Verzending:** 
     - verzend vormgegevens naar het eindpunt REST: `/api/v1/toepassingen ` 
     - de gegevens van het Formaat als JSON 
     - toon succesbericht: &quot;De met succes voorgelegde Toepassing&quot;
     - toon foutenmelding als de voorlegging ontbreekt: &quot;Verzending, gelieve opnieuw te proberen&quot;

**dan voeg geleidelijk Secundaire Acties toe:**

     voegt e-mailbericht aan @applicationForm toe: Verzend bevestigingsmail naar @email adres met het aantal van de toepassingsverwijzing 
    
     toevoegt de integratie van CRM aan @applicationForm: Creeer nieuw loodverslag met @firstName, @lastName, @email, en plaats Status aan &quot;Nieuwe Toepassing&quot;

**Vraag van het Voorbeeld - Standaard multi-kanaalverzending:**

     vormt vormvoorlegging met veelvoudige gegevensbestemmingen:
    
    **Primaire Verzending:** 
     - verzend vormgegevens naar het eindpunt REST: `/api/v1/toepassingen ` 
     - omvat authentificatiekop met API sleutel 
     - de gegevens van het Formaat zoals JSON met genestelde voorwerpen voor adres en werkgelegenheid 
     - de succesvolle reactie van de Handle (201) door te tonen dank bericht 
    
     &#x200B;* Secundair Handelingen:** 
     - verzend bericht e-mail naar aanvrager op @email adres 
     - de toepassingsgegevens van het Exemplaar aan het volgen systeem 
     - de werkschema van de trekker voor goedkeuringsproces 
     - creeer verslag in CRM met loodstatus &quot;Nieuwe Toepassing&quot;
    
     **Fout Behandeling:** 
     - als de primaire voorlegging ontbreekt, sparen gegevens plaatselijk en probeert 
     - toon gebruikersvriendelijk bericht: &quot;Subtoon missie tijdelijk niet beschikbaar&quot;
     - Verstrek optie om vormgegevens als steun te downloaden 
     - verzend waakzame e-mail naar adminteam over ontbroken voorlegging 
    
     **Successtroom:* 
     - Redirect aan bevestigingspagina met toepassingsverwijzingsaantal 
     - verzend bevestigingsmail met volgende stappen 
     - Vertoning geschatte verwerkingschronologie 

**integratie-Specifieke herinneringen:**

     verbind dit formulier met **CRM systeem** om nieuwe leads te maken. Wijs @firstName aan FirstName, @email aan E-mail toe, plaats LeadSource aan &quot;de Vorm van het Web&quot;, en Status aan &quot;Nieuwe&quot;
    
     Opstelling **werkschemamarkering** wanneer de vorm wordt voorgelegd. Geef alle vormgegevens door en teweegbrengt goedkeuringswerkschema met managerbericht 
    
     vormen **gegevensbestand integratie** om vormvoorlegging als verslagen te bewaren. Nieuwe map maken voor elke verzending met geüploade documenten 



## Opdrachtverwijzing

### Essentiële opdrachten

| Opdracht | Hoofd-/kleine letters | Voorbeeld |
|---------|---------------|---------|
| `/create-form` | Nieuwe formulieren starten | `/create-form employee onboarding with personal info and benefits selection` |
| `/add-form` | Formulieren toevoegen aan pagina&#39;s | `/add-form newsletter signup with email and preferences` |
| `/update-layout` | De formulierstructuur wijzigen | `/update-layout wizard with 4 steps: info, preferences, review, confirm` |
| `/update-field` | Veldeigenschappen wijzigen | `/update-field @email to be mandatory with real-time validation` |
| `/create-rule` | Dynamisch gedrag toevoegen | `/create-rule show @spouseInfo if @maritalStatus equals "Married"` |
| `/create-panel` | Formuliersecties ordenen | `/create-panel Employment Details with job title, company, salary fields` |
| `/add-panel` | Ontwerpen converteren | `/add-panel from uploaded form image with field recognition` |
| `/help` | Hulp krijgen | `/help how to implement multi-step validation?` |

### Veldverwijzingen

Gebruik de syntaxis `@fieldName` om te verwijzen naar bestaande velden in uw vragen:

- `@email` - Referentie-e-mailveld
- `@firstName` - Referentie, voornaamveld
- `@maritalStatus` - Referentieveld voor burgerlijke staat

### Componenttypen

**de Componenten van de Input:**

- `text`, `email`, `number`, `tel`, `date`, `checkbox`, `radio`, `dropdown`, `file`, `textarea`

**Componenten van de Container:**

- `fieldset`, `panel`, `repeatable`, `wizard`

### Componenteigenschappen

**Universele Eigenschappen (Alle Componenten):**

- **Type**: Het type van component
- **Naam**: Het herkenningsteken van het gebied voor vormvoorlegging
- **Etiket**: De tekst van de vertoning voor het gebied
- **Beschrijving**: De tekst van de hulp voor het gebied
- **Zichtbaar**: Van Boole voor aanvankelijke zicht
- **Verplicht**: Van Boole voor vereiste gebieden

**Eigenschappen van het Gebied van de Input:**

- **Waarde**: Gebrek/aanvankelijke waarde
- **Placeholder**: De tekst van de tip voor inputgebieden
- **Min**: Minimumwaarde (voor aantallen/data)
- **Max**: Maximumwaarde (voor aantallen/data)

**Dossier uploadt Eigenschappen:**

- **keurt** goed: De types van dossier (.pdf, .doc, .docx, .jpg, .png, enz.)
- **Veelvoud**: Van Boole voor veelvoudige dossierselectie

**Eigenschappen van de Controle van de Selectie:**

- **Opties**: Keuzen voor dropdowns (komma-gescheiden lijst)
- **Gecontroleerd**: Standaard selectie voor checkboxes/radio

**Eigenschappen van de Container:**

- **Veldset**: Groepering verwante gebieden
- **Herhalbaar**: Van Boole voor herhaalbare secties

**Geavanceerde Eigenschappen:**

- **Zichtbare Uitdrukking**: Formule voor voorwaardelijk zicht (=formule)
- **Uitdrukking van de Waarde**: Formule voor berekende waarden (=formule)

### Integratieopdrachten

**legt Acties voor:**

- E-mailmeldingen
- REST API-verzendingen
- Cloudopslag (Azure, SharePoint)
- Workflowautomatisering (Power Automate, Workfront Fusion)
- Marketingplatforms (Marketo)
- CRM-integratie

### Syntaxisrichtlijnen vragen

- **Verwijzingen van het Gebied**: Gebruik `@fieldName` voor bestaande gebieden
- **Bevelen**: Gebruik `/command` voor specifieke acties
- **Natuurlijke Taal**: Beschrijf vereisten duidelijk en specifiek

### Controlelijst voor validatie

Voor uitvoerige beste praktijken en bevestigingsrichtlijnen, zie de [&#x200B; Begonnen Gids van de Bouwer van de Ervaring van Forms &#x200B;](/help/forms/experience-builder/forms-experience-builder-getting-started.md).

*Deze snelle bibliotheek wordt onophoudelijk bijgewerkt gebaseerd op gebruiker terugkoppelt en de nieuwe mogelijkheden van de Bouwer van de Ervaring van Forms. Voor de recentste eigenschappen en de voorbeelden, controleer de [&#x200B; documentatie van AEM Forms &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html?lang=nl-NL).*
