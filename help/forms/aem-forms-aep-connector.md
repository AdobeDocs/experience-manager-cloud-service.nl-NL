---
title: AEM Forms verbinden met Adobe Experience Platform (AEP) | Handleiding voor gegevensintegratie
description: Leer hoe u AEM Forms met Adobe Experience Platform kunt integreren om klantprofielen te benutten, formuliergegevens te verzenden en persoonlijke ervaringen te creëren. Stapsgewijze handleiding.
contentOwner: Khushwant Singh
docset: CloudService
role: Admin, Developer, User
feature: Adaptive Forms, Core Components
source-git-commit: 4144c726a6f8551df9497732c2ca95b8eec5c63a
workflow-type: tm+mt
source-wordcount: '1595'
ht-degree: 0%

---


# AEM Forms-integratie met Adobe Experience Platform (AEP) {#aem-forms-aep-integration}

<span class="preview"> De mogelijkheid om Adaptive Forms (AEM Forms) te verbinden met Adobe Experience Platform (AEP) valt onder het programma voor vroege toegang. Om toegang tot het vermogen te verzoeken, verzend eenvoudig een e-mail van uw officieel adres aan [ aem-forms-ea@adobe.com ](mailto:aem-forms-ea@adobe.com?subject=Request%20for%20Early%20Access%20to%20AEP%20Connector%20\(AEM%20Forms%20Integration%20with%20Adobe%20Experience%20Platform\)&body=Dear%20AEM%20Forms%20Team%2C%0D%0A%0D%0AI%20hope%20this%20message%20finds%20you%20well.%0D%0A%0D%0AI%20am%20writing%20to%20request%20access%20to%20the%20Early%20Access%20Program%20for%20the%20AEP%20Connector%2C%20which%20enables%20integration%20between%20AEM%20Forms%20and%20Adobe%20Experience%20Platform.%0D%0A%0D%0AOrganization%20Name%3A%20%5BYour%20organization%20name%5D%0D%0AOrganization%20ID%3A%20%5BYour%20organization%20ID%2C%20if%20available%5D%0D%0AUse%20Case%3A%20%5BBriefly%20describe%20your%20intended%20use%20case%2C%20including%20goals%20or%20benefits%20you%20aim%20to%20achieve%20with%20the%20integration%5D%0D%0A%0D%0AThank%20you%20for%20your%20time%20and%20consideration.%0D%0A%0D%0ABest%20regards%2C%0D%0A%5BYour%20Full%20Name%5D%0D%0A%5BYour%20Job%20Title%2C%20if%20applicable%5D%0D%0A%5BYour%20Contact%20Information%2C%20if%20appropriate%5D). U kunt ook de <a href="/help/forms/early-access-ea-features.md"> Vroege pagina van het Programma van de Toegang </a> bezoeken om alle beschikbare innovaties en mogelijkheden te ontdekken. . </span>

## Overzicht {#overview}

U kunt AEM Forms verbinden met Adobe Experience Platform om uw formulierervaringen te transformeren. Deze krachtige integratie laat organisaties toe om klantenprofielen in real time voor gepersonaliseerde vormervaringen te hefboomwerking, **de gegevensvoorlegging van AEM Forms aan Experience Platform** te stroomlijnen, en verenigde klantenverslagen over het ecosysteem van Adobe tot stand te brengen. Door uw adaptieve formulieren aan te sluiten met de robuuste mogelijkheden voor gegevensbeheer van Experience Platform, kunt u relevantere ervaringen creëren en de conversiesnelheden verbeteren terwijl u één bron van waarheid voor klantgegevens behoudt.

### Wat is AEM Forms Connector voor Adobe Experience Platform (AEP)? {#what-is-connector}

De AEM Forms Connector voor Adobe Experience Platform (AEP) is een out of the box (OOTB) connector die door AEM Forms wordt geleverd en naadloze integratie tussen AEM Forms en Adobe Experience Platform (AEP) mogelijk maakt. Dankzij deze integratie kunt u formulieren maken met behulp van XDM-schema&#39;s die beschikbaar zijn in AEP en gegevens terugsturen naar AEP voor personalisatie en hydratatie van profielen.

