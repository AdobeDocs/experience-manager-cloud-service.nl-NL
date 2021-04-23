---
title: Aangesloten middelen gebruiken om DAM-middelen te delen in [!DNL Sites]
description: Gebruik middelen die beschikbaar zijn op een externe [!DNL Adobe Experience Manager Assets] deployment when creating your web pages on another [!DNL Adobe Experience Manager Sites] implementatie.
contentOwner: AG
feature: Middelenbeheer, Verbonden middelen, Asset Distribution, Gebruiker en Groepen
role: Administrator,Business Practitioner,Architect
exl-id: 2346f72d-a383-4202-849e-c5a91634617a
translation-type: tm+mt
source-git-commit: bbc396fbe7b3c11f8011a32fa78577957422fcf2
workflow-type: tm+mt
source-wordcount: '2816'
ht-degree: 25%

---

# Aangesloten middelen gebruiken om DAM-elementen te delen in [!DNL Experience Manager Sites] {#use-connected-assets-to-share-dam-assets-in-aem-sites}

In grote ondernemingen is de infrastructuur voor het maken van websites soms gedistribueerd. Soms zijn de functies en de digitale assets voor het maken van websites opgenomen in verschillende implementaties. Één reden kan geografisch gedistribueerde bestaande plaatsingen zijn die worden vereist om samen te werken. Een andere reden kunnen acquisities zijn die leiden tot heterogene infrastructuren die de moedermaatschappij samen wil gebruiken.

Gebruikers kunnen webpagina&#39;s maken in [!DNL Experience Manager Sites]. [!DNL Experience Manager Assets] is het DAM-systeem (Digital Asset Management) dat de vereiste middelen voor websites levert. [!DNL Experience Manager] ondersteunt nu het bovenstaande gebruiksgeval door integratie  [!DNL Sites] en  [!DNL Assets].

## Overzicht van gekoppelde assets {#overview-of-connected-assets}

Wanneer het uitgeven van pagina&#39;s in [!UICONTROL Page Editor] als doelbestemming, kunnen de auteurs vlot zoeken, doorbladeren, en activa van een verschillende [!DNL Assets] plaatsing inbedden die als bron van activa dienst doet. De beheerders maken een eenmalige integratie van een implementatie van [!DNL Experience Manager] met [!DNL Sites]-mogelijkheid met een andere implementatie van [!DNL Experience Manager] met [!DNL Assets]-mogelijkheid.

Voor de [!DNL Sites] auteurs, zijn de verre activa beschikbaar als read-only lokale activa. Met deze functie kunt u naadloos zoeken naar telkens een klein aantal externe assets voor gebruik. Als u veel externe middelen beschikbaar wilt maken voor een [!DNL Sites]-implementatie in één keer, kunt u overwegen de middelen in bulk te migreren.

### Vereisten en ondersteunde implementaties {#prerequisites}

Controleer de volgende punten voordat u deze functie gebruikt of configureert:

* De gebruikers maken deel uit van de aangewezen gebruikersgroepen op elke plaatsing.
* Voor [!DNL Adobe Experience Manager] implementatietypen wordt aan een van de ondersteunde criteria voldaan. [!DNL Experience Manager] als Cloud Service  [!DNL Assets] werkt met  [!DNL Experience Manager] 6.5. Zie  [!DNL Experience Manager] Verbonden elementen in [6.5 voor meer informatie over hoe deze functionaliteit werkt in  [!DNL Experience Manager] 6.5 [!DNL Assets]](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/use-assets-across-connected-assets-instances.html).

   |  | [!DNL Sites] als  [!DNL Cloud Service] | [!DNL Experience Manager] 6.5  [!DNL Sites] over AMS | [!DNL Experience Manager] 6.5  [!DNL Sites] on-premise |
   |---|---|---|---|
   | **[!DNL Experience Manager Assets]als[!DNL Cloud Service]** | Ondersteund | Ondersteund | Ondersteund |
   | **[!DNL Experience Manager]6.5  [!DNL Assets] over AMS** | Ondersteund | Ondersteund | Ondersteund |
   | **[!DNL Experience Manager]6.5  [!DNL Assets] on-premise** | Niet ondersteund | Niet ondersteund | Niet ondersteund |

