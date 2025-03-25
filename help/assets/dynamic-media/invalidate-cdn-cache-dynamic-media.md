---
title: De cache van het netwerk voor inhoudslevering ongeldig maken via Dynamic Media
description: Leer hoe u inhoud in de cache van uw CDN (Content Delivery Network) ongeldig maakt, zodat u snel elementen kunt bijwerken die door Dynamic Media worden geleverd, in plaats van te wachten tot de cache verloopt.
contentOwner: Rick Brough
feature: Asset Management
role: Admin,User
exl-id: c631079b-8082-4ff7-a122-dac1b20d8acd
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '1310'
ht-degree: 0%

---

# De CDN-cache ongeldig maken via Dynamic Media {#invalidating-cdn-cache-for-dm-assets-in-aem-cs}

De dynamische activa van Media worden in het voorgeheugen ondergebracht door CDN (het Netwerk van de Levering van de Inhoud) voor snelle levering aan uw klanten. Wanneer u echter updates van deze elementen uitvoert, wilt u dat deze wijzigingen onmiddellijk op uw website van kracht worden. Door de CDN-cache te wissen of ongeldig te maken, kunt u snel elementen bijwerken die door Dynamic Media worden geleverd. U hoeft niet meer te wachten tot de cache verloopt met een TTL-waarde (Time To Live) (de standaardwaarde is tien uur). In plaats daarvan kunt u een aanvraag vanuit de gebruikersinterface van Dynamic Media verzenden om de cache binnen enkele minuten te laten verlopen.

>[!NOTE]
>
>Deze functie vereist dat u de door Adobe gebundelde CDN gebruikt die wordt geleverd bij Adobe Experience Manager Dynamic Media. Een andere aangepaste CDN wordt niet ondersteund met deze functie.

<!-- REMOVED MARCH 28, 2022 BECAUSE OF 404; NO REDIRECT WAS PUT IN PLACE BY SUPPORT See also [Cache overview in Dynamic Media](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html). -->

Als u [ Slimme Beeldvorming ](/help/assets/dynamic-media/imaging-faq.md) op uw rekening hebt toegelaten en u Adobe-Gebundelde CDN gebruikt, kunt u alle URLs met verschillende vraagkoorden zuiveren door enige basis URL te zuiveren.

Als u bijvoorbeeld `https://weekendsite.scene7.com/is/image/<CUSTOMER-NAME>/image` ongeldig maakt, worden ook de volgende URL&#39;s ongeldig:

* `https://weekendsite.scene7.com/is/image/<CUSTOMER-NAME>/image`
* `https://weekendsite.scene7.com/is/image/<CUSTOMER-NAME>/image?wid=300`
* `https://weekendsite.scene7.com/is/image/<CUSTOMER-NAME>/image?$PLP$`
* enzovoort.

Deze validatie is echter niet het geval voor algemene domeinen die Smart Imaging niet ondersteunen, zoals `s7d1.scene7.com` . Dergelijke domeinen hebben nog steeds de volledige URL nodig om validatiewerkzaamheden met succes uit te voeren.

**om het CDN geheime voorgeheugen als Dynamische Media ongeldig te maken:**

*Deel 1 van 2: Creërend een malplaatje van de Invalidatie CDN*

1. Ga in Adobe Experience Manager as a Cloud Service naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL CDN Invalidation Template]** .

   ![ eigenschap van de Bevestiging CDN ](/help/assets/assets-dm/cdn-invalidation-template.png)

