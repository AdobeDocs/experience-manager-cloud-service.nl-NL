---
title: Adaptieve Forms maken en publiceren met Edge Delivery Services
description: Stapsgewijze instructies voor het maken, ontwerpen en publiceren van Adaptieve Forms met Edge Delivery Services-sjablonen in AEM, met de nadruk op technische nauwkeurigheid en duidelijkheid.
keywords: adaptieve formulieren, services voor randlevering, universele editor, maken van formulieren, AEM-formulieren, publiceren
feature: Edge Delivery Services
role: User, Developer
level: Beginner
exl-id: 1eab3a3d-5726-4ff8-90b9-947026c17e22
source-git-commit: 07160248d5b5817d155a118475878ce04a687a32
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 0%

---


# Adaptieve Forms maken en publiceren met Edge Delivery Services

Dit document bevat stapsgewijze instructies voor het maken, configureren en publiceren van Adaptieve Forms met Edge Delivery Services-sjablonen in AEM. Het behandelt de volledige werkstroom van de verwezenlijking van vorm tot productieleiding.

Aan het einde van deze handleiding leert u hoe u:

- Formulieren maken met Edge Delivery Services-sjablonen
- Auteurformulieren met Universal Editor
- Formulieren configureren en publiceren naar Edge Delivery Services
- Gepubliceerde formulieren openen en implementatie controleren



## Vereisten

Zorg ervoor dat aan de volgende voorwaarden is voldaan voordat u verdergaat:


