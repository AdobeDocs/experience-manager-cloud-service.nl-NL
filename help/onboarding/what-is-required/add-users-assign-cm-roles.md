---
title: 'Gebruikers toevoegen en rollen van Cloud Manager toewijzen '
description: Volg deze pagina om te leren hoe u gebruikers kunt toevoegen en toewijzen aan rollen in Cloud Manager
translation-type: tm+mt
source-git-commit: 6e8cf08ec3f85437a8472a45895f3818e473e98c
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 5%

---


# Gebruikers toevoegen en rollen voor Cloud Manager toewijzen {#add-users-assign}

Adobe zal een **Organisatie** herkenningsteken voor uw bedrijf in het Systeem van Adobe Identity Management (IMS) tot stand brengen, waar al uw gebruikers en hun toestemmingen kunnen worden beheerd. Elke gebruiker, die lid van deze organisatie moet zijn, en toegang tot om het even welke [!UICONTROL Experience Cloud] dienst zal worden verleend, zal zijn eigen **Adobe ID** moeten hebben.

## Werken met gebruikersrollen {#user-roles}

Voor veel functies in Cloud Manager zijn specifieke machtigingen vereist.

Cloud Manager definieert momenteel vier rollen voor gebruikers die de beschikbaarheid van specifieke functies bepalen:

* Business Owner
* Deployment Manager
* Program Manager
* Developer

>[!NOTE]
>De ontwikkelaar persona in Admin Console is niet gerelateerd aan de rol van de Ontwikkelaar in [!UICONTROL Cloud Manager].

De volgende tabel geeft een overzicht van de rollen:

| [!UICONTROL Cloud Manager] Rollen | Beschrijving |
|--- |--- |
| Zakelijke eigenaar | Verantwoordelijk voor het bepalen van KPIs, het goedkeuren van productieplaatsingen en het met voeten treden van belangrijke 3-tier mislukkingen. |
| Programmabeheerder | Gebruikt [!UICONTROL Cloud Manager] om teamopstelling uit te voeren, status te herzien en KPIs te bekijken. Kan belangrijke fouten met drie niveaus goedkeuren. |
| Implementatiebeheer | Beheert implementatiebewerkingen. Gebruikt [!UICONTROL Cloud Manager] om werkgebied/productie plaatsingen uit te voeren. Kan CI/CD pijpleidingen uitgeven. Kan belangrijke fouten met drie niveaus goedkeuren. Kan toegang krijgen tot de Git-opslagplaats. |
| Ontwikkelaar | Ontwikkelt en test aangepaste toepassingscode. Gebruikt hoofdzakelijk [!UICONTROL Cloud Manager] om status te bekijken. Kan toegang krijgen tot de Git-opslagplaats voor code commit. |
| Inhoudsauteur | Doorgaans heeft dit geen invloed op [!UICONTROL Cloud Manager]. Kan [!UICONTROL Cloud Manager] de Schakelaar van het Programma gebruiken (die van [!UICONTROL Experience Cloud]) is genavigeerd om tot AEM toegang te hebben. |

### Het profiel van het integratieproduct {#integration-product-profile}

Naast het bovenstaande maakt Cloud Manager automatisch een productprofiel met de naam &quot;Integrations - Cloud Service&quot;. Dit productprofiel wordt gebruikt voor de integratie tussen Adobe Experience Manager en andere Adobe-producten. Dit productprofiel **moet** niet worden geschrapt. Als u dit profiel per ongeluk verwijdert, moet het handmatig opnieuw worden gemaakt. De weergavenaam voor dit profiel **must** is `CM_CS_DEFAULT`.


## Machtigingen voor roldefinities {#permissions}

[!UICONTROL Cloud Manager] heeft pre-gevormde rollen met aangewezen toestemmingen. Een ontwikkelaar ontwikkelt bijvoorbeeld code en heeft de toestemming om de code naar **Git Repository** te duwen. Alternatief, heeft een bedrijfseigenaar verschillende toestemmingen die hen toestaan om de Zeer belangrijke Indicatoren van Prestaties (KPIs) te bepalen en plaatsingen goed te keuren.

Elk van de rollen heeft specifieke toestemmingen verbonden aan elke rol. De volgende tabel geeft een overzicht van de rollen, geeft een overzicht van de beschikbare functies en van de rollen die de functie kunnen uitvoeren.

