---
title: Omgevingen beheren - Cloud-service
description: Omgevingen beheren - Cloud-service
translation-type: tm+mt
source-git-commit: 81f993325b80c0de17d6032a45ebd61c22169d39

---


# Omgevingen beheren {#manage-environments}

In de volgende sectie worden de typen omgeving beschreven die een gebruiker kan maken en hoe de gebruiker een omgeving kan maken.

## Omgevingstypen {#environment-types}

Een gebruiker met de vereiste toestemmingen kan de volgende milieutypes (binnen de grenzen van wat aan de specifieke huurder beschikbaar is) tot stand brengen.

* **Productie- en Stage-omgeving**:
De productie en het werkgebied zijn beschikbaar als duo en worden gebruikt voor test- en productiedoeleinden.

* **Ontwikkeling**: Een ontwikkelomgeving kan worden gecreëerd voor ontwikkelings- en testdoeleinden en zal alleen worden geassocieerd met niet-productiepijpleidingen.

   >[!NOTE]
   >Een ontwikkelomgeving die automatisch in een Sandbox-programma wordt gemaakt, wordt geconfigureerd om de oplossingen Sites en Assets te bevatten.

   De volgende tabel geeft een overzicht van de typen omgeving en hun kenmerken:

   | Naam | Auteurslijst | Lijst publiceren | Gebruiker kan maken | Gebruiker kan | Pijpleiding die in verband kan worden gebracht met het milieu |
   |--- |--- |--- |--- |---|---|
   | Productie | Ja | Ja als sites zijn opgenomen | Ja | Nee | Productiepijpleiding |
   | Werkgebied | Ja | Ja als sites zijn opgenomen | Ja | Nee | Productiepijpleiding |
   | Ontwikkeling | Ja | Ja als sites zijn opgenomen | Ja | Ja | Niet-productiepijpleiding |

   >[!NOTE]
   >
De productie en het werkgebied zijn beschikbaar als duo en worden gebruikt voor test- en productiedoeleinden.  De gebruiker kan niet alleen een werkgebied of alleen een productieomgeving maken.

## Een omgeving toevoegen {#adding-environments}


1. De gebruiker klikt op de knop Omgeving **** toevoegen om een omgeving toe te voegen.

   ![](assets/add-environment.png)

1. Het dialoogvenster Omgeving **** toevoegen wordt weergegeven. De gebruiker moet details indienen zoals het **Omgevingstype** en de naam **van het** Milieu en de beschrijving **van het** Milieu (afhankelijk van de doelstelling van de gebruiker bij het creëren van de omgeving binnen de grenzen van wat beschikbaar is voor de specifieke huurder).

   ![](assets/add-environment2.png)

   >[!NOTE]
   >Wanneer u een omgeving maakt, worden een of meer *integraties* gemaakt in Adobe I/O. Deze zijn zichtbaar voor gebruikers van de klant die toegang hebben tot de Adobe I/O-console en mogen niet worden verwijderd. Dit wordt beschreven in de beschrijving in de Adobe I/O-console.

   ![](assets/add-environment-image1.png)

1. Klik op **Opslaan** om een omgeving met de ingevulde criteria toe te voegen.  Nu toont het *scherm van het Overzicht* de kaart van waar u opstelling uw pijpleiding kunt.

   >[!NOTE]
   >Als, u nog niet opstelling uw niet productiepijplijn hebt, toont het *scherm van het Overzicht* de kaart van waar u uw niet productiepijplijn kunt tot stand brengen.


## Omgeving bijwerken {#updating-dev-environment}

Updates van werkgebied- en productieomgevingen worden automatisch beheerd door Adobe.

Updates voor ontwikkelomgevingen worden beheerd door gebruikers van het programma. Als een omgeving niet de nieuwste openbaar beschikbare AEM-versie uitvoert, wordt in de status op de milieuvriendenkaart op het startscherm de **UPDATE-BESCHIKBAAR** weergegeven.

![](assets/manage-environments2.png)
)

Wanneer deze status wordt weergegeven, is de optie **Bijwerken** beschikbaar in het vervolgkeuzemenu, zowel op de milieucaart als in het menu **Beheren** als u op **Details** van de **MILIEUkaart** klikt.

![](assets/add-environment4.png)

Het selecteren van dit van dropdown menu zal een Manager van de Plaatsing toestaan om de pijpleiding verbonden aan dit milieu aan de recentste versie bij te werken en dan de pijpleiding uit te voeren.

Als de pijpleiding reeds is bijgewerkt, wordt de gebruiker ertoe aangezet om de pijpleiding uit te voeren.
