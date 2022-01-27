---
title: Exporteren van ervaringsfragmenten naar Adobe Target
description: Exporteren van ervaringsfragmenten naar Adobe Target
source-git-commit: 4b83fdbe4c0c260a609734b3c460ce884f0c8c9e
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 0%

---

# Exporteren van ervaringsfragmenten naar Adobe Target{#exporting-experience-fragments-to-adobe-target}

>[!CAUTION]
>
>* De fragmenten AEM Experience worden geëxporteerd naar de standaardwerkruimte van Adobe Target.
>* AEM moet in Adobe Target worden geïntegreerd volgens de instructies in [Integreren met Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md).


U kunt exporteren [Ervaar fragmenten](/help/sites-cloud/authoring/fundamentals/experience-fragments.md), gemaakt in Adobe Experience Manager as a Cloud Service (AEM), naar Adobe Target (Target). Zij kunnen dan als aanbiedingen in de activiteiten van het Doel worden gebruikt, om ervaringen op schaal te testen en te personaliseren.

Er zijn drie formaatopties beschikbaar voor het uitvoeren van een Fragment van de Ervaring naar Adobe Target:

* HTML (standaard): Ondersteuning voor weergave van webinhoud en hybride inhoud
* JSON: Ondersteuning voor levering van inhoud zonder kop
* HTML en JSON

Na [Integreren met Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md) AEM Experience Fragments kunnen worden geëxporteerd naar de standaardwerkruimte in Adobe Target of naar door de gebruiker gedefinieerde werkruimten voor Adobe Target.

>[!NOTE]
>
>De Adobe Target-werkruimten bestaan niet in Adobe Target zelf. Ze worden gedefinieerd en beheerd in Adobe IMS (Identity Management System) en vervolgens geselecteerd voor gebruik in verschillende oplossingen met behulp van Adobe I/O-integratie.

>[!NOTE]
>
>De werkruimten van Adobe Target kunnen worden gebruikt om leden van een organisatie (groep) toe te staan om aanbiedingen en activiteiten voor slechts deze organisatie tot stand te brengen en te beheren; zonder andere gebruikers toegang te geven. Bijvoorbeeld landspecifieke organisaties binnen een wereldwijd bereik.

