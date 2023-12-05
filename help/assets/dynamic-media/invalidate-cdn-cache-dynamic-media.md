---
title: De cache van het Content Delivery Network ongeldig maken via Dynamic Media
description: Leer hoe u inhoud in de cache van uw CDN (Content Delivery Network) ongeldig maakt, zodat u snel elementen kunt bijwerken die door Dynamic Media worden geleverd, in plaats van te wachten tot de cache verloopt.
contentOwner: Rick Brough
feature: Asset Management
role: Admin,User
exl-id: c631079b-8082-4ff7-a122-dac1b20d8acd
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '1310'
ht-degree: 0%

---

# De CDN-cache ongeldig maken via Dynamic Media {#invalidating-cdn-cache-for-dm-assets-in-aem-cs}

Dynamic Media-elementen worden in cache geplaatst door de CDN (Content Delivery Network) voor snelle levering aan uw klanten. Wanneer u echter updates van deze elementen uitvoert, wilt u dat deze wijzigingen onmiddellijk op uw website van kracht worden. Door de CDN-cache te wissen of ongeldig te maken, kunt u snel elementen bijwerken die door Dynamic Media worden geleverd. U hoeft niet meer te wachten tot de cache verloopt met een TTL-waarde (Time To Live) (de standaardwaarde is tien uur). In plaats daarvan kunt u een aanvraag vanuit de Dynamic Media-gebruikersinterface verzenden om de cache binnen enkele minuten te laten verlopen.

>[!NOTE]
>
>Deze functie vereist dat u de CDN met Adobe-bundled gebruikt die bij Adobe Experience Manager Dynamic Media wordt geleverd. Een andere aangepaste CDN wordt niet ondersteund met deze functie.

<!-- REMOVED MARCH 28, 2022 BECAUSE OF 404; NO REDIRECT WAS PUT IN PLACE BY SUPPORT See also [Cache overview in Dynamic Media](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html). -->

Als u [Slimme afbeeldingen](/help/assets/dynamic-media/imaging-faq.md) op uw account en u gebruikt de Adobe-gebundelde CDN, kunt u alle URL&#39;s met verschillende querytekenreeksen leegmaken door de enige basis-URL op te schonen.

Bijvoorbeeld, ongeldig maken `https://weekendsite.scene7.com/is/image/<CUSTOMER-NAME>/image`maakt ook de volgende URL&#39;s ongeldig:

* `https://weekendsite.scene7.com/is/image/<CUSTOMER-NAME>/image`
* `https://weekendsite.scene7.com/is/image/<CUSTOMER-NAME>/image?wid=300`
* `https://weekendsite.scene7.com/is/image/<CUSTOMER-NAME>/image?$PLP$`
* enzovoort.

Deze ongeldigmaking is echter niet het geval voor algemene domeinen die geen ondersteuning bieden voor Smart Imaging, zoals `s7d1.scene7.com`. Dergelijke domeinen hebben nog steeds de volledige URL nodig om validatiewerkzaamheden met succes uit te voeren.

**De CDN-cache ongeldig maken via Dynamic Media:**

*Deel 1 van 2: Een CDN-validatiesjabloon maken*

1. Ga in Adobe Experience Manager as a Cloud Service naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL CDN Invalidation Template]**.

   ![Functie voor CDN-validatie](/help/assets/assets-dm/cdn-invalidation-template.png)

1. Op de **[!UICONTROL CDN Invalidation template]** op basis van uw scenario een van de volgende opties uitvoeren:

   | Scenario | Optie |
   | --- | --- |
   | Ik heb in het verleden al een CDN-validatiesjabloon gemaakt met Dynamic Media Classic. | De **[!UICONTROL Create Template]** Het tekstveld wordt vooraf gevuld met uw sjabloongegevens. In dat geval kunt u de sjabloon bewerken of doorgaan met de volgende stap. |
   | Ik moet een sjabloon maken. Wat ga ik binnen? | In de **[!UICONTROL Create Template]** tekstveld, voer een afbeeldings-URL (inclusief voorinstellingen of wijzigingstoetsen) in waarnaar wordt verwezen `<ID>`in plaats van een specifieke afbeelding-id zoals in het volgende voorbeeld:<br>`https://my.publishserver.com/is/image/company_name/<ID>?$product$`<br>Als de sjabloon net `<ID>`en vervolgens vult Dynamic Media in `https://<publishserver_name>/is/image/<company_name>/<ID>` waar `<publishserver_name>` is de naam van uw publicatieserver die is gedefinieerd in Algemene instellingen in Dynamic Media Classic. De `<company_name>` is de naam van uw bedrijfwortel verbonden aan deze instantie van Experience Manager, en `<ID>` de geselecteerde elementen via de elementkiezer worden ongeldig gemaakt.<br>Voorinstellingen/modifiers na `<ID>` worden naar behoren gekopieerd in de URL-definitie.<br>Alleen afbeeldingen, dat wil zeggen `/is/image`-kan automatisch worden gevormd op basis van de sjabloon.<br>Voor `/is/content/`Wanneer u elementen zoals video&#39;s of PDF toevoegt met de elementkiezer, worden er geen automatisch URL&#39;s gegenereerd. In plaats daarvan moet u deze elementen opgeven in de CDN-validatiesjabloon of kunt u de URL handmatig aan deze elementen toevoegen in *Deel 2 van 2: Opties voor CDN-validatie instellen*.<br>**Voorbeelden:**<br> In dit eerste voorbeeld bevat de validatiesjabloon `<ID>` samen met de URL van het element `/is/content`. Bijvoorbeeld: `http://my.publishserver.com:8080/is/content/dms7snapshot/<ID>`. Dynamic Media maakt de URL op basis van dit pad, met `<ID>` de elementen zijn die u hebt geselecteerd via de elementenkiezer die u ongeldig wilt maken.<br>In dit tweede voorbeeld bevat de validatiesjabloon de volledige URL van het element dat in uw westeigenschappen wordt gebruikt met `/is/content` (niet afhankelijk van de kiezer van het element). Bijvoorbeeld: `http://my.publishserver.com:8080/is/content/dms7snapshot/backpack` waarbij backpack de element-id is.<br>Elementformaten die in Dynamic Media worden ondersteund, komen in aanmerking voor ongeldigmaking. Elementbestandstypen die *niet* CDN-validatie wordt ondersteund door onder andere PostScript®, Encapsulated PostScript®, Adobe Illustrator, Adobe InDesign, Microsoft® Powerpoint, Microsoft® Excel, Microsoft® Word en Rich Text Format.<br><br>・ Wanneer u de sjabloon maakt, maar zorg dat u zorgvuldig de syntaxis en typos in acht neemt; Dynamic Media voert geen sjabloonvalidatie uit.<br>・ Met de CDN-validatiesjabloon kunt u maximaal 2500 tekens opslaan.<br>・ Geef URL&#39;s op voor slimme afbeeldingsgewassen in deze CDN-validatiesjabloon of in het dialoogvenster **[!UICONTROL Add URL]** tekstveld in *Deel 2: Opties voor CDN-validatie instellen.*<br>・ Elk item in een CDN-validatiesjabloon moet op een aparte regel staan.<br>・ Het volgende voorbeeld van de CDN-validatiesjabloon is alleen bedoeld voor demonstratiedoeleinden. |

   ![CDN-validatiesjabloon - maken](/help/assets/assets-dm/cdn-invalidation-template-create-2.png)

   >[!NOTE]
   >
   >Met de CDN-validatiesjabloon kunt u maximaal 2500 tekens opslaan.

1. In de rechterbovenhoek van het dialoogvenster **[!UICONTROL CDN Invalidation template]** pagina, selecteert u **[!UICONTROL Save]** selecteert u vervolgens **[!UICONTROL OK]**.<br>
   *Deel 2 van 2: Opties voor CDN-validatie instellen*
   <br>

1. Ga in as a Cloud Service Experience Manager naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL CDN Invalidation]**.

   ![Functie voor CDN-validatie](/help/assets/assets-dm/cdn-invalidation-path.png)

1. Op de **[!UICONTROL CDN Invalidation]** - **[!UICONTROL Add Details]** selecteert u de elementen voor CDN-validatie.

   ![CDN-validatie - Details toevoegen](/help/assets/assets-dm/cdn-invalidation-add-details-2.png)

   >[!NOTE]
   >
   >Als u besluit de opties te handhaven **[!UICONTROL Invalidate asset associated image presets in CDN]** *en* **[!UICONTROL Invalidate based on template]** Als deze optie is uitgeschakeld, wordt de basis-URL van de geselecteerde elementen samengesteld voor ongeldigmaking. Gebruik deze optie-indeling alleen voor afbeeldingen.


   | Optie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Invalidate asset associated image presets in CDN]** | (Optioneel) Wanneer u deze optie inschakelt, worden geselecteerde elementen en alle bijbehorende URL&#39;s met voorinstellingen voor afbeeldingen automatisch samengesteld voor cachevalidatie.<br>Elementen en de bijbehorende vooraf gedefinieerde URL&#39;s met voorinstellingen worden automatisch gevormd voor validatie. Deze optie werkt alleen voor afbeeldingselementen. |
   | **[!UICONTROL Invalidation based on template]** | (Optioneel) Schakel deze optie in als u alleen de gedefinieerde sjabloon voor URL-formatie wilt gebruiken. |
   | **[!UICONTROL Add Assets]** | Gebruik de elementkiezer om elementen te selecteren die u ongeldig wilt maken. U kunt gepubliceerde of niet-gepubliceerde elementen selecteren.<br>Het in cache plaatsen van de CDN is gebaseerd op URL en niet op elementen. Daarom is het noodzakelijk dat u op de hoogte bent van de volledige URL&#39;s die op uw website staan. Nadat u deze URL&#39;s hebt bepaald, kunt u ze aan de sjabloon toevoegen. Vervolgens kunt u deze elementen selecteren en toevoegen en de URL&#39;s in één stap ongeldig maken. <br>Deze optie gebruiken met **[!UICONTROL Invalidate asset associated image presets in CDN]**, of **[!UICONTROL Invalidation based on template]**, of beide. |
   | **[!UICONTROL Add URL]** | Voeg handmatig volledige URL-paden toe of plak deze naar Dynamic Media-elementen waarvan u de CDN-cache wilt ongeldig maken. Gebruik deze optie als u geen CDN-validatiesjabloon hebt gemaakt in ***Deel 1 van 2: Een CDN-validatiesjabloon maken*** en hebben slechts een paar elementen om ongeldig te maken.<br>**Belangrijk:** Elke URL die u toevoegt, moet op een eigen regel staan.<br>U kunt maximaal 1000 URL&#39;s op een bepaald moment ongeldig maken. Als het aantal URL&#39;s in het dialoogvenster **[!UICONTROL Add URL]** tekstveld is groter dan 1000, u kunt niet selecteren **[!UICONTROL Next]**. In dergelijke gevallen moet u **[!UICONTROL X]** rechts van een geselecteerd element of een handmatig toegevoegde URL om dit te verwijderen uit de lijst met validaties.<br>Geef URL&#39;s op voor slimme afbeeldingsgewassen in de CDN-validatiesjabloon of in deze **[!UICONTROL Add URL]** tekstveld. |

