---
title: De CDN-cache ongeldig maken via Dynamic Media
description: Door de CDN-inhoud (Content Delivery Network) in de cache te ongeldig te maken, kunt u snel elementen bijwerken die door Dynamic Media worden geleverd, in plaats van te wachten tot de cache verloopt.
translation-type: tm+mt
source-git-commit: 68ee2c58588ad519aac673652349e0fefd20ee57
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# De CDN-cache ongeldig maken via Dynamic Media {#invalidating-cdn-cache-for-dm-assets-in-aem-cs}

De dynamische activa van Media worden in het voorgeheugen ondergebracht door CDN (het Netwerk van de Levering van de Inhoud) voor snelle levering aan uw klanten. Wanneer u echter updates uitvoert voor deze elementen, kunt u deze wijzigingen direct op uw website toepassen. Door de CDN-cache te wissen of ongeldig te maken, kunt u snel elementen bijwerken die door Dynamic Media worden geleverd. In plaats van te wachten op het verlopen van het geheime voorgeheugen gebruikend een waarde van TTL (Tijd aan Levende) (gebrek is 10 uren), kunt u een verzoek van binnen Dynamische de gebruikersinterface van Media verzenden om het geheime voorgeheugen binnen notulen te laten verlopen.

>[!IMPORTANT]
>
>De volgende stappen zijn alleen van toepassing op Dynamic Media op AEM als Cloud Service. U moet ook de uit-van-de-doos CDN gebruiken die met AEM Dynamische Media wordt gebundeld. Een andere aangepaste CDN wordt niet ondersteund door deze functie. <!-- If you are using Dynamic Media in AEM 6.5, Service Pack 5 or earlier to invalidate the CDN cache [use the steps found here](/help/assets/invalidate-cdn-cache-dm-classic.md). -->

