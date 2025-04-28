---
title: Handelingencentrum
description: Gebruik het actiecentrum om incidenten en andere belangrijke informatie op een gemakkelijke manier aan te pakken
exl-id: d5a95ac4-aa88-44d5-ba02-7c9702050208
feature: Operations
role: Admin
source-git-commit: 821dd9f172ea286a7a3de74cf8dec8001e9afee9
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 0%

---

# Handelingencentrum {#actions-center}

AEM as Cloud Service verzendt via e-mail meldingen van het Actions Center wanneer zich kritieke gebeurtenissen voordoen die onmiddellijke actie vereisen, en proactieve aanbevelingen voor optimalisatie. De voorbeelden omvatten een geblokkeerde rij, of een het verlopen reeks geloofsbrieven; de volledige reeks het berichttypes van het Centrum van Acties kan in de [ lijst hieronder ](#supported-notification-types) worden bekeken, die in tijd zal uitbreiden.

Wanneer een e-mailbericht van het Centrum van Acties wordt ontvangen, kan het worden geklikt om het Centrum van Acties van AEM as a Cloud Service met een pop-up te openen die extra context toont waarin de actie voor een klant wordt verklaard te nemen.

Naast het weergeven van informatie over het zojuist geklikte e-mailbericht, fungeert het Actions Center als een hub waarin u de set met huidige en oudere meldingen kunt weergeven en beheren. <!-- It can be accessed directly at the url TBD (Alexandru: I'm intentionally keeping it TBD for now so customers do not find it) -->

Er zijn twee categorieën meldingen op hoog niveau die in het Actions Center worden weergegeven:

1. Operationele incidenten - er is een gebeurtenis opgetreden waarvoor meestal een snelle oplossing vereist is. Bijvoorbeeld het oplossen van een geblokkeerde wachtrij.
1. Proactieve aanbevelingen - Adobe heeft een aanbeveling voor een actie die een klant in de nabije toekomst zou moeten ondernemen. Bijvoorbeeld, ophouden verwijzend naar een afgekeurde UI.

Zie de [ lijst hieronder ](#supported-notification-types) voor de berichten momenteel gesteund in het Centrum van Acties.

Vanuit het Actions Center kunt u een specifiek programma en een specifieke omgeving selecteren die het effect hebben van filteren voor dat bereik.

## Configuratie {#configuration}

Om het ontvangen de e-mailberichten van het Centrum van Acties te vormen, creeer de Profielen van het Product zoals die onder [ Profielen van het Bericht ](/help/journey-onboarding/notification-profiles.md) worden beschreven, namelijk Bericht van het Ongeval - Cloud Service en Proactieve Bericht - Cloud Service. Wijs ook de juiste Adobe-id&#39;s van uw organisatie toe aan die profielen. Hierdoor kan een beheerder bepalen welke gebruikers in aanmerking komen om deze e-mailberichten te ontvangen.

>[!NOTE]
>De e-mailberichten van het Centrum van acties functioneren op het organisatieniveau zodat zullen de abonnees berichten voor alle programma&#39;s en milieu&#39;s binnen die programma&#39;s ontvangen.

## Gedetailleerde gebruikersstroom {#detailed-user-flow}

Als u op de e-mail klikt, gaat u naar het Actions Center. In een pop-up ziet u de context van de melding waarop u hebt geklikt en in sommige gevallen gaat u naar aanvullende informatie over het uitvoeren van corrigerende maatregelen. U kunt tot het Centrum van Acties direct in [ https://experience.adobe.com/aem/actions-center ](https://experience.adobe.com/aem/actions-center/) ook toegang hebben, waar u het relevante programma en het milieu kunt selecteren.

![ Incidentdetails ](/help/operations/assets/incident-details.png)

Het klikken van **Leer meer** verbinding navigeert de gebruiker aan dit artikel, waar het berichttype in de [ gesteunde lijst van berichttypes ](#supported-notification-types) kan worden van verwijzingen voorzien hieronder, die begeleiding op welke actie verstrekt te nemen.

In het Centrum van Acties, kunt u een lijst van andere recente berichten zien. U wordt aangeraden de lijst Handelingen te gebruiken om een melding te bevestigen dat uw organisatie op de hoogte is van de taak en om de melding later op te lossen wanneer corrigerende maatregelen zijn genomen.

![ lijst van het Bericht ](/help/operations/assets/notification-list.png)

In de meeste gevallen moet de pop-up alle noodzakelijke context bieden om het probleem op te lossen. Nochtans, als er vragen voor de Steun van Adobe zijn, kunt u de **verbinding van de Steun van het Contact** in pop-up klikken. Zo wordt een formulier weergegeven waaruit u de vraag kunt beschrijven en deze kunt verzenden voor het maken van een ondersteuningsticket. Dit formulier bevat ook een verwijzing naar de specifieke melding, zodat een Adobe Support Engineer de relevante context heeft.

![ de steun van het Contact 1 ](/help/operations/assets/contact-support1.png)

![ de steun van het Contact 2 ](/help/operations/assets/contact-support2.png)

Als alle steunkaartjes, zal het in de [ Gevallen van de Steun van Adobe Admin Console tabel ](https://helpx.adobe.com/enterprise/using/support-for-enterprise.html) verschijnen, waar u het kunt volgen en extra commentaren toevoegen.

![ de Steun van Admin Console ](/help/operations/assets/admin-console-support.png)

## Welke meldingen worden weergegeven? {#which-notification}

AEM as a Cloud Service heeft verschillende soorten meldingen, maar er wordt alleen een subset weergegeven in het Actions Center, zoals in de onderstaande tabel wordt geïllustreerd.

| Meldingstype | Beschrijving | Hoe te vormen | Wordt weergegeven in actiecentrum |
|---------------------------------|-----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------|
| Operationele incidenten | Kritieke incidenten die onmiddellijke actie vereisen | Gebruiker toegewezen aan productprofiel &quot;Incident Notification - Cloud Service&quot; | X |
| Proactieve aanbevelingen | Optimalisaties die moeten worden gepland | Gebruiker toegewezen aan productprofiel &quot;Proactive Notification - Cloud Service&quot; | X |
| Cloud Manager-pijpleidingstatussen | Informatie over de toestand van uw pijpleidingen | Gebruiker met BedrijfsEigenaar, de Manager van het Programma, of de rollen van de Manager van de Plaatsing, &quot;Andere&quot;checkbox die in [ de Voorkeur van Experience Cloud ](https://experience.adobe.com/preferences) wordt geselecteerd, zie [ Meldingen ](/help/implementing/cloud-manager/notifications.md). |                           |

## Ondersteunde berichttypen {#supported-notification-types}

In de volgende tabel worden de berichttypen weergegeven die momenteel worden ondersteund in Actions Center. Meldingen zijn momenteel beperkt tot productieomgevingen.

| Meldingstype | Verwante productprofiel | Correctieve actie |
|---------------------------------|-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Geblokkeerde replicatiewachtrij | Incident | Ontgrendel rij door instructies in de [ Documentatie van de Replicatie ](/help/operations/replication.md#troubleshooting) te volgen |
| Ongeldige aaneengesloten GraphQL-query | Incident | Verbeter de ongeldige vraag van GraphQL door naar de [ Persisted GraphQL van verwijzingen te verwijzen het oplossen van problemendocumentatie ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/headless/graphql-api/persisted-queries-troubleshoot.html) |
| Verkeerspiek bij oorsprong | Incident | Bescherm uw oorsprong door de regels van de het verkeersfilter van de tariefgrens te vormen die bij lagere drempels dan de standaardverkeerspiek bij oorsprongsalarm teweegbrengen.  Zie [ het Blokkeren Dos en aanvallen DDoS gebruikend verkeersregels ](/help/security/traffic-filter-rules-including-waf.md#blocking-dos-and-ddos-attacks-using-traffic-filter-rules) sectie van de documentatie van de Regels van de Filter van het Verkeer, die verwijzingen een leerprogramma. |
| Regels voor CDN-verkeersfilters geactiveerd | Incident | Als de aangepaste regel van de verkeersfilter op een aanval wijst, en uw plaats dat verkeer niet blokkeert, beschermt uw plaats door een regel van de verkeersfilter op het blokkeren wijze te vormen. Zie [ Beschermend websites met de regels van de verkeersfilter (met inbegrip van de regels van WAF) ](/help/security/traffic-filter-rules-including-waf.md#tutorial-protecting-websites) sectie van de documentatie van de Regels van de Filter van het Verkeer, die verwijzingen een leerprogramma. |
| Fouten in het log doorsturen van delen | Incident | Controleer uw Splunk eindpunt werkt en bereikbaar is vanuit uw AEM Cloud Service-omgeving. Voor meer informatie bij logboek door:sturen, bezoek het [ logboek dat van de Splunk documentatie ](/help/implementing/developing/introduction/logging.md#splunk-logs) door:sturen. Als u hulp het oplossen van problemen nodig hebt, of veranderingen in uw registrerenconfiguratie moet aanbrengen, neem een steunkaartje met Adobe op. |
| Pagina&#39;s bevatten veel knooppunten | Proactief | Het totale aantal knooppunten op een pagina verminderen. Verwijs naar [ documentatie van de Complexiteit van de Pagina ](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/pcx) | |
| Groot aantal actieve workflowinstanties | Proactief | Beëindig actieve workflows die niet meer nodig zijn. Leer hoe te [ een zuiveringsbaan ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/maintenance) vormen |               |
| S2S-certificaat vervalt | Proactief | Leer hoe te om een referentie in [ te verfrissen die Tokens van de Toegang voor de Server Zijde APIs documentatie produceren ](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials) | Aantal hoge verbindingen | Proactief | Leer over verbinding het pooling in [ Pooling van de Verbinding naast de Geavanceerde documentatie van het Voorzien van een netwerk ](/help/security/configuring-advanced-networking.md#connection-pooling-advanced-networking) |
| Verouderde gebruikerstoewijzing voor de service | Proactief | Leer hoe te om het nieuwere Verschuivende formaat van de Toewijzing van de Gebruiker van de Dienst te gebruiken, zoals vermeld in [ Beste praktijken voor het Verdelen van de Toewijzing van de Gebruiker van de Dienst en de Definitie van de Gebruiker van de Dienst ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/best-practices-for-sling-service-user-mapping-and-service-user-definition) |
| Aantal hoge verbindingen | Proactief | Leer over verbinding het pooling in de [ Geavanceerde documentatie van het Voorzien van een netwerk ](/help/security/configuring-advanced-networking.md#connection-pooling-advanced-networking) |  |
| Gebruikers die rechtstreeks aan een aangepaste groep zijn toegevoegd | Proactief | Gebruikers moeten worden toegevoegd aan relevante IMS-groepen en deze IMS-groepen moeten worden toegevoegd als leden van AEM-groepen. Lijn met [ IMS beste praktijken ](/help/security/ims-support.md) uit | |
| Ontbrekende JCR-inhoud | Proactief | Voeg het ontbrekende knooppunt voor JCR-inhoud toe. Verwijs naar [ de documentatie van de Validator van de Inhoud van Assets ](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/acv) | |
| Voltooide workflows niet gewist | Proactief | Minimaliseer het aantal workflowinstanties en verbeter de prestaties door workflowinstanties van meer dan 90 dagen oud te wissen. Leer hoe te [ om onderhoudstaken ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/maintenance) te vormen | |
| Ontbrekend Sling-brontype in pagina | Proactief | Ontbrekend knooppunt voor Sling-resource toevoegen. Verwijs naar [ de documentatie van de Validator van de Inhoud van Assets ](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/acv) | |
| Langzame query | Proactief | Repareer langzame vragen door correcte indexdefinities te bepalen zoals die door het [ JCQ vraagbedriegblad ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/JCR_query_cheatsheet-v1.1.pdf) worden voorgesteld | |
| Query zonder index | Proactief | Vermijd uitvoerend vraag die geen index gebruikt - [ verbinding aan het Indexeren documentatie ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/indexing) |