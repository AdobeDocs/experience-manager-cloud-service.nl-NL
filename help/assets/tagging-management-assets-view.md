---
title: Hoe kan ik tags beheren in de weergave Elementen?
description: Leer hoe u tags beheert in de weergave Middelen. Met tags kunt u elementen categoriseren waarin u efficiënter kunt bladeren en zoeken.
exl-id: 7c5e1212-054f-46ca-9982-30e40b0482e1
feature: Smart Tags
role: User, Admin, Developer
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '1712'
ht-degree: 0%

---

# Tags beheren in de weergave Elementen {#view-assets-and-details}


>[!CONTEXTUALHELP]
>id="assets_taxonomy_management"
>title="Tags beheren"
>abstract="Met tags kunt u elementen categoriseren waarin u efficiënter kunt bladeren en zoeken. Beheerders kunnen de hiërarchische coderingsstructuur gebruiken, die het toepassen van relevante metagegevens, het indelen van elementen, het ondersteunen van zoeken, het hergebruiken van tags, het verbeteren van de ontdekkingsmogelijkheden, enzovoort, vergemakkelijkt."

Met tags kunt u elementen categoriseren waarin u efficiënter kunt bladeren en zoeken. Tags helpen andere gebruikers en workflows de juiste taxonomie te geven.

Vlakke lijsten met gecontroleerde woordenboeken kunnen in de loop der tijd onbeheersbaar worden. Beheerders kunnen de hiërarchische coderingsstructuur gebruiken, die het toepassen van relevante metagegevens, het indelen van elementen, het ondersteunen van zoeken, het hergebruiken van tags, het verbeteren van de ontdekkingsmogelijkheden, enzovoort, vergemakkelijkt.

U kunt een naamruimte maken op hoofdniveau en een hiërarchische structuur van subtags maken binnen de naamruimte. U kunt bijvoorbeeld een `Activities` naamruimte op hoofdniveau en `Cycling`, `Hiking`, en `Running` -tags binnen de naamruimte. U kunt nog meer subtags hebben `Clothing` en `Shoes` binnen `Running`.

![Tagbeheer](assets/tags-hierarchy.png)

Tags bieden veel voordelen, zoals:

* Door middel van tags kunnen auteurs op eenvoudige wijze verschillende elementen ordenen via een gemeenschappelijke taxonomie. Auteurs kunnen snel elementen zoeken en ordenen aan de hand van algemene tags.

* Hiërarchische tags zijn uiterst flexibel en vormen een uitstekende manier om termen op een logische manier te ordenen. Via naamruimten, codes en subcodes kunnen volledige taxonomische systemen worden weergegeven.

* Tags kunnen in de loop der tijd evolueren als een organisatorische woordenwisseling.

* Tags die in de beheerweergave worden beheerd, blijven synchroon met de tags die in de middelenweergave worden beheerd. Hierdoor zijn governance en integriteit van de metagegevens gegarandeerd.

Als u tags wilt toepassen op elementen, moet u eerst een naamruimte maken en er vervolgens tags aan toevoegen. U kunt ook tags maken en deze toevoegen aan een bestaande naamruimte. Alle tags die u maakt op hoofdniveau, worden automatisch toegevoegd aan de naamruimte Standaardtags. Vervolgens kunt u het veld Codes toevoegen aan het metagegevensformulier, zodat het wordt weergegeven op de pagina met gegevens over elementen. Nadat u deze instellingen hebt geconfigureerd, kunt u tags toepassen op elementen.

>[!NOTE]
>
>U hoeft het veld Codes alleen aan het metagegevensformulier toe te voegen als u het standaardmetagegevensformulier niet gebruikt.

![Tagbeheer](assets/tagging-taxonomy-management.png)

Aanvullende mogelijkheden die verder gaan dan wat in dit artikel wordt vermeld, zoals tags samenvoegen, hernoemen, lokaliseren en publiceren, zijn beschikbaar in de beheerweergave.

## Een naamruimte maken {#create-a-namespace}

Een naamruimte is een container voor tags die alleen op hoofdniveau kunnen bestaan. U kunt de hiërarchische structuur van tags instellen door eerst een logische naam voor de naamruimte te definiëren. Als u geen tag toevoegt aan een van de bestaande naamruimten, wordt de tag automatisch naar de standaardlabels verplaatst.

