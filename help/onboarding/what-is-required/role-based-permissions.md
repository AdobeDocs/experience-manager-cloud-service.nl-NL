---
title: Op rollen gebaseerde machtigingen
description: Op rollen gebaseerde machtigingen
translation-type: tm+mt
source-git-commit: a1b4feced2dd8becc74383fe8a3b835bde7159d2

---


# Op rollen gebaseerde machtigingen {#role-based-permissions}

[!UICONTROL De Manager] van de wolk heeft pre-gevormde rollen met aangewezen toestemmingen. Bijvoorbeeld, ontwikkelt een ontwikkelaar code en heeft de toestemming om de code aan de Bewaarplaats van de **it te duwen**. Alternatief, heeft een bedrijfseigenaar verschillende toestemmingen die hen toestaan om de Belangrijkste Indicatoren van Prestaties (KPIs) te bepalen en plaatsingen goed te keuren.

## Gebruikersrechten {#user-permissions}

Elk van de rollen heeft specifieke toestemmingen, preconfigured taken, of toestemmingen, verbonden aan elke rol. Deze lijst maakt een lijst van de beschikbare functies en de rollen die de functie kunnen uitvoeren.

| Toestemming | Beschrijving | Zakelijke eigenaar | Deployment Manager | Programmabeheer | Ontwikkelaar |
|--- |--- |--- |--- |--- |--- |
| Programma toevoegen | Voeg een nieuw programma toe. | x |  |  |  |
| Omgeving maken | Creëer Prod+Stage, Dev, afspeelomgevingen. | x | x |  |  |
| Update-omgeving | Werk Prod+Stage bij, ontwikkel, afspeelomgevingen. | x | x |  |  |
| Omgeving verwijderen | Verwijder non-prod-, ontwikkelings- en afspeelomgevingen. | x | x |  |  |
| Omgeving verwijderen | Schrap Prod+Stage Milieu. |  |  |  |  |
| Programma instellen | Vorm Programma (met inbegrip van KPIs). | x |  |  |  |
| Programma instellen | Git Commit Access. |  | x |  | x |
| Opstelling pijpleiding | Opstelling of geef Pijpleiding uit. |  | x |  |  |
| Uitvoering pijpleiding | Start de pijpleiding. | x | x |  |  |
| Uitvoering pijpleiding | Belangrijke fouten van drie niveaus afwijzen/goedkeuren. | x | x | x |  |
| Uitvoering pijpleiding | Geef GoLive-goedkeuring op. | x | x | x |  |
| Uitvoering pijpleiding | Implementatie van productie plannen. | x | x | x |  |
| Uitvoering pijpleiding | Hervat de Productiepijpleiding. |  |  |  |  |
| Omgeving beheren | Voeg segment Publish-Dispatcher van het Manage Scherm van het Milieu toe. | x | x |  |  |  |
| Push Update | Start de pijplijn bijwerken. |  |  |  |  |
| Produceer Persoonlijk Token van de Toegang | Toegangspunt. |  | x |  | x |

