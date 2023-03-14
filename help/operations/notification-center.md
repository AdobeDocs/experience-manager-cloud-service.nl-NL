---
title: Meldingscentrum
description: Gebruikmaken van het kennisgevingscentrum om gemakkelijk actie te ondernemen tegen incidenten en andere belangrijke informatie
hidefromtoc: true
source-git-commit: a5977c667d831c47d41cd86b68e9196fbe726899
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---


# Meldingscentrum {#notification-center}

>[!NOTE]
>Deze functie is niet vrijgegeven.

Zodra gevormd, AEM als Cloud Service verzendt berichten over belangrijke informatie waarvoor de klanten actie zouden moeten ondernemen. Voorbeelden van meldingen zijn een geblokkeerde wachtrij of een verloopset van referenties. De volledige reeks berichttypes kunnen in worden bekeken [tabel hieronder](#current-notification-types)en wordt na verloop van tijd groter. Meldingen worden ontvangen via e-mail en als een nieuw item onder de berichtenwidget, die wordt geopend door te klikken op het belpictogram in de rechterbovenhoek van de Adobe Experience Cloud. De instellingen voor meldingen kunnen worden geconfigureerd.

Wanneer een bericht wordt ontvangen, kan het worden geklikt om AEM as a Cloud Service Centrum van het Bericht met popup te openen die extra context toont die de geadviseerde actie voor een klant verklaren om te nemen.

Naast het tonen van informatie over het juist-geklikte bericht, dient het Centrum van het Bericht als hub waar u de reeks huidige en oudere berichten kunt bekijken en beheren. <!-- It can be accessed directly at the url TBD (Alexandru: I'm intentionally keeping it TBD for now so customers don't find it) -->

Er zijn twee soorten kennisgevingen op hoog niveau:

1. Incidenten - er is een gebeurtenis opgetreden waarvoor meestal een snelle resolutie is vereist. Bijvoorbeeld, het oplossen van een geblokkeerde rij
1. Proactief - Adobe heeft een aanbeveling voor een actie een klant in de nabije toekomst zou moeten nemen. Bijvoorbeeld, ophouden verwijzend naar een afgekeurde UI.

Zie de [tabel hieronder](#current-notification-types) voor de momenteel ondersteunde meldingen.

Van het scherm van het Centrum van het Bericht, kunt u een specifiek programma en een milieu selecteren, dat het effect van het filtreren voor dat werkingsgebied heeft.

## Configuratie {#configuration}

U kunt de volgende stappen volgen om het ontvangen berichten te vormen:

1. De volgende productprofielen maken, zoals beschreven [in dit artikel](/help/journey-onboarding/user-groups.md), door de juiste Adobe-id&#39;s van uw organisatie toe te wijzen aan die profielen.
1. Bepaal de instellingen voor de berichtconfiguratie. [Op deze pagina](https://experience.adobe.com/preferences/notification-section), zorg ervoor het Abonnement van de Experience Manager wordt toegelaten en **Overige** selectievakje is ingeschakeld. Daarnaast wordt aangeraden de sectie E-mails in te stellen op **Directe meldingen** dus ontvangt u meldingen direct nadat een incident heeft plaatsgevonden.

>[!NOTE]
>Abonnementen functioneren op organisatieniveau, zodat abonnees meldingen ontvangen voor alle programma&#39;s en omgevingen binnen die programma&#39;s.

## Gedetailleerde gebruikersstroom {#detailed-user-flow}

Als u op de e-mail klikt, wordt u naar het Berichtgevingscentrum gestuurd. In een pop-up ziet u de context voor de melding waarop u hebt geklikt en in sommige gevallen gaat u naar aanvullende informatie waarin wordt beschreven hoe u corrigerende maatregelen kunt nemen.

![Gegevens over incidenten](/help/operations/assets/incident-details.png)

Klik op de knop **Meer informatie** de verbinding navigeert de gebruiker aan dit artikel, waar het bericht in de lijst kan worden van verwijzingen voorzien hieronder, dat begeleiding over welke actie om verstrekt te nemen.

In het Berichtencentrum, kunt u een lijst van andere recente berichten zien. U wordt aangeraden dat u met de lijst Handelingen een melding bevestigt om aan de Adobe te laten weten dat uw organisatie zich bewust is van de taak en om de melding later op te lossen wanneer corrigerende actie is ondernomen.

![Lijst met meldingen](/help/operations/assets/notification-list.png)

In de meeste gevallen moet de kennisgeving alle noodzakelijke context bieden om het probleem op te lossen. Als er echter vragen zijn voor ondersteuning van Adobe, kunt u op de knop **Contact opnemen met ondersteuning** koppeling in het pop-upvenster met meldingen. Dit zal omhoog een vorm van waar u de vraag kunt beschrijven en voorleggen om het kaartje van de Steun te creëren, dat ook een verwijzing naar het specifieke bericht zal omvatten zodat een Ingenieur van de Steun van de Adobe de relevante context heeft.

![Contact opnemen met ondersteuning 1](/help/operations/assets/contact-support1.png)

![Contact opnemen met ondersteuning 2](/help/operations/assets/contact-support2.png)

Zoals alle steunkaartjes, zal het in [Tabblad Adobe Admin Console-ondersteuningsgevallen](https://helpx.adobe.com/enterprise/using/support-for-enterprise.html), waar u het kunt bijhouden en aanvullende opmerkingen kunt toevoegen.

![Ondersteuning voor Admin Consoles](/help/operations/assets/admin-console-support.png)

## Huidige meldingstypen {#current-notification-types}

De onderstaande tabel bevat de momenteel ondersteunde berichttypen

| Meldingstype | Verwante productprofiel | Correctieve actie |
|---|---|---|
| Geblokkeerde replicatiewachtrij | Incident | Blokkeren van wachtrij opheffen door instructies in het dialoogvenster [Replicatiedocumentatie](/help/operations/replication.md#troubleshooting) |
| S2S-certificaat vervalt | Proactief | Leer hoe u een referentie kunt vernieuwen in het dialoogvenster [Access Tokens genereren voor documentatie van server-side API&#39;s](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials) |
