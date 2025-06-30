---
title: Hoe kan ik tags beheren in de Assets-weergave?
description: Leer hoe u tags kunt beheren in de Assets-weergave. Met tags kunt u elementen categoriseren waarin u efficiënter kunt bladeren en zoeken.
exl-id: 7c5e1212-054f-46ca-9982-30e40b0482e1
feature: Smart Tags
role: User, Admin, Developer
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '1712'
ht-degree: 0%

---

# Tags beheren in de Assets-weergave {#view-assets-and-details}

>[!CONTEXTUALHELP]
>id="assets_taxonomy_management"
>title="Tags beheren"
>abstract="Met tags kunt u elementen categoriseren waarin u efficiënter kunt bladeren en zoeken. Beheerders kunnen de hiërarchische coderingsstructuur gebruiken, die het toepassen van relevante metagegevens, het indelen van elementen, het ondersteunen van zoeken, het hergebruiken van tags, het verbeteren van de ontdekkingsmogelijkheden, enzovoort, vergemakkelijkt."

Met tags kunt u elementen categoriseren waarin u efficiënter kunt bladeren en zoeken. Tags helpen andere gebruikers en workflows de juiste taxonomie te geven.

Vlakke lijsten met gecontroleerde woordenboeken kunnen in de loop der tijd onbeheersbaar worden. Beheerders kunnen de hiërarchische coderingsstructuur gebruiken, die het toepassen van relevante metagegevens, het indelen van elementen, het ondersteunen van zoeken, het hergebruiken van tags, het verbeteren van de ontdekkingsmogelijkheden, enzovoort, vergemakkelijkt.

U kunt een naamruimte maken op hoofdniveau en een hiërarchische structuur van subtags maken binnen de naamruimte. U kunt bijvoorbeeld een naamruimte `Activities` op hoofdniveau maken en tags `Cycling` , `Hiking` en `Running` in de naamruimte gebruiken. U kunt nog meer subtags `Clothing` en `Shoes` within `Running` gebruiken.

![ het Taggen Beheer ](assets/tags-hierarchy.png)

Tags bieden veel voordelen, zoals:

* Door middel van tags kunnen auteurs op eenvoudige wijze verschillende elementen ordenen via een gemeenschappelijke taxonomie. Auteurs kunnen snel elementen zoeken en ordenen aan de hand van algemene tags.

* Hiërarchische tags zijn uiterst flexibel en vormen een uitstekende manier om termen op een logische manier te ordenen. Via naamruimten, codes en subcodes kunnen volledige taxonomische systemen worden weergegeven.

* Tags kunnen in de loop der tijd evolueren als een organisatorische woordenwisseling.

* Tags die in de beheerweergave worden beheerd, blijven synchroon met de tags die in de Assets-weergave worden beheerd. Hierdoor zijn governance en integriteit van de metagegevens gegarandeerd.

Als u tags wilt toepassen op elementen, moet u eerst een naamruimte maken en er vervolgens tags aan toevoegen. U kunt ook tags maken en deze toevoegen aan een bestaande naamruimte. Alle tags die u maakt op hoofdniveau, worden automatisch toegevoegd aan de naamruimte Standaardtags. Vervolgens kunt u het veld Codes toevoegen aan het metagegevensformulier, zodat het wordt weergegeven op de pagina met gegevens over elementen. Nadat u deze instellingen hebt geconfigureerd, kunt u tags toepassen op elementen.

>[!NOTE]
>
>U hoeft het veld Codes alleen aan het metagegevensformulier toe te voegen als u het standaardmetagegevensformulier niet gebruikt.

![ het Taggen Beheer ](assets/tagging-taxonomy-management.png)

Aanvullende mogelijkheden die verder gaan dan wat in dit artikel wordt vermeld, zoals tags samenvoegen, hernoemen, lokaliseren en publiceren, zijn beschikbaar in de beheerweergave.

## Een naamruimte maken {#create-a-namespace}

Een naamruimte is een container voor tags die alleen op hoofdniveau kunnen bestaan. U kunt de hiërarchische structuur van tags instellen door eerst een logische naam voor de naamruimte te definiëren. Als u geen tag toevoegt aan een van de bestaande naamruimten, wordt de tag automatisch naar de standaardlabels verplaatst.

