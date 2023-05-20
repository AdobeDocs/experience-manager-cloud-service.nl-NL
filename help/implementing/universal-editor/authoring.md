---
title: Inhoud ontwerpen met de Universal Editor
description: Leer hoe gemakkelijk en intuïtief het is voor inhoudsauteurs om inhoud tot stand te brengen gebruikend de Universele Redacteur.
exl-id: 15fbf5bc-2e30-4ae7-9e7f-5891442228dd
source-git-commit: 9cff6e94b38016f008fd8177be2e071a530d80b6
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 0%

---

# Inhoud ontwerpen met de Universal Editor {#authoring}

Leer hoe gemakkelijk en intuïtief het is voor inhoudsauteurs om inhoud tot stand te brengen gebruikend de Universele Redacteur.

## Inleiding {#introduction}

Met de Universal Editor kunt u alle aspecten van inhoud in elke implementatie bewerken, zodat u over uitzonderlijke ervaringen beschikt, de snelheid van de inhoud verhoogt en een geavanceerde ontwikkelaarservaring hebt.

Hiervoor beschikken inhoudsauteurs over een intuïtieve gebruikersinterface die minimale training vereist om eenvoudig in de inhoud te kunnen springen en te kunnen beginnen bewerken.

>[!TIP]
>
>Zie het document voor een meer gedetailleerde inleiding tot de Universal Editor [Introductie van de Universal Editor.](introduction.md)

>[!NOTE]
>
>De Universal Editor is nog in ontwikkeling en kan momenteel niet alle inhoudstypen bewerken.

## De app voorbereiden {#prepare-app}

Als u inhoud voor een app wilt ontwerpen met de Universal Editor, moet de app van instrumenten worden voorzien door een ontwikkelaar om de editor te ondersteunen.

>[!TIP]
>
>Zie het document [Aan de slag met de Universal Editor in AEM](getting-started.md) voor een voorbeeld van hoe u een AEM toepassing configureert voor gebruik met de Universal Editor.

## Aanmelden {#sign-in}

