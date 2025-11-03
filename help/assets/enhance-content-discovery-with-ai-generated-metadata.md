---
title: Verbeter de detectie van inhoud met door AI gegenereerde metagegevens in de beheerweergave
description: Leer hoe u de detectie van inhoud kunt verbeteren met metagegevens die door AI zijn gegenereerd in de beheerweergave
feature: Smart Tags,Tagging
role: Admin,User
source-git-commit: d73ca2317d594b0d98bb9765796870cc28aa1158
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 0%

---


# Detectie van inhoud verbeteren met door AI gegenereerde metagegevens {#ai-smart-tags}

In plaats van handmatig in te voeren, wijst AI automatisch beschrijvende tags toe aan digitale elementen. Deze door AI gegenereerde tags verbeteren de kwaliteit van de metagegevens, waardoor de elementen gemakkelijker kunnen worden doorzocht, gecategoriseerd en aanbevolen. Deze aanpak verbetert niet alleen de efficiëntie door handmatige codering te elimineren, maar zorgt ook voor consistentie en schaalbaarheid op grote volumes digitale inhoud. Als het element bijvoorbeeld een afbeelding is, kan AI objecten, scènes, emoties of zelfs merklogo&#39;s in het element herkennen en relevante tags genereren, zoals &quot;zonsondergang&quot;, &quot;strand&quot;, &quot;vakantie&quot; of &quot;glimlachen&quot;. Door AI gegenereerde inhoud kan het zoeken naar elementen verbeteren door gebruik te maken van zowel semantische als lexicale zoektechnieken. Zie meer [ Onderzoek Assets ](search-assets.md). <!--If the asset is a document, AI reads and interprets the text to assign meaningful keywords that summarize its content—such as "climate change," "policy," or "renewable energy.-->

![ Verbeterde slimme markeringen ](assets/enhanced-smart-tags1.png)

## Hoe kan ik door AI gegenereerde metagegevens inschakelen? {#enable-ai-generated-metadata}

Door AI gegenereerde metagegevens inschakelen:

* Minimaal vereiste AEM-releaseversie is `20626` .

* U moet een GenAI Rider-overeenkomst ondertekenen. Neem voor meer informatie contact op met uw Adobe-vertegenwoordiger.

## Door AI gegenereerde titels configureren {#configure-ai-generated-titles}

Met AEM kunt u de weergave van elementtitels configureren in de Kaart- of lijstweergave op de pagina Bladeren door middel van middelen. U kunt ervoor kiezen om de door u gedefinieerde elementtitel weer te geven, de titel die met AI is gegenereerd, of alleen een door AI gegenereerde titel te gebruiken als er geen bestaande titel voor het element bestaat.

Door AI gegenereerde titels configureren:

1. Navigeer naar **[!UICONTROL Tools > Assets > Assets Configuration > Smart Tag Enhancement Configuration]** .

1. Selecteer een van de volgende opties:

   * **Titel van gelijkstroom van de Vertoning (Gebrek)**: Specificeer de titel op het **[!UICONTROL Title]** gebied beschikbaar in activa eigenschappen om het in de mening van de Kaart of mening van de Lijst te tonen. Als de titel van het element niet is gedefinieerd, geeft AEM Assets de bestandsnaam weer.

   * **AI-Gegenereerde Titel van de Vertoning**: Toont de AI-Gegenereerde titel en negeert de titel die in activa eigenschappen wordt gespecificeerd. Als door AI gegenereerde titel niet beschikbaar is voor een element, geeft AEM Assets de standaardtitel van het element weer die beschikbaar is in de eigenschappen ervan.

   * **AI-Gegenereerde Titel van de Vertoning slechts als Titel van gelijkstroom niet** bestaat: AEM Assets toont de AI-Gegenereerde titel slechts als de activatitel niet voor activa wordt bepaald.

     ![ vorm AI-Gegenereerde titels ](assets/configure-title-ai-generated.png)

## Door AI gegenereerde metagegevens gebruiken {#using-ai-generated-smart-tags}

<!--[!NOTE]
>
>The enhanced smart tags capability is available only for the newly uploaded assets.
-->

Voer de volgende stappen uit om de verbeterde functie Slimme tags te gebruiken:

1. Ga in de interface [!DNL Experience Manager] naar de gewenste map en klik op **[!UICONTROL Add Assets]** . <!--Alternatively, to update enhanced smart tags in an existing content, click **[!UICONTROL reprocess]**.--> De compatibele indelingen voor afbeeldingsbestanden zijn `png` , `jpg` , `jpeg` , `psd` , `tiff` , `gif` , `webp` , `crw` , `cr2` , `3fr` , `nef` , `arw` en `bmp` .

1. Wacht tot het net geüploade element is verwerkt. Ga vervolgens naar de eigenschappen van de elementen.

1. Ga naar tabblad **[!UICONTROL AI-Generated]** . Als de [!DNL Experience Manager] -versie incompatibel is of niet wordt bijgewerkt, is dit tabblad niet zichtbaar. De volgende velden zijn beschikbaar:

   * **[!UICONTROL Generated title]:** de titel verstrekt een duidelijke en beknopte titel die het kernidee van een geüploade activa vangt, die het gemakkelijk maken in een blik te begrijpen. Als u een element toevoegt en u een titel opgeeft (in `dc:title` ), wordt deze weergegeven in de bladerweergave met elementen. Als deze optie leeg blijft, wordt automatisch een door AI gegenereerde titel toegewezen.
   * **[!UICONTROL Generated description]:** De beschrijving geeft een korte maar informatieve samenvatting van wat de activa over is, die gebruikers en onderzoeksmodule helpen om zijn relevantie snel te begrijpen.
   * **[!UICONTROL Generated keywords]:** De trefwoorden zijn doeltermen die de hoofdthema&#39;s van een element vertegenwoordigen en die u helpen bij het labelen en filteren van inhoud.

1. [ Facultatief ] u kunt extra markeringen toevoegen of uw creëren als u om het even welke relevante markeringen voelt ontbreken. U doet dit door uw tags in het veld **[!UICONTROL Generated keywords]** te schrijven en op **[!UICONTROL Save]** te klikken.

## Door AI gegenereerde metagegevens uitschakelen {#disable-ai-generated-metadata}

U kunt door AI gegenereerde metagegevens op mapniveau uitschakelen. Alle onderliggende mappen overerven de eigenschappen van de bovenliggende map.

Door AI gegenereerde metagegevens op mapniveau uitschakelen:

1. Navigeer naar **[!UICONTROL Adobe Experience Manager > Assets > Files]** .

1. Selecteer de map en klik op **[!UICONTROL Properties]** .

1. Navigeer op het tabblad **[!UICONTROL Asset Processing]** naar de map **[!UICONTROL Smart Tags Enhancements for images]** . Selecteer een van de volgende waarden in de vervolgkeuzelijst:

   * Overgenomen - De map neemt de opties voor in- of uitschakelen over van de bovenliggende map.

   * Inschakelen - Door AI gegenereerde metagegevens worden ingeschakeld voor de geselecteerde map.

   * Uitschakelen - Door AI gegenereerde metagegevens voor de geselecteerde map worden uitgeschakeld.

     ![ maak AI-Gegenereerde meta-gegevens ](assets/disable-ai-generated-metadata.png) onbruikbaar