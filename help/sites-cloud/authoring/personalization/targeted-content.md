---
title: Authoring van getargete content met targetingmodus
description: De gerichte wijze en de component van het Doel verstrekken hulpmiddelen om inhoud voor ervaringen tot stand te brengen
translation-type: tm+mt
source-git-commit: 10aba35c0795ef946edce02e9396947fc6348514
workflow-type: tm+mt
source-wordcount: '5348'
ht-degree: 5%

---


# Authoring van getargete content met targetingmodus {#authoring-targeted-content-using-targeting-mode}

Door de auteur opgegeven inhoud met de doelmodus van AEM. De gerichte wijze en de component van het Doel verstrekken hulpmiddelen om inhoud voor ervaringen tot stand te brengen:

* Herken eenvoudig de doelinhoud op de pagina. Een stippellijn vormt een rand rondom alle doelinhoud.
* Selecteer een merk en een activiteit om de ervaringen te bekijken.
* Ervaringen toevoegen aan een activiteit of ervaringen verwijderen.
* A/B-tests uitvoeren en winnaars converteren (alleen Adobe Target).
* Voeg aanbiedingen toe aan een ervaring door aanbiedingen te maken of aanbiedingen uit een bibliotheek te gebruiken.
* Configureer doelen en controleer de prestaties.
* Simuleer de gebruikerservaring.
* Voor meer aanpassing, vorm de component van het Doel.

U kunt AEM of Adobe Target gebruiken als de doelengine (u moet over een geldige Adobe Target-account beschikken om Adobe Target te kunnen gebruiken). Als u Adobe Target gebruikt, moet u eerst de integratie configureren. Zie de instructies voor integratie met Adobe Target. <!--See the[instructions for integrating with Adobe Target](/help/sites-administering/target.md).-->

![Inhoud als doel instellen](../assets/targeted-content.png)

De activiteiten en ervaringen die u op de wijze van het Doel ziet wijzen op [Activiteitenconsole](/help/sites-cloud/authoring/personalization/activities.md):

* Wijzigingen die u aanbrengt in activiteiten en ervaringen die gebruikmaken van de modus Doel, worden weerspiegeld in de console Activiteiten.
* De veranderingen die in de console van Activiteiten worden aangebracht worden weerspiegeld in het richten wijze.

>[!NOTE]
>
>Wanneer u een campagne in Adobe Target creeert, wijst het een bezit genoemd `thirdPartyId` aan elke campagne toe. Wanneer u de campagne in Adobe Target verwijdert, wordt de thirdPartyId niet verwijderd. U kunt `thirdPartyId` voor campagnes van verschillende types (AB, XT) niet opnieuw gebruiken en het kan niet manueel worden verwijderd. Geef elke campagne een unieke naam om dit probleem te voorkomen. campagnemenamen kunnen daarom niet opnieuw worden gebruikt in verschillende soorten campagnes.
>
>Als u dezelfde naam gebruikt in hetzelfde type campagne, overschrijft u de bestaande campagne.
>
>Als tijdens het synchroniseren de fout &quot;Verzoek is mislukt. `thirdPartyId` bestaat al.&quot; Wijzig de naam van de campagne en synchroniseer opnieuw.

>[!NOTE]
>
>Wanneer het richten, blijft de branding en activiteitencombinatie op het gebruikersniveau niet op kanaalniveau voortbestaan.

## Overschakelen naar doelmodus {#switching-to-targeting-mode}

Schakel over naar de modus Doel om toegang te krijgen tot de gereedschappen voor het ontwerpen van doelinhoud.

Ga naar de modus Doel:

1. Open de pagina waarvoor u doelinhoud wilt ontwerpen.
1. Klik of tik op de werkbalk boven aan de pagina op de vervolgkeuzelijst met modi om de beschikbare modustypen weer te geven.

   ![Doelmodus](../assets/targeted-mode.png)

1. Klik of tik **gericht**. De doelopties worden boven aan de pagina weergegeven.

   ![Doelwerkbalk](../assets/targeted-toolbar.png)

## Een activiteit toevoegen met de doelmodus {#adding-an-activity-using-targeting-mode}

Gebruik de modus Doel om een activiteit aan een merk toe te voegen. Wanneer u een activiteit toevoegt, bevat het de Standaardervaring. Nadat u de activiteit hebt toegevoegd, start u het proces voor het toewijzen van inhoud voor de activiteit.

U kunt ook Adobe Target-activiteiten maken en beheren vanuit AEM met de optie om de doelengine (AEM of Adobe Target) te selecteren en het type activiteit (Experience Targeting of A/B Test) te selecteren.

Bovendien kunt u doelstellingen en maatstaven voor alle Adobe Target-activiteiten beheren en uw Adobe Target-publiek beheren. Er wordt ook melding gemaakt van Adobe Target-activiteiten, waaronder het converteren van winnaars voor A/B-tests.

Wanneer u een activiteit toevoegt, verschijnt het ook in [Activiteitenconsole](/help/sites-cloud/authoring/personalization/activities.md).

Een activiteit toevoegen:

