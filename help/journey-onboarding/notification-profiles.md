---
title: Meldingsprofielen
description: Leer hoe u gebruikersprofielen maakt in de Admin Console voor het beheer van de ontvangst van belangrijke e-mailberichten.
feature: Onboarding
role: Admin, User, Developer
exl-id: 4edecfcd-6301-4a46-98c7-eb5665f48995
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '982'
ht-degree: 0%

---


# Meldingsprofielen {#notification-profiles}

Leer hoe u gebruikersprofielen maakt in de Admin Console voor het beheer van de ontvangst van belangrijke e-mailberichten.

## Overzicht {#overview}

Van tijd tot tijd, contacteert de Adobe gebruikers betreffende hun AEM as a Cloud Service milieu&#39;s. Naast productmeldingen wordt in Adobe soms ook e-mail gebruikt voor meldingen. Er zijn twee typen e-mailmeldingen:

* **Melding incident** - Deze meldingen worden verzonden tijdens een incident of wanneer de Adobe een potentieel probleem met de beschikbaarheid van uw AEM as a Cloud Service omgeving heeft vastgesteld.
* **Proactieve kennisgeving** - Deze meldingen worden verzonden wanneer een medewerker van het ondersteuningsteam van de Adobe advies wil geven over een mogelijke optimalisatie of aanbeveling die uw AEM as a Cloud Service omgeving ten goede kan komen.

>[!NOTE]
>
>Het toewijzen van groepen aan proactieve meldingen wordt niet ondersteund. In plaats daarvan moet u gebruikers rechtstreeks toewijzen aan de productprofielen.

Voor de correcte gebruikers om deze berichten te ontvangen, moet u gebruikersprofielen vormen en toewijzen zoals die in dit document worden beschreven.

## Vereisten {#prerequisites}

Omdat gebruikersprofielen worden gemaakt en onderhouden in de Admin Console, moet u voordat u profielen voor meldingen maakt:

* Machtigingen hebben om leden toe te voegen en te profielen.
* Een geldig Adobe Admin Console-profiel hebben.

## Nieuwe productprofielen voor Cloud Manager maken {#create-profiles}

Maak twee gebruikersprofielen om de ontvangst van meldingen correct in te stellen. Deze stappen worden slechts één keer uitgevoerd.

