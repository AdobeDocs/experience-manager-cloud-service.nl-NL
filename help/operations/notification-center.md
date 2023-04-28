---
title: Meldingscentrum
description: Gebruikmaken van het kennisgevingscentrum om gemakkelijk actie te ondernemen tegen incidenten en andere belangrijke informatie
hidefromtoc: true
exl-id: d5a95ac4-aa88-44d5-ba02-7c9702050208
source-git-commit: b72d22e8788c04ab4faa3616a4a0ce5e6d8ce991
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 0%

---

# Meldingscentrum {#notification-center}

>[!NOTE]
>Deze functie is niet vrijgegeven.

AEM als Cloud Service berichten verzendt wanneer kritieke incidenten voorkomen die onmiddellijke actie vereisen, evenals pro-actieve aanbevelingen voor optimalisaties. De voorbeelden omvatten een geblokkeerde rij, of een het verlopen reeks geloofsbrieven; de volledige reeks meldingstypen kan worden bekeken in de [tabel hieronder](#supported-notification-types), die na verloop van tijd zal toenemen.

Deze meldingen kunnen worden geconfigureerd om te worden ontvangen via e-mail en onder de berichtenwidget, die wordt geopend door te klikken op het belpictogram in de rechterbovenhoek van de Adobe Experience Cloud.

Wanneer een bericht wordt ontvangen, kan het worden geklikt om AEM as a Cloud Service Centrum van het Bericht met popup te openen die extra context toont die de actie voor een klant verklaren om te nemen.

Naast het tonen van informatie over het juist-geklikte bericht, dient het Centrum van het Bericht als hub waar u de reeks huidige en oudere berichten kunt bekijken en beheren. <!-- It can be accessed directly at the url TBD (Alexandru: I'm intentionally keeping it TBD for now so customers don't find it) -->

Er zijn twee categorieën meldingen op hoog niveau die in het Berichtgevingscentrum worden weergegeven:

1. Operationele incidenten - er is een gebeurtenis opgetreden waarvoor meestal een snelle oplossing vereist is. Bijvoorbeeld het oplossen van een geblokkeerde wachtrij.
1. Proactieve aanbevelingen - Adobe heeft een aanbeveling voor een actie een klant in de nabije toekomst zou moeten nemen. Bijvoorbeeld, ophouden verwijzend naar een afgekeurde UI.

Zie de [tabel hieronder](#supported-notification-types) voor de momenteel ondersteunde meldingen.

Van het Centrum van het Bericht, kunt u een specifiek programma en een milieu selecteren, dat het effect van het filtreren voor dat werkingsgebied heeft.

## Configuratie {#configuration}

Voer de onderstaande stappen uit om ontvangende meldingen te configureren:

1. De volgende productprofielen maken, zoals beschreven [in dit artikel](/help/journey-onboarding/notification-profiles.md), ook door de juiste Adobe-id&#39;s van uw organisatie toe te wijzen aan die profielen. Hierdoor kan een beheerder bepalen welke gebruikers in aanmerking komen om deze meldingen te ontvangen.
1. Elke toegewezen gebruiker die in de vorige stap wordt toegewezen kan vormen hoe zij hun berichten zouden willen ontvangen. Op de [Pagina met voorkeuren voor Experience Cloud](https://experience.adobe.com/preferences/notification-section), zorgt u ervoor dat het abonnement op de Experience Manager is ingeschakeld en **Operationele incidenten** en **Proactieve aanbevelingen** selectievakjes zijn ingeschakeld. Daarnaast wordt aangeraden de sectie E-mails in te stellen op **Directe meldingen** dus worden meldingen onmiddellijk ontvangen wanneer zich een incident voordoet.

>[!NOTE]
>Meldingen functioneren op organisatieniveau, zodat abonnees meldingen ontvangen voor alle programma&#39;s en omgevingen binnen die programma&#39;s.

## Gedetailleerde gebruikersstroom {#detailed-user-flow}

Als u op de e-mail klikt, wordt u naar het Berichtgevingscentrum gestuurd. In een pop-up ziet u de context voor de melding waarop u hebt geklikt en in sommige gevallen gaat u naar aanvullende informatie waarin wordt beschreven hoe u corrigerende maatregelen kunt nemen.

![Gegevens over incidenten](/help/operations/assets/incident-details.png)

Klik op de knop **Meer informatie** de verbinding navigeert de gebruiker aan dit artikel, waar het bericht in de lijst kan worden van verwijzingen voorzien hieronder, dat begeleiding over welke actie om verstrekt te nemen.

In het Berichtencentrum, kunt u een lijst van andere recente berichten zien. U wordt aangeraden dat u met de lijst Handelingen een melding bevestigt om aan de Adobe te laten weten dat uw organisatie zich bewust is van de taak en om de melding later op te lossen wanneer corrigerende actie is ondernomen.

![Lijst met meldingen](/help/operations/assets/notification-list.png)

In de meeste gevallen moet de kennisgeving alle noodzakelijke context bieden om het probleem op te lossen. Als er echter vragen zijn voor ondersteuning van Adobe, kunt u op de knop **Contact opnemen met ondersteuning** koppeling in het pop-upvenster met meldingen. Dit zal omhoog een vorm van waar u de vraag kunt beschrijven en voorleggen om het kaartje van de Steun te creëren, dat ook een verwijzing naar het specifieke bericht zal omvatten zodat heeft een Ingenieur van de Steun van Adobe de relevante context.

![Contact opnemen met ondersteuning 1](/help/operations/assets/contact-support1.png)

![Contact opnemen met ondersteuning 2](/help/operations/assets/contact-support2.png)

Zoals alle steunkaartjes, zal het in [Tabblad Adobe Admin Console-ondersteuningsgevallen](https://helpx.adobe.com/enterprise/using/support-for-enterprise.html), waar u het kunt bijhouden en aanvullende opmerkingen kunt toevoegen.

![Ondersteuning voor Admin Consoles](/help/operations/assets/admin-console-support.png)

## Welke meldingen worden weergegeven? {#which-notification}

AEM as a Cloud Service heeft verschillende soorten meldingen, maar er wordt alleen een subset weergegeven in het Berichtingscentrum, zoals in de onderstaande tabel wordt geïllustreerd.

| Meldingstype | Beschrijving | Hoe te vormen | Wordt weergegeven in Berichtgevingscentrum |
|---|---|---|---|
| Operationele incidenten | Kritieke incidenten die onmiddellijke actie vereisen | Gebruiker toegewezen aan productprofiel &quot;Incident Notification - Cloud Service&quot;, selectievakje &quot;Operationele incidenten&quot; ingeschakeld in [Voorkeuren Experience Cloud](https://experience.adobe.com/preferences) | X |
| Proactieve aanbevelingen | Optimalisaties die moeten worden gepland | Gebruiker toegewezen aan productprofiel &quot;Proactieve kennisgeving - Cloud Service&quot;, selectievakje &quot;Proactieve aanbevelingen&quot; ingeschakeld in [Voorkeuren Experience Cloud](https://experience.adobe.com/preferences) | X |
| Klassepijplusstatussen van Cloud Manager | Informatie over de toestand van uw pijpleidingen | Gebruiker met de rollen Bedrijfs van de Eigenaar, van de Manager van het Programma, of van de Manager van de Plaatsing, &quot;Andere&quot;checkbox binnen geselecteerd [Voorkeuren Experience Cloud](https://experience.adobe.com/preferences) |  |

## Ondersteunde berichttypen {#supported-notification-types}

In de volgende tabel worden de berichttypen weergegeven die momenteel worden ondersteund.

| Meldingstype | Verwante productprofiel | Correctieve actie |
|---|---|---|
| Geblokkeerde replicatiewachtrij | Incident | Blokkeren van wachtrij opheffen door instructies in het dialoogvenster [Replicatiedocumentatie](/help/operations/replication.md#troubleshooting) |
| S2S-certificaat vervalt | Proactief | Leer hoe u een referentie kunt vernieuwen in het dialoogvenster [Access Tokens genereren voor documentatie van server-side API&#39;s](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials) |