1. Voer op de pagina **[!UICONTROL CDN Invalidation template]** op basis van uw scenario een van de volgende opties uit:

   | Scenario | Optie |
   | --- | --- |
   | Ik heb in het verleden al een CDN-validatiesjabloon gemaakt met Dynamic Media Classic. | Het tekstveld **[!UICONTROL Create Template]** wordt vooraf gevuld met uw sjabloongegevens. In dat geval kunt u de sjabloon bewerken of doorgaan met de volgende stap. |
   | Ik moet een sjabloon maken. Wat ga ik binnen? | Op het **[!UICONTROL Create Template]** tekstgebied, ga een beeld URL (met inbegrip van beeldvoorinstellingen of bepalingen) die `<ID>` van verwijzingen voorzien, in plaats van een specifieke beeldidentiteitskaart zoals in het volgende voorbeeld:<br>`https://my.publishserver.com/is/image/company_name/<ID>?$product$`<br> als het malplaatje enkel `<ID>` bevat, dan vult de Dynamische Media `https://<publishserver_name>/is/image/<company_name>/<ID>` in waar `<publishserver_name>` de naam van uw Publish Server is die in Algemene Montages in Dynamic Media Classic wordt bepaald. `<company_name>` is de naam van de hoofdmap van uw bedrijf die aan deze Experience Manager-instantie is gekoppeld. `<ID>` is de geselecteerde elementen via de elementenkiezer die ongeldig moeten worden gemaakt.<br> Om het even welke vooraf instelt/bepalingen na `<ID>` worden gekopieerd aangezien-is in de definitie URL.<br> slechts beelden-dat is, `/is/image` - kan worden auto gevormd gebaseerd op het malplaatje.<br> Voor `/is/content/`, produceert het toevoegen van activa zoals video&#39;s of PDFs gebruikend de activa plukker geen automatisch URLs. In plaats daarvan, moet u dergelijke activa of in het malplaatje van de Invalidatie CDN specificeren, of u kunt URL aan dergelijke activa in *Deel 2 van 2 manueel toevoegen: Het plaatsen van CDN de opties van de Invalidatie*.<br>**Voorbeelden:**<br> In dit eerste voorbeeld, bevat het ongeldigingsmalplaatje `<ID>` samen met activa URL die `/is/content` hebben. Bijvoorbeeld `http://my.publishserver.com:8080/is/content/dms7snapshot/<ID>` . Dynamische media vormen de URL op basis van dit pad, waarbij `<ID>` de elementen is die zijn geselecteerd via de elementenkiezer die u ongeldig wilt maken.<br> In dit tweede voorbeeld, bevat het validatiesjabloon de volledige URL van het element dat in uw wegeigenschappen met `/is/content` wordt gebruikt (niet afhankelijk van de elementenkiezer). Bijvoorbeeld `http://my.publishserver.com:8080/is/content/dms7snapshot/backpack` , waarbij rugzak de element-id is.<br> formaten van Activa die in Dynamische Media worden gesteund zijn geschikt voor ongeldigverklaring. De dossiertypes van activa die *niet* voor CDN ongeldig worden gesteund omvatten PostScript®, Encapsulated PostScript®, Adobe Illustrator, Adobe InDesign, Microsoft® Powerpoint, Microsoft® Excel, Microsoft® Word, en Rich Text Format.<br><br>・ Wanneer u de sjabloon maakt, maar zorg ervoor dat u de syntaxis en typos goed in de gaten houdt. Dynamische media voert geen sjabloonvalidatie uit.<br>・ Met de CDN-validatiesjabloon kunt u maximaal 2500 tekens opslaan.<br>・ Specificeer URLs voor beeld slimme gewassen of in dit malplaatje van de Invalidatie CDN, of in het **[!UICONTROL Add URL]** tekstgebied in *Deel 2: Plaatsende opties van de Invalidatie CDN.*<br>・ Elk item in een CDN-validatiesjabloon moet op een aparte regel staan.<br>・ Het volgende voorbeeld van de CDN-validatiesjabloon is alleen bedoeld als demonstratie. |

   ![ CDN Sjabloon voor validatie - creeer ](/help/assets/assets-dm/cdn-invalidation-template-create-2.png)

   >[!NOTE]
   >
   >Met de CDN-validatiesjabloon kunt u maximaal 2500 tekens opslaan.

1. Selecteer **[!UICONTROL Save]** in de rechterbovenhoek van de pagina **[!UICONTROL CDN Invalidation template]** en selecteer vervolgens **[!UICONTROL OK]** . <br>
   *Deel 2 van 2: De plaatsende opties van de Invalidatie CDN*
   <br>

1. Ga in Experience Manager as a Cloud Service naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL CDN Invalidation]** .

   ![ eigenschap van de Bevestiging CDN ](/help/assets/assets-dm/cdn-invalidation-path.png)

