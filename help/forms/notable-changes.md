---
title: Wat is er veranderd tussen AEM 6.5 Forms en AEM Cloud Services
description: 'Bent u een Experience Manager Forms-gebruiker en wilt u een upgrade uitvoeren naar Adobe Experience Manager Forms as a Cloud Service? Leer de opvallendste wijzigingen voordat u gaat upgraden of migreren naar Cloud Service.  '
contentOwner: khsingh
exl-id: 46fcc1b4-8fd5-40e1-b0fc-d2bc9df3802e
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1211'
ht-degree: 2%

---

# Opmerkelijke wijzigingen voor bestaande Adobe Experience Manager Forms-gebruikers  {#notable-changes-for-existing-AEM-Forms-users}

Adobe Experience Manager Forms as a Cloud Service brengt enkele opmerkelijke wijzigingen aan in bestaande functies in vergelijking met Adobe Experience Manager FormsOn-Premise en [!DNL Adobe-Managed Service] omgevingen. De belangrijkste verschillen worden hieronder vermeld:

* De service biedt een lokale en een ontwikkelomgeving in de cloud. U kunt een [plaatselijke ontwikkelomgeving](setup-local-development-environment.md) om uw aangepaste code, componenten, sjablonen, thema&#39;s, Adaptive Forms en andere middelen te ontwikkelen en te testen voordat u deze middelen implementeert in een cloud-omgeving. Het helpt het ontwikkelingsproces te versnellen.
* [!DNL AEM] als Cloud Service wordt verzonden met een ingebouwde CDN. Het belangrijkste doel is het verminderen van latentie door content te leveren die in de cache kan worden opgeslagen en die komt van de CDN-knooppunten aan de rand van de omgeving, dicht in de buurt van de browser. Het systeem wordt volledig beheerd en geconfigureerd voor optimale prestaties van AEM-applicaties.
* Een cloud-native omgeving heeft geen webconsole (configuratiemanager). U kunt [[!DNL AEM Forms] as a Cloud Service SDK om configuraties te genereren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart) en CI/CD pijpleiding aan [stel de configuratie op](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) naar de instantie Cloud Service.

* De URL-conventie van gelokaliseerde adaptieve Forms ondersteunt nu het opgeven van een landinstelling in de URL. Met de nieuwe URL-conventie kunnen gelokaliseerde formulieren op een verzender of CDN in cache worden geplaatst. Gebruik in een Cloud Service-omgeving de URL-indeling `http://host:port/content/forms/af/<afName>.<locale>.html` een gelokaliseerde versie van een adaptief formulier aanvragen in plaats van `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`. Adobe raadt u aan Dispatcher of CDN in cache te plaatsen. Hiermee kunt u de rendersnelheid van voorgevulde formulieren verbeteren.
* Met de voorkeursservice worden gegevens samengevoegd met een adaptief formulier op een client. Hiermee kunt u de tijd verbeteren die nodig is om een adaptief formulier vooraf in te vullen. U kunt altijd configureren om de samenvoegactie uit te voeren op de Adobe Experience Manager FormsServer.
* E-mailondersteuning biedt standaard alleen HTTP- en HTTP-protocollen. [Contact opnemen met het ondersteuningsteam](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email) om havens voor het verzenden van e-mail toe te laten en SMTP protocol voor uw milieu toe te laten.
* Adobe Experience Manager Forms as a Cloud Service brengt vele nieuwe eigenschappen en mogelijkheden in uw AEMProjecten. Er zijn echter enkele wijzigingen vereist voor Adobe Experience Manager Maven-projecten om verenigbaar te zijn met AEM Cloud Service. Op hoog niveau vereist AEM een scheiding van inhoud en code in afzonderlijke subpakketten om de splitsing tussen muteerbare en onveranderlijke inhoud te respecteren. Gebruik de [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html) om bestaande projectpakketten te herstructureren door inhoud en code te scheiden in afzonderlijke pakketten, zodat deze compatibel zijn met de projectstructuur die voor Adobe Experience Manager as a Cloud Service is gedefinieerd.