## Waarom maakt u verbinding met Adobe Experience Platform (AEP)? {#benefits}

De verbinding van uw Adaptieve Forms met Adobe Experience Platform biedt aanzienlijke voordelen voor zowel uw organisatie als uw klanten:

* **Verenigde klantenprofielen** - verrijkt klantenprofielen met de gegevens van de vormvoorlegging, die tot een uitvoerige mening van klanteninteractie en voorkeur leiden
* **Gepersonaliseerde vormervaringen** - hefboomwerking bestaande profielgegevens om gebieden vooraf in te vullen en vormen aan te passen die op bekende klanteninformatie worden gebaseerd
* **Gestroomlijnde gegevensinzameling** - vangt de vormgegevens direct in de datasets van AEP zonder de aanpasbare schakelaars of integratiecode te bouwen
* **Realtime gegevensactivering** - verzend de gegevens van de vormvoorlegging naar andere toepassingen van Adobe door Real-Time CDP voor directe activering
* **Vereenvoudigd nalevingsbeheer** - beheer toestemming en gegevensbeleid centraal door AEP
* **Verminderde ontwikkelingstijd** - Elimineer het werk van de douaneintegratie met een pre-gebouwde schakelaar die beste praktijken volgt
* **het profielverrijking van de Klant met vormgegevens** - werk automatisch klantenprofielen met elke vormvoorlegging bij en verbetert, creërend rijkere klanteninzichten

## Belangrijkste kenmerken {#key-features}

* Formulieren maken met AEP XDM-schema&#39;s
* Formuliergegevens naar AEP verzenden voor personalisatie
* Ondersteuning voor het streamen van gegevensinvoer
* Profielhydratie inschakelen voor verbeterde gebruikerservaring
* Integratie met AEP-profielsysteem
* Integratie van XDM-schema&#39;s met adaptieve formulieren voor gestandaardiseerde gegevensverzameling
* AEP-streamingverbinding voor formulieren die realtime gegevensverwerking mogelijk maken

De onderstaande video bevat een stapsgewijze handleiding over de vereisten (zoals het maken van een schema, het instellen van de gegevensconfiguratie en verificatie) en laat zien hoe u Adaptieve Forms kunt maken en verbinden met Adobe Experience Platform (AEP)

