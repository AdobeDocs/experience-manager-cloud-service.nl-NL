---
title: Op rollen gebaseerde machtigingen
description: Op rollen gebaseerde machtigingen
translation-type: tm+mt
source-git-commit: e59fe55c255d5239a561a9fb878faa81d17b4b48

---


# Op rollen gebaseerde machtigingen {#role-based-permissions}

[!UICONTROL Cloud Manager] heeft vooraf geconfigureerde rollen met de juiste machtigingen. Een ontwikkelaar ontwikkelt bijvoorbeeld code en heeft de toestemming om de code naar de **Git Repository** te duwen. Alternatief, heeft een bedrijfseigenaar verschillende toestemmingen die hen toestaan om de Zeer belangrijke Indicatoren van Prestaties (KPIs) te bepalen en plaatsingen goed te keuren.

## Gebruikersmachtigingen {#user-permissions}

Elk van de rollen heeft specifieke toestemmingen, vooraf geconfigureerde taken, of toestemmingen, verbonden aan elke rol. Deze lijst maakt een lijst van de beschikbare functies en de rollen die de functie kunnen uitvoeren.

| Machtiging | Beschrijving | Zakelijke eigenaar | Implementatiebeheer | Programmabeheerder | Ontwikkelaar |
|--- |--- |--- |--- |--- |--- |
| Programma toevoegen | Nieuw programma toevoegen. | x | x | x | x |
| Toepassing lezen | Lees Programma-KPI&#39;s. | x | x | x | x |
| Toepassing schrijven | Programma instellen of bewerken. | x |  |  |  |  |
| Leesomgeving | Zie Omgevingsdetails. | x | x | x | x |
| Uitvoering maken | Start Pipeline. | x | x | x |  |
| Uitvoering lezen | Zie uitvoeringsstatus. | x | x | x | x |
| Uitvoering hervatten | Kan uitvoering hervatten wanneer gepauzeerd. | x | x | x |  | x |
| Implementatie Goedkeuren Distributie naar productie | Geef GoLive-goedkeuring op. | x | x | x |  |  |
| Implementatieschema Distribueren naar productie | Plan de Implementatie van de Productie. | x | x | x |
| Uitvoering annuleren | Huidige uitvoering annuleren. | x | x | x |  |
| Uitvoering heeft kwaliteitsfouten genegeerd | Belangrijke kwaliteitsfouten goedkeuren. | x | x | x |  |
| Pipet maken | Setup/Edit Pipeline. |  | x |  |  |
| Pipet gelezen | Zie details pijpleiding. | x | x | x | x |
| Pipet schrijven | Setup/Edit Pipeline. |  | x |  |  |
| Goedkeuring pijpleiding wijzigen | Hiermee kunt u de optie Bedrijfseigenaar bewerken. |  | x |  |  |
| Stap lezen | Zie de resultaten van metrische gegevens voor de stapkwaliteit. | x | x | x | x |