Voer de volgende stappen uit om een naamruimte te maken:

1. Ga naar `Taxonomy Management` krachtens `Settings` om de lijst met bestaande naamruimten weer te geven. U kunt ook de datum weergeven waarop het laatst is gewijzigd, de gebruiker die de naamruimte(n) heeft gewijzigd en het aantal keren dat de tag in een element wordt gebruikt.
1. Klik op `Create Namespace`.
1. Toevoegen `Title`, `Name`, en `Description` voor de naamruimte. De invoer die u opgeeft in het dialoogvenster `Title` veld wordt boven in de hiërarchie weergegeven. In de volgende afbeelding, bijvoorbeeld: **Activiteiten** verwijst naar de titel van de naamruimte.

   ![Tagbeheer](assets/tags-hierarchy.png)

1. Klik op `Save`.

## Codes toevoegen aan een naamruimte {#add-tags-to-namespace}

Voer de volgende stappen uit om tags toe te voegen aan een naamruimte:

1. Ga naar **[!UICONTROL Taxonomy Management]**.
1. Selecteer de naamruimte en klik op `Create` om de tag op het hoogste niveau onder de naamruimte te maken. Als u een subtag wilt maken onder een tag die voorkomt in een naamruimte, selecteert u de tag en klikt u op `Create`.
   ![Hiërarchie van tags](assets/hierarchy-of-tags.png)

   In dit voorbeeld vertegenwoordigt de afbeelding aan de linkerkant de tag direct onder de naamruimte `automobile-four-wheeler` weergegeven in het dialoogvenster `Path` veld. De afbeelding aan de rechterkant is een voorbeeld van subtags die binnen een tag worden toegevoegd, omdat er meer tagnamen zijn. `jeep` en `jeep-meridian`, weergegeven in de `Path` naast de naamruimte.
1. Geef de titel, naam en beschrijving voor de tag op en klik op `Save`.


   >[!NOTE]
   >
   >* De `Title` en `Name` velden zijn verplicht terwijl de `Description` veld is optioneel.
   >* Standaard kopieert het gereedschap de tekst die u in het veld Titel typt, verwijdert het de lege spaties of speciale tekens (. &amp; / \ : * ? [ ] | &quot; %), en slaat het als Naam op.
   >* U kunt de `Title` veld later, maar `Name` is alleen-lezen.

## Codes toevoegen aan standaardcodes {#add-tags-to-standard-tags}

Niet-gestructureerde tags of tags zonder hiërarchie worden onder `Standard Tags` naamruimte. Bovendien kunt u die waarde opslaan onder `Standard Tags`. U kunt deze waarden in de loop der tijd onder gestructureerde naamruimten verplaatsen. Bovendien kunt u de opdracht `Standard Tags` naamruimte als een gratis formulieritem voor trefwoorden.

Als u een standaardcode wilt maken, klikt u op `Create Tag` op het hoofdniveau. Geef een titel, naam en beschrijving op en klik vervolgens op `Save`.

![Labels toevoegen aan standaardcodes](assets/adding-tags-to-standard-tags.png)

>[!NOTE]
>
>Als u `Standard Tags` naamruimte maken met behulp van as a Cloud Service elementen. De tags die op hoofdniveau zijn gemaakt, worden niet weergegeven in de lijst met beschikbare tags.

## Labels verplaatsen {#move-tags}

Als u de tags opslaat onder de verkeerde hiërarchie of als de taxonomie in de loop der tijd verandert, kunt u de geselecteerde tags verplaatsen om de gegevensintegriteit te behouden. Bij het verplaatsen van tags moet rekening worden gehouden met de volgende voorwaarden:

* Tags kunnen alleen onder bestaande naamruimten of binnen een bestaande taghiërarchie worden verplaatst.
* Labels kunnen niet naar het hoofdniveau worden verplaatst om een naamruimte te worden.
* Als u een bovenliggende tag verplaatst, worden ook alle onderliggende tags verplaatst die in de hiërarchie zijn opgeslagen.

