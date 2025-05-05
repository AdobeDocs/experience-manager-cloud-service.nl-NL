---
title: Inhoudsfragmenten
description: Met Adobe Experience Manager as a Cloud Service Content Fragments kunt u kanaalonafhankelijke inhoud ontwerpen, maken, beheren en gebruiken. Deze inhoud kan ook worden gebruikt bij het ontwerpen van uw pagina's.
exl-id: 7a44fc4e-3793-4aa3-8c21-db0567c93244
solution: Experience Manager Sites
feature: Authoring, Content Fragments
role: User
source-git-commit: 369f0be002413d164911515349b3e25d33eb8b2f
workflow-type: tm+mt
source-wordcount: '1272'
ht-degree: 0%

---

# Inhoudsfragmenten {#content-fragments}

De fragmenten van de inhoud in Adobe Experience Manager (AEM) as a Cloud Service worden [ gecreeerd en beheerd als pagina-onafhankelijke activa ](/help/sites-cloud/administering/content-fragments/overview.md), toestaand u om kanaal-neutrale inhoud, samen met (misschien kanaal-specifieke) variaties tot stand te brengen. U kunt deze fragmenten en de variaties ervan gebruiken bij het ontwerpen van de inhoudspagina&#39;s.

>[!CAUTION]
>
>Deze pagina moet samen met [ worden gelezen het Werken met de Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/overview.md) (en verwante pagina&#39;s) aangezien het basisterminologie en concepten, samen met informatie over het creëren van en het beheren van fragmenten introduceert, en het leveren van gestructureerde inhoudsfragmenten aan kanalen buiten de pagina&#39;s van AEM.

>[!NOTE]
>
>De Fragmenten van de inhoud zijn a **eigenschap van de Plaatsen**, maar worden opgeslagen als **Assets**.
>
>Zij worden hoofdzakelijk geleid met de **[console van de Fragmenten van de Inhoud](/help/sites-cloud/administering/content-fragments/overview.md#content-fragments-console)**, hoewel zij nog van de **[Assets](/help/assets/content-fragments/content-fragments-managing.md)** console kunnen worden beheerd.
>
>De standaardeditor voor [ Fragmenten van de Inhoud - Authoring ](/help/sites-cloud/administering/content-fragments/authoring.md) is de nieuwe redacteur; betreden van zowel de **console van de Fragmenten van de Inhoud** als de **Assets** console.
>
>Om de [ originele redacteur ](/help/assets/content-fragments/content-fragments-variations.md) te gebruiken, open eerst de nieuwe redacteur en deactiveer dan de **Nieuwe redacteur** schakelaar.

>[!NOTE]
>
>**de Fragmenten van de Inhoud** en **[Fragmenten van de Ervaring](/help/sites-cloud/authoring/fragments/content-fragments.md)** zijn verschillende eigenschappen binnen AEM:
>* **de Fragmenten van de Inhoud** zijn redactionele inhoud, met definitie en structuur, maar zonder extra visueel ontwerp en/of lay-out. Ze kunnen worden gebruikt om onder andere toegang te krijgen tot gestructureerde gegevens, zoals teksten, cijfers en datums.
>* **de Fragmenten van de Ervaring** zijn volledig opgemaakt inhoud; een fragment van een Web-pagina.
>
>De Fragmenten van de ervaring kunnen inhoud in de vorm van Inhoudsfragmenten bevatten, maar niet andersom.
>
>Voor meer informatie, zie [ Begrip van de Fragmenten van de Inhoud en de Fragmenten van de Ervaring in AEM ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html?lang=nl-NL#content-fragments).

Met de inhoudsfragmenten kunt u:

* **marketing en Campagne Strategie**
   * Inhoud controleren via centraal beheerde inhoudsfragmenten.
* **Creative Pro**
   * Het bijhouden van creatieve elementen via verzamelingen die zijn gekoppeld aan inhoudsfragmenten.
* **Schrijvers van het Exemplaar**
   * Schrijf in de AEM-inhoudsfragmenteditor.
   * Kan inhoudvariaties maken.
   * Kan relevante inhoud aan het inhoudsfragment koppelen.
   * Kan versioning/workflow gebruiken.
   * Kan inhoudsfragment delen.
   * Kan vertalingen centraal beheren.
* **Producenten en de Managers van de Reis**
   * Maak een keuze uit vooraf gedefinieerde fragmenten en variaties bij het ontwerpen in AEM.
   * Kan erop vertrouwen dat het fragment en de bijbehorende inhoud altijd up-to-date zijn terwijl kopieerschrijvers en -creatieven hun updates in centraal beheerde fragmenten en elementen maken.
   * Kan voor relevantie vertrouwen op gekoppelde media-inhoud die wordt verwerkt.
   * U kunt ad-hocinhoudvariaties maken terwijl u er toch voor zorgt dat deze variaties centraal worden beheerd in het fragment.

## Een inhoudsfragment toevoegen aan uw pagina {#adding-a-content-fragment-to-your-page}

1. Open de pagina om deze te bewerken.
2. Voeg de **component van het Fragment van de Inhoud** toe; van of **Componenten** browser of **Tussenvoegsel Nieuwe Component**.
3. U kunt:
   * Open **browser van Assets** en filter voor **de Fragmenten van de Inhoud** (het gebrek is Beelden). Sleep het gewenste fragment vervolgens naar de componentinstantie.
   * Selecteer de component van het inhoudsfragment, dan **vorm** van de toolbar. In de dialoog kunt u de selectiedialoog openen om het vereiste **Fragment van de Inhoud** te doorbladeren en te selecteren.

   >[!NOTE]
   >
   >Een andere methode is om een specifiek inhoudsfragment rechtstreeks naar de pagina te slepen. Hiermee wordt automatisch de bijbehorende component (inhoudsfragment) gemaakt.

4. Aanvankelijk, wordt de inhoud van het **Belangrijkste** Element en **Hoofd** (variatie) getoond. U kunt [ andere elementen en/of variaties ](#selecting-the-element-or-variation) zoals vereist selecteren.

   ![ de Fragmenten van de Inhoud in Browser van Assets ](/help/sites-cloud/authoring/assets/content-fragments.png)

   >[!NOTE]
   >
   >Zie ook voor meer informatie over de verdere bewerkingsfunctionaliteit:
   >
   >* [Responsieve lay-out](/help/sites-cloud/authoring/page-editor/responsive-layout.md)
   >* [Paginacontent bewerken](/help/sites-cloud/authoring/page-editor/edit-content.md)

### Het element of de variatie selecteren {#selecting-the-element-or-variation}

Open de dialoog van de Configuratie van het fragment **&#x200B;**&#x200B;om het fragment voor gebruik op de huidige pagina te vormen. Het dialoogvenster kan afhankelijk zijn van de gebruikte component.

>[!NOTE]
>
>Zie ook {de Componenten van 0} Kern, de Component van het Fragment van de Inhoud [&#128279;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=nl-NL)

In het juiste configuratiedialoogvenster kunt u de beschikbare parameters selecteren, waaronder:

* **het Fragment van de Inhoud**
   * Geef op welk fragment moet worden gebruikt.
* **Wijze van de Vertoning**:
   * **Enig Element van de Tekst**
   * **Veelvoudige Elementen**
* **Element**
   * Een selectie is beschikbaar afhankelijk van het gebruikte model.

  >[!NOTE]
  >
  >De beschikbare elementen zijn afhankelijk van het gebruikte model.

* **Variatie**
   * Het gebrek **Hoofd** is altijd beschikbaar.
   * Er is een selectie beschikbaar als er variaties zijn gemaakt voor het fragment.

* **identiteitskaart**

   * **identiteitskaart van HTML** attributen om op de component van toepassing te zijn.

### Snelle verbinding met de fragmenteditor {#quick-connection-to-fragment-editor}

U kunt de fragmentbron voor het uitgeven (de activa) openen gebruikend **uitgeeft** pictogram op de componententoolbar. Dit zal u [ toestaan om het inhoudsfragment ](/help/sites-cloud/administering/content-fragments/overview.md) uit te geven en te beheren.

>[!CAUTION]
>
>Zoals altijd heeft het bewerken van de fragmentbron invloed op alle pagina&#39;s die naar dat inhoudsfragment verwijzen.

### Tussenliggende inhoud toevoegen {#adding-in-between-content}

Wanneer een specifiek inhoudsfragment aan de pagina wordt toegevoegd, is er de componenten van de a **Belemmering hier** placeholder tussen elke paragraaf van HTML (en bij de bovenkant/bodem) van het fragment.

Dit laat u extra inhoud [ binnen-tussen (namelijk in-tussen inhoud) ](/help/assets/content-fragments/content-fragments.md#in-between-content-when-page-authoring-with-content-fragments) toevoegen de fragmentinhoud (op om het even welke beschikbare punten), zonder het moeten het wortelfragment veranderen.

Voor tussenliggende inhoud kunt u:

* Voeg componenten van [ browser van Componenten ](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser) toe
* Voeg activa van [ browser van Assets ](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#assets-browser) toe
* Het gebruik [ Verwante Inhoud ](#using-associated-content) als bron voor binnen-tussen inhoud.

>[!CAUTION]
>
>De tussenliggende inhoud is pagina-inhoud. Deze wordt niet opgeslagen in het inhoudsfragment.

![ component van het Tussenvoegsel ](/help/sites-cloud/authoring/assets/content-fragments-insert.png)

>[!NOTE]
>
>U kunt visuele activa (beelden) aan het fragment ook [ opnemen zelf ](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment).
>
>Visuele elementen die in het fragment zelf worden ingevoegd, worden aan de voorafgaande alinea in het fragment gekoppeld. Dit betekent dat u geen tussenliggende inhoud tussen een visueel element en de voorgaande alinea kunt plaatsen. Als u dit niveau van verbinding nodig hebt kunt u het beeld aan het fragment (als a [ mengen-media fragment ](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets)) toevoegen.

>[!CAUTION]
>
>Nadat u tussenliggende inhoud aan een inhoudsfragment op uw pagina hebt toegevoegd, kan het wijzigen van de structuur van het onderliggende inhoudsfragment (dat wil zeggen in de inhoudfragmenteditor) leiden tot onjuiste/onverwachte resultaten.
>
>Als dit gebeurt, wordt de tussenliggende inhoud als volgt bewaard:
>
>* Tussen componenten heeft een absolute positie binnen de reeks componenten in de fragmentstroom. Deze positie verandert niet, zelfs niet wanneer de inhoud van alinea&#39;s in het fragment verandert.
>
>  Hierdoor kan het lijken alsof de relatieve positionering is gewijzigd, aangezien de tussenliggende alinea&#39;s geen contextafhankelijke relatie hebben met de (fragment)alinea&#39;s naast de alinea&#39;s.
>* Tenzij de twee alinea&#39;s met elkaar in strijd zijn, wordt in dat geval de tussenliggende inhoud niet weergegeven (hoewel deze intern nog steeds aanwezig is).

### Gekoppelde inhoud gebruiken {#using-associated-content}

Als u [ bijbehorende inhoud ](/help/assets/content-fragments/content-fragments-assoc-content.md) met het [ inhoudsfragment ](/help/assets/content-fragments/content-fragments.md) hebt zijn deze activa beschikbaar van het zijpaneel (nadat u uw fragment op de inhoudspagina plaatst). De bijbehorende inhoud is effectief een speciale bron van inhoud voor [ binnen-tussen inhoud ](/help/assets/content-fragments/content-fragments.md#in-between-content-when-page-authoring-with-content-fragments).

>[!NOTE]
>
>Er zijn diverse methodes om [ visuele activa (bijvoorbeeld, beelden) ](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets) aan het fragment en/of de pagina toe te voegen.

>[!NOTE]
>
>Als u veelvoudige inhoudsfragmenten op één pagina hebt, zal het **Geassocieerde Inhoud** lusje activa aangewezen aan alle fragmenten tonen.

Zodra u een fragment met bijbehorende inhoud aan uw pagina hebt toegevoegd wordt een nieuw lusje (**Geassocieerde Inhoud**) geopend in het zijpaneel.

Van hieruit kunt u de elementen naar de gewenste locatie slepen (naar een bestaande component of naar de gewenste positie waar de desbetreffende component is gemaakt):

![ Invoegend een beeld ](/help/sites-cloud/authoring/assets/content-fragments-image.png)

### Assets ingevoegd in het fragment {#assets-inserted-into-the-fragment}

Als de activa (bijvoorbeeld, beelden) in het fragment zelf (als [ gemengd-media fragmenten ](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets)) zijn opgenomen, dan zijn de opties om deze activa in de paginaredacteur uit te geven beperkt.

Voor een afbeelding kunt u bijvoorbeeld

* Snijd, roteer of draai de afbeelding.
* Voeg een titel of alternatieve tekst toe.
* Geef een grootte op.
* U kunt ook de lay-out configureren.

Andere wijzigingen, zoals verplaatsen, kopiëren en verwijderen, moeten worden aangebracht in de fragmenteditor.

### Publiceren {#publishing}

Fragmenten moeten worden gepubliceerd zodat ze op gepubliceerde webpagina&#39;s kunnen worden gebruikt:

* Een fragment kan na [ worden gepubliceerd creërend het fragment in de console van de Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/managing.md#publishing-and-previewing-a-fragment).
* Als een *niet gepubliceerd fragment* op een pagina wordt gebruikt die wordt gepubliceerd, kan het fragment ook op dit ogenblik worden gepubliceerd.

## Inhoudsfragmenten exporteren {#exporting-content-fragments}

Voor export naar Adobe Target kan JSON worden gebruikt om het fragment te leveren. Zie:

* [Integreren met Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md)
* [Inhoudsfragmenten exporteren naar Adobe Target](/help/sites-cloud/integrating/content-fragments-target.md)
