---
title: Verzamelingen beheren
description: Een verzameling is een set elementen in de weergave Experience Manager Assets. Gebruik verzamelingen om elementen tussen gebruikers te delen.
exl-id: 33c889f5-c989-4772-9591-db62f50e5c80
source-git-commit: d198b3f0c7d8469a376ba7a3e95e57c84f835dbb
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 1%

---

# Verzamelingen beheren {#manage-collections}

>[!CONTEXTUALHELP]
>id="assets_collections"
>title="Verzamelingen beheren"
>abstract="Een verzameling is een set elementen, mappen of andere verzamelingen in de weergave Elementen. Gebruik verzamelingen om elementen tussen gebruikers te delen. In tegenstelling tot mappen kan een verzameling elementen van verschillende locaties bevatten. U kunt meerdere verzamelingen delen met een gebruiker. Elke verzameling bevat verwijzingen naar elementen. De referentiële integriteit van activa wordt gehandhaafd over inzamelingen."

Een verzameling is een set elementen, mappen of andere verzamelingen in de weergave Adobe Experience Manager Assets. Gebruik verzamelingen om elementen tussen gebruikers te delen.

In tegenstelling tot mappen kan een verzameling elementen van verschillende locaties bevatten.

<!--
You can share collections with various users that are assigned different levels of privileges, including viewing, editing, and so on.
-->

U kunt meerdere verzamelingen delen met een gebruiker. Elke verzameling bevat verwijzingen naar elementen. De referentiële integriteit van activa wordt gehandhaafd over inzamelingen.

![Verzamelingen](assets/collections.png)

U kunt de volgende taken uitvoeren om inzamelingen te beheren en te gebruiken:

* [Een verzameling maken](#create-collection)

* [Elementen toevoegen aan een verzameling](#add-assets-to-collection)

* [Elementen uit een verzameling verwijderen](#remove-assets-from-collection)

* [Een slimme verzameling maken](#create-smart-collection)

* [Een slimme verzameling bewerken](#edit-smart-collection)

* [Metagegevens van verzamelingen weergeven en bewerken](#view-edit-collection-metadata)

* [Koppelingen voor verzamelingen delen](#share-collection-links)

* [Een verzameling downloaden](#download-collection)

* [Een verzameling verwijderen](#delete-collection)

## Een verzameling maken {#create-collection}

Een verzameling maken:

1. Klikken **[!UICONTROL Collections]** in het linkerspoor en klik vervolgens op **[!UICONTROL Create Collection]**.

1. Geef een titel en een optionele beschrijving voor de verzameling op.

1. Selecteer als u een Privé inzameling of een Openbare inzameling moet tot stand brengen. Een openbare inzameling is beschikbaar voor het bekijken en het uitgeven aan alle gebruikers. Nochtans, is een Privéinzameling beschikbaar aan de schepper en de gebruikers met beheerdervoorrechten.

1. Klikken **[!UICONTROL Create]** om de verzameling te maken.

![Verzameling maken](assets/create-collection.png)

<!--
   
   for viewing and editing only to users with the appropriate [permissions](#manage-collection-access).

-->

## Elementen toevoegen aan een verzameling {#add-assets-to-collection}

Elementen toevoegen aan een verzameling:

1. Klikken **[!UICONTROL Assets]** in het linkerspoor en selecteer de activa die u aan een inzameling moet toevoegen.

1. Klik op **[!UICONTROL Add to Collection]**.

1. Op de [!UICONTROL Collections] selecteert u de verzamelingen waaraan u de geselecteerde elementen wilt toevoegen.

1. Klikken **[!UICONTROL Add]** om het element aan de geselecteerde verzamelingen toe te voegen.

## Elementen uit een verzameling verwijderen {#remove-assets-from-collection}

Elementen uit een verzameling verwijderen:

1. Klikken **[!UICONTROL Collections]** in het linkerspoor om de lijst van inzamelingen te bekijken.

1. Klik op de verzameling en selecteer de items die u uit de verzameling wilt verwijderen.

1. Klik op **[!UICONTROL Remove]**.

## Een slimme verzameling beheren {#manage-smart-collection}

Sla de zoekresultaten op als een slimme verzameling om de inhoud van de verzameling dynamisch bij te werken. Als er elementen zijn toegevoegd aan de gegevensweergaveopslagplaats die voldoen aan de zoekcriteria die zijn gedefinieerd tijdens het maken van de slimme verzameling, wordt de inhoud van de slimme verzameling automatisch bijgewerkt wanneer u een slimme verzameling opent.

### Een slimme verzameling maken {#create-smart-collection}

Een slimme verzameling maken:

1. Klikken **[!UICONTROL Filter]** en [de zoekcriteria definiëren](search-assets-view.md#refine-search-results).

1. Klikken **[!UICONTROL Save as]** en selecteer vervolgens **[!UICONTROL Smart Collection]**.

   ![Slimme verzameling maken](assets/create-smart-collection.png)

1. Op de [!UICONTROL Create Smart Collection] geeft u een titel en een beschrijving op voor de slimme verzameling.

1. Selecteren **[!UICONTROL Public Collection]** als u alle gebruikers nodig hebt om toegang te krijgen tot de verzameling. Selecteren **[!UICONTROL Private Collection]** als u een beperkte groep gebruikers nodig hebt om toegang te krijgen tot de verzameling.

1. Klikken **[!UICONTROL Create]** om de slimme verzameling te maken.

### Een slimme verzameling bewerken {#edit-smart-collection}

Een slimme verzameling bewerken:

1. Klikken **[!UICONTROL Collections]** in het linkerspoor en klik dan de naam van de inzameling tweemaal die u moet uitgeven.

1. Klik op **[!UICONTROL Edit Smart Collection]**.

1. Op de [!UICONTROL Edit Smart Collection Filters] dialoogvenster, [de zoekcriteria bijwerken](search-assets-view.md#refine-search-results) voor de slimme verzameling.

1. Klik op **[!UICONTROL Save]**.

<!--

## Manage access to a Private collection {#manage-collection-access}

The permission management for collections function in the same manner as folders in [!DNL Assets view]. Administrators can manage the access levels for collections available in the repository. As an administrator, you can create user groups and assign permissions to those groups to manage access levels. You can also delegate the permission management privileges to user groups at the collection-level.

For more information, see [Manage permissions for folders and collections](manage-permissions.md).

-->

<!--

## Search a collection {#search-collections}

Click **[!UICONTROL Collections]** in the left rail and use the Search box to specify a text as the criteria to search for a collection. [!DNL Assets view] uses the specified text to search collection names, metadata including tags defined for a collection and returns appropriate results.

>[!NOTE]
>
>Assets view performs search in collections available at the root level. It does not perform search in assets and folders available in collections.

-->

## Metagegevens van verzamelingen weergeven en bewerken {#view-edit-collection-metadata}

Metagegevens over verzamelingen bevatten gegevens over de verzameling, zoals titel en beschrijving.

Metagegevens van verzamelingen weergeven en bewerken:

1. Klikken **[!UICONTROL Collections]** Selecteer een verzameling in de linkertrack en klik op **[!UICONTROL Details]**.
1. De metagegevens van de verzameling weergeven met de opdracht **[!UICONTROL Basic]** tab.
1. Wijzig desgewenst de metagegevensvelden. U kunt de [!UICONTROL Title] en [!UICONTROL Description] velden.

![Metagegevens verzameling](assets/collection-metadata.png)

## Koppelingen voor verzamelingen delen {#share-collection-links}

[!DNL Assets view] kunt u een koppeling genereren en verzamelingen en middelen delen in verzamelingen met externe belanghebbenden die geen toegang hebben tot de [!DNL Assets view] toepassing. U kunt een vervaldatum voor de verbinding bepalen en dan het delen met anderen gebruikend uw aangewezen communicatie methode zoals e-mail of overseinendiensten. Ontvangers van de koppeling kunnen een voorbeeld van de elementen bekijken en deze downloaden.

![Koppeling voor elementen delen](assets/share-link-collections.png)

Voor meer informatie over hoe te om inzamelingsverbindingen met externe belanghebbenden te delen, zie [koppelingen delen voor elementen](/help/assets/share-links-for-assets-view.md).

## Een verzameling downloaden {#download-collection}

Een verzameling downloaden:

1. Klikken **[!UICONTROL Collections]** in het linkerspoor.

1. Selecteer de verzameling die u wilt downloaden en klik op **[!UICONTROL Download]**.

1. Op de [!UICONTROL Downloading Asset] dialoogvenster, klikt u op **[!UICONTROL OK]**.

De verzameling wordt als een ZIP-bestand gedownload op uw lokale computer.

## Een verzameling verwijderen {#delete-collection}

Een verzameling verwijderen:

1. Klikken **[!UICONTROL Collections]** in het linkerspoor.

1. Selecteer de verzameling die u wilt verwijderen.

1. Klik op **[!UICONTROL Delete]**.

## Volgende stappen {#next-steps}

* Feedback geven op het product met de [!UICONTROL Feedback] optie beschikbaar in de gebruikersinterface van de weergave Elementen

* Documentfeedback geven met [!UICONTROL Edit this page] ![de pagina bewerken](assets/do-not-localize/edit-page.png) of [!UICONTROL Log an issue] ![een GitHub-probleem maken](assets/do-not-localize/github-issue.png) beschikbaar op de rechterzijbalk

* Contact [Klantenservice](https://experienceleague.adobe.com/?support-solution=General#support)