Wanneer de app van instrumenten is voorzien om met de Universal Editor te werken, moet u zich aanmelden bij de Universal Editor. U hebt een Adobe ID nodig om u aan te melden en [toegang hebben tot de Universal Editor.](getting-started.md#request-access)

Wanneer u bent aangemeld, voert u de URL in van de pagina die u wilt bewerken in het dialoogvenster [adresbalk.](#address-bar) om te beginnen [bewerken van de inhoud.](#edit-content)

## De gebruikersinterface begrijpen {#ui}

De interface is verdeeld in vier hoofdgebieden.

* [De koptekst Experience Cloud](#experience-cloud-header)
* [De koptekst van de Universal Editor](#universal-editor-header)
* [De spoorwegen](#rail)
* [De editor](#editor)

![De gebruikersinterface van de Universal Editor](assets/ui.png)

### De koptekst Experience Cloud {#experience-cloud-header}

De koptekst van de Experience Cloud staat altijd boven aan het scherm. Het is een anker dat u vertelt waar u zich binnen Experience Cloud bevindt en u helpt u naar andere Experience Cloud-apps te navigeren.

![De koptekst Experience Cloud](assets/experience-cloud-header.png)

#### Experience Manager {#experience-manager}

Selecteer de verbinding van Adobe Experience Cloud bij de linkerzijde van de kopbal om aan de wortel van uw oplossing van de Experience Manager te navigeren om tot hulpmiddelen zoals [Cloud Manager,](/help/onboarding/cloud-manager-introduction.md) [Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/introduction/overview-cam.md) en [Softwaredistributie.](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html)

![De knop Algemene navigatie](assets/global-navigation.png)

#### Organisatie {#organization}

Hier wordt de organisatie weergegeven waarmee u momenteel bent aangemeld. Tik of klik om over te schakelen naar een andere organisatie als uw Adobe ID is gekoppeld aan meerdere.

![Organisatie-indicator](assets/organization.png)

#### Oplossingen {#solutions}

Als u op de schakeloptie voor oplossingen tikt of erop klikt, kunt u snel naar andere Experience Cloud-oplossingen gaan.

![Oplossingsschakelaar](assets/solutions.png)

#### Help {#help}

Met het Help-pictogram hebt u snel toegang tot leermiddelen en ondersteuningsbronnen.

![Help](assets/help.png)

#### Meldingen {#notifications}

Dit pictogram wordt gemarkeerd met het aantal momenteel toegewezen onvolledige [meldingen.](/help/implementing/cloud-manager/notifications.md)

![Meldingen](assets/notifications.png)

#### Gebruikerseigenschappen {#user-properties}

Tik of klik op het pictogram dat uw gebruiker vertegenwoordigt om toegang te krijgen tot uw gebruikersinstellingen. Als u geen gebruikersbeeld hebt gevormd, zal een pictogram willekeurig worden toegewezen.

![Gebruikerseigenschappen](assets/user-properties.png)

### De koptekst van de Universal Editor {#universal-editor-header}

De Universal Editor-koptekst bevindt zich altijd boven aan het scherm net onder [de koptekst van de Experience Cloud.](#experience-cloud-header) Hiermee kunt u snel naar een andere pagina navigeren om te bewerken en de huidige pagina publiceren.

![De koptekst van de Universal Editor](assets/universal-editor-header.png)

#### Het menu Hamburger {#hamburger-menu}

Het hamburgermenu is nog niet geïmplementeerd.

![Hambuger-menu](assets/hamburger-menu.png)

#### Locatiebalk {#Location-bar}

Op de locatiebalk ziet u het adres van de pagina die u bewerkt. Tik of klik om het adres in te voeren van een andere pagina die u wilt bewerken.

![Locatiebalk](assets/address-bar.png)

>[!TIP]
>
>De sneltoets gebruiken `L` om de adresbalk te openen.

>[!NOTE]
>
>Elke pagina die u wilt bewerken met de universele editor moet [van instrumenten voorzien om de Universele Redacteur te steunen.](getting-started.md)

#### App-voorvertoning openen {#open-app-preview}

Tik of klik op het pictogram met de voorvertoning van de geopende app om de pagina die u momenteel bewerkt te openen in een eigen browser, zodat de editor er geen voorvertoning van kan weergeven.

![App-voorvertoning openen](assets/open-app-preview.png)

>[!TIP]
>
>De sneltoets gebruiken `O` om de voorvertoning van de app te openen.

#### Publicatie {#publish}

Tik of klik op de knop Publiceren om de wijzigingen in de live inhoud voor gebruik door uw lezers te publiceren.

![Knop Publiceren](assets/publish.png)

>[!TIP]
>
>Zie het document [Inhoud publiceren met de Universal Visual Editor](publishing.md) voor meer informatie over publiceren met de Universele Redacteur.

### Het spoor {#rail}

De spoorstaaf is altijd aanwezig langs de linkerkant van de redacteur. Het staat voor gemakkelijke omschakeling toe de redacteur tussen voorproefwijze en geeft wijze uit.

![De spoorwegen](assets/rail.png)

#### Voorvertoningsmodus {#preview-mode}

In voorproefwijze, de pagina die in de redacteur wordt teruggegeven zoals het op uw gepubliceerde dienst zou worden gezien. Hierdoor kan de auteur van de inhoud door de inhoud navigeren door op koppelingen te klikken, enz.

![Voorvertoningsmodus](assets/preview-mode.png)

>[!TIP]
>
>De sneltoets gebruiken `P` om over te schakelen naar de voorvertoningsmodus.

#### Bewerkingsmodus {#edit-mode}

In de bewerkingsmodus wordt de pagina gerenderd in de editor, maar de auteur van de inhoud kan klikken om de inhoud te selecteren en te bewerken. Dit is de standaardmodus van de editor wanneer een pagina wordt geladen.

![Bewerkingsmodus](assets/edit-mode.png)

### De Editor {#editor}

De editor neemt het grootste deel van het venster in beslag en bevindt zich op de locatie van de pagina die is opgegeven in [de adresbalk](#address-bar) wordt weergegeven.

Afhankelijk van of de editor is ingesloten [bewerkingsmodus](#edit-mode) of [voorvertoningsmodus,](#edit-mode) de inhoud kan worden bewerkt of kan worden genavigeerd.

![Editor](assets/editor.png)

## Inhoud bewerken {#editing-content}

Inhoud bewerken is eenvoudig en intuïtief. In [bewerkingsmodus,](#edit-mode) terwijl u de muis over de inhoud in de editor beweegt, wordt de bewerkbare inhoud gemarkeerd met een blauw vak.

![Bewerkbare inhoud wordt gemarkeerd door een blauw vak](assets/editable-content.png)

Tik of klik op de inhoud in het blauwe vak om een interne editor te starten en uw wijzigingen aan te brengen. Druk op Enter of Return om de wijzigingen op te slaan.

![Inhoud bewerken](assets/editing-content.png)

Houd er rekening mee dat in de bewerkingsmodus door tikken of klikken op inhoud wordt geprobeerd deze te selecteren voor bewerking. Als u door de inhoud wilt navigeren door de koppelingen te volgen, schakelt u over naar [voorvertoningsmodus.](#preview-mode)

## Inhoud voorvertonen {#previewing-content}

Wanneer u klaar bent met het bewerken van inhoud, wilt u er vaak door navigeren om te zien hoe het er uitziet in de inhoud van andere pagina&#39;s. In [voorbeeldmodus](#preview-mode) u kunt op koppelingen klikken om door de inhoud te navigeren zoals een lezer zou doen. De inhoud wordt in de editor gerenderd zoals deze zou worden gepubliceerd.

Houd er rekening mee dat in de voorvertoningsmodus tikken of klikken op inhoud reageert op de manier waarop dit voor een lezer van de inhoud gebeurt. Als u de te bewerken inhoud wilt selecteren, schakelt u over naar [bewerkingsmodus.](#edit-mode)

## Aanvullende bronnen {#additional-resources}

Zie deze documenten voor meer informatie over de Universal Editor.

* [Introductie van Universal Editor](introduction.md) - Leer hoe u met de Universal Editor elk aspect van elke inhoud in een implementatie kunt bewerken om buitengewone ervaringen te bieden, de snelheid van de inhoud te verhogen en een geavanceerde ontwikkelaarservaring te bieden.
* [Inhoud publiceren met de Universal Editor](publishing.md) - Leer hoe de Universal Visual Editor inhoud publiceert en hoe uw apps de gepubliceerde inhoud kunnen verwerken.
* [Aan de slag met de Universal Editor in AEM](getting-started.md) - Leer hoe u toegang krijgt tot de Universal Editor en hoe u uw eerste AEM-app van instrumenten kunt voorzien om deze te gebruiken.
* [Architectuur van Universal Editor](architecture.md) - Leer over de architectuur van de Universele Redacteur en hoe de gegevens tussen zijn diensten en lagen stromen.
* [Kenmerken en typen](attributes-types.md) - Meer informatie over de gegevenskenmerken en typen die de Universal Editor nodig heeft.
* [Universal Editor-verificatie](authentication.md) - Leer hoe de Universal Editor wordt geverifieerd.
