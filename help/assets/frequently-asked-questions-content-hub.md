---
title: Veelgestelde vragen (FAQ's) voor Content Hub
description: Antwoorden op enkele veelgestelde vragen (FAQ's) voor Content Hub.
exl-id: 74b5c308-c1d3-4787-9f1f-f64cf09d298a
source-git-commit: fb7ce7dbb58be9fef5ab087441457770828d73c8
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 0%

---

# Content Hub veelgestelde vragen {#content-hub-frequently-asked-questions}

![ Content Hub vaak gestelde vraag ](assets/content-hub-faqs.png)

## Wat is Content Hub? {#what-is-content-hub}

Content Hub is een onderdeel van Adobe Experience Manager Assets as a Cloud Service.

Content Hub stelt bredere teams in staat om eenvoudig relevante, goedgekeurde middelen te ontdekken via een intuïtief portaal en deze snel aan te passen aan hun behoeften.  Daarnaast biedt Content Hub een inspraakmechanisme waarmee deze gebruikers eenvoudig zelf kunnen werken wanneer ze elementen uploaden naar de DAM. Dit komt direct tegemoet aan de behoefte van organisaties aan een hogere snelheid voor het creëren van inhoud, terwijl de consistentie van merken en de naleving van passende waarborgen behouden blijven.

## Waarom kan ik Content Hub niet inschakelen voor mijn Cloud Manager-programma/omgeving? {#cannot-enable-content-hub}

Content Hub is op dit moment alleen beschikbaar voor AEM Cloud Manager Production-programma&#39;s, waaronder een Assets-licentie (Assets Cloud Service, Assets Ultimate, Assets). Wanneer u [ Content Hub ](/help/assets/deploy-content-hub.md#enable-content-hub) klikt om het toe te laten, wordt het opgesteld en geassocieerd met het milieu van de auteursproductie van AEM in dat programma. Zie [ Content Hub ](/help/assets/deploy-content-hub.md) voor details en eerste vereisten opstellen.

## Ik heb Content Hub ingeschakeld in mijn productieprogramma/omgeving. Mag ik het uitschakelen? {#can-i-disable-content-hub}

Als Content Hub in staat wordt gesteld een productieprogramma uit te voeren, maakt het deel uit van de productie-infrastructuur. AEM Cloud Manager staat het verwijderen of uitschakelen van de productie-infrastructuur niet toe om het risico voor het productiegebruik door menselijke fouten tot een minimum te beperken.

Als u geen Content Hub aan uw gebruikers wilt verstrekken zodra het wordt opgesteld, wijs geen gebruikers aan het het productprofiel van Content Hub in Admin Console toe. Zie [ Content Hub ](/help/assets/deploy-content-hub.md#content-hub-instance-product-profile) voor details opstellen.

## Hoe kan ik Content Hub in mijn organisatie beoordelen, aangezien het alleen beschikbaar is voor productieprogramma&#39;s/productieontwerpomgevingen? {#how-can-i-evaluate-content-hub}

Content Hub is een functie die Adobe biedt en onderhoudt en heeft geen aangepaste code die standaard moet worden gevalideerd via dev/stage/production. Bovendien, wordt de toegang tot de eigenschap voor gebruikers volledig gecontroleerd door de beheerder, zodat kunt u het evalueren zonder het aan alle gebruikers bloot te stellen.

Het is mogelijk om Content Hub te evalueren zonder gevolgen voor uw gebruikers/productie-inhoud die in AEM as a Cloud Service Assets wordt beheerd. Een evaluatieprocedure kan er als volgt uitzien:

* [ laat Content Hub ](/help/assets/deploy-content-hub.md#enable-content-hub) op productiemilieu (het programma van Cloud Manager) toe
* [ voeg een gebruiker van de Beheerder van AEM ](/help/assets/deploy-content-hub.md#onboard-content-hub-administrator) van de productieauteur aan het productprofiel van Content Hub toe.
* AEM Beheerder [ vormt Content Hub ](/help/assets/configure-content-hub-ui-options.md)
* De Beheerder van AEM of een Gebruiker van AEM op de productiesauteur van AEM [ keurt een aantal activa voor Content Hub ](/help/assets/approve-assets-content-hub.md) goed; als u geen productieinhoud in DAM wilt veranderen, zou u een afzonderlijke evaluatiemap in de de auteurinstantie van AEM kunnen willen tot stand brengen, en upload/markering of kopieer sommige activa van DAM in het.
* De beheerder van Admin Console voegt [ een paar geselecteerde gebruikers ](/help/assets/deploy-content-hub.md#onboard-content-hub-users) aan het het productprofiel van Content Hub toe, zodat zij evaluatie kunnen beginnen.
* Nadat de evaluatie is voltooid, kunnen AEM-gebruikers in de auteur goedkeuring verwijderen uit testmiddelen, productiemiddelen goedkeuren voor Content Hub en vervolgens kunnen Admin Console-beheerders alle gebruikers toevoegen die toegang tot Content Hub en goedgekeurde inhoud nodig hebben. Gefeliciteerd, je Content Hub is nu live.

Er is een programma voor vroege toegang tot Content Hub voor Sandbox-programma&#39;s en de productieomgevingen van de auteur. Voor meer informatie, zie [ Inleiding aan Programma&#39;s Sandbox ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md). Neem contact op met uw Adobe-accountteam voor meer informatie over het programma voor vroege toegang.

Content Hub is nog niet beschikbaar voor niet-productieomgevingen (stadium &amp; ontwikkeling). Assets Ultimate zal naar verwachting in maart 2025 beschikbaar zijn voor stadium-/ontwikkelomgevingen.

## Waarom zie ik geen middelen na het aanmelden bij Content Hub? {#no-assets-in-content-hub}

De activa die zijn gemarkeerd als goedgekeurd in Assets as a Cloud Service, zijn automatisch beschikbaar in Content Hub. Als er na het aanmelden bij Content Hub geen elementen worden weergegeven, moet u elementen goedkeuren met behulp van de AEM as a Cloud Service-auteursomgeving om deze beschikbaar te maken in Content Hub. Voor meer informatie, zie [ activa voor Content Hub ](/help/assets/approve-assets-content-hub.md) goedkeuren.

## Waarom zie ik mijn activa niet die ik of direct gebruikend Content Hub upload of hen uit Dropbox of rekeningen Importeer OneDrive gebruikend Content Hub? {#no-assets-uploaded-from-content-hub}

De vertoning van activa die gebruikend Content Hub worden geupload hangt af van als u de [ auto-goedkeuring ](/help/assets/configure-content-hub-ui-options.md#configure-import-options-content-hub) knevel beschikbaar op het gebruikersinterface van de Configuratie hebt toegelaten:

* Als de **auto-goedkeuring** knevel wordt toegelaten, zijn de activa die u gebruikend Content Hub uploadt automatisch beschikbaar.

* Als de **auto-goedkeuring** knevel gehandicapt is, tonen de activa die u gebruikend Content Hub uploadt niet automatisch. De middelen zijn beschikbaar in de map `hydrated-assets` van uw Assets as a Cloud Service-omgeving. Navigeer aan de omslag en [ bulkgeef ](/help/assets/approve-assets-content-hub.md) het statuut van die activa `Approved` voor die activa uit om in Content Hub te tonen.

## Hoe kunt u snel middelen zoeken die met Content Hub zijn geüpload naar een AEM as a Cloud Service-omgeving? {#find-uploaded-assets-on-aem-cloud}

Middelen die met Content Hub zijn geüpload in een AEM as a Cloud Service-omgeving, kunt u snel vinden op:

1. Navigeer naar de map `hydrated-assets` .

1. Klik op **[!UICONTROL Filters]** en stel **[!UICONTROL No Status]** in het veld **[!UICONTROL Asset Status]** in.

1. Elementen sorteren met het veld **[!UICONTROL Modified Date]** .

## Waarom zie ik de optie Bewerken met Adobe Express op mijn assetkaart niet om elementen opnieuw te mixen om nieuwe variaties te maken? {#edit-using-express-not-available}

Om **te bekijken geef het gebruiken van Adobe Express** optie op de activakaart uit, moet de gebruiker de Onderneming van Adobe Express of de rechten van Teams (zie [ plannen ](https://www.adobe.com/express/pricing)) naast voorrechten voor [ Content Hub gebruikers met rechten hebben om activa aan nieuwe variaties ](#onboard-content-hub-users-add-assets) opnieuw te mengen.

Er zijn een paar configuraties van hoe gebruikers worden toegewezen aan [!DNL Content Hub] &amp; [!DNL Adobe Express] :

1. De organisatie heeft [ Assets Ultimate ](/help/assets/assets-ultimate-overview.md) of [ Assets Prime ](/help/assets/assets-prime.md) vergunning, en de gebruiker wordt toegewezen aan één van de profielen van Experience Manager in Admin console die de rechten van Adobe Express (Medewerker of de gebruiker van de Macht) omvatten. De integratie werkt zonder enige extra configuratie.

1. [!DNL Adobe Express] wordt geïmplementeerd in dezelfde [!DNL Adobe Admin Console] als [!DNL Experience Manager Assets] met [!DNL Content Hub] . De integratie werkt zonder enige extra configuratie.

1. [!DNL Adobe Express] wordt geïmplementeerd in een andere [!DNL Adobe Admin Console] dan [!DNL Experience Manager Assets] met [!DNL Content Hub] . In dit geval, kan de [!DNL Assets] beheerder de integratie (zie [ documentatie ](/help/assets/connect-assets-with-creative-cloud.md)) voor de integratie vormen om te werken.

   >[!NOTE]
   >
   >De gebruiker die aan Uitdrukkelijke en Assets productprofielen in twee Consoles Admin wordt toegewezen moet het zelfde e-mailadres hebben en een bedrijfs **rekening van de Onderneming of van de School gebruiken**, en niet **Persoonlijke**. De ideale configuratie moet zowel Consoles Admin opstelling als **Federated ID** met vertrouwensverhouding opstelling tussen hen hebben, zodat de gebruiker een naadloze enige sign-on ervaring heeft. Sommige Express-plannen (bijvoorbeeld Express Teams) bieden geen ondersteuning voor Federated ID/Single Sign-On.

Naast de juiste productrechten vereist de integratie van Adobe Express in Content Hub dat de toegewezen gebruiker minstens [!UICONTROL Can Edit] toestemmingen op de het auteursmilieu van Assets die Content Hub aandrijft, op minstens de **[!UICONTROL # /content/dam/hydrated-assets/]** omslaghiërarchie heeft, waar de gebruikers van Content Hub inhoud kunnen bewaren die zij gebruikend Druk creeerden. Zie [ het Beheer van Toestemmingen ](/help/security/touch-ui-principal-view.md) in de mening Admin (Aanraak UI) of een vereenvoudigd [ toestemmingenbeheer in de mening van Assets ](https://experienceleague.adobe.com/nl/docs/experience-manager-assets-essentials/help/get-started-admins/folder-access/manage-permissions).

## Kan ik Content Hub zo instellen dat de merkrichtlijnen van mijn organisatie als een link op de homepage worden weergegeven? {#content-hub-setup-brand-guidelines}

U kunt aangepaste koppelingen als afzonderlijke tabbladen toevoegen, naast de standaardtabbladen Alle Assets, Verzamelingen en Inzichten op de startpagina van Content Hub. Voor informatie over hoe te om het te plaatsen, zie [ de Verbindingen van de Douane ](/help/assets/configure-content-hub-ui-options.md#configure-custom-links-content-hub).

## Bestaat er een plan voor het migreren van bestaande Brand Portal-klanten naar Content Hub? {#migration-brand-portal}

Adobe biedt migratiesupport van Brand Portal naar Content Hub die u kunt gebruiken door een Adobe-ondersteuningsticket te maken.

## Waarom kan ik de optie Productinstellingen/Configuratie in Content Hub niet zien? {#ui-configuration-option-missing}

Om tot het [ Gebruikersinterface van de Configuratie ](/help/assets/configure-content-hub-ui-options.md) toegang te hebben, moet u a [ Beheerder van Content Hub ](/help/assets/deploy-content-hub.md##onboard-content-hub-administrator) zijn. Als u aan het het productprofiel van de Beheerders van AEM op de productie auteurinstantie in Adobe Admin Console wordt toegewezen en u nog niet de configuratieoptie ziet, zorg ervoor dat het de productprofiel van de Beheerders van AEM niet anders wordt genoemd. Zie [ het Team van AEM as a Cloud Service en de Profielen van het Product ](/help/onboarding/aem-cs-team-product-profiles.md) voor meer details.