Voer de volgende stappen uit om tags van de ene locatie naar de andere te verplaatsen:

1. Selecteer de tag of de volledige hiërarchie van tags onder de desbetreffende naamruimte en klik op `Move`.
1. Selecteer in het dialoogvenster Verplaatsen de nieuwe doeltag of -naamruimte met de opdracht `Select Tag` sectie.
1. Klik op `Save`. De tag wordt op de nieuwe locatie weergegeven.

## Tags bewerken {#edit-tags}

Als u de titel van de tag wilt bewerken, selecteert u de tag en klikt u op `Edit`. Geef de nieuwe titel op en klik op `Save`.

>[!NOTE]
>
>* De `Name` van een tag kan niet worden bijgewerkt. Het hoofdpad van een tag is ook gebaseerd op de naam van de tag. Het pad blijft hetzelfde, ook als u het `Title` veld.
>* Extra bewerkingen zoals samenvoegen, lokaliseren en publiceren zijn beschikbaar in as a Cloud Service elementen.

## Labels verwijderen {#delete-tags}

U kunt meerdere naamruimten of tags tegelijk verwijderen. De verwijderbewerking kan niet ongedaan worden gemaakt.

Voer de volgende stappen uit om tags te verwijderen:

1. Selecteer de naamruimte of tag en klik op `Delete`.
1. Klik op `Confirm`.