>[!NOTE]
>
>Zie ook voor meer informatie:
>
>* [Adobe Target-ontwikkeling](https://www.adobe.io/apis/experiencecloud/target.html)
>* [Kernonderdelen - Ervaar fragmenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)
>* [Adobe Target - Hoe gebruik ik Adobe Experience Manager (AEM)-fragmenten?](https://experienceleague.adobe.com/docs/target/using/experiences/offers/aem-experience-fragments.html?lang=en)


## Vereisten {#prerequisites}


Er zijn verschillende acties vereist:

1. U moet [AEM integreren met Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md).
2. De Fragmenten van de ervaring worden uitgevoerd van de AEM auteurinstantie zodat moet u [Vorm AEM Verbinding Externalzer](/help/implementing/developing/extending/experience-fragments.md#configuring-the-aem-link-externalizer) op de auteurinstantie om ervoor te zorgen dat om het even welke verwijzingen binnen het Fragment van de Ervaring voor Weblevering worden geexternaliseerd.

   >[!NOTE]
   >
   >Voor het herschrijven van koppelingen die niet door de standaardwaarde worden gedekt, wordt de [Experience Fragment Link Rewriter Provider](/help/implementing/developing/extending/experience-fragments.md#the-experience-fragment-link-rewriter-provider-html) is beschikbaar. Met dit, kunnen de aangepaste regels voor uw geval worden ontwikkeld.

## Cloudconfiguratie toevoegen {#add-the-cloud-configuration}

Voordat u een fragment exporteert, moet u de opdracht **Cloud Configuration** for **Adobe Target** naar het fragment of de map. Hierdoor kunt u ook:

* de indelingsoptie(s) opgeven die voor de export moet worden gebruikt
* een doelwerkruimte selecteren als doel
* selecteer een extern domein om verwijzingen in het Fragment van de Ervaring te herschrijven (facultatief)

U kunt de vereiste opties selecteren in **Pagina-eigenschappen** van de vereiste map en/of het vereiste fragment; het productdossier zal zo nodig worden geërfd .

1. Ga naar de **Ervaar fragmenten** console.

1. Openen **Pagina-eigenschappen** voor de juiste map of het juiste fragment.

   >[!NOTE]
   >
   >Als u de wolkenconfiguratie aan de ouderomslag van het Fragment van de Ervaring toevoegt, wordt de configuratie geërft door alle kinderen.
   >
   >
   >Als u de wolkenconfiguratie aan het Fragment van de Ervaring zelf toevoegt, wordt de configuratie geërft door alle variaties.

1. Selecteer **Cloud Services** tab.

1. Onder **Configuratie Cloud Service**, selecteert u **Adobe Target** in de vervolgkeuzelijst.

   >[!NOTE]
   >
   >De JSON-indeling van een Experience Fragment-aanbieding kan worden aangepast. Hiervoor definieert u een component van het fragment van de klantenervaring en annoteert u hoe u de eigenschappen van de component in het Sling-model van de component exporteert.
   >
   >Zie de kerncomponent:
   >
   >[Kernonderdelen - Ervaar fragmenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/experience-fragment.html)

   Onder **Adobe Target** selecteren:

   * de juiste configuratie
   * de optie voor de vereiste indeling
   * een Adobe Target-werkruimte
   * indien vereist - het externalizer-domein

   >[!CAUTION]
   >
   >Het externalizer-domein is optioneel.
   >
   > Er is een AEM-externalizer geconfigureerd wanneer u wilt dat de geëxporteerde inhoud naar een specifieke map verwijst *publish* domein. Zie voor meer informatie [Het vormen van de Verbinding Externalzer van de AEM](/help/implementing/developing/extending/experience-fragments.md#configuring-the-aem-link-externalizer).
   >
   > Houd er ook rekening mee dat Externe domeinen alleen relevant zijn voor de inhoud van het ervaringsfragment dat naar Doel wordt verzonden, en niet voor metagegevens zoals Inhoud weergaveaanbod.

<!--
   For example, for a folder:

   ![Folder - Cloud Services](assets/xf-target-integration-01.png "Folder - Cloud Services")
-->

1. **Opslaan en sluiten**.

## Een ervaringsfragment exporteren naar Adobe Target {#exporting-an-experience-fragment-to-adobe-target}

>[!CAUTION]
>
>Voor media-elementen, zoals afbeeldingen, wordt alleen een verwijzing naar Doel geëxporteerd. Het element zelf blijft opgeslagen in AEM Assets en wordt geleverd via de AEM-publicatie-instantie.
>
>Daarom moet het ervaringsfragment, met alle gerelateerde elementen, worden gepubliceerd voordat het naar Target kan worden geëxporteerd.

Een ervaringsfragment exporteren van AEM naar doel (na het opgeven van de cloudconfiguratie):

1. Navigeer naar de Experience Fragment-console.
1. Selecteer het ervaringsfragment dat u naar doel wilt exporteren.

   >[!NOTE]
   >
   >Het moet een variant van het Web van het Fragment van de Ervaring zijn.

1. Tikken/klikken **Exporteren naar Adobe Target**.

   >[!NOTE]
   >
   >Als het ervaringsfragment al is geëxporteerd, selecteert u **Bijwerken in Adobe Target**.

1. Tikken/klikken **Exporteren zonder publiceren** of **Publiceren** zoals vereist.

   >[!NOTE]
   >
   >Selecteren **Publiceren** publiceert het ervaringsfragment meteen en verzendt het naar Target.

1. Tikken/klikken **OK** in het bevestigingsdialoogvenster.

   Het ervaringsfragment moet nu in Doel staan.

   >[!NOTE]
   >
   >[Diverse details](/help/sites-cloud/authoring/fundamentals/experience-fragments.md#details-of-your-experience-fragment) van de uitvoer **Lijstweergave** van de console en **Eigenschappen**.

   >[!NOTE]
   >
   >Als u een Experience Fragment weergeeft in Adobe Target, kunt u *laatst gewijzigd* De datum die wordt weergegeven, is de datum waarop het fragment voor het laatst is gewijzigd in AEM, niet de datum waarop het fragment voor het laatst is geëxporteerd naar Adobe Target.

>[!NOTE]
>
>U kunt het exporteren ook vanuit de paginaeditor uitvoeren met behulp van vergelijkbare opdrachten in het dialoogvenster [Pagina-informatie](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) -menu.

## Uw ervaringsfragmenten in Adobe Target gebruiken {#using-your-experience-fragments-in-adobe-target}

Na het uitvoeren van de voorafgaande taken, toont het ervaringsfragment op de pagina van Aanbiedingen in Doel. Kijk eens naar de [specifieke doeldocumentatie](https://experiencecloud.adobe.com/resources/help/en_US/target/target/aem-experience-fragments.html) om te leren wat je daar kunt bereiken.

>[!NOTE]
>
>Als u een Experience Fragment weergeeft in Adobe Target, kunt u *laatst gewijzigd* De datum die wordt weergegeven, is de datum waarop het fragment voor het laatst is gewijzigd in AEM, niet de datum waarop het fragment voor het laatst is geëxporteerd naar Adobe Target.

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