Voer de volgende stappen uit om een naamruimte te maken:

1. Ga naar `Taxonomy Management` onder `Settings` om de lijst met bestaande naamruimten weer te geven. U kunt ook de datum weergeven waarop het laatst is gewijzigd, de gebruiker die de naamruimte(n) heeft gewijzigd en het aantal keren dat de tag in een element wordt gebruikt.
1. Klik op `Create Namespace`.
1. Voeg `Title` , `Name` en `Description` toe voor de naamruimte. De invoer die u opgeeft in het veld `Title` wordt boven in de hiërarchie weergegeven. Bijvoorbeeld, in het volgende beeld, **Activiteiten** verwijst naar de titel van Namespace.

   ![ het Taggen Beheer ](assets/tags-hierarchy.png)

1. Klik op `Save`.

## Codes toevoegen aan een naamruimte {#add-tags-to-namespace}

Voer de volgende stappen uit om tags toe te voegen aan een naamruimte:

1. Ga naar **[!UICONTROL Taxonomy Management]** .
1. Selecteer de naamruimte en klik op `Create` om de tag op het hoogste niveau onder de naamruimte te maken. Als u een subtag wilt maken onder een tag in een naamruimte, selecteert u de tag en klikt u op `Create` .
   ![ Hiërarchie van Markeringen ](assets/hierarchy-of-tags.png)

   In dit voorbeeld vertegenwoordigt de afbeelding aan de linkerkant de tag direct onder de naamruimte `automobile-four-wheeler` die in het `Path` -veld wordt weergegeven. De afbeelding aan de rechterkant is een voorbeeld van subtags die binnen een tag worden toegevoegd, omdat er naast de naamruimte meer tagnamen `jeep` en `jeep-meridian` worden weergegeven in het veld `Path` .
1. Geef de titel, naam en beschrijving voor de tag op en klik op `Save` .


   >[!NOTE]
   >
   >* De velden `Title` en `Name` zijn verplicht, terwijl het veld `Description` optioneel is.
   >* Standaard kopieert het gereedschap de tekst die u in het veld Titel typt, verwijdert het de lege spaties of speciale tekens (. &amp; / \ : * ? [ ] | &quot; %), en slaat het als Naam op.
   >* U kunt het veld `Title` later bijwerken, maar het veld `Name` is alleen-lezen.

## Codes toevoegen aan standaardcodes {#add-tags-to-standard-tags}

Niet-gestructureerde tags of tags zonder hiërarchie worden opgeslagen onder naamruimte `Standard Tags` . Bovendien kunt u die waarde opslaan onder `Standard Tags` als u aanvullende beschrijvende termen wilt toevoegen zonder dat dit van invloed is op de beheerde taxonomie. U kunt deze waarden in de loop der tijd onder gestructureerde naamruimten verplaatsen. Bovendien kunt u de naamruimte `Standard Tags` gebruiken als een gratis formulieritem voor trefwoorden.

Als u een standaardcode wilt maken, klikt u op `Create Tag` op het hoofdniveau. Geef een titel, naam en beschrijving op en klik op `Save` .

![ Toevoegend markeringen aan standaardmarkeringen ](assets/adding-tags-to-standard-tags.png)

>[!NOTE]
>
>Als u naamruimte `Standard Tags` verwijdert met Assets as a Cloud Service, worden de tags die op hoofdniveau zijn gemaakt, niet weergegeven in de lijst met beschikbare tags.

## Labels verplaatsen {#move-tags}

Als u de tags opslaat onder de verkeerde hiërarchie of als de taxonomie in de loop der tijd verandert, kunt u de geselecteerde tags verplaatsen om de gegevensintegriteit te behouden. Bij het verplaatsen van tags moet rekening worden gehouden met de volgende voorwaarden:

* Tags kunnen alleen onder bestaande naamruimten of binnen een bestaande taghiërarchie worden verplaatst.
* Labels kunnen niet naar het hoofdniveau worden verplaatst om een naamruimte te worden.
* Als u een bovenliggende tag verplaatst, worden ook alle onderliggende tags verplaatst die in de hiërarchie zijn opgeslagen.

