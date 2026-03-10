---
title: Assets delen in  [!DNL the Content Hub]
description: Assets delen in  [!DNL the Content Hub]
role: User
badgeSaas: label="AEM Assets" type="Positive" tooltip="van toepassing op AEM Assets)."
exl-id: 5284d229-1596-40bf-aa5f-af4b6500ebdf
source-git-commit: 59f97fc6ded4274c27400f56b50b4a3329cc471a
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---

# Elementen delen in Content Hub {#search-assets-as-a-link}

Maak een koppeling naar geselecteerde elementen zodat u deze gemakkelijk met anderen kunt delen. Als geautoriseerde gebruiker van [!DNL Content Hub] selecteert u een of meer middelen die beschikbaar zijn in uw [!DNL Content Hub] -omgeving, genereert u een koppeling en stuurt u deze naar andere gebruikers van het type private of public.

>[!VIDEO](https://video.tv.adobe.com/v/3474890/?learn=on&enablevpops=on){transcript=true}

## Vereisten {#prerequisites}

[&#x200B; de gebruikers van Content Hub &#x200B;](deploy-content-hub.md#onboard-content-hub-users) kunnen tot een verbinding aan geselecteerde activa leiden en het met andere gebruikers delen.

## Elementen delen {#share-assets}

Voer de volgende stappen uit om een of meer elementen te delen met particuliere of openbare gebruikers:

1. Navigeer aan uw [!DNL Content Hub] homepage, selecteer één of meerdere activa en klik ![&#x200B; aandeel &#x200B;](/help/assets/assets/share.svg) **[!UICONTROL Share]** om één enkel geselecteerd element of een lijst van veelvoudige geselecteerde activa in het **[!UICONTROL Share assets]** dialoogvakje te tonen.

   U kunt activa ook selecteren en delen beschikbaar in ![&#x200B; inzamelingen &#x200B;](/help/assets/assets/Smock_Collection_18_N.svg) **[!UICONTROL Collections]**.

1. Een element weergeven of de lijst met beschikbare elementen in het dialoogvenster **[!UICONTROL Share assets]** bekijken. Klik ![&#x200B; unselect &#x200B;](/help/assets/assets/Close.svg) naast een activa om het uit de lijst te verwijderen.

1. Geef een titel en een optionele beschrijving op die de set geselecteerde elementen definiëren.

1. Selecteer **[!UICONTROL Period of expiration]** .

1. Selecteer onder **[!UICONTROL Who can access]** de toegangsopties en klik op **[!UICONTROL Get Link]** om een koppeling te genereren die u met de geselecteerde gebruikers wilt delen. Particuliere gebruikers moeten zich aanmelden bij hun [!DNL Content Hub] -omgeving om toegang te krijgen tot de pagina met gedeelde elementen. Openbare gebruikers kunnen als gasten toegang krijgen tot de pagina met gedeelde elementen zonder zich aan te melden bij [!DNL Content Hub] .

<!--1. Select a **[!UICONTROL period of expiration]** and click **[!UICONTROL Get Link]** to generate a link to share with private users. Private users sign in to their [!DNL Content Hub] environment to access the shared assets page.-->

![&#x200B; privé en openbare verbinding &#x200B;](/help/assets/assets/shared-link-for-assets.png)

<!--Enable the **[!UICONTROL Public Link]** toggle, select a **[!UICONTROL period of expiration]** and click **[!UICONTROL Generate Public Link]** to generate a link to share with public users. Public users, as guests, access the shared assets page without signing in to [!DNL Content Hub].-->

>[!NOTE]
> 
> [&#x200B; laat openbare verbinding toe delend van de configuratiepagina &#x200B;](/help/assets/configure-content-hub-ui-options.md#enable-public-link-sharing) om **[!UICONTROL Public Link]** knevel op het **[!UICONTROL Share assets]** dialoogvakje te tonen.

## Middelen delen delen vanaf de voorvertoningspagina {#share-asset-from-preview-page}

Voer de volgende stappen uit om een element te delen terwijl het wordt voorvertoond:

1. Navigeer naar de startpagina van [!DNL Content Hub] en klik op de elementminiatuur om een voorvertoning van het element weer te geven en de menuopties weer te geven in het rechterdeelvenster van het dialoogvenster.
1. Selecteer ![&#x200B; aandeel &#x200B;](/help/assets/assets/share.svg) om het **[!UICONTROL Share]** paneel te tonen.
   ![&#x200B; deel activa terwijl het voorvertonen van &#x200B;](/help/assets/assets/share-link-asset-preview.png)
1. Volg Stap 3 tot 5 in [&#x200B; activa van het Aandeel &#x200B;](#share-assets) sectie om de activa (Privé of openbaar) verbinding van dit **[!UICONTROL Share]** te produceren en te delen.

## Toegang tot gedeelde elementen {#access-shared-assets}

Open de pagina met gedeelde elementen via de koppeling en voer de volgende handelingen uit:

* Selecteer één of meerdere activa en klik ![&#x200B; download &#x200B;](/help/assets/assets/download-icon.svg) **[!UICONTROL Download]** om **[!UICONTROL Original]**, **[!UICONTROL Static]** of beide vertoningen van de beschikbare downloadopties te selecteren.
  ![](/help/assets/assets/download-shared-assets.png)
* Klik op de elementminiatuur om de metagegevens van het element weer te geven.
* Voor de gedeelde activa pagina ([&#x200B; die door een privé verbinding &#x200B;](#share-assets) wordt betreden), klik een activaduimnagel en selecteer ![&#x200B; download &#x200B;](/help/assets/assets/download-icon.svg) om de beschikbare dynamische vertoningen van de activa op het **[!UICONTROL Download]** paneel te selecteren en te bekijken alvorens hen te selecteren en te downloaden.
  ![](/help/assets/assets/download-renditions-shared-assets-page.png)

## Veelgestelde vragen {#faqs-share-assets-content-hub}

### Wat betekent het delen van activa in AEM Assets Content Hub?

Door middelen te delen in AEM Assets Content Hub kunnen geautoriseerde gebruikers eenvoudig een of meer assets of volledige verzamelingen met anderen delen door een koppeling te genereren. Deze koppeling kan worden verzonden naar particuliere gebruikers (die zich moeten aanmelden) of openbare gebruikers (die toegang kunnen krijgen als gasten), zodat ontvangers rechtstreeks toegang hebben tot de geselecteerde middelen en deze kunnen downloaden.

### Hoe kan ik middelen of verzamelingen delen met anderen die AEM Assets Content Hub gebruiken?

Als u elementen of verzamelingen wilt delen in AEM Assets Content Hub, navigeert u naar de Content Hub-startpagina, selecteert u een of meer elementen (of gaat u naar het tabblad Verzamelingen voor verzamelingen) en klikt u op het pictogram Delen. In het dialoogvenster Delen kunt u een voorvertoning van de elementen weergeven, desgewenst een koppeling verwijderen, een titel en beschrijving toevoegen, selecteren wie toegang heeft tot de koppeling (privé of openbaar), een vervalperiode instellen en vervolgens op Koppeling ophalen klikken om de deelbare URL te genereren en te kopiëren. De koppeling kan vervolgens naar teamleden of belanghebbenden worden verzonden.

### Welke toegangsopties zijn beschikbaar wanneer het delen van activa in AEM Assets Content Hub, en hoe verschillen zij?

In Content Hub kunt u kiezen uit twee toegangsopties voor gedeelde koppelingen: privé en openbaar. Voor persoonlijke koppelingen moeten ontvangers zich aanmelden bij hun Content Hub-omgeving om elementen weer te geven en te downloaden. Dit biedt extra beveiliging. Openbare koppelingen zijn toegankelijk voor iedereen met de koppeling, zonder aanmeldingsnaam. Elk verbindingstype komt met zijn eigen vervalmontages, zoals 24 uren aan één week voor openbare verbindingen en douanedata voor privé verbindingen.

### Is er een configuratie die door de beheerder wordt beheerd om openbare verbindingen voor activa in AEM Assets Content Hub te kunnen produceren?

Ja, kunnen de beheerders **toelaten of onbruikbaar maken Openbare verbinding** knevel beschikbaar in **Inzamelingen en het Delen** lusje op de Configuratie UI om de generatie van openbare verbindingen voor activa in AEM Assets Content Hub te beheren.

### Kan ik vervaldata instellen voor koppelingen naar gedeelde elementen in AEM Assets Content Hub, en waarom is dit belangrijk?

Ja, u kunt vervaldatums instellen voor zowel persoonlijke als openbare gedeelde koppelingen in AEM Assets Content Hub. Voor openbare koppelingen kunt u voorinstellingen kiezen van 24 uur tot en met een week, terwijl u met persoonlijke koppelingen een voorinstelling kunt selecteren of een aangepaste vervaldatum kunt instellen. Vervaldatums zijn belangrijk omdat de koppeling na het verlopen niet meer kan worden gebruikt om de elementen te openen of te downloaden. Hierdoor blijven de beveiliging en de controle van de inhoud behouden.

### Wat kunnen ontvangers doen met de koppeling voor gedeelde elementen die is gemaakt met AEM Assets Content Hub en zijn er opties voor het downloaden van verschillende uitvoeringen?

Ontvangers die een koppeling voor gedeelde elementen ontvangen, kunnen deze in hun browser openen om de aangeboden elementen voor te vertonen, te selecteren en te downloaden. Als rendities van elementen zijn ingeschakeld in AEM Assets Content Hub, kunnen ontvangers kiezen welke uitvoeringen (zoals Origineel of Statisch) ze willen downloaden. De elementen en vertoningen worden gedownload als een ZIP-bestand en metagegevens kunnen worden weergegeven door op de elementminiatuur te klikken. De koppeling blijft functioneel tot de ingestelde vervaldatum.