### Ondersteunde bestandsindelingen {#mimetypes}

Auteurs zoeken naar afbeeldingen en de volgende typen documenten in de Inhoudszoeker en gebruiken de doorzochte elementen in de Pagina-editor. Documenten worden toegevoegd aan de `Download`-component en afbeeldingen aan de `Image`-component. Auteurs voegen ook de externe elementen toe in een aangepaste [!DNL Experience Manager]-component die de standaardcomponenten `Download` of `Image` uitbreidt. De ondersteunde indelingen zijn:

* **Afbeeldingsindelingen**: De indelingen die de  [component Image ](https://www.aemcomponents.dev/content/core-components-examples/library/page-authoring/image.html) ondersteunt.
* **Documentindelingen**: Zie de  [ondersteunde documentindelingen](file-format-support.md#document-formats).

### Betrokken gebruikers en groepen {#users-and-groups-involved}

Hieronder worden de diverse rollen beschreven voor de configuratie en toepassing van een kenmerk en de overeenkomstige gebruikersgroepen. Het lokale bereik wordt gebruikt voor het geval waarin een auteur een webpagina maakt. De externe scope wordt gebruikt voor de DAM-implementatie die als host fungeert voor de vereiste assets. De auteur [!DNL Sites] haalt deze externe elementen op.

| Rol | Scope | Gebruikersgroep | Gebruikersnaam in voorbeeldprocedure | Vereiste |
|------|--------|-----------|-----|----------|
| [!DNL Sites] beheerder | Lokaal | [!DNL Experience Manager] `administrators` | `admin` | Stel [!DNL Experience Manager] in en configureer integratie met de externe [!DNL Assets]-implementatie. |
| DAM-gebruiker | Lokaal | `Authors` | `ksaner` | Wordt gebruikt om de assets die bij `/content/DAM/connectedassets/` zijn opgehaald, weer te geven en te dupliceren. |
| [!DNL Sites] author | Lokaal | <ul><li>`Authors` (met lees toegang op verre DAM en auteurstoegang op lokaal  [!DNL Sites]) </li> <li>`dam-users` op lokaal niveau  [!DNL Sites]</li></ul> | `ksaner` | Eindgebruikers zijn [!DNL Sites] auteurs die deze integratie gebruiken om hun inhoudssnelheid te verbeteren. Auteurs kunnen bestanden in externe DAM zoeken en doorbladeren met [!UICONTROL Content Finder] en de vereiste afbeeldingen in lokale webpagina&#39;s gebruiken. De referenties van de `ksaner` DAM-gebruiker worden gebruikt. |
| [!DNL Assets] beheerder | Extern | [!DNL Experience Manager] `administrators` | `admin` op afstand  [!DNL Experience Manager] | Configureer CORS (Cross-Origin Resource Sharing). |
| DAM-gebruiker | Extern | `Authors` | `ksaner` op afstand  [!DNL Experience Manager] | Auteurrol bij de externe [!DNL Experience Manager]-implementatie. Zoek en blader naar assets in gekoppelde assets met de [!UICONTROL Content Finder]. |
| DAM-distributeur (technische gebruiker) | Extern | <ul> <li> [!DNL Sites] `Authors`</li> <li> `connectedassets-assets-techaccts` </li> </ul> | `ksaner` op afstand  [!DNL Experience Manager] | Deze gebruiker die aanwezig is op de externe implementatie wordt gebruikt door de lokale server [!DNL Experience Manager] (niet de auteur-rol [!DNL Sites]) om de externe middelen op te halen, namens de auteur [!DNL Sites]. Deze rol is anders dan de twee bovenstaande `ksaner`-rollen en hoort bij een andere gebruikersgroep. |
| [!DNL Sites] technisch gebruiker | Lokaal | `connectedassets-sites-techaccts` | - | Staat [!DNL Assets] plaatsing toe om verwijzingen naar activa in [!DNL Sites] Web-pagina&#39;s te zoeken. |

## Een verbinding configureren tussen [!DNL Sites]- en [!DNL Assets]-implementaties {#configure-a-connection-between-sites-and-assets-deployments}

Een [!DNL Experience Manager] beheerder kan deze integratie tot stand brengen. Zodra gecreeerd, worden de toestemmingen die worden vereist om het te gebruiken gevestigd via gebruikersgroepen. De gebruikersgroepen worden gedefinieerd bij de [!DNL Sites]-implementatie en bij de DAM-implementatie.

Voer de volgende stappen uit om Connected Assets en lokale [!DNL Sites]-connectiviteit te configureren:

1. Toegang tot een bestaande [!DNL Sites]-implementatie. Deze [!DNL Sites]-implementatie wordt gebruikt voor het ontwerpen van webpagina&#39;s, bijvoorbeeld op `https://[sites_servername]:port`. Aangezien de pagina creatie op [!DNL Sites] plaatsing gebeurt, laten wij [!DNL Sites] plaatsing als lokaal vanuit het het auteursperspectief van de pagina roepen.

1. Toegang tot een bestaande [!DNL Assets]-implementatie. Deze [!DNL Assets]-implementatie wordt gebruikt voor het beheer van digitale elementen, bijvoorbeeld op `https://[assets_servername]:port`.

1. Zorg ervoor dat de gebruikers en rollen met het juiste bereik aanwezig zijn op de [!DNL Sites]-implementatie en op de [!DNL Assets]-implementatie op AMS. Creeer een technische gebruiker op [!DNL Assets] plaatsing en voeg aan de gebruikersgroep toe die in [betrokken gebruikers en groepen](/help/assets/use-assets-across-connected-assets-instances.md#users-and-groups-involved) wordt vermeld.

1. Open de lokale [!DNL Sites]-implementatie op `https://[sites_servername]:port`. Klik op **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Connected Assets Configuration]** en geef de volgende waarden op:

   1. A **[!UICONTROL Title]** van de configuratie.
   1. **[!UICONTROL Remote DAM URL]** is de URL van de  [!DNL Assets] locatie in de notatie  `https://[assets_servername]:[port]`.
   1. Referenties van een DAM-distributeur (technische gebruiker).
   1. Voer in het veld **[!UICONTROL Mount Point]** het lokale [!DNL Experience Manager]-pad in waar [!DNL Experience Manager] de elementen ophaalt. Bijvoorbeeld de map `connectedassets`. De middelen die van DAM worden gehaald worden opgeslagen in deze omslag op [!DNL Sites] plaatsing.
   1. **[!UICONTROL Local Sites URL]** is de locatie van de  [!DNL Sites] implementatie. [!DNL Assets] de plaatsing gebruikt deze waarde om verwijzingen naar de digitale activa te handhaven die door deze  [!DNL Sites] plaatsing worden gehaald.
   1. Referenties van technische gebruiker [!DNL Sites].
   1. De waarde van **[!UICONTROL Original Binary transfer optimization Threshold]** gebied specificeert als de originele activa (met inbegrip van de vertoningen) synchroon of niet worden overgebracht. Elementen met een kleinere bestandsgrootte kunnen gemakkelijk worden opgehaald terwijl elementen met een relatief grotere bestandsgrootte het best asynchroon kunnen worden gesynchroniseerd. De waarde hangt van uw netwerkmogelijkheden af.
   1. Selecteer **[!UICONTROL Datastore Shared with Connected Assets]** als u een datastore gebruikt om uw activa op te slaan en de Datastore de gemeenschappelijke opslag tussen beide plaatsingen is. In dit geval is de drempellimiet niet van belang omdat de werkelijke binaire activa op de datastore beschikbaar zijn en niet worden overgedragen.

   ![Een typische configuratie voor de functionaliteit van Connected Assets](assets/connected-assets-typical-config.png)

   *Afbeelding: Een standaardconfiguratie voor de functionaliteit van Connected Assets.*

1. De bestaande digitale middelen op [!DNL Assets]-implementatie worden al verwerkt en de uitvoeringen worden gegenereerd. Deze vertoningen worden opgehaald gebruikend deze functionaliteit zodat is er geen behoefte om de vertoningen opnieuw te produceren. Schakel de workflowdraagprogramma&#39;s uit om te voorkomen dat uitvoeringen opnieuw worden gegenereerd. Pas de startconfiguraties van de implementatie ([!DNL Sites]) aan om de map `connectedassets` uit te sluiten (de elementen worden opgehaald in deze map).

   1. Klik bij [!DNL Sites]-implementatie op **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Launchers]**.

   1. Zoek naar startprogramma&#39;s met workflows als **[!UICONTROL DAM Update Asset]** en **[!UICONTROL DAM Metadata Writeback]**.

   1. Selecteer het workflowstartprogramma en klik op **[!UICONTROL Properties]** op de actiebalk.

   1. Wijzig in de wizard [!UICONTROL Properties] de velden **[!UICONTROL Path]** als de volgende toewijzingen om de reguliere expressies bij te werken om het koppelingspunt **[!UICONTROL connectedassets]** uit te sluiten.

   | Voor | Na |
   | ------ | ------------ |
   | `/content/dam(/((?!/subassets).)*/)renditions/original` | `/content/dam(/((?!/subassets)(?!connectedassets).)*/)renditions/original` |
   | `/content/dam(/.*/)renditions/original` | `/content/dam(/((?!connectedassets).)*/)renditions/original` |
   | `/content/dam(/.*)/jcr:content/metadata` | `/content/dam(/((?!connectedassets).)*/)jcr:content/metadata` |

   >[!NOTE]
   >
   >Alle uitvoeringen die beschikbaar zijn op de externe implementatie worden opgehaald, wanneer auteurs middelen ophalen. Als u meer weergaven van een opgehaalde asset tot stand wilt brengen, moet u deze configuratiestap overslaan. De [!UICONTROL DAM Update Asset]-workflow wordt geactiveerd en er worden meer uitvoeringen gemaakt. Deze uitvoeringen zijn alleen beschikbaar bij de lokale [!DNL Sites]-implementatie en niet bij de externe DAM-implementatie.

1. Voeg de [!DNL Sites]-implementatie toe als een toegestane oorsprong in de CORS-configuratie bij de [!DNL Assets]-implementatie. Zie [CORS](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html) begrijpen voor meer informatie.

1. Configureer [dezelfde ondersteuning voor sitecookie](/help/security/same-site-cookie-support.md).

U kunt de connectiviteit tussen de gevormde [!DNL Sites] plaatsingen en [!DNL Assets] plaatsing controleren.

![Verbindingstest van Verbonden activa gevormde  [!DNL Sites]](assets/connected-assets-multiple-config.png)
*Cijfer: Verbindingstest van gevormde Verbonden Activa  [!DNL Sites].*

<!-- TBD: Check if Launchers are to be disabled on CS instances. Is this option even available to the users on CS? -->

## Een verbinding configureren tussen [!DNL Sites]- en [!DNL Dynamic Media]-implementaties {#sites-dynamic-media-connected-assets}

U kunt een verbinding configureren tussen [!DNL Sites]-implementatie en [!DNL Dynamic Media]-implementatie waarmee auteurs van webpagina&#39;s [!DNL Dynamic Media]-afbeeldingen in hun webpagina&#39;s kunnen gebruiken. Tijdens het ontwerpen van webpagina&#39;s blijft de ervaring om externe middelen en externe [!DNL Dynamic Media]-implementaties te gebruiken ongewijzigd. Hierdoor kunt u de [!DNL Dynamic Media]-functionaliteit benutten via de functie Verbonden elementen, bijvoorbeeld voorinstellingen voor slimme uitsnijden en afbeeldingen.

Voer de volgende stappen uit om deze verbinding te configureren.

1. Configuratie van verbonden elementen maken zoals hierboven beschreven. Selecteer **[!UICONTROL Fetch original rendition for Dynamic Media Connected Assets]** bij het configureren van de functionaliteit.

1. Configureer [!DNL Dynamic Media] op lokale [!DNL Sites]- en externe [!DNL Assets]-implementaties. Volg de instructies aan [configure [!DNL Dynamic Media]](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).

   * Gebruik dezelfde bedrijfsnaam in alle configuraties.
   * Selecteer **[!UICONTROL Disabled by default]** op het lokale [!DNL Sites] in [!UICONTROL Dynamic Media sync mode]. Voor de implementatie van Sites hebt u alleen alleen-lezen toegang tot de [!DNL Dynamic Media]-account nodig.
   * Selecteer **[!UICONTROL Selective Publish]** in de lokale [!DNL Sites] optie. **[!UICONTROL Publish Assets]** Selecteer **[!UICONTROL Sync All Content]** niet.
   * Bij externe [!DNL Assets]-implementatie selecteert u **[!UICONTROL Enabled by default]** in [!UICONTROL Dynamic Media sync mode].

1. Schakel [[!DNL Dynamic Media] ondersteuning in Image Core Component](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/image.html#dynamic-media) in. Met deze functie schakelt u de standaard [Image component](https://www.aemcomponents.dev/content/core-components-examples/library/page-authoring/image.html) in om [!DNL Dynamic Media]-afbeeldingen weer te geven wanneer [!DNL Dynamic Media]-afbeeldingen door auteurs worden gebruikt op webpagina&#39;s bij lokale [!DNL Sites]-implementatie.

## Externe assets gebruiken {#use-remote-assets}

De auteurs van de website maken gebruik van Content Finder om verbinding te maken met de DAM-implementatie. Auteurs kunnen externe assets zoeken, doorbladeren en naar een component slepen. Om de externe DAM te verifiëren, moet u de referenties van de DAM-gebruiker die door uw beheerder zijn verstrekt, bij de hand houden.

Auteurs kunnen de middelen die beschikbaar zijn op de lokale DAM en de externe DAM-implementatie, in één webpagina gebruiken. Gebruik de Content Finder om te schakelen tussen het doorzoeken van de lokale of de externe DAM.

Alleen die tags met externe elementen worden opgehaald die een exact overeenkomende tag hebben samen met dezelfde taxonomihiërarchie, die beschikbaar is op de lokale [!DNL Sites]-implementatie. Alle andere tags worden verwijderd. Auteurs kunnen naar externe middelen zoeken met alle tags die zich op de externe [!DNL Experience Manager]-implementatie bevinden, omdat deze functie een full-text zoekopdracht biedt.

### Procedure voor gebruik {#walk-through-of-usage}

Gebruik bovenstaande instellingen om de functionaliteit van een authoring-ervaring beter te begrijpen. Gebruik documenten of afbeeldingen van uw keuze op de externe DAM-implementatie.

1. Navigeer naar de [!DNL Assets]-interface op de externe implementatie door **[!UICONTROL Assets]** > **[!UICONTROL Files]** vanuit [!DNL Experience Manager]-werkruimte te openen. U kunt `https://[assets_servername_ams]:[port]/assets.html/content/dam` ook in een browser openen. Upload de assets van uw keuze.
1. Klik op [!DNL Sites] in de profielactivator rechtsboven in de **[!UICONTROL Impersonate as]**-implementatie. Geef `ksaner` op als gebruikersnaam, selecteer de opgegeven optie en klik op **[!UICONTROL OK]**.
1. Open een `We.Retail`-websitepagina op **[!UICONTROL Sites]** > **[!UICONTROL We.Retail]** > **[!UICONTROL us]** > **[!UICONTROL en]**. Bewerk de pagina. U kunt `https://[aem_server]:[port]/editor.html/content/we-retail/us/en/men.html` ook in een browser openen om een pagina te bewerken.

   Klik op **[!UICONTROL Toggle Side Panel]** in de linkerbovenhoek van de pagina.

1. Open de tab [!UICONTROL Assets] en klik **[!UICONTROL Log in to Connected Assets]**.
1. Geef de referenties op: `ksaner` als gebruikersnaam en `password` als wachtwoord. Deze gebruiker heeft auteurstoestemmingen op zowel [!DNL Experience Manager] plaatsingen.
1. Zoek naar de asset die u aan DAM hebt toegevoegd. De externe assets worden weergegeven in het linkerdeelvenster. Filter op afbeeldingen of documenten en filter verder op de typen ondersteunde documenten. Sleep de afbeeldingen naar een `Image`-component en sleep documenten naar een `Download`-component.

   De opgehaalde middelen zijn alleen-lezen op de lokale [!DNL Sites]-implementatie. U kunt nog steeds de opties gebruiken die door uw [!DNL Sites] componenten worden geboden om het opgehaalde element te bewerken. Het bewerken op basis van componenten is niet-destructief.

   ![Opties voor het filteren van documenttypen en afbeeldingen bij het zoeken naar assets op de externe DAM](assets/filetypes_filter_connected_assets.png)

   *Afbeelding: Opties voor het filteren van documenttypen en afbeeldingen bij het zoeken naar assets op de externe DAM.*

1. De auteur van een site krijgt een melding als een asset asynchroon wordt opgehaald en als het ophalen mislukt. Tijdens het ontwerpen of zelfs na het ontwerpen, kunnen de auteurs gedetailleerde informatie over het halen van taken en fouten in [asynchrone banen](/help/operations/asynchronous-jobs.md) gebruikersinterface zien.

   ![Melding van het asynchroon op de achtergrond ophalen van assets.](assets/assets_async_transfer_fails.png)

   *Afbeelding: Melding van het asynchroon op de achtergrond ophalen van assets.*

1. Bij het publiceren van een pagina wordt [!DNL Experience Manager] weergegeven met een volledige lijst met elementen die op de pagina worden gebruikt. Zorg ervoor dat de externe assets op het moment van publicatie worden opgehaald. Zie [asynchrone taken](/help/operations/asynchronous-jobs.md) gebruikersinterface om de status van elk opgehaald element te controleren.

   >[!NOTE]
   >
   >Zelfs als een of meer externe assets niet worden opgehaald, wordt de pagina gepubliceerd. De component die gebruikmaakt van de externe asset, wordt leeg (zonder content) gepubliceerd. In het meldingsgebied [!DNL Experience Manager] wordt een melding weergegeven voor fouten die worden weergegeven op de pagina voor asynchrone taken.

>[!CAUTION]
>
>Nadat de opgehaalde externe elementen in een webpagina zijn gebruikt, kunnen ze worden doorzocht en kunnen ze worden gebruikt door iedereen die toegangsrechten heeft tot de lokale map. De opgehaalde elementen worden opgeslagen in de lokale map (`connectedassets` in de bovenstaande doorloop). De assets zijn ook doorzoekbaar en zichtbaar in de lokale opslagplaats, en wel via [!UICONTROL Content Finder].

De opgehaalde assets kunnen net als elke andere lokale asset worden gebruikt, alleen kunnen de bijbehorende metadata niet worden bewerkt.

### Gebruik van een element op webpagina&#39;s controleren {#asset-usage-references}

[!DNL Experience Manager] Hiermee kunnen DAM-gebruikers alle verwijzingen naar een element controleren. Het helpt het gebruik van een middel in verre [!DNL Sites] en in samenstellingsactiva begrijpen en beheren. Veel auteurs van webpagina&#39;s die [!DNL Experience Manager Sites] implementeren, kunnen een middel gebruiken op een externe DAM in verschillende webpagina&#39;s. Om het beheer van bedrijfsmiddelen te vereenvoudigen en niet tot verbroken verwijzingen te leiden, is het belangrijk dat de DAM-gebruikers het gebruik van middelen op lokale en externe webpagina&#39;s controleren. Op het tabblad [!UICONTROL References] in de pagina [!UICONTROL Properties] van een element worden de lokale en externe referenties van het element weergegeven.

Ga als volgt te werk om verwijzingen bij de [!DNL Assets]-implementatie weer te geven en te beheren:

1. Selecteer een element in [!DNL Assets] Console en klik **[!UICONTROL Properties]** van de toolbar.
1. Klik op het tabblad **[!UICONTROL References]**. Zie **[!UICONTROL Local References]** voor gebruik van het element op de [!DNL Assets]-implementatie. Zie **[!UICONTROL Remote References] voor gebruik van het middel op [!DNL Sites] plaatsing waar het middel werd gehaald gebruikend de Verbonden functionaliteit van Activa.

   ![Externe verwijzingen op de pagina Eigenschappen van element](assets/connected-assets-remote-reference.png)

1. De verwijzingen voor [!DNL Sites] pagina&#39;s tonen totaal aantal verwijzingen voor elke lokale [!DNL Sites]. Het kan enige tijd duren om alle verwijzingen te vinden en het totale aantal verwijzingen te tonen.
1. De lijst met verwijzingen is interactief en DAM-gebruikers kunnen op een verwijzing klikken om de verwijzingspagina te openen. Als de verre verwijzingen niet om één of andere reden kunnen worden gehaald, wordt een bericht getoond op de hoogte brengend van de mislukking.
1. Gebruikers kunnen het element verplaatsen of verwijderen. Wanneer u een element verplaatst of verwijdert, wordt het totale aantal referenties van alle geselecteerde elementen/mappen weergegeven in een waarschuwingsvenster. Wanneer u een element verwijdert waarvan de referenties nog niet worden weergegeven, wordt een waarschuwingsvenster weergegeven.

   ![waarschuwing forceren verwijderen](assets/delete-referenced-asset.png)

## Beperkingen en aanbevolen procedures {#tip-and-limitations}

* Om inzicht in activagebruik te krijgen, vorm [de functionaliteit van het Inzicht van Activa](/help/assets/assets-insights.md) op [!DNL Sites] instantie.

### Machtigingen en middelenbeheer {#permissions-and-managing-assets}

* Lokale assets worden niet gesynchroniseerd met de oorspronkelijke assets op de externe implementatie. Eventuele bewerkingen, verwijderingen of intrekkingen van machtigingen voor de DAM-implementatie worden niet verderop in de DAM-implementatie doorgegeven.
* Lokale assets zijn alleen-lezen kopieën. [!DNL Experience Manager] componenten bewerken niet-destructieve elementen in elementen. Andere soorten bewerkingen zijn niet toegestaan.
* Lokaal opgehaalde assets zijn alleen beschikbaar voor authoring. Workflows voor het bijwerken van assets kunnen niet worden toegepast en metadata kunnen niet worden bewerkt.
* Alleen afbeeldingen en de vermelde documentindelingen worden ondersteund. Inhoudsfragmenten en ervaringsfragmenten worden niet ondersteund.
* [!DNL Experience Manager] haalt niet de meta-gegevensschema&#39;s. Dit betekent dat mogelijk niet alle opgehaalde metagegevens worden weergegeven. Als het schema afzonderlijk wordt bijgewerkt, worden alle eigenschappen weergegeven.
* Alle [!DNL Sites] auteurs hebben leestemmingen op de opgehaalde exemplaren, zelfs als de auteurs tot de verre plaatsing DAM niet kunnen toegang hebben.
* Geen API-ondersteuning om de integratie aan te passen.
* De functionaliteit ondersteunt naadloos zoeken en gebruiken van externe assets. Als u veel externe assets in één keer beschikbaar wilt maken voor lokale implementatie, kunt u overwegen om de assets te migreren.
* Het is niet mogelijk om een extern middel als paginaminiatuur in [!UICONTROL Page Properties] gebruikersinterface te gebruiken. U kunt een miniatuur van een webpagina instellen in de [!UICONTROL Page Properties]-gebruikersinterface van [!UICONTROL Thumbnail] door op [!UICONTROL Select Image] te klikken.

### Installatie en licenties {#setup-licensing}

* [!DNL Assets] implementatie op  [!DNL Adobe Managed Services] wordt ondersteund.
* [!DNL Sites] kan tegelijkertijd verbinding maken met één  [!DNL Assets] opslagplaats.
* Een licentie van [!DNL Assets] die als externe opslagruimte werkt.
* Een of meer licenties van [!DNL Sites] die als lokale ontwerpimplementatie werken.

### Gebruik {#usage}

* Gebruikers kunnen tijdens het ontwerpen zoeken naar externe elementen en deze naar de lokale pagina slepen. Er wordt geen andere functionaliteit ondersteund.
* Voor ophaalbewerkingen geldt een time-out na 5 seconden. Auteurs kunnen problemen ervaren bij het ophalen van assets, bijvoorbeeld als er netwerkproblemen optreden. Auteurs kunnen opnieuw proberen door het externe element van [!UICONTROL Content Finder] naar [!UICONTROL Page Editor] te slepen.
* Eenvoudige bewerkingen die niet-destructief zijn en bewerkingen die worden ondersteund via de `Image`-component van , kunnen worden uitgevoerd op opgehaalde elementen. Assets zijn alleen-lezen.
* De enige methode om het element opnieuw op te halen is het op een pagina te slepen. Er is geen API-ondersteuning of andere methoden om middelen opnieuw op te halen om deze bij te werken.
* Als de activa van DAM worden ontmanteld, blijven die op [!DNL Sites] pagina&#39;s in gebruik.
* De externe referentie-items van een element worden asynchroon opgehaald. De verwijzingen en het totale aantal zijn niet in echt - tijd en er kan één of ander verschil zijn als een [!DNL Sites] auteur het element gebruikt terwijl een DAM gebruiker de verwijzing bekijkt. DAM-gebruikers kunnen de pagina vernieuwen en het totaalaantal over een paar minuten opnieuw proberen.

## Problemen oplossen {#troubleshoot}

Ga als volgt te werk om algemene fouten op te lossen:

* Als u niet naar verre activa van [!UICONTROL Content Finder] kunt zoeken, dan zorg ervoor dat de vereiste rollen en de toestemmingen op zijn plaats zijn.

* Een middel dat van verre DAM wordt gehaald kan niet op een Web-pagina om één of meerdere redenen worden gepubliceerd. Het bestaat niet op verre server, gebrek aan aangewezen toestemmingen om het te halen, of de netwerkmislukking kan de redenen zijn. Zorg ervoor dat het element niet wordt verwijderd van de externe DAM. Zorg ervoor dat de juiste machtigingen zijn ingesteld en dat aan de voorwaarden is voldaan. Voeg het element opnieuw toe aan de pagina en publiceer het opnieuw. Controleer de [lijst met asynchrone taken](/help/operations/asynchronous-jobs.md) op fouten bij het ophalen van assets.

* Als u geen toegang kunt krijgen tot de externe DAM-implementatie vanaf de lokale [!DNL Sites]-implementatie, moet u ervoor zorgen dat cookies die naar andere sites verwijzen, zijn toegestaan en dat [ondersteuning voor dezelfde sitecookie](/help/security/same-site-cookie-support.md) is geconfigureerd. Als cookies die naar andere sites verwijzen, worden geblokkeerd, wordt de implementatie van [!DNL Experience Manager] mogelijk niet geverifieerd. [!DNL Google Chrome] in Incognito-modus kan cookies van derden bijvoorbeeld blokkeren. Als u cookies wilt toestaan in de browser [!DNL Chrome], klikt u op het pictogram &#39;oog&#39; in de adresbalk, navigeert u naar **Site niet werken** > **Geblokkeerd**, selecteert u de externe DAM-URL en staat u aanmeldtoken-cookie toe. Afwisselend, zie [hoe te om derdekoekjes toe te laten](https://support.google.com/chrome/answer/95647).

   ![Cookie-fout in Chrome-browser in Incognito-modus](assets/chrome-cookies-incognito-dialog.png)

* Als externe referenties niet worden opgehaald en een foutbericht opleveren, controleert u of de [!DNL Sites]-implementatie beschikbaar is en controleert u op problemen met de netwerkconnectiviteit. Probeer het later opnieuw om te controleren. [!DNL Assets] de plaatsing probeert tweemaal om verbinding met  [!DNL Sites] plaatsing te vestigen en dan een mislukking meldt.

   ![fout bij ophalen externe elementverwijzingen](assets/reference-report-failure.png)
