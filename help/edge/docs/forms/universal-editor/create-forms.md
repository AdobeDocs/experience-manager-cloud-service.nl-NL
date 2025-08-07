---
title: Adaptieve Forms maken en publiceren met Edge Delivery Services
description: Stapsgewijze instructies voor het maken, ontwerpen en publiceren van Adaptieve Forms met gebruik van Core Component- of Edge Delivery Services-sjablonen in AEM, met de nadruk op technische nauwkeurigheid en duidelijkheid.
keywords: adaptieve formulieren, services voor randlevering, kerncomponenten, universele editor, formulierontwerp, AEM-formulieren, sjabloonselectie, formulierpublicatie
feature: Edge Delivery Services
role: User, Developer
level: Beginner
exl-id: 1eab3a3d-5726-4ff8-90b9-947026c17e22
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '1773'
ht-degree: 0%

---


# Adaptieve Forms maken en publiceren met Edge Delivery Services

Dit document bevat instructies voor het maken, configureren en publiceren van Adaptive Forms in AEM met Edge Delivery Services. De klasse omvat Core Component- en Edge Delivery Services-sjablonen.

Aan het einde van deze handleiding leert u hoe u:

- Selecteer het juiste sjabloontype voor uw gebruik
- Formulieren maken met Core Components of Edge Delivery Services-sjablonen
- Auteurformulieren met de juiste editor
- Formulieren configureren en publiceren naar Edge Delivery Services
- Gepubliceerde formulieren openen en implementatie controleren

## Sjabloonselectie

Voordat u begint, bepaalt u welk sjabloontype u op uw vereisten uitlijnt:

| Criteria | Sjabloon voor kerncomponenten | Edge Delivery Services-sjabloon |
|-------------------------|-----------------------------------------|-------------------------------------|
| Best voor | Bedrijfsworkflows, complexe integratie | Krachtige openbare formulieren |
| Editor | Adaptieve Forms Editor | Universele editor |
| Publiceren | AEM Publish + Edge Delivery Services | Alleen Edge Delivery Services |
| Complexiteit | Geavanceerde formuliermogelijkheden | Gestroomlijnde, snelle formulieren |
| Integratie | Volledig AEM-ecosysteem | Ontwikkeling op basis van git |
| Leercurve | Kennis hebben van AEM-gebruikers | Moderne, vereenvoudigde aanpak |

**Begeleiding van het Besluit:**

- De Componenten van de Kern van het gebruik **voor complexe werkschema&#39;s, diepe integratie van AEM, of als het leveraging van bestaande activa van AEM.**
- Het gebruik **Edge Delivery Services** voor prestaties, eenvoud, en moderne ontwikkelingspraktijken.

![ Besluit van de Selectie van het Malplaatje ](/help/edge/docs/forms/universal-editor/assets/template-selection-decision.svg)
*Stroomschema van het Besluit voor het kiezen van het aangewezen malplaatjetype*

## Vereisten

Zorg ervoor dat aan de volgende voorwaarden is voldaan voordat u verdergaat:

### Technische vereisten

- **AEM Forms as a Cloud Service**: Een actieve auteursinstantie met een vergunning van Forms.
- **Rekening GitHub**: Persoonlijke of organisatorische rekening voor bewaarplaatsbeheer.
- **Opstelling van de Bewaarplaats**: Kies één van het volgende:
   - **Nieuw Project**: [ creeer een nieuw project van AEM met het AanpassingsBlok van Forms ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block). De opslagplaats is vooraf geconfigureerd voor Edge Delivery Services.
   - **Bestaand Project**: [ voeg het Aangepaste Blok van Forms aan een bestaande bewaarplaats ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) toe en werk de configuratie bij.

### Omgevingsconfiguratie

- **AEM-GitHub Verbinding**: [ Vestig een verbinding ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template) tussen uw instantie van AEM en bewaarplaats GitHub.
- **Edge Delivery Services**: Zorg ervoor de bewaarplaats voor automatische plaatsing wordt gevormd.
- **Toestemmingen**: Verifieer u de noodzakelijke toegangsrechten voor vormverwezenlijking en het publiceren hebt.