Voer de volgende stappen uit om tags van de ene locatie naar de andere te verplaatsen:

1. Selecteer de tag of de volledige hiërarchie van tags onder de desbetreffende naamruimte en klik op `Move` .
1. Selecteer in het dialoogvenster Verplaatsen de nieuwe doeltag of naamruimte met behulp van de sectie `Select Tag` .
1. Klik op `Save`. De tag wordt op de nieuwe locatie weergegeven.

## Tags bewerken {#edit-tags}

Als u de titel van de tag wilt bewerken, selecteert u de tag en klikt u op `Edit` . Geef de nieuwe titel op en klik op `Save` .

>[!NOTE]
>
>* De `Name` van een tag kan niet worden bijgewerkt. Het hoofdpad van een tag is ook gebaseerd op de naam van de tag. Het pad blijft hetzelfde, zelfs als u het veld `Title` bijwerkt.
>* Extra bewerkingen zoals samenvoegen, lokaliseren en publiceren zijn beschikbaar in Assets as a Cloud Service.

## Labels verwijderen {#delete-tags}

U kunt meerdere naamruimten of tags tegelijk verwijderen. De verwijderbewerking kan niet ongedaan worden gemaakt.

Voer de volgende stappen uit om tags te verwijderen:

1. Selecteer de naamruimte of tag en klik op `Delete` .
1. Klik op `Confirm`.