Zie ook [Caching overzicht in Dynamische Media](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**De CDN-cache ongeldig maken met behulp van dynamische media**

*Deel 1: Een CDN-validatiesjabloon maken*

1. In AEM as a Cloud Service, tap **[!UICONTROL Tools > Assets > CDN Invalidation Template.]**

   ![Functie voor CDN-validatie](/help/assets/assets-dm/cdn-invalidation-template.png)

1. Voer op de **[!UICONTROL CDN Invalidation Template]** pagina een van de volgende opties uit op basis van uw scenario:

   | Scenario | Optie |
   | --- | --- |
   | Ik heb in het verleden al een CDN-validatiesjabloon gemaakt met Dynamic Media Classic. | Het **[!UICONTROL Create Template]** tekstveld wordt vooraf gevuld met uw sjabloongegevens. In dat geval kunt u de sjabloon bewerken of doorgaan met de volgende stap. |
   | Ik moet een sjabloon maken. Wat ga ik binnen? | Voer in het **[!UICONTROL Create Template]** tekstveld een afbeeldings-URL (inclusief voorinstellingen of modifiers voor afbeeldingen) in die verwijst `<ID>`in plaats van een specifieke afbeeldings-id zoals in het volgende voorbeeld:<br><br>`https://my.publishserver.com/is/image/company_name/<ID>?$product$`<br><br>Als de sjabloon alleen bevat `<ID>`, vult Dynamic Media in `https://<publishserver_name>/is/image` waar `<publishserver_name>` de naam van uw publicatieserver is en `ID` de geselecteerde elementen ongeldig moeten worden gemaakt.<br><br>Alleen afbeeldingen, dat wil zeggen `/is/image`- kunnen op basis van de sjabloon automatisch worden gevormd. Als u bijvoorbeeld elementen zoals video&#39;s of PDF&#39;s toevoegt met de elementkiezer, worden er automatisch geen URL&#39;s gegenereerd. `/is/content/` In plaats daarvan moet u deze elementen opgeven in de CDN-validatiesjabloon of kunt u de URL handmatig aan deze elementen toevoegen in *deel 2: Opties voor* CDN-validatie instellen.<br>De formaten van activa die in Dynamische Media worden gesteund zijn in aanmerking voor ongeldigverklaring. Elementen zoals PowerPoints of tekstbestanden zonder opmaak worden niet ondersteund voor CDN-validatie.<br>Wanneer u het malplaatje creeert, maar zeker u zorgvuldig aandacht aan syntaxis en typos besteedt; Dynamische media kan geen sjabloonvalidatie uitvoeren.<br>Het volgende sjabloonvoorbeeld is alleen ter illustratie. |

   ![CDN-validatiesjabloon - maken](/help/assets/assets-dm/cdn-invalidation-template-create-2.png)

1. Tik in de rechterbovenhoek van de pagina CDN-validatiesjabloon op **[!UICONTROL Save]** en tik vervolgens op **[!UICONTROL OK]**.

   *Deel 2: Opties voor CDN-validatie instellen*

1. In AEM as a Cloud Service, tap **[!UICONTROL Tools > Assets > CDN Invalidation.]**

   ![Functie voor CDN-validatie](/help/assets/assets-dm/cdn-invalidation-path.png)

1. Selecteer op de pagina **[!UICONTROL CDN Invalidation]** - **[!UICONTROL Add Details]** de elementen voor CDN-validatie.

   ![CDN-validatie - Details toevoegen](/help/assets/assets-dm/cdn-invalidation-add-details-2.png)

   >[!NOTE]
   >
   >Als u besluit om de opties **[!UICONTROL Invalidate asset associated image presets in CDN]** en *het* **[!UICONTROL Invalidate based on template]** selectievakje uit te schakelen, wordt de basis-URL van de geselecteerde elementen voor ongeldigmaking samengesteld. Gebruik deze optie alleen voor afbeeldingen.


   | Optie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Invalidate asset associated image presets in CDN]** | (Optioneel) Wanneer u deze optie inschakelt, kunt u een of meer dynamische media-elementen selecteren, ongeacht het MIME-type en de bijbehorende voorinstellingen voor afbeeldingen, zodat de cache ongeldig wordt.<br>Elementen en de bijbehorende vooraf gedefinieerde URL&#39;s met voorinstellingen worden automatisch gevormd voor validatie. Deze optie werkt alleen voor<br>afbeeldingselementen. U kunt wel een of meer mappen met elementen selecteren, maar Adobe raadt deze aanpak niet aan. In plaats daarvan moet u afzonderlijke elementbestanden selecteren. |
   | **[!UICONTROL Invalidation based on template]** | (Optioneel) Schakel deze optie in als u alleen de gedefinieerde sjabloon voor URL-formatie wilt gebruiken. |
   | **[!UICONTROL Add Assets]** | Gebruik de elementkiezer om elementen te selecteren die u ongeldig wilt maken. U kunt gepubliceerde of niet-gepubliceerde elementen selecteren.<br>U krijgt mogelijk een lege lijst wanneer u elementen toevoegt. Dynamische media gebruikt de CDN ongeldig malplaatje om automatisch URL tot stand te brengen om CDN ongeldig te maken. Als er geen CDN is gemaakt voor ongeldig maken van sjabloon, wordt er een lege lijst weergegeven.<br>Het in cache plaatsen van de CDN is gebaseerd op URL en niet op elementen. Daarom is het noodzakelijk dat u op de hoogte bent van de volledige URL&#39;s die op uw website staan. Nadat u deze URL&#39;s hebt bepaald, kunt u ze aan de sjabloon toevoegen. Vervolgens kunt u deze elementen selecteren en toevoegen en de URL&#39;s in één stap ongeldig maken. De andere optie die u hebt, is het toevoegen van URL&#39;s aan de lijst CDN-validatie. Als u deze aanpak wilt gebruiken, hoeft u geen elementen te selecteren en toe te voegen voordat u tikt **[!UICONTROL Next]** en vervolgens **[!UICONTROL Submit]** voor validatie.<br>Gebruik deze optie in combinatie met **[!UICONTROL Invalidate asset associated image presets in CDN]**, of **[!UICONTROL Invalidation based on template]**, of beide. |
   | **[!UICONTROL Add URL]** | Voeg handmatig volledige URL-paden toe aan dynamische media-elementen waarvan u de CDN-cache wilt ongeldig maken. Gebruik deze optie als u geen CDN-validatiesjabloon hebt gemaakt in ***Deel 1: Werken met de CDN-validatiesjabloon*** en slechts een paar elementen bevatten om ongeldig te maken.<br> |

