---
title: Gebruikersrollen en -machtigingen
description: Deze pagina beschrijft gebruikersrollen en toestemmingen. Volg deze pagina om te leren hoe u gebruikers kunt toevoegen en toewijzen aan Cloud Manager Roles.
translation-type: tm+mt
source-git-commit: 98c7105aed1b9092a72005cf2cfab4bcf227601f
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 7%

---


# Gebruikersrollen en -machtigingen {#user-roles-permissions}

Adobe zal een **Organisatie** herkenningsteken voor uw bedrijf in het Systeem van Adobe Identity Management (IMS) tot stand brengen, waar al uw gebruikers en hun toestemmingen kunnen worden beheerd. Elke gebruiker, die lid van deze organisatie moet zijn, en toegang tot om het even welke [!UICONTROL Experience Cloud] dienst zal worden verleend, zal zijn eigen **Adobe ID** moeten hebben.

## Gebruikersrollen {#user-roles}

Voor veel functies in Cloud Manager zijn specifieke machtigingen vereist.

Veel functies in Cloud Manager vereisen specifieke machtigingen om te werken en beperken de handelingen die u uitvoert binnen de gebruikersinterface op basis van de toegewezen rollen en machtigingen. In sommige gevallen, als u niet de toestemming hebt om een actie te voeren, is de interfacecontrole aanwezig, maar gehandicapt.

Als er een actie is wilt u, maar niet, controleert [toestemmingen verbonden aan roldefinities](#permissions). Afhankelijk van uw doel, kunt u de Beheerder van het Systeem contacteren en om de rol verzoeken u wenst.

Cloud Manager definieert momenteel vier rollen voor gebruikers die de beschikbaarheid van specifieke functies bepalen:

* Business Owner
* Deployment Manager
* Program Manager
* Developer

>[!NOTE]
>De ontwikkelaar persona in Admin Console is niet gerelateerd aan de rol van de Ontwikkelaar in [!UICONTROL Cloud Manager].

## Roldefinities {#role-definitions}

De volgende tabel geeft een overzicht van de rollen:

| [!UICONTROL Cloud Manager] Rollen | Beschrijving |
|--- |--- |
| Zakelijke eigenaar | Verantwoordelijk voor het bepalen van KPIs, het goedkeuren van productieplaatsingen en het met voeten treden van belangrijke 3-tier mislukkingen. |
| Programmabeheerder | Gebruikt [!UICONTROL Cloud Manager] om teamopstelling uit te voeren, status te herzien en KPIs te bekijken. Kan belangrijke fouten met drie niveaus goedkeuren. |
| Implementatiebeheer | Beheert implementatiebewerkingen. Gebruikt [!UICONTROL Cloud Manager] om werkgebied/productie plaatsingen uit te voeren. Kan CI/CD pijpleidingen uitgeven. Kan belangrijke fouten met drie niveaus goedkeuren. Kan toegang krijgen tot de Git-opslagplaats. |
| Ontwikkelaar | Ontwikkelt en test aangepaste toepassingscode. Gebruikt hoofdzakelijk [!UICONTROL Cloud Manager] om status te bekijken. Kan toegang krijgen tot de Git-opslagplaats voor code commit. |
| Inhoudsauteur | Doorgaans heeft dit geen invloed op [!UICONTROL Cloud Manager]. Kan [!UICONTROL Cloud Manager] de Schakelaar van het Programma gebruiken (die van [!UICONTROL Experience Cloud]) is genavigeerd om tot AEM toegang te hebben. |

### Uw rollen bekijken {#view-roles}

Als u uw rol in Cloud Manager wilt weergeven, meldt u zich aan bij de interface van Cloud Manager, selecteert u het profielpictogram in de rechterbovenhoek en selecteert u **Gebruikersrollen**, zoals in de onderstaande afbeelding wordt getoond.

![](/help/onboarding/what-is-required/assets/admin-console-9.png)

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