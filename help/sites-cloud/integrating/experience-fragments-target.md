---
title: Exporteren van ervaringsfragmenten naar Adobe Target
description: Leer hoe u uw Experience Fragments naar Adobe Target exporteert, om ervaringen te testen en te personaliseren.
exl-id: 752d91f9-13a6-40c2-9425-7d18dafe9205
solution: Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '2184'
ht-degree: 0%

---

# Exporteren van ervaringsfragmenten naar Adobe Target{#exporting-experience-fragments-to-adobe-target}

>[!CAUTION]
>
>* De fragmenten AEM Ervaring worden geëxporteerd naar de standaardwerkruimte van Adobe Target.
>* AEM moet met Adobe Target volgens de instructies onder [ worden geïntegreerd die met Adobe Target ](/help/sites-cloud/integrating/integrating-adobe-target.md) integreren.

U kunt [ Fragmenten van de Ervaring ](/help/sites-cloud/authoring/fragments/content-fragments.md) uitvoeren, die in Adobe Experience Manager as a Cloud Service (AEM), aan Adobe Target (Doel) worden gecreeerd. Zij kunnen dan als aanbiedingen in de activiteiten van het Doel worden gebruikt, om ervaringen op schaal te testen en te personaliseren.

Er zijn drie opties beschikbaar voor het exporteren van een Experience-fragment naar Adobe Target:

* HTML (standaard): ondersteuning voor web en hybride inhoud
* JSON: ondersteuning voor levering van inhoud zonder kop
* HTML en JSON

Als u uw exemplaar wilt voorbereiden voor het exporteren van AEM Experience Fragments naar Adobe Target, moet u:

