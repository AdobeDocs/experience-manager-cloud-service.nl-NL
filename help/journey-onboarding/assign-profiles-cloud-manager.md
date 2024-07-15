---
title: Teamleden toewijzen aan Cloud Manager-productprofielen
description: Volg deze pagina om te leren hoe u teamleden kunt toewijzen aan Cloud Manager-productprofielen
feature: Onboarding
role: Admin, User, Developer
exl-id: 555688e5-f937-462c-9fcc-b90685f1882b
source-git-commit: 8ed477ec0c54bb0913562b9581e699c0bdc973ec
workflow-type: tm+mt
source-wordcount: '1520'
ht-degree: 0%

---


# Teamleden toewijzen aan Cloud Manager-productprofielen {#assign-team-members}

In dit deel van de [ onboarding reis, ](overview.md) leert u hoe te om teamleden aan de productprofielen van Cloud Manager toe te wijzen.

## Doelstelling {#objective}

In de vorige stap in deze reis, [ die tot de Admin Console toegang heeft, ](admin-console.md) u nu login aan de Admin Console leerde en uw voorrechten als systeembeheerder verifieerde. U kunt uw teamleden nu toegang geven tot Cloud Manager. U doet dit door productprofielen toe te wijzen.

Wanneer het verlenen van toegang tot een oplossing van de Adobe, wilt u hen niet noodzakelijk volledige toegang verlenen. Met productprofielen kan elke oplossing beschikken over een eigen set gebruikersrechten. U gebruikt de Admin Console om productprofielen toe te wijzen.

Je eerste stap is om gebruikers toegang te geven tot Cloud Manager. Cloud Manager ondersteunt u met instellingen voor bedrijfsontwikkeling en de speciaal daarvoor gebouwde CI-/CD-pijpleidingen, die zijn uitgerust voor grondig testen en de hoogste codekwaliteit voor uitzonderlijke ervaringen.

Nadat u dit document hebt gelezen, moet u:

* Begrijp welke productprofielen zijn.
* Begrijp wat Cloud Manager is.
* Ken de drie belangrijke het productprofielen van Cloud Manager: **BedrijfsEigenaar**, **Manager van de Plaatsing**, en **Ontwikkelaar**.
* Teamleden kunnen toewijzen aan Cloud Manager-productprofielen.

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

Als systeembeheerder, weet u dat een succesvol project van AEM as a Cloud Service niet alleen van de verwezenlijking van verbluffende inhoud gebruikend AEM, maar ook de ontwikkeling en de plaatsing van uw eigen douanecode en toepassingen afhangt om uw AEM inhoud te leveren.

Cloud Manager is een integraal onderdeel van AEM as a Cloud Service en wordt gebruikt voor het beheer van uw CI/CD-pijpleidingen voor het implementeren van code, het beheer van uw gegevensbanken voor code en het beheer van uw omgevingen.

Voordat uw team iets anders kan doen, moeten ze in Cloud Manager worden binnengehaald door hun de vereiste productprofielen te geven. In de volgende stappen ziet u waar u het Cloud Manager-productprofiel vindt met de Admin Console en hoe u deze toewijst aan uw teamleden.

## Cloud Manager-productprofielen bekijken {#review-product-profiles}

Met de Admin Console kunt u de lijst met Cloud Manager-profielen weergeven.

