---
title: Aangepaste machtigingen
description: Leer hoe u douanetoestemmingen kunt gebruiken om profielen van de douanetoestemming met configureerbare toestemmingen tot stand te brengen om toegang tot programma's, pijpleidingen, en milieu's voor de gebruikers van de Managers van de Wolk te beperken.
exl-id: 167da985-7f19-45b3-90a3-884817907da2
solution: Experience Manager
feature: Security, Developing
role: Admin, Architect, Developer
source-git-commit: 0afd74120380c9ae3d02db9fb684189c2f19648f
workflow-type: tm+mt
source-wordcount: '1490'
ht-degree: 1%

---


# Aangepaste machtigingen {#custom-permissions}

Leer hoe u douanetoestemmingen kunt gebruiken om profielen van de douanetoestemming met configureerbare toestemmingen tot stand te brengen om toegang tot programma&#39;s, pijpleidingen, en milieu&#39;s voor de gebruikers van de Managers van de Wolk te beperken.

## Inleiding {#introduction}

Cloud Manager heeft een set vooraf gedefinieerde rollen die de toegang tot verschillende Cloud Manager-functies bepalen:

* Business Owner
* Program Manager
* Deployment Manager
* Developer

Met aangepaste machtigingen kunnen gebruikers aangepaste machtigingsprofielen maken met configureerbare machtigingen om de toegang voor gebruikers van Cloud Managers te beperken tot programma&#39;s, pijpleidingen en omgevingen.

>[!TIP]
>
>Voor details op vooraf bepaalde rollen, zie [ het Team van AEM as a Cloud Service en de Profielen van het Product ](/help/onboarding/aem-cs-team-product-profiles.md).

## Aangepaste machtigingen gebruiken {#using}

Voor het maken en gebruiken van uw eigen aangepaste machtigingen zijn drie stappen vereist:

