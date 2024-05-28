---
title: Handelingencentrum
description: Gebruik het actiecentrum om incidenten en andere belangrijke informatie op een gemakkelijke manier aan te pakken
exl-id: d5a95ac4-aa88-44d5-ba02-7c9702050208
source-git-commit: ae8c5e832134caf4ff6799c601810e9a735f4195
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 0%

---

# Handelingencentrum {#actions-center}

AEM als Cloud Service verzendt de e-mailberichten van het Centrum van Acties wanneer de kritieke incidenten voorkomen die onmiddellijke actie vereisen, en pro-actieve aanbevelingen voor optimalisaties. De voorbeelden omvatten een geblokkeerde rij, of een het verlopen reeks geloofsbrieven; de volledige reeks berichten van het Centrum van Acties kunnen in worden bekeken [tabel hieronder](#supported-notification-types), die na verloop van tijd zal toenemen.

Wanneer een e-mailbericht van het Centrum van Acties wordt ontvangen, kan het worden geklikt om AEM Centrum van Acties van de as a Cloud Service met een pop-up te openen die extra context toont die de actie verklaart voor een klant te nemen.

Naast het weergeven van informatie over het zojuist geklikte e-mailbericht, fungeert het Actions Center als een hub waarin u de set met huidige en oudere meldingen kunt weergeven en beheren. <!-- It can be accessed directly at the url TBD (Alexandru: I'm intentionally keeping it TBD for now so customers do not find it) -->

Er zijn twee categorieën meldingen op hoog niveau die in het Actions Center worden weergegeven:

1. Operationele incidenten - er is een gebeurtenis opgetreden waarvoor meestal een snelle oplossing vereist is. Bijvoorbeeld het oplossen van een geblokkeerde wachtrij.
1. Proactieve aanbevelingen - Adobe heeft een aanbeveling voor een actie een klant in de nabije toekomst zou moeten nemen. Bijvoorbeeld, ophouden verwijzend naar een afgekeurde UI.

Zie de [tabel hieronder](#supported-notification-types) voor de meldingen die momenteel worden ondersteund in het Actions Center.

Vanuit het Actions Center kunt u een specifiek programma en een specifieke omgeving selecteren die het effect hebben van filteren voor dat bereik.

## Configuratie {#configuration}

Om het ontvangen van de e-mailberichten van het Centrum van Acties te vormen, creeer de beschreven Profielen van het Product [in dit artikel](/help/journey-onboarding/notification-profiles.md), namelijk kennisgeving van incidenten - Cloud Service en proactieve kennisgeving - Cloud Service. Wijs ook de juiste Adobe-id&#39;s van uw organisatie toe aan die profielen. Hierdoor kan een beheerder bepalen welke gebruikers in aanmerking komen om deze e-mailberichten te ontvangen.

>[!NOTE]
>De e-mailberichten van het Centrum van acties functioneren op het organisatieniveau zodat zullen de abonnees berichten voor alle programma&#39;s en milieu&#39;s binnen die programma&#39;s ontvangen.

## Gedetailleerde gebruikersstroom {#detailed-user-flow}

Als u op de e-mail klikt, gaat u naar het Actions Center. In een pop-up ziet u de context van de melding waarop u hebt geklikt en in sommige gevallen gaat u naar aanvullende informatie over het uitvoeren van corrigerende maatregelen. U hebt ook rechtstreeks toegang tot het Actions Center op [https://experience.adobe.com/aem/actions-center](https://experience.adobe.com/aem/actions-center/), waar u het relevante programma en de omgeving kunt selecteren.

![Gegevens over incidenten](/help/operations/assets/incident-details.png)

Klik op de knop **Meer informatie** de verbinding navigeert de gebruiker aan dit artikel, waar het berichttype in kan van verwijzingen worden voorzien [tabel met ondersteunde berichttypen](#supported-notification-types) hieronder, dat een leidraad biedt voor de te nemen maatregelen.

In het Centrum van Acties, kunt u een lijst van andere recente berichten zien. Men adviseert dat het gebruiken van de lijst van Acties, u een bericht bevestigt om aan Adobe te signaleren dat uw organisatie zich van de taak bewust is, en het bericht later op te lossen wanneer de correctieve actie is ondernomen.

![Lijst met meldingen](/help/operations/assets/notification-list.png)

In de meeste gevallen moet de pop-up alle noodzakelijke context bieden om het probleem op te lossen. Als er echter vragen zijn voor ondersteuning van Adoben, kunt u op de knop **Contact opnemen met ondersteuning** in het pop-upvenster. Dit zal omhoog een vorm van waar u de vraag kunt beschrijven en het voorleggen om een kaartje van de Steun te creëren, dat ook een verwijzing naar de specifieke kennisgeving zal omvatten zodat heeft een Ingenieur van de Steun van de Adobe de relevante context.

![Contact opnemen met ondersteuning 1](/help/operations/assets/contact-support1.png)

![Contact opnemen met ondersteuning 2](/help/operations/assets/contact-support2.png)

Zoals alle steunkaartjes, zal het in [Tabblad Adobe Admin Console-ondersteuningsgevallen](https://helpx.adobe.com/enterprise/using/support-for-enterprise.html), waar u het kunt bijhouden en aanvullende opmerkingen kunt toevoegen.

![Ondersteuning voor Admin Consoles](/help/operations/assets/admin-console-support.png)

## Welke meldingen worden weergegeven? {#which-notification}

AEM as a Cloud Service heeft verschillende soorten meldingen, maar er wordt alleen een subset weergegeven in het Actions Center, zoals in de onderstaande tabel wordt geïllustreerd.

| Meldingstype | Beschrijving | Hoe te vormen | Wordt weergegeven in actiecentrum |
|---------------------------------|-----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------|
| Operationele incidenten | Kritieke incidenten die onmiddellijke actie vereisen | Gebruiker toegewezen aan productprofiel &quot;Incident Notification - Cloud Service&quot; | X |
| Proactieve aanbevelingen | Optimalisaties die moeten worden gepland | Gebruiker toegewezen aan productprofiel &quot;Proactieve kennisgeving - Cloud Service&quot; | X |
| Klassepijplusstatussen van Cloud Manager | Informatie over de toestand van uw pijpleidingen | Gebruiker met de rollen Bedrijfs van de Eigenaar, van de Manager van het Programma, of van de Manager van de Plaatsing, &quot;Andere&quot;checkbox binnen geselecteerd [Voorkeuren Experience Cloud](https://experience.adobe.com/preferences), als [hier beschreven](/help/implementing/cloud-manager/notifications.md). |                           |

## Ondersteunde berichttypen {#supported-notification-types}

In de volgende tabel worden de berichttypen weergegeven die momenteel worden ondersteund in Actions Center. Meldingen zijn momenteel beperkt tot productieomgevingen.

| Meldingstype | Verwante productprofiel | Correctieve actie |
|---------------------------------|-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Geblokkeerde replicatiewachtrij | Incident | Blokkeren van wachtrij opheffen door instructies in het dialoogvenster [Replicatiedocumentatie](/help/operations/replication.md#troubleshooting) |
| Ongeldige aaneengesloten GraphQL-query | Incident | Corrigeer de ongeldige GraphQL-query door te verwijzen naar de [Blijvende documentatie over probleemoplossing voor GraphQL-query&#39;s](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/headless/graphql-api/persisted-queries-troubleshoot.html) |
| Verkeerspiek bij oorsprong | Incident | Protect uw oorsprong door de regels van de het verkeersfilter van de tariefgrens te vormen die bij lagere drempels dan de standaardverkeerspiek bij oorsprongsalarm teweegbrengen.  Zie de [Het blokkeren Dos en aanvallen DDoS gebruikend verkeersregels](/help/security/traffic-filter-rules-including-waf.md#blocking-dos-and-ddos-attacks-using-traffic-filter-rules) sectie van de documentatie van de Regels van de Filter van het Verkeer, die verwijzingen een leerprogramma. |
| S2S-certificaat vervalt | Proactief | Leer hoe u een referentie kunt vernieuwen in het dialoogvenster [Access Tokens genereren voor documentatie van server-side API&#39;s](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials) | Aantal hoge verbindingen | Proactief | Meer informatie over het samenvoegen van verbindingen in [Verbindingspoolen naast de documentatie van het Geavanceerde Voorzien van een netwerk](/help/security/configuring-advanced-networking.md#connection-pooling-advanced-networking) |
| Verouderde gebruikerstoewijzing voor de service | Proactief | Leer hoe u de nieuwere indeling voor gebruikerstoewijzingen voor verkoopservices gebruikt, zoals aangegeven in [Beste praktijken voor het Verkopen van de Toewijzing van de Gebruiker van de Dienst en de Definitie van de Gebruiker van de Dienst](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/best-practices-for-sling-service-user-mapping-and-service-user-definition) |
| Aantal hoge verbindingen | Proactief | Meer informatie over het samenvoegen van verbindingen in het dialoogvenster [Geavanceerde netwerkdocumentatie](/help/security/configuring-advanced-networking.md#connection-pooling-advanced-networking) |