- **AEM Forms as a Cloud Service**: Een actieve auteursinstantie met een vergunning van Forms.
- **Rekening GitHub**: Persoonlijke of organisatorische rekening voor bewaarplaatsbeheer.
- **Opstelling van de Bewaarplaats**: Kies één van het volgende:
   - **Nieuw Project**: [&#x200B; creeer een nieuw project van AEM met het AanpassingsBlok van Forms &#x200B;](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block). De opslagplaats is vooraf geconfigureerd voor Edge Delivery Services.
   - **Bestaand Project**: [&#x200B; voeg het Aangepaste Blok van Forms aan een bestaande bewaarplaats &#x200B;](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) toe en werk de configuratie bij.

- **AEM-GitHub Verbinding**: [&#x200B; Vestig een verbinding &#x200B;](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template) tussen uw instantie van AEM en bewaarplaats GitHub.
- **Edge Delivery Services**: Zorg ervoor de bewaarplaats voor automatische plaatsing wordt gevormd.
- **Toestemmingen**: Verifieer u de noodzakelijke toegangsrechten voor vormverwezenlijking en het publiceren hebt.

- Bevestig dat de GitHub-opslagplaats het Adaptive Forms Block bevat.



## Workflow voor het maken en publiceren van formulieren

Het proces bestaat uit drie hoofdfasen:

- **Fase 1:** [&#x200B; de Creatie van de Vorm &#x200B;](#step-1-form-creation)
- **Fase 2:** [&#x200B; Authoring en Ontwerp van de Vorm &#x200B;](#step-2-form-authoring-and-design)
- **Fase 3:** [&#x200B; Configuratie en het Publiceren &#x200B;](#step-3-configuration-and-publishing)

Elke fase omvat bevestigingsstappen om correcte opstelling te bevestigen.


### Stap 1: Formulier maken

1. **Van de Toegang Vorm creatie**
   - Meld u aan bij de AEM Forms as a Cloud Service-auteur.
   - Navigeer aan **Adobe Experience Manager** > **Forms** > **Forms &amp; Documenten**.
   - Klik **creëren** > **Aanpassings Forms**.

1. **Uitgezochte Malplaatje**
   - In het **Source** lusje, selecteer een **op Edge Delivery Services-Gebaseerde malplaatje**.
   - **creeer** knoop wordt toegelaten.

     ![&#x200B; creeer EDS Forms &#x200B;](/help/edge/assets/create-eds-forms.png)

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

   ![&#x200B; creeer de Tovenaar van de Vorm &#x200B;](/help/edge/assets/create-form-wizard.png)

1. **Bevestiging**
   - Na het klikken **creeer**, verifieer:
      - Het formulier wordt geopend in de Universal Editor.
      - De GitHub URL is correct verbonden.
      - Het componentpalet is beschikbaar.
      - Het canvas van het formulier is zichtbaar.

   ![&#x200B; Universele Interface van de Redacteur &#x200B;](/help/edge/assets/author-form.png)

**Resultaat:** de vorm is klaar voor creatie in de Universele Redacteur.

### Stap 2: Formulierontwerp en -ontwerp


1. **Bibliotheek van de Component van de Toegang**
   - Open de Content browser in Universal Editor.
   - Navigeer aan de **Aangepaste component van de Vorm** in de inhoudsboom.

   ![&#x200B; de Navigatie van de Boom van 0&rbrace; Inhoud](/help/edge/assets/content-tree.png)

1. **voeg de Gebieden van de Vorm** toe
   - Klik **toevoegen** pictogram om de componentenbibliotheek te openen.
   - Selecteer componenten van de **Adaptieve lijst van Componenten van de Vorm**.
   - Sleep componenten naar het canvas van het formulier.

   ![&#x200B; voegt Componenten &#x200B;](/help/edge/assets/add-component.png) toe

1. **Ontwerp de Vorm**
   - Veldeigenschappen configureren in het deelvenster Eigenschappen.
   - Stel validatieregels en -gedrag in.
   - Pas de opmaak en lay-out naar wens aan.

   ![&#x200B; Voltooide Vorm van de Registratie &#x200B;](/help/edge/assets/contact-us.png)

#### Validatie

- Alle vereiste velden zijn aanwezig.
- Veldeigenschappen zijn op de juiste wijze geconfigureerd.
- Layout is responsief en toegankelijk.
- Validatieregels functioneren naar behoren.

#### Volgende stappen

- [&#x200B; vormen voorlegt acties &#x200B;](/help/edge/docs/forms/universal-editor/submit-action.md) voor gegevens behandeling.
- [&#x200B; Universele gids van de Redacteur &#x200B;](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg) voor geavanceerde eigenschappen.

### Stap 3: Configuratie en publicatie

Configureer Edge Delivery Services en publiceer uw formulier.

**Configuratie:** Automatisch (geen vereiste handopstelling).

- De verbinding van de bewaarplaats GitHub en de configuratie van Edge Delivery Services worden gecreeerd tijdens vormverwezenlijking.
- Publicatie-eindpunten worden automatisch geconfigureerd.

**Verificatie:**

- De configuratie bevestigen wordt weergegeven in de instellingen van het formulier.
- Zorg ervoor dat de GitHub-URL correct is gekoppeld.

![&#x200B; Automatische Configuratie EDS &#x200B;](/help/edge/assets/aem-instance-eds-configuration.png)

#### Het formulier publiceren

1. In Universele Redacteur, klik **publiceren** knoop (hoger-juiste hoek).
2. Bevestig het publiceren succes in de dialoog.
3. Maak een notitie van de gegenereerde URL&#39;s voor gefaseerde en live versies.

   ![&#x200B; Universele Redacteur publiceert &#x200B;](/help/edge/assets/publish-form.png)

- [Handleiding voor publiceren](/help/edge/docs/forms/universal-editor/publish-forms.md)

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

![&#x200B; Structuur URL &#x200B;](/help/edge/docs/forms/universal-editor/assets/url-structure.svg)
*de structuurindeling van Edge Delivery Services van URL*

#### Visuele voorbeelden

**Malplaatje van Edge Delivery Services:**

- Staged: ![&#x200B; Van de Registratie vorm gestage versie &#x200B;](/help/forms/assets/registration-form-staged-version.png)
- Levend: ![&#x200B; de vorm van de Registratie levende versie &#x200B;](/help/forms/assets/registration-form-live-version.png)

## Problemen oplossen

Hieronder vindt u algemene problemen en oplossingen voor AEM Forms met Edge Delivery Services.

+++Formulier niet laden

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

+++Problemen met de Universal Editor

**Uitgave:** kan vorm of componenten uitgeven niet ladend.

**Resolutie:**

- Gebruik een ondersteunde browser (Chrome, Firefox, Safari).
- Cache en cookies van de browser wissen.
- Controleer de netwerkconnectiviteit.
- Machtigingen van auteur bevestigen.

+++

+++Formulierverzendfouten

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
2. Herzie {de documentatie van 0} Edge Delivery Services [.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/overview.html?lang=nl-NL)
3. Bezoek [&#x200B; Gemeenschap van de Liga van de Ervaring van Adobe &#x200B;](https://experienceleaguecommunities.adobe.com/?profile.language=nl).
4. Neem contact op met de klantenservice van Adobe.

+++

## Volgende stappen

Nadat u het maken en publiceren van formulieren hebt voltooid, kunt u het volgende overwegen:

- [&#x200B; vormt voorleggen Acties &#x200B;](/help/edge/docs/forms/universal-editor/submit-action.md): De opstelling gegevens die en integratie behandelen.
- [&#x200B; Modellen van de Gegevens van de Vorm &#x200B;](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md): Verbind vormen met achterste gegevensbronnen.
- [&#x200B; Beste praktijken van Edge Delivery Services &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/overview.html?lang=nl-NL): Maximaliseer prestaties.
- [&#x200B; Analytics van de Vorm &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/analytics.html): De vormprestaties en gebruikersgedrag van het spoor.