1. Near the upper-right corner of the page, tap **[!UICONTROL Next]**.
1. Op de **[!UICONTROL CDN Invalidation]** - pagina, in de **[!UICONTROL Confirm]** **[!UICONTROL URLs]** lijstdoos, zult u een lijst van één of meerdere URLs zien die van het Malplaatje van de Bevestiging CDN worden geproduceerd u vroeger creeerde en de activa u enkel toevoegde.

   Stel dat u met de eerder gemaakte CDN-validatiesjabloon één element met de naam `spinset`hebt toegevoegd. Wanneer u hierop tikt, resulteert dit in de volgende vijf gegenereerde URL&#39;s in de **[!UICONTROL Tools > Assets > CDN Invalidation]** **[!UICONTROL CDN Invalidation - Confirm]** gebruikersinterface:

   ![CDN-validatie - Bevestigen](/help/assets/assets-dm/cdn-invalidation-confirm-2.png)

   Tik zo nodig op de **X** rechts van een URL om deze te verwijderen uit het validatieproces. U kunt maximaal 1000 URL&#39;s tegelijk gebruiken.

1. Tik in de rechterbovenhoek van de pagina **[!UICONTROL Submit]** om het CDN-validatieproces te starten.

## Problemen met CDN-validatiefouten oplossen

* Met deze functie kunt u maximaal 1000 URL&#39;s per keer ongeldig maken. Een getal groter dan 1000 resulteert in een fout die u kunt oplossen door URL&#39;s op de **[!UICONTROL CDN Invalidation – Confirm]** pagina te verwijderen.
* In alle gevallen wordt de gehele batch voor ongeldigmaking verwerkt of is de hele batch mislukt.

| Fout | Toelichting |
| --- | --- |
| *Kan URL(&#39;s) voor geselecteerde middel(en) niet ophalen.* | Komt voor als om het even welke volgende scenario&#39;s worden voldaan:<br>- een Dynamische configuratie van Media wordt niet gevonden.<br>- Er is een uitzondering bij het ophalen van een servicegebruiker via welke de configuratie Dynamische media wordt gelezen.<br>- De publicatieserver of de hoofdmap van het bedrijf die wordt gebruikt om de URL&#39;s te vormen, ontbreekt in de configuratie Dynamische media. |
| *Sommige URL&#39;s zijn niet correct gedefinieerd. Corrigeer en verzend opnieuw.* | Komt voor als IPS CDN geheim voorgeheugenongeldigheid API een fout terugkeert die URL naar een verschillend bedrijf verwijst of als URL niet geldig zoals volgens de bevestiging is door IPS cdnCacheInvalidation API wordt gedaan. |
| *Kan de CDN-cache niet ongeldig maken.* | Komt voor als het CDN verzoek van de geheim voorgeheugenongeldigverklaring om een andere reden ontbreekt. |
| *Er zijn geen URL&#39;s ingevoerd om ongeldig te worden gemaakt.* | Komt voor als er geen URLs aanwezig in zijn, **[!UICONTROL CDN Invalidation – Confirm page]** en u tikt **[!UICONTROL Submit]**. |


<!--  | I do not want to create a template. | Near the upper-right corner of the page, tap **[!UICONTROL Cancel]**, then continue with ***Part 2: Working with CDN Invalidation***. Note that while you are not required to create a template to use CDN Invalidation, Adobe recommends that you create one, especially if you have numerous assets that you need to update immediately, on a regular basis. The template is used at the time you set CDN invalidation options. | -->