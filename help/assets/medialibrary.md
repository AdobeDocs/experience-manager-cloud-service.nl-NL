---
title: Media Library gebruiken voor elementair beheer van digitale middelen
description: "[!DNL Experience Manager Assets] en Media Library voor middelenbeheer."
contentOwner: AG
feature: Asset Management,Publishing
role: User,Architect,Leader
exl-id: 4737d5ee-9a93-49f3-9f20-d4368e60e9fb
source-git-commit: bc4da79735ffa99f8c66240bfbfd7fcd69d8bc13
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 0%

---

<!--

Define Media Lib
Define req for it
Define use cases
Define what is not included

-->

# Media Library gebruiken voor elementair beheer van bedrijfsmiddelen {#manage-assets-using-media-library}

[!DNL Adobe Experience Manager] platform biedt verschillende mogelijkheden om elementen te beheren. Met Media Library kunnen gebruikers een klein aantal elementen uploaden naar de opslagplaats, zoeken en gebruiken in de webpagina&#39;s en eenvoudige taken voor middelenbeheer uitvoeren op de middelen.

Media Library is een lichte DAM-oplossing (Digital Asset Management) die gratis wordt geleverd met [!DNL Adobe Experience Manager Sites] licentie. [!DNL Sites] is een Web Content Management (WCM)-aanbieding. Media Library werkt met alle mogelijkheden van Experience Manager.

[!DNL Adobe Experience Manager Assets] licentie is apart verkrijgbaar. [!DNL Experience Manager Assets] maakt een robuuste verwerking van bedrijfsmiddelen mogelijk via gevallen voor bedrijfsgebruik, aanpassingen voor metagegevens, schema&#39;s, zoekopdrachten en gebruikersinterface, en vele andere functies die verder gaan dan wat Media Library biedt.

## Vergunningsvereisten {#avail-media-library-license}

Klanten die [!DNL Sites] Media Library mag worden gebruikt. Het werkt met alle componenten van [!DNL Experience Manager].

Media Library wordt geïnstalleerd als onderdeel van Sites. Naast de licentie en installatie van Sites is geen extra licentie of pakket vereist.

## [!DNL Assets] versus Media Library {#assets-and-media-library}

Experience Manager Assets biedt DAM-functionaliteit op bedrijfsniveau. Functionaliteit voor elementen wordt geleverd bij [!DNL Experience Manager] in één enkele verpakking. Gebruikers die geen middelenlicentie hebben aangeschaft, hebben echter geen recht op het gebruik van de geavanceerde DAM-functies. Alleen zonder middelenlicentie [Media Library-functies](#use-media-library) zijn beschikbaar.

Als u onbedoeld gebruik van [!DNL Assets] functies waarvoor u geen licentie hebt, verwijdert u vervolgens alle [!DNL Assets]specifieke workflows, componenten, taxonomieën, opties en de [!DNL Assets] beheerder van [!DNL Experience Manager]. Zo voorkomt u dat uw gebruikers per ongeluk [!DNL Assets] functies waarvoor u geen licentie hebt verleend.

## Media Library gebruiken {#use-media-library}

Media Library bestrijkt in grote lijnen de volgende gebruiksgevallen:

* Basisfuncties voor DAM bieden voor webpagina&#39;s die zijn gemaakt met [!DNL Adobe Experience Manager Sites].
* Adaptieve formulieren en communicatie die zijn gemaakt met [!DNL Adobe Experience Manager Forms].
* Ervaringen met digitale schermen die zijn gemaakt met [!DNL Adobe Experience Manager Screens].
* [!DNL Assets] HTTP REST-API&#39;s voor bewerkingen zonder kop.

<!-- TBD: Remove this after confirmation. May need to merge this list with the list provided by PMs.

* Static renditions

-->

Als u de Media Library-functionaliteit wilt gebruiken, kunt u de standaard [!DNL Experience Manager] gebruikersinterface. Media Library maakt deel uit van de [!DNL Experience Manager Sites] installatie en er is geen afzonderlijke interface of invoegtoepassing vereist. Met behulp van de bestaande interface kunnen Media Library-gebruikers de volgende taken uitvoeren:

* Maak mappen om elementen te ordenen.
* Elementen uploaden.
* Elementen publiceren.
* Elementen bewerken, verplaatsen en kopiëren.
* Blader naar de elementen die u wilt gebruiken, filter en zoek (inclusief zoeken op basis van gelijkenis).
* Voeg waarden toe aan en bewerk de waarden in de metagegevensvelden, behalve het veld Slimme tags, die beschikbaar zijn in het dialoogvenster [!UICONTROL Basic] tabblad van een element [!UICONTROL Properties] pagina standaard.
* Statische vertoningen toevoegen en verwijderen.
* Download mappen, elementen en elementenuitvoeringen.
* Elementversies maken.
* Revisietaken voor elementen maken en uitvoeren.
* Annoteer elementen.
* Elementen toevoegen aan [!DNL Sites] pagina&#39;s door de Inhoudszoeker.
* Gebruiken [!DNL Content Fragments].
* HTTP REST- en GraphQL-API&#39;s gebruiken voor [!DNL Content Fragments] en media-elementen waarnaar wordt verwezen, onder Sites-licentie.
* integratie van de Marketing Cloud.
* Gebruikersinterface voor middelenbeheer aanpassen en uitbreiden.
* Heb toegang tot de Bouwer van de Vraag (API) om de onderzoeksfunctionaliteit uit te breiden.
* Statische tags maken.
* Ontwerpprojecten en -taken.
* Activiteitsstroom (tijdlijn).
* Opmerkingen en annotaties.

<!-- TBD: Define exactly which basic Assets workflow are available for use with Media Library?

As per PM, we must avoid stating such a list, as we don't have a list that makes sense in Cloud Service.
-->

>[!IMPORTANT]
>
>Vele geavanceerde gevallen van gebruik van DAM worden vervuld door [!DNL Experience Manager Assets]. Met Media Library-licentie kunt u alleen de vermelde gebruiksgevallen met Media Library afhandelen. Als een gebruiksgeval niet wordt vermeld, gebruik het niet met de vergunning van Media Library. Neem contact op met Customer Support als je vragen hebt.

U kunt geen slimme tags gebruiken. [!DNL Asset] koppeling, [!DNL Asset] selector, bulksgewijs labelen, workflows voor elementen wijzigen of de standaard [!DNL Adobe Experience Manager] gebruikersinterface voor toegang tot Media Library zonder [!DNL Assets] licentie.

<!-- TBD: Add a CTA - how to contact Adobe for queries. -->

>[!MORELIKETHIS]
>
>* [DAM-functies in [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/home.html)
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-cloud-service.html)