1. Login aan Adobe Admin Console bij [ adminconsole.adobe.com ](https://adminconsole.adobe.com/) en van de **pagina van het Overzicht**, uitgezochte **Adobe Experience Manager as a Cloud Service** van de **Producten en de diensten** kaart.

   ![ AEM als product ](/help/journey-onboarding/assets/assign-team1.png)

1. Navigeer aan de **instantie van Cloud Manager** van de lijst van alle instanties.

   ![Cloud Manager](/help/journey-onboarding/assets/assign-team2.png)

1. U kunt de lijst met vooraf geconfigureerde Cloud Manager-productprofielen bekijken.

   ![ Profielen van het Product ](/help/journey-onboarding/assets/assign-team3.png)

De belangrijkste profielen die in het kader van het eerste instapproces moeten worden toegewezen, zijn:

* **BedrijfsEigenaar** - Deze gebruikers leiden verschillende programma&#39;s.
* **Manager van de Plaatsing** - Deze gebruikers stellen code van uw bewaarplaatsen aan het runnen van AEM milieu&#39;s op.
* **Ontwikkelaar** - Deze gebruikers ontwikkelen uw douane AEM toepassingen en begaan code aan uw bewaarplaatsen.

Als u weet wat deze rollen zijn en wat ze doen, controleert u uw lijst met teamleden om te bepalen wie welk profiel nodig heeft. Houd in mening dat de gebruikers veelvoudige rollen in uw team kunnen hebben en vaak hebben en daarom ook veelvoudige profielen nodig hebben.

## Het productprofiel van de eigenaar van het bedrijf toewijzen {#assign-business-owner}

U bent nu bereid om gebruikers toe te voegen en hen toe te wijzen aan het **BedrijfsEigenaar** productprofiel.

1. Identificeer de gebruikers die Cloud Manager-programma&#39;s moeten beheren. Dit zijn uw **Bedrijfseigenaars**.

1. Logon aan de Admin Console bij `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` en op de **2} pagina van het Overzicht {, uitgezocht** Adobe Experience Manager as a Cloud Service **product van** Producten en de diensten **kaart.**

   ![ Producten en de diensten ](/help/journey-onboarding/assets/assign-team1.png)

1. Selecteer het **lusje van Gebruikers** van de hoogste navigatie, dan uitgezocht **voeg Gebruiker** toe.

   ![ voeg gebruiker ](/help/journey-onboarding/assets/assign-team4.png) toe

1. In **voeg gebruikers aan uw team** dialoog toe, ga e-mailidentiteitskaart van de gebruiker in u wilt toevoegen.

   * Als federated identiteitskaart voor uw teamleden nog niet opstelling is, uitgezochte **Adobe ID** voor het **Type van identiteitskaart**.

   ![ voeg gebruikersdetail ](/help/journey-onboarding/assets/assign-team5.png) toe

1. Klik plus knoop onder **Uitgezochte producten of gebruikersgroepen** rubriek om met productselectie te beginnen en **Adobe Experience Manager as a Cloud Service** te selecteren en **BedrijfsEigenaar** productprofiel aan de gebruiker toe te wijzen.

   * Wijs elke gebruiker aan minstens één productprofiel toe zodat de gebruiker tot Cloud Manager kan toegang hebben.
   * Herinner me om zich als systeembeheerder aan de **rol van BedrijfsEigenaar** toe te wijzen.

   ![ Toewijzend gebruikers ](/help/journey-onboarding/assets/assign-team6.png)

1. Klik **sparen** en een welkome e-mail wordt verzonden naar de gebruiker u toevoegde. De uitgenodigde gebruiker kan tot Cloud Manager toegang hebben door de verbinding in welkome e-mail te klikken en het ondertekenen binnen gebruikend hun Adobe ID.

1. Herhaal deze stappen voor de gebruikers in uw team.

Uw **BedrijfsEigenaar** is toegewezen en kan tot Cloud Manager nu toegang hebben. Vergeet niet om zich als systeembeheerder aan het **profiel van de Bedrijfs eigenaar** ook toe te wijzen.

## Het productprofiel van Deployment Manager toewijzen {#assign-deployment-manager}

1. Identificeer de gebruiker(s) die code moet opstellen.

1. Login aan de Admin Console bij `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` en op de **2} pagina van het Overzicht {uitgezocht 3} Adobe Experience Manager as a Cloud Service** product van de **Producten en de diensten** kaart.****

   ![ Producten en de diensten ](/help/journey-onboarding/assets/assign-team1.png)

1. Selecteer het **lusje van Gebruikers** van de hoogste navigatie en selecteer dan **Gebruiker** toevoegen.

   ![ voeg gebruiker ](/help/journey-onboarding/assets/assign-team4.png) toe

1. In **voeg gebruikers aan uw team** dialoog toe, ga e-mailidentiteitskaart van de gebruiker in u wilt toevoegen.

   * Als federated identiteitskaart voor uw teamleden nog niet opstelling is, uitgezochte **Adobe ID** voor het **Type van identiteitskaart**.

   ![ ga identiteitskaart ](/help/journey-onboarding/assets/assign-team5.png) binnen

1. Klik de plus knoop onder **Uitgezochte producten of gebruikersgroepen** rubriek om met productselectie te beginnen en **Adobe Experience Manager as a Cloud Service** te selecteren en **het productprofiel van de Manager van de Plaatsing** aan de gebruiker toe te wijzen.

   ![ wijs profiel ](/help/journey-onboarding/assets/assign-team6.png) toe