### Validatie instellen


1. Bevestig dat de GitHub-opslagplaats het Adaptive Forms Block bevat.
2. Test de verbinding tussen AEM en uw gegevensopslagplaats GitHub.
3. Zorg ervoor dat u inhoud naar Edge Delivery Services kunt publiceren.



## Workflow voor het maken en publiceren van formulieren

Het proces bestaat uit drie hoofdfasen:

- **Fase 1:** [ de Selectie van het Malplaatje en de Creatie van de Vorm ](#step-1-template-selection-and-form-creation)
- **Fase 2:** [ Authoring en Ontwerp van de Vorm ](#step-2-form-authoring-and-design)
- **Fase 3:** [ Configuratie en het Publiceren ](#step-3-configuration-and-publishing)

Elke fase omvat bevestigingsstappen om correcte opstelling te bevestigen.

![ Drie Werkschema van de Fase ](/help/edge/docs/forms/universal-editor/assets/three-phase-workflow.svg)
*Overzicht van de drie belangrijkste fasen in vormverwezenlijking en het publiceren*

### Stap 1: Sjabloonselectie en Formulierontwerp

Selecteer de workflow op basis van uw sjabloonkeuze:

>[!BEGINTABS]

>[!TAB  Malplaatje van Edge Delivery Services ]

**Geval van het Gebruik:** Krachtige vormen en moderne ontwikkelingswerkschema&#39;s.

**Eigenschappen:** Universal Editor creatie en het publiceren van Edge Delivery Services.

#### Procedure

1. **Van de Toegang Vorm creatie**
   - Meld u aan bij de AEM Forms as a Cloud Service-auteur.
   - Navigeer aan **Adobe Experience Manager** > **Forms** > **Forms &amp; Documenten**.
   - Klik **creëren** > **Aanpassings Forms**.

1. **Uitgezochte Malplaatje**
   - In het **Source** lusje, selecteer een **op Edge Delivery Services-Gebaseerde malplaatje**.
   - **creeer** knoop wordt toegelaten.

     ![ creeer EDS Forms ](/help/edge/assets/create-eds-forms.png)

1. **vorm Opties (Facultatief)**
   - **Gegevens Source tabel**: Selecteer gegevensintegratie indien vereist.
   - **Verzending tabel**: Kies een verzendactie (kan later worden gevormd).
   - **lusje van de Levering**: Plaats het publiceren/unpublishing programma.

1. **Volledige Opstelling van de Vorm**
   - Klik **creëren** om de tovenaar van de Aanmaak van de Vorm te openen.
   - Voer het volgende in:
      - **Naam**: Interne herkenningsteken (geen ruimten, gebruiks koppeltekens).
      - **Titel**: De naam van de vertoning voor uw vorm.
      - **GitHub URL**: Bewaarplaats URL (bijvoorbeeld, `https://github.com/your-org/your-repo`).

   ![ creeer de Tovenaar van de Vorm ](/help/edge/assets/create-form-wizard.png)

1. **Bevestiging**
   - Na het klikken **creeer**, verifieer:
      - Het formulier wordt geopend in de Universal Editor.
      - De GitHub URL is correct verbonden.
      - Het componentpalet is beschikbaar.
      - Het canvas van het formulier is zichtbaar.

   ![ Universele Interface van de Redacteur ](/help/edge/assets/author-form.png)

**Resultaat:** de vorm is klaar voor creatie in de Universele Redacteur.

>[!TAB  Malplaatje van de Component van de Kern ]

**Geval van het Gebruik:** de werkschema&#39;s van de Onderneming en complexe integratie.

**Eigenschappen:** het Aanpassings van de Redacteur van Forms, het dubbele publiceren (AEM + Edge Delivery Services), geavanceerde vormmogelijkheden.

#### Procedure

1. **Van de Toegang Vorm creatie**
   - Meld u aan bij de AEM Forms as a Cloud Service-auteur.
   - Navigeer aan **Adobe Experience Manager** > **Forms** > **Forms &amp; Documenten**.
   - Klik **creëren** > **Aanpassings Forms**.

1. **Uitgezochte Malplaatje en Thema**
   - In het **Source** lusje, selecteer a **op component-Gebaseerde malplaatje van de Kern**.
   - Kies a **thema** voor het stileren.
   - **creeer** knoop wordt toegelaten.

   {de Selectie van het Malplaatje van de Component van 0} Kern ![](/help/forms/assets/core-component-based-template.png)

1. **vorm Opties (Facultatief)**
   - **Gegevens Source tabel**: Selecteer gegevensintegratie indien vereist.
   - **Verzending tabel**: Kies een verzendactie (kan later worden gevormd).
   - **lusje van de Levering**: Plaats het publiceren/unpublishing programma.

1. **Volledige Opstelling van de Vorm**
   - Klik **creëren** om de tovenaar van de Aanmaak van de Vorm te openen.
   - Voer het volgende in:
      - **Naam**: Interne herkenningsteken (geen ruimten, gebruiks koppeltekens).
      - **Titel**: De naam van de vertoning voor uw vorm.
      - **Weg**: De plaats van de opslag in de bewaarplaats van AEM.

     ![ creeer de Tovenaar van de Vorm ](/help/forms/assets/create-cc-form.png)

1. **Bevestiging**
   - Na het klikken **creeer**, verifieer:
      - Het formulier wordt geopend in de Adaptive Forms Editor.
      - De werkbalk van de component is beschikbaar.
      - Het deelvenster Eigenschappen is toegankelijk.
      - Thema-opmaak wordt toegepast.

     ![ de Aanpassings Redacteur van de Vorm ](/help/forms/assets/af-editor-form.png)

**Resultaat:** de vorm is klaar voor creatie in de Adaptieve Redacteur van Forms.

>[!ENDTABS]

### Stap 2: Formulierontwerp en -ontwerp

De ontwerpervaring varieert per sjabloon:

- **Malplaatje van Edge Delivery Services**: Universele Redacteur
- **Malplaatje van de Component van de Kern**: De Adaptieve Redacteur van Forms

![&#128279;](/help/edge/docs/forms/universal-editor/assets/editor-comparison.svg) Vergelijking van 0&rbrace; Redacteur
 Vergelijking van Universele Redacteur met de Adaptieve mogelijkheden van de Redacteur van Forms **

>[!BEGINTABS]

>[!TAB  Universele Redacteur (Edge Delivery Services) ]

**Interface:** Modern, gestroomlijnde het uitgeven geoptimaliseerd voor prestaties.

#### Formuliercomponenten toevoegen

1. **Bibliotheek van de Component van de Toegang**
   - Open de Content browser in Universal Editor.
   - Navigeer aan de **Aangepaste component van de Vorm** in de inhoudsboom.

   ![ de Navigatie van de Boom van 0&rbrace; Inhoud](/help/edge/assets/content-tree.png)

1. **voeg de Gebieden van de Vorm** toe
   - Klik **toevoegen** pictogram om de componentenbibliotheek te openen.
   - Selecteer componenten van de **Adaptieve lijst van Componenten van de Vorm**.
   - Sleep componenten naar het canvas van het formulier.

   ![ voegt Componenten ](/help/edge/assets/add-component.png) toe

1. **Ontwerp de Vorm**
   - Veldeigenschappen configureren in het deelvenster Eigenschappen.
   - Stel validatieregels en -gedrag in.
*s Pas de opmaak en lay-out naar wens aan.

   ![ Voltooide Vorm van de Registratie ](/help/edge/assets/contact-us.png)

#### Validatie

- Alle vereiste velden zijn aanwezig.
- Veldeigenschappen zijn op de juiste wijze geconfigureerd.
- Layout is responsief en toegankelijk.
- Validatieregels functioneren naar behoren.

#### Volgende stappen

- [ vormen voorlegt acties ](/help/edge/docs/forms/universal-editor/submit-action.md) voor gegevens behandeling.
- [ Universele gids van de Redacteur ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg) voor geavanceerde eigenschappen.

>[!TAB  de Aangepaste Redacteur van Forms (de Componenten van de Kern) ]

**Interface:** Volledig-gekenmerkte het uitgeven met geavanceerde vormmogelijkheden.

#### Formuliercomponenten toevoegen

1. **Bibliotheek van de Component van de Toegang**
   - Klik **component van het Tussenvoegsel** in de **componenten van de Belemmering hier** sectie.

   ![ Gebied van de Invoeging van de Component ](/help/forms/assets/drag-components-af-editor.png)

2. **voeg de Gebieden van de Vorm** toe
   - Blader de **Adaptieve lijst van Componenten van de Vorm**.
   - Sleep de gewenste componenten naar het formulier.
   - Geavanceerde componenten van het gebruik zoals panelen, tovenaars, en gegevensintegratie.

   ![ voeg de Bibliotheek van Componenten ](/help/forms/assets/add-component-af.png) toe

3. **Ontwerp de Vorm**
   - Veldeigenschappen configureren in het deelvenster Eigenschappen.
   - Stel complexe validatieregels en bedrijfslogica in.
   - Pas thema&#39;s en geavanceerde stijlen toe.

   ![ Voltooide Vorm van de Inschrijving ](/help/forms/assets/af-editor-form.png)

#### Validatie

- Alle vereiste velden zijn aanwezig.
- Complexe validatieregels worden geconfigureerd.
- Thema-opmaak wordt toegepast.
- Gegevensintegratie werkt zoals verwacht (indien van toepassing).

#### Volgende stappen

- [ vormen voorlegt acties ](/help/forms/configure-submit-actions-core-components.md) voor geavanceerde werkschema&#39;s.
- {de gids van de Componenten van 0} Kern [ voor ondernemingseigenschappen.](/help/forms/creating-adaptive-form-core-components.md)

>[!ENDTABS]

### Stap 3: Configuratie en publicatie

Configureer Edge Delivery Services en publiceer uw formulier. Het proces verschilt per sjabloontype.

#### Edge Delivery Services-configuratie

>[!BEGINTABS]
>[!TAB  Malplaatje van Edge Delivery Services (Automatisch) ]

**Configuratie:** Automatisch (geen vereiste handopstelling).

- De verbinding van de bewaarplaats GitHub en de configuratie van Edge Delivery Services worden gecreeerd tijdens vormverwezenlijking.
- Publicatie-eindpunten worden automatisch geconfigureerd.

**Verificatie:**

- De configuratie bevestigen wordt weergegeven in de instellingen van het formulier.
- Zorg ervoor dat de GitHub-URL correct is gekoppeld.

![ Automatische Configuratie EDS ](/help/edge/assets/aem-instance-eds-configuration.png)

>[!TAB  Malplaatje van de Component van de Kern (Hand) ]

**Configuratie:** Vereiste handopstelling.

#### Handmatige configuratiestappen

1. **Hulpmiddelen van de Configuratie van de Toegang**
   - Navigeer aan **Hulpmiddelen** > **de Diensten van de Wolk** > **Configuratie van Edge Delivery Services**.

   ![ EDS Toegang van de Configuratie ](/help/edge/assets/select-eds-conf.png)

1. **creeer Configuratie**
   - Selecteer de map die overeenkomt met de naam van het formulier (bijvoorbeeld `forms/enrollment-form` ).
   - Klik **creëren** > **Configuratie**.

   ![ creeer EDS Configuratie ](/help/forms/assets/create-eds-conf.png)

1. **vorm Eigenschappen**
   - Klik **Configuratie van Edge Delivery Services**.
   - Selecteer **Eigenschappen** om de configuratiedialoog te openen.

   ![ Eigenschappen van de Configuratie ](/help/forms/assets/eds-conf.png)

1. **vastgestelde Parameters**
   - **Vereist:**
      - **Organisatie**: De organisatienaam van GitHub.
      - **Naam van de Plaats**: De bewaarplaatsnaam van GitHub.
      - **Tak**: De naam van de tak (verlaten leeg voor hoofd).
   - **Facultatief:**
      - **Gastheer van Edge**: Het gebrek (publiceert aan zowel .page als .live).
      - **Token van de Authentificatie van de Plaats**: Voor veilige authentificatie (indien vereist).

1. **sparen Configuratie**
   - Klik **sparen en Sluiten**.

#### Validatie

- Configuratie is gemaakt.
- De organisatie en de bewaarplaats van GitHub worden correct gespecificeerd.
- Branch-instellingen komen overeen met de structuur van de repository.
- Het formulier wordt weergegeven in de configuratiemap.

>[!ENDTABS]

#### Het formulier publiceren

>[!BEGINTABS]
>[!TAB  Universele Redacteur het Publiceren ]

**voor de Malplaatjes van Edge Delivery Services**

1. In Universele Redacteur, klik **publiceren** knoop (hoger-juiste hoek).
2. Bevestig het publiceren succes in de dialoog.
3. Maak een notitie van de gegenereerde URL&#39;s voor gefaseerde en live versies.

   ![ Universele Redacteur publiceert ](/help/edge/assets/publish-form.png)

- [Handleiding voor publiceren](/help/edge/docs/forms/universal-editor/publish-forms.md)

>[!TAB  het AanpassingsUitgeven van de Redacteur van Forms ]

1. Selecteer in de Experience Manager Forms-console het formulier dat u wilt publiceren.
2. Klik op **[!UICONTROL Publish]** op de werkbalk. Referentie-elementen controleren die moeten worden gepubliceerd.

![ publiceer Vorm op de Adaptieve Redacteur van de Vorm ](/help/forms/assets/publish-af-editor.png)

>[!NOTE]
>
> Zie [ Publicatie in Experience Manager Forms beheren ](/help/forms/manage-publication.md) voor details.

>[!ENDTABS]

## URL&#39;s van formulier

Gepubliceerde formulieren zijn toegankelijk via Edge Delivery Services-URL&#39;s.

### URL-structuur

- **Gelaagd (Voorproef/het Testen):**

  ```
  https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>
  ```

- **Levend (Productie):**

  ```
  https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>
  ```

#### URL-parameters

- `<branch>`: naam van GitHub-vertakking (bijvoorbeeld `main` , `develop` )
- `<repo>`: naam van GitHub-opslagplaats (bijvoorbeeld `my-forms-project` )
- `<owner>`: GitHub-organisatie of gebruikersnaam (bijvoorbeeld `company-name` )
- `<form_name>`: Formulierid zoals gedefinieerd in AEM (bijvoorbeeld `contact-us` )

#### Voorbeeld

Voorbeeld voor formulier `contact-us` in gegevensopslagruimte `forms-project` onder organisatie `acme-corp` :

- **Staged:** `https://main--forms-project--acme-corp.aem.page/content/forms/af/contact-us`
- **Levend:** `https://main--forms-project--acme-corp.aem.live/content/forms/af/contact-us`

#### Omgevingsverschillen

- **Gelaagd (.page):** Laatste veranderingen voor het testen.
- **Levend (.live):** Gepubliceerde inhoud voor productie.

![ Structuur URL ](/help/edge/docs/forms/universal-editor/assets/url-structure.svg)
*de structuurindeling van Edge Delivery Services van URL*

#### Visuele voorbeelden

**Malplaatje van Edge Delivery Services:**

- Staged: ![ Van de Registratie vorm gestage versie ](/help/forms/assets/registration-form-staged-version.png)
- Levend: ![ de vorm van de Registratie levende versie ](/help/forms/assets/registration-form-live-version.png)

**Malplaatje van de Component van de Kern:**

- Staged: ![ de vorm van de Inschrijving gestapelde versie ](/help/forms/assets/enrollment-form-staged-version.png)
- Levend: ![ de vorm van de Inschrijving levende versie ](/help/forms/assets/enrollment-form-live-version.png)

## Problemen oplossen

Hieronder vindt u algemene problemen en oplossingen voor AEM Forms met Edge Delivery Services.

+++Formulier wordt niet geladen

**Uitgave:** De Vorm URL keert 404 of lege pagina terug.

**Resolutie:**

- Verwijder de extensie `.html` van URL&#39;s.
- Controleer of het formulier is gepubliceerd.
- Controleer de bewaarplaats GitHub voor het AanpassingsBlok van Forms.
- Zorg ervoor dat de naam van het formulier overeenkomt met de URL (hoofdlettergevoelig).

+++

+++Configuratieproblemen

**Uitgave:** de configuratie van Edge Delivery Services werkt niet.

**Resolutie:**

- Zorg ervoor dat de GitHub-URL de `https://github.com/owner/repository` -indeling heeft.
- Gebruik de correcte taknaam in configuratie.
- Toegang tot opslagplaats controleren (openbaar of geverifieerd).
- Controleer `fstab.yaml` voor correcte details GitHub.

+++

+++Problemen met publiceren

**Uitgave:** Veranderingen verschijnen niet op de levende plaats.

**Resolutie:**

- Wacht 2-3 minuten op CDN geheim voorgeheugen verfrist zich.
- Bevestig dat de publicatieworkflow is voltooid.
- Test eerst op een gefaseerde (.page) omgeving.
- Verzeker de bewaarplaats GitHub wordt bijgewerkt.

+++

+++Universal Editor-problemen

**Uitgave:** kan vorm of componenten uitgeven niet ladend.

**Resolutie:**

- Gebruik een ondersteunde browser (Chrome, Firefox, Safari).
- Cache en cookies van de browser wissen.
- Controleer de netwerkconnectiviteit.
- Machtigingen van auteur bevestigen.

+++

+++Fout bij verzenden van formulier

**Uitgave:** de inzendingen van de Vorm werken niet.

**Resolutie:**

- Configureer de verzendactie in formuliereigenschappen.
- Test de eindpunten van de verzending handmatig.
- Controleer de CORS-instellingen bij het insluiten van formulieren.
- Controleer of de vereiste velden zijn geconfigureerd.

+++

+++Prestatieproblemen

**Uitgave:** Langzame vormlading of slechte prestaties.

**Resolutie:**

- Afbeeldingen optimaliseren.
- Verwijder overbodige componenten.
- Gebruik Edge Delivery Services CDN.
- Aangepaste JavaScript/CSS minimaliseren.

+++

+++Help opvragen

Als er problemen blijven optreden:

1. Controleer de Adobe Experience Cloud-servicestatus.
2. Herzie {de documentatie van 0} Edge Delivery Services [.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/overview.html)
3. Bezoek [ Gemeenschap van de Liga van de Ervaring van Adobe ](https://experienceleaguecommunities.adobe.com/).
4. Neem contact op met de klantenservice van Adobe.

+++

## Volgende stappen

Nadat u het maken en publiceren van formulieren hebt voltooid, kunt u het volgende overwegen:

### Onmiddellijke handelingen

- Test het formulier met deze handleiding.
- Valideer uw GitHub-opslagplaats en AEM-verbinding.
- Voorbeeldformulieren bekijken.

### Geavanceerde onderwerpen

- [ vormt voorleggen Acties ](/help/edge/docs/forms/universal-editor/submit-action.md): De opstelling gegevens die en integratie behandelen.
- [ Modellen van de Gegevens van de Vorm ](/help/forms/create-form-data-models.md): Verbind vormen met achterste gegevensbronnen.

### Optimalisatie van prestaties

- [ Beste praktijken van Edge Delivery Services ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/overview.html): Maximaliseer prestaties.
- [ Analytics van de Vorm ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/analytics.html): De vormprestaties en gebruikersgedrag van het spoor.

