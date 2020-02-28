---
title: Op rollen gebaseerde machtigingen
description: Op rollen gebaseerde machtigingen
translation-type: tm+mt
source-git-commit: 6cae9b2b719dab687f601a0596d37f99afded9ab

---


# Op rollen gebaseerde machtigingen {#role-based-permissions}

[!UICONTROL Cloud Manager] heeft vooraf geconfigureerde rollen met de juiste machtigingen. Een ontwikkelaar ontwikkelt bijvoorbeeld code en heeft de toestemming om de code naar de **Git Repository** te duwen. Alternatief, heeft een bedrijfseigenaar verschillende toestemmingen die hen toestaan om de Zeer belangrijke Indicatoren van Prestaties (KPIs) te bepalen en plaatsingen goed te keuren.

## Gebruikersmachtigingen {#user-permissions}

Elk van de rollen heeft specifieke toestemmingen, vooraf geconfigureerde taken, of toestemmingen, verbonden aan elke rol. Deze lijst maakt een lijst van de beschikbare functies en de rollen die de functie kunnen uitvoeren.

| Machtiging | Beschrijving | Zakelijke eigenaar | Implementatiebeheer | Programmabeheerder | Ontwikkelaar |
|--- |--- |--- |--- |--- |--- |
| Tenant maken | Maak een nieuwe huurder. |  |  |  |  |
| Tenant bijwerken | Update Tenant. |  |  |  |  |
| Programma toevoegen | Voeg een nieuw programma toe. | x |  |  |  |
| Omgeving maken | Maak Prod+Stage, Dev, Playground-omgevingen. | x | x |  |  |
| Omgevingsvariabelen configureren | Omgevingsvariabelen en geheimen configureren. |  | x |  | x |
| Aangepaste domeinnaam toevoegen of verwijderen, SSL-waarschuwing uploaden of bijwerken | Aangepaste domeinnaam toevoegen/verwijderen, uploaden/SSL-waarschuwing bijwerken. | x | x |  |  |
| Omgeving bijwerken | Werk Prod+werkgebied, Dev, Playground-omgevingen bij. | x | x |  |  |
| Omgeving verwijderen | Verwijder niet-prod-, ontwikkelings- en afspeelomgevingen. | x | x |  |  |
| Omgeving verwijderen | Prod+Stage-omgeving verwijderen. |  |  |  |  |
| Sluimeromgeving | Niet-prod, Dev, afspeelomgevingen gesiberneerd. | x | x |  |  |
| Programma instellen | Vorm Programma (met inbegrip van KPIs). | x |  |  |  |
| Programma instellen | Configureer het schalingsbeleid (algemeen): het vormen maximum aantal lagen en horizontale schaal-uit op bestelling: Inschakelen). | x |  |  |  |
| Programma instellen | Toegang vastleggen. |  | x |  | x |
| Instellingen pijpleiding | Setup of Edit Pipeline. |  | x |  |  |
| Uitvoering pijpleiding | Start de pijplijn. | x | x |  |  |
| Uitvoering pijpleiding | Belangrijke 3-Tier-fouten afwijzen/goedkeuren. | x | x | x |  |
| Uitvoering pijpleiding | Geef GoLive-goedkeuring op. | x | x | x |  |
| Uitvoering pijpleiding | Plan de Implementatie van de Productie. | x | x | x |  |
| Uitvoering pijpleiding | Hervat de Productiepijpleiding. |  |  |  |  |
| Inschakelen (of uit) naar provisioning | Opt-binnen aan Horizontale levering op bestelling van het Scherm van de Opstelling van het Programma. Configureer de maximale &#39;toegestane&#39; P-D-segmenten die horizontaal kunnen worden uitgeschaald in PROD- en niet-PROD-omgevingen. | x |  |  |  |
| Omgeving beheren | Voeg segment Publish-Dispatcher van het Manage Scherm van het Milieu toe. | x | x |  |  |  |
| Productupdates | AEM-updatekaart is zichtbaar en de gebruiker moet de wizard Bijwerken starten. | x | x | x | x |
| Productupdates | Wizard Productupdates kan worden ingeschakeld. | x | x |  |  |
| Push Update | Start Push Update Pipeline. |  |  |  |  |
| Token voor persoonlijke toegang genereren | Genereer persoonlijke toegangstoken. |  | x |  | x |

