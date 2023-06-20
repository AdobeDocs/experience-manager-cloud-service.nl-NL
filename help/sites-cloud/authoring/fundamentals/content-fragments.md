---
title: Contentfragmenten
description: Met Adobe Experience Manager as a Cloud Service Content Fragments kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en gebruiken
exl-id: 7a44fc4e-3793-4aa3-8c21-db0567c93244
source-git-commit: 635f4c990c27a7646d97ebd08b453c71133f01b3
workflow-type: tm+mt
source-wordcount: '1222'
ht-degree: 1%

---

# Contentfragmenten {#content-fragments}

Inhoudsfragmenten in as a Cloud Service Adobe Experience Manager (AEM) zijn [gemaakt en beheerd als pagina-onafhankelijke elementen](/help/sites-cloud/administering/content-fragments/content-fragments.md).

U kunt hiermee kanaalneutrale inhoud maken, samen met (mogelijk kanaalspecifieke) variaties. Vervolgens kunt u deze fragmenten en de variaties ervan gebruiken bij het ontwerpen van de inhoudspagina&#39;s.

Samen met de bijgewerkte JSON-exportfunctie kunnen gestructureerde inhoudsfragmenten ook worden gebruikt om AEM inhoud via Content Services te leveren aan andere kanalen dan AEM pagina&#39;s.

