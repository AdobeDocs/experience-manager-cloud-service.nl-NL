---
title: De AI-assistent in Adobe Experience Manager configureren
description: Leer hoe u de AI Assistant instelt en configureert met de Admin Console in Adobe Experience Manager.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
exl-id: a7f3dc14-29f7-473a-9870-d52393e6fa6e
source-git-commit: e853e7b46c762ab724d5eecb344897a83e4fb724
workflow-type: tm+mt
source-wordcount: '950'
ht-degree: 0%

---

# De AI-assistent in Adobe Experience Manager configureren {#aem-ai-asst-admin-setup}

Een beheerder moet toegang, machtigingen en instellingen configureren voordat gebruikers in hun organisatie de functies in AEM (Adobe Experience Manager) AI Assistant kunnen gebruiken.

Het configuratieproces van de AEM AI Assistant bestaat uit de volgende stappen:

1. [ creeer een nieuw productprofiel in Adobe Admin Console ](#create-profile).
1. [ laat de toestemming van de Kennis van het AI Hulpproduct ](#enable-permission) toe.
1. [ creeer een nieuwe gebruikersgroep (of gebruik een bestaande gebruikersgroep) ](#create-user-group).
1. [ voegt gebruikers aan de gebruikersgroep ](#add-users) toe.
1. [ wijs het productprofiel aan de gebruikersgroep ](#assign-product-profile) toe.

**Eerste vereisten**

Voordat u begint, moet u controleren of aan de volgende voorwaarden is voldaan:

* U moet minstens over de rechten van de Beheerder van het Product in Adobe Admin Console beschikken.
* U hebt inzicht in de gebruikersbeheerstructuur van uw organisatie.

**overwegingen van de Configuratie**

* Verwerkingstijd: het kan maximaal 2 minuten duren voordat de in Cloud Manager gemaakte bronnen in de Admin Console worden weergegeven voor machtigingsconfiguratie.
* Meerdere profielen: gebruikers kunnen deel uitmaken van meerdere profielen en machtigingen worden gecombineerd van alle toegewezen profielen.
* Organisatiebereik: sommige machtigingen kunnen op organisatieniveau van toepassing zijn op alle programma&#39;s.
* Vooraf gedefinieerde profielen: Verwijder vooraf gedefinieerde machtigingsprofielen niet uit de Admin Console.


## 1 - Een nieuw productprofiel maken in de Adobe Admin Console{#create-profile}

1. Volg de gedetailleerde instructies in [ creeer een nieuw productprofiel in Adobe Admin Console ](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/ui/create-profile) dat in de documentatie van Experience Platform wordt gevonden.

1. Bij het maken van het nieuwe productprofiel kunt u de volgende voorgestelde waarden voor de AI Assistant gebruiken.

   | Tekstveld | Voorgestelde waarde |
   | --- | --- |
   | Naam van productprofiel | `AEM AI Assistant` (of uw voorkeursbeschrijvende naam) |
   | Weergavenaam (optioneel) | `AI Assistant` |
   | Beschrijving (optioneel) | `Product profile for managing AEM AI Assistant access` |
   | Melding | Configureren op basis van de voorkeuren van uw organisatie |


## 2 - De AI Assistant-toestemming voor productkennis inschakelen{#enable-permission}

Het proces voor het toewijzen van aangepaste machtigingen aan productprofielen volgt de standaard Adobe Cloud Manager-workflow voor aangepaste machtigingen.

Het artikel van de verwijzing: [ wijst douanetoestemmingen aan het nieuwe productprofiel ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/requirements/custom-permissions#assign-permissions) toe

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

1. Op de **pagina van de Groepen van de Gebruiker 0} {, klik** Nieuwe gebruikersgroep **.**

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

>[!TAB  voeg individuele gebruikers ] toe

1. Op de **pagina van de Gebruikersgroepen**, in de **naam van de Groep** lijst, klik de naam van de gebruikersgroep die u, of een bestaande naam van de gebruikersgroep onlangs creeerde.

   ![ pagina van de Gebruikersgroepen die de naam van de de gebruikersgroep van AEM AI Hulpgroep in de lijst tonen ](/help/implementing/cloud-manager/assets/ai-assistant-user-group-name-in-table.png)

1. In de **pagina van de groepen van de Gebruiker** voor de **Medewerker van AEM AI**, klik de **Gebruikers** tabel, dan klik **toevoegen gebruikers**.

   ![ De pagina van de gebruikersgroepen van AEM AI van de Hulp, die het lusje van Gebruikers en de Add gebruikersknoop toont ](/help/implementing/cloud-manager/assets/ai-assistant-add-users.png)

1. Zoek en selecteer op de pagina **`Add users to this user group`** gebruikers die toegang tot de AEM AI Assistant nodig hebben.

   ![ voegt gebruikers aan deze pagina van de gebruikersgroep ](/help/implementing/cloud-manager/assets/ai-assistant-add-users-to-this-group.png) toe

1. In de laag-juiste hoek van de pagina, klik **sparen**.
1. Wijs nu het productprofiel toe aan de gebruikersgroep] (#assign-product-profile).

>[!TAB  voegt gebruikers in bulk toe ]

U kunt de bulkupload-functie in de Admin Console gebruiken.

1. Een CSV-bestand met gebruikersgegevens voorbereiden.
1. Gebruik de optie **`Add users by CSV`** voor efficiënte bulktoevoeging.
1. Wijs nu het productprofiel toe aan de gebruikersgroep] (#assign-product-profile).

>[!ENDTABS]


## 5 - Het productprofiel toewijzen aan de gebruikersgroep{#assign-product-profile}

Deze stap volgt de standaard Adobe Admin Console-workflow voor het toewijzen van productprofielen aan gebruikersgroepen.

Het artikel van de verwijzing: [ beheert productprofielen voor ondernemingsgebruikers ](https://helpx.adobe.com/enterprise/using/manage-product-profiles.html)

1. Terwijl nog in uw AEM AI Hulp gebruikersgroep van [ 4 - voeg gebruikers aan de gebruikersgroep ](#add-users) toe, klik de **Toegewezen productprofielen** tabel.
1. Klik **toewijzen profiel**.

   ![ AEM AI de Hulp pagina van de gebruikersgroep met Toegewezen geselecteerde productprofielen ](/help/implementing/cloud-manager/assets/ai-assistant-assign-profile.png)

1. Op **wijs producten en profielen** pagina toe, in het **Uitgezochte de dialoogvakje van productprofielen**, onderzoek naar en selecteer uw **AI Medewerker** productprofiel.

   ![ de &quot;Assign producten en profielen&quot;pagina, die de &quot;Uitgezochte productprofielen&quot;dialoogdoos toont, en het &quot;AI Medewerker&quot;geselecteerde productprofiel ](/help/implementing/cloud-manager/assets/ai-assistant-select-product-profile.png)

1. Vlak de laag-juiste hoek van de dialoogdoos, past de klik **** toe.
1. Vlak de laag-juiste hoek van **wijs producten en profielen** pagina toe, klik **sparen**.

   ![ het AI Hulpgetoonde profiel van het product dat aan de Hulpgebruikersgroep van AEM wordt toegewezen AI ](/help/implementing/cloud-manager/assets/ai-assistant-profile-assigned-to-user-group.png)


## De configuratie controleren

* Controleer of het profiel van uw product het juiste aantal toegewezen gebruikersgroepen bevat.
* Controleer of in de gebruikersgroep het juiste aantal gebruikers wordt weergegeven.
* Bevestig dat de toestemming van de Kennis van het Product van AI Hulpmiddel wordt toegelaten en behoorlijk gevormd.


## De configuratie testen

Een gebruiker van de toegewezen groep hebben doe het volgende:

1. Log in bij AEM.
2. Controleer of de AI Assistant-functies toegankelijk zijn.
3. Test de functionaliteit van de AI Assistant om te zorgen dat deze correct wordt geactiveerd.

## Zie ook

* [ de Toegangscontrole van Adobe Experience Platform ](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/ui/overview)
* [Aangepaste Cloud Manager-machtigingen](/help/implementing/cloud-manager/custom-permissions.md)


