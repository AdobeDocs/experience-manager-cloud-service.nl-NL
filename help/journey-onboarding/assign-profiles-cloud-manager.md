---
title: Teamleden toewijzen aan productprofielen van Cloud Manager
description: Volg deze pagina om te leren hoe u teamleden kunt toewijzen aan productprofielen van Cloud Manager
feature: Onboarding
role: Admin, User, Developer
exl-id: 555688e5-f937-462c-9fcc-b90685f1882b
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '1528'
ht-degree: 0%

---


# Teamleden toewijzen aan productprofielen van Cloud Manager {#assign-team-members}

In dit deel van het [aan boord gaan,](overview.md) leert u hoe u teamleden kunt toewijzen aan productprofielen van Cloud Manager.

## Doelstelling {#objective}

In de vorige stap van deze reis: [Toegang tot de Admin Console,](admin-console.md) u hebt nu login aan de Admin Console geleerd en uw voorrechten als systeembeheerder verifiëren. U kunt uw teamleden nu toegang verlenen tot Cloud Manager. U doet dit door productprofielen toe te wijzen.

Wanneer het verlenen van toegang tot een oplossing van de Adobe, wilt u hen niet noodzakelijk volledige toegang verlenen. Met productprofielen kan elke oplossing beschikken over een eigen set gebruikersrechten. U gebruikt de Admin Console om productprofielen toe te wijzen.

In de eerste stap geeft u gebruikers toegang tot Cloud Manager. Cloud Manager ondersteunt u met instellingen voor bedrijfsontwikkeling en de speciaal daarvoor gebouwde CI-/CD-pijpleidingen, die zijn uitgerust voor grondig testen en de hoogste codekwaliteit voor uitzonderlijke ervaringen.

Nadat u dit document hebt gelezen, moet u:

* Begrijp welke productprofielen zijn.
* Begrijp wat Cloud Manager is.
* De drie belangrijke productprofielen van Cloud Manager kennen: **Zakelijke eigenaar**, **Implementatiebeheer**, en **Ontwikkelaar**.
* Teamleden kunnen toewijzen aan productprofielen van Cloud Manager.

## Vereisten {#prerequisites}

Om teamleden aan productprofielen toe te wijzen, moet u details over uw teamleden hebben, die tot AEM as a Cloud Service moeten toegang hebben, met inbegrip van:

* Namen
* E-mailadressen
* Taken en verantwoordelijkheden

>[!TIP]
>
>Met het oog op het instappen, adviseert de Adobe dat u aanvankelijk gebruikers toevoegt die aan de directe taken, zoals beheerders, ontwikkelaars, en inhoudsauteurs zullen deelnemen.
>
>U kunt het instapproces voortzetten zonder alle gebruikers toe te voegen. Nadat u het instappen hebt gebeëindigd, kunt u extra gebruikers toevoegen.

## Productprofielen {#product-profiles}

Wanneer het verlenen van toegang tot een oplossing van de Adobe, wilt u hen niet noodzakelijk volledige toegang verlenen. De profielen van het product laten elke oplossing toe om zijn eigen reeks gebruikerstoestemmingen te hebben die gebruikend de Admin Console worden geplaatst.

Bijvoorbeeld, later in deze reis zult u de Admin Console gebruiken om gebruikers toegang tot de AEM oplossing te verlenen door productprofielen voor AEM beheerders en AEM auteurs toe te wijzen.

De volgende stap bestaat echter uit het toekennen van productprofielen, zodat uw teamleden eerst toegang hebben tot Cloud Manager.

## Cloud Manager {#cloud-manager}

Als systeembeheerder, weet u dat een succesvol AEM as a Cloud Service project niet alleen van de verwezenlijking van verbluffende inhoud gebruikend AEM, maar ook de ontwikkeling en de plaatsing van uw eigen douanecode en toepassingen afhangt om uw AEM inhoud te leveren.

Cloud Manager is een integraal onderdeel van AEM as a Cloud Service en wordt gebruikt voor het beheer van uw CI/CD-pijpleidingen voor de implementatie van code, het beheer van uw gegevensopslagruimten voor code en het beheer van uw omgevingen.

Voordat uw team iets anders kan doen, moet u deze bestanden opnemen in Cloud Manager door ze de vereiste productprofielen te geven. In de volgende stappen ziet u waar u het productprofiel van Cloud Manager vindt met de Admin Console en hoe u deze toewijst aan uw teamleden.

## Productprofielen van Cloud Manager bekijken {#review-product-profiles}

Met de Admin Console kunt u de lijst met Cloud Manager-profielen weergeven.

1. Aanmelden bij Adobe Admin Console [adminconsole.adobe.com](https://adminconsole.adobe.com/) en van de **Overzicht** pagina, selecteert u **Adobe Experience Manager as a Cloud Service** van de **Producten en diensten** kaart.

   ![AEM als product](/help/journey-onboarding/assets/assign-team1.png)

1. Ga naar de **Cloud Manager** uit de lijst van alle instanties.

   ![Cloud Manager](/help/journey-onboarding/assets/assign-team2.png)

1. U kunt de lijst met vooraf geconfigureerde productprofielen van Cloud Manager bekijken.

   ![Productprofielen](/help/journey-onboarding/assets/assign-team3.png)

De belangrijkste profielen die in het kader van het eerste instapproces moeten worden toegewezen, zijn:

* **Zakelijke eigenaar** - Deze gebruikers beheren verschillende programma&#39;s.
* **Implementatiebeheer** - Deze gebruikers implementeren code van uw opslagruimten naar AEM omgevingen.
* **Ontwikkelaar** - Deze gebruikers ontwikkelen uw aangepaste AEM toepassingen en wijzen code toe aan uw opslagruimten.

Als u weet wat deze rollen zijn en wat ze doen, controleert u uw lijst met teamleden om te bepalen wie welk profiel nodig heeft. Houd in mening dat de gebruikers veelvoudige rollen in uw team kunnen hebben en vaak hebben en daarom ook veelvoudige profielen nodig hebben.

## Het productprofiel van de eigenaar van het bedrijf toewijzen {#assign-business-owner}

U kunt nu gebruikers toevoegen en deze toewijzen aan de **Zakelijke eigenaar** productprofiel.

1. Identificeer de gebruikers die Cloud Manager-programma&#39;s moeten beheren. Dit zijn uw **Bedrijfseigenaren**.

1. Log in bij de Admin Console `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` en op de **Overzicht** pagina, selecteert u **Adobe Experience Manager as a Cloud Service** product van **Producten en diensten** kaart.

   ![Producten en diensten](/help/journey-onboarding/assets/assign-team1.png)

1. Selecteer de **Gebruikers** tabblad van de bovenste navigatie en selecteer vervolgens **Gebruiker toevoegen**.

   ![Gebruiker toevoegen](/help/journey-onboarding/assets/assign-team4.png)

1. In de **Gebruikers aan uw team toevoegen** voert u de e-mailadres in van de gebruiker die u wilt toevoegen.

   * Als de federatieve id voor uw teamleden nog niet is ingesteld, selecteert u **Adobe ID** voor de **Type id**.

   ![Gebruikersdetails toevoegen](/help/journey-onboarding/assets/assign-team5.png)

1. Klik op de plusknop onder de knop **Producten of gebruikersgroepen selecteren** kop om productselectie te beginnen en selecteer **Adobe Experience Manager as a Cloud Service** en toewijzen **Zakelijke eigenaar** productprofiel voor de gebruiker.

   * Wijs elke gebruiker aan minstens één productprofiel toe zodat de gebruiker tot Cloud Manager kan toegang hebben.
   * Herinner me als systeembeheerder aan toe te wijzen **Zakelijke eigenaar** rol.

   ![Gebruikers toewijzen](/help/journey-onboarding/assets/assign-team6.png)

1. Klikken **Opslaan** en er wordt een welkomstbericht verzonden naar de gebruiker die u hebt toegevoegd. De uitgenodigde gebruiker kan tot de Manager van de Wolk toegang hebben door de verbinding in welkome e-mail te klikken en zich binnen te ondertekenen gebruikend hun Adobe ID.

1. Herhaal deze stappen voor de gebruikers in uw team.

Uw **Zakelijke eigenaar** is toegewezen en heeft nu toegang tot Cloud Manager. Vergeet niet om zich als systeembeheerder aan te wijzen **Zakelijke eigenaar** profiel.

## Het productprofiel van Deployment Manager toewijzen {#assign-deployment-manager}

1. Identificeer de gebruiker(s) die code moet opstellen.

1. Log in bij de Admin Console op `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` en op de **Overzicht** pagina selecteren **Adobe Experience Manager as a Cloud Service** product uit de **Producten en diensten** kaart.

   ![Producten en diensten](/help/journey-onboarding/assets/assign-team1.png)

1. Selecteer de **Gebruikers** van de hoogste navigatie en selecteer dan **Gebruiker toevoegen**.

   ![Gebruiker toevoegen](/help/journey-onboarding/assets/assign-team4.png)

1. In de **Gebruikers aan uw team toevoegen** voert u de e-mailadres in van de gebruiker die u wilt toevoegen.

   * Als de federatieve id voor uw teamleden nog niet is ingesteld, selecteert u **Adobe ID** voor de **Type id**.

   ![ID invoeren](/help/journey-onboarding/assets/assign-team5.png)

1. Klik op de plusknop onder de knop **Producten of gebruikersgroepen selecteren** kop om productselectie te beginnen en selecteer **Adobe Experience Manager as a Cloud Service** en toewijzen **Implementatiebeheer** productprofiel voor de gebruiker.

   ![Profiel toewijzen](/help/journey-onboarding/assets/assign-team6.png)

Uw **Implementatiebeheer** is toegewezen en heeft nu toegang tot Cloud Manager. Afhankelijk van uw toekomstige verantwoordelijkheden, kunt u of kan niet te hoeven ook om zich als systeembeheerder aan toe te wijzen **Implementatiebeheer** profiel.

## Het productprofiel voor ontwikkelaars toewijzen {#assign-developer}

1. Identificeer de gebruiker(s) die AEM toepassingen moet ontwikkelen en code moet beheren.

1. Log in bij de Admin Console op `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` en op de **Overzicht** pagina selecteren **Adobe Experience Manager as a Cloud Service** product uit de **Producten en diensten** kaart.

   ![Producten en diensten](/help/journey-onboarding/assets/assign-team1.png)

1. Selecteer de **Gebruikers** van de hoogste navigatie en selecteer dan **Gebruiker toevoegen**.

   ![Gebruiker toevoegen](/help/journey-onboarding/assets/assign-team4.png)

1. In **Gebruikers aan uw team toevoegen** voert u de e-mailadres in van de gebruiker die u wilt toevoegen.

   * Als de federatieve id voor uw teamleden nog niet is ingesteld, selecteert u **Adobe ID** voor de **Type id**.

   ![Gebruikersnaam toevoegen](/help/journey-onboarding/assets/assign-team5.png)

1. Klik op de plusknop onder de knop **Producten of gebruikersgroepen selecteren** kop om productselectie te beginnen en selecteer **Adobe Experience Manager as a Cloud Service** en toewijzen **Ontwikkelaar** productprofiel voor de gebruiker.

   ![Profiel toewijzen](/help/journey-onboarding/assets/assign-team6.png).

Uw **Ontwikkelaar** is toegewezen en heeft nu toegang tot Cloud Manager. Afhankelijk van uw toekomstige verantwoordelijkheden, kunt u of kan niet te hoeven ook om zich als systeembeheerder aan toe te wijzen **Ontwikkelaar** profiel.

## Volgende functies {#whats-next}

Gefeliciteerd! Uw nieuwe team van Cloud Manager (inclusief uzelf die is toegewezen aan **Zakelijke eigenaar** is ingesteld. In de rol van **Zakelijke eigenaar** En u bent nu maar één stap verwijderd van aanmelden bij Cloud Manager en het maken van uw cloudbronnen mogelijk maken.

In dit gedeelte van de instapreis leerde u over het toewijzen van uw teamleden aan profielen in de Admin Console. Nu moet u:

* Begrijp welke productprofielen zijn.
* Begrijp wat Cloud Manager is.
* De drie belangrijke productprofielen van Cloud Manager kennen: **Zakelijke eigenaar**, **Implementatiebeheer**, en **Ontwikkelaar**.
* Teamleden kunnen toewijzen aan productprofielen van Cloud Manager.

U bent nu klaar om uw instapreis voort te zetten door het document opnieuw te bekijken [Access Cloud Manager,](cloud-manager.md) Hier leert u hoe u toegang krijgt tot Cloud Manager en hoe u uw projectbronnen maakt.

## Aanvullende bronnen {#additional-resources}

Het verdient aanbeveling de hierboven beschreven instapreis voort te zetten. Dit zijn enkele extra bronnen als u een diepgaande duik wilt maken over een bepaald onderwerp van deze reis.

* [Introductie van Cloud Manager](/help/onboarding/cloud-manager-introduction.md) - Meer informatie over Cloud Manager, Cloud Manager-programma&#39;s en omgevingen.
* [Productprofielen van Cloud Manager](/help/onboarding/aem-cs-team-product-profiles.md) - Meer informatie over AEM as a Cloud Service teams en productprofielen.
* [Identiteitstypen in Adobe Admin Console](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/identity.ug.html) - Met het identiteitsbeheersysteem van de Adobe kunnen beheerders de toegang van gebruikers tot toepassingen en services creëren en beheren. Met Adobe kunt u deze typen identiteiten of accounts verifiëren en autoriseren.

