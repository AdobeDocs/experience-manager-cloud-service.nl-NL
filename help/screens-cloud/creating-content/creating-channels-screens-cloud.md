---
title: Kanalen maken en beheren in as a Cloud Service schermen
description: In deze pagina wordt beschreven hoe u kanalen in as a Cloud Service schermen maakt en beheert.
exl-id: 3b0bae7a-4a45-485a-ab04-604510ff6578
feature: Authoring Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 1%

---

# Een kanaal maken en beheren in as a Cloud Service schermen {#creating-channels-screens-cloud}

Nadat u een AEM Screens-project hebt gemaakt, moet u kanalen maken.
***Kanalen***, geeft u een reeks inhoud (afbeeldingen en video&#39;s), een website of een toepassing van één pagina weer.

## Doelstelling {#objective}

Met dit document krijgt u meer inzicht in het maken en beheren van kanalen voor uw AEM Screens-project in de Inhoudsprovider voor schermen. Na het lezen moet u:

* begrijpen hoe u kanalen maakt voor de Inhoudsprovider voor schermen
* inhoud in uw kanalen beheren en bewerken
* beheer het taak- en activeringsschema voor uw kanalen in [Serviceprovider voor schermen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/navigating-to-screens-services-provider.html?lang=en)

## Stappen voor het maken van een nieuw sequentiekanaal in as a Cloud Service schermen {#create-new-channel}

>[!NOTE]
>**Vereisten**
>Voordat u deze sectie van de Guide start, moet u [Projecten maken en beheren in as a Cloud Service schermen](/help/screens-cloud/creating-content/creating-projects-screens-cloud.md).

Voer de onderstaande stappen uit om een volgnummer te maken in as a Cloud Service schermen:

1. Navigeer naar de Inhoudsprovider voor schermen.

1. Ga naar uw AEM Screens-project, zoals *FirstDigitalExperience*.

1. Selecteer de **Kanalen** map van uw project, zoals **FirstDigitalExperience** —> **Kanalen** en klik op **Maken** in de actiebalk.

   ![channel-create1](/help/screens-cloud/assets/create-content/channel-create1.png)

1. Selecteer de sjabloon, zoals: **Volgekanaal** van de **Maken** wizard en klik op **Volgende**.

   ![channel-create2](/help/screens-cloud/assets/create-content/channel-create2.png)

   >[!NOTE]
   > De **Maken** biedt verschillende typen sjablonen tijdens het maken van een kanaal. Zie [Beschikbare sjablonen](#available-templates) in de wizard Maken voor meer informatie.

1. Voer de naam van het volgnummer in, bijvoorbeeld: **LoopingChannelOne** en klik op **Maken**.

   ![channel-create3](/help/screens-cloud/assets/create-content/channel-create3.png)

   U ziet nu een **LoopingChannelOne** in uw map Kanalen in uw AEM Screens-project.

   Nadat u het kanaal hebt gemaakt, kunt u nu inhoud aan het kanaal toevoegen. Zie [Inhoud toevoegen aan een kanaal](#add-content) voor informatie over het toevoegen van elementen (afbeeldingen/video&#39;s) aan uw kanaal.

## Een kanaal beheren {#managing-channels}

U kunt een kanaal bewerken, weergeven, eigenschappen en dashboard, kopiëren, voorvertonen en verwijderen.

Navigeer naar het kanaal vanuit uw project en selecteer het kanaal, zoals in de onderstaande afbeelding wordt getoond. U kunt nu opties selecteren, zoals het bewerken van het kanaal, het weergeven van eigenschappen, het voorvertonen van inhoud, het beheren van publicatie of het verwijderen van het kanaal uit de actiebalk.

![channelprop1](/help/screens-cloud/assets/create-content/channelprop1.png)

### Inhoud toevoegen aan een kanaal {#add-content}

Ga als volgt te werk om inhoud aan een kanaal toe te voegen of te bewerken:

1. Selecteer het kanaal dat u wilt bewerken, zoals in de onderstaande afbeelding wordt getoond. Klikken **Bewerken** in de linkerbovenhoek van de actiebalk om de editor te openen.

   ![edit-channel1](/help/screens-cloud/assets/create-content/edit-channel1.png)

1. In de editor kunt u elementen/componenten aan uw kanaal toevoegen die u wilt publiceren.

1. Sleep de elementen vanuit het linkerdeelvenster en voeg deze toe aan de editor.

   ![bewerkingskanaal2](/help/screens-cloud/assets/create-content/edit-channel2.png)

   >[!NOTE]
   >Klikken **Voorvertoning** om de inhoud van het kanaal voor te vertonen.
   >![bewerken, kanaalvoorbeeld](/help/screens-cloud/assets/create-content/edit-channelpreview.png)

## Beschikbare sjablonen in wizard Maken {#available-templates}

De volgende sjablonen zijn beschikbaar tijdens het gebruik van de **Maken** wizard Kanaal:

| Beschikbare sjablonen | Beschrijving |
|--- |--- |
| Map Kanalen | Hiermee kunt u een map maken waarin de verzameling kanalen wordt opgeslagen. |
| Volgekanaal | Hiermee kunt u een kanaal maken waarmee de componenten opeenvolgend worden afgespeeld (een voor een in een presentatie). |
| Linker- of rechterL-balkgesplitste schermkanaal | Hiermee kunnen auteurs van inhoud verschillende typen elementen weergeven in zones met de juiste grootte. |

## Standaardtoewijzingsdetails gebruiken voor kanalen {#default-channels}

Met deze functie kunt u een standaard activeringsschema voor een kanaal definiëren en dit standaard gebruiken voor elke toewijzing voor een weergave. Dit verstrekt een methode zodat de lastige programmadefinitie niet te hoeven worden herhaald.

1. Ga vanuit [hier](https://experience.adobe.com/screens).

### Standaardtoewijzingsdetails maken voor een kanaal {#create-default}

1. Navigeer naar de detailspagina voor het kanaal u wilt vormen.
1. Zoek de **Standaardtoewijzingsdetails** tegel op de pagina.

   ![afbeelding](/help/screens-cloud/assets/display/Assignment1.png)

1. Klikken **Standaarddetails instellen**.
1. Configureer de standaardtoewijzingsdetails, inclusief prioriteit, begin- en einddatums en herhalingspatronen voor het kanaal en klik op **Toewijzen**.

   ![afbeelding](/help/screens-cloud/assets/display/Assignments2.png)

1. De details van de toewijzing worden weergegeven in het dialoogvenster **Standaardtoewijzingsdetails** tegel:

   ![afbeelding](/help/screens-cloud/assets/display/Assignments3.png)

In deze tegel wordt de volgende informatie weergegeven:
* Standaardprioriteit van het kanaal in de weergave.
* De begin- en einddatum van de activering wanneer het kanaal volgens de planning moet worden afgespeeld.
* Synthetisch overzicht van de herhaling (Uur/Daily/Weekly/Maandelijks/Jaarlijks en naam die aan die herhaling wordt gegeven).

### De standaardtoewijzingsdetails gebruiken bij het toewijzen aan een weergave {#default-display}

Kanalen met standaardtoewijzingsdetails kunnen op dezelfde manier worden weergegeven als gewone kanalen, met de toegevoegde optie om de standaardtoewijzingsdetails te gebruiken in plaats van telkens handmatig aangepaste details te definiëren.

1. Navigeer naar de pagina met weergavedetails waaraan u het kanaal wilt toewijzen en klik op de knop **Kanaal toewijzen**.
Of selecteer de gewenste weergave in het dialoogvenster [voorraad](https://experience.adobe.com/screens/displays) weergeven en klikken op de knop **Kanaal toewijzen**.
1. Het dialoogvenster Kanaaltoewijzing wordt geopend.

   ![afbeelding](/help/screens-cloud/assets/display/Assignments4.png)

1. Selecteer in de kanaalkiezer het gewenste kanaal met de standaardtoewijzingsdetails.
1. U ziet dat het dialoogvenster voor kanaaltoewijzing is gewijzigd, zodat u de standaardtoewijzingsdetails kunt kiezen of aangepaste toewijzingsdetails kunt selecteren:

   ![afbeelding](/help/screens-cloud/assets/display/Assignments5.png)

1. Klikken **Toewijzen** om de toewijzing te voltooien, of klik **Aangepaste toewijzingsdetails instellen** als u de standaardinstellingen liever overschrijft met een aantal andere waarden in de context van die bepaalde weergave.

   ![afbeelding](/help/screens-cloud/assets/display/Assignments6.png)

1. Let op: **Toegewezen kanalen** De tegel wordt bijgewerkt met de nieuwe toewijzing:

   ![afbeelding](/help/screens-cloud/assets/display/Assignments7.png)

1. U ziet dat de kanalen een ander pictogram hebben, afhankelijk van het feit of ze aangepaste programma&#39;s (het pictogram Klok) gebruiken of de standaarddetails (het pictogram voor de klok van de Wereld) overnemen. Als u op deze kanalen klikt, worden de planningsdetails weergegeven.
1. U ziet ook dat de beschikbare acties voor elk type verschillen.

   ![afbeelding](/help/screens-cloud/assets/display/Assignments8.png)

**Opmerking:** Een kanaaltoewijzing die de standaardtoewijzingsdetails gebruikt, kan niet worden bewerkt in de context van de weergave.

* Als u deze in een aangepaste toewijzing moet wijzigen, verwijdert u deze eerst en voegt u deze vervolgens opnieuw toe met de opdracht **Aangepaste toewijzingsdetails instellen** -optie.
* Als u de eigenschappen van de standaardtoewijzingsdetails moet wijzigen, doet u dit rechtstreeks vanaf de pagina met kanaaldetails.

### Standaardtoewijzingsgegevens uit een kanaal verwijderen {#remove-display}

1. Navigeer naar de detailpagina voor het kanaal u de standaardtoewijzingsdetails wilt verwijderen.
1. Zoek de **Standaardtoewijzingsdetails** tegel op de pagina
1. Klik op de knop **Standaard verwijderen**.

   ![afbeelding](/help/screens-cloud/assets/display/Assignments9.png)

1. Er wordt een bevestigingsdialoogvenster weergegeven en de details komen overeen met een van de volgende voorwaarden:
   **a.** Kanaal wordt in geen enkele weergave gebruikt.

   ![afbeelding](/help/screens-cloud/assets/display/Assignments10.png)

**b.** Kanaal wordt gebruikt in één scherm.

![afbeelding](/help/screens-cloud/assets/display/Assignment11.png)

**c.** Kanaal wordt gebruikt in verschillende beeldschermen.

![afbeelding](/help/screens-cloud/assets/display/Assignments12.png)

1. Klik op de knop *Verwijderen* om de wijziging te valideren.

**Opmerking:** Als u de standaardtoewijzingsdetails uit een kanaal verwijdert, worden de overeenkomende toewijzingen verwijderd voor alle weergaven die het kanaal gebruikten.
Dit kan dan ook leiden tot lege schermen als er geen alternatieve inhoud op die schermen moet worden afgespeeld.

## Volgende functies {#whats-next}

Nu u een AEM Screens-kanaal hebt ingesteld in uw project, moet u uw kanaal publiceren. Zie [Kanalen in as a Cloud Service schermen publiceren](manage-publish.md) voordat u uw spelers beheert bij Screens Services Provider.
