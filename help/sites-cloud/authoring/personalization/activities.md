---
title: Beheersactiviteiten
description: Met de activiteitenconsole kunt u de marketingactiviteiten van uw merken maken, organiseren en beheren
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Beheersactiviteiten {#managing-activities}

Met de activiteitenconsole kunt u de marketingactiviteiten [](/help/sites-cloud/authoring/personalization/overview.md#activities) van uw merken maken, organiseren en beheren:

* Brandmerken toevoegen
* Voor elk merk, voeg en vorm activiteiten toe
* Activiteiten beheren

>[!TIP]
>
>Als u Adobe Target als doelengine gebruikt, kunt u ook prestatiegegevens van uw activiteiten [](#viewing-performance-and-converting-winning-experiences-a-b-test)bekijken. Als u A/B test, kunt u winnaars [](#viewing-performance-and-converting-winning-experiences-a-b-test)omzetten.

Op de Activity Console worden de activiteiten georganiseerd door merk. U kunt merken en mappen gebruiken om de organisatie van uw activiteiten te structureren. U navigeert aan de console van Activiteiten door te tikken/te klikken **Personalisatie** en het tikken/het klikken **Activiteiten**.

Activiteiten zijn beschikbaar in de modus Doel voor het [ontwerpen van doelgerichte inhoud](/help/sites-cloud/authoring/personalization/targeted-content.md), waar u ook activiteiten kunt maken. De activiteiten die u op het richten wijze creeert verschijnen in de console van Activiteiten.

De activiteiten worden getoond met een etiket beschrijvend welke soort activiteit wordt bepaald:

* XT - Adobe Target-ervaring gericht
* A/B - Adobe Target A/B-tests
* AEM - Adobe Experience Manager-doel (bijvoorbeeld door ContextHub aangestuurd)

![Typen activiteiten](/help/sites-cloud/authoring/assets/activities-types.png)

>[!NOTE]
>
>Welke soorten activiteiten beschikbaar zijn, wordt bepaald door:
>
>* Als de `xt_only` optie is ingeschakeld in de Adobe Target-agent (clientcode) die op de AEM-zijde wordt gebruikt om verbinding te maken met Adobe Target, kunt u **alleen** XT-activiteiten maken in AEM.
   >
   >
* Als de `xt_only` opties **niet** op de huurder van het Doel van Adobe (cliëntcode) worden toegelaten, dan kunt u **zowel** XT als A/B activiteiten in AEM tot stand brengen.
>
>
**** Aanvullende opmerking: De `xt_only` optie is een instelling die wordt toegepast op een bepaalde doelgebruiker (clientcode) en kan alleen rechtstreeks worden gewijzigd in Adobe Target. U kunt deze optie niet in- of uitschakelen in AEM.

>[!CAUTION]
>
>U moet het knooppunt met activiteiteninstellingen `cq:ActivitySettings` op de publicatie-instantie beveiligen, zodat dit niet toegankelijk is voor normale gebruikers. Het knooppunt met activiteiteninstellingen mag alleen toegankelijk zijn voor de service die de activiteitensynchronisatie afhandelt naar Adobe Target.
>
>Zie Vereisten voor integratie met Adobe Target voor meer informatie.
<!--
>See [Prerequisites for Integrating with Adobe Target](/help/sites-administering/target-requirements.md#securingtheactivitysettings) for detailed information.
-->

## Een merk maken met de activiteitenconsole {#creating-a-brand-using-the-activities-console}

Maak een merk waarvoor u marketingactiviteiten wilt beheren.

Wanneer u een merk creeert gebruikend de console van Activiteiten, verschijnt het ook in de console [van](/help/sites-cloud/authoring/personalization/offers.md) Aanbiedingen waar u aanbiedingen voor de ervaringen van uw activiteiten kunt tot stand brengen.

1. Klik of tik op **Personalisatie** in de navigatieconsole. Klik of tik **Activiteiten**.

   ![Navigeren naar activiteiten](/help/sites-cloud/authoring/assets/activities-navigation.png)

1. Klik of tik op **Maken in de Activiteitenconsole** en kies **Merk** maken.
1. Selecteer de merksjabloon en klik of tik op **Volgende**.
1. Typ een titel voor het merk zoals u deze wilt weergeven in de consoles Activiteiten en Aanbiedingen. Typ of selecteer eventueel een of meer tags die u aan het merk wilt koppelen.
1. Klik of tik op **Maken**. Uw merk wordt weergegeven in de Activiteitenconsole.

## Een activiteit toevoegen/bewerken met de activiteitenconsole {#adding-editing-an-activity-using-the-activities-console}

Voeg een activiteit toe of bewerk een bestaande activiteit om uw marketing inspanningen op specifieke doelgroepen te concentreren. Wanneer u een activiteit creeert/uitgeeft, specificeert u de volgende informatie:

* **** Naam: De naam van de activiteit.
* **** Richtingsmotor: Of [AEM](/help/sites-cloud/authoring/personalization/overview.md#aem) of [Adobe Target](/help/sites-cloud/authoring/personalization/overview.md#adobe-target) als motor voor gerichte inhoud.
* **** Selecteer een doelconfiguratie: (Alleen Adobe Target) De cloudconfiguratie die deze activiteit moet gebruiken om verbinding te maken met Adobe Target. Deze optie wordt alleen weergegeven als Adobe Target is geselecteerd voor Targeting Engine.
* **Type** activiteit: Type activiteit - A/B-test of ervaring gericht op
* **** Doel: (Optioneel) Een beschrijving van de activiteit.
* **** Ervaringen: Toewijzingen tussen publieksnamen en de marketingsegmenten waarop u zich richt.
* **** Verkeerspercentages: Als de test A/B wordt geselecteerd, kunt u veranderen hoeveel verkeer (in percenten) naar elke ervaring gaat.
* **** Duur: De periode waarin de activiteit wordt toegepast.
* **** Prioriteit: De relatieve prioriteit van de activiteit. Wanneer de activiteiten inhoud voor de zelfde gebruikerssegmenten verstrekken, krijgt de activiteit van de hogere prioriteit belangrijkheid.
* **** Metrisch doel: Als Adobe Target is geselecteerd als de doelengine, kunt u succeswaarden aan de activiteit toevoegen. Één succesmetrisch wordt vereist.

>[!NOTE]
>
>De nieuwe activiteiten van het Doel van Adobe moeten in de gerichte inhoudsredacteur, niet in de console van *Activiteiten* worden **** gecreeerd, aangezien de synchronisatie aan Adobe Target zal ontbreken.
>
>U kunt echter bestaande Adobe Target-activiteiten in de console bewerken.

Een activiteit toevoegen:

1. Klik of tik op het merk waarvoor u de activiteit maakt en klik op **Maken** of tik vervolgens op Activiteit **** maken. Selecteer bij het bewerken de activiteit in het scherm Hoofdgebied en klik op Activiteit **** bewerken of tikt erop.
1. Geef de volgende informatie op en klik of tik op **Volgende**:
   * Een naam voor de activiteit.
   * De doelengine die moet worden gebruikt. ContextHub (AEM) wordt geselecteerd door gebrek. Als u Adobe Target moet gebruiken, maakt u de activiteit in de beoogde inhoudseditor.
   * Als u Adobe Target hebt geselecteerd als de doelengine, selecteert of bewerkt u de cloudconfiguratie die u wilt gebruiken om verbinding te maken met Adobe Target. (Zorg ervoor dat u geen framework selecteert dat u hebt gemaakt voor uw cloudconfiguratie.)
   * (Optioneel) Het doel of een beschrijving van de activiteit.
   * Selecteer het type activiteit.
1. Voeg een of meer ervaringen toe aan de activiteit. Klik of tik op Ervaring **** toevoegen.
1. Als u AEM-doelversie of Adobe Target-ervaring gebruikt voor:
   1. Klik of tik **Uitgezochte Publiek** en selecteer het segment dat uw ervaringsdoelstellingen.
   1. Klik of tik op **Ervaring** toevoegen, typ een naam en klik of tik op **OK**.
   1. Klik of tik op **Volgende**.
Als u Adobe Target A/B Testing gebruikt:
   1. Klik of tik op het potlood in het vak Soorten publiek om een publiek te selecteren.
   1. Klik of tik op **Ervaring** toevoegen, typ een naam en klik of tik op **OK**.
   1. Ga het percentage van verkeer in dat elke ervaring toont.
   1. Klik of tik op **Volgende**.
1. Als u wilt opgeven wanneer de activiteit begint, selecteert u een van de volgende waarden in het keuzemenu **Start** :
   * **** Indien geactiveerd: De activiteit begint wanneer de pagina die de beoogde inhoud bevat, wordt geactiveerd.
   * **** Opgegeven datum en tijd: Een specifieke tijd. Wanneer u deze optie selecteert, klikt of tikt u op het kalenderpictogram, selecteert u een datum en geeft u de tijd op om de activiteit te starten.
1. Als u wilt opgeven wanneer de activiteit eindigt, gebruikt u het vervolgkeuzemenu Einde om een van de volgende waarden te selecteren:
   * **Wanneer gedeactiveerd**: De activiteit eindigt wanneer de pagina die de beoogde inhoud bevat, wordt gedeactiveerd.
   * **Opgegeven datum en tijd**: Een specifieke tijd. Wanneer u deze optie selecteert, klikt of tikt u op het kalenderpictogram, selecteert u een datum en geeft u de tijd op om de activiteit te beëindigen.
1. Als u een prioriteit voor de activiteit wilt opgeven, gebruikt u de schuifregelaar om **Laag**, **Normaal** of **Hoog** te selecteren.
1. Als u Adobe Target als doelengine gebruikt, selecteert u wat u met deze activiteit wilt meten. Zie de Activiteit [Vormen en Plaatsende Doelstellingen](/help/sites-cloud/authoring/personalization/targeted-content.md) voor meer informatie over de beschikbare succesmetriek. U moet ten minste één doel selecteren.
1. Klik of tik op **Opslaan**.

   >[!NOTE]
   >
   >Nadat u een activiteit hebt gemaakt, moet u deze publiceren zodat deze beschikbaar is.

## Publicatie- en publicatieactiviteiten {#publishing-and-unpublishing-activities}

U moet activiteiten publiceren om deze beschikbaar te maken. Omgekeerd kunt u activiteiten onbeschikbaar maken door deze te verwijderen.

>[!NOTE]
>
>Wanneer u de publicatie van een activiteit ongedaan maakt,

Om activiteiten te publiceren of unpublish:

1. Klik of tik op het merk en vervolgens het gebied met de activiteit die u wilt publiceren of de publicatie ongedaan wilt maken.
1. Tik of klik op het pictogram naast de activiteit of activiteiten die u wilt publiceren of waarvan u de publicatie ongedaan wilt maken.

   ![Publiceren vanaf de activiteitenconsole](/help/sites-cloud/authoring/assets/activities-console.png)

1. Tik of klik op **Publiceren** om te publiceren. Tik of klik op **Publiceren** ongedaan maken om de publicatie ongedaan te maken. Uw activiteit of activiteiten worden gepubliceerd of niet gepubliceerd en hun statusveranderingen in de console van de Activiteiten (kan vereisen verfrissen).

## Activiteiten met betrekking tot instanties Auteur en Publiceren {#activities-on-author-and-publish-instances}

Wanneer een activiteit wordt geactiveerd die de doelengine van Adobe Target gebruikt, wordt een tweede activiteit gemaakt op de publicatie-instantie:

* De activiteit op de auteurinstantie volgt activiteit op de auteursinstantie en is nuttig om de bezoekerservaring te simuleren. De analyses die voor deze activiteit worden geregistreerd, weerspiegelen slechts wat op de auteursinstantie voorkomt.
* De activiteit op de publicatie-instantie geeft de activiteit op de publicatieserver weer en reageert hierop. Dit is de activiteit die op de openbare website loopt. Alleen de publicatieactiviteit is relevant voor het bijhouden en analyseren van het gebruik van de feitelijke openbare site.

## Weergaveprestaties en bekroonde ervaringen (A/B-test) {#viewing-performance-and-converting-winning-experiences-a-b-test}

U kunt de prestaties zien van elke Adobe Target-activiteit (XT of A/B). Als u A/B tests gebruikt, kunt u het winnen ervaring ook omzetten, die dan de standaardervaring wordt.

Om de prestaties van de activiteit te bekijken en het winnen ervaringen om te zetten:

1. Klik of tik op **Activiteiten** in **Personalisatie** om naar de **Activiteiten** -console te navigeren.
1. Klik of tik op het merk waarvoor u activiteiten wilt zien.
1. Selecteer de activiteit en klik of tik Eigenschappen **van de** Mening en klik het lusje van **Rapporten** en selecteer de activiteit u prestaties voor wilt bekijken/het winnen ervaringen voor omzetten. Prestatiegegevens worden weergegeven.

   ![Prestaties van activiteiten controleren](/help/sites-cloud/authoring/assets/activities-performance.png)

1. Klik of tik op de koppeling **Push Win** om die ervaring als de standaardervaring te gebruiken.

   Als u de winnaar omzet, gebeurt het volgende:

   * De huidige activiteit wordt uitgeschakeld
   * Hiermee wijzigt u alle pagina&#39;s en vervangt u de doelinhoud door de feitelijke inhoud van de winnende ervaring. De inhoud van de winnende ervaring wordt onderdeel van de normale pagina **zonder** doeleinde.
   ![Winnaar omzetten](/help/sites-cloud/authoring/assets/activities-reports.png)

   Een winnende ervaring is de ervaring die meer Lift in de rapporten produceert, die op de omrekeningskoers gebaseerd is.

1. Klik of tik op **Ja** om te bevestigen dat u de winnaar wilt converteren, de huidige ervaring wilt uitschakelen en vervangen door de inhoud van de winnende ervaring.

## Activiteiten synchroniseren met Adobe Target {#synchronizing-activities-with-adobe-target}

Activiteiten die gebruikmaken van de Adobe Target-engine worden gesynchroniseerd met Adobe Target-campagnes. Een activiteit wordt automatisch gesynchroniseerd met Adobe Target als aan de volgende voorwaarden wordt voldaan:

* De activiteit bevat minstens één ervaring.
* Ten minste één ervaring bevat een toegewezen segment en één aanbieding.
* Elke ervaring in de activiteit moet hetzelfde aantal aanbiedingen hebben.

Deze voorwaarden gelden voor activiteiten met betrekking tot auteur- en publicatieinstanties.

Wanneer een activiteit wordt gesynchroniseerd, wordt een overeenkomstige campagne gecreeerd in het Doel van Adobe:

* De activiteiten in het publicatieexemplaar hebben de zelfde naam zoals de overeenkomstige campagne van het Doel van Adobe.
* De activiteiten op de auteurinstantie stemmen met campagnes van het Doel van de zelfde naam met het `_author` achtervoegsel.

![Synchroniseren met Adobe Target](/help/sites-cloud/authoring/assets/activities-synch.png)

De activiteiten van de auteur worden meteen gesynchroniseerd wanneer de activiteit wordt gewijzigd. De directe synchronisatie laat de simulatie van activiteiten met ContextHub toe.

De publicatieactiviteiten worden gesynchroniseerd wanneer de activiteit wordt gepubliceerd naar de publicatie-instantie van AEM.

## Synchronisatie van activiteiten voor probleemoplossing {#troubleshooting-activity-synchronization}

Wanneer AEM een activiteit met Adobe Target synchroniseert, omvat AEM een bezit van de genoemde activiteit `thirdPartyId`. De waarde van deze eigenschap is gebaseerd op het pad van de activiteit in de AEM-opslagplaats. Geen twee campagnes in Adobe Target kunnen de zelfde waarde voor het `thirdPartyId` bezit hebben. Daarom zal een activiteit er niet in slagen om te synchroniseren als een bestaande campagne (van een verschillend type AB, XT) in het Doel van Adobe de zelfde waarde voor gebruikt `thirdPartyId`.

Deze situatie kan zich voordoen in de volgende omstandigheden:

1. Er wordt een activiteit gemaakt en gesynchroniseerd met Adobe Target.
1. Op een andere AEM-instantie wordt een activiteit onder hetzelfde merk en met dezelfde naam gemaakt. Synchronisatie van deze activiteit mislukt bij poging.

Deze situatie kan zich ook voordoen in de volgende omstandigheden:

1. Er wordt een activiteit gemaakt en gesynchroniseerd met Adobe Target. De activiteit wordt dan geschrapt op AEM.
1. Een activiteit wordt gecreeerd onder het zelfde merk en gebruikend de zelfde naam zoals de geschrapte activiteit. Synchronisatie van deze activiteit mislukt bij poging.

Gebruik altijd unieke namen voor activiteiten om synchronisatieproblemen te voorkomen. Als een activiteit er niet in slaagt te synchroniseren, kunt u de campagne verwijderen in Adobe Target die dezelfde naam gebruikt als die campagne niet wordt gebruikt.

>[!NOTE]
>
>Wanneer u een campagne maakt in Adobe Target, wordt aan elke campagne een eigenschap toegewezen die `thirdPartyId` wordt aangeroepen. Wanneer u de campagne verwijdert in Adobe Target, `thirdPartyId` wordt deze niet verwijderd. U kunt niet `thirdPartyId` voor campagnes van verschillende types (AB, XT) opnieuw gebruiken en het kan niet manueel worden verwijderd. Geef elke campagne een unieke naam om dit probleem te voorkomen. campagnemenamen kunnen daarom niet opnieuw worden gebruikt in verschillende soorten campagnes.
>
>Als u dezelfde naam gebruikt in hetzelfde type campagne, overschrijft u de bestaande campagne.
>
>Als tijdens het synchroniseren de fout &quot;Verzoek is mislukt. `thirdPartyId` bestaat al.&quot; Wijzig de naam van de campagne en synchroniseer opnieuw.