<!--  If your Cloud Configuration contains a secret (password), create a separate Cloud Configuration for every Author instance (Developer, Stage, and Production). If a Cloud Configuration is also required on Publish instances, publish/replicate a separate Cloud Configuration for every Publish instance (Developer, Stage, and Production). 

* When you create a Cloud Configuration that contains a secret, each Cloud Service instance (Developer, Stage, and Production) uses its own encryption key to encrypt the password before storing it. So, manually create such Cloud Configuration for every Cloud Service instance (Developer, Stage, and Production). Also, do not store secrets used in a Cloud Configuration to your Cloud Manager Git repository.

* Use [!DNL Cloud Manager] [APIs to convert and provide your passwords as secrets](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#setting-values-via-api). Do not store plain text password or secrets on your environments. -->

* Gebruik van milieu-specifieke configuraties voor geheime OSGi configuratiewaarden, zoals wachtwoorden, privé API sleutels, of een andere waarden. Deze kunnen om veiligheidsredenen niet in Git worden opgeslagen. [Gebruik geheime milieu-specifieke configuraties om de waarde voor geheimen op alle milieu&#39;s van Adobe Experience Manager as a Cloud Service, met inbegrip van Stadium en Productie op te slaan](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#when-to-use-secret-environment-specific-configuration-values).

Voor een uitgebreide lijst met wijzigingen in Adobe Experience Manager as a Cloud Service raadpleegt u [Wat is nieuw en wat is anders](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html).

<!-- ## Feature comparison {#comparison}

[!DNL AEM Forms] as a Cloud Service and Experience Manager 6.5 Forms share a common set of features: Adaptive Forms, data integration, integration with [!DNL Adobe Sign], themes, templates, and forms management interface are identical. You can easily port your existing Adaptive Forms from an Experience Manager 6.5 Forms or an earlier version to [!DNL AEM Forms] as a Cloud Service.

### Features of AEM 6.5 Forms and [!DNL AEM Forms] as a Cloud Service {#feature-comparison}

The following table lists the major features of Experience Manager 6.5 Forms and provides information about whether the feature is partially or fully supported in [!DNL AEM Forms] as a Cloud Service, with a link to more information about the feature. The table also lists extra features available in [!DNL AEM Forms] as a Cloud Service.


| Feature/Capability | AEM 6.5 Forms | [!DNL AEM Forms] as a Cloud Service |
| - | - | - |
| Adaptive Forms | &#x2611; | &#x2611; |
| Data Integration | &#x2611; | &#x2611;(With some changes) |
| Automated Forms Conversion Service | &#x2611; | &#x2611; |
| Integration with Adobe Sign | &#x2611; | &#x2611;(With some changes) |
| Themes and Templates | &#x2611; | &#x2611; ([With some changes](themes.md#difference-in-themes))|
| Rule editor | &#x2611; | &#x2611; (With some changes) |
| Forms Portal | &#x2611; | --- |
| Integration with Adobe Analytics | &#x2611; | &#x2612; |
| Document Security | &#x2611; | &#x2612; | -->

<!-- ## New features {#comparison} -->



## Belangrijke verbeteringen {#whats-new}

<!-- [!DNL AEM Forms] as a Cloud Service offers benefits like auto-scaling, cost-effectiveness, zero downtime for upgrades, and cloud-native development environment and more. The list does not stop here. The following features are are start and are available only for [!DNL AEM Forms] as a Cloud Service: -->

De volgende functies en verbeteringen zijn alleen beschikbaar op [!DNL AEM Forms] as a Cloud Service:

**Uitgebreide editor voor Visual Rule**
De dienst verstrekt een gehard [Visuele regeleditor](rule-editor.md#visual-rule-editor). De dienst heeft volgende eigenschappen aan Visuele regelredacteur toegevoegd om u te helpen capabele regels schrijven:

* [Nieuwe verzendgebeurtenissen](working-with-adobe-sign.md#available-operator-types-and-events-in-rule-editor): `Navigation`, `Step Completion`, `Successful Submission`, en `Error`

* [Nieuw gegevenstype `scope`](rule-editor.md#custom-functions). U kunt de `scope` gegevenstype in een aangepaste functie om het volledige bereik van een formulier door te geven.

* Gebruiksmogelijkheden [@this om een JSDoc in een aangepaste functie op te geven](rule-editor.md#custom-functions). Hiermee kan een aangepaste functie worden aangeroepen door @this in een actieve component te gebruiken.

* Mogelijkheid om voorwaarden voor op eigenschap-gebaseerde regels toe te voegen.

**Kernonderdelen**
De [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=en) zijn een reeks gestandaardiseerde componenten van het Beheer van de Inhoud van het Web (WCM) voor AEM om ontwikkelingstijd te versnellen en onderhoudskosten te drukken. [!DNL AEM Forms] as a Cloud Service ondersteuning **[!UICONTROL AEM Forms Container]** Core Component. U kunt de component gebruiken om een adaptief formulier in te sluiten op een AEM Sites-pagina.

**AEM Archetype voor Forms as a Cloud Service**
[AEM Archetype](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-27) helpt u zich te ontwikkelen voor [!DNL AEM Forms] as a Cloud Service. U kunt Archetype versie 27 of later gebruiken om een projectmalplaatje tot stand te brengen compatibel met [!DNL AEM Forms] as a Cloud Service omgeving. Archetype bevat ook enkele voorbeeldthema&#39;s en sjablonen waarmee u snel aan de slag kunt gaan.

**Beveiligde en verbeterde informatiestroom tussen formulieren en ondertekenen**
[Aangepaste Forms- en Adobe Sign-integratie](working-with-adobe-sign.md) bij Cloud Service gelijktijdig gegevens en ondertekeningsactiviteiten aanbieden. Het maakt het verzenden van formulieren onafhankelijk van de ondertekeningsstatus en maakt een weg vrij voor snellere inzendingen. Bovenop slaat de service geen gegevens op over instanties van Cloud Servicen die het ondertekeningsproces superveilig maken.

**Best Practices Analyzer en migratie**
Analysator van beste praktijken verstrekt een beoordeling van uw huidige AEM implementatie. Het gereedschap uitvoeren voordat [migreren naar Forms as a Cloud Service](migrate-to-forms-as-a-cloud-service.md). Het evalueert bereidheid om van een bestaande plaatsing van Adobe Experience Manager (AEM) aan AEM as a Cloud Service over te stappen.

De dienst verstrekt ook [verbeterde migratieervaring](migrate-to-forms-as-a-cloud-service.md) om u te helpen gemakkelijk migreren van [!DNL AEM 6.4 Forms] en [!DNL AEM 6.5 Forms] tot [!DNL AEM Forms] as a Cloud Service.

**Snellere formulieruitvoeringen en snellere validaties aan de serverzijde**
De service maakt gebruik van CDN en Verzender in cache plaatsen om snellere uitvoeringen en servervalidaties voor Adaptive Forms te leveren.

**Verbeterde CAPTCHA**
U kunt nu [CAPTCHA valideren](captcha-adaptive-forms.md) ofwel via Aangepaste verzending van formulieren of op basis van een zakelijke logica. U kunt ook voorwaarden toevoegen om CAPTCHA te valideren bij een gebruikersactie en de component CAPTCHA weergeven of verbergen in een adaptief formulier op basis van regels.

De component CAPTCHA biedt een out-of-the-box integratie met Google reCAPTCHA. U kunt meer diensten CAPTCHA voor de component, indien nodig ook vormen.

**Meerdere master pagina&#39;s voor document van record**
U kunt nu een andere master pagina gebruiken voor elke pagina van een Document of Record en de plaatsing van een deelvenster Adaptief formulier op een Document of Record met pagineringsopties bepalen.

**Kolommen toevoegen aan tabellen zonder kop**
U kunt kolommen zonder kopteksten toevoegen en verwijderen aan tabellen. Verborgen kopteksten worden toegevoegd aan dergelijke lijsten helpen u kolommen toevoegen en schrappen. Deze kopteksten zijn zichtbaar tijdens het ontwerpen maar blijven verborgen in het gepubliceerde formulier. Tabellen zonder kopteksten zijn meestal te vinden in Adaptief Forms dat is gemaakt met de Automatede form conversion Service.

**Verbeterde verzendacties**
U kunt de [E-mail verzenden](configuring-submit-actions.md#send-email#send-email) Verzend Actie om een Document van Verslag (DoR) PDF als gehechtheid te verzenden.

**E-mailadres groeperen voor workflow**
U kunt ervoor kiezen [e-mailberichten verzenden](aem-forms-workflow-step-reference.md#assign-task-step) van de Assign stap van de Taak aan één enkele persoon of een groep.

**Verbeterde stap Formuliergegevensmodel aanroepen**
U kunt nu een mappad opgeven voor de optie Ten opzichte van Payload van argumenten voor invoerservices in een stap Formuliergegevensmodel aanroepen. Hiermee kunt u een bestand in de opgegeven map toewijzen aan het serviceargument zonder de exacte bestandsnaam op te geven.

**Verbeterde leesbaarheid van vertaalbestanden**
In Forms as a Cloud Service heeft de leesvolgorde van de velden en deelvensters van een adaptief formulier en berichtsleutels van de bijbehorende vertaalbestanden (.XLIFF-bestanden) een vergelijkbare structuur. Het helpt de snelheid van handmatige vertaling te verbeteren.

<!-- ## Feature comparison {#feature-comparison}

[!DNL AEM Forms] as a Cloud Service and [!DNL AEM 6.5 Forms] share some features like Adaptive Forms, Data Integration, and Forms Portal. You can easily port your existing Adaptive Forms from an [!DNL AEM 6.5 Forms] or an earlier version to [!DNL AEM Forms] as a Cloud Service.

### Features of [!DNL AEM 6.5 Forms] and [!DNL AEM Forms] as a Cloud Service {#aem-6.5-vs-aem-forms-as-a-cloud-service}

The following table lists the major features of [!DNL AEM 6.5 Forms] and provides information about the features coming soon to [!DNL AEM Forms] as a Cloud Service:

| Feature/Capability | AEM 6.5 Forms  | [!DNL AEM Forms] as a Cloud Service |
|---|---|---|
| Cloud-native architecture | &#x2612; | &#x2611;  |
| Auto-scaling based on load | &#x2612; | &#x2611;  |
| Zero downtime for upgrades | &#x2612; | &#x2611;  |
| Feature roll-out frequency | Quarterly | Agile*  |
| CDN (content delivery network) included | &#x2612; | &#x2611;  |
| Topologies optimized for maximum resilience and efficiency | &#x2612; | &#x2611;  |
| Cloud-native development environment | &#x2612; | &#x2611;  |
| Self-Service via Cloud Manager | &#x2612; | &#x2611;  |
| Automated upgrades with Continuous Integration and Continuous Delivery (CI/CD)| &#x2611; | &#x2611;  |
| Adaptive Forms | &#x2611; | &#x2611; |
| Data Integration | &#x2611; | &#x2611; |
| Automated Forms Conversion Service | &#x2611; | &#x2611; |
| Integration with [!DNL Adobe Sign] | &#x2611; | &#x2611; |
| Integration with [!DNL AEM Sites] | &#x2611; | &#x2611; |
| Enhanced Visual Rule editor | &#x2612; | &#x2611; |
| Forms Portal | &#x2611; | Coming Soon |
| Integration with [!DNL Adobe Analytics] | &#x2611; | Coming Soon |
| Integration with [!DNL Adobe Target] | &#x2611; | Coming Soon |
| Document Security | &#x2611; | &#x2612; |

`*` New features every month and bug fix updates on daily basis.

For a comprehensive list of changes in AEM as a Cloud Service, See [What is New and What is Different](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/overview/what-is-new-and-different.html) and [Notable changes in [!DNL AEM Forms] as a Cloud Service](notable-changes.md) -->