1. Aanmelden bij Admin Console bij [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. Zorg ervoor dat u zich in de juiste organisatie bevindt.

1. Van de **Overzicht** pagina, selecteert u **Adobe Experience Manager as a Cloud Service** van de **Producten en diensten** kaart.

   ![Lijst van producten en diensten in de Admin Console](assets/products_services.png)

1. Ga naar de **Cloud Manager** uit de lijst van alle instanties.

   ![Lijst met instanties in de Admin Console](assets/cloud_manager_instance.png)

1. U kunt de lijst met alle geconfigureerde productprofielen van Cloud Manager bekijken.

   ![Productprofielen in de Admin Console](assets/cloud_manager_profiles.png)

1. Klikken **Nieuw profiel** en de volgende gegevens verstrekken:

   * **Naam van productprofiel**: `Incident Notification - Cloud Service`
   * **Weergavenaam**: `Incident Notification - Cloud Service`
   * **Beschrijving**: Cloud Manager-profiel voor gebruikers die meldingen ontvangen tijdens een incident of wanneer de Adobe een potentieel beschikbaarheidsprobleem met uw AEM as a Cloud Service omgeving heeft vastgesteld

1. Klikken **Opslaan**.

1. Klikken **Nieuw profiel** nogmaals de volgende gegevens verstrekken:

   * **Naam van productprofiel**: `Proactive Notification - Cloud Service`
   * **Weergavenaam**: `Proactive Notification - Cloud Service`
   * **Beschrijving**: Cloud Manager-profiel voor gebruikers die meldingen ontvangen wanneer een lid van het ondersteuningsteam voor Adoben advies wil geven over een mogelijke optimalisatie of aanbeveling voor de configuratie van uw AEM as a Cloud Service omgeving

1. Klikken **Opslaan**.

Uw twee nieuwe meldingsprofielen worden gemaakt.

>[!NOTE]
>
>Het is belangrijk dat de Cloud Manager **productprofielnaam** is precies hetzelfde als opgegeven. Kopieer en plak de opgegeven productprofielnaam om fouten te voorkomen. Eventuele afwijkingen of typos leiden ertoe dat meldingen niet naar wens worden verzonden.
>
>Als er een fout optreedt of als de profielen niet zijn gedefinieerd, wordt de Adobe standaard ingesteld op het op de hoogte brengen van bestaande gebruikers die aan de **Cloud Manager Developer** of **Implementatiebeheer** profielen.

## Gebruikers toewijzen aan de meldingsprofielen {#add-users}

Nu de profielen zijn gemaakt, moet u de juiste gebruikers toewijzen. Dit kunt u doen wanneer u nieuwe gebruikers maakt of bestaande gebruikers bijwerkt.

### Nieuwe gebruikers toevoegen aan profielen {#new-user}

Voer de volgende stappen uit om gebruikers toe te voegen voor wie gefedereerde id&#39;s nog niet zijn ingesteld.

1. Identificeer de gebruiker(s) die of incident of pro-actieve berichten zou moeten ontvangen.

1. Aanmelden bij Admin Console bij [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com) als u nog niet bent aangemeld.

1. Zorg ervoor dat u de juiste organisatie hebt geselecteerd.

1. Van de **Overzicht** pagina, selecteert u **Adobe Experience Manager as a Cloud Service** van de **Producten en diensten** kaart.

   ![Gebruikers](assets/product_services.png)

1. Als de gefederaliseerde id voor uw teamleden nog niet is ingesteld, selecteert u de optie **Gebruikers** tabblad van de bovenste navigatie en selecteer vervolgens **Gebruiker toevoegen**. Anders overslaan naar de sectie [Bestaande gebruikers toevoegen aan profielen.](#existing-users)

   ![Gebruikers](assets/cloud_manager_add_user.png)

1. In de **Gebruikers aan uw team toevoegen** voert u de e-mailid in van de gebruiker die u wilt toevoegen en selecteert u `Adobe ID` voor de **Type id**.

1. Klik op de plusknop onder de knop **Producten selecteren** kop om productselectie te beginnen.

1. Selecteren **Adobe Experience Manager as a Cloud Service** en wijs een of beide nieuwe profielen aan de gebruiker toe.

   * **Melding van voorvallen - Cloud Service**
   * **Proactieve melding - Cloud Service**

1. Klikken **Opslaan** en er wordt een welkomstbericht verzonden naar de gebruiker die u hebt toegevoegd.

De uitgenodigde gebruiker zal nu de berichten ontvangen. Herhaal deze stappen voor de gebruikers in uw team die u meldingen wilt ontvangen.

### Bestaande gebruikers toevoegen aan profielen {#existing-user}

Voer de volgende stappen uit om gebruikers toe te voegen voor wie gefedereerde id&#39;s al bestaan.

1. Identificeer de gebruiker(s) die of incident of pro-actieve berichten zou moeten ontvangen.

1. Aanmelden bij Admin Console bij [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com) als u nog niet bent aangemeld.

1. Zorg ervoor dat u de juiste organisatie hebt geselecteerd.

1. Van de **Overzicht** pagina, selecteert u **Adobe Experience Manager as a Cloud Service** van de **Producten en diensten** kaart.

1. Selecteer de **Gebruikers** van de bovenste navigatie.

1. Als de gefedereerde identiteitskaart reeds voor het teamlid bestaat die u aan een berichtprofiel wilt toevoegen, bepaal de plaats van die gebruiker in de lijst en klik het. Anders overslaan naar de sectie [Voeg nieuwe gebruikers toe aan profielen.](#add-user)

1. In de **Producten** in het venster met gebruikersgegevens klikt u op de knop voor ovaal en selecteert u **Bewerken**.

1. In de **Producten bewerken** venster, klik de potloodknoop onder **Producten selecteren** kop om productselectie te beginnen.

1. Selecteren **Adobe Experience Manager as a Cloud Service** en wijs een of beide nieuwe profielen aan de gebruiker toe.

   * **Melding van voorvallen - Cloud Service**
   * **Proactieve melding - Cloud Service**

1. Klikken **Opslaan** en er wordt een welkomstbericht verzonden naar de gebruiker die u hebt toegevoegd.

De uitgenodigde gebruiker zal nu de berichten ontvangen. Herhaal deze stappen voor de gebruikers in uw team die u meldingen wilt ontvangen.

## Aanvullende bronnen {#additional-resources}

Hieronder volgen aanvullende, optionele bronnen als u verder wilt gaan dan de inhoud van de instapreis.

* [Handelingencentrum](/help/operations/actions-center.md) - Gebruik het actiecentrum om incidenten en andere belangrijke informatie op een gemakkelijke manier aan te pakken.
