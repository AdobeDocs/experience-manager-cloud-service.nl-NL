---
title: Op rollen gebaseerde machtigingen
description: Op rollen gebaseerde machtigingen
translation-type: tm+mt
source-git-commit: 1765cc81bcd6b3404642efbd3ddde27047583f85

---


# Op rollen gebaseerde machtigingen {#role-based-permissions}

[!UICONTROL Cloud Manager] heeft vooraf geconfigureerde rollen met de juiste machtigingen. Een ontwikkelaar ontwikkelt bijvoorbeeld code en heeft de toestemming om de code naar de **Git Repository** te duwen. Alternatief, heeft een bedrijfseigenaar verschillende toestemmingen die hen toestaan om de Zeer belangrijke Indicatoren van Prestaties (KPIs) te bepalen en plaatsingen goed te keuren.

## Gebruikersmachtigingen {#user-permissions}

Elk van de rollen heeft specifieke toestemmingen, vooraf geconfigureerde taken, of toestemmingen, verbonden aan elke rol. Deze lijst maakt een lijst van de beschikbare functies en de rollen die de functie kunnen uitvoeren.

| Machtiging | Beschrijving | Zakelijke eigenaar | Implementatiebeheer | Programmabeheerder | Ontwikkelaar |
|--- |--- |--- |--- |--- |--- |
| Programma toevoegen | Voeg een nieuw programma toe. | x |  |  |  |
| Omgeving maken | Maak Prod+Stage, Dev, Playground-omgevingen. | x | x |  |  |
| Omgeving bijwerken | Werk Prod+werkgebied, Dev, Playground-omgevingen bij. | x | x |  |  |
| Omgeving verwijderen | Verwijder niet-prod-, ontwikkelings- en afspeelomgevingen. | x | x |  |  |
| Omgeving verwijderen | Prod+Stage-omgeving verwijderen. |  |  |  |  |
| Programma instellen | Vorm Programma (met inbegrip van KPIs). | x |  |  |  |
| Programma instellen | Toegang vastleggen. |  | x |  | x |
| Instellingen pijpleiding | Setup of Edit Pipeline. |  | x |  |  |
| Uitvoering pijpleiding | Start de pijplijn. | x | x |  |  |
| Uitvoering pijpleiding | Belangrijke 3-Tier-fouten afwijzen/goedkeuren. | x | x | x |  |
| Uitvoering pijpleiding | Geef GoLive-goedkeuring op. | x | x | x |  |
| Uitvoering pijpleiding | Plan de Implementatie van de Productie. | x | x | x |  |
| Uitvoering pijpleiding | Hervat de Productiepijpleiding. |  |  |  |  |
| Omgeving beheren | Voeg segment Publish-Dispatcher van het Manage Scherm van het Milieu toe. | x | x |  |  |  |
| Push Update | Start Push Update Pipeline. |  |  |  |  |
| Token voor persoonlijke toegang genereren | Genereer persoonlijke toegangstoken. |  | x |  | x |

