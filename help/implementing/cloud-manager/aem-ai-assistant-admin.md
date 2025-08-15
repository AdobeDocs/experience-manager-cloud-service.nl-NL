---
title: De AI-assistent in Adobe Experience Manager configureren
description: Leer hoe u de AI Assistant instelt en configureert met de beheerconsole in Adobe Experience Manager.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: ab8fefe18e43c1fe937d0d16df65b6137fc8a292
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 0%

---

# AEM AI Assistant configureren - installatie van beheerder {#aem-ai-asst-admin-setup}

Een beheerder moet toegang, toestemmingen, en montages vormen alvorens de gebruikers in hun organisatie de eigenschappen in de Medewerker van AEM kunnen gebruiken AI. In dit artikel wordt beschreven hoe u de AI-assistent voor uw organisatie kunt inschakelen, welke aanmeldingsgegevens vereist zijn en welke configuratiewijzigingen u wilt opslaan.

**Overzicht van het proces van de Configuratie van AEM AI Hulp**

Het configuratieproces bestaat uit de volgende stappen:

1. Een nieuw productprofiel maken in Adobe Admin Console.
1. Schakel de machtiging &quot;AI Assistant Product Knowledge&quot; in.
1. Maak of gebruik een bestaande gebruikersgroep.
1. Voeg gebruikers toe aan de gebruikersgroep.
1. Wijs het productprofiel toe aan de gebruikersgroep.

**Eerste vereisten**

Voordat u begint, moet u controleren of aan de volgende voorwaarden is voldaan:

* U moet minstens over de rechten van de Beheerder van het Product in Adobe Admin Console beschikken.
* U hebt inzicht in de gebruikersbeheerstructuur van uw organisatie.

## 1 - Een nieuw productprofiel maken in Adobe Admin Console{#create-profile}

1. Volg de gedetailleerde instructies in [ creeer een nieuw productprofiel in Adobe Admin Console ](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/ui/create-profile) vond de documentatie van Experience Platform.

1. Gebruik bij het maken van het nieuwe productprofiel de volgende voorbeelden van de waarden die u voor de AI-assistent kunt gebruiken.

   | Tekstveld | Voorgestelde waarde |
   | --- | --- |
   | Naam van productprofiel | `AEM AI Assistant` (of uw voorkeursbeschrijvende naam) |
   | Weergavenaam (optioneel) | `AI Assistant` |
   | Beschrijving (optioneel) | `Product profile for managing AEM AI Assistant access` |
   | Melding | Configureren op basis van de voorkeuren van uw organisatie |




## 2 - Toestemming voor &quot;AI Assistant Product Knowledge&quot; inschakelen{#enable-permission}

Het proces voor het toewijzen van aangepaste machtigingen aan productprofielen volgt de standaard Adobe Cloud Manager-workflow voor aangepaste machtigingen.

Het artikel van de verwijzing: [ wijst douanetoestemmingen aan het nieuwe productprofiel ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/requirements/custom-permissions#assign-permissions) toe

1. Klik in de Admin Console op de naam van het zojuist gemaakte productprofiel (`AEM AI Assistant`)

   ![ Screenshot ](/help/implementing/cloud-manager/assets/ai-assistant-console.png)

1. Om de lijst van editable toestemmingen te bekijken, klik de **Toestemmingen** tabel.

1. Zoek in de lijst met tabellen de machtiging `AI Assistant Product Knowledge` .

   ![ AI Hulp het lusje van Toestemmingen in Admin Console ](/help/implementing/cloud-manager/assets/ai-assistant-permission.png)

1. Rechts van de toestemmingsnaam, klik ![ pictogram van het Potlood of geef pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) uit.

1. In **geef Toestemmingen voor AI Medewerker** pagina uit, zet de **AI Hulpschakelaar van de Kennis van het Product** van het Product van een knevel.

   ![ geef de pagina van Toestemmingen voor de AI Hulpoptie van de knevel van de Kennis van het Product ](/help/implementing/cloud-manager/assets/ai-assistant-prod-knowledge.png) uit

1. In de laag-juiste hoek van de pagina, klik **sparen**.

   Voor uw productprofiel is nu de machtiging AI Assistant-productkennis ingeschakeld.


## 3 - Een gebruikersgroep maken (of een bestaande gebruikersgroep gebruiken){#create-user-group}

1. Voer een van de volgende handelingen uit:

>[!BEGINTABS]

>[!TAB  creeer een nieuwe gebruikersgroep ]

1. In Admin Console, klik **Gebruikers** > **Gebruikersgroepen**.

   ![ Gebruikersgroepen ](/help/implementing/cloud-manager/assets/ai-assistant-user-groups.png)

1. In de **pagina van de Gebruikersgroepen**, klik **Nieuwe gebruikersgroep**.

   ![ Nieuwe knoop van de gebruikersgroep op de pagina van de Gebruikersgroepen ](/help/implementing/cloud-manager/assets/ai-assistant-new-user-group.png)

1. In **creeer een nieuwe gebruikersgroep** pagina, verstrek de volgende informatie:

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

1. Op **voeg gebruikers aan deze gebruikersgroep** pagina toe, onderzoek naar en selecteer gebruikers die toegang tot de Medewerker van AEM AI nodig hebben.

   ![ voegt gebruikers aan deze pagina van de gebruikersgroep ](/help/implementing/cloud-manager/assets/ai-assistant-add-users-to-this-group.png) toe

1. In de laag-juiste hoek van de pagina, klik **sparen**.

>[!TAB  voegt gebruikers in bulk toe ]

U kunt de bulkupload-functie in de Admin Console gebruiken.

1. Een CSV-bestand met gebruikersgegevens voorbereiden.

1. Gebruik **gebruikers door CSV** optie voor efficiënte bulktoevoeging toevoegen.

>[!ENDTABS]




## 5 - Het productprofiel toewijzen aan de gebruikersgroep{#assign-product-profile}




