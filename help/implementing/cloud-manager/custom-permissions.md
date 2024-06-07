---
title: Aangepaste machtigingen
description: Leer hoe u douanetoestemmingen kunt gebruiken om profielen van de douanetoestemming met configureerbare toestemmingen tot stand te brengen om toegang tot programma's, pijpleidingen, en milieu's voor de gebruikers van de Managers van de Wolk te beperken.
exl-id: 167da985-7f19-45b3-90a3-884817907da2
solution: Experience Manager
feature: Security, Developing
role: Admin, Architect, Developer
source-git-commit: bc92ed7acefbbd906b0986ea0b6b96fa6d8422de
workflow-type: tm+mt
source-wordcount: '1515'
ht-degree: 1%

---


# Aangepaste machtigingen {#custom-permissions}

Leer hoe u douanetoestemmingen kunt gebruiken om profielen van de douanetoestemming met configureerbare toestemmingen tot stand te brengen om toegang tot programma&#39;s, pijpleidingen, en milieu&#39;s voor de gebruikers van de Managers van de Wolk te beperken.

## Inleiding {#introduction}

Cloud Manager heeft een set vooraf gedefinieerde rollen die de toegang tot verschillende functies van cloud Manager regelen:

* Business Owner
* Program Manager
* Deployment Manager
* Developer

Met aangepaste machtigingen kunnen gebruikers aangepaste machtigingsprofielen maken met configureerbare machtigingen om de toegang voor gebruikers van Cloud Managers te beperken tot programma&#39;s, pijpleidingen en omgevingen.

>[!TIP]
>
>Zie voor meer informatie over vooraf gedefinieerde rollen [as a Cloud Service teams en productprofielen AEM](/help/onboarding/aem-cs-team-product-profiles.md).

## Aangepaste machtigingen gebruiken {#using}

Voor het maken en gebruiken van uw eigen aangepaste machtigingen zijn drie stappen vereist:

