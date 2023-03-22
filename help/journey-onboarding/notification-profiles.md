---
title: Meldingsprofielen
description: Leer hoe u gebruikersprofielen maakt in de Admin Console voor het beheer van de ontvangst van belangrijke e-mailberichten.
feature: Onboarding
role: Admin, User, Developer
exl-id: 4edecfcd-6301-4a46-98c7-eb5665f48995
source-git-commit: f7b3dec6380266a35f1bf7d90e0195277dd37335
workflow-type: tm+mt
source-wordcount: '934'
ht-degree: 0%

---


# Meldingsprofielen {#notification-profiles}

Leer hoe u gebruikersprofielen maakt in de Admin Console voor het beheer van de ontvangst van belangrijke e-mailberichten.

## Overzicht {#overview}

Van tijd tot tijd moet Adobe contact opnemen met gebruikers over hun AEM as a Cloud Service omgeving. Naast productmeldingen gebruikt Adobe soms ook e-mail voor berichten. Er zijn twee typen e-mailmeldingen:

* **Melding incident** - Deze meldingen worden verzonden tijdens een incident of wanneer Adobe een probleem met de mogelijke beschikbaarheid in uw AEM as a Cloud Service omgeving heeft vastgesteld.
* **Proactieve kennisgeving** - Deze meldingen worden verzonden wanneer een lid van het ondersteuningsteam van Adobe advies wil geven over een mogelijke optimalisatie of aanbeveling die uw AEM as a Cloud Service omgeving ten goede kan komen.

Voor de correcte gebruikers om deze berichten te ontvangen, moet u gebruikersprofielen vormen en toewijzen zoals die in dit document worden beschreven.

## Vereisten {#prerequisites}

Omdat gebruikersprofielen worden gemaakt en onderhouden in de Admin Console, moet u voordat u profielen voor meldingen maakt:

* Machtigingen hebben om leden toe te voegen en te profielen.
* Een geldig Adobe Admin Console-profiel hebben.

## Nieuwe productprofielen voor Cloud Manager maken {#create-profiles}

Als u de ontvangst van meldingen correct wilt instellen, moet u twee gebruikersprofielen maken. Deze stappen moeten slechts eenmaal worden uitgevoerd.

1. Aanmelden bij Admin Console bij [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. Zorg ervoor dat u zich in de juiste organisatie bevindt.

1. Van de **Overzicht** pagina, selecteert u **Adobe Experience Manager as a Cloud Service** van de **Producten en diensten** kaart.

   ![Lijst van producten en diensten in de Admin Console](assets/products_services.png)

1. Ga naar de **Cloud Manager** uit de lijst van alle instanties.

   ![Lijst met instanties in de Admin Console](assets/cloud_manager_instance.png)

1. De lijst met alle geconfigureerde productprofielen van Cloud Manager wordt weergegeven.

   ![Productprofielen in de Admin Console](assets/cloud_manager_profiles.png)

1. Klikken **Nieuw profiel** en de volgende gegevens verstrekken:

   * **Naam van productprofiel**: `Incident Notification - Cloud Service`
   * **Weergavenaam**: `Incident Notification - Cloud Service`
   * **Beschrijving**: Het profiel van de Manager van de wolk voor de gebruikers die berichten tijdens een incident zullen ontvangen of wanneer Adobe een potentieel beschikbaarheidsprobleem met uw AEM as a Cloud Service milieu heeft geïdentificeerd

1. Klikken **Opslaan**.

1. Klikken **Nieuw profiel** nogmaals de volgende gegevens verstrekken:

   * **Naam van productprofiel**: `Proactive Notification - Cloud Service`
   * **Weergavenaam**: `Proactive Notification - Cloud Service`
   * **Beschrijving**: Het profiel van de Manager van de wolk voor de gebruikers die berichten zullen ontvangen wanneer een lid van het de ondersteuningsteam van Adobe raad over een potentiële optimalisering of aanbeveling willen verstrekken om met uw AEM as a Cloud Service omgevingsconfiguratie te doen

1. Klikken **Opslaan**.

Uw twee nieuwe meldingsprofielen worden gemaakt.

>[!NOTE]
>
>Het is belangrijk dat de Cloud Manager **productprofielnaam** is precies hetzelfde als opgegeven. Kopieer en plak de opgegeven productprofielnaam om fouten te voorkomen. Eventuele afwijkingen of typos leiden ertoe dat meldingen niet naar wens worden verzonden.
>
>Als er een fout optreedt of als de profielen niet zijn gedefinieerd, meldt Adobe de bestaande gebruikers die aan de profielen zijn toegewezen standaard **Cloud Manager Developer** of **Implementatiebeheer** profielen.

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

   * **Melding van incidenten - Cloud Service**
   * **Proactieve melding - Cloud Service**

1. Klikken **Opslaan** en er wordt een welkomstbericht verzonden naar de gebruiker die u hebt toegevoegd.

De uitgenodigde gebruiker zal nu de berichten ontvangen. Herhaal deze stappen voor de gebruikers in uw team die u meldingen wilt ontvangen.

### Bestaande gebruikers toevoegen aan profielen {#existing-user}

Voer de volgende stappen uit om gebruikers toe te voegen voor wie gefedereerde id&#39;s al bestaan.

1. Identificeer de gebruiker(s) die of incident of pro-actieve berichten zou moeten ontvangen.

1. Aanmelden bij Admin Console bij [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com) als u nog niet bent aangemeld.

1. Zorg ervoor dat u de juiste organisatie hebt geselecteerd.

1. Van de **Overzicht** pagina, selecteert u **Adobe Experience Manager as a Cloud Service** van de **Producten en diensten** kaart.

1. Selecteer **Gebruikers** van de bovenste navigatie.

1. Als de gefedereerde identiteitskaart reeds voor het teamlid bestaat die u aan een berichtprofiel wilt toevoegen, bepaal de plaats van die gebruiker in de lijst en klik het. Anders overslaan naar de sectie [Voeg nieuwe gebruikers toe aan profielen.](#add-user)

1. In de **Producten** in het venster met gebruikersgegevens klikt u op de knop voor ovaal en selecteert u **Bewerken**.

1. In de **Producten bewerken** venster, klikt u op de potloodknop onder de **Producten selecteren** kop om productselectie te beginnen.

1. Selecteren **Adobe Experience Manager as a Cloud Service** en wijs een of beide nieuwe profielen aan de gebruiker toe.

   * **Melding van incidenten - Cloud Service**
   * **Proactieve melding - Cloud Service**

1. Klikken **Opslaan** en er wordt een welkomstbericht verzonden naar de gebruiker die u hebt toegevoegd.

De uitgenodigde gebruiker zal nu de berichten ontvangen. Herhaal deze stappen voor de gebruikers in uw team die u meldingen wilt ontvangen.
