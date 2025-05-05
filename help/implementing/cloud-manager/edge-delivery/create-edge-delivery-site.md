---
title: Een Edge Delivery-site maken in Cloud Manager
description: Klik op een knop om snel een Edge Delivery-site te maken in Cloud Manager.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 0e30cf827e764a356dde304df3124d0be3d2e58b
workflow-type: tm+mt
source-wordcount: '1101'
ht-degree: 0%

---


# Over Een Edge Delivery-site maken in Cloud Manager {#about-one-click-edge-delivery-site}

De functie Een Edge Delivery-site maken is ontworpen om u te helpen bij het automatiseren van het aan boord nemen en implementeren van Edge Delivery-sites in Cloud Manager. Het vereenvoudigt het proces enorm door u te laten één enkele knoop klikken. Dat enige klikbepalingen de vereiste infrastructuur, integreert met GitHub voor versiecontrole, en vormt uw document en activaopslag in de Aandrijving van Google.

Deze automatisering helpt de handmatige inspanningen te verminderen die nodig zijn om uw eerste site in te stellen. Het zorgt voor naadloze workflows, schaalbaarheid en verbetert de prestaties van uw teams als het gaat om het beheren van inhoud aan de rand.

## Belangrijkste concepten {#key-concepts}

Belangrijke concepten wanneer u met één klik een Edge Delivery-site maakt in Cloud Manager.

| Belangrijk concept | Beschrijving |
| --- | --- |
| Automated Edge-implementatie | <ul><li>Gebruikers kunnen direct Edge Delivery-sites maken en configureren.</li><li>Door Cloud Manager-integratie met CI/CD-workflow te gebruiken, vermindert of verwijdert u de noodzaak van handmatige instapprocessen.</li><li>Geïntegreerd met Cloud Manager voor naadloze CI/CD-workflows.</li></ul> |
| Integratie met Cloud Manager | <ul><li>Gebruikt Cloud Manager-gebruikersinterface om het One Click Edge Delivery-proces te activeren.</li><li>Toegang bieden tot het maken en implementeren van geautomatiseerde gegevensopslagruimten.</li></ul> |
| Op GitHub gebaseerde versiecontrole | <ul><li>Creeert een bewaarplaats GitHub binnen een organisatie gebruikend vooraf bepaalde boilerplate malplaatjes om plaatsingen te standaardiseren.</li><li>Koppelingen met AEM Bot voor updates van inhoud.</li></ul> |
| Integratie van documenten en middelen | <ul><li>Genereert een Google Drive-map voor opslag.<li>Hiermee installeert u de AEM Code Sync-toepassing in de repository, zodat u verzekerd bent van naadloze synchronisatie en implementatie.</li></li><li>Medewerkers kunnen documenten eenvoudig beheren.</li></ul> |
| Beveiliging en schaalbaarheid | <ul><li>Zorgt voor naleving van de beveiligingsnormen voor bedrijven.</li><li>Ondersteunt meerdere Edge Delivery-sites onder verschillende Cloud Manager-huurders.</li></ul> |

<!-- >
## Practical use cases {#use-cases}

| Use case | Description |
| --- | --- |
| Website and application deployment | <ul><li>Automate the hosting and delivery of static or dynamic sites.</li><li>Ensure fast performance through edge caching. </li></ul> |
| API gateway and content delivery | <ul><li>Optimize API responses by caching data at the edge.</li><li>Reduce backend load and improved response times. </li></ul> |
| Real-time content updates | <ul><li>Instant deployment of new content across edge locations.</li><li>Support integration with automated content pipelines. </li></ul> |
| Edge computing workloads | <ul><li>Support serverless computing to process workloads closer to users.</li><li>Reduce latency and enhance performance. </li></ul> |
| Security and governance | <ul><li>Security is provided with integrated DDoS (Distributed Denial of Service) protection and WAF (Web Application Firewall) integration.</li><li>Ensure that content is delivered securely through TLS (Transport Security Layer) encryption. </li></ul> |
-->

## Een Edge Delivery-site maken in Cloud Manager met één klik {#one-click-edge-delivery-site}

Als u met één klik een Adobe Edge Delivery-site wilt maken, moet uw organisatie over een beschikbare Edge Delivery Services-licentie beschikken. Deze licentie maakt deel uit van Adobe Experience Manager (AEM) en is nodig voor het maken van Edge Delivery Services in Cloud Manager.

In termen van toestemmingen, moet u lid van de rol van BedrijfsEigenaar zijn of de aangewezen toestemmingen zijn verleend om programma&#39;s in Cloud Manager toe te voegen of uit te geven. Met dit toegangsniveau kunt u de integratie van Edge Delivery Services in uw programma&#39;s beheren.

Zie ook [ Inleiding aan Edge Delivery Services in Cloud Manager ](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md).

<!-- PROPER AEM BOT CONFIGURATIONS MUST BE IN PLACE FIRST FOR AUTOMATIC CONTENT UPDATES? TRUE or FALSE? -->

**om een plaats van Edge Delivery in Cloud Manager met één klik tot stand te brengen:**