1. [Een productprofiel maken.](#create)
1. [Wijs aangepaste machtigingen toe aan het productprofiel.](#assign-permissions)
1. [Gebruikers toewijzen aan het productprofiel.](#assign-users)

In deze sectie worden deze stappen beschreven. Het kan handig zijn om te zien [Voorwaarden](#terms) en [Configureerbare machtigingen](#configurable-permissions) secties als u uw eigen aangepaste machtigingen maakt.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service kan alleen profielen maken en machtigingen voor Cloud Manager beheren als Admin Console beschikt over de rechten van productbeheerders.

### Een nieuw productprofiel maken {#create}

Maak eerst een productprofiel voordat u aangepaste machtigingen kunt toewijzen.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/).

1. Selecteer op de bestemmingspagina van Cloud Manager de optie **Toegang beheren** knop.

![Knop Toegang beheren](assets/manage-access.png)

1. U wordt omgeleid naar de **Producten** tabblad van de Admin Console, waar u gebruikers en machtigingen voor cloudbeheer kunt beheren. Selecteer in de Admin Console de optie **Nieuw profiel** knop.

![Knop Nieuw profiel](assets/admin-console-new-profile.png)

1. Geef de algemene details over het profiel op.

   * **Naam van productprofiel** - Een beschrijvende naam voor het profiel
   * **Weergavenaam** - Een afgekorte naam die wordt weergegeven in de gebruikersinterface (opties)
   * **Beschrijving** - Een informatieve beschrijving van het profiel waarin het doel van het profiel wordt toegelicht (optioneel)
   * **Gebruikers via e-mail op de hoogte stellen** - Als deze optie is geselecteerd, krijgen gebruikers een e-mail te zien wanneer ze uit dit profiel worden toegevoegd of verwijderd.

1. Selecteren **Opslaan** wanneer voltooid.

Het nieuwe productprofiel wordt opgeslagen en wordt weergegeven in de lijst met productprofielen in de Admin Console.

### Aangepaste machtigingen toewijzen aan profiel {#assign-permissions}

Nu u een nieuw productprofiel hebt, kunt u er aangepaste machtigingen aan toewijzen.

1. Selecteer in de Admin Console de naam van het dialoogvenster [nieuw productprofiel dat u hebt gemaakt](#create).

1. Selecteer in het venster dat wordt geopend de optie **Machtigingen** om een lijst met bewerkbare machtigingen weer te geven.

   ![Bewerkbare machtigingen](assets/permissions-tab.png)

1. Selecteer de **Bewerken** koppeling van een machtiging zodat u deze kunt bewerken.

1. De **Machtiging bewerken** wordt geopend.
   * De machtigingen die u in de vorige stap hebt geselecteerd, worden in de linkerkolom geselecteerd.
   * De machtigingsitems die beschikbaar zijn voor toewijzing voor de machtiging bevinden zich in de middelste kolom met het label **Beschikbare machtiging** Items.
   * De toegewezen toestemmingspunten zijn in de juiste kolom geëtiketteerd **Opgenomen machtigingsitems**.

   ![Machtigingsitems bewerken](assets/edit-permission-items.png)

1. Selecteer de plus (`+`) naast het machtigingsitem zodat u dit aan de kolom kunt toevoegen **Opgenomen machtigingsitems**.

   * Selecteer de `i` pictogram naast een machtigingsitem als u er meer over wilt weten.

1. Selecteer de **Alles toevoegen** aan de bovenkant van de **Beschikbare machtigingen** zodat u alle machtigingen kunt toevoegen.

1. Selecteren **Opslaan** als u klaar bent met het definiëren van de machtigingsitems voor uw nieuwe productprofiel.

Uw nieuwe productprofiel wordt nu opgeslagen met de aangepaste machtigingen.

### Gebruikers toewijzen aan aangepaste machtigingen {#assign-users}

U kunt nu gebruikers toewijzen aan het nieuwe productprofiel dat u met aangepaste machtigingen hebt gemaakt.

1. Selecteer in de Admin Console de naam van het dialoogvenster [nieuw productprofiel waaraan u aangepaste machtigingen hebt toegewezen.](#assign-permissions)

1. Selecteer in het venster dat wordt geopend de optie **Gebruikers** tab.

1. Selecteer de **Gebruikers toevoegen** en wijs gebruikers aan uw nieuw productprofiel met douanetoestemmingen toe.

Zie de sectie **Gebruikers en gebruikersgroepen toevoegen aan een productprofiel** van het document [Productprofielen beheren voor zakelijke gebruikers](https://helpx.adobe.com/enterprise/using/manage-product-profiles.html) voor meer informatie over het gebruik van de Admin Console.

## Configureerbare machtigingen {#configurable-permissions}

De volgende machtigingen zijn beschikbaar voor het maken van aangepaste profielen.

| Machtiging | Beschrijving |
|---|---|
| Programma maken | Gebruikers toestaan een programma te maken |
| Programmatoegang | Gebruikers toegang geven tot programma&#39;s |
| Programmabewerking | Gebruikers mogen programma&#39;s bewerken |
| Omgeving maken | Gebruikers toestaan een omgeving te maken |
| Omgevingsbewerking | Gebruikers toestaan omgevingen bij te werken en te bewerken |
| Omgevingslogboeken gelezen | Gebruikers toestaan omgevingslogboeken te lezen |
| Omgevingsvariabelen beheren | Gebruikers toestaan omgevingsconfiguraties te maken/te bewerken/te verwijderen |
| Omgevingsherstel maken | Gebruikers toestaan om de omgeving te herstellen |
| Rapid Dev Environment opnieuw instellen | Gebruikers toestaan om de omgeving voor snel ontwikkelen opnieuw in te stellen |
| Inhoud kopiëren beheren | Gebruikers toestaan bewerkingen voor het kopiëren van inhoud te beheren |
| Pipet maken | Gebruikers toestaan pijpleidingen te maken |
| Pipet verwijderen | Gebruikers toestaan pijpleidingen te verwijderen |
| Pipet bewerken | Gebruikers toestaan pijpleidingen te bewerken |
| Productieimplementaties goedkeuren/afwijzen | Gebruikers toestaan een stap voor productieimplementatie goed te keuren of af te wijzen |
| Uitvoeringen pijplijn annuleren | Laat gebruikers uitvoeren pijpleidingen annuleren |
| Start van pijplijnuitvoering | Gebruikers toestaan een nieuwe pijpleidingsuitvoering te starten |
| Belangrijke metrische fouten negeren/negeren | Gebruikers toestaan belangrijke metrische fouten te negeren/af te wijzen |
| Plan voor productieimplementaties | Gebruikers toestaan een stap voor productieimplementatie te plannen |
| Toegang tot opslaggegevens | Gebruikers toegang geven tot dataopslag en een wachtwoord voor toegang genereren |
| Opslagplaats maken | Gebruikers mogen it-opslagruimten maken |
| Opslagplaats verwijderen | Gebruikers mogen it-opslagruimten verwijderen |
| Bewerken opslagplaats | Gebruikers mogen it-opslagruimten bewerken |
| Code opslagplaats genereren | Gebruikers toestaan projecten te genereren op basis van het archetype |
| Domeinnaam beheren | Gebruikers toestaan domeinnamen te maken, te bewerken/te verwijderen |
| IP Lijst van gewenste personen beheert | Sta gebruikers toe om IP lijst van gewenste personen en IP lijst van gewenste personen tot stand te brengen uit te geven/te schrappen binden |
| Netwerkinfrastructuur beheren | Gebruikers toestaan netwerkinfrastructuur te maken/te bewerken/te verwijderen |
| SSL-certificaatbeheer | Gebruikers toestaan een SSL-certificaat te maken, te bewerken/te verwijderen |
| Gebruikersbeheer subaccount van New Relic | Gebruikers toestaan New Relic-subaccountgebruikers te lezen/te bewerken |

### Rechten op organisatieniveau {#organization-level}

Machtigingen op organisatieniveau verwijzen naar machtigingen die altijd worden gegeven voor alle programma&#39;s in een organisatie.

De volgende machtigingen zijn bevoegdheden op organisatieniveau:

* **Programma maken** - Met deze machtiging kunnen gebruikers een programma in de organisatie maken.
* **Toegang tot opslaggegevens** Deze huurder/organisatie niveautoestemming staat gebruikers toe om gebruikersbenaming, wachtwoord, en bewaarplaats URL voor toegang te produceren en tot klantenproject bij te dragen.
   * Gebruikersnaam en wachtwoord voor toegang tot opslagplaats zijn hetzelfde voor alle repos op de org, maar de URL van de opslagplaats is uniek voor elk programma.
   * Zie [Toegang tot opslagplaatsen](/help/implementing/cloud-manager/managing-code/accessing-repos.md) voor meer informatie .

## Voorwaarden {#terms}

De volgende termen worden gebruikt bij het maken en beheren van aangepaste machtigingen en vooraf gedefinieerde rollen.

| Term | Beschrijving |
|---|---|
| Vooraf gedefinieerde machtigingen | Vooraf gedefinieerde rollen zoals **Zakelijke eigenaar** en **Implementatiebeheer** om verschillende functies van Cloud Manager te beheren. Zie voor meer informatie over vooraf gedefinieerde rollen [AEM as a Cloud Service team en productprofielen.](/help/onboarding/aem-cs-team-product-profiles.md) |
| Aangepaste machtigingen | Met de functies van Cloud Manager kunnen gebruikers machtigingsprofielen maken om rollen te definiëren waarmee ondersteunde functies van Cloud Manager worden beheerd |
| Productprofiel | Gemaakt in de Admin Console voor het beheer van configureerbare machtigingen die van toepassing zijn op gebruikers die deel uitmaken van het machtigingsprofiel |
| Configureerbare machtiging | Cloudbeheermachtigingen die kunnen worden geconfigureerd in machtigingsprofiel |
| Machtigingsitem | Een programma, milieu, of pijpleidingsmiddel waarop een toestemming kan worden toegepast |

De punten van de toestemming verwijzen naar het werkingsgebied waar de toestemming wordt toegepast. Doorgaans is dit een van de volgende:

| Type machtigingsitem | Voorbeeld | Beschrijving |
|---|---|---|
| Organisatie | organisatie:bedrijfA | Alle toepasselijke middelen van een organisatie. Een bron kan een programma, omgeving of pijpleiding zijn. Als de gebruiker een organisatie voor om het even welke toestemming toevoegt, dan hebben alle nieuwe middelen in die organisatie ook die toestemming. |
| Programma | Programma A | Alle toepasselijke middelen van een programma |
| Omgeving | Programma A: milieu | Van toepassing op een specifieke omgeving |
| Pijpleiding | Programma A : Pipeline | Van toepassing op een specifieke pijpleiding |

## Beperkingen {#limitations}

Houd rekening met de volgende beperkingen wanneer u aangepaste machtigingen gebruikt.

* Het profiel Aangepaste machtigingen bevat ook een lijst met AMS-programma&#39;s, -omgevingen en -pijpleidingen bij het configureren van machtigingen.
* De middelen zoals programma, het milieu, en de pijpleiding die in de Manager van de Wolk werden gecreeerd kunnen twee minuten aan vertoning in Admin Console voor toestemmingsconfiguratie vergen.
* In zeldzame gevallen waarin de service met aangepaste machtigingen niet reageert, zijn vooraf gedefinieerde profielen nog steeds beschikbaar en hebben gebruikers in vooraf gedefinieerde profielen nog steeds de juiste toegang.

## Veelgestelde vragen {#faq}

### Welke machtigingsprofielen zijn vooraf gedefinieerde machtigingsprofielen?

* Business Owner
* Program Manager
* Deployment Manager
* Developer

Zie voor meer informatie over vooraf gedefinieerde rollen [AEM as a Cloud Service team en productprofielen.](/help/onboarding/aem-cs-team-product-profiles.md)

### Wat gebeurt er met vooraf gedefinieerde machtigingsprofielen met inleiding tot aangepaste profielen?

De standaardproductprofielen en de rollen van de wolkenmanager blijven het zelfde werken zoals voordien.

### Kan ik vooraf gedefinieerde machtigingsprofielen bewerken?

Nee, standaardprofielen kunnen niet worden bewerkt. U kunt geen machtigingen toevoegen aan of verwijderen uit het standaardmachtigingsprofiel. U kunt alleen gebruikers toevoegen aan of verwijderen uit vooraf gedefinieerde profielen.

### Moet ik vooraf gedefinieerde machtigingsprofielen verwijderen, omdat aangepaste profielen nu beschikbaar zijn?

Verwijder vooraf gedefinieerde machtigingsprofielen niet uit de Admin Console.

### Kan ik gebruikers toevoegen aan meerdere machtigingsprofielen?

Ja, een gebruiker kan deel uitmaken van meerdere profielen, waaronder vooraf gedefinieerde en aangepaste machtigingsprofielen. Wanneer een gebruiker aan meerdere profielen wordt toegewezen, zijn de gecombineerde machtigingen van alle toegewezen machtigingsprofielen beschikbaar voor die gebruiker.

### Wat gebeurt als een gebruiker toestemming heeft om een milieu/pijpleiding uit te geven maar geen toegang tot een programma heeft dat het milieu/de pijpleiding bevat?

In dit geval heeft de gebruiker geen toegang tot de omgeving of pijpleiding als hij/zij niet over de **Programmatoegang** machtigingen die de omgeving of pijplijn bevatten.
