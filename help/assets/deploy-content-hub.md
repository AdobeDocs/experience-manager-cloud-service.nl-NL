---
title: Implementeren [!DNL Content Hub]
description: Leer hoe u Content Hub kunt implementeren en activeren en gebruikers toegang kunt bieden met verschillende typen rechten (middelen uploaden, gebruikers van Adoben Express) en hoe u beheerdersrechten kunt bieden aan gebruikers.
role: Admin
source-git-commit: 56af07a198e1350282f5d3f771c1c29db318b90e
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 0%

---


# Content Hub implementeren {#deploy-content-hub}

![Content Hub implementeren](assets/deploy-content-hub.png)

Content Hub is beschikbaar als onderdeel van Experience Manager Assets as a Cloud Service voor het democratiseren van de toegang tot online-inhoud voor organisaties en hun zakelijke partners.

De activa die op Experience Manager Assets as a Cloud Service zijn gemerkt zijn beschikbaar voor activaverdeling op Content Hub.

Dit artikel biedt een end-to-end workflow om Content Hub toegang te bieden aan gebruikers, inclusief de variaties van bevoegdheden op basis van hun behoeften.

De verschillende privileges in Content Hub zijn onder meer:

* [Middelconsumenten](#onboard-content-hub-consumer-users): Gebruik merkgoedgekeurde middelen op de Content Hub-portal.

* [Beheerders](#onboard-content-hub-administrator): Toegang tot de [Gebruikersinterface configuratie](/help/assets/configure-content-hub-ui-options.md) op Content Hub, naast Asset Consumer met rechten voor het indienen van voorstellen.

* [Middelenconsumenten met voorleggingsrechten](#onboard-content-hub-consumer-users-submission-rights): Mogelijkheid om [middelen uploaden naar Content Hub](/help/assets/upload-brand-approved-assets.md) en [Adobe Express-integratie](/help/assets/edit-images-content-hub.md) naast de toegang tot merkgoedgekeurde middelen op het Content Hub-portaal.

* [Middeldistributeurs](#content-hub-asset-distributors): Mogelijkheid om activa op Experience Manager Assets as a Cloud Service goed te keuren om deze activa op Content Hub beschikbaar te stellen.

## Stap 1: Content Hub for Experience Manager Assets inschakelen met Cloud Manager {#enable-content-hub}

Om toegang te krijgen tot het Content Hub-portaal, moeten beheerders eerst Content Hub voor Experience Manager Assets as a Cloud Service inschakelen met Cloud Manager. Voer de volgende stappen uit:

1. Meld u aan bij Cloud Manager. Zorg ervoor dat u de juiste organisatie selecteert terwijl u zich aanmeldt. In Cloud Manager worden al uw programma&#39;s vermeld.

1. Ga naar Experience Manager Assets as a Cloud Service, klik op het pictogram Meer opties (...) en selecteer **[!UICONTROL Edit Program]**.

   ![Programma bewerken in Cloud Manager](assets/edit-program-cloud-manager.png)

1. Op de [!UICONTROL Edit Program] selecteert u de **[!UICONTROL Solutions & Add-ons]** tab.

1. Uitbreiden **[!UICONTROL Assets]** en selecteert u **[!UICONTROL Content Hub]**.
   ![Content Hub selecteren in Cloud Manager](assets/edit-program-cloud-manager-content-hub.png)

1. Klik op **[!UICONTROL Update]**.

Content Hub is nu ingeschakeld voor Experience Manager Assets as a Cloud Service.

Als je nog geen ervaring hebt met Experience Manager Assets, klikt u op **[!UICONTROL Add Program]** en geef vervolgens de programmatiedetails (Programmanaam, Instelling voor Productie) op en klik op **[!UICONTROL Continue]**. U kunt vervolgens **[!UICONTROL Assets]** en **[!UICONTROL Content Hub]** in de **[!UICONTROL Solutions & Add-ons]** tab.

### Content Hub-exemplaar en productprofiel op Admin Console{#content-hub-instance-product-profile}

Na [Content Hub inschakelen voor Assets as a Cloud Service met Cloud Manager](#enable-content-hub), er is een nieuwe instantie gemaakt in AEM Assets as a Cloud Service Admin Console met `contenthub` als achtervoegsel:

![Nieuwe instantie voor Content Hub](assets/new-instance-content-hub.png)

Er is geen `author` of `publish` in de instantienaam voor Content Hub.

Klik op de instantienaam om het Content Hub-productprofiel weer te geven.

![Content Hub-productprofiel](assets/content-hub-product-profile.png)

## Stap 2: on-board Content Hub-beheerder {#onboard-content-hub-administrator}

Content Hub-beheerders kunnen elementen toevoegen aan Content Hub en kunnen ook de [Configuratieopties](/help/assets/configure-content-hub-ui-options.md) voor andere gebruikers binnen uw organisatie.

Aan boord van de Content Hub-beheerder:

1. [Open en klik op het Content Hub-gebruikersprofiel](#content-hub-instance-product-profile).

1. Klikken **[!UICONTROL Add users]** om gebruikers of gebruikersgroepen toe te voegen aan het productprofiel.

1. Klikken **[!UICONTROL Save]** om de wijzigingen op te slaan

1. Nadat u de gebruiker aan het Content Hub-productprofiel hebt toegevoegd, opent u de Experience Manager Assets-productprofielen door op de AEM as a Cloud Service-productnaam in de lijst met producten op de Admin Console te klikken.

1. Klik op de productieauteur-instantie voor AEM as a Cloud Service:
   ![Productprofielen voor AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

   Admin Console geeft twee productprofielen voor AEM as a Cloud Service weer: beheerders en gebruikers.
1. Klik op het productprofiel Beheerders en klik op **[!UICONTROL Add users]** om de gebruiker aan het productprofiel toe te voegen.
   ![Beheerdersprofiel](assets/aem-cs-admin-product-profile.png)

1. Klikken **[!UICONTROL Save]** om de wijzigingen op te slaan

## Stap 3: On-board Content Hub-middelen voor consumenten {#onboard-content-hub-consumer-users}

Consumenten van Content Hub hebben toegang tot middelen die beschikbaar zijn op de portal, maar kunnen geen nieuwe middelen toevoegen of bestaande middelen wijzigen.

Aan boord van gebruikers aan Content Hub:

1. [Open en klik op het Content Hub-gebruikersprofiel](#content-hub-instance-product-profile).

1. Klikken **[!UICONTROL Add users]** om gebruikers of gebruikersgroepen toe te voegen aan het productprofiel.

1. Klikken **[!UICONTROL Save]** om de wijzigingen op te slaan

Deze gebruikers hebben nu toegang tot de middelen die beschikbaar zijn op de Content Hub-portal.

>[!NOTE]
>
>U kunt alle geavanceerde bedrijfsfuncties gebruiken, zoals synchronisatie met externe identiteitsproviders.

Na het toevoegen van de aangewezen gebruikers die Admin Console gebruiken, kunnen de gebruikers tot Content Hub toegang hebben gebruikend de volgende verbinding:

`https://experience.adobe.com/#/assets/contenthub`

### E-mailberichten aan gebruikers uitschakelen {#disable-email-notifications}

Als beheerders e-mailmeldingen die naar gebruikers worden verzonden moeten uitschakelen wanneer ze aan het Content Hub-productprofiel worden toegevoegd:

Klik op het zoekpictogram naast de naam van het productprofiel en schakel de optie **[!UICONTROL Notify users by email]** schakelen.

![E-mailberichten uitschakelen](assets/disable-email-notifications.png)


## Stap 4: On-board Content Hub Asset Consumer-gebruikers met verzendmachtigingen (optioneel) {#onboard-content-hub-consumer-users-submission-rights}

Gebruikers van Content Hub-middelen met verzendmachtigingen kunnen:

* [Nieuwe merkgoedgekeurde middelen uploaden naar Content Hub](/help/assets/upload-brand-approved-assets.md).

* [Bestaande elementen wijzigen met behulp van Adobe Express en het middel opslaan in de gegevensopslagruimte](/help/assets/edit-images-content-hub.md). Elementen bewerken met Adobe Express is alleen beschikbaar als de gebruiker rechten op Adobe Express heeft.

Aan boord van Content Hub-gebruiker met verzendrechten:

1. [Nadat u de gebruiker aan het Content Hub-productprofiel hebt toegevoegd](#onboard-content-hub-consumer-users)Als u Experience Manager Assets-productprofielen wilt openen, klikt u op de AEM as a Cloud Service-productnaam in de lijst met producten op de Admin Console.

1. Klik op de productieauteur-instantie voor AEM as a Cloud Service:
   ![Productprofielen voor AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

   Admin Console geeft twee productprofielen voor AEM as a Cloud Service weer: beheerders en gebruikers.
1. Klik op het gebruikersproductprofiel en klik op **[!UICONTROL Add users]** om de gebruiker aan het productprofiel toe te voegen.
   ![Gebruikersprofiel](assets/aem-cs-user-product-profile.png)

1. Klikken **[!UICONTROL Save]** om de wijzigingen op te slaan

## Content Hub-distributeurs {#content-hub-asset-distributors}

Middelendistributeurs kunnen activa op AEM as a Cloud Service goedkeuren, zodat deze op Content Hub beschikbaar zijn.

Om de rol van de activaverdeler te vormen:

1. Open Experience Manager Assets-productprofielen door op de AEM as a Cloud Service-productnaam in de lijst met producten op de Admin Console te klikken.

1. Klik op de productieauteur-instantie voor AEM as a Cloud Service:
   ![Productprofielen voor AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

   Admin Console geeft twee productprofielen voor AEM as a Cloud Service weer: beheerders en gebruikers.
1. Klik op het gebruikersproductprofiel en klik op **[!UICONTROL Add users]** om de gebruiker aan het productprofiel toe te voegen.
   ![Gebruikersprofiel](assets/aem-cs-user-product-profile.png)

1. Klikken **[!UICONTROL Save]** om de wijzigingen op te slaan

   >[!NOTE]
   >
   > U hoeft niet aan de [Content Hub-productprofiel](#onboard-content-hub-consumer-users) voor de rol van vermogensdistributie.