* [Integreren met Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md)
* [Cloudconfiguratie toevoegen](#add-the-cloud-configuration)
* [De verouderde configuratie toevoegen](#add-the-legacy-configuration)

Daarna kunt u:

* [Een ervaringsfragment exporteren naar Adobe Target](#exporting-an-experience-fragment-to-adobe-target)
* [Je ervaringsfragmenten in Adobe Target gebruiken](#using-your-experience-fragments-in-adobe-target)
* En ook [ schrap een Fragment van de Ervaring reeds die naar Adobe Target ](#deleting-an-experience-fragment-already-exported-to-adobe-target) wordt uitgevoerd

U kunt Experience Fragments exporteren naar de standaardwerkruimte in Adobe Target of naar door de gebruiker gedefinieerde werkruimten voor Adobe Target.

>[!NOTE]
>
>De Adobe Target-werkruimten bestaan niet in Adobe Target zelf. Deze worden gedefinieerd en beheerd in Adobe IMS (Identity Management System) en vervolgens geselecteerd voor gebruik in verschillende oplossingen met Adobe Developer Console.

>[!NOTE]
>
>De werkruimten van Adobe Target kunnen worden gebruikt om leden van een organisatie (groep) toe te staan om aanbiedingen en activiteiten voor deze organisatie slechts tot stand te brengen en te beheren; zonder toegang tot andere gebruikers te verlenen. Bijvoorbeeld landspecifieke organisaties binnen een wereldwijd bereik.

>[!NOTE]
>
>Raadpleeg de volgende secties voor meer informatie:
>
>* [ de ontwikkeling van Adobe Target ](https://developers.adobetarget.com/)
>* [ Componenten van de Kern - de Fragmenten van de Ervaring ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=nl-NL)
>* [ Adobe Target - hoe gebruik ik de Fragmenten van de de Ervaring van Adobe Experience Manager (AEM)?](https://experienceleague.adobe.com/docs/target/using/experiences/offers/aem-experience-fragments.html?lang=nl-NL)
>* [ AEM 6.5 - Vormend manueel de Integratie met Adobe Target - Creërend een Configuratie van de Wolk van het Doel ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/target-configuring.html?lang=nl-NL#creating-a-target-cloud-configuration)

## Vereisten {#prerequisites}

Er zijn verschillende acties vereist:

1. U moet [ AEM met Adobe Target ](/help/sites-cloud/integrating/integrating-adobe-target.md) integreren.

1. De Fragmenten van de ervaring worden uitgevoerd van de AEM auteurinstantie, zodat moet u [ AEM Verbinding uiterlijk vormen ](/help/implementing/developing/extending/experience-fragments.md#configuring-the-aem-link-externalizer) op de auteursinstantie om ervoor te zorgen dat om het even welke verwijzingen binnen het Fragment van de Ervaring voor Weblevering worden geexternaliseerd.

   >[!NOTE]
   >
   >Voor verbinding die niet door het gebrek herschrijft, is de [ Verstrekker van de Verbinding van het Fragment van de Ervaring Rewriter ](/help/implementing/developing/extending/experience-fragments.md#the-experience-fragment-link-rewriter-provider-html) beschikbaar. Met dit, kunnen de aangepaste regels voor uw geval worden ontwikkeld.

## Cloudconfiguratie toevoegen {#add-the-cloud-configuration}

Alvorens een fragment uit te voeren moet u de **Configuratie van de Wolk** voor **Adobe Target** aan het fragment, of de omslag toevoegen. Hierdoor kunt u ook:

* de indelingsoptie(s) opgeven die voor de export moet worden gebruikt
* een doelwerkruimte selecteren als doel
* selecteer een extern domein om verwijzingen in het Fragment van de Ervaring te herschrijven (facultatief)

De vereiste opties kunnen in **Eigenschappen van de Pagina** van de vereiste omslag, of fragment, of allebei worden geselecteerd; de specificatie wordt zonodig geërft.

1. Navigeer aan de **console van de Fragmenten van de Ervaring**.

1. Open **Eigenschappen van de Pagina** voor de aangewezen omslag of het fragment.

   >[!NOTE]
   >
   >Als u de wolkenconfiguratie aan de ouderomslag van het Fragment van de Ervaring toevoegt, wordt de configuratie geërft door alle kinderen.
   >
   >Als u de wolkenconfiguratie aan het Fragment van de Ervaring zelf toevoegt, wordt de configuratie geërft door alle variaties.

1. Selecteer de **Cloud Servicen** tabel.

1. Onder **Configuratie van de Cloud Service**, uitgezochte **Adobe Target** van de drop-down lijst.

   >[!NOTE]
   >
   >De JSON-indeling van een Experience Fragment-aanbieding kan worden aangepast. Hiervoor definieert u een component van het fragment van de klantenervaring en annoteert u hoe u de eigenschappen van de component in het Sling-model kunt exporteren.
   >
   >Zie de kerncomponent: [ Componenten van de Kern - de Fragmenten van de Ervaring ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/experience-fragment.html?lang=nl-NL)

1. Onder **Adobe Target** uitgezocht:

   * de juiste configuratie
   * de optie voor de vereiste indeling
   * een Adobe Target-werkruimte
   * indien nodig - het externalizer domein

   >[!CAUTION]
   >
   >Het externalizer-domein is optioneel.
   >
   > Een AEM externalizer wordt gevormd wanneer u de uitgevoerde inhoud aan specifiek *wilt richten publiceert* domein. Voor meer details zie [ Vormend de AEM Verbinding Externalzer ](/help/implementing/developing/extending/experience-fragments.md#configuring-the-aem-link-externalizer).
   >
   > Houd er ook rekening mee dat Externe domeinen alleen relevant zijn voor de inhoud van het ervaringsfragment dat naar Doel wordt verzonden, en niet voor metagegevens zoals Inhoud weergaveaanbod.

   Bijvoorbeeld voor een map:

   ![ Omslag - Cloud Servicen ](assets/xf-target-integration-01.png " Omslag - Cloud Servicen ")

1. **sparen &amp; sluit**.

## De verouderde configuratie toevoegen {#add-the-legacy-configuration}

<!-- This is effectively the Manually Integrating with Adobe Target {#manually-integrating-with-adobe-target} section from 6.5 -->

>[!IMPORTANT]
>
>Het toevoegen van een nieuwe configuratie van de Oudheid is een speciaal casescenario dat slechts voor de uitvoer van de Fragmenten van de Ervaring wordt gesteund.

Na [ toevoegend de Configuratie van de Wolk ](#add-the-cloud-configuration) om Launch by Adobe te gebruiken, om AEM met Adobe Target aanvankelijk te integreren, moet u ook manueel met Adobe Target integreren gebruikend een erfenisconfiguratie.

### Een doelcloud-configuratie maken {#creating-a-target-cloud-configuration}

Om AEM in staat te stellen om met Adobe Target in wisselwerking te staan, creeer een de wolkenconfiguratie van het Doel. Als u de configuratie wilt maken, geeft u de Adobe Target-clientcode en gebruikersgegevens op.

U kunt de configuratie van de wolk van het Doel slechts eenmaal tot stand brengen omdat u de configuratie met veelvoudige AEM campagnes kunt associëren. Als u meerdere Adobe Target-clientcodes hebt, maakt u één configuratie voor elke clientcode.

U kunt de wolkenconfiguratie vormen om segmenten van Adobe Target te synchroniseren. Als u synchronisatie inschakelt, worden segmenten op de achtergrond geïmporteerd van Target zodra de cloudconfiguratie is opgeslagen.

Gebruik de volgende procedure om een de wolkenconfiguratie van het Doel in AEM tot stand te brengen:

1. Navigeer aan **Verouderde Cloud Servicen** via het **AEM embleem** > **Hulpmiddelen** > **Cloud Servicen** > **Verouderde Cloud Servicen**.
Bijvoorbeeld: ([ http://localhost:4502/libs/cq/core/content/tools/cloudservices.html ](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html))

   De **Adobe Experience Cloud** overzichtspagina opent.

1. In de **Adobe Target** sectie, klik **nu** vormen.
1. In **creeer de dialoog van de Configuratie**:

   1. Geef de configuratie a **Titel**.
   1. Selecteer het **malplaatje van de Configuratie van 0&rbrace; Adobe Target.**
   1. Klik **creëren**.

U kunt nu de nieuwe configuratie selecteren om te bewerken.

1. Het dialoogvenster Bewerken wordt geopend.

   ![ config-doel-montages-dialoog ](assets/config-target-settings-dialog.png)

   <!-- Can this still occur?

   >[!NOTE]
   >
   >When configuring A4T with AEM, you may see a Configuration reference missing entry. To be able to select the analytics framework, do the following:
   >
   >1. Navigate to **Tools** &gt; **General** &gt; **CRXDE Lite**.
   >1. Navigate to **/libs/cq/analytics/components/testandtargetpage/dialog/items/tabs/items/tab1_general/items/a4tAnalyticsConfig**
   >1. Set the property **disable** to **false**.
   >1. Select **Save All**.

   -->

1. In het **de dialoogvakje van de Montages van Adobe Target**, verstrek waarden voor deze eigenschappen.

   * **Authentificatie**: dit gebrek aan IMS (de Referentie van de Gebruiker wordt afgekeurd)

   * **Code van de Cliënt**: De code van de de rekeningscliënt van het Doel

   * **identiteitskaart van de HTENT**: HULPVERLENER identiteitskaart

   * **IMS Configuratie**: selecteer de vereiste configuratie van de drop-down lijst

   * **API Type**: gebreken aan REST (XML wordt afgekeurd)

   * **A4T de Configuratie van Analytics Cloud**: Selecteer de de wolkenconfiguratie van Analytics die voor de doelstellingen en metriek van de doelactiviteit wordt gebruikt. Dit is nodig als u Adobe Analytics als rapportagebron gebruikt wanneer u inhoud als doel instelt.

     <!-- Is this needed?
     If you do not see your cloud configuration, see note in [Configuring A4T Analytics Cloud Configuration](#configuring-a-t-analytics-cloud-configuration).
     -->

   * **het nauwkeurige richten van het Gebruik:** Door gebrek wordt dit controlevakje geselecteerd. Als deze optie is geselecteerd, wacht de configuratie van de cloudservice tot de context is geladen voordat inhoud wordt geladen. Zie het volgende.

   * **synchroniseer Segmenten van Adobe Target:** selecteer deze optie om segmenten te downloaden die in Doel worden bepaald om hen in AEM te gebruiken. Selecteer deze optie als de eigenschap API Type REST is, omdat inline-segmenten niet worden ondersteund en u altijd segmenten van Target moet gebruiken. (De AEM term &#39;segment&#39; komt overeen met de doelterm &#39;publiek&#39;.)

   * **bibliotheek van de Cliënt:** dit gebrek aan AT.js (mbox.js wordt afgekeurd)

     >[!NOTE]
     >
     >Het dossier van de Bibliotheek van het Doel, [ AT.JS ](https://experienceleague.adobe.com/docs/target-dev/developer/client-side/at-js-implementation/at-js/how-atjs-works.html?lang=nl-NL), is een nieuwe implementatiebibliotheek voor Adobe Target die voor zowel typische Webimplementaties als enig-paginatoepassingen wordt ontworpen.
     >
     >mbox.js is afgekeurd en wordt in een later stadium verwijderd.
     >
     >De Adobe adviseert dat u AT.js in plaats van mbox.js als cliëntbibliotheek gebruikt.
     >
     >AT.js biedt verschillende verbeteringen aan ten opzichte van de bibliotheek mbox.js:
     >
     >* Verbeterde laadtijden voor webimplementaties
     >* Verbeterde beveiliging
     >* Betere implementatieopties voor toepassingen van één pagina
     >* AT.js bevat de componenten die in target.js inbegrepen waren, zodat is er niet meer een vraag aan target.js
     >
     >U kunt AT.js of mbox.js in het **de bibliotheek van de Cliënt** drop-down menu selecteren.

   * **het Systeem van Tag Management van het Gebruik om cliëntbibliotheek** te leveren - selecteer deze optie om de cliëntbibliotheek van de Lancering van de Adobe of een ander systeem van het markeringsbeheer (of DTM, die wordt afgekeurd) te gebruiken.

   * **Douane AT.js**: Blader om uw douane AT.js te uploaden. Leeg laten om de standaardbibliotheek te gebruiken.

     >[!NOTE]
     >
     >Wanneer u zich aanmeldt bij de Adobe Target-configuratietovenaar, wordt Accurate gericht inschakelen.
     >
     >Nauwkeurige het richten betekent dat de de dienstconfiguratie van de wolk op de context wacht te laden alvorens inhoud te laden. Hierdoor kan het, in termen van prestaties, nauwkeuriger richten tot een paar milliseconde vertraging leiden alvorens inhoud te laden.
     >
     >Nauwkeurige het richten wordt altijd toegelaten op de auteursinstantie. Nochtans, op publiceer instantie kunt u verkiezen om nauwkeurige gericht uit te zetten globaal door het vinkje naast Accurate het richten in de configuratie van de wolkendienst (**http://localhost:4502/etc/cloudservices.html**) te ontruimen. U kunt nauwkeurige het richten voor individuele componenten ook nog uitzetten ongeacht uw plaatsen in de configuratie van de wolkendienst.
     >
     >Als u ***reeds*** gecreeerd gerichte componenten hebt en u dit het plaatsen verandert, beïnvloeden uw veranderingen niet die componenten. U moet om het even welke veranderingen in die component direct aanbrengen.

1. Klik **verbinden met Adobe Target** om de verbinding met Doel te initialiseren. Als de verbinding succesvol is, wordt het bericht **succesvolle Verbinding** getoond. Klik **O.K.** op het bericht en dan **O.K.** op de dialoog.

### Een doelframework toevoegen {#adding-a-target-framework}

<!-- Is this section needed? -->

Nadat u de de wolkenconfiguratie van het Doel vormt, voeg een kader van het Doel toe. Het kader identificeert de standaardparameters die naar Adobe Target van de beschikbare [&#128279;](/help/implementing/developing/personalization/configuring-contexthub.md) componenten ContextHub worden verzonden. Het doel gebruikt de parameters om de segmenten te bepalen die op de huidige context van toepassing zijn.

U kunt veelvoudige kaders voor één enkele configuratie van het Doel creëren. Meerdere frameworks zijn handig wanneer u een andere set parameters naar Doel moet sturen voor verschillende gedeelten van uw website. Maak een framework voor elke set parameters die u wilt verzenden. Koppel elk gedeelte van uw website aan het juiste framework. Opmerking t*dat een webpagina slechts één framework tegelijk kan gebruiken.

1. Voor uw de configuratiepagina van het Doel, klik **+** (plusteken) naast Beschikbare Configuraties.

1. In de Create dialoog van het Kader, specificeer a **Titel**, selecteer het **Kader van Adobe Target**, en klik **creeer**.

   <!-- ![config-target-framework-dialog](assets/config-target-framework-dialog.png) -->

   De pagina Framework wordt geopend. Sidekick verstrekt componenten die informatie van [ ContextHub ](/help/implementing/developing/personalization/configuring-contexthub.md) vertegenwoordigen die u kunt in kaart brengen.

   <!-- ![Framework](assets/chlimage_1-162.png) -->

1. Sleep de component van de Context van de Cliënt die de gegevens vertegenwoordigt die u voor afbeelding aan het dalingsdoel wilt gebruiken. Alternatief, sleep de **component van de Winkel 0&rbrace; ContextHub aan het kader.**

   >[!NOTE]
   >
   >Bij toewijzing worden parameters via eenvoudige tekenreeksen aan een box doorgegeven. U kunt geen series van ContextHub in kaart brengen.

   Bijvoorbeeld, om **Gegevens van het Profiel** over uw plaatsbezoekers te gebruiken om uw campagne van het Doel te controleren, sleep de **component van de Gegevens van het Profiel** aan de pagina. De variabelen van profielgegevens die voor afbeelding aan de parameters van het Doel beschikbaar zijn verschijnen.

   <!-- ![Profile Data](assets/chlimage_1-163.png) -->

1. Selecteer de variabelen die u zichtbaar aan het systeem van Adobe Target wilt maken door het **aandeel** checkbox in de aangewezen kolommen te selecteren.

   <!-- ![Share](assets/chlimage_1-164.png) -->

   >[!NOTE]
   >
   >Het synchroniseren van parameters is slechts één manier - van AEM naar Adobe Target.

Uw framework is gemaakt. Om het kader aan te herhalen publiceer instantie, gebruik **activeer Kader** optie van sidekick.

<!--
### Associating Activities With the Target Cloud Configuration  {#associating-activities-with-the-target-cloud-configuration}

Associate your [AEM activities](/help/sites-cloud/authoring/personalization/activities.md) with your Target cloud configuration so that you can mirror the activities in [Adobe Target](https://experienceleague.adobe.com/docs/target/using/experiences/offers/manage-content.html?lang=nl-NL).

>[!NOTE]
>
>What types of activities are available is determined by the following:
>
>* If the **xt_only** option is enabled on the Adobe Target tenant (clientcode) used on the AEM side to connect to Adobe Target, then you can create **only** XT activities in AEM.
>
>* If the **xt_only** options is **not** enabled on the Adobe Target tenant (clientcode), then you can create **both** XT and A/B activities in AEM.
>
>**Additional note:** **xt_only** options is a setting applied on a certain Target tenant (clientcode) and can only be modified directly in Adobe Target. You cannot enable or disable this option in AEM.
-->

<!--
### Associating the Target Framework With Your Site {#associating-the-target-framework-with-your-site}

After you create a Target framework in AEM, associate your web pages with the framework. The targeted components on the pages send the framework-defined data to Adobe Target for tracking. (See [Content Targeting](/help/sites-cloud/authoring/personalization/targeted-content.md).)

When you associate a page with the framework, the child pages inherit the association.

1. In the **Sites** console, navigate to the site that you want to configure.
1. Using either [quick actions](/help/sites-cloud/authoring/basic-handling.md#quick-actions) or [selection mode](/help/sites-cloud/authoring/basic-handling.md#selecting-resources), select **View Properties.**
1. Select the **Cloud Services** tab.
1. Select **Edit**.
1. Select **Add Configuration** under **Cloud Service Configurations** and select **Adobe Target**.

  ![Cloud Service Configuration](assets/chlimage_1-165.png)

1. Select the framework you want under **Configuration Reference**.

   >[!NOTE]
   >
   >Make sure that you select the specific **framework** that you created and not the Target cloud configuration under which it was created.

1. Select **Done**.
1. Activate the root page of the website to replicate it to the publish server. (See [How To Publish Pages](/help/sites-cloud/authoring/sites-console/publishing-pages.md).)

   >[!NOTE]
   >
   >If the framework you attached to the page was not activated yet, a wizard opens which lets you publish it as well.
-->

## Een ervaringsfragment exporteren naar Adobe Target {#exporting-an-experience-fragment-to-adobe-target}

>[!CAUTION]
>
>Voor media-elementen, zoals afbeeldingen, wordt alleen een verwijzing naar Doel geëxporteerd. Het element zelf blijft opgeslagen in AEM Assets en wordt geleverd via de AEM-publicatie-instantie.
>
>Daarom moet het ervaringsfragment met alle gerelateerde elementen worden gepubliceerd voordat u het exporteert naar Target.

Een ervaringsfragment exporteren van AEM naar doel (na het opgeven van de cloudconfiguratie):

1. Navigeer naar de Experience Fragment-console.
1. Selecteer het ervaringsfragment dat u naar doel wilt exporteren.

   >[!NOTE]
   >
   >Het moet een variant van het Web van het Fragment van de Ervaring zijn.

1. Selecteer **Uitvoer aan Adobe Target**.

   >[!NOTE]
   >
   >Als het Fragment van de Ervaring reeds is uitgevoerd, uitgezochte **Update in Adobe Target**.

1. Selecteer **Uitvoer zonder het publiceren** of **Publish** zoals vereist.

   >[!NOTE]
   >
   >Het selecteren van **Publish** zal het ervaringsfragment onmiddellijk publiceren en het verzenden naar Doel.

1. Selecteer **O.K.** in de bevestigingsdialoog.

   Het ervaringsfragment moet nu in Doel staan.

   >[!NOTE]
   >
   >[ de Diverse details ](/help/sites-cloud/authoring/fragments/content-fragments.md#details-of-your-experience-fragment) van de uitvoer kunnen in **Mening van de Lijst** van de console en **Eigenschappen** worden gezien.

   >[!NOTE]
   >
   >Wanneer het bekijken van een Fragment van de Ervaring in Adobe Target, is de *laatst gewijzigde* datum die wordt gezien de datum dat het fragment het laatst in AEM werd gewijzigd, niet de datum dat het fragment het laatst werd uitgevoerd naar Adobe Target.

>[!NOTE]
>
>Alternatief, kunt u de uitvoer van de paginaredacteur uitvoeren, gebruikend vergelijkbare bevelen in het [ menu van de Informatie van de Pagina ](/help/sites-cloud/authoring/page-editor/introduction.md#page-information).

## Uw ervaringsfragmenten in Adobe Target gebruiken {#using-your-experience-fragments-in-adobe-target}

Na het uitvoeren van de voorafgaande taken, toont het ervaringsfragment op de pagina van Aanbiedingen in Doel. Zie [ specifieke documentatie van het Doel ](https://experiencecloud.adobe.com/resources/help/en_US/target/target/aem-experience-fragments.html) om over te leren wat u daar kunt bereiken.

>[!NOTE]
>
>Wanneer het bekijken van een Fragment van de Ervaring in Adobe Target, is de *laatst gewijzigde* datum die wordt gezien de datum dat het fragment het laatst in AEM werd gewijzigd, niet de datum dat het fragment het laatst werd uitgevoerd naar Adobe Target.

## Een ervaringsfragment verwijderen dat al naar Adobe Target is geëxporteerd {#deleting-an-experience-fragment-already-exported-to-adobe-target}

Als u een ervaringsfragment verwijdert dat al naar Target is geëxporteerd, kan dit problemen veroorzaken als het fragment al in een aanbieding in Target wordt gebruikt. Als u het fragment verwijdert, wordt de aanbieding onbruikbaar omdat de fragmentinhoud door AEM wordt geleverd.

Om dergelijke situaties te voorkomen:

* Als het ervaringsfragment momenteel niet wordt gebruikt in een activiteit, AEM kan de gebruiker het fragment zonder een waarschuwingsbericht verwijderen.
* Als het ervaringsfragment momenteel door een activiteit in Doel wordt gebruikt, wordt de AEM gebruiker een foutbericht gegeven over de mogelijke gevolgen die het verwijderen van het fragment voor de activiteit zal hebben.

  Het foutbericht in AEM belet de gebruiker niet (geforceerd) het ervaringsfragment te verwijderen. Als het ervaringsfragment wordt verwijderd:

   * De aanbieding van het Doel met AEM Fragment van de Ervaring kan ongewenste gedrag tonen

      * Het aanbod wordt waarschijnlijk nog steeds weergegeven, aangezien de HTML van het ervaringsfragment naar Target is geduwd
      * Eventuele verwijzingen in het ervaringsfragment werken mogelijk niet correct als middelen waarnaar wordt verwezen ook in AEM worden verwijderd.

   * Uiteraard zijn verdere wijzigingen van het ervaringsfragment niet mogelijk omdat het ervaringsfragment niet meer in AEM bestaat.