1. Meld u aan bij Cloud Manager op [`https://my.cloudmanager.adobe.com` ](https://my.cloudmanager.adobe.com/) en selecteer het gewenste programma.
1. In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het linkerzijmenu te openbaren.
1. In het linkerzijmenu, onder de **rubriek van het Programma**, klik **Overzicht**.
1. Voor de **pagina van het Overzicht van het 0&rbrace; Programma, klik** Edge Delivery **tabel.**
1. Op de pagina van Edge Delivery, in **Edge Delivery om lijst** dialoogdoos te doen, in **voeg Edge Delivery plaats** groepsvakje toe, klik **creeer plaats nu**.
1. In **creeer de plaats van Edge Delivery** dialoogdoos, op het **3&rbrace; tekstgebied van de Naam van het Project &lbrace;, ga de naam van uw plaats in, dan klik** creeer plaats nu **.**

   In het midden boven op het scherm wordt een pop-up weergegeven om u te laten weten dat de Edge Delivery-siteprovisioning is gestart.

Wanneer de plaatslevering en de bevestiging door Cloud Manager volledig zijn, verschijnt de **naam van de Plaats** (de projectnaam u vroeger) inging in het **de plaatsen van Edge Delivery** lijstvakje op de pagina van Edge Delivery. Links van de URL van de gegevensopslagruimte wordt bovendien een groen vinkje weergegeven.


### Een Edge Delivery-site verkennen die met één klik is gemaakt {#explore-one-click-ed-site}

1. Meld u aan bij Cloud Manager op [`https://my.cloudmanager.adobe.com` ](https://my.cloudmanager.adobe.com/) en selecteer het gewenste programma.
1. In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het linkerzijmenu te openbaren.
1. In het linkerzijmenu, onder de **rubriek van het Programma**, klik **Overzicht**.
1. Voor de **pagina van het Overzicht van het 0&rbrace; Programma, klik** Edge Delivery **tabel.**
1. Voer op de Edge Delivery-pagina een van de volgende handelingen uit:

   | Wat te verkennen | Stappen |
   | --- | --- |
   | GitHub-opslagplaats van een site | <ul><li>In het **de plaatsen van Edge Delivery** lijstvakje, onder de **3&rbrace; kolomrubriek van de Bewaarplaats &lbrace;, klik URL van de plaats u enkel creeerde.**<br> u kunt worden vereist om binnen aan GitHub met uw gebruikersbenaming of e-mailadres en uw wachtwoord te ondertekenen.</li> |
   | Een site publiceren | <ul><li> In het **de plaatsen van Edge Delivery** lijstvakje, uiterst rechts van de naam van uw plaats, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) om het drop-down menu te openen.</li><li>Klik ![ publiceren het pictogram van de Controle ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_PublishCheck_18_N.svg) **publiceren plaats** in het drop-down menu.<br> A toast bericht lijkt latend u dat het publiceren van de plaats met succes is begonnen.</li></ul> |
   | Een voorvertoning van een gepubliceerde site weergeven | <ul><li>In het **de plaatsen van Edge Delivery** lijstvakje, onder de **naam van de Plaats** kolomrubriek, klik URL van de plaats u enkel creeerde en publiceerde.<br> in de bar van het Adres URL van uw browser, merk op dat URL van de plaats met `.page` het erop wijzen beëindigt die dat u een voorproef van de plaats ziet.</li><li>Als u de site live wilt zien, wijzigt u `.page` handmatig in `.live` op de URL-adresbalk.</li></ul> |
   | Gebruikers toegang geven tot de opslagplaats voor inhoud op Google Drive | <ul><li> In het **de plaatsen van Edge Delivery** lijstvakje, uiterst rechts van de naam van uw plaats, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) om het drop-down menu te openen.</li><li>Klik ![ Gebruikers toevoegen pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_UsersAdd_18_N.svg) **toegang van de Versterking tot de inhoudsbewaarplaats** in het drop-down menu.</li><li>In **voeg medewerkers aan uw plaats** dialoogdoos toe, ga het e-mailadres van een medewerker in, dan klik ![ pictogram van het Vinkje ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg).</li><li>Voeg indien nodig e-mails van contribuanten toe.</li><li>Wanneer u wordt gebeëindigd, klik **medewerkers** toevoegen.</li><li>Om de verbinding met uw inhoudsmedewerkers te delen, in **met succes toegevoegde Collaboration** dialoogdoos, klik O.K. **&#x200B;**.</li><li>In Collaboration voegde met succes dialoogdoos toe, klik ![ pictogram van het Exemplaar ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) om de verbinding te kopiëren en het met uw medewerkers te delen.<br> alvorens de verbinding te delen, bevestig dat de medewerkers met het e-mailadres verbonden aan hun rekening worden het programma geopend IMS. Als hun IMS-e-mailaccount niet beschikbaar is, moeten ze het e-mailadres gebruiken dat is toegevoegd als medewerker. Zo zorgt u ervoor dat medewerkers toegang hebben tot de koppeling en de inhoud kunnen bekijken die u wilt bewerken of bijwerken op Google Drive.</li><li>Wanneer gedaan het uitgeven, klik **publiceren plaats** in Cloud Manager, zoals hierboven beschreven.<br> Of, voorproef de aangebrachte veranderingen, zoals hierboven beschreven.</li></ul> |
   | Geef gebruikers toegang tot de basisbewaarplaats op GitHub | <ul><li> In het **de plaatsen van Edge Delivery** lijstvakje, uiterst rechts van de naam van uw plaats, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) om het drop-down menu te openen.</li><li>Klik ![ het pictogram van de Code ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Code_18_N.svg) **toegang van de Versterking tot de basisbewaarplaats** in het drop-down menu.</li><li>In de **Toegang tot de basisbewaarplaats voor uw plaats** dialoogdoos, ga de gebruikersbenaming GitHub van een medewerker in, dan klik ![ pictogram van het Vinkje ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg).</li><li>Ga zo nodig verder met het toevoegen van GitHub-gebruikersnamen.</li><li>Wanneer u wordt gebeëindigd, klik **medewerkers** toevoegen.</li>De gebruikers moeten toegang tot hun eigen gebruiker verlenen GitHub om de bewaarplaats te bekijken. |