>[!VIDEO](https://video.tv.adobe.com/v/3457850/)

## Vereisten {#prerequisites}

Voordat u de AEP-connector instelt in AEM Forms, moet u controleren of het volgende in Adobe Experience Platform is voltooid:

1. Schema instellen
   * [ creeer een schema XDM ](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/tutorials/create-schema-ui)
   * [ laat schema voor het profileren ](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/tutorials/create-schema-ui#profile) toe
   * [ bepaalt identiteitsgebied ](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/tutorials/create-schema-ui#profile)

2. Gegevensconfiguratie
   * [ creeer een dataset ](https://experienceleague.adobe.com/nl/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/create-datasets)
   * [ opstelling die verbinding ](https://experienceleague.adobe.com/nl/docs/experience-platform/ingestion/tutorials/create-streaming-connection) stromen (u hebt het stromen eindpunt URL later nodig, zo maak een nota van het nu.)

3. Verificatie
   * [ produceer API geloofsbrieven ](https://experienceleague.adobe.com/nl/docs/experience-platform/landing/platform-apis/api-authentication#generate-credentials) (identiteitskaart van de Cliënt en Geheime cliënt) van Adobe Developer Console


## Implementatiestappen

### 1. AEP Cloud-configuratie maken

1. Navigeer aan uw **instantie van Adobe Experience Manager** > **Hulpmiddelen** > **de Diensten van de Wolk** > **Adobe Experience Platform**.
1. Selecteer de Container van de a **Configuratie** om de configuratie op te slaan.
1. Klik **creëren** om de configuratietovenaar van AEP te openen
1. Voer de volgende gegevens in:
   * Titel
   * Client-id (verkregen via de ontwikkelaarsconsole)
   * Clientgeheim (verkregen van ontwikkelaarsconsole)
   * OAuth URL (Er is een standaard-URL maar deze kan ook worden verkregen via de ontwikkelaarsconsole)

1. Klik **verbinden** om de verbinding te vestigen. Nadat u de verbinding tot stand hebt gebracht, configureert u de volgende aanvullende instellingen:
   * Basis-URL: platform.adobe.io (dit is een standaard-URL en kan ook worden verkregen via de ontwikkelaarsconsole. De URL&#39;s van het oauth- en platform worden standaard ingesteld op URL&#39;s van het pod-object. Als u verbinding moet maken met het werkgebied, moet u URL&#39;s van het werkgebied gebruiken.)
   * Organisatie-id (deze wordt samen met de client-id/geheim opgehaald uit de ontwikkelaarsconsole)
   * Sandboxnaam (vereist voor ontwikkelings- en productieomgevingen)

### 2. Formulier maken met XDM-schemaintegratie {#form-creation}

1. De wizard Formulier maken openen:
   * Navigeer aan uw **instantie van Adobe Experience Manager** > **Forms** > **Forms &amp; Documenten**.
   * Klik **creëren** > **AanpassingsVorm**.
1. In het **bron** lusje, selecteer een malplaatje
1. In het **lusje van Gegevens**, selecteer de **Adobe Experience Platform** optie.

1. Selecteer uw cloudconfiguratie in het deelvenster Eigenschappen. Het systeem laadt alle beschikbare schema&#39;s van Adobe Experience Platform

   >[!NOTE]
   >
   >
   > * Alleen schema&#39;s waarvoor een profiel is ingeschakeld en schema&#39;s die niet door het systeem worden gegenereerd, worden opgehaald.
   > * Het laden van het eerste schema kan enige tijd in beslag nemen bij de eerste setup.
1. Selecteer de juiste/verplichte velden van het schema. (Zie video voor gedetailleerde stappen)
1. Op het tabblad Verzending:
   * Selecteer **voorleggen aan Adobe Experience Platform** voorlegt actie
   * Vorm de montages van de vormvoorlegging voor **AEM Forms gegevensvoorlegging aan Experience Platform**
1. In het deelvenster Eigenschappen:
   * Voeg de URL voor streaming toe (verkregen via AEP-bronnen > Streaming Connection)
   * De gegevensstroom-id toevoegen (in AEP-bronnen > Stroom > API-gebruiksgegevens)
1. Klik **sparen**. Geef de formuliergegevens op:
   * Titel
   * Naam
   * Opslagpad
1. Voeg de verzendknop toe aan het formulier. Uw formulier is klaar om gegevens naar AEP te verzenden.


## Belangrijke opmerkingen {#important-notes}

* Gegevens die via formulieren worden ingediend, worden na ongeveer 10-15 minuten in AEP zichtbaar
* Standaard worden alleen schema&#39;s met profiel weergegeven
* Hoewel gegevensverzending werkt voor alle schema&#39;s, is de prefill functionaliteit beperkt tot profiel-toegelaten schema&#39;s
* De gegevens in niet-profiel-toegelaten schema&#39;s zullen niet voor profielverwezenlijking worden gebruikt, zelfs als het schema later voor het profileren wordt toegelaten
* **het profielverrijking van de Klant met vormgegevens** vereist juiste configuratie van het identiteitsgebied in uw schema XDM
* **de gegevensvoorlegging van AEM Forms aan Experience Platform** gebruikt **het stromen verbinding van AEP voor vormen** om gegevensstroom in real time te verzekeren

## Aanbevolen procedures {#best-practices}

1. Plan de schemastructuur zorgvuldig voordat u profilering inschakelt
1. Overweeg gegevensvolume en systeem het schrapen vereisten wanneer vestiging **AEP het stromen verbinding voor vormen**
1. De integratie grondig testen voordat de productie wordt geïmplementeerd
1. Bewaking van gegevensinvoer en processen voor het maken van profielen
1. Ontwerp uw **XDM schemaintegratie met adaptieve vormen** om slechts noodzakelijke gegevens te verzamelen
1. De verrijking van het klantenprofiel van het gebruik **met vormgegevens** strategisch om verpersoonlijking te verbeteren

## Technische overwegingen {#technical-considerations}

* De schakelaar gebruikt openbare het stromen APIs voor gegevensvoorlegging
* Profiel maken is gebaseerd op het identiteitsveld
* Gegevensunificatie vindt automatisch plaats in AEP
* De integratie ondersteunt zowel het maken van nieuwe formulieren als het wijzigen van bestaande formulieren
* Integratie met XDM-schema met adaptieve formulieren zorgt voor standaardisering van de gegevensstructuur voor verschillende aanraakpunten
* AEP-streamingverbinding voor formulieren biedt realtime mogelijkheden voor gegevensinvoer

## Veelgestelde vragen (FAQ) {#faq}

### Algemene vragen {#general-questions}

**Q: Kan ik deze schakelaar met om het even welke versie van AEM Forms gebruiken?**
A: Nee, deze integratie is alleen beschikbaar voor AEM Forms as a Cloud Service in het kader van het programma Vroege Toegang.

**Q: Werkt deze schakelaar met zowel de AanpassingsComponenten van de Kern van Forms als de Componenten van de Stichting?**
A: Deze connector werkt het best met Adaptive Forms Core Components, de aanbevolen aanpak voor alle nieuwe formulieren.

**Q: Kan ik gegevens naar veelvoudige datasets van AEP van één enkele vorm verzenden?**
A: Op dit moment kan elk formulier slechts naar één gegevensset verzenden. Voor veelvoudige datasetvoorlegging, zou u douanewerkschema&#39;s moeten tot stand brengen.

**Q: Is er een grens aan hoeveel vormvoorlegging kan worden verwerkt?**
A: Voor formulierverzendingen gelden de quota&#39;s voor het inslikken van formulieren en tarieflimieten van AEP.

**Q: Kunnen de vormgehechtheid worden verzonden naar AEP?**
A: Nee, formulierbijlagen kunnen niet rechtstreeks naar AEP worden verzonden. U moet bijlagen dan afzonderlijk opslaan en alleen metagegevens naar AEP verzenden.

### Implementatievragen {#implementation-questions}

**Q: Hoe los ik verbindingskwesties tussen AEM Forms en AEP problemen op?**
A: Verifieer uw montages van de wolkenconfiguratie, controleer API geloofsbrieven correct zijn, en controleer dat het stromen eindpunt URL behoorlijk wordt gevormd.

**Q: Kan ik douaneXDM schema&#39;s met deze integratie gebruiken?**
A: Ja, u kunt elk aangepast XDM-schema gebruiken zolang het correct is geconfigureerd in AEP en, voor vooraf ingevulde functionaliteit, is ingeschakeld voor profielen.

**Q: Hoe laat ik vorm toe prefilling met AEP profielgegevens?**
A: Zorg ervoor dat het schema is ingeschakeld voor profielen en dat het formulier is geconfigureerd voor gebruik van hetzelfde identiteitsveld dat in het schema is gedefinieerd.

**Q: Wat als ik gegevens moet omzetten alvorens het naar AEP te verzenden?**
A: U kunt formulierregels of aangepaste functies gebruiken om gegevens te transformeren voordat u ze verzendt. Voor complexe transformaties kunt u een aangepaste verzendactie gebruiken.

**Q: Kan ik deze integratie in een hybride plaatsingsmodel gebruiken?**
A: Nee, deze integratie is specifiek voor AEM Forms as a Cloud Service.

## Samenvatting en volgende stappen {#summary-next-steps}

Dankzij de AEM Forms-integratie met Adobe Experience Platform kunnen organisaties een naadloze gegevensstroom creëren tussen formulieren en het bredere Experience Platform-ecosysteem. Dankzij deze integratie kunt u meer persoonlijke formulierervaringen opbouwen, gegevensverzameling stroomlijnen en klantprofielen verbeteren met waardevolle gegevens voor formulierverzending.

Aan de slag met deze integratie:

1. **de toegang van het Verzoek** - als u niet reeds hebt, zich bij het Vroege programma van de Toegang aansluiten door [ aem-forms-ea@adobe.com ](mailto:aem-forms-ea@adobe.com?subject=Request%20for%20Early%20Access%20to%20AEP%20Connector%20\(AEM%20Forms%20Integration%20with%20Adobe%20Experience%20Platform\)&body=Dear%20AEM%20Forms%20Team%2C%0D%0A%0D%0AI%20hope%20this%20message%20finds%20you%20well.%0D%0A%0D%0AI%20am%20writing%20to%20request%20access%20to%20the%20Early%20Access%20Program%20for%20the%20AEP%20Connector%2C%20which%20enables%20integration%20between%20AEM%20Forms%20and%20Adobe%20Experience%20Platform.%0D%0A%0D%0AOrganization%20Name%3A%20%5BYour%20organization%20name%5D%0D%0AOrganization%20ID%3A%20%5BYour%20organization%20ID%2C%20if%20available%5D%0D%0AUse%20Case%3A%20%5BBriefly%20describe%20your%20intended%20use%20case%2C%20including%20goals%20or%20benefits%20you%20aim%20to%20achieve%20with%20the%20integration%5D%0D%0A%0D%0AThank%20you%20for%20your%20time%20and%20consideration.%0D%0A%0D%0ABest%20regards%2C%0D%0A%5BYour%20Full%20Name%5D%0D%0A%5BYour%20Job%20Title%2C%20if%20applicable%5D%0D%0A%5BYour%20Contact%20Information%2C%20if%20appropriate%5D) te contacteren
2. **bereidt uw milieu** voor - verzeker u de noodzakelijke toestemmingen en de configuraties in zowel AEM Forms als Adobe Experience Platform hebt
3. **volg de implementatiestappen** - gebruik de gids hierboven aan opstelling uw wolkenconfiguratie en creeer uw eerste AEP-Verbonden vorm met XDM schemaintegratie
4. **Test grondig** - bevestigt zowel de gegevensvoorlegging als prefill mogelijkheden in een ontwikkelomgeving
5. **Plan voor productie** - werk met uw implementatieteam om de plaatsing van de gegevens van AEM Forms te plannen die aan Experience Platform in productie worden voorgelegd

## Gerelateerde bronnen {#related-resources}

* [ de documentatie van AEM Forms as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html?lang=nl-NL)
* [ documentatie van Adobe Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/landing/home.html?lang=nl-NL)
* [ XDM overzicht van het Systeem ](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html?lang=nl-NL)
* [ Streaming opname in Adobe Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html?lang=nl-NL)
* [ overzicht van het Profiel van de Klant in real time ](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=nl-NL)
* [AEM Forms-functies voor vroege toegang](/help/forms/early-access-ea-features.md)
* [Adaptieve Forms maken met kerncomponenten](/help/forms/creating-adaptive-form-core-components.md)
* [Formuliergegevensmodellen gebruiken in AEM Forms](/help/forms/using-form-data-model.md)

<!--
Schema markup for technical documentation
{
  "@context": "https://schema.org",
  "@type": "TechArticle",
  "headline": "Connect AEM Forms with Adobe Experience Platform (AEP) | Data Integration Guide",
  "description": "Learn how to integrate AEM Forms with Adobe Experience Platform to leverage customer profiles, submit form data, and create personalized experiences.",
  "datePublished": "2025-05-28",
  "author": {
    "@type": "Corporation",
    "name": "Adobe"
  },
  "publisher": {
    "@type": "Organization",
    "name": "Adobe Experience League",
    "logo": {
      "@type": "ImageObject",
      "url": "https://experienceleague.adobe.com/assets/img/favicons/apple-touch-icon.png"
    }
  },
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/aem-forms-aep-connector.html"
  },
  "articleSection": "AEM Forms",
  "keywords": "AEM Forms, Adobe Experience Platform, XDM schema, data integration, form submission, customer profiles, personalization"
}
-->