1. Gebruik het vervolgkeuzemenu **Merk** om het merk te selecteren waarvoor u de activiteit wilt maken.

   >[!NOTE]
   >
   >Het wordt geadviseerd om [merken door de activiteitenconsole te creëren](/help/sites-cloud/authoring/personalization/activities.md#creating-a-brand-using-the-activities-console).
   >
   >
   >Als u een merk op een andere manier creeert, zorg ervoor dat de knoop `/campaigns/<brand>/master` bestaat of een fout zal resulteren wanneer u probeert om een activiteit tot stand te brengen.

1. Klik of tik + naast **Activiteit** drop-down menu.
1. Typ een naam voor de activiteit.

   >[!NOTE]
   >
   >Wanneer u een nieuwe activiteit creeert en een de wolkenconfiguratie van Adobe Target verbonden aan de pagina of één van zijn ouder hebt, AEM automatisch Adobe Target als motor veronderstelt.

1. Selecteer in het vervolgkeuzemenu **Doelengine** de doelengine.

   * Als u **ContextHub AEM** selecteert, worden de resterende gebieden gedimd en niet beschikbaar. Klik of tik **Create**.

   * Als u **Adobe Target** selecteert, kunt u een configuratie (door gebrek selecteren, is het de configuratie u verstrekte toen u de rekening) vormde en Type van Activiteit. <!--If you select **Adobe Target**, you can select a configuration (by default, it is the configuration you provided when you [configured the account](/help/sites-administering/opt-in.md)) and Activity Type.-->

1. Selecteer **Experience Targeting** of **A/B Test** in het menu Activiteit.

   * De ervaring richt zich - beheert de activiteiten van Adobe Target van AEM.
   * A/B-test - A/B-testactiviteiten in Adobe Target maken/beheren vanuit AEM.

## Het doelproces: {#the-targeting-process-create-target-and-goals-settings} maken, Doel en Doelen &amp; instellingen

De gerichte wijze laat u toe om verscheidene aspecten van een activiteit te vormen. Gebruik het volgende proces in drie stappen voor het maken van gerichte inhoud voor een merkactiviteit:

1. [Maken](#create-authoring-the-experiences): Voeg ervaringen toe of verwijder ervaringen en voeg aanbiedingen toe voor elke ervaring.
1. [Doel](#target-configuring-the-audiences): Geef het publiek op dat elke ervaring als doel heeft. U kunt een specifiek publiek richten en als het gebruiken van het testen A/B beslist welk percentage van verkeer naar welke ervaring gaat.
1. [Doelstellingen en instellingen](#goals-settings-configuring-the-activity-and-setting-goals): Plan de activiteit en stel de prioriteit in. U kunt succes metrische doelstellingen ook plaatsen.

Gebruik de volgende procedure om het doelproces voor inhoud voor een activiteit te starten.

>[!NOTE]
>
>Om het het richten proces te gebruiken, moet u een lid van de de gebruikersgroep van de Auteurs van de Activiteit van het Doel zijn.

Een activiteit toevoegen:

1. Selecteer in het vervolgkeuzemenu **Merk** het merk dat de activiteit bevat waaraan u werkt.
1. Selecteer in het vervolgkeuzemenu **Activiteit** de activiteit waarvoor u doelinhoud ontwerpt.
1. Als u de besturingselementen wilt weergeven die u door het doelproces begeleiden, klikt of tikt u op **Doelgericht starten**.

   ![Doelstelling starten](../assets/targeted-start-targeting.png)

   >[!NOTE]
   >
   >Als u de activiteit wilt wijzigen waarmee u werkt, klikt of tikt u op **Terug**.

## Maken: Ontwerpen van de Ervaringen {#create-authoring-the-experiences}

Bij het maken van inhoud als doel gaat het om het maken van ervaringen. Tijdens deze stap kunt u de ervaringen van de activiteit creëren of schrappen, en aanbiedingen toevoegen aan elke ervaring.

### Aanbiedingen voor zichtbare ervaring in doelmodus {#seeing-experience-offers-in-targeting-mode}

Nadat u [het richten proces ](#the-targeting-process-create-target-and-goals-settings) begint, selecteer een ervaring om de aanbiedingen te zien die voor die ervaring worden verstrekt. Wanneer u een ervaring selecteert, veranderen de doelcomponenten op de pagina om de aanbieding voor die ervaring te tonen.

>[!CAUTION]
>
>Wees voorzichtig wanneer u het richten voor een component onbruikbaar maakt die reeds in de auteursinstantie gericht is. De respectievelijke activiteit wordt automatisch ook uit het publicatieexemplaar verwijderd.

>[!NOTE]
>
>Een aanbieding is de inhoud van een doelcomponent.

De ervaringen worden weergegeven in het deelvenster Doelgroep. In het volgende voorbeeld zijn de ervaringen **Standaard**, **Vrouwelijk**, **Vrouwelijk ouder dan 30** en **Vrouwelijk jonger dan 30**. In dit voorbeeld wordt het standaardaanbod van een beoogde **afbeeldingscomponent** getoond.

![Doelafbeeldingscomponent](../assets/targeted-image-component.png)

Wanneer u een andere ervaring hebt geselecteerd, wordt in de component Image het aanbod voor die ervaring weergegeven.

![Doelafbeeldingscomponent gewijzigd](../assets/targeted-image-different.png)

Wanneer een ervaring wordt geselecteerd en de doelcomponent geen aanbieding voor die ervaring omvat, toont de component **Aanbieding toevoegen** bovenop de semitransparante standaardaanbieding. Wanneer geen aanbieding voor een ervaring is gecreëerd, wordt de **Standaardaanbieding** getoond voor het segment dat aan de ervaring is toegewezen.

![Voorstel toevoegen](../assets/targeted-add-offer.png)

De ervaring Standaard wordt ook weergegeven wanneer de eigenschappen van de bezoeker niet overeenkomen met segmenten die aan de ervaringen zijn toegewezen. Zie [Ervaringen toevoegen met de doelmodus](#adding-and-removing-experiences-using-targeting-mode).

### Aangepaste aanbiedingen en bibliotheekaanbiedingen {#custom-offers-and-library-offers}

Aanbiedingen die [op pagina](#adding-a-custom-offer) worden ontworpen en voor één enkele ervaring worden gebruikt worden genoemd douaneaanbiedingen. De volgende afbeelding wordt over de inhoud van een aangepaste aanbieding heen geplaatst:

![Aangepast aanbiedingspictogram](../assets/targeted-custom-offer-icon.png)

Aanbiedingen die worden [toegevoegd uit een aanbiedingsbibliotheek](#adding-an-offer-from-an-offer-library), worden overschreven door de volgende afbeelding:

![Bibliotheekpictogram](../assets/targeted-library-offer-icon.png)

U kunt aangepaste voorstellen opslaan in een aanbiedingsbibliotheek als u besluit dat u deze opnieuw wilt gebruiken. U kunt een bibliotheekaanbieding in een douaneaanbieding ook omzetten als u de inhoud voor een ervaring wilt wijzigen. Na het bewerken kunt u de aanbieding opnieuw opslaan in de bibliotheek.

### Ervaringen toevoegen en verwijderen met de doelmodus {#adding-and-removing-experiences-using-targeting-mode}

Met de stap Maken van [het het richten proces](#the-targeting-process-create-target-and-goals-settings), kunt u ervaringen toevoegen en verwijderen. Bovendien kunt u een ervaring dupliceren en ook de naam ervan wijzigen.

#### Ervaringen toevoegen met de doelmodus {#adding-experiences-using-targeting-mode}

Een ervaring toevoegen:

1. Als u een ervaring wilt toevoegen, klikt of tikt u op **+** **Beleving toevoegen die is gericht** en die onder bestaande ervaringen in het **deelvenster Soorten publiek** wordt weergegeven.
1. Selecteer en publiek. Standaard is die naam de naam van de ervaring. U kunt desgewenst een andere naam typen. Klik of tik **OK**.

#### Ervaringen verwijderen met de doelmodus {#removing-experiences-using-targeting-mode}

Een ervaring verwijderen:

1. Klik of tik op de pijl naast de ervaringsnaam.

   ![Verwijderen en ervaren](../assets/targeted-delete-experiene.png)

1. Klik **Delete**.

#### Ervaringen hernoemen met doelmodus {#renaming-experiences-using-targeting-mode}

Ervaringen een andere naam geven in de doelmodus:

1. Klik of tik op de pijl naast de ervaringsnaam.
1. Klik **Naam van ervaring wijzigen** en typ de nieuwe naam.
1. Klik of tik ergens anders op het scherm om de wijzigingen op te slaan.

#### Soorten publiek bewerken met doelmodus {#editing-audiences-using-targeting-mode}

Het publiek bewerken in de modus Doel:

1. Klik of tik op de pijl naast de ervaringsnaam.
1. Klik **Soorten publiek bewerken** en selecteer een nieuw publiek.
1. Klik **OK**.

#### Dubbele ervaringen met doelmodus {#duplicating-experiences-using-targeting-mode}

Ervaringen kopiëren met de doelmodus:

1. Klik of tik op de pijl naast de ervaringsnaam.
1. Klik **Dupliceer** en kies het publiek.
1. Wijzig desgewenst de naam van de ervaring en klik op **OK**.

### Aanbiedingen maken met de doelmodus {#creating-offers-using-targeting-mode}

Kies een component om aanbiedingen voor ervaringen te maken. De gerichte componenten verstrekken de inhoud die als aanbiedingen voor ervaringen wordt gebruikt.

* [Doel een bestaande component](#creating-a-default-offer-by-targeting-an-existing-component). De inhoud wordt de standaardervaring.
* [Voeg een doelcomponent](#creating-an-offer-by-adding-a-target-component) toe en voeg vervolgens inhoud toe aan de component.

Nadat een component is aangewezen, kunt u aanbiedingen voor elke ervaring toevoegen:

* [Voeg aangepaste aanbiedingen](#adding-a-custom-offer) toe.
* [Voeg voorstellen van een bibliotheek](#adding-an-offer-from-an-offer-library) toe.

De volgende gereedschappen zijn beschikbaar voor het werken met aanbiedingen:

* [Voeg een aangepaste aanbieding toe aan een aanbiedingsbibliotheek](#adding-a-custom-offer-to-a-library).
* [Een bibliotheekaanbieding omzetten in een aangepaste aanbieding](#converting-a-library-offer-to-a-custom-library).
* [Open een bibliotheekaanbieding en bewerk de inhoud](#editing-a-library-offer).

#### Een standaardaanbieding maken door een bestaande component {#creating-a-default-offer-by-targeting-an-existing-component} te activeren

Wijs een component op de pagina aan om het als aanbieding voor de Standaardervaring van de activiteit te gebruiken. Wanneer u een component als doel instelt, wordt deze in een doelcomponent verpakt en wordt de inhoud van deze component de aanbieding voor de standaardervaring.

Wanneer u een component als doel instelt, kan alleen die component in de aanbieding worden gebruikt. U kunt de component niet uit de aanbieding verwijderen of andere componenten aan de aanbieding toevoegen.

Voer de volgende procedure uit nadat [het het richten proces](#the-targeting-process-create-target-and-goals-settings) begint.

1. Klik op de component of tik op de component om deze als doel in te stellen. De werkbalk voor de component wordt weergegeven, net als in het volgende voorbeeld.

   ![Doelcomponent](../assets/targeted-component.png)

1. Klik of tik op het pictogram Doel.

   ![Doelknop](../assets/targeted-target-button.png)

   De inhoud van de component is de aanbieding voor de Standaardervaring. Wanneer een component wordt gericht, zal zijn standaardknoop voor elke ervaring worden herhaald. Dit is nodig voor het bewerken van het juiste inhoudsknooppunt tijdens specifieke ontwerphandelingen. Voor deze niet-standaard ervaringen, of [voeg een douaneaanbieding ](#adding-a-custom-offer) of [voeg een bibliotheekaanbieding](#adding-an-offer-from-an-offer-library) toe.

#### Een aanbieding maken door een doelcomponent {#creating-an-offer-by-adding-a-target-component} toe te voegen

Voeg een component van het Doel toe om de aanbieding voor de Standaardervaring tot stand te brengen. De doelcomponent is een container voor andere componenten en componenten die erin worden geplaatst, worden als doel ingesteld. Wanneer u de component van het Doel gebruikt, kunt u verscheidene componenten toevoegen om een aanbieding tot stand te brengen. Bovendien kunt u verschillende componenten in elke ervaring gebruiken om verschillende aanbiedingen te maken.

Zie [Opties voor doelcomponenten configureren](#configuring-target-component-options) voor informatie over het aanpassen van deze component.

>[!NOTE]
>
>Aanbiedingen die u met de [console van Aanbiedingen](/help/sites-cloud/authoring/personalization/offers.md) creeert kunnen verscheidene componenten ook bevatten. Deze aanbiedingen horen bij een aanbiedingsbibliotheek en kunnen voor meerdere ervaringen worden gebruikt.

Aangezien de doelcomponent een container is, wordt deze weergegeven als een neerzetgebied voor andere componenten.

In de modus Doel heeft de component Doel een blauwe rand en geeft het bericht voor de neerzetbestemming de doelaard aan.

![Doeldropzone](../assets/targeted-drop-target.png)

In de modus Bewerken heeft de component Doel een pictogram met een opsommingsteken.

![Pictogram van doeldropzone](../assets/targeted-drop-target-icon.png)

Wanneer u componenten naar de component van het Doel sleept, zijn zij gerichte componenten.

![Slagzone met doelen](../assets/targeted-drop-zone-populated.png)

Wanneer u een component aan de component van het Doel toevoegt, verstrekt het inhoud voor een specifieke ervaring. Als u de ervaring wilt opgeven, selecteert u de ervaring voordat u de componenten toevoegt.

U kunt een doelcomponent aan de pagina toevoegen in de modus Bewerken of in de modus Doel. U kunt componenten alleen in de modus Doel aan de component Doel toevoegen. De component van het Doel behoort tot de de componentengroep van de Personalisatie.

Als u de doelinhoud wilt bewerken, moet u **Doel starten** klikken of tikken voordat u dit kunt doen.

1. Sleep de component Target naar de pagina waar u het aanbod wilt weergeven.
1. Standaard is er geen locatie-id ingesteld. Klik of tik de Configure cog wiel om de plaats te plaatsen.

   >[!NOTE]
   >
   >Indien ingesteld door uw beheerder, moet u de locatie mogelijk expliciet instellen.
   >
   >Beheerders kunnen bepalen of deze configuratie vereist is op `https://<host>:<port>/system/console/configMgr/com.day.cq.personalization.impl.servlets.TargetingConfigurationServlet`
   >
   >Als u wilt dat gebruikers een locatie moeten invoeren, schakelt u het selectievakje **Locatie forceren** in.

1. Selecteer de ervaring waarvoor u de aanbieding wilt maken.
1. Maak het voorstel:

   * Voor de Standaardervaring, sleep componenten aan het gerichte dalingsgebied, en geef de componenteneigenschappen zoals gebruikelijk uit om de inhoud voor de aanbieding tot stand te brengen.
   * Voor niet-standaard ervaringen, of [voeg een douaneaanbieding ](#adding-a-custom-offer) of [voeg een bibliotheekaanbieding](#adding-an-offer-from-an-offer-library) toe.

#### Een aangepaste aanbieding {#adding-a-custom-offer} toevoegen

Maak een aanbieding door de inhoud van een doelcomponent te ontwerpen in de modus Doel. Wanneer u een aangepaste aanbieding maakt, wordt deze gebruikt als de aanbieding voor één ervaring.

Als u besluit dat de aanbieding voor andere ervaringen kan worden gebruikt, kunt u een douaneaanbieding tot stand brengen en [toevoegen het aan bibliotheek](#adding-a-custom-offer-to-a-library). Voor informatie over het gebruiken van de console van Aanbiedingen om een herbruikbare aanbieding tot stand te brengen, zie [een Aanbieding aan een Bibliotheek van de Aanbieding toevoegen](/help/sites-cloud/authoring/personalization/offers.md#add-an-offer-to-an-offer-library).

1. Selecteer de ervaring waaraan u het voorstel wilt toevoegen.
1. Als u het deelvenstermenu wilt weergeven, klikt of tikt u op de doelcomponent waaraan u de aanbieding wilt toevoegen.

   ![Een voorstel toevoegen](../assets/targeted-component-menu.png)

1. Klik op of tik op het +-pictogram.

   De inhoud van de standaardaanbieding wordt gebruikt als de aanbieding voor de huidige ervaring.

1. Klik of tik op de aanbieding om het aanbiedingsmenu weer te geven en klik op het bewerkingspictogram.

   ![Werkbalk Doelcomponent](../assets/targeted-offer-menu.png)

1. Bewerk de inhoud van de component.

#### Een voorstel toevoegen vanuit een aanbiedingsbibliotheek {#adding-an-offer-from-an-offer-library}

Voeg een aanbieding van [aanbiedingsbibliotheek](/help/sites-cloud/authoring/personalization/offers.md) aan een ervaring toe. U kunt elke aanbieding toevoegen uit de bibliotheek van het merk waarvoor u momenteel kiest.

U kunt geen bibliotheekaanbiedingen toevoegen aan de standaardervaring.

1. Selecteer de ervaring waaraan u het voorstel wilt toevoegen.
1. Als u het deelvenstermenu wilt weergeven, klikt of tikt u op de doelcomponent waaraan u de aanbieding wilt toevoegen.

   ![Gericht aanbod](../assets/targeted-add-offer-large.png)

1. Klik of tik op het mappictogram.

   ![Mappictogram](../assets/targeted-folder-button.png)

1. Selecteer de aanbieding in de bibliotheek en klik of tik op het pictogram van het vinkje.

   ![Bibliotheek van aanbieding](../assets/targeted-select-content.png)

   Met de aanbiedingenkiezer kunt u naar voorstellen bladeren of filteren. Wanneer u bladert of filtert, kunt u de aanbiedingen ook willen sorteren en veranderen hoe u hen bekijkt. Het getal in de rechterbovenhoek geeft aan hoeveel aanbiedingen beschikbaar zijn in de huidige bibliotheek.

   * Klik of tik **Bladeren** om naar een andere map te navigeren. Het navigatievenster wordt geopend en u klikt op de pijl om naar de mappen te gaan. Klik of tik **Bladeren** opnieuw om het navigatiegebied te sluiten.

   ![Bladeren door inhoud](../assets/targeted-select-content-browse.png)

   * Klik of tik **Filter** om de aanbiedingen tegen sleutelwoorden of markeringen te filtreren. U voert trefwoorden in en u selecteert tags in het keuzemenu. Klik of tik **Filter** opnieuw om de het filtreren ruit te sluiten.

   ![Inhoud filteren](../assets/targeted-filter.png)

   * Wijzig de sortering van de aanbiedingen door op de pijl naast **Nieuwst naar Oudst** te klikken of erop te tikken. Aanbiedingen kunnen nieuwste worden gesorteerd op oudst of oudst op nieuwste.

   ![Sorteervolgorde filteren](../assets/targeted-filter-sort.png)

   Klik of tik het pictogram naast **Weergeven als** om aanbiedingen als tegels of als lijst weer te geven.

   ![Weergeven als knop](../assets/targeted-view-as-button.png)

#### Een aangepaste aanbieding toevoegen aan een bibliotheek {#adding-a-custom-offer-to-a-library}

Voeg een douaneaanbieding aan [aanbiedingsbibliotheek](/help/sites-cloud/authoring/personalization/offers.md) toe wanneer u het als aanbieding voor veelvoudige ervaringen wilt hergebruiken. U kunt aanbiedingen toevoegen aan de bibliotheek van het huidige merk waarop u zich richt.

Voor informatie over het gebruiken van de console van Aanbiedingen om een herbruikbare aanbieding tot stand te brengen, zie [een Aanbieding aan een Bibliotheek van de Aanbieding toevoegen](/help/sites-cloud/authoring/personalization/offers.md#add-an-offer-to-an-offer-library).

1. Selecteer de ervaring om de aangepaste aanbieding weer te geven.
1. Klik of tik op de aangepaste aanbieding om het aanbiedingsmenu weer te geven en klik op het pictogram **Aanbieding opslaan in bibliotheek**.

   ![Aanbieding opslaan om bibliotheek aan te bieden](../assets/targeted-save-offer-library-button.png)

1. Typ een naam voor de aanbieding, selecteer de bibliotheek waaraan u de aanbieding toevoegt, dan klik of tik het controlemerkpictogram.

#### Een bibliotheekaanbod omzetten in een aangepaste bibliotheek {#converting-a-library-offer-to-a-custom-library}

Een bibliotheekaanbieding omzetten in een aangepaste aanbieding om de aanbieding voor de huidige ervaring te wijzigen zonder de aanbieding in andere ervaringen te wijzigen.

1. Selecteer de ervaring om het bibliotheekaanbod weer te geven.
1. Klik of tik op de bibliotheekaanbieding om het aanbiedingsmenu weer te geven en klik vervolgens op het pictogram Omzetten in inline-aanbieding of tik op dit pictogram.

   ![Omzetten in inline aanbieding](../assets/targeted-convert-inline.png)

#### Een bibliotheekaanbieding {#editing-a-library-offer} bewerken

Open een bibliotheekaanbieding vanuit een ervaring in de modus Gericht om de aanbieding te bewerken. De wijzigingen die u aanbrengt, worden weergegeven in alle ervaringen die gebruikmaken van de aanbieding.

1. Selecteer de ervaring om het bibliotheekaanbod weer te geven.
1. De bibliotheekaanbieding omzetten in een lokale/aangepaste aanbieding. Zie [Een bibliotheekaanbod omzetten in een aangepaste bibliotheek](#converting-a-library-offer-to-a-custom-library).
1. Bewerk de inhoud van de aanbieding.

1. Sla het bestand weer op in de bibliotheek. Zie [Een aangepaste aanbieding toevoegen aan een bibliotheek](#adding-a-custom-offer-to-a-library).

## Doel: Het vormen van het publiek {#target-configuring-the-audiences}

De stap van het Doel van [het richten proces](#the-targeting-process-create-target-and-goals-settings) impliceert het in kaart brengen van publiek met de ervaringen die u met in Create stap werkte. De pagina Doel toont het publiek dat elke ervaring richt. U kunt het publiek voor elke ervaring opgeven of wijzigen. Als u Adobe Target gebruikt, kunt u A/B tests ook tot stand brengen die u toestaan om percentage van verkeer voor een publiek aan een bepaalde ervaring te richten.

### Als u AEM of Adobe Target gebruikt (ervaring richt zich) {#if-you-are-using-aem-targeting-or-adobe-target-experience-targeting}

Het publiek verschijnt aan de linkerkant van het kaartdiagram, en de ervaringen verschijnen aan de rechterkant.

![Toewijzingspubliek](../assets/targeted-diagram.png)

Definieer een publiek met een segment. De wolkenconfiguratie voor de pagina bepaalt de segmenten die aan u beschikbaar zijn. Wanneer de pagina niet is gekoppeld aan een Adobe Target-cloudconfiguratie, zijn AEM segmenten beschikbaar voor het definiëren van soorten publiek. Wanneer de pagina aan een de wolkenconfiguratie van Adobe Target wordt geassocieerd, gebruikt u de segmenten van het Doel.

Zie [Richtende motor](/help/sites-cloud/authoring/personalization/overview.md#targeting-engine) voor informatie over motoren.

Een publiek mag niet door meer dan één ervaring worden gebruikt. Er verschijnt een waarschuwingssymbool naast een ervaring wanneer het wordt toegewezen aan een publiek dat is toegewezen aan een andere ervaring.

![Waarschuwingspictogram](../assets/targeted-warn.png)

### Ervaringen koppelen aan publiek (AEM of Adobe Target) {#associating-experiences-with-audiences-aem-or-adobe-target}

Gebruik de volgende procedure om een ervaring met een publiek te associëren wanneer het gebruiken van AEM richten (of de ervaring van Adobe Target het richten):

1. Klik of tik de drop-down pijl naast in de publieksdoos die aan de ervaring wordt toegewezen.
1. (Optioneel) Klik of tik op **Bewerken** en typ een trefwoord om naar het gewenste segment te zoeken.
1. Selecteer het publiek in de lijst met soorten publiek en klik of tik op **OK**.

### Als u A/B Testing (Adobe Target) {#if-you-are-using-a-b-testing-adobe-target} gebruikt

Als u een A/B testactiviteit hebt, zijn de soorten publiek op uw linkerzijde, is het percentage dat elke ervaring wordt bekeken in het midden, en de ervaringen zijn op het recht.

U kunt de percentages wijzigen zolang ze maar optellen tot 100 procent. Een publiek kan door veelvoudige ervaringen in het testen A/B worden gebruikt.

![Doelstelling A/B](../assets/targeted-ab.png)

### Soorten publiek en verkeerspercentages koppelen aan A/B-tests {#associating-audiences-and-traffic-percentages-with-a-b-testing}

1. Klik of tik de drop-down doos naast het publiek dat aan de ervaring in kaart wordt gebracht.
1. (Optioneel) Klik op **Bewerken** en typ een trefwoord om naar het gewenste segment te zoeken.
1. Klik of tik **OK.**
1. Ga in percentages in om te vormen hoe het publieksverkeer aan elke ervaringen wordt verpletterd. Het totale getal moet 100 zijn.
1. (Optioneel) Bewerk de ervaringsnaam door te klikken op het keuzemenu naast de naam van de ervaring.

## Doelstellingen en instellingen: Het vormen van de Doelstellingen van de Activiteit en van het Plaatsen {#goals-settings-configuring-the-activity-and-setting-goals}

Bij de stap Doelstellingen en instellingen van [het doelproces](#the-targeting-process-create-target-and-goals-settings) wordt het gedrag van de merkactiviteit geconfigureerd. Geef op wanneer de activiteit begint en eindigt en geef ook de prioriteit van de activiteit op. Bovendien volgt u ook doelstellingen. Specifiek kunt u beslissen wat u met uw activiteiten wilt meten.

Goal Metrics zijn alleen beschikbaar als je Adobe Target gebruikt voor je doelengine. U moet minstens één doel metrisch bepalen. Als u Adobe Analytics hebt geconfigureerd en een cloudconfiguratie voor A4T Analytics hebt, kunt u kiezen of u de rapportbron Adobe Target of Adobe Analytics wilt zijn.

De doelmeetgegevens worden alleen gemeten voor de gepubliceerde campagne.

Indien AEM wordt gebruikt als motor die als doel heeft:

![AEM als doelmotor](../assets/targeted-goals.png)

Indien Adobe Target wordt gebruikt als de motor waarop is gericht:

![Adobe Target als doelmotor](../assets/targeted-engine.png)

Als u Adobe Target gebruikt als de doelengine en u A4T Analytics hebt geconfigureerd voor het account, hebt u een extra vervolgkeuzemenu voor **Bron van rapportage**:

![A4T](../assets/targeted-source.png)

De volgende succeswaarden zijn beschikbaar (alleen gebruikt voor publiceren):

| Metrisch | Beschrijving | Opties |
|---|---|---|
| Conversie | Het percentage bezoekers dat heeft geklikt op een onderdeel van de ervaring die wordt getest. Een conversie kan één keer per bezoeker worden geteld of telkens wanneer een bezoeker een conversie voltooit. De omzettingsnorm wordt geplaatst aan één van het volgende: | Een pagina weergegeven - U kunt definiëren welke pagina de doelgroep heeft weergegeven door een URL te selecteren en vervolgens de URL of meerdere URL&#39;s te definiëren, of door een URL te selecteren en vervolgens een pad of trefwoord toe te voegen. Een box weergegeven - U kunt opgeven welke box uw publiek heeft weergegeven door de naam van de mbox in te voeren. U kunt veelvoudige dozen ingaan door Add een Mbox te klikken. |
| Ontvangsten | Door het bezoek gegenereerde inkomsten. U kunt uit de vermelde omzetcijfers kiezen. Voor al deze opties geeft het feit of een box is weergegeven aan dat het doel is bereikt. U kunt de box of meerdere vakken definiëren. | Ontvangsten per bezoeker (RPV), gemiddelde bestelwaarde (AOV), totale verkoop, bestellingen |
| Betrokkenheid | U kunt drie soorten betrokkenheid meten | Paginaweergaven, Aangepaste score, Tijd op site |

Bovendien zijn er geavanceerde montages die u laten bepalen hoe te om succesmetriek te tellen. U kunt onder andere de metrische waarde per impositie of één keer per bezoeker tellen en kiezen of de gebruiker in de activiteit moet blijven of de activiteit moet verwijderen.

Gebruik de geavanceerde montages om te bepalen wat **after** een gebruiker het doel metrisch ontmoet. In de volgende tabel staan de beschikbare opties.

| Nadat een gebruiker dit doel metrisch ontmoet.. | U selecteert het volgende om te gebeuren... |
|---|---|
| Aantal verhogen en Gebruiker in activiteit houden | Geef op hoe het aantal wordt verhoogd: Eenmaal per gegadigde, Op elke indruk, zonder pagina-vernieuwingen, Op elke indruk |
| Aantal stappen, Gebruiker vrijgeven en Opnieuw invoeren toestaan | Selecteer de ervaring die de bezoeker ziet als ze de activiteit opnieuw betreden: Zelfde ervaring, Willekeurige ervaring, Onzichtbare ervaring |
| Aantal verhogende, Gebruiker van de Versie en de Heringang van de Bar | Bepaal wat de gebruiker ziet in plaats van de inhoud van de activiteit: Dezelfde ervaring, zonder reeksspatiëring, standaardinhoud of andere activiteit-inhoud |

Zie [Adobe Target documentation](https://docs.adobe.com/content/help/en/target/using/activities/success-metrics/success-metrics.html) voor meer informatie over succesmetriek.

### Instellingen configureren (AEM gericht) {#configuring-settings-aem-targeting}

Om montages te vormen wanneer het gebruiken van AEM richten:

1. Als u wilt opgeven wanneer de activiteit begint, gebruikt u het vervolgkeuzemenu **Start** om een van de volgende waarden te selecteren:

   * **Indien geactiveerd**: De activiteit begint wanneer de pagina die de beoogde inhoud bevat, wordt geactiveerd.
   * **Opgegeven datum en tijd**: Een specifieke tijd. Wanneer u deze optie selecteert, klikt of tikt u op het kalenderpictogram, selecteert u een datum en geeft u de tijd op waarop de activiteit wordt gestart.

1. Als u wilt opgeven wanneer de activiteit eindigt, gebruikt u het vervolgkeuzemenu **End** om een van de volgende waarden te selecteren:

   * **Wanneer gedeactiveerd**: De activiteit eindigt wanneer de pagina die de beoogde inhoud bevat, wordt gedeactiveerd.
   * **Opgegeven datum en tijd**: Een specifieke tijd. Wanneer u deze optie selecteert, klikt of tikt u op het kalenderpictogram, selecteert u een datum en geeft u de tijd op om de activiteit te beëindigen.

1. Als u een prioriteit voor de activiteit wilt opgeven, gebruikt u de schuifregelaar om **Laag**, **Normaal** of **Hoog** te selecteren.

### Doelstellingen en instellingen configureren (Adobe Target) {#configuring-goals-settings-adobe-target}

Als u Adobe Target gebruikt, kunt u als volgt doelen en instellingen configureren:

1. Als u wilt opgeven wanneer de activiteit begint, gebruikt u het vervolgkeuzemenu **Start** om een van de volgende waarden te selecteren:

   * **Indien geactiveerd**: De activiteit begint wanneer de pagina die de beoogde inhoud bevat, wordt geactiveerd.
   * **Opgegeven datum en tijd**: Een specifieke tijd. Wanneer u deze optie selecteert, klikt of tikt u op het kalenderpictogram, selecteert u een datum en geeft u de tijd op waarop de activiteit wordt gestart.

1. Als u wilt opgeven wanneer de activiteit eindigt, gebruikt u het vervolgkeuzemenu **End** om een van de volgende waarden te selecteren:

   * **Wanneer gedeactiveerd**: De activiteit eindigt wanneer de pagina die de beoogde inhoud bevat, wordt gedeactiveerd.
   * **Opgegeven datum en tijd**: Een specifieke tijd. Wanneer u deze optie selecteert, klikt of tikt u op het kalenderpictogram, selecteert u een datum en geeft u de tijd op om de activiteit te beëindigen.

1. Als u een prioriteit voor de activiteit wilt opgeven, gebruikt u de schuifregelaar om **Laag**, **Normaal** of **Hoog** te selecteren.
1. Als u Adobe Analytics hebt geconfigureerd voor uw Adobe Target-account, wordt het vervolgkeuzemenu **Bron van rapportage** weergegeven. Selecteer **Adobe Target** of **Adobe Analytics** als bron.

   Als u **Adobe Analytics** selecteert, selecteert het bedrijf en rapportreeks. Als u **Adobe Target** selecteert, is geen actie vereist.

   ![Rapportbron](../assets/targeted-reporting-source.png)

1. In het gebied **Metrische data van doel** selecteert u onder **Mijn primaire doel** de metrische data voor succes die u wilt volgen (Omzetting, Inkomsten, Betrokkenheid) en geeft u op hoe deze metrische waarde wordt gemeten (of welke actie de doelgroep uitvoert om aan te geven dat een doel bereikt is). Zie de definitie van de metrische data van doel in de vorige tabel en zie de [Adobe Target-documentatie](https://docs.adobe.com/content/help/en/target/using/activities/success-metrics/success-metrics.html) over metrische data voor succes.

   U kunt de naam van het doel wijzigen door op de drie stippen in de rechterbovenhoek te klikken en **Naam wijzigen** te selecteren.

   Als u alle velden wilt wissen, klikt u op de drie stippen in de rechterbovenhoek en selecteert u **Alle velden wissen**.

   Alle metriek hebben ook geavanceerde montages u kunt bepalen. Selecteer **Geavanceerde instellingen** om deze te openen. Zie definitie van hoe succesmetriek in vorige lijst worden geteld en [Adobe Target documentatie](https://docs.adobe.com/content/help/en/target/using/activities/success-metrics/success-metrics.html) zien.

   >[!NOTE]
   >
   >Er moet ten minste één doel zijn gedefinieerd.

   ![Metrisch doel](../assets/targeted-goal-metric.png)

   >[!NOTE]
   >
   >Als er informatie ontbreekt in metrisch, omringt een rode lijn metrisch.

1. Klik **Voeg een Nieuwe Metrisch** toe om extra succesmetriek te vormen.

   ![Aanvullende meetwaarden](../assets/targeted-additional-metrics.png)

   >[!NOTE]
   >
   >U kunt extra doelstellingen verwijderen door de drie punten te klikken of te tikken en **Delete** te klikken of te tikken. AEM vereist dat u minstens één doel hebt gedefinieerd.

1. Als u meer controle wilt hebben over de manier waarop succesmetingen worden geteld, klikt of tikt u op **Geavanceerde instellingen** om deze instellingen te openen.
1. Klik **Opslaan**.

Na het vormen, kunt u [de prestaties van uw activiteiten bekijken](/help/sites-cloud/authoring/personalization/activities.md#viewing-performance-and-converting-winning-experiences-a-b-test) die Adobe Target (of ervaring of A/B test het richten) gebruiken. Bovendien kunt u met A/B test het richten, de winnaars [omzetten.](/help/sites-cloud/authoring/personalization/activities.md#viewing-performance-and-converting-winning-experiences-a-b-test)

## Een ervaring simuleren {#simulating-an-experience}

Simuleer de ervaring van een bezoeker om te controleren of de pagina-inhoud op de verwachte wijze wordt weergegeven, afhankelijk van het ontwerp van uw doelinhoud. Tijdens het simuleren kunt u verschillende gebruikersprofielen laden en de doelinhoud voor die gebruiker bekijken.

De volgende criteria bepalen de inhoud die wordt weergegeven wanneer bezoekerservaring wordt gesimuleerd:

* De gegevens in de zittingsopslag van de gebruiker (via de Hub van de Context).
* De [Activiteiten die op](/help/sites-cloud/authoring/personalization/activities.md) zijn.
* De [regels die de segmenten](/help/sites-cloud/authoring/personalization/segmentation.md) bepalen.
* De inhoud van de ervaringen in de componenten van het Doel.
* De [configuratie van de richtende motor](/help/sites-cloud/authoring/personalization/activities.md).

Als er onverwachte inhoud op de pagina wordt weergegeven wanneer u een profiel laadt, controleert u de configuratie van elk item in deze lijst.

>[!NOTE]
>
>Als u A/B het testen gebruikt, wanneer het simuleren van ervaringen wordt getoond gebaseerd op verkeerspercentage. Dit wordt gecontroleerd door Adobe Target, wat tot onverwachte resultaten voor auteurs kan leiden. (De _auteuractiviteit is gesynchroniseerd met specifieke montages die herevaluatie tijdens simulatie toestaan.) De auteurs kunnen moeten verfrissen om de andere ervaringen te zien die op hun verkeersmontages worden gebaseerd.

Gebruik de volgende gereedschappen om de ervaring van de bezoeker te simuleren:

* De simulatieactiviteit op het richten wijze: De pagina toont de aanbiedingen voor de gebruiker die momenteel in de Hub van de Context wordt geselecteerd. U kunt de aanbiedingen bewerken die op de gebruiker zijn gericht.
* Modus Voorvertoning: De Hub van de Context van het gebruik om de gebruikers en de plaatsen te selecteren die aan de criteria van de segmenten voldoen dat uw ervaringen op gebaseerd zijn. Wanneer uw selecties van de Hub van de Context veranderen, verandert de gerichte inhoud dienovereenkomstig.

1. Als u wilt overschakelen naar de modus Voorbeeld, klikt of tikt u op **Voorvertoning**.
1. Voor de hulpmiddelbar, klik of tik het pictogram van de Hub van de Context.

   ![Knop ContextHub](../assets/targeted-contexthub-button.png)

1. Gebruik Context Hub om context-eigenschappen te wijzigen. Klik of tik bijvoorbeeld op de eigenschap Person om een andere gebruiker te selecteren.

   ![ContextHub-werkbalk](../assets/targeted-contexthub-toolbar.png)

   De pagina verandert om de inhoud te tonen die voor de huidige context wordt gericht.

1. Als u wijzigingen wilt aanbrengen in de weergegeven aanbiedingen, schakelt u over naar de modus Doel. Selecteer de simulatieactiviteit en bewerk de aanbiedingen voor de context die u hebt geconfigureerd in de modus Voorbeeld.

## Opties voor doelcomponenten configureren {#configuring-target-component-options}

U kunt de component van het Doel aanpassen door tot de opties van de component op één van twee manieren toegang te hebben:

1. Nadat u de component hebt aangewezen, in de component van het Doel, klik of tik de component en toen het montagespictogram (versnelling).

   ![Componentinstellingen](../assets/targeted-component-settings.png)

   AEM geeft het venster met opties voor de doelcomponent weer.

   ![Doel, dialoogvenster](../assets/targeted-dialog.png)

1. U kunt deze instellingen ook openen in de modus Volledig scherm door in het venster met opties voor de doelcomponent op het pictogram voor het volledige scherm te klikken of te tikken.

   ![Knop Volledig scherm](../assets/targeted-fullscreen.png)

   AEM geeft het venster met opties voor de doelcomponent voor volledig scherm weer.

   ![Component in volledig scherm](../assets/targeted-target-as-enging.png)

1. Configureer de instellingen voor de doelcomponent zoals beschreven in de volgende tabellen.

| Optie | Beschrijving |
|---|---|
| Locatie | De locatie is een tekenreeks die de doellocatie van de inhoud een naam geeft en aanbiedingen verbindt met plaatsen (of locaties of componenten) op de pagina waar deze aanbiedingen moeten worden geplaatst. Dit veld is een algemene waarde. Als u een voorstel in een component zet, onthoudt de aanbieding de locatie-id. Wanneer de pagina wordt uitgevoerd, evalueert de motor de segmenten van de gebruiker en gebaseerd op dit, lost het de ervaringen van de actieve campagnes op die zouden moeten worden getoond. Vervolgens worden de locatie-id&#39;s op de pagina gecontroleerd en wordt geprobeerd voorstellen met die locatie-id&#39;s aan te passen. |
| Engine | Selecteer tussen Regels aan de clientzijde (zonder reeksspatiëring), Adobe Target, ContextHub en Adobe Campaign, afhankelijk van de engine die u wilt gebruiken. |

Als u Adobe Target als engine selecteert:

![Doel als motor](../assets/targeted-target-as-enging.png)

| Optie | Beschrijving |
|---|---|
| Nauwkeurige bestemming | Wanneer u nauwkeurige adressering inschakelt, weet de component dat deze moet wachten totdat de context- of contexthubgegevens beschikbaar zijn voordat de aanvraag naar Adobe Target wordt verzonden. Hierdoor kan de laadtijd toenemen. Voor creatie, wordt het nauwkeurige richten altijd toegelaten. Als u het selectievakje Nauwkeurig aanwijzen inschakelt, voert het selectievakje eerst een mboxDefine uit en later een mboxUpdate. Dit resulteert in een Ajax-aanvraag zodra de gegevens beschikbaar zijn. Als u het selectievakje Nauwkeurig aanwijzen niet inschakelt, voert de mbox een mboxCreate uit die onmiddellijk een synchrone aanvraag oplevert (in dit geval zijn mogelijk nog niet alle contextgegevens beschikbaar). Opmerking: Het in- of uitschakelen van het nauwkeurig opgeven van een bepaald onderdeel heeft geen invloed op de instellingen die u globaal hebt ingesteld. U kunt globale instellingen altijd overschrijven door Accurate doelen selecteren in de component. |
| Omgezette segmenten opnemen | Het selecteren van deze controledoos omvat alle opgeloste segmenten in de mbox vraag en om het even welke parameters die in de pagina en in het kader worden gevormd. Dit werkt alleen in situaties met XML API waarin u AEM segmenten synchroniseert. Als u segmenten in AEM hebt die niet door Adobe Target (als manuscriptsegmenten) worden behandeld, dan staat deze optie u toe om het segment in AEM op te lossen en informatie naar Adobe Target te verzenden dat het segment actief is. |
| Overgenomen contextparameters | Hier worden eventueel van het Adobe Target-framework overgeërfde contextparameters weergegeven die aan de geselecteerde pagina zijn gekoppeld. |
| Contextparameters | Klik of tik Add gebied om extra contextparameters te vormen (het zelfde als wat in het kader van het Doel beschikbaar is). Contextparameters die aan de component worden toegevoegd, gelden alleen voor de component en niet voor andere componenten, zoals het geval zou zijn als u contextparameters rechtstreeks aan het framework toevoegt. |
| Statische parameters | Klik of tik Add gebied om extra statische parameters (het zelfde als wat in het kader van het Doel beschikbaar is) te vormen. Statische parameters die aan de component zijn toegevoegd, gelden alleen voor de component en niet voor andere componenten, zoals het geval zou zijn als u statische parameters rechtstreeks aan het framework hebt toegevoegd. Statische parameters komen niet uit context (cliëntcontext van inhoudshub). |

>[!NOTE]
>
>Wanneer u een component selecteert en deze doelbaar maakt, vervangt AEM ook de component en injecteert een Adobe Target-component. (De Adobe Target-component wordt niet alleen gebruikt wanneer u deze handmatig aan de pagina toevoegt, maar ook wanneer u een bestaande component als doel instelt.)
>
>U selecteert **Adobe Campaign** als motor als u AEM met Adobe Campaign integreert. Zie AEM integreren met Adobe Campaign voor meer informatie.
>
>Selecteer **ContextHub** als motor als u ContextHub voor het richten gebruikt. Zie het Vormen ContextHub voor meer informatie.
<!--You select **Adobe Campaign** as the engine if you are integrating AEM with Adobe Campaign. See [Integrating AEM with Adobe Campaign](/help/sites-administering/campaign.md) for more information.-->
<!--Select **ContextHub** as the engine if you are using ContextHub for targeting. See [Configuring ContextHub.](/help/sites-administering/contexthub-config.md)-->
