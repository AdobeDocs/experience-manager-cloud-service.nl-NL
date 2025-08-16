---
title: De AI-assistent in Adobe Experience Manager configureren
description: Leer hoe u de AI Assistant instelt en configureert met de Admin Console in Adobe Experience Manager.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: a216777f6d5bb3dd1afe5d7cdb88ec41435c0500
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 0%

---

# De AI-assistent in Adobe Experience Manager configureren {#aem-ai-asst-admin-setup}

Een beheerder moet toegang, machtigingen en instellingen configureren voordat gebruikers in hun organisatie de functies in AEM (Adobe Experience Manager) AI Assistant kunnen gebruiken. In dit artikel wordt beschreven hoe u de AI-assistent voor uw organisatie kunt inschakelen, welke aanmeldingsgegevens vereist zijn en welke configuratiewijzigingen u wilt opslaan.

**Overzicht van het proces van de Configuratie van AEM AI Hulp**

Het configuratieproces bestaat uit de volgende stappen:

1. [ creeer een nieuw productprofiel in Adobe Admin Console ](#create-profile).
1. [ laat de toestemming van de Kennis van het AI Hulpproduct ](#enable-permission) toe.
1. [ creeer een nieuwe gebruikersgroep (of gebruik een bestaande gebruikersgroep) ](#create-user-group).
1. [ voegt gebruikers aan de gebruikersgroep ](#add-users) toe.
1. [ wijs het productprofiel aan de gebruikersgroep ](#assign-product-profile) toe.

**Eerste vereisten**

Voordat u begint, moet u controleren of aan de volgende voorwaarden is voldaan:

* U moet minstens over de rechten van de Beheerder van het Product in Adobe Admin Console beschikken.
* U hebt inzicht in de gebruikersbeheerstructuur van uw organisatie.

## 1 - Een nieuw productprofiel maken in de Adobe Admin Console{#create-profile}

1. Volg de gedetailleerde instructies in [ creeer een nieuw productprofiel in Adobe Admin Console ](https://experienceleague.adobe.com/nl/docs/experience-platform/access-control/ui/create-profile) dat in de documentatie van Experience Platform wordt gevonden.

1. Bij het maken van het nieuwe productprofiel kunt u de volgende voorgestelde waarden voor de AI Assistant gebruiken.

   | Tekstveld | Voorgestelde waarde |
   | --- | --- |
   | Naam van productprofiel | `AEM AI Assistant` (of uw voorkeursbeschrijvende naam) |
   | Weergavenaam (optioneel) | `AI Assistant` |
   | Beschrijving (optioneel) | `Product profile for managing AEM AI Assistant access` |
   | Melding | Configureren op basis van de voorkeuren van uw organisatie |




## 2 - De AI Assistant-toestemming voor productkennis inschakelen{#enable-permission}

Het proces voor het toewijzen van aangepaste machtigingen aan productprofielen volgt de standaard Adobe Cloud Manager-workflow voor aangepaste machtigingen.

Het artikel van de verwijzing: [ wijst douanetoestemmingen aan het nieuwe productprofiel ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-manager/content/requirements/custom-permissions#assign-permissions) toe

1. Klik in de Admin Console op de naam van het zojuist gemaakte productprofiel (`AEM AI Assistant`)

   ![ Screenshot ](/help/implementing/cloud-manager/assets/ai-assistant-console.png)

1. Om de lijst van editable toestemmingen te bekijken, klik de **Toestemmingen** tabel.

1. Zoek in de lijst met tabellen de machtiging `AI Assistant Product Knowledge` .

   ![ AI Hulp het lusje van Toestemmingen in Admin Console ](/help/implementing/cloud-manager/assets/ai-assistant-permission.png)

1. Rechts van de toestemmingsnaam, klik ![ pictogram van het Potlood of geef pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) uit.

1. Op **geef Toestemmingen voor AI Medewerker** pagina uit, zet de **AI Hulpschakelaar van de Kennis van het Product** van het Product van een knevel.

   ![ geef de pagina van Toestemmingen voor de AI Hulpoptie van de knevel van de Kennis van het Product ](/help/implementing/cloud-manager/assets/ai-assistant-prod-knowledge.png) uit

1. In de laag-juiste hoek van de pagina, klik **sparen**.

   Voor uw productprofiel is nu de machtiging AI Assistant-productkennis ingeschakeld.


## 3 - Een nieuwe gebruikersgroep maken (of een bestaande gebruikersgroep gebruiken){#create-user-group}

1. Voer een van de volgende handelingen uit:

>[!BEGINTABS]

>[!TAB  creeer een nieuwe gebruikersgroep ]

1. In Admin Console, klik **Gebruikers** > **Gebruikersgroepen**.

   ![ Gebruikersgroepen ](/help/implementing/cloud-manager/assets/ai-assistant-user-groups.png)

1. Op de **pagina van de Groepen van de Gebruiker 0&rbrace; &lbrace;, klik** Nieuwe gebruikersgroep **.**

   ![ Nieuwe knoop van de gebruikersgroep op de pagina van de Gebruikersgroepen ](/help/implementing/cloud-manager/assets/ai-assistant-new-user-group.png)

1. Op **creeer een nieuwe gebruikersgroep** pagina, verstrek de volgende informatie:

   | Optie | Voorgestelde waarde |
   | --- | --- |
   | Naam gebruikersgroep | `AEM AI Assistant` (of uw voorkeursnaam) |
   | Beschrijving (optioneel) | `User group for managing AEM AI Assistant access` |

   ![ creeer een nieuwe pagina van de gebruikersgroep ](/help/implementing/cloud-manager/assets/ai-assistant-create-new-user-group.png)

1. In de lagere juiste hoek van de pagina, klik **sparen**.

>[!TAB  Gebruik een bestaande gebruikersgroep ]

U kunt een bestaande AEM-gebruikersgroep gebruiken als deze voldoet aan de vereisten voor toegang tot AI Assistant in plaats van een nieuwe groep te maken.

>[!ENDTABS]

## 4 - Gebruikers toevoegen aan de gebruikersgroep{#add-users}

1. Voer een van de volgende handelingen uit:

>[!BEGINTABS]

>[!TAB voeg individuele gebruikers  toe]

1. Op de **pagina van de Gebruikersgroepen**, in de **naam van de Groep** lijst, klik de naam van de gebruikersgroep die u, of een bestaande naam van de gebruikersgroep onlangs creeerde.

   ![ pagina van de Gebruikersgroepen die de naam van de de gebruikersgroep van AEM AI Hulpgroep in de lijst tonen ](/help/implementing/cloud-manager/assets/ai-assistant-user-group-name-in-table.png)

1. In de **pagina van de groepen van de Gebruiker** voor de **Medewerker van AEM AI**, klik de **Gebruikers** tabel, dan klik **toevoegen gebruikers**.

   ![ De pagina van de gebruikersgroepen van AEM AI van de Hulp, die het lusje van Gebruikers en de Add gebruikersknoop toont ](/help/implementing/cloud-manager/assets/ai-assistant-add-users.png)

1. Zoek en selecteer op de pagina **`Add users to this user group`** gebruikers die toegang tot de AEM AI Assistant nodig hebben.

   ![ voegt gebruikers aan deze pagina van de gebruikersgroep ](/help/implementing/cloud-manager/assets/ai-assistant-add-users-to-this-group.png) toe

1. In de laag-juiste hoek van de pagina, klik **sparen**.

>[!TAB  voegt gebruikers in bulk toe ]

U kunt de bulkupload-functie in de Admin Console gebruiken.

1. Een CSV-bestand met gebruikersgegevens voorbereiden.

1. Gebruik de optie **`Add users by CSV`** voor efficiënte bulktoevoeging.

>[!ENDTABS]




## 5 - Het productprofiel toewijzen aan de gebruikersgroep{#assign-product-profile}