1. Selecteer rechtsboven in de pagina de optie **[!UICONTROL Next]**.
1. Op de **[!UICONTROL CDN Invalidation]** - **[!UICONTROL Confirm]** pagina, in de **[!UICONTROL URLs]** in de keuzelijst, ziet u een lijst met een of meer URL&#39;s die zijn gegenereerd op basis van de CDN-validatiesjabloon die u eerder hebt gemaakt en de elementen die u zojuist hebt toegevoegd.

   Als u bijvoorbeeld het voorbeeld voor de CDN-validatiesjabloon gebruikt dat eerder in de stappen werd weergegeven, kunt u een enkel element met de naam `spinset`. Wanneer u gaat naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL CDN Invalidation]** resulteert dit in de volgende vijf gegenereerde URL&#39;s in het dialoogvenster **[!UICONTROL CDN Invalidation - Confirm]** gebruikersinterface:

   ![CDN-validatie - Bevestigen](/help/assets/assets-dm/cdn-invalidation-confirm-2.png)

   Selecteer indien nodig **X** rechts van een URL om deze te verwijderen uit het validatieproces.

1. Selecteer rechtsboven in de pagina de optie **[!UICONTROL Submit]** om het CDN-validatieproces te starten.

## CDN-validatiefouten oplossen

In alle gevallen wordt de gehele batch voor ongeldigmaking verwerkt of is de hele batch mislukt.

| Fout | Toelichting |
| --- | --- |
| *Kan URL&#39;s voor geselecteerde elementen niet ophalen.* | Vindt plaats als aan een van de volgende scenario&#39;s is voldaan:<br>- Er is geen Dynamic Media-configuratie gevonden.<br>- Er is een uitzondering bij het ophalen van een servicegebruiker via welke de Dynamic Media-configuratie wordt gelezen.<br>- De publicatieserver of de hoofdmap van het bedrijf die wordt gebruikt om de URL&#39;s te maken, ontbreekt in de Dynamic Media-configuratie. |
| *Sommige URL&#39;s zijn niet correct gedefinieerd. Corrigeer en verzend opnieuw.* | Vindt plaats als de API voor invalidatie van het IPS CDN-cachegeheugen een fout retourneert. De fout wijst erop dat URL naar een verschillend bedrijf verwijst of URL is niet geldig zoals door de bevestiging door IPS cdnCacheInvalidation API wordt gedaan. |
| *Kan de CDN-cache niet ongeldig maken.* | Komt voor als het CDN verzoek van de geheim voorgeheugenongeldigverklaring om een andere reden ontbreekt. |
| *Er zijn geen URL&#39;s ingevoerd om ongeldig te worden gemaakt.* | Vindt plaats als er geen URL&#39;s aanwezig zijn in het dialoogvenster **[!UICONTROL CDN Invalidation]** - **[!UICONTROL Confirm]** en selecteert u **[!UICONTROL Submit]**. |


<!--  | I do not want to create a template. | Near the upper-right corner of the page, select **[!UICONTROL Cancel]**, then continue with ***Part 2: Working with CDN Invalidation***. While you are not required to create a template to use CDN Invalidation, Adobe recommends that you create one, especially if you have numerous assets that you need to update immediately, on a regular basis. The template is used at the time you set CDN invalidation options. | -->
