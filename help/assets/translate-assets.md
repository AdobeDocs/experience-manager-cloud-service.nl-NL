---
title: Digitale middelen maken en beheren in meerdere talen
description: Leer hoe u workflows automatiseert voor het vertalen van elementen, waaronder binaire bestanden, metagegevens en tags in meerdere talen.
contentOwner: AG
feature: Beheer van bedrijfsmiddelen, vertaling
role: Admin,User
exl-id: 98df1412-a957-48a3-81c2-7dfe1d5e6d31
source-git-commit: 4be76f19c27aeab84de388106a440434a99a738c
workflow-type: tm+mt
source-wordcount: '2440'
ht-degree: 19%

---

# Meertalige activa {#multilingual-assets}

Meertalige elementen zijn elementen met binaire getallen, metagegevens en tags in meerdere talen. Over het algemeen bestaan binaire bestanden, metagegevens en tags voor elementen in één taal, die vervolgens naar andere talen worden vertaald voor gebruik in meertalige projecten. Met Adobe Experience Manager Assets kunt u vertaalworkflows automatiseren voor middelen (inclusief binaire bestanden, metagegevens en tags) om elementen in andere talen te genereren voor gebruik in meertalige projecten.

Om vertaalworkflows te automatiseren, integreert u de leveranciers van vertaaldiensten met Experience Manager en creeert projecten voor het vertalen van activa in veelvoudige talen. Experience Manager ondersteunt workflows voor het vertalen van mensen en machines.

Menselijke vertaling: De vertaalde elementen worden geretourneerd en in Experience Manager geïmporteerd. Wanneer uw vertaalbureau met Experience Manager wordt geïntegreerd, worden de activa automatisch verzonden tussen Experience Manager en de vertaalleverancier.

Machinevertaling: De vertaalservice zet de metagegevens en tags voor elementen direct om.

<!--
We have multiple articles around translation of assets. For now, dumping all content in this article to remove others and create only ONE UBER article.

https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/translation-projects.html
https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/preparing-assets-for-translation.html
[Apply translation cloud services to folders](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/transition-cloud-services.html)

One of these articles is a copy of [Preparing Content for Translation](https://experienceleague.adobe.com/docs/experience-manager-65/administering/introduction/tc-prep.html

-->

<!-- 
Translating assets includes the following:

1. [Connecting Experience Manager with the translation service provider](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider)
1. [Creating translation integration framework configurations](/help/sites-administering/tc-tic.md)
1. [Preparing assets for translation](prepare-assets-for-translation.md)
1. [Applying translation cloud services to folders](transition-cloud-services.md)
1. [Create translation projects](translation-projects.md)

If your translation service provider does not provide a connector to integrate with Experience Manager, use an [alternative process](/help/sites-administering/tc-manage.md#exporting-a-translation-job).

Also see, [Creating translation projects for content fragments](creating-translation-projects-for-content-fragments.md).

-->

## Elementen voorbereiden voor vertaling {#prepare-assets-for-translation}

Meertalige elementen zijn elementen met binaire getallen, metagegevens en tags in meerdere talen. Over het algemeen bestaan binaire bestanden, metagegevens en tags voor elementen in één taal, die vervolgens naar andere talen worden vertaald voor gebruik in meertalige projecten.

In Adobe Experience Manager Assets worden meertalige middelen opgenomen in mappen, waarbij elke map de middelen in een andere taal bevat.

Elke taalmap wordt een taalkopie genoemd. De hoofdmap van een taalkopie, de hoofdmap van de taal genoemd, identificeert de taal van de inhoud in de taalkopie. `/content/dam/it` is bijvoorbeeld de Italiaanse hoofdtaal voor de Italiaanse taalkopie. De exemplaren van de taal moeten [correct-gevormde taalwortel](#create-a-language-root) gebruiken zodat de correcte taal wordt gericht wanneer de vertalingen van bronactiva worden uitgevoerd.

De taalkopie waarvoor u oorspronkelijk elementen toevoegt, is de primaire taal. De primaire taal is de bron die in andere talen wordt vertaald. Een voorbeeld van een maphiërarchie bevat verschillende taalwortels:

```shell
/content
    /- dam
        |- en
        |- fr
        |- de
        |- es
        |- it
        |- ja
        |- zh
```

Voer de volgende stappen uit om uw middelen voor vertaling voor te bereiden:

1. Maak de hoofdtaalhoofdmap van uw primaire taal. De hoofdmap van de Engelse taalkopie in de hiërarchie van de voorbeeldmap is bijvoorbeeld `/content/dam/en`. Zorg ervoor dat de taalwortel correct volgens de informatie in [creeer een taalwortel](#create-a-language-root) wordt gevormd.

1. Voeg middelen toe aan uw primaire taal.
1. Creeer de taalwortel van elke doeltaal waarvoor u een taalexemplaar vereist.

### Een hoofdmap voor talen maken {#create-a-language-root}

Als u de hoofdmap van de taal wilt maken, maakt u een map en gebruikt u een ISO-taalcode als waarde voor de eigenschap Naam. Nadat u de hoofdtaal hebt gemaakt, kunt u op elk niveau in de hoofdmap van de taal een kopie van de taal maken.

De basispagina van de Italiaanse taalkopie van de voorbeeldhiërarchie heeft bijvoorbeeld `it` als eigenschap Name. Het bezit van de Naam wordt gebruikt als naam van de activaknoop in de bewaarplaats, en bepaalt daarom de weg van de activa. (*&lt;server>:&lt;port>/assets.html/content/dam/it/*)

1. Klik of tik op de assetconsole op **[!UICONTROL Create]** en kies **[!UICONTROL Folder]** in het menu.
1. Typ in het veld Naam de landcode in de notatie `<language-code>`.
1. Klik of tik **[!UICONTROL Create]**. De taalwortel wordt gecreeerd in de console van Activa.

### Taalwortels weergeven {#view-language-roots}

De interface met geoptimaliseerde aanrakingen biedt een paneel Referenties met een lijst met taalwortels die zijn gemaakt in [!DNL Assets].

1. Selecteer in de middelenconsole de primaire taal waarvoor u taalkopieën wilt maken.
1. Klik of tik op het pictogram GlobalNav en kies **[!UICONTROL References]** om het paneel Referentie te openen.
1. Klik of tik op **[!UICONTROL Language Copies]** in het venster Referenties. In het deelvenster Taalkopieën worden de taalkopieën van de elementen weergegeven.

### Een nieuw vertaalproject maken {#create-a-new-translation-project}

Als u deze optie gebruikt, worden de te vertalen middelen gekopieerd aan de taalwortel van de taal waaraan u wilt vertalen. Afhankelijk van de opties u kiest, wordt een vertaalproject gecreeerd voor de activa in de console van Projecten. Afhankelijk van de instellingen kan het vertaalproject handmatig worden gestart of automatisch worden uitgevoerd zodra het vertaalproject is gemaakt.

1. Selecteer in de interface Elementen de bronmap waarvoor u een taalkopie wilt maken.
1. Open het deelvenster **[!UICONTROL References]** en klik of tik op **[!UICONTROL Language Copies]** onder **[!UICONTROL Copies]**.
1. Klik/tik **[!UICONTROL Create & Translate]** bij de bodem.
1. Selecteer in de lijst **[!UICONTROL Target Languages]** de taal of talen waarvoor u een mappenstructuur wilt maken.
1. Selecteer **[!UICONTROL Create a new translation project]** in de lijst **[!UICONTROL Project]**.
1. Voer in het veld **[!UICONTROL Project Title]** een titel in voor het project.
1. Klik/tik op **[!UICONTROL Create]**. Middelen uit de bronmap worden gekopieerd naar de doelmappen voor de landinstellingen die u in stap 4 hebt geselecteerd.
1. Als u naar de map wilt navigeren, selecteert u de taalkopie en klikt u op **[!UICONTROL Reveal in Assets]**.
1. Navigeer aan de console van Projecten. De vertaalomslag wordt gekopieerd aan de console van Projecten.
1. Open de map om het vertaalproject weer te geven.
1. Klik of tik op het project om de detailpagina te openen.
1. Klik op de ellips onder aan de tegel **[!UICONTROL Translation Job]** om de status van de vertaaltaak weer te geven. <!-- For more details around job statuses, see [Monitoring the Status of a Translation Job](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job). -->
1. Open in de gebruikersinterface Elementen de pagina Eigenschappen voor elk van de vertaalde elementen om de vertaalde metagegevens weer te geven.

>[!NOTE]
>
>Deze functie is beschikbaar voor zowel elementen als mappen. Wanneer een middel in plaats van een omslag wordt geselecteerd, wordt de volledige hiërarchie van omslagen tot de taalwortel gekopieerd om een taalexemplaar voor de activa tot stand te brengen.

### Toevoegen aan een bestaand vertaalproject {#add-to-existing-translation-project}

Als u deze optie gebruikt, wordt de vertaalworkflow uitgevoerd voor elementen die u na een vorige vertaalworkflow aan de bronmap toevoegt. Alleen de nieuw toegevoegde elementen worden gekopieerd naar de doelmap die eerder vertaalde elementen bevat. In dit geval wordt geen nieuw vertaalproject opgezet.

1. Navigeer in de interface Elementen naar de bronmap die niet-vertaalde elementen bevat.
1. Selecteer een asset die u wilt vertalen en open het **[!UICONTROL Reference pane]**. In de sectie **[!UICONTROL Language Copies]** wordt het aantal momenteel beschikbare vertaalkopieën weergegeven.
1. Klik of tik op **[!UICONTROL Language Copies]** onder **[!UICONTROL Copies]**. Er wordt een lijst met beschikbare vertaalkopieën weergegeven.
1. Klik/tik **[!UICONTROL Create & Translate]** bij de bodem.
1. Selecteer in de lijst **[!UICONTROL Target Languages]** de taal of talen waarvoor u een mappenstructuur wilt maken.
1. Selecteer in de lijst **[!UICONTROL Project]** de optie **[!UICONTROL Add to existing translation project]** om de vertaalworkflow in de map uit te voeren.
   >[!NOTE]
   >
   >Als u de optie **[!UICONTROL Add to existing translation project]** kiest, wordt uw vertaalproject toegevoegd aan een reeds bestaand project slechts als uw projectmontages precies de montages van het reeds bestaande project aanpassen. Anders wordt een nieuw project gemaakt.
1. Selecteer in de lijst **[!UICONTROL Existing translation project]** een project om het element voor vertaling toe te voegen.
1. Klik of tik op **[!UICONTROL Create]**. De te vertalen assets worden toegevoegd aan de doelmap. De bijgewerkte map wordt weergegeven onder de sectie **[!UICONTROL Language Copies]**.
1. Navigeer aan de console van Projecten, en open het bestaande vertaalproject u aan toevoegde.
1. Klik/tik de mening van het vertaalproject de pagina van projectdetails.
1. Klik/tik de ellips bij de bodem van **Vertaalbaan** tegel om de activa in het vertaalwerkschema te bekijken. In de lijst met vertaaltaken worden ook items voor metagegevens en tags van elementen weergegeven. Deze vermeldingen geven aan dat de metagegevens en tags voor de elementen ook worden vertaald.

   >[!NOTE]
   >
   >* Als u het item voor tags of metagegevens verwijdert, worden er geen tags of metagegevens voor de elementen omgezet.
   >* Als u Machine Translation gebruikt, worden binaire bestanden met elementen niet vertaald.
   >* Als het element dat u toevoegt aan de vertaaltaak subelementen bevat, selecteert u de subelementen en verwijdert u deze zodat de vertaling zonder scheuren kan worden uitgevoerd.


1. Als u de vertaling voor de elementen wilt starten, klikt of tikt u op de pijl op de **[!UICONTROL Translation Job]**-tegel en selecteert u **[!UICONTROL Start]** in de lijst. Een bericht brengt het begin van de vertaalbaan op de hoogte.
1. Als u de status van de vertaaltaak wilt weergeven, klikt of tikt u op de ellips onder aan de tegel **[!UICONTROL Translation Job]**. <!-- For more details, see [Monitoring the Status of a Translation Job](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job). -->
1. Nadat de vertaling is voltooid, verandert de status in Ready to Review. Navigeer naar de interface Middelen en open de pagina Eigenschappen voor elk van de vertaalde elementen om de vertaalde metagegevens weer te geven.

### Taalkopieën bijwerken {#update-language-copies}

Voer deze workflow uit om extra elementen te vertalen en deze op te nemen in een taalkopie voor een bepaalde landinstelling. In dit geval worden de vertaalde elementen toegevoegd aan de doelmap die al eerder vertaalde elementen bevat. Afhankelijk van de keuze van opties wordt een vertaalproject gemaakt of wordt een bestaand vertaalproject bijgewerkt voor de nieuwe elementen. De workflow voor het kopiëren van de taal Bijwerken bevat de volgende opties:

* Een nieuw vertaalproject maken
* Toevoegen aan bestaand vertaalproject

### Toevoegen aan bestaand vertaalproject {#add-to-existing-translation-project-1}

Als u deze optie gebruikt, worden de elementen toegevoegd aan een bestaand vertaalproject en wordt de taalkopie bijgewerkt voor de landinstelling die u kiest.

1. Selecteer in de interface Middelen de bronmap waaraan u een elementmap hebt toegevoegd.
1. Open de pagina **[!UICONTROL References pane]** en klik of tik op **[!UICONTROL Language Copies]** onder **[!UICONTROL Copies]** om de lijst met taalkopieën weer te geven.
1. Schakel het selectievakje voor **[!UICONTROL Language Copies]** in om alle taalkopieën te selecteren. Hef de selectie van andere kopieën op, met uitzondering van de taalkopieën die overeenkomen met de landinstellingen waarnaar u wilt vertalen.
1. Klik/tik **[!UICONTROL Update language copies]** bij de bodem.
1. Kies in de lijst **[!UICONTROL Project]** de optie **[!UICONTROL Add to existing translation project]**.
1. Selecteer in de lijst **[!UICONTROL Existing translation project]** een project om het element voor vertaling toe te voegen.
1. Klik of tik op **[!UICONTROL Start]**.
1. Zie stappen 9-14 van [Toevoegen aan bestaand vertaalproject](#add-to-existing-translation-project) om de rest van de procedure te voltooien.

### Tijdelijke taalkopieën maken {#creating-temporary-language-copies}

Wanneer u een vertaalworkflow uitvoert om een taalkopie bij te werken met bewerkte versies van de originele elementen, blijft de bestaande taalkopie behouden totdat u de vertaalde elementen goedkeurt. [!DNL Assets] Hiermee slaat u de nieuw vertaalde middelen op een tijdelijke locatie op en werkt u de bestaande taalkopie bij nadat u de middelen expliciet hebt goedgekeurd. Als u de middelen afwijst, blijft de taalkopie ongewijzigd.

1. Klik of tik op de hoofdmap van de bron onder **[!UICONTROL Language Copies]** waarvoor u al een taalkopie hebt gemaakt, en klik of tik vervolgens op **[!UICONTROL Reveal in Assets]** om de map te openen in [!DNL Assets].
1. Selecteer in de interface Elementen een element dat u al hebt vertaald en klik op het pictogram **[!UICONTROL Edit]** op de werkbalk om het element te openen in de bewerkingsmodus.
1. Bewerk het element en sla de wijzigingen op.
1. Voer stap 2-14 van [Add aan bestaand vertaalproject](#add-to-existing-translation-project) procedure uit om het taalexemplaar bij te werken.
1. Klik/tik de ellips bij de bodem van de **[!UICONTROL Translation Job]** tegel. Uit de lijst met elementen op de pagina **[!UICONTROL Translation Job]** kunt u duidelijk de tijdelijke locatie weergeven waar de vertaalde versie van het element is opgeslagen.
1. Schakel het selectievakje naast **[!UICONTROL Title]** in.
1. Klik of tik op de werkbalk op **[!UICONTROL Accept Translation]** en klik of tik vervolgens op **[!UICONTROL Accept]** in het dialoogvenster om de vertaalde asset in de doelmap te overschrijven met de vertaalde versie van de bewerkte asset.

   >[!NOTE]
   >
   >Accepteer zowel het element als de metagegevens om de vertaalworkflow in staat te stellen het doelmiddel bij te werken.

   Klik/tik **[!UICONTROL Reject Translation]** om de oorspronkelijk vertaalde versie van het element in de hoofdmap van de doellandinstelling te behouden en de bewerkte versie af te wijzen.

1. Navigeer naar de middelenconsole en open de pagina Eigenschappen voor elk van de vertaalde elementen om de vertaalde metagegevens weer te geven.

<!-- TBD: Possibly this blog wasn't migrated. Still try to find from the author. Old one is archived at https://web.archive.org/web/20180423042713/https://blogs.adobe.com/experiencedelivers/experience-management/translate_aemassets_metadata/

For tips on translating metadata for assets efficiently, see [5 Steps to efficiently translate metadata](https://blogs.adobe.com/experiencedelivers/experience-management/translate_aemassets_metadata/). 
-->

## Vertaalprojecten maken {#creating-translation-projects}

Als u een kopie van de taal wilt maken, activeert u een van de volgende workflows voor het kopiëren van de taal die beschikbaar zijn onder de References-rail in de interface Elementen:

**Maken en vertalen**

In deze workflow worden elementen die moeten worden vertaald, gekopieerd naar de hoofdtaal van de taal waarnaar u wilt vertalen. Bovendien wordt, afhankelijk van de opties u kiest, een vertaalproject gecreeerd voor de activa in de console van Projecten. Afhankelijk van de instellingen kan het vertaalproject handmatig worden gestart of automatisch worden uitgevoerd zodra het vertaalproject is gemaakt.

**Taalkopieën bijwerken**

U voert deze workflow uit om een extra groep elementen te vertalen en deze op te nemen in een taalkopie voor een bepaalde landinstelling. In dit geval worden de vertaalde elementen toegevoegd aan de doelmap die al eerder vertaalde elementen bevat.

>[!NOTE]
>
>De binaire boeken van activa worden vertaald slechts als de vertaaldienstverlener de vertaling van binaire getallen steunt.

>[!NOTE]
>
>Als u een vertaalworkflow start voor complexe elementen, zoals PDF-bestanden en Adobe InDesign-bestanden, worden de submiddelen of vertoningen (indien aanwezig) van die elementen niet verzonden voor vertaling.

### Workflow maken en vertalen {#create-and-translate-workflow}

Met de workflow Maken en vertalen kunt u voor het eerst voor een bepaalde taal een kopie van de taal genereren. De workflow bevat de volgende opties:

* Alleen structuur maken
* Een nieuw vertaalproject maken
* Toevoegen aan bestaand vertaalproject

### Alleen structuur maken {#create-structure-only}

Met de optie **Alleen structuur maken** kunt u een doelmaphiërarchie in de hoofdmap van de doeltaal maken die overeenkomt met de hiërarchie van de bronmap in de hoofdmap van de brontaal. In dit geval worden bronassets naar de doelmap gekopieerd. Er wordt echter geen vertaalproject gegenereerd.

1. Selecteer in de interface Elementen de bronmap waarvoor u een structuur wilt maken in de hoofdmap van de doeltaal.
1. Open het deelvenster **[!UICONTROL References]** en klik of tik op **[!UICONTROL Language Copies]** onder **[!UICONTROL Copies]**.
1. Klik/tik **[!UICONTROL Create & Translate]** bij de bodem.
1. Selecteer in de lijst **[!UICONTROL Target Languages]** de taal waarvoor u een mapstructuur wilt maken.
1. Kies in de lijst **[!UICONTROL Project]** de optie **[!UICONTROL Create structure only]**.
1. Klik of tik op **[!UICONTROL Create]**. De nieuwe structuur voor de doeltaal wordt vermeld onder **[!UICONTROL Language Copies]**.
1. Klik/tik de structuur van de lijst, en klik dan **[!UICONTROL Reveal in Assets]** om aan de omslagstructuur binnen de doeltaal te navigeren.

## Vertaalcloudservices toepassen op mappen {#applying-translation-cloud-services-to-folders}

Met Adobe Experience Manager kunt u vertaalservices in de cloud gebruiken van het vertaalbureau van uw keuze om ervoor te zorgen dat uw middelen op basis van uw vereisten worden vertaald.

U kunt de vertaalcloudservice rechtstreeks toepassen op de map met middelen, zodat u deze kunt gebruiken tijdens vertaalworkflows.

### Vertaalservices toepassen {#applying-the-translation-services}

Als u de vertaalcloud-services rechtstreeks toepast op uw map met middelen, hoeft u geen vertaalservices te configureren wanneer u vertaalworkflows maakt of bijwerkt.

1. Selecteer in de gebruikersinterface Middelen de map waarop u vertaalservices wilt toepassen.
1. Klik of tik op het pictogram **[!UICONTROL Properties]** op de werkbalk om de pagina **[!UICONTROL Folder Properties]** weer te geven.

   ![chlimage_1-215](assets/chlimage_1-215.png)

1. Ga naar het tabblad **[!UICONTROL Cloud Services]**.
1. Kies in de lijst Configuraties van Cloud Servicen de gewenste vertaalprovider. Als u bijvoorbeeld vertaalservices wilt gebruiken vanuit Microsoft, kiest u **[!UICONTROL Microsoft Translator]**.

   ![chlimage_1-216](assets/chlimage_1-216.png)

1. Kies de connector voor de vertaalprovider.

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. Klik of tik op de werkbalk op **[!UICONTROL Save]** en klik vervolgens op **[!UICONTROL OK]** om het dialoogvenster te sluiten. De vertaalservice wordt toegepast op de map.

### Aangepaste vertaalaansluiting toepassen {#applying-custom-translation-connector}

Als u een aangepaste connector wilt toepassen voor de vertaalservices die u wilt gebruiken in vertaalworkflows. Om een aangepaste connector toe te passen installeert u eerst de connector vanaf Package Manager. Vervolgens configureert u de connector vanaf de Cloud Services-console. Nadat u de connector hebt geconfigureerd, is deze beschikbaar in de lijst met connectors op het tabblad Cloud Services die wordt beschreven in [De vertaalservices toepassen](#applying-the-translation-services). Nadat u de aangepaste connector hebt toegepast en vertaalworkflows hebt uitgevoerd, geeft de tegel **[!UICONTROL Translation Summary]** van het vertaalproject de connectordetails weer onder de koppen **[!UICONTROL Provider]** en **[!UICONTROL Method]**.

1. Installeer de connector via Package Manager.
1. Klik/tik het embleem van de Experience Manager, en navigeer aan **[!UICONTROL Tools > Deployment > Cloud Services]**.
1. Zoek de connector die u onder de pagina **[!UICONTROL Third Party Services]** in de **[!UICONTROL Cloud Services]** hebt geïnstalleerd.

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. Klik op de koppeling **[!UICONTROL Configure now]** of tik op deze koppeling om het dialoogvenster **[!UICONTROL Create Configuration]** te openen.

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. Geef een titel en een naam op voor de connector en klik of tik vervolgens op **[!UICONTROL Create]**. De aangepaste connector is beschikbaar in de lijst met connectors op het tabblad **[!UICONTROL Cloud Services]** zoals beschreven in stap 5 van [De vertaalservices toepassen](#applying-the-translation-services).
1. Voer een vertaalworkflow uit die in het maken van vertaalprojecten wordt beschreven nadat u de aangepaste connector hebt toegepast. Verifieer de details van de connector in de tegel **[!UICONTROL Translation Summary]** van het vertaalproject in de **[!UICONTROL Projects]**-console.

   ![chlimage_1-220](assets/chlimage_1-220.png)