1. Selecteer op de pagina **[!UICONTROL CDN Invalidation]** - **[!UICONTROL Add Details]** de elementen voor CDN-validatie.

   ![ CDN ongeldig - voeg Details ](/help/assets/assets-dm/cdn-invalidation-add-details-2.png) toe

   >[!NOTE]
   >
   >Als u besluit om de opties **[!UICONTROL Invalidate asset associated image presets in CDN]** *en* **[!UICONTROL Invalidate based on template]** ongecontroleerd te verlaten, dan wordt de basis URL van de geselecteerde activa gevormd voor ongeldigverklaring. Gebruik deze optie-indeling alleen voor afbeeldingen.


   | Optie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Invalidate asset associated image presets in CDN]** | (Optioneel) Wanneer u deze optie inschakelt, worden geselecteerde elementen en alle bijbehorende URL&#39;s met voorinstellingen voor afbeeldingen automatisch samengesteld voor cachevalidatie.<br> Assets en hun bijbehorende vooraf bepaalde vooraf bepaalde URLs worden auto gevormd voor ongeldigverklaring. Deze optie werkt alleen voor afbeeldingselementen. |
   | **[!UICONTROL Invalidation based on template]** | (Optioneel) Schakel deze optie in als u alleen de gedefinieerde sjabloon voor URL-formatie wilt gebruiken. |
   | **[!UICONTROL Add Assets]** | Gebruik de elementkiezer om elementen te selecteren die u ongeldig wilt maken. U kunt gepubliceerde of niet-gepubliceerde elementen selecteren.<br> Caching bij CDN is op URL-Gebaseerd, niet op activa-gebaseerd. Daarom is het noodzakelijk dat u op de hoogte bent van de volledige URL&#39;s die op uw website staan. Nadat u deze URL&#39;s hebt bepaald, kunt u ze aan de sjabloon toevoegen. Vervolgens kunt u deze elementen selecteren en toevoegen en de URL&#39;s in één stap ongeldig maken. <br> Gebruik deze optie met **[!UICONTROL Invalidate asset associated image presets in CDN]**, of **[!UICONTROL Invalidation based on template]**, of allebei. |
   | **[!UICONTROL Add URL]** | Voeg handmatig volledige URL-paden toe aan dynamische media-elementen waarvan u de CDN-cache wilt ongeldig maken. Gebruik deze optie als u geen Malplaatje van de Invalidatie CDN in ***Deel 1 van 2 creeerde: Creërend een malplaatje van de Invalidatie CDN***, en slechts een paar activa hebben om ongeldig te maken.<br>**Belangrijk:** Elke URL die u toevoegt moet op zijn eigen lijn zijn.<br> u kunt tot 1000 URLs in een bepaalde tijd ongeldig maken. Als het aantal URL&#39;s in het tekstveld **[!UICONTROL Add URL]** groter is dan 1000, kunt u **[!UICONTROL Next]** niet selecteren. In dergelijke gevallen moet u **[!UICONTROL X]** rechts van een geselecteerd element selecteren of een handmatig toegevoegde URL selecteren om het element uit de lijst met validaties te verwijderen.<br> specificeer URLs voor beeld slimme gewassen of in het malplaatje van de Invalidatie CDN, of in dit **[!UICONTROL Add URL]** tekstgebied. |

1. Selecteer **[!UICONTROL Next]** in de rechterbovenhoek van de pagina.
1. Op de pagina **[!UICONTROL CDN Invalidation]** - **[!UICONTROL Confirm]** ziet u in de keuzelijst **[!UICONTROL URLs]** een lijst met een of meer URL&#39;s die zijn gegenereerd op basis van de eerder gemaakte CDN-validatiesjabloon en de elementen die u zojuist hebt toegevoegd.

   Als u bijvoorbeeld het voorbeeld voor de CDN-validatiesjabloon gebruikt dat eerder in de stappen werd weergegeven, kunt u een enkel element met de naam `spinset` toevoegen. Wanneer u naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL CDN Invalidation]** gaat, resulteert dit in de volgende vijf gegenereerde URL&#39;s in de gebruikersinterface van **[!UICONTROL CDN Invalidation - Confirm]** :

   ![ CDN ongeldig - bevestigt ](/help/assets/assets-dm/cdn-invalidation-confirm-2.png)

   Indien nodig, uitgezochte **X** rechts van een URL om het van het invalidatieproces te schrappen.

1. Selecteer **[!UICONTROL Submit]** in de rechterbovenhoek van de pagina om het CDN-validatieproces te starten.

## CDN-validatiefouten oplossen

In alle gevallen wordt de gehele batch voor ongeldigmaking verwerkt of is de hele batch mislukt.

| Fout | Toelichting |
| --- | --- |
| *Slaagde er niet in om URLs voor geselecteerde activa terug te winnen.* | Komt voor als om het even welke volgende scenario&#39;s worden voldaan:<br> - een Dynamische configuratie van Media wordt niet gevonden.<br> - Er is een uitzondering bij het ophalen van een servicegebruiker via welke de configuratie Dynamische media wordt gelezen.<br>- De publicatieserver of de hoofdmap van het bedrijf die wordt gebruikt om de URL&#39;s te maken, ontbreekt in de dynamische mediaconfiguratie. |
| *sommige URLs wordt niet correct bepaald. Juist en opnieuw verzenden.* | Vindt plaats als de API voor invalidatie van het IPS CDN-cachegeheugen een fout retourneert. De fout wijst erop dat URL naar een verschillend bedrijf verwijst of URL is niet geldig zoals door de bevestiging door IPS cdnCacheInvalidation API wordt gedaan. |
| *Slaagde er niet in om CDN geheime voorgeheugen ongeldig te maken.* | Komt voor als het CDN verzoek van de geheim voorgeheugenongeldigverklaring om een andere reden ontbreekt. |
| *Geen URLs inging om ongeldig te worden gemaakt.* | Vindt plaats als de pagina **[!UICONTROL CDN Invalidation]** - **[!UICONTROL Confirm]** geen URL&#39;s bevat en u **[!UICONTROL Submit]** selecteert. |


<!--  | I do not want to create a template. | Near the upper-right corner of the page, select **[!UICONTROL Cancel]**, then continue with ***Part 2: Working with CDN Invalidation***. While you are not required to create a template to use CDN Invalidation, Adobe recommends that you create one, especially if you have numerous assets that you need to update immediately, on a regular basis. The template is used at the time you set CDN invalidation options. | -->