>[!NOTE]
>
>* Als u de bovenliggende tag of naamruimte verwijdert, worden ook de subtags verwijderd die in de hiërarchie zijn opgeslagen. Als u de ouder Namespace moet schrappen of bijwerken, wordt het geadviseerd om [ uw markeringen ](#moving-tags) aan de nieuwe bestemming te bewegen alvorens de ouderhiërarchie te schrappen.
>* Als u een tag verwijdert, worden ook alle verwijzingen uit de elementen verwijderd.
>* U kunt geen standaardlabels verwijderen die zich op het hoofdniveau bevinden.

## De component Codes toevoegen aan het formulier Metagegevens {#add-tags-to-metadata-form}

De tagcomponent wordt automatisch toegevoegd aan het metagegevensformulier `default` . U kunt de vorm van a [ Meta-gegevens ](https://experienceleague.adobe.com/docs/experience-manager-assets-essentials/help/metadata.html?lang=en#metadata-forms) of door een malplaatje of van kras te gebruiken ontwerpen. Als u geen bestaande sjabloon voor metagegevens gebruikt, kunt u het formulier Metagegevens wijzigen en de tagcomponent toevoegen. De toewijzing van de eigenschap metadata wordt automatisch ingevuld en kan op dit moment niet worden gewijzigd. [!DNL Assets as a Cloud Service] -gebruikers kunnen de toewijzing bijwerken om tagwaarden op te slaan met behulp van aangepaste naamruimten en alleen subsets van hiërarchieën toegankelijk maken met behulp van hoofdpaden.

Bekijk deze korte video om te zien hoe u de component Tags aan het metagegevensformulier kunt toevoegen:

>[!VIDEO](https://video.tv.adobe.com/v/3420452)


### Codes toevoegen aan Assets {#add-tags-to-assets}

1. Ga naar de pagina met elementdetails en navigeer naar de sectie `Tags` van het formulier Metagegevens.
1. Selecteer het tagkiezerpictogram dat naast het veld Tags staat of typ een labelnaam om de voorgestelde resultaten te zien.

   ![ Tags-activa ](assets/adding-tags-to-assets.png)

1. Selecteer een of meer tags. De subtag wordt automatisch geselecteerd samen met de bovenliggende tag of naamruimte.
Tags die zijn gewijzigd in de Elementen worden ook toegepast in Assets as a Cloud Service.

## Codes toevoegen aan lijst van gewezen personen {#blocklist-essentials}

Met [!DNL Assets view] kunt u een lijst van gewezen personen configureren die woorden bevat die niet als slimme tags aan elementen mogen worden toegevoegd wanneer deze naar de opslagplaats worden geüpload. Met deze functie kunt u de naleving van het merk handhaven en de inspanningen voor het reduceren van slimme tags verminderen.
<!--
### Block smart tags for single asset {#block-smart-tags-for-single-asset}
![block smart tags](assets/block-smart-tags.png)
-->

### Slimme tags voor alle elementen blokkeren {#block-smart-tags-for-all-assets}

Met [!DNL Assets view] kan een beheerder slimme tags voor de bestaande en de nieuw toegevoegde elementen blokkeren. Voer de volgende stappen uit om tags te blokkeren:

1. Navigeer naar **[!UICONTROL Blocked Tags]** onder **[!UICONTROL Settings]** .
1. Klik op **[!UICONTROL Add blocked tag]**.
1. Typ de tags in het tekstvak die u wilt blokkeren en klik op **[!UICONTROL Enter]** .
1. Als u klaar bent met het toevoegen van tags, klikt u op **[!UICONTROL Add]** . De ingevoerde tags worden vermeld in de lijst met geblokkeerde tags.

   >[!NOTE]
   >
   >U kunt maximaal 25 tags tegelijk aan de lijst toevoegen. Herhaal de stappen om meer markeringen aan de lijst van gewezen personen toe te voegen.

U kunt ook slimme tags voor één element blokkeren. Navigeer naar de details van een element. Verwijder de ongewenste slimme tags onder **[!UICONTROL Tags]** en klik op **[!UICONTROL Save]** . De labels worden vermeld in de lijst van gewezen personen voor het geselecteerde element.

### Op lijst van gewezen personen uitgevoerde handelingen {#blocklist-actions}

* **verwijder markeringen:** u kunt de markeringen uit lijst van gewezen personen ook verwijderen. Selecteer hiervoor een of meer tags die u wilt verwijderen. Klik op **[!UICONTROL Remove]**. U kunt maximaal 25 tags tegelijk uit de lijst verwijderen.
* **Uitgezocht allen:** selecteer checkbox naast **Naam van de Markering** om alle markeringen in de lijst van gewezen personen te selecteren.
* **Sorterend:** u kunt de lijst van gewezen personen in of het stijgen of dalende orde sorteren. Om dit te doen, klik pijl naast **Naam van de Markering**.

  ![ blokmarkeringen ](assets/blocklist.gif)

  >[!NOTE]
  >
  >Gebruik geen speciale tekens wanneer u een label toevoegt aan de lijst van gewezen personen. Tekens zoals a-z, A-Z, 0-9, en - kunnen worden gebruikt.

### Lijst van gewezen personen exporteren{#export-blocklist}

In de Assets-weergave kunt u de weergegeven geblokkeerde tags exporteren naar de CSV-indeling. Voer de onderstaande stappen uit om lijst van gewezen personen te exporteren:

1. Klik op **[!UICONTROL Export as CSV]**.
1. Kies de juiste locatie voor het opslaan van het CSV-bestand. U kunt de naam van het bestand ook naar wens wijzigen.
1. Klik op **[!UICONTROL Save]**. De geëxporteerde lijst in CSV-indeling wordt gedownload op de geselecteerde locatie.

### Lijst van gewezen personen importeren{#import-blocklist}

In de Assets-weergave kunt u geblokkeerde tags importeren uit een gegevensbron (CSV). Voer de onderstaande stappen uit om lijst van gewezen personen te importeren:

1. Klik op **[!UICONTROL Import as CSV]**.
1. Kies het CSV-bestand van uw apparaat. Klik op **[!UICONTROL select a file]** om vanaf uw apparaat naar het bestand te navigeren. U kunt het CSV-bestand ook slepen en neerzetten vanaf het apparaat.
1. Klik op **[!UICONTROL Upload]**. De tags uit het CSV-bestand worden vermeld in de lijst met geblokkeerde tags.

   ![ de Invoer geblokkeerde lijst van markeringen ](assets/import-blocked-tags.png)

Voer de onderstaande stappen uit als u een sjabloon voor geblokkeerde tags wilt downloaden:

1. Klik op **[!UICONTROL Download Template]**.
1. Kies de juiste locatie voor het opslaan van het CSV-bestand. U kunt de naam van het bestand ook naar wens wijzigen.
1. Klik op **[!UICONTROL Save]**. De bloktagsjabloon in CSV-indeling wordt gedownload op de geselecteerde locatie.
