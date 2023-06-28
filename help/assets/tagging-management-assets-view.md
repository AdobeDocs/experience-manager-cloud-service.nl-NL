---
title: Hoe kan ik tags beheren in de weergave Elementen?
description: Leer hoe u tags beheert in de weergave Middelen. Met tags kunt u elementen categoriseren waarin u efficiënter kunt bladeren en zoeken.
source-git-commit: bdbe47a8f06d2ec1cd75103905677fcd3955632d
workflow-type: tm+mt
source-wordcount: '1422'
ht-degree: 0%

---

# Tags beheren in de middelenweergave {#view-assets-and-details}


>[!CONTEXTUALHELP]
>id="assets_taxonomy_management"
>title="Tags beheren"
>abstract="Met tags kunt u elementen categoriseren waarin u efficiënter kunt bladeren en zoeken. Beheerders kunnen gebruikmaken van de hiërarchische coderingsstructuur, die het toepassen van relevante metagegevens, het indelen van elementen, het ondersteunen van zoeken, het hergebruiken van tags, het verbeteren van de ontdekkingsmogelijkheden enzovoort vergemakkelijkt."

Met tags kunt u elementen categoriseren waarin u efficiënter kunt bladeren en zoeken. Tags helpen andere gebruikers en workflows de juiste taxonomie te geven.

Vlakke lijsten met gecontroleerde woordenboeken kunnen in de loop der tijd onbeheersbaar worden. Beheerders kunnen gebruikmaken van de hiërarchische coderingsstructuur, die het toepassen van relevante metagegevens, het indelen van elementen, het ondersteunen van zoeken, het hergebruiken van tags, het verbeteren van de ontdekkingsmogelijkheden enzovoort vergemakkelijkt.

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

## Een naamruimte maken {#creating-a-namespace}

Een naamruimte is een container voor tags die alleen op hoofdniveau kunnen bestaan. U kunt de hiërarchische structuur van tags instellen door eerst een logische naam voor de naamruimte te definiëren. Als u geen tag toevoegt aan een van de bestaande naamruimten, wordt de tag automatisch naar de standaardlabels verplaatst.

Voer de volgende stappen uit om een naamruimte te maken:

1. Ga naar `Taxonomy Management` krachtens `Settings` om de lijst met bestaande naamruimten weer te geven. U kunt ook de datum weergeven waarop het laatst is gewijzigd, de gebruiker die de naamruimte(n) heeft gewijzigd en het aantal keren dat de tag in een element wordt gebruikt.
1. Klik op `Create Namespace`.
1. Toevoegen `Title`, `Name`, en `Description` voor de naamruimte. De invoer die u opgeeft in het dialoogvenster `Title` veld wordt boven in de hiërarchie weergegeven. In de volgende afbeelding, bijvoorbeeld **Activiteiten** verwijst naar de titel van de naamruimte.

   ![Tagbeheer](assets/tags-hierarchy.png)

   <!--
    >[!NOTE]
    >
    >You can use `Name` as a primary key if you are using any other metadata management tool is the source of truth for taxonomy values, you can use the name as a primary key.
    >
    -->

1. Klik op `Save`.

## Labels toevoegen aan een naamruimte {#adding-tags-to-namespace}

Voer de volgende stappen uit om tags toe te voegen aan een naamruimte:

1. Ga naar `Taxonomy Management`.
1. Selecteer de naamruimte en klik op `Create` om de tag op het hoogste niveau onder de naamruimte te maken. Als u een subtag wilt maken onder een tag die voorkomt in een naamruimte, selecteert u de tag en klikt u op `Create`.
   ![Hiërarchie van tags](assets/hierarchy-of-tags.png)

   In dit voorbeeld vertegenwoordigt de afbeelding aan de linkerkant de tag direct onder de naamruimte `automobile-four-wheeler` weergegeven in de `Path` veld. De afbeelding aan de rechterkant is een voorbeeld van subtags die binnen een tag worden toegevoegd, omdat er meer tagnamen zijn. `jeep` en `jeep-meridian`, weergegeven in de `Path` naast de naamruimte.