| Machtiging | Beschrijving | Zakelijke eigenaar | Implementatiebeheer | Programmabeheerder | Ontwikkelaar |
|--- |--- |--- |--- |--- |--- |
| Programma toevoegen | Voeg een nieuw programma toe. | x |  |  |  |
| Omgeving maken | Maak Prod+Stage, Dev, omgevingen. | x | x |  |  |
| Omgeving bijwerken | Prod+werkgebied, Dev, omgevingen bijwerken. | x | x |  |  |
| Omgeving verwijderen | Verwijder Niet-prod, Dev, omgevingen. | x | x |  |  |
| Instellingen pijpleiding | Setup of Edit Pipeline. |  | x |  |  |
| Uitvoering pijpleiding | Start de pijplijn. | x | x |  |  |
| Uitvoering pijpleiding | Belangrijke 3-Tier-fouten afwijzen/goedkeuren. | x | x | x |  |
| Uitvoering pijpleiding | Geef GoLive-goedkeuring op. | x | x | x |  |
| Uitvoering pijpleiding | Plan de Implementatie van de Productie. | x | x | x |  |
| Pipet verwijderen | Hiermee wordt het verwijderen van een pijpleiding toegestaan. |  | x |  |  |
| Uitvoering annuleren | Huidige uitvoering annuleren. |  | x |  |  |
| Token voor persoonlijke toegang genereren | Toegangspoort. |  | x |  | x |

## Gebruikers {#add-users} toevoegen

>[!NOTE]
>U moet een systeembeheerder zijn om een gebruiker toe te voegen.

1. Als u een Beheerder van het Systeem bent, navigeer aan [Admin Console](https://adminconsole.adobe.com). U kunt ook naar Cloud Manager navigeren waar u de knop **Toegang beheren** ziet, zoals hieronder wordt beschreven.

1. Klik op de **knop Toegang beheren**, rechtsboven op de bestemmingspagina van Cloud Manager, om de Admin Console op een nieuw tabblad te openen.

   ![](/help/onboarding/getting-access-to-aem-in-cloud/assets/sys-admin5.png)

   Vanuit de **Admin Console** kunt u gebruikers toevoegen aan Cloud Manager en deze toewijzen aan Rol(en), ofwel Productprofielen in Admin Console.

1. Selecteer **Adobe Experience Manager als een Cloud Service** van **Producten en services** kaart zoals hieronder getoond.

   ![](/help/onboarding/what-is-required/assets/admin-console-1.png)

1. Selecteer het tabblad **Gebruikers** in de actiebalk en selecteer **Gebruiker toevoegen**.

   ![](/help/onboarding/what-is-required/assets/admin-console-2.png)

1. Selecteer de gebruiker en wijs de juiste rol(en) of productprofiel(en) van Cloud Manager aan de gebruiker toe, zoals hieronder wordt weergegeven.

   ![](/help/onboarding/what-is-required/assets/admin-console-3.png)

   >[!NOTE]
   >Verwijs naar de voorafgaande secties, [Rollen en Toestemmingen van de Gebruiker ](#user-roles) en [Toestemmingen verbonden aan de Definities van de Rol](#permissions) om ervoor te zorgen dat de juiste gebruikers de juiste Rol(en) in **Admin Console** worden toegewezen.

   Nu hebt u gebruikers aan Adobe Experience Manager toegevoegd als context van het Product van de Cloud Service en bent opstelling met de juiste Rollen of Profielen van het Product.

   Bijvoorbeeld, als u in de rol van a bent:

   * ***Bedrijfs Eigenaar***, hebt u de toestemming om een nieuw programma toe te voegen of een programma uit te geven, een milieu toe te voegen of bij te werken, de pijpleiding toe te voegen/uit te geven en om het even welke pijpleiding in werking te stellen, en code aan AEM milieu of codekwaliteit op te stellen.

   * ***De Manager*** van de plaatsing, hebt u de toestemming om een milieu toe te voegen of bij te werken, om het even welke pijpleiding in werking te stellen, en code aan AEM milieu of code-kwaliteit op te stellen.

   * ***De ontwikkelaar***, hebt u de toestemming om Persoonlijk Token van de Toegang te produceren om tot Git toegang te hebben.

      >[!NOTE]
      > Een gebruiker kan aan veelvoudige rollen worden toegewezen. Bijvoorbeeld het toewijzen van de rollen Bedrijfs van de Eigenaar en van de Manager van de Plaatsing aan een gebruiker geeft hen de combinatie of de som deze toestemmingen.