>[!NOTE]
>
>**Inhoudsfragmenten** en **[Ervaar fragmenten](/help/sites-cloud/authoring/fundamentals/experience-fragments.md)** zijn verschillende functies in AEM:
>* **Inhoudsfragmenten** redactionele inhoud, met definitie en structuur, maar zonder extra visueel ontwerp en/of lay-out. Ze kunnen worden gebruikt om onder andere toegang te krijgen tot gestructureerde gegevens, zoals teksten, cijfers en datums.
>* **Ervaar fragmenten** volledig zijn ingedeeld; een fragment van een webpagina.
>
>De Fragmenten van de ervaring kunnen inhoud in de vorm van Inhoudsfragmenten bevatten, maar niet andersom.
>
>Zie ook voor meer informatie [Inhoudsfragmenten en ervaringsfragmenten in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html#content-fragments).

>[!CAUTION]
>
>Deze pagina moet worden gelezen in combinatie met [Werken met inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/content-fragments.md) (en verwante pagina&#39;s), aangezien deze basisterminologie en -concepten introduceert en fragmenten maakt en beheert.

Met de inhoudsfragmenten kunt u:

* **Marketings- en Campagne-strategie**
   * Inhoud controleren via centraal beheerde inhoudsfragmenten.
* **Creative Pro**
   * Het bijhouden van creatieve elementen via verzamelingen die zijn gekoppeld aan inhoudsfragmenten.
* **Schrijvers kopiëren**
   * Schrijf in de fragmenteditor voor AEM inhoud.
   * Kan inhoudvariaties maken.
   * Kan relevante inhoud aan het inhoudsfragment koppelen.
   * Kan versioning/workflow gebruiken.
   * Kan inhoudsfragment delen.
   * Kan vertalingen centraal beheren.
* **Producenten en reismanagers**
   * Maak een keuze uit vooraf gedefinieerde fragmenten en variaties bij het ontwerpen in AEM.
   * Kan erop vertrouwen dat het fragment en de bijbehorende inhoud altijd up-to-date zijn terwijl kopieerschrijvers en -creatieven hun updates in centraal beheerde fragmenten en elementen maken.
   * Kan voor relevantie vertrouwen op gekoppelde media-inhoud die wordt verwerkt.
   * U kunt ad-hocinhoudvariaties maken terwijl u er toch voor zorgt dat deze variaties centraal worden beheerd in het fragment.

## Een inhoudsfragment toevoegen aan uw pagina {#adding-a-content-fragment-to-your-page}

1. Open de pagina om deze te bewerken.
2. Voeg de **Inhoudsfragment** onderdeel; van **Componenten** browser of **Nieuwe component invoegen**.
3. U kunt:
   * Open de **Activa** browser en filter voor **Inhoudsfragmenten** (de standaardwaarde is Afbeeldingen). Sleep het gewenste fragment vervolgens naar de componentinstantie.
   * Selecteer vervolgens de inhoudfragment-component **Configureren** op de werkbalk. In het dialoogvenster kunt u het dialoogvenster Selectie openen waarin u de vereiste **Inhoudsfragment**.

   >[!NOTE]
   >
   >Een andere methode is om een specifiek inhoudsfragment rechtstreeks naar de pagina te slepen. Hiermee wordt automatisch de bijbehorende component (inhoudsfragment) gemaakt.

4. In eerste instantie de inhoud van de **Hoofd** Element en **Master** (variatie) worden weergegeven. U kunt [andere elementen en/of variaties selecteren](#selecting-the-element-or-variation) zoals vereist.

   ![Inhoudsfragmenten in de middelenbrowser](/help/sites-cloud/authoring/assets/content-fragments.png)

   >[!NOTE]
   >
   >Zie ook voor meer informatie over de verdere bewerkingsfunctionaliteit:
   >
   >* [Responsieve lay-out](/help/sites-cloud/authoring/features/responsive-layout.md)
   >* [Paginacontent bewerken](/help/sites-cloud/authoring/fundamentals/editing-content.md)

### Het element of de variatie selecteren {#selecting-the-element-or-variation}

De fragmentinstellingen openen **Configuratie** om het fragment te configureren voor gebruik op de huidige pagina. Het dialoogvenster kan afhankelijk zijn van de gebruikte component.

>[!NOTE]
>
>Zie ook [Core Components, de component Content Fragment](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html)

In het juiste configuratiedialoogvenster kunt u de beschikbare parameters selecteren, waaronder:

* **Inhoudsfragment**
   * Geef op welk fragment moet worden gebruikt.
* **Weergavemodus**:
   * **Element voor één tekst**
   * **Meerdere elementen**
* **Element**
   * Een selectie is beschikbaar afhankelijk van het gebruikte model.

  >[!NOTE]
  >
  >Welke elementen beschikbaar zijn, is afhankelijk van het gebruikte model.

* **Variatie**
   * De standaardwaarde **Master** is altijd beschikbaar.
   * Er is een selectie beschikbaar als er variaties zijn gemaakt voor het fragment.

* **ID**

   * **HTML-id** kenmerk dat op de component moet worden toegepast.

### Snelle verbinding met de fragmenteditor {#quick-connection-to-fragment-editor}

U kunt de fragmentbron openen voor bewerking (het element) met de opdracht **Bewerken** op de werkbalk van de component. Hierdoor kunt u [het inhoudsfragment bewerken en beheren](/help/sites-cloud/administering/content-fragments/content-fragments.md).

>[!CAUTION]
>
>Zoals altijd heeft het bewerken van de fragmentbron invloed op alle pagina&#39;s die naar dat inhoudsfragment verwijzen.

### Tussenliggende inhoud toevoegen {#adding-in-between-content}

Wanneer een specifiek inhoudsfragment aan de pagina wordt toegevoegd, is er een **Componenten hierheen slepen** tijdelijke aanduiding tussen elke HTML-alinea (en boven/onder) van het fragment.

Zo kunt u extra inhoud toevoegen [tussenliggend (d.w.z. tussen inhoud)](/help/sites-cloud/administering/content-fragments/content-fragments.md#in-between-content-when-page-authoring-with-content-fragments) de fragmentinhoud (op een van de beschikbare punten), zonder dat u het basisfragment hoeft te wijzigen.

Voor tussenliggende inhoud kunt u:

* Componenten toevoegen uit het dialoogvenster [Browser voor componenten](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser).
* Elementen toevoegen uit het dialoogvenster [Bandenbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser).
* Gebruiken [Gekoppelde inhoud](#using-associated-content) als bron voor tussenliggende inhoud.

>[!CAUTION]
>
>De tussenliggende inhoud is pagina-inhoud. Deze wordt niet opgeslagen in het inhoudsfragment.

![Component invoegen](/help/sites-cloud/authoring/assets/content-fragments-insert.png)

>[!NOTE]
>
>U kunt ook [visuele elementen (afbeeldingen) invoegen in het fragment zelf](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment).
>
>Visuele elementen die in het fragment zelf worden ingevoegd, worden aan de voorafgaande alinea in het fragment gekoppeld. Dit betekent dat u geen tussenliggende inhoud tussen een visueel element en de voorgaande alinea kunt plaatsen. Als u dit verbindingsniveau nodig hebt, kunt u de afbeelding aan het fragment toevoegen (als een [fragment met gemengde media](/help/sites-cloud/administering/content-fragments/content-fragments.md#fragments-with-visual-assets)).

>[!CAUTION]
>
>Nadat u tussenliggende inhoud hebt toegevoegd aan een inhoudsfragment op uw pagina, kan het wijzigen van de structuur van het onderliggende inhoudsfragment (in de editor voor het inhoudsfragment) leiden tot onjuiste/onverwachte resultaten.
>
>Als dit gebeurt, wordt de tussenliggende inhoud als volgt bewaard:
>
>* Tussen componenten heeft een absolute positie binnen de reeks componenten in de fragmentstroom. Deze positie verandert niet, zelfs niet wanneer de inhoud van alinea&#39;s in het fragment verandert.
>
>  Hierdoor kan het lijken alsof de relatieve positionering is gewijzigd, aangezien de tussenliggende alinea&#39;s geen contextafhankelijke relatie hebben met de (fragment)alinea&#39;s naast de alinea&#39;s.
>* Tenzij de twee alinea&#39;s met elkaar in strijd zijn; in dat geval wordt de tussenliggende inhoud niet weergegeven (hoewel deze inhoud intern nog steeds aanwezig is).

### Gekoppelde inhoud gebruiken {#using-associated-content}

Als u [gekoppelde inhoud](/help/sites-cloud/administering/content-fragments/content-fragments-assoc-content.md) met de [inhoudsfragment](/help/sites-cloud/administering/content-fragments/content-fragments.md) deze elementen zijn beschikbaar in het zijpaneel (nadat u het fragment op de inhoudspagina hebt geplaatst). Gekoppelde inhoud is in feite een speciale inhoudsbron voor [tussenliggende inhoud](/help/sites-cloud/administering/content-fragments/content-fragments.md#in-between-content-when-page-authoring-with-content-fragments).

>[!NOTE]
>
>Er zijn verschillende methoden om toe te voegen [visuele elementen (bijvoorbeeld afbeeldingen)](/help/sites-cloud/administering/content-fragments/content-fragments.md#fragments-with-visual-assets) op het fragment en/of de pagina.

>[!NOTE]
>
>Als u meerdere inhoudsfragmenten op één pagina hebt, kunt u **Gekoppelde inhoud** worden de elementen weergegeven die geschikt zijn voor alle fragmenten.

Nadat u een fragment met de bijbehorende inhoud aan de pagina hebt toegevoegd, wordt een nieuw tabblad toegevoegd (**Gekoppelde inhoud**) wordt geopend in het zijpaneel.

Van hieruit kunt u de elementen naar de gewenste locatie slepen (naar een bestaande component of naar de gewenste positie waar de desbetreffende component is gemaakt):

![Een afbeelding invoegen](/help/sites-cloud/authoring/assets/content-fragments-image.png)

### Elementen die in het fragment zijn ingevoegd {#assets-inserted-into-the-fragment}

Als elementen (bijvoorbeeld afbeeldingen) in het fragment zelf zijn ingevoegd (zoals [gemengde-mediafragmenten](/help/sites-cloud/administering/content-fragments/content-fragments.md#fragments-with-visual-assets)), zijn de opties voor het bewerken van deze elementen in de pagina-editor beperkt.

Voor een afbeelding kunt u bijvoorbeeld

* Snijd, roteer of draai de afbeelding.
* Voeg een titel of alternatieve tekst toe.
* Geef een grootte op.
* U kunt ook de lay-out configureren.

Andere wijzigingen, zoals verplaatsen, kopiëren en verwijderen, moeten worden aangebracht in de fragmenteditor.

### Publiceren {#publishing}

Fragmenten moeten worden gepubliceerd zodat ze op gepubliceerde webpagina&#39;s kunnen worden gebruikt:

* Een fragment kan na [het fragment maken in de console Inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md#publishing-and-previewing-a-fragment).
* Als een *niet-gepubliceerd fragment* wordt gebruikt op een pagina die wordt gepubliceerd, kan het fragment ook op dit moment worden gepubliceerd.

## Inhoudsfragmenten exporteren {#exporting-content-fragments}

Voor export naar Adobe Target kan JSON worden gebruikt om het fragment te leveren. Zie:

* [Integreren met Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md)
* [Inhoudsfragmenten exporteren naar Adobe Target](/help/sites-cloud/integrating/content-fragments-target.md)