>[!NOTE]
>
>* Als u de bovenliggende tag of naamruimte verwijdert, worden ook de subtags verwijderd die in de hiërarchie zijn opgeslagen. Als u de bovenliggende naamruimte moet verwijderen of bijwerken, is het raadzaam [uw tags verplaatsen](#moving-tags) naar de nieuwe bestemming alvorens de ouderhiërarchie te schrappen.
>* Als u een tag verwijdert, worden ook alle verwijzingen uit de elementen verwijderd.
>* U kunt geen standaardlabels verwijderen die zich op het hoofdniveau bevinden.

## De component Codes toevoegen aan het formulier Metagegevens {#add-tags-to-metadata-form}

De component tags wordt toegevoegd aan de `default` automatisch een metagegevensformulier. U kunt een [Metagegevensformulier](https://experienceleague.adobe.com/docs/experience-manager-assets-essentials/help/metadata.html?lang=en#metadata-forms) met behulp van een sjabloon of helemaal opnieuw. Als u geen bestaande sjabloon voor metagegevens gebruikt, kunt u het formulier Metagegevens wijzigen en de tagcomponent toevoegen. De toewijzing van de eigenschap metadata wordt automatisch ingevuld en kan op dit moment niet worden gewijzigd. [!DNL Assets as a Cloud Service] gebruikers kunnen de toewijzing bijwerken om tagwaarden op te slaan met behulp van aangepaste naamruimten en alleen subsets van hiërarchieën toegankelijk maken met behulp van hoofdpaden.

Bekijk deze korte video om te zien hoe u de component Tags aan het metagegevensformulier kunt toevoegen:

>[!VIDEO](https://video.tv.adobe.com/v/3420452)


### Codes toevoegen aan elementen {#add-tags-to-assets}

1. Ga naar de pagina met elementdetails en navigeer naar de `Tags` sectie van het formulier Metagegevens.
1. Selecteer het tagkiezerpictogram dat naast het veld Tags staat of typ een labelnaam om de voorgestelde resultaten te zien.

   ![Tagingmiddelen](assets/adding-tags-to-assets.png)

1. Selecteer een of meer tags. De subtag wordt automatisch geselecteerd samen met de bovenliggende tag of naamruimte.
Tags die in de Assets Essentials zijn gewijzigd, worden ook in as a Cloud Service elementen toegepast.

## Codes toevoegen aan lijst van gewezen personen {#blocklist-essentials}

[!DNL Assets view] kunt u een lijst van gewezen personen configureren die woorden bevat die niet als slimme tags aan elementen moeten worden toegevoegd wanneer deze naar de opslagplaats worden geüpload. Met deze functie kunt u de naleving van het merk handhaven en de inspanningen voor het reduceren van slimme tags verminderen.
<!--
### Block smart tags for single asset {#block-smart-tags-for-single-asset}
![block smart tags](assets/block-smart-tags.png)
-->

### Slimme tags voor alle elementen blokkeren {#block-smart-tags-for-all-assets}

[!DNL Assets view] Hiermee kan een beheerder slimme tags voor de bestaande en de nieuw toegevoegde elementen blokkeren. Voer de volgende stappen uit om tags te blokkeren:

1. Navigeren naar **[!UICONTROL Blocked Tags]** krachtens **[!UICONTROL Settings]**.
1. Klik op **[!UICONTROL Add blocked tag]**.
1. Typ de tags in het tekstvak die u wilt blokkeren en klik op **[!UICONTROL Enter]**.
1. Als u klaar bent met het toevoegen van tags, klikt u op **[!UICONTROL Add]**. De ingevoerde tags worden vermeld in de lijst met geblokkeerde tags.

   >[!NOTE]
   >
   >U kunt maximaal 25 tags tegelijk aan de lijst toevoegen. Herhaal de stappen om meer markeringen aan de lijst van gewezen personen toe te voegen.

U kunt ook slimme tags voor één element blokkeren. Navigeer naar de details van een element. Onder **[!UICONTROL Tags]** , verwijdert u de ongewenste slimme tags en klikt u op **[!UICONTROL Save]**. De labels worden vermeld in de lijst van gewezen personen voor het geselecteerde element.

### Op lijst van gewezen personen uitgevoerde handelingen {#blocklist-actions}

* **Tags verwijderen:** U kunt de labels ook uit de lijst van gewezen personen verwijderen. Selecteer hiervoor een of meer tags die u wilt verwijderen. Klik op **[!UICONTROL Remove]**. U kunt maximaal 25 tags tegelijk uit de lijst verwijderen.
* **Alles selecteren:** Selecteert het selectievakje naast **Tagnaam** om alle labels in de lijst van gewezen personen te selecteren.
* **Sorteren:** U kunt de lijst van gewezen personen in oplopende of aflopende volgorde sorteren. Klik hiertoe op de pijl naast **Tagnaam**.

  ![bloklabels](assets/blocklist.gif)

  >[!NOTE]
  >
  >Gebruik geen speciale tekens wanneer u een label toevoegt aan de lijst van gewezen personen. Tekens zoals a-z, A-Z, 0-9, en - kunnen worden gebruikt.

### Lijst van gewezen personen exporteren{#export-blocklist}

In de middelenweergave kunt u de weergegeven geblokkeerde tags exporteren naar de CSV-indeling. Voer de onderstaande stappen uit om lijst van gewezen personen te exporteren:

1. Klik op **[!UICONTROL Export as CSV]**.
1. Kies de juiste locatie voor het opslaan van het CSV-bestand. U kunt de naam van het bestand ook naar wens wijzigen.
1. Klik op **[!UICONTROL Save]**. De geëxporteerde lijst in CSV-indeling wordt gedownload op de geselecteerde locatie.

### Lijst van gewezen personen importeren{#import-blocklist}

In de middelenweergave kunt u geblokkeerde tags importeren uit een gegevensbron (CSV). Voer de onderstaande stappen uit om lijst van gewezen personen te importeren:

1. Klik op **[!UICONTROL Import as CSV]**.
1. Kies het CSV-bestand van uw apparaat. Klikken **[!UICONTROL select a file]** om vanaf uw apparaat naar het bestand te navigeren. U kunt het CSV-bestand ook slepen en neerzetten vanaf het apparaat.
1. Klik op **[!UICONTROL Upload]**. De tags uit het CSV-bestand worden vermeld in de lijst met geblokkeerde tags.

   ![Lijst met geblokkeerde tags importeren](assets/import-blocked-tags.png)

Voer de onderstaande stappen uit als u een sjabloon voor geblokkeerde tags wilt downloaden:

1. Klik op **[!UICONTROL Download Template]**.
1. Kies de juiste locatie voor het opslaan van het CSV-bestand. U kunt de naam van het bestand ook naar wens wijzigen.
1. Klik op **[!UICONTROL Save]**. De bloktagsjabloon in CSV-indeling wordt gedownload op de geselecteerde locatie.