1. [ creeer een productprofiel ](#create).
1. [ wijs douanetoestemmingen aan het productprofiel ](#assign-permissions) toe.
1. [ wijs gebruikers aan het productprofiel ](#assign-users) toe.

In deze sectie worden deze stappen beschreven. U kunt het nuttig vinden om de [ Termijnen ](#terms) en [ Configurable 3&rbrace; secties van Toestemmingen te zien aangezien u uw eigen douanetoestemmingen creeert.](#configurable-permissions)

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service kan alleen profielen maken en machtigingen voor Cloud Manager beheren als Admin Console beschikt over de rechten van productbeheerders.

### Een nieuw productprofiel maken {#create}

Maak eerst een productprofiel waaraan u aangepaste machtigingen kunt toewijzen.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/).

1. Voor de Cloud Manager landende pagina, selecteer **leiden de knoop van de Toegang**.

![ beheert de knoop van de Toegang ](assets/manage-access.png)

1. U wordt opnieuw gericht aan het **Producten** lusje van Admin Console, waar u gebruikers en toestemmingen voor Cloud Manager kunt beheren. In Admin Console, selecteer de **Nieuwe knoop van het Profiel**.

![ Nieuwe knoop van het Profiel ](assets/admin-console-new-profile.png)

1. Geef de algemene details over het profiel op.

   * **het profielnaam van het Product** - een beschrijvende naam voor het profiel
   * **naam van de Vertoning** - een afgekorte naam die in UI (opties) wordt getoond
   * **Beschrijving** - een informatieve beschrijving van het profiel die zijn doel (facultatief) verklaren
   * **breng gebruikers op de hoogte door e-mail** - de gebruikers ontvangen een e-mailbericht wanneer zij aan of verwijderd uit dit profiel worden toegevoegd.

1. Selecteer **sparen** wanneer volledig.

Het nieuwe productprofiel wordt opgeslagen en wordt weergegeven in de lijst met productprofielen in de Admin Console.

### Aangepaste machtigingen toewijzen aan profiel {#assign-permissions}

Nu u een nieuw productprofiel hebt, kunt u er aangepaste machtigingen aan toewijzen.

1. In Admin Console, selecteer de naam van het [ nieuwe productprofiel u ](#create) creeerde.

1. In het venster dat opent, selecteer het **lusje van Toestemmingen** om een lijst van editable toestemmingen te bekijken.

   ![ Bewerkbare toestemmingen ](assets/permissions-tab.png)

1. Selecteer **uitgeven** verbinding van een toestemming zodat kunt u het uitgeven.

1. Het **geeft** venster van de Toestemming uit opent.
   * De machtigingen die u in de vorige stap hebt geselecteerd, worden in de linkerkolom geselecteerd.
   * De toestemmingspunten beschikbaar voor taak voor de toestemming zijn in de middenkolom geëtiketteerd **Beschikbare Punten van de Toestemming**.
   * De toegewezen toestemmingspunten zijn in de juiste kolom geëtiketteerd **Inclusief Punten van de Toestemming**.

   ![ geef toestemmingspunten ](assets/edit-permission-items.png) uit

1. Selecteer plus (`+`) pictogram naast het toestemmingspunt zodat kunt u het aan de kolom **Included Punten van de Toestemming** toevoegen.

   * Selecteer het pictogram `i` naast een machtigingsitem als u er meer over wilt weten.

1. Selecteer **alle** knoop bij de bovenkant van de **Beschikbare kolom van Toestemmingen** toevoegen zodat kunt u alle toestemmingen toevoegen.

1. Selecteer **sparen** wanneer u klaar bent met het bepalen van de toestemmingspunten voor uw nieuw productprofiel.

Uw nieuwe productprofiel wordt nu opgeslagen met de aangepaste machtigingen.

### Gebruikers toewijzen aan aangepaste machtigingen {#assign-users}

U kunt nu gebruikers toewijzen aan het nieuwe productprofiel dat u met aangepaste machtigingen hebt gemaakt.

1. In Admin Console, selecteer de naam van het [ nieuwe productprofiel waaraan u douanetoestemmingen ](#assign-permissions) toewees.

1. In het venster dat opent, selecteer de **Gebruikers** tabel.

1. Selecteer **toevoegen Gebruikers** knoop en wijs gebruikers aan uw nieuw productprofiel met douanetoestemmingen toe.

Zie de sectie **gebruikers en gebruikersgroepen aan een productprofiel** van het document [ toevoegen productprofielen voor ondernemingsgebruikers ](https://helpx.adobe.com/enterprise/using/manage-product-profiles.html) voor meer details op hoe te om Admin Console te gebruiken.

## Configureerbare machtigingen {#configurable-permissions}

De volgende machtigingen zijn beschikbaar voor het maken van aangepaste profielen.

| Machtiging | Beschrijving |
| --- | --- |
| Programma maken | Gebruikers een programma laten maken. |
| Programmatoegang | Gebruikers toegang geven tot programma&#39;s. |
| Programmabewerking | Gebruikers de programma&#39;s laten bewerken. |
| Omgeving maken | Gebruikers een omgeving laten maken. |
| Omgevingsbewerking | Laat gebruikers milieu&#39;s bijwerken en uitgeven. |
| Omgevingslogboeken gelezen | Laat gebruikers omgevingslogboeken lezen. |
| Omgevingsvariabelen beheren | Hiermee kunnen gebruikers omgevingsconfiguraties maken, bewerken/verwijderen. |
| Omgevingsherstel maken | Gebruikers een omgeving laten maken die kan worden hersteld. |
| Snelle ontwikkelomgeving opnieuw instellen | Laat gebruikers het Snelle Milieu van de Ontwikkeling (RDE) terugstellen. |
| Inhoud kopiëren beheren | Gebruikers bewerkingen voor het kopiëren van inhoud laten beheren. |
| Pipet maken | Hiermee kunnen gebruikers pijpleidingen maken. |
| Pipet verwijderen | Laat gebruikers pijpleidingen schrappen. |
| Pipet bewerken | Hiermee kunnen gebruikers pijpleidingen bewerken. |
| Productieimplementaties goedkeuren/afwijzen | Laat gebruikers een stap voor productieimplementatie goedkeuren of afwijzen. |
| Uitvoeringen pijplijn annuleren | Laat gebruikers pijpleiding uitvoeren annuleren. |
| Start van pijplijnuitvoering | Laat gebruikers een nieuwe pijpleidingsuitvoering beginnen. |
| Belangrijke metrische fouten negeren/negeren | Laat gebruikers belangrijke metrische mislukkingen met voeten treden/verwerpen. |
| Plan voor productieimplementaties | Laat gebruikers een stap van de productieplaatsing plannen. |
| Toegang tot opslaggegevens | Gebruikers toegang geven tot de gegevens in de opslagplaats en een toegangswachtwoord laten genereren. |
| Opslagplaats maken | Gebruikers Git-opslagruimten laten maken. |
| Opslagplaats verwijderen | Gebruikers Git-opslagruimten laten verwijderen. |
| Bewerken opslagplaats | Gebruikers Git-opslagruimten laten bewerken. |
| Code opslagplaats genereren | Laat gebruikers een project van archetype produceren. |
| Domeinnaam beheren | Gebruikers domeinnamen laten maken/bewerken/verwijderen. |
| IP Lijst van gewenste personen beheert | Laat gebruikers tot stand brengen/uitgeven/schrappen IP lijst van gewenste personen en IP de lijst van gewenste personen band van de . |
| Netwerkinfrastructuur beheren | Hiermee kunnen gebruikers netwerkinfrastructuur maken/bewerken/verwijderen. |
| SSL-certificaatbeheer | Gebruikers SSL-certificaat laten maken/bewerken/verwijderen. |
| Gebruikersbeheer subaccount van New Relic | Gebruikers New Relic-subaccountgebruikers laten lezen/bewerken. |

### Rechten op organisatieniveau {#organization-level}

Machtigingen op organisatieniveau verwijzen naar machtigingen die altijd worden gegeven voor alle programma&#39;s in een organisatie.

De volgende machtigingen zijn bevoegdheden op organisatieniveau:

* **Programma creeert** - Deze toestemming laat gebruikers een programma in de organisatie tot stand brengen.
* **Toegang van Info van de Bewaarplaats** Dit huurder/organisatieniveau toestemming staat gebruikers toe om een gebruikersbenaming, een wachtwoord, en een bewaarplaats URL voor toegang te produceren en tot een klantenproject bij te dragen.
   * De gebruikersnaam en het wachtwoord voor toegang tot de opslagplaats zijn dezelfde voor alle opslagplaatsen in de organisatie. De URL van de gegevensopslagruimte is echter uniek voor elk programma.
   * Zie [ Toegang hebbend tot Bewaarplaatsen ](/help/implementing/cloud-manager/managing-code/accessing-repos.md) voor meer informatie.

## Voorwaarden {#terms}

De volgende termen worden gebruikt bij het maken en beheren van aangepaste machtigingen en vooraf gedefinieerde rollen.

| Term | Beschrijving |
| --- | --- |
| Vooraf gedefinieerde machtigingen | Vooraf bepaalde rollen zoals **BedrijfsEigenaar** en **Manager van de Plaatsing** om diverse eigenschappen van Cloud Manager te regeren. Voor details op vooraf bepaalde rollen, zie [ het Team van AEM as a Cloud Service en de Profielen van het Product ](/help/onboarding/aem-cs-team-product-profiles.md). |
| Aangepaste machtigingen | Met Cloud Manager-functies kunnen gebruikers machtigingsprofielen maken om rollen te definiëren die de ondersteunde functies van Cloud Manager bepalen. |
| Productprofiel | Gemaakt in de Admin Console voor het beheer van configureerbare machtigingen die van toepassing zijn op gebruikers die deel uitmaken van het machtigingsprofiel. |
| Configureerbare machtiging | Cloud Manager-machtigingen die u kunt configureren in het machtigingsprofiel. |
| Machtigingsitem | Een programma, milieu, of pijpleidingsmiddel waarop een toestemming kan worden toegepast. |

De punten van de toestemming verwijzen naar het werkingsgebied waar de toestemming wordt toegepast. Doorgaans is dit een van de volgende:

| Type machtigingsitem | Voorbeeld | Beschrijving |
| --- | --- | --- |
| Organisatie | organisatie :companyA | Alle toepasselijke middelen van een organisatie. Een bron kan een programma, omgeving of pijpleiding zijn. Als de gebruiker een organisatie voor om het even welke toestemming toevoegt, dan hebben alle nieuwe middelen in die organisatie ook die toestemming. |
| Programma | Programma A | Alle toepasselijke middelen van een programma. |
| Omgeving | Programma A: milieu | Van toepassing op een specifieke omgeving. |
| Pijpleiding | Programma A : Pipeline | Van toepassing op een specifieke pijpleiding. |

## Gebruiksnotities {#usage-notes}

* Een profiel voor aangepaste machtigingen bevat ook een overzicht van AMS-programma&#39;s, -omgevingen en -pijpleidingen bij het configureren van machtigingen.
* De middelen zoals programma, het milieu, en de pijpleiding die in Cloud Manager werden gecreeerd kunnen twee minuten aan vertoning in Admin Console voor toestemmingsconfiguratie vergen.
* In zeldzame gevallen waarin een service met aangepaste machtigingen niet reageert, zijn vooraf gedefinieerde profielen nog steeds beschikbaar en hebben gebruikers in vooraf gedefinieerde profielen nog steeds de juiste toegang.

## Veelgestelde vragen {#faq}

### Welke machtigingsprofielen zijn vooraf gedefinieerde machtigingsprofielen?

* Business Owner
* Program Manager
* Deployment Manager
* Developer

Voor details op vooraf bepaalde rollen, zie [ het Team van AEM as a Cloud Service en de Profielen van het Product ](/help/onboarding/aem-cs-team-product-profiles.md).

### Wat gebeurt er met vooraf gedefinieerde machtigingsprofielen met inleiding tot aangepaste profielen?

Standaardproductprofielen en Cloud Manager-rollen werken nog steeds hetzelfde als voorheen.

### Kan ik vooraf gedefinieerde machtigingsprofielen bewerken?

Nee, standaardprofielen kunnen niet worden bewerkt. U kunt geen machtigingen toevoegen aan of verwijderen uit het standaardmachtigingsprofiel. U kunt alleen gebruikers toevoegen aan of verwijderen uit vooraf gedefinieerde profielen.

### Moet ik vooraf gedefinieerde machtigingsprofielen verwijderen, omdat aangepaste profielen nu beschikbaar zijn?

Verwijder vooraf gedefinieerde machtigingsprofielen niet uit de Admin Console.

### Kan ik gebruikers toevoegen aan meerdere machtigingsprofielen?

Ja, een gebruiker kan deel uitmaken van meerdere profielen, waaronder vooraf gedefinieerde en aangepaste machtigingsprofielen. Wanneer een gebruiker aan meerdere profielen wordt toegewezen, zijn de gecombineerde machtigingen van alle toegewezen machtigingsprofielen beschikbaar voor die gebruiker.

### Wat gebeurt als een gebruiker toestemming heeft om een milieu/pijpleiding uit te geven maar geen toegang tot een programma heeft dat het milieu/de pijpleiding bevat?

In dit geval, kan de gebruiker tot het milieu of de pijpleiding toegang hebben als zij niet de **toestemmingen hebben van de Toegang van het 0&rbrace; Programma die het milieu of de pijpleiding bevatten.**
