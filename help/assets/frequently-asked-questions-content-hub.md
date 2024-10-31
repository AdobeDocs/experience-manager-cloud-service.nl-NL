---
title: Veelgestelde vragen (FAQ's) voor Content Hub
description: Antwoorden op enkele veelgestelde vragen (FAQ's) voor Content Hub.
source-git-commit: 3b8a80e346fe63450f9b57733c67de2e4b52b2b8
workflow-type: tm+mt
source-wordcount: '1093'
ht-degree: 0%

---

# Content Hub veelgestelde vragen {#content-hub-frequently-asked-questions}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

![ Content Hub vaak gestelde vraag ](assets/content-hub-faqs.png)

## Wat is Content Hub? {#what-is-content-hub}

Content Hub is een functie van Adobe Experience Manager Assets as a Cloud Service.

Content Hub stelt bredere teams in staat om eenvoudig relevante, goedgekeurde middelen te ontdekken via een intuïtief portaal en deze snel aan te passen aan hun behoeften.  Daarnaast biedt Content Hub een inspraakmechanisme waarmee deze gebruikers eenvoudig zelf kunnen werken wanneer ze elementen uploaden naar de DAM. Dit komt direct tegemoet aan de behoefte van organisaties aan een hogere snelheid voor het creëren van inhoud, terwijl de consistentie van merken en de naleving van passende waarborgen behouden blijven.

## Waarom kan ik Content Hub niet inschakelen voor mijn Cloud Manager-programma/omgeving? {#cannot-enable-content-hub}

Content Hub is op dit moment alleen beschikbaar voor AEM Cloud Manager Production-programma&#39;s, die een Assets-licentie bevatten. Wanneer u [ Content Hub ](/help/assets/deploy-content-hub.md#enable-content-hub) klikt om het toe te laten, wordt het opgesteld en geassocieerd met het milieu van de auteursproductie van AEM in dat programma. Zie [ Content Hub ](/help/assets/deploy-content-hub.md) voor details en eerste vereisten opstellen.

Er is een programma voor vroege toegang tot Content Hub voor Sandbox-programma&#39;s/productieomgevingen van auteurs. Voor meer informatie, zie [ Inleiding aan Programma&#39;s Sandbox ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md). Neem contact op met het accountteam van uw Adobe voor meer informatie over het programma voor vroege toegang.

Content Hub is in dit stadium niet beschikbaar voor omgevingen die niet voor productie bestemd zijn (werkgebied, dev, enzovoort).

## Ik heb Content Hub ingeschakeld in mijn productieprogramma/omgeving. Mag ik het uitschakelen? {#can-i-disable-content-hub}

Als Content Hub in staat wordt gesteld een productieprogramma uit te voeren, maakt het deel uit van de productie-infrastructuur. AEM Cloud Manager staat het verwijderen of uitschakelen van de productie-infrastructuur niet toe om het risico voor het productiegebruik door menselijke fouten tot een minimum te beperken.

Als u geen Content Hub aan uw gebruikers wilt verstrekken zodra het wordt opgesteld, wijs geen gebruikers aan het het productprofiel van Content Hub in Admin Console toe. Zie [ Content Hub ](/help/assets/deploy-content-hub.md#content-hub-instance-product-profile) voor details opstellen.

## Hoe kan ik Content Hub in mijn organisatie beoordelen, aangezien het alleen beschikbaar is voor productieprogramma&#39;s/productieontwerpomgevingen? {#how-can-i-evaluate-content-hub}

Content Hub is een functie die door de Adobe wordt geleverd en onderhouden en heeft geen aangepaste code waarvoor typische validatie via dev/stage/production nodig is. Bovendien, wordt de toegang tot de eigenschap voor gebruikers volledig gecontroleerd door de beheerder, zodat kunt u het evalueren zonder het aan alle gebruikers bloot te stellen.

Het is mogelijk om Content Hub te evalueren zonder gevolgen voor uw gebruikers/productie-inhoud die in AEM as a Cloud Service Assets wordt beheerd. Een evaluatieprocedure kan er als volgt uitzien:

* [ laat Content Hub ](/help/assets/deploy-content-hub.md#enable-content-hub) op productiemilieu (het programma van Cloud Manager) toe
* [ voeg een AEM gebruiker van de Beheerder ](/help/assets/deploy-content-hub.md#onboard-content-hub-administrator) van de productiesauteur aan het productprofiel van Content Hub toe.
* AEM Beheerder [ vormt Content Hub ](/help/assets/configure-content-hub-ui-options.md)
* AEM Beheerder of een AEM Gebruiker op AEM productiesauteur [ keurt een aantal activa voor Content Hub ](/help/assets/approve-assets-content-hub.md) goed; als u geen productieinhoud in DAM wilt veranderen, zou u een afzonderlijke evaluatiemap in de AEM auteurinstantie kunnen willen tot stand brengen, en upload/markering of kopieer sommige activa van DAM in het.
* De beheerder van de Admin Console voegt [ een paar geselecteerde gebruikers ](/help/assets/deploy-content-hub.md#onboard-content-hub-users) aan het het productprofiel van Content Hub toe, zodat zij evaluatie kunnen beginnen.
* Nadat de evaluatie is voltooid, kunnen AEM Gebruikers in auteurinstantie goedkeuring uit testactiva verwijderen, productieactiva voor Content Hub goedkeuren, en dan kan de beheerder van de Admin Console alle gebruikers toevoegen die toegang tot Content Hub en goedgekeurde inhoud nodig hebben. Gefeliciteerd, je Content Hub is nu live.

Adobe biedt Content Hub ook vroege toegang tot Stage-omgevingen - raadpleeg de vraag [ Waarom kan ik Content Hub niet inschakelen in mijn Cloud Manager-programma/omgeving?](#cannot-enable-content-hub) voor meer informatie.

## Waarom zie ik geen middelen na het aanmelden bij Content Hub? {#no-assets-in-content-hub}

De activa die als goedgekeurd in Assets as a Cloud Service zijn gemarkeerd, zijn automatisch beschikbaar in Content Hub. Als er na het aanmelden bij Content Hub geen elementen worden weergegeven, moet u elementen goedkeuren met behulp van de AEM as a Cloud Service-auteursomgeving om deze beschikbaar te maken in Content Hub. Voor meer informatie, zie [ activa voor Content Hub ](/help/assets/approve-assets-content-hub.md) goedkeuren.

## Waarom zie ik mijn middelen niet die ik of direct gebruikend Content Hub upload of hen van Dropbox of rekeningen Importeer OneDrive gebruikend Content Hub? {#no-assets-uploaded-from-content-hub}

De vertoning van activa die gebruikend Content Hub worden geupload hangt af van als u de [ auto-goedkeuring ](/help/assets/configure-content-hub-ui-options.md#configure-import-options-content-hub) knevel beschikbaar op het gebruikersinterface van de Configuratie hebt toegelaten:

* Als de **auto-goedkeuring** knevel wordt toegelaten, zijn de activa die u gebruikend Content Hub uploadt automatisch beschikbaar.

* Als de **auto-goedkeuring** knevel gehandicapt is, tonen de activa die u gebruikend Content Hub uploadt niet automatisch. De middelen zijn beschikbaar in de `hydrated-assets` map van uw as a Cloud Service omgeving van Assets. Navigeer aan de omslag en [ bulkgeef ](/help/assets/approve-assets-content-hub.md) het statuut van die activa `Approved` voor die activa uit om in Content Hub te tonen.

## Hoe kunt u snel middelen zoeken die met Content Hub zijn geüpload naar een AEM as a Cloud Service-omgeving? {#find-uploaded-assets-on-aem-cloud}

Middelen die met Content Hub zijn geüpload in een AEM as a Cloud Service-omgeving, kunt u snel vinden op:

1. Navigeer naar de map `hydrated-assets` .

1. Klik op **[!UICONTROL Filters]** en stel **[!UICONTROL No Status]** in het veld **[!UICONTROL Asset Status]** in.

1. Elementen sorteren met het veld **[!UICONTROL Modified Date]** .

## Waarom bekijk ik niet uitgeven gebruikend de optie van de Adobe Express op mijn activakaart om activa opnieuw te mengen om nieuwe variaties tot stand te brengen? {#edit-using-express-not-available}

Om uit te geven gebruikend de optie van de Adobe Express op de activakaart, moet u Adobe Express rechten naast voorrechten voor [ gebruikers van Content Hub met rechten hebben om activa aan nieuwe variaties ](#onboard-content-hub-users-add-assets) opnieuw te mengen. De Adobe Express moet in de zelfde organisatie in de console van Admin van de Adobe worden opgesteld waar Adobe Experience Manager wordt opgesteld.

## Kan ik Content Hub zo instellen dat de merkrichtlijnen van mijn organisatie als een link op de homepage worden weergegeven? {#content-hub-setup-brand-guidelines}

U kunt aangepaste koppelingen als afzonderlijke tabbladen toevoegen, naast de standaardtabbladen Alle Assets, Verzamelingen en Inzichten op de startpagina van Content Hub. Voor informatie over hoe te om het te plaatsen, zie [ de Verbindingen van de Douane ](/help/assets/configure-content-hub-ui-options.md#configure-custom-links-content-hub).

## Bestaat er een plan voor het migreren van bestaande Brand Portal-klanten naar Content Hub? {#migration-brand-portal}

Adobe biedt migratieondersteuning van Brand Portal naar Content Hub die u kunt gebruiken door een Adobe-ondersteuningsticket te maken.

## Waarom kan ik de optie Productinstellingen/Configuratie in Content Hub niet zien? {#ui-configuration-option-missing}

Om tot het [ Gebruikersinterface van de Configuratie ](/help/assets/configure-content-hub-ui-options.md) toegang te hebben, moet u a [ Beheerder van Content Hub ](/help/assets/deploy-content-hub.md##onboard-content-hub-administrator) zijn. Als u aan het het productprofiel van AEM Beheerders op de productie auteursinstantie in Adobe Admin Console wordt toegewezen en u nog steeds niet de configuratieoptie ziet, zorg ervoor dat het het productprofiel van AEM Beheerders niet anders wordt genoemd. Zie [ het Team van AEM as a Cloud Service en de Profielen van het Product ](/help/onboarding/aem-cs-team-product-profiles.md) voor meer details.