Uw **Manager van de Plaatsing** is toegewezen en kan tot Cloud Manager nu toegang hebben. Afhankelijk van uw toekomstige verantwoordelijkheden, kunt u of kan niet nodig ook om zich als systeembeheerder aan het **profiel van de Manager van de Plaatsing toe te wijzen 0}.**

## Het productprofiel voor ontwikkelaars toewijzen {#assign-developer}

1. Identificeer de gebruiker(s) die AEM toepassingen moet ontwikkelen en code moet beheren.

1. Login aan de Admin Console bij `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` en op de **2} pagina van het Overzicht {uitgezocht 3} Adobe Experience Manager as a Cloud Service** product van de **Producten en de diensten** kaart.****

   ![ Producten en de diensten ](/help/journey-onboarding/assets/assign-team1.png)

1. Selecteer het **lusje van Gebruikers** van de hoogste navigatie en selecteer dan **Gebruiker** toevoegen.

   ![ voeg gebruiker ](/help/journey-onboarding/assets/assign-team4.png) toe

1. In **voeg gebruikers aan uw team** dialoog toe, ga e-mailidentiteitskaart van de gebruiker in u wilt toevoegen.

   * Als federated identiteitskaart voor uw teamleden nog niet opstelling is, uitgezochte **Adobe ID** voor het **Type van identiteitskaart**.

   ![ toevoegen gebruiker - identiteitskaart ](/help/journey-onboarding/assets/assign-team5.png)

1. Klik de plus knoop onder **Uitgezochte producten of gebruikersgroepen** rubriek om met productselectie te beginnen en **Adobe Experience Manager as a Cloud Service** te selecteren en **het productprofiel van de Ontwikkelaar** aan de gebruiker toe te wijzen.

   ![ wijs profiel ](/help/journey-onboarding/assets/assign-team6.png) toe.

Uw **Ontwikkelaar** is toegewezen en kan tot Cloud Manager nu toegang hebben. Afhankelijk van uw toekomstige verantwoordelijkheden, kunt u of niet nodig ook om zich als systeembeheerder aan het **profiel van de Ontwikkelaar** toe te wijzen.

## Volgende functies {#whats-next}

Gefeliciteerd! Uw onlangs gevormd team van Cloud Manager (met inbegrip van u die aan het **profiel van de Bedrijfs eigenaar** wordt toegewezen) is opstelling. In de rol van **BedrijfsEigenaar**, bent u nu enkel één stap weg van het aanmelden aan Cloud Manager en het toelaten van de verwezenlijking van uw wolkenmiddelen.

In dit gedeelte van de instapreis leerde u over het toewijzen van uw teamleden aan profielen in de Admin Console. Nu moet u:

* Begrijp welke productprofielen zijn.
* Begrijp wat Cloud Manager is.
* Ken de drie belangrijke het productprofielen van Cloud Manager: **BedrijfsEigenaar**, **Manager van de Plaatsing**, en **Ontwikkelaar**.
* Teamleden kunnen toewijzen aan Cloud Manager-productprofielen.

U bent nu bereid om uw aan boord gaan reis door het document [ te herzien Cloud Manager van de Toegang, ](cloud-manager.md) waar u leert om tot Cloud Manager toegang te hebben en uw projectmiddelen tot stand te brengen.

## Aanvullende bronnen {#additional-resources}

U wordt aangeraden de instapreis voort te zetten zoals eerder beschreven. Dit zijn enkele extra bronnen als je een diep duik wilt maken over een bepaald onderwerp van deze reis.

* [ Inleiding van Cloud Manager ](/help/onboarding/cloud-manager-introduction.md) - Leer over Cloud Manager, de programma&#39;s van Cloud Manager, en milieu&#39;s.
* [ de Profielen van het Product van Cloud Manager ](/help/onboarding/aem-cs-team-product-profiles.md) - Leer over het team van AEM as a Cloud Service en productprofielen.
* [ de types van Identiteit op Adobe Admin Console ](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/identity.ug.html) - de hulp van het het identiteitsbeheersysteem van de Adobe leidt tot en beheert gebruikerstoegang tot toepassingen en de diensten. Met Adobe kunt u deze typen identiteiten of accounts verifiëren en autoriseren.

