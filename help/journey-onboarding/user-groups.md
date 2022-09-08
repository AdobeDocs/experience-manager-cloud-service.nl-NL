---
title: Gebruikersgroepen voor meldingen
description: Leer hoe u een gebruikersgroep in de Admin Console kunt maken om de ontvangst van belangrijke e-mailberichten te beheren.
feature: Onboarding
role: Admin, User, Developer
source-git-commit: a663e21d100953f87c012a1d7962fb0e88e6a7f2
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---


# Gebruikersgroepen voor meldingen {#user-groups}

Leer hoe u een gebruikersgroep in de Admin Console kunt maken om de ontvangst van belangrijke e-mailberichten te beheren.

## Overzicht {#overview}

Van tijd tot tijd moet Adobe contact opnemen met betrekking tot hun AEM as a Cloud Service omgeving. Naast productmeldingen gebruikt Adobe soms ook e-mail voor dergelijke berichten. Er zijn twee soorten meldingen:

* **Melding van incidenten — Cloud Service** - Deze meldingen worden verzonden tijdens een incident of wanneer Adobe een probleem met de mogelijke beschikbaarheid in uw AEM as a Cloud Service omgeving heeft vastgesteld.
* **Proactieve melding - Cloud Service** - Deze meldingen worden verzonden wanneer een lid van het ondersteuningsteam van Adobe advies wil geven over een mogelijke optimalisatie of aanbeveling die uw AEM as a Cloud Service omgeving ten goede kan komen.

Voor de correcte gebruikers om deze berichten te ontvangen, moet u gebruikersgroepen vormen.

## Vereisten {#prerequisites}

Omdat gebruikersgroepen in de Admin Console worden gecreeerd en gehandhaafd, alvorens gebruikersgroepen voor berichten tot stand te brengen, moet u:

* Heeft machtigingen om groepslidmaatschappen toe te voegen en te bewerken.
* Een geldig Adobe Admin Console-profiel hebben.

## Nieuwe productprofielen voor Cloud Manager maken {#create-groups}

Als u de ontvangst van meldingen correct wilt instellen, moet u twee gebruikersgroepen maken. Deze stappen moeten slechts eenmaal worden uitgevoerd.

1. Aanmelden bij Admin Console bij [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. Van de **Overzicht** pagina, selecteert u **Adobe Experience Manager as a Cloud Service** van de **Producten en diensten** kaart.

   ![Gebruikersgroepen](assets/products_services.png)

1. Ga naar de **Cloud Manager** uit de lijst van alle instanties.

   ![Gebruikersgroep maken](assets/cloud_manager_instance.png)

1. De lijst met alle geconfigureerde productprofielen van Cloud Manager wordt weergegeven. Bijvoorbeeld:

   ![Gebruikersgroep maken](assets/cloud_manager_profiles.png)

1. Klik op Nieuw profiel en voer de volgende details in:

* Naam van productprofiel: Melding van incidenten - Cloud Service
* Weergavenaam: Melding van incidenten - Cloud Service
* Omschrijving: Het profiel van de Manager van de wolk voor de gebruikers die berichten tijdens een incident zullen ontvangen of wanneer Adobe een potentieel beschikbaarheidsprobleem met uw AEM as a Cloud Service milieu heeft geïdentificeerd.

1. Klik op Opslaan en herhaal stap 4 met de volgende details:

* Naam van productprofiel: Proactieve melding - Cloud Service
* Weergavenaam: Proactieve melding - Cloud Service
* Omschrijving: Het profiel van de Manager van de wolk voor de gebruikers die berichten zullen ontvangen wanneer een lid van het de steunteam van de Adobe raad over een potentiële optimalisering of aanbeveling willen verstrekken om met uw AEM as a Cloud Service omgevingsconfiguratie te doen.

>[!NOTE]
>
>Het is belangrijk dat de naam van het profiel Cloud Manager exact gelijk is aan de bovenstaande naam. Kopieer en plak de naam van het productprofiel uit de opgegeven beschrijving. Eventuele afwijkingen of typos leiden ertoe dat meldingen niet naar wens worden verzonden. Als er een fout optreedt of als er geen profielen zijn gedefinieerd, stuurt Adobe standaard een melding naar bestaande gebruikers die zijn toegewezen aan de profielen voor implementatiebeheer van Cloud Manager Developer (is dit of , en).

## De gebruikers toewijzen aan de nieuwe productprofielen voor meldingen {#add-users}

Nu de groepen zijn gemaakt, moet u de juiste gebruikers toewijzen. Dit kunt u doen wanneer u nieuwe gebruikers maakt of bestaande gebruikers bijwerkt.

### Nieuwe gebruikers toevoegen aan groepen {#new-user}

1. Identificeer de gebruiker(s) die of Incident of Proactieve Meldingen zou moeten ontvangen.

1. Aanmelden bij Admin Console bij [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com) als u nog niet bent aangemeld.

1. Van de **Overzicht** pagina, selecteert u **Adobe Experience Manager as a Cloud Service** van de **Producten en diensten** kaart.

   ![Gebruikers](assets/product_services.png)

1. Selecteer **Gebruikers** tabblad van de bovenste navigatie en selecteer vervolgens **Gebruiker toevoegen**.

![Gebruikers](assets/cloud_manager_add_user.png)

1. Voer in het dialoogvenster Gebruikers toevoegen aan uw team de e-mailadres in van de gebruiker die u wilt toevoegen.

* Als de gefedereerde id voor uw teamleden nog niet is ingesteld, selecteert u Adobe ID voor het id-type.
* Zie stap 7 als de gebruiker al bestaat.

1. Klik op de plusknop onder de knop **Producten selecteren** kop om productselectie te beginnen en selecteer **Adobe Experience Manager as a Cloud Service** en wijst **Melding van incidenten - Cloud Service** of **Proactieve melding - Cloud Service**, of beide aan de gebruiker.

1. Klikken **Opslaan** en er wordt een welkomstbericht verzonden naar de gebruiker die u hebt toegevoegd. De uitgenodigde gebruiker zal nu de berichten ontvangen.

1. Herhaal deze stappen voor de gebruikers in uw team die u de meldingen wilt ontvangen.

1. Zoek in het geval dat de gebruiker al bestaat de naam van de gebruiker en:

* Klik op de naam van de gebruiker.
* In de **Producten** sectie, klikt u op **Bewerken**.
* Klik op de knop Potlood in het dialoogvenster **Producten selecteren** kop om productselectie te beginnen en selecteer **Adobe Experience Manager as a Cloud Service** en wijst **Melding van incidenten - Cloud Service** of **Proactieve melding - Cloud Service**, of beide aan de gebruiker.
* Klikken **Opslaan** en er wordt een welkomstbericht verzonden naar de gebruiker die u hebt toegevoegd. De uitgenodigde gebruiker zal nu de berichten ontvangen.
