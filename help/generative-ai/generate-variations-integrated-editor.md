---
title: Variaties genereren
description: Meer informatie over Variaties genereren, toegankelijk via verschillende editors in AEM as a Cloud Service
feature: Generate Variations, AI Tools
role: Admin, Developer, User
exl-id: d380ddd6-43f9-4bbf-8167-a6a472b9fc01
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1418'
ht-degree: 1%

---

# Variaties genereren - Geïntegreerd in AEM Editors {#generate-variations-integrated-in-aem-editors}

Als u op zoek bent naar een manier om uw digitale kanalen te optimaliseren en het maken van inhoud te versnellen, kunt u de functie Variaties genereren gebruiken die zijn geïntegreerd in de AEM-editors.

Bij het genereren van variaties wordt gebruikgemaakt van generatieve kunstmatige intelligentie (AI) om inhoudvariaties te maken op basis van uw invoer. Na het creëren van variaties, kunt u de inhoud op uw website gebruiken, en ook hun succes meten gebruikend de [&#x200B; 1&rbrace; functionaliteit van de Experimentatie &lbrace;van &#x200B;](https://www.aem.live/docs/experimentation) Edge Delivery Services [.](/help/edge/overview.md)

Dit helpt de snelheid van de inhoud te versnellen door binnen enkele minuten snel inhoud op het merk te maken. Hierdoor wordt de conversie met nieuwe kopieervarianten verbeterd.

U kunt [&#x200B; toegang tot Variaties &#x200B;](#access-generate-variations) van de volgende redacteurs produceren ([&#x200B; zodra zij &#x200B;](#access-generate-variations)) zijn gevormd:

* [in de Sidekick van AEM Edge Delivery Services; voor op documenten gebaseerde ontwerpen](#access-aem-sidekick)
* [in de Universal Editor](#access-aem-universal-editor)
* [in de Inhoudsfragmenteditor](#access-aem-content-fragment-editor)

>[!IMPORTANT]
>
>Deze pagina gebruikt op documenten gebaseerde authoring als basis voor voorbeelden, maar de beginselen zijn van toepassing op de andere editors.

>[!NOTE]
>
>In alle gevallen, om te gebruiken produceert Variaties u moet ervoor zorgen dat de [&#x200B; toegangseerste vereisten &#x200B;](#access-prerequisites) worden vervuld.

>[!NOTE]
>
>Het wordt geadviseerd dat u deze versie gebruikt, aangezien hoewel de standalone versie van [&#x200B; Variaties nog kan direct worden betreden &#x200B;](/help/generative-ai/generate-variations.md), het in de toekomst zal worden afgekeurd.

U kunt dan:

* [&#x200B; selecteer de inhoud u met &#x200B;](#select-the-content) wilt werken - van bestaande blokken van uw inhoud
   * Het geselecteerde blok bepaalt wat wordt weergegeven en de beschikbare acties
* [Beschrijf de gewenste wijzigingen](#describe-the-changes-you-want)
* [&#x200B; produceer variaties van uw inhoud &#x200B;](#generate-copy), dan [&#x200B; neem verdere acties indien gewenst &#x200B;](#take-further-action-on-a-variation)
* [Een variatie selecteren en gebruiken](#use-a-generated-variation)
* Herzie uw [&#x200B; geschiedenis &#x200B;](#history)
* Bekijk uw [&#x200B; favorieten &#x200B;](#favorites)

## Opmerking bij wet en gebruik {#legal-usage-note}

<!--
Generative AI and Generate Variations for AEM are powerful tools – but **you** are responsible for use of the output.

Your inputs to the service should be tied to a context. This context can be your branding materials, website content, data, schemas for such data, templates, or other trusted documents.

You must evaluate the accuracy of any output as appropriate to your use case.

Before using Generate Variations you are recommended to read the [Adobe Experience Cloud Generative AI User Guidelines](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html).
-->

[&#x200B; Gebruik van produceerde Variaties &#x200B;](#generative-action-usage) is gebonden aan de consumptie van generatieve acties.

>[!NOTE]
>
>Zie het [&#x200B; Werkblad van het Fact van de Veiligheid voor details met betrekking tot het produceren van Variatie in AEM &#x200B;](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/aem-sites-generate-variations-security-fact-sheet.pdf).

## Overzicht {#overview}

Wanneer u Genereren-variaties opent die zijn geïntegreerd in een editor, ziet u de extensie als een zwevend deelvenster met drie tabbladen.

![&#x200B; produceer Variaties - document gebaseerd auteursoverzicht &#x200B;](assets/generate-variations-doc-based-overview.png)

* De editor:
   * Dit toont de inhoudsstroom in de redacteur.
   * Hier kunt u een blok van inhoud voor gebruik in **selecteren produceert variaties**.
* **produceer variaties**:
   * Is een zwevend deelvenster met drie tabbladen die u naar wens kunt verplaatsen
   * [&#x200B; produceer &#x200B;](#get-started-with-generate-variations):
      * Toont de [&#x200B; inhoud u &#x200B;](#select-the-content) hebt geselecteerd.
      * Verstrekt steekproef **Suggesties** voor veranderingen.
      * Staat u toe om [&#x200B; te beschrijven de veranderingen u &#x200B;](#describe-the-changes-you-want) wilt.
      * Staat u toe om [&#x200B; &#x200B;](#generate-copy) nieuwe variaties te produceren.
      * Geeft de gegenereerde variaties weer. <!--, together with their [brand score](#the-brand-score).-->
      * [&#x200B; neem verdere acties op een variatie &#x200B;](#take-further-action-on-a-variation).
      * [&#x200B; Gebruik een geproduceerde variatie &#x200B;](#use-a-generated-variation).
   * [&#x200B; Geschiedenis &#x200B;](#history):
      * Toont je recente geschiedenis van generaties.
   * [&#x200B; Favorieten &#x200B;](#favorites):
      * Geeft resultaten van vorige generaties weer die u als Favorieten hebt gemarkeerd.
   * **Adobe Generative AI termijnen**: Verbindingen met [&#x200B; Generatieve AI de Richtlijnen van de Gebruiker van Adobe Experience Cloud &#x200B;](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html).

## Aan de slag met het genereren van variaties {#get-started-with-generate-variations}

De interface begeleidt u door het proces om inhoud te produceren. Na het openen van de interface, is de eerste stap het blok van inhoud te selecteren u wilt gebruiken.

### Selecteer de inhoud {#select-the-content}

Selecteer in de hoofdinhoudsstroom van de editor de inhoud waarvoor u variaties wilt genereren. Deze **Selectie** zal in **worden getoond produceert** tabel.

### Beschrijf de gewenste wijzigingen {#describe-the-changes-you-want}

Om variaties van de inhoud te produceren moet u de veranderingen beschrijven u wilt. U kunt of één van de **Gerichte Suggesties** selecteren, of uw eigen beschrijving verstrekken.

U kunt **Modifiers** ook specificeren om meer context te verstrekken:

* **Verwijzing een Web-pagina**
Geef een URL op voor meer context.
* **uploadt inhoudssamenvatting**
Werk een `.docx` -bestand bij met gegevens over de inhoudsopgave (10 MB of minder).

### Kopie genereren {#generate-copy}

Nadat u de veranderingen hebt beschreven u wilt, uitgezochte **&#x200B;**&#x200B;produceren om reacties van generatieve AI te zien.

![&#x200B; produceer Variaties - gebaseerd document produceert exemplaar &#x200B;](assets/generate-variations-doc-based-generate-copy.png)

<!--
### The Brand Score {#the-brand-score}

The brand score shows you how on-brand the generated variation is.
-->

### Verdere actie ondernemen met betrekking tot een wijziging {#take-further-action-on-a-variation}

Wanneer u één variatie selecteert, kunt u de volgende acties gebruiken:

* **geeft** uit
   * U kunt de tekst van de gegenereerde variatie bewerken.

      * U kunt een voorvertoning van uw updates weergeven op de webpagina.

   * Sla uw wijzigingen op voor later gebruik.
* **Favoriet**
   * Vul deze variatie aan voor toekomstig gebruik.
   * Zodra gemarkeerd, zal het onder [&#x200B; Favorieten &#x200B;](#favorites) tabel worden getoond.
* **AI Rationale**
   * Voor extra transparantie geeft dit een korte beschrijving van waarom generatieve AI die specifieke variatie heeft gegenereerd.

### Een gegenereerde variatie gebruiken {#use-a-generated-variation}

Om de inhoud te gebruiken die met generatieve AI wordt geproduceerd, moet u eerst selecteren en **Uitvoer naar CSV**.

Na het exporteren kunt u de inhoud elders gebruiken, bijvoorbeeld wanneer u inhoud voor uw website ontwerpt. U kunt ook een [&#x200B; experiment &#x200B;](https://www.aem.live/docs/experimentation) in werking stellen.

>[!NOTE]
>
>Wanneer Generate de Variaties van of [&#x200B; wordt betreden de Universele Redacteur van AEM &#x200B;](#access-aem-universal-editor) of [&#x200B; de Redacteur van het Fragment van de Inhoud van AEM &#x200B;](#access-aem-content-fragment-editor), dan wordt de geselecteerde geproduceerde inhoud automatisch bewaard aan AEM.

## Historie {#history}

Dit lusje toont uw vroegere activiteit zoals nadat u **selecteert produceert**. De ingang van de a **Geschiedenis** wordt toegevoegd.

Als, op een recentere punt, u de zelfde inhoud in de belangrijkste stroom selecteert en het **lusje van de Geschiedenis** opent, dan ziet u alle geproduceerde variaties voor dat blok.

## Favorieten {#favorites}

Nadat u de inhoud hebt bekeken, kunt u geselecteerde variaties opslaan als favorieten.

Zodra bewaard worden zij getoond onder **Favorieten**. De favorieten worden voortgeduurd (tot u **Unfavoriet** hen, of ontruim het browser geheime voorgeheugen).

* U kunt **uitgeven** **of** AI Rationale **voor een ingang tonen.**
* Zodra een variatie wordt geselecteerd, kunt u ook **Uitvoer naar CSV**.

## Generatief actieverbruik {#generative-action-usage}

Gebruiksbeheer is afhankelijk van de actie die wordt uitgevoerd:

* Variaties genereren

  Eén generatie van een kopieervariant is gelijk aan één generatieve actie. Als klant hebt u een aantal generatieve acties die bij uw AEM-licentie worden geleverd. Zodra de basisrechten zijn verbruikt, kunt u extra handelingen aanschaffen.

  >[!NOTE]
  >
  >Zie [&#x200B; Adobe Experience Manager: Cloud Service | Productbeschrijving &#x200B;](https://helpx.adobe.com/legal/product-descriptions/aem-cloud-service.html) voor meer informatie over basisrechten en neem contact op met uw accountteam als u meer generatieve acties wilt aanschaffen.

## Toegang genereert variaties {#access-generate-variations}

Nadat u aan de voorwaarden hebt voldaan, hebt u toegang tot Variaties genereren vanuit AEM as a Cloud Service of de Sidekick van de Edge Delivery Services.

### Toegangsvoorwaarden {#access-prerequisites}

Als u Variaties genereren wilt gebruiken, moet u ervoor zorgen dat aan de voorwaarden is voldaan:

* [Toegang tot Experience Manager as a Cloud Service met Edge Delivery Services](#access-to-aemaacs-with-edge-delivery-services)

#### Toegang tot Experience Manager as a Cloud Service met Edge Delivery Services{#access-to-aemaacs-with-edge-delivery-services}

Gebruikers die toegang nodig hebben om variaties te genereren, moeten recht hebben op een Experience Manager as a Cloud Service-omgeving met Edge Delivery Services.

>[!NOTE]
>
>Als uw contract voor AEM Sites as a Cloud Service Edge Delivery Services niet bevat, moet u een nieuw contract ondertekenen om toegang te krijgen.
>
>Neem contact op met uw accountteam om te bespreken hoe u met Edge Delivery Services naar AEM Sites as a Cloud Service kunt gaan.

Als u toegang wilt verlenen aan specifieke gebruikers, wijst u hun gebruikersaccount toe aan het desbetreffende productprofiel. Zie [&#x200B; Toewijzend de Profielen van het Product van AEM voor verdere details &#x200B;](/help/journey-onboarding/assign-profiles-cloud-manager.md).

### Toegang vanuit de AEM Sidekick voor op documenten gebaseerd ontwerpen {#access-aem-sidekick}

De toegang van AEM Sidekick wordt gebruikt voor [&#x200B; document gebaseerd creatie &#x200B;](https://www.aem.live/docs/aem-authoring).

Er is enige configuratie nodig voordat u toegang krijgt tot Variaties genereren via de Sidekick (van Edge Delivery Services).

>[!NOTE]
>
>Zie het document [&#x200B; Installerend AEM Sidekick &#x200B;](https://www.aem.live/docs/sidekick-extension) voor hoe te om Sidekick te installeren en te vormen.

Als u de functie Variaties genereren in de Sidekick (van Edge Delivery Services) wilt gebruiken, neemt u de volgende configuraties op in uw Edge Delivery Services-projecten.

1. Uw app inschakelen in:

   * `tools/sidekick/config.json`

   Dit moet in uw bestaande configuratie worden samengevoegd en dan opgesteld.

   Bijvoorbeeld:

   ```prompt
   {
     "plugins": [
       {
         "id": "aem-genai-variations",
         "titleI18n": {
           "en": "Generate with AI"
         },
         "environments": [
           "preview"
         ],
         "includePaths": [
           "**.docx**"
         ],
         "event": "aem-genai-variations-sidekick"
       }
     ]
   }
   ```

1. Maken:

   * `/tools/sidekick/aem-genai-variations.js`

   U moet dit bestand maken met de volgende inhoud:

   ```prompt
   (function () {
     let isAEMGenAIVariationsAppLoaded = false;
     function loadAEMGenAIVariationsApp() {
       const script = document.createElement('script');
       script.src = 'https://experience.adobe.com/solutions/aem-sites-genai-aem-genai-variations-mfe/static-assets/resources/sidekick/client.js?source=plugin';
       script.onload = function () {
         isAEMGenAIVariationsAppLoaded = true;
       };
       script.onerror = function () {
         console.error('Error loading AEMGenAIVariationsApp.');
       };
       document.head.appendChild(script);
     }
   
     function handlePluginButtonClick() {
       if (!isAEMGenAIVariationsAppLoaded) {
         loadAEMGenAIVariationsApp();
       }
     }
   
     // The code snippet for the Sidekick V1 extension, https://chromewebstore.google.com/detail/aem-sidekick/ccfggkjabjahcjoljmgmklhpaccedipo?hl=en
     const sidekick = document.querySelector('helix-sidekick');
     if (sidekick) {
       // sidekick already loaded
       sidekick.addEventListener('custom:aem-genai-variations-sidekick', handlePluginButtonClick);
     } else {
       // wait for sidekick to be loaded
       document.addEventListener('sidekick-ready', () => {
         document.querySelector('helix-sidekick')
           .addEventListener('custom:aem-genai-variations-sidekick', handlePluginButtonClick);
       }, { once: true });
     }
   
     // The code snippet for the Sidekick V2 extension, https://chromewebstore.google.com/detail/aem-sidekick/igkmdomcgoebiipaifhmpfjhbjccggml?hl=en
     const sidekickV2 = document.querySelector('aem-sidekick');
     if (sidekickV2) {
       // sidekick already loaded
       sidekickV2.addEventListener('custom:aem-genai-variations-sidekick', handlePluginButtonClick);
     } else {
       // wait for sidekick to be loaded
       document.addEventListener('sidekick-ready', () => {
         document.querySelector('aem-sidekick')
           .addEventListener('custom:aem-genai-variations-sidekick', handlePluginButtonClick);
       }, { once: true });
     }
   }());
   ```

1. Bijwerken:

   * `/scripts/scripts.js`

   Dit moet worden bijgewerkt om de volgende verklaring in de `loadLazy()` functie te omvatten:

   ```prompt
     import('../tools/sidekick/aem-genai-variations.js');
   ```

   Hierdoor wordt `/tools/sidekick/aem-genai-variations.js` geladen als onderdeel van het lazy laadproces.

   ![&#x200B; produceer Variaties - luie loader &#x200B;](assets/generate-variations-sidekick-lazyloader.png)

1. U kunt dan moeten ervoor zorgen dat de gebruikers [&#x200B; Toegang tot Experience Manager as a Cloud Service met Edge Delivery Services &#x200B;](#access-to-aemaacs-with-edge-delivery-services) hebben.

1. U kunt tot de eigenschap dan toegang hebben, door **te selecteren met AI** van de toolbar van Sidekick produceert:

   ![&#x200B; produceer Variaties - toegang van AEM Sidekicj &#x200B;](assets/generate-variations-doc-based-sidekick.png)

### Toegang tot de AEM Universal Editor {#access-aem-universal-editor}

De toegang van de [&#x200B; Universele Redacteur van AEM &#x200B;](/help/sites-cloud/authoring/universal-editor/authoring.md) wordt uitgevoerd als uitbreiding.

* Voor details op hoe te om tot toegang te hebben produceren Variaties van de Universele Redacteur, gelieve het document [&#x200B; Authoring Inhoud met de Universele Redacteur te zien.](/help/sites-cloud/authoring/universal-editor/authoring.md#generate-variations)
* Voor details op hoe te om de uitbreiding toe te laten, te zien gelieve het document [&#x200B; Extension Manager in AEM Experience Manager.](https://developer.adobe.com/uix/docs/extension-manager/)

### Toegang vanuit de AEM Content Fragment Editor {#access-aem-content-fragment-editor}

De toegang van de [&#x200B; Redacteur van het Fragment van de Inhoud van AEM &#x200B;](/help/sites-cloud/administering/content-fragments/authoring.md#generate-variations-ai) wordt uitgevoerd als uitbreiding. Zie [&#x200B; Extension Manager in AEM Experience Manager &#x200B;](https://developer.adobe.com/uix/docs/extension-manager/) voor verdere details.

## Aanvullende informatie {#further-information}

Voor meer informatie kunt u ook lezen:

* [&#x200B; GenAI produceert Variaties op GitHub &#x200B;](https://github.com/adobe/aem-genai-assistant#setting-up-aem-genai-assistant)
* [&#x200B; de Experimentatie van Edge Delivery Services &#x200B;](https://www.aem.live/docs/experimentation)
* [&#x200B; Generatieve AI in de producten van Experience Cloud &#x200B;](https://experienceleague.adobe.com/en/docs/core-services/interface/features/generative-ai)

   * [&#x200B; Generatieve AI in de producten van Experience Cloud - Adobe Experience Manager &#x200B;](https://experienceleague.adobe.com/en/docs/core-services/interface/features/generative-ai#aem)

* [&#x200B; produceer Variaties die pagina op Experience Cloud &#x200B;](https://experience.adobe.com/solutions/aem-sites-genai-aem-genai-variations-mfe/static-assets/resources/ga.html) landen

* [Generatieve AI in AEM as a Cloud Service](/help/ai-in-aem/overview.md#generative-ai-in-aem)

## Releasegeschiedenis {#release-history}

Voor details van huidige, en vorige, versies zien de [&#x200B; Nota&#39;s van de Versie voor produceer Variaties &#x200B;](/help/generative-ai/release-notes-generate-variations.md)