1. Geef de titel, naam en beschrijving voor de tag op en klik op `Save`.


   >[!NOTE]
   >
   >* De `Title` en `Name` velden zijn verplicht terwijl de `Description` veld is optioneel.
   >* Standaard kopieert het gereedschap de tekst die u in het veld Titel typt, verwijdert het de lege spaties of speciale tekens (. &amp; / \ : * ? [ ] | &quot; %), en slaat het als Naam op.
   >* U kunt de `Title` veld later, maar `Name` is alleen-lezen.

## Labels toevoegen aan standaardlabels {#adding-tags-to-standard-tags}

Niet-gestructureerde tags of de tags die geen hiërarchie hebben, worden opgeslagen onder `Standard Tags` naamruimte. Bovendien kunt u die waarde opslaan onder `Standard Tags`. U kunt deze waarden in de loop der tijd onder gestructureerde naamruimten verplaatsen. Bovendien kunt u de opdracht `Standard Tags` naamruimte als een gratis formulieritem voor trefwoorden.

Als u een standaardcode wilt maken, klikt u op `Create Tag` op hoofdniveau. Geef een titel, naam en beschrijving op en klik vervolgens op `Save`.

![Labels toevoegen aan standaardcodes](assets/adding-tags-to-standard-tags.png)

>[!NOTE]
>
>Als u `Standard Tags` naamruimte gebruiken in de beheerweergave. De tags die op hoofdniveau zijn gemaakt, worden niet weergegeven in de lijst met beschikbare tags.

## Labels verplaatsen {#moving-tags}

Als u de tags opslaat onder de verkeerde hiërarchie of als de taxonomie in de loop der tijd verandert, kunt u de geselecteerde tags verplaatsen om de gegevensintegriteit te behouden. Bij het verplaatsen van tags moet rekening worden gehouden met de volgende voorwaarden:

* Tags kunnen alleen onder bestaande naamruimten of binnen een bestaande taghiërarchie worden verplaatst.
* Labels kunnen niet naar het hoofdniveau worden verplaatst om een naamruimte te worden.
* Als u een bovenliggende tag verplaatst, worden ook alle onderliggende tags verplaatst die in de hiërarchie zijn opgeslagen.

Voer de volgende stappen uit om tags van de ene locatie naar de andere te verplaatsen:

1. Selecteer de tag of de volledige hiërarchie van tags onder de desbetreffende naamruimte en klik op `Move`.
1. Selecteer in het dialoogvenster Verplaatsen de nieuwe doeltag of -naamruimte met de opdracht `Select Tag` sectie.
1. Klik op `Save`. De tag wordt op de nieuwe locatie weergegeven.

## Tags bewerken {#editing-tags}

Als u de titel van de tag wilt bewerken, selecteert u de tag en klikt u op `Edit`. Geef de nieuwe titel op en klik op `Save`.

>[!NOTE]
>
>* De `Name` van een tag kan niet worden bijgewerkt. Het hoofdpad van een tag is ook gebaseerd op de naam van de tag. Het pad blijft hetzelfde, ook als u het `Title` veld.
>* Extra bewerkingen zoals samenvoegen, lokaliseren en publiceren zijn beschikbaar in de beheerweergave.

## Tags verwijderen {#deleting-tags}

U kunt meerdere naamruimten of tags tegelijk verwijderen. De verwijderbewerking kan niet ongedaan worden gemaakt.

Voer de volgende stappen uit om tags te verwijderen:

1. Selecteer de naamruimte of tag en klik op `Delete`.
1. Klik op `Confirm`.

>[!NOTE]
>
>* Als u de bovenliggende tag of naamruimte verwijdert, worden ook de subtags verwijderd die in de hiërarchie zijn opgeslagen. Als u de bovenliggende naamruimte moet verwijderen of bijwerken, is het raadzaam [uw tags verplaatsen](#moving-tags) naar de nieuwe bestemming alvorens de ouderhiërarchie te schrappen.
>* Als u een tag verwijdert, worden ook alle verwijzingen uit de elementen verwijderd.
>* U kunt geen standaardlabels verwijderen die zich op het hoofdniveau bevinden.

## De component Tags toevoegen aan het formulier Metagegevens {#adding-tags-to-metadata-form}

De component tags wordt toegevoegd aan de `default` automatisch een metagegevensformulier. U kunt een [Metagegevensformulier](https://experienceleague.adobe.com/docs/experience-manager-assets-essentials/help/metadata.html?lang=en#metadata-forms) met behulp van een sjabloon of helemaal opnieuw. Als u geen bestaande sjabloon voor metagegevens gebruikt, kunt u het formulier Metagegevens wijzigen en de tagcomponent toevoegen. De toewijzing van de eigenschap metadata wordt automatisch ingevuld en kan op dit moment niet worden gewijzigd. Gebruikers in de Admin-weergave kunnen de toewijzing bijwerken om tagwaarden op te slaan met behulp van aangepaste naamruimten en alleen subsets van hiërarchieën beschikbaar maken met behulp van hoofdpaden.

Bekijk deze korte video om te zien hoe u de component Tags aan het metagegevensformulier kunt toevoegen:

>[!VIDEO](https://video.tv.adobe.com/v/3420452)


### Labels toevoegen aan elementen {#adding-tags-to-assets}

1. Ga naar de pagina met elementdetails en navigeer naar de `Tags` sectie van het formulier Metagegevens.
1. Selecteer het tagkiezerpictogram dat naast het veld Tags staat of typ een labelnaam om de voorgestelde resultaten te zien.

   ![Tagingmiddelen](assets/adding-tags-to-assets.png)

1. Selecteer een of meer tags. De subtag wordt automatisch geselecteerd samen met de bovenliggende tag of naamruimte.
Tags die zijn gewijzigd in de weergave Middelen, worden ook toegepast in de beheerweergave.

## Beperkingen {#limitations}

De volgende geavanceerde taxonomiemogelijkheden zijn momenteel niet beschikbaar in de weergave Elementen en zijn alleen toegankelijk via de beheerweergave:

* **Lokalisatie:** Elke lokalisatie moet plaatsvinden in de beheerweergave.
* **Hoofdpad:** Hoofdpaden kunnen niet worden geconfigureerd. Alle naamruimten die zijn opgeslagen in Taxonomy Management, worden weergegeven in de eigenschap Tags in de weergave Elementen.
* **Standaardlabels:** De standaardlabels die worden toegepast in de beheerweergave zijn zichtbaar in de middelenweergave. U kunt geen nieuwe standaardlabels toevoegen in de weergave Middelen op de pagina Asset Details. De bestaande waarden die zijn opgeslagen in Standaardcodes worden toegepast op de pagina Elementdetails.
* **Aangepaste naamruimten:** Labels kunnen niet worden toegewezen aan aangepaste naamruimten.
* **Referenties weergeven:** Beheerders kunnen het taggebruik zien in de weergave Middelen. Dit heeft betrekking op alle elementen die actief een tag gebruiken. Beheerders kunnen echter geen afzonderlijke elementen zien die de tag in verwijzingen gebruiken.

<!--
*   Overview
*   Benefits
*   Prerequisites and Permissions
*   Configuration
*   Managing Tags
    *   Creating a Namespace
    *   Adding Tags to a Namespace
    *   Adding Tags to Standard Tags
    *   Moving Tags
    *   Editing Tags
    *   Deleting Tags
*   Applying Tags
    *   Adding Tags to the Metadata form
    *   Adding Tags to Assets
*   Limitations
-->