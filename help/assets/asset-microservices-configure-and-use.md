---
title: Elementmicroservices configureren en gebruiken
description: Configureer en gebruik de 'cloud-native asset microservices' om elementen op schaal te verwerken.
contentOwner: AG
feature: Asset Compute Microservices, Asset Processing, Asset Management
role: Architect, Admin
exl-id: 7e01ee39-416c-4e6f-8c29-72f5f063e428
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '2821'
ht-degree: 0%

---

# Middelenmicroservices en verwerkingsprofielen gebruiken {#get-started-using-asset-microservices}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Asset microservices zorgen voor schaalbare en veerkrachtige verwerking van middelen met behulp van cloudnative toepassingen (ook wel workers genoemd). Adobe beheert de services voor een optimale afhandeling van verschillende soorten bedrijfsmiddelen en verwerkingsopties.

De microdiensten van activa laten u a [ brede waaier van dossiertypes ](/help/assets/file-format-support.md) behandelen die meer formaten uit-van-de-doos dan wat met vorige versies van [!DNL Experience Manager] mogelijk is. Zo is het nu mogelijk miniatuurextractie van PSD- en PSB-indelingen uit te voeren, maar hiervoor zijn oplossingen van derden vereist, zoals [!DNL ImageMagick] .

De verwerking van elementen is afhankelijk van de configuratie in **[!UICONTROL Processing Profiles]** . De Experience Manager verstrekt een basisstandaardopstelling en laat beheerders specifiekere configuratie van de activaverwerking toevoegen. Beheerders maken, onderhouden en wijzigen de configuraties van naverwerkingsworkflows, inclusief optionele aanpassing. Door de workflows aan te passen kunnen ontwikkelaars de standaardaanbieding uitbreiden.

<!-- Proposed DRAFT diagram for asset microservices flow - see section "asset-microservices-flow.png (asset-microservices-configure-and-use.md)" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![ Een mening op hoog niveau van activa verwerkend ](assets/asset-microservices-flow.png " een mening op hoog niveau van activa verwerkend ")

>[!NOTE]
>
>De hier beschreven elementverwerking vervangt het `DAM Update Asset` -workflowmodel uit de vorige versies van [!DNL Experience Manager] . De meeste stappen voor het genereren van standaardvertoningen en het genereren van metagegevens worden vervangen door de verwerking van de asset microservices. Eventuele resterende stappen kunnen worden vervangen door de configuratie van de workflow na verwerking.

## Opties voor middelenverwerking begrijpen {#get-started}

In [!DNL Experience Manager] zijn de volgende verwerkingsniveaus mogelijk.

| Optie | Beschrijving | Gebruikte gevallen |
|---|---|---|
| [ Standaardconfiguratie ](#default-config) | Het is beschikbaar zoals is en kan niet worden gewijzigd. Deze configuratie biedt de mogelijkheid voor het genereren van zeer eenvoudige vertoningen. | <ul> <li>Standaardminiaturen die worden gebruikt door de gebruikersinterface van [!DNL Assets] (48, 140 en 319 pixels) </li> <li> Grote voorvertoning (webuitvoering, 1280 pixels) </li><li> Metagegevens en tekstextractie.</li></ul> |
| [ de configuratie van de Douane ](#standard-config) | Gevormd door beheerders via gebruikersinterface. Biedt meer opties voor het genereren van vertoningen door de standaardoptie uit te breiden. De optie voor het uit-van-de-doos uitbreiden voor verschillende indelingen en uitvoeringen. | <ul><li>FPO-uitvoering. </li> <li>Bestandsindeling en resolutie van afbeeldingen wijzigen</li> <li> Voorwaardelijk van toepassing op gevormde dossiertypes. </li> </ul> |
| [ profiel van de Douane ](#custom-config) | Gevormd door beheerders via gebruikersinterface om douanecode door douanetoepassingen te gebruiken om [ de Dienst van de Asset compute te roepen ](https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html). Ondersteunt complexere vereisten in een cloudnative en schaalbare methode. | Zie [ toegestane gebruiksgevallen ](#custom-config). |

<!-- To create custom processing profiles specific to your custom requirements, say to integrate with other systems, see [post-processing workflows](#post-processing-workflows).
-->

## Ondersteunde bestandsindelingen {#supported-file-formats}

Asset microservices bieden ondersteuning voor een groot aantal verschillende bestandsindelingen voor het verwerken, genereren en extraheren van metagegevens. Zie [ gesteunde dossierformaten ](file-format-support.md) voor de volledige lijst van types MIME en de functionaliteit die voor elk type wordt gesteund.

## Standaardconfiguratie {#default-config}

Sommige standaardwaarden zijn vooraf geconfigureerd om ervoor te zorgen dat de standaarduitvoeringen die in Experience Manager worden vereist, beschikbaar zijn. De standaardconfiguratie zorgt er ook voor dat extractie van metagegevens en tekstextractie beschikbaar zijn. Gebruikers kunnen direct beginnen met het uploaden of bijwerken van elementen en de standaardverwerking is standaard beschikbaar.

Met de standaardconfiguratie, slechts wordt het meest basisverwerkingsprofiel gevormd. Een dergelijk verwerkingsprofiel is niet zichtbaar in de gebruikersinterface en u kunt het niet wijzigen. Het wordt altijd uitgevoerd om geüploade elementen te verwerken. Een dergelijk standaardverwerkingsprofiel zorgt ervoor dat de basisverwerking die door [!DNL Experience Manager] wordt vereist, op alle elementen wordt voltooid.

<!-- ![processing-profiles-standard](assets/processing-profiles-standard.png)
-->

## Standaardconfiguratie {#standard-config}

[!DNL Experience Manager] biedt mogelijkheden om specifiekere uitvoeringen te genereren voor veelgebruikte indelingen, afhankelijk van de behoeften van de gebruiker. Een beheerder kan aanvullende [!UICONTROL Processing Profiles] maken om het maken van dergelijke vertoningen te vergemakkelijken. Gebruikers wijzen vervolgens een of meer van de beschikbare profielen toe aan specifieke mappen om de extra verwerking te voltooien. De extra verwerking kan bijvoorbeeld uitvoeringen genereren voor het web, mobiele apparaten en tablets. In de volgende video ziet u hoe u [!UICONTROL Processing Profiles] kunt maken en toepassen en hoe u de gemaakte uitvoeringen kunt openen.

* **de breedte en de hoogte van de Vertoning**: De breedte en de hoogtespecificatie van de Vertoning verstrekt maximumgrootte van het geproduceerde uitvoerbeeld. Middelenmicroservices proberen de grootst mogelijke uitvoering te produceren, waarbij de breedte en hoogte niet groter zijn dan respectievelijk de opgegeven breedte en hoogte. De hoogte-breedteverhouding blijft behouden, dat wil zeggen hetzelfde als het origineel. Een lege waarde houdt in dat bij de verwerking van elementen de pixelafmetingen van het origineel worden gebruikt.

* **MIME de regels van de typeopneming**: Wanneer een activa met een specifiek MIME type wordt verwerkt, wordt het MIME type eerst gecontroleerd tegen de uitgesloten MIME typewaarde voor de vertoningsspecificatie. Als deze overeenkomt met die lijst, wordt deze specifieke uitvoering niet gegenereerd voor het element (lijst van gewezen personen). Anders wordt het MIME-type gecontroleerd op basis van het opgenomen MIME-type en als het overeenkomt met de lijst, wordt de vertoning gegenereerd (lijst van gewenste personen).

* **Speciale FPO vertoning**: Wanneer het plaatsen van grote activa van [!DNL Experience Manager] in [!DNL Adobe InDesign] documenten, wacht een creatieve beroeps op een wezenlijke tijd nadat zij [ activa ](https://helpx.adobe.com/indesign/using/placing-graphics.html) plaatsen. Ondertussen kan de gebruiker [!DNL InDesign] niet gebruiken. Dit onderbreekt de creatieve stroom en beïnvloedt de gebruikerservaring negatief. Met Adobe kunt u tijdelijk kleine uitvoeringen in [!DNL InDesign] -documenten plaatsen, die later op verzoek kunnen worden vervangen door middelen met volledige resolutie. [!DNL Experience Manager] biedt uitvoeringen die alleen voor plaatsing worden gebruikt (FPO). Deze FPO-uitvoeringen hebben een kleine bestandsgrootte maar hebben dezelfde hoogte-breedteverhouding.

Het verwerkingsprofiel kan een FPO-uitvoering (alleen voor plaatsing) bevatten. Zie [!DNL Adobe Asset Link] [ documentatie ](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html) om te begrijpen als u het voor uw verwerkingsprofiel moet aanzetten. Voor meer informatie, zie {de volledige documentatie van de Verband van Activa van de Adobe 0} ](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html).[

### Een standaardprofiel maken {#create-standard-profile}

Ga als volgt te werk om een standaard verwerkingsprofiel te maken:

1. Beheerders openen **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Processing Profiles]** . Klik op **[!UICONTROL Create]**.
1. Geef een naam op waarmee u het profiel op unieke wijze kunt identificeren wanneer u het toepast op een map.
1. Schakel **[!UICONTROL Create FPO Rendition]** in op het tabblad **[!UICONTROL Image]** om FPO-uitvoeringen te genereren. Voer een **[!UICONTROL Quality]** -waarde in van 1-100.
1. Als u andere vertoningen wilt genereren, klikt u op **[!UICONTROL Add New]** en geeft u de volgende informatie op:

   * Bestandsnaam van elke vertoning.
   * Bestandsindeling (PNG, JPEG, GIF of WebP) van elke uitvoering.
   * Breedte en hoogte in pixels van elke uitvoering. Als de waarden niet worden opgegeven, wordt de volledige pixelgrootte van de oorspronkelijke afbeelding gebruikt.
   * Kwaliteit in procenten van elke JPEG en vertoning WebP.
   * MIME-typen zijn opgenomen en uitgesloten om de toepasbaarheid van een profiel te definiëren.

   ![ verwerking-profielen-toevoegend ](assets/processing-profiles-image.png)

1. Klik op **[!UICONTROL Save]**.

<!-- TBD: Update the video link when a new video is available from Tech Marketing.

The following video demonstrates the usefulness and usage of standard profile.

>[!VIDEO](https://video.tv.adobe.com/v/29832?quality=9)
-->

<!-- This image was removed per cqdoc-15624, as requested by engineering.
 ![processing-profiles-list](assets/processing-profiles-list.png) 
 -->

## Aangepast profiel en gebruiksscenario&#39;s {#custom-config}

[!DNL Asset Compute Service] steunt een verscheidenheid van gebruiksgevallen zoals standaardverwerking, verwerkings Adobe-specifieke formaten zoals de dossiers van Photoshop, en het uitvoeren van douane of organisatie-specifieke verwerking. De in het verleden vereiste aanpassing van de DAM-updateworkflow voor middelen wordt automatisch verwerkt of als configuratie van verwerkingsprofielen. Als met deze verwerkingsopties niet aan de bedrijfsbehoeften wordt voldaan, raadt de Adobe aan de standaardmogelijkheden te ontwikkelen en te gebruiken [!DNL Asset Compute Service] . Voor een overzicht, zie [ uitbreidbaarheid begrijpen en wanneer om het ](https://experienceleague.adobe.com/docs/asset-compute/using/extend/understand-extensibility.html) te gebruiken.

>[!NOTE]
>
>Adobe raadt u aan alleen een aangepaste toepassing te gebruiken als de zakelijke vereisten niet kunnen worden vervuld met de standaardconfiguraties of het standaardprofiel.

Het kan beeld, video, document, en andere dossierformaten in verschillende vertoningen met inbegrip van duimnagels, gehaalde tekst en meta-gegevens, en archieven omzetten.

De ontwikkelaars kunnen [!DNL Asset Compute Service] gebruiken [ om douanetoepassingen ](https://experienceleague.adobe.com/docs/asset-compute/using/extend/develop-custom-application.html) voor de gesteunde gebruiksgevallen tot stand te brengen. [!DNL Experience Manager] kan deze aangepaste toepassingen vanuit de gebruikersinterface aanroepen met behulp van aangepaste profielen die beheerders configureren. [!DNL Asset Compute Service] biedt ondersteuning voor de volgende gevallen waarin externe services worden aangeroepen:

* Gebruik [ ImageCutout API van 0} ](https://developer.adobe.com/photoshop/photoshop-api-docs/) en bewaar het resultaat als vertoning.[!DNL Adobe Photoshop]
* De systemen van de derde vraag om gegevens, bijvoorbeeld, een PIM systeem bij te werken.
* Gebruik de [!DNL Photoshop] API om verschillende uitvoeringen te genereren op basis van de Photoshop-sjabloon.
* Het gebruik [ Adobe Lightroom API ](https://developer.adobe.com/photoshop/photoshop-api-docs/) om de opgenomen activa te optimaliseren en die als vertoningen te bewaren.

>[!NOTE]
>
>U kunt de standaardmetagegevens niet bewerken met de aangepaste toepassingen. U kunt alleen aangepaste metagegevens wijzigen.

### Een aangepast profiel maken {#create-custom-profile}

Ga als volgt te werk om een aangepast profiel te maken:

1. Beheerders openen **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Processing Profiles]** . Klik op **[!UICONTROL Create]**.
1. Klik op het tabblad **[!UICONTROL Custom]**. Klik op **[!UICONTROL Add New]**. Geef de gewenste bestandsnaam van de vertoning op.
1. Geef de volgende informatie op.

   * Bestandsnaam van elke vertoning en een ondersteunde bestandsextensie.
   * [ Eind-punt URL van een aangepaste app van App Builder ](https://experienceleague.adobe.com/docs/asset-compute/using/extend/deploy-custom-application.html). De app moet afkomstig zijn van dezelfde organisatie als de Experience Manager-account.
   * Voeg de Parameters van de Dienst aan [ extra informatie of parameters tot de douanetoepassing ](https://experienceleague.adobe.com/docs/asset-compute/using/extend/develop-custom-application.html#extend) over.
   * MIME-typen zijn opgenomen en uitgesloten om de verwerking te beperken tot een paar specifieke bestandsindelingen.

   Klik op **[!UICONTROL Save]**.

De douanetoepassingen zijn hoofd [ App Builder ](https://developer.adobe.com/app-builder/docs/overview/) apps van het Project. Uw aangepaste toepassing krijgt alle beschikbare bestanden als deze zijn ingesteld met een verwerkingsprofiel. De toepassing moet de bestanden filteren.

>[!CAUTION]
>
>Als de App Builder-app en [!DNL Experience Manager] -account niet van dezelfde organisatie afkomstig zijn, werkt de integratie niet.

### Een voorbeeld van een aangepast profiel {#custom-profile-example}

Als u het gebruik van een aangepast profiel wilt illustreren, kunt u het beste een kwestie-case gebruiken om aangepaste tekst toe te passen op campagneafbeeldingen. U kunt een verwerkingsprofiel maken dat de Photoshop API gebruikt om de afbeeldingen te bewerken.

Dankzij de asset compute Service-integratie kan Experience Manager deze parameters aan de aangepaste toepassing doorgeven met behulp van het veld [!UICONTROL Service Parameters] . De aangepaste toepassing roept vervolgens de Photoshop API aan en geeft deze waarden door aan de API. U kunt bijvoorbeeld lettertypenaam, tekstkleur, tekstdikte en tekstgrootte doorgeven om aangepaste tekst toe te voegen aan campagneafbeeldingen.

<!-- TBD: Check screenshot against the interface. -->

![ douane-verwerkings-profiel ](assets/custom-processing-profile.png)

*Figuur: Het gebied van het gebruik [!UICONTROL Service Parameters] om toegevoegde informatie tot vooraf bepaalde parameters over te gaan bouwt in de douanetoepassing. In dit voorbeeld worden de afbeeldingen bijgewerkt met `Jumanji` tekst in `Arial-BoldMT` font.*

## Verwerkingsprofielen gebruiken om elementen te verwerken {#use-profiles}

Maak en pas de extra aangepaste verwerkingsprofielen toe op specifieke mappen die Experience Manager kan verwerken voor elementen die zijn geüpload naar of bijgewerkt in deze mappen. Het standaard ingebouwde standaard verwerkingsprofiel wordt altijd uitgevoerd, maar is niet zichtbaar in de gebruikersinterface. Als u een aangepast profiel toevoegt, worden beide profielen gebruikt om de geüploade elementen te verwerken.

Pas verwerkingsprofielen toe op mappen met een van de volgende methoden:

* Beheerders kunnen een definitie van het verwerkingsprofiel selecteren in **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Processing Profiles]** en **[!UICONTROL Apply Profile to Folders]** gebruiken. Er wordt een inhoudbrowser geopend waarmee u naar specifieke mappen kunt navigeren, deze kunt selecteren en de toepassing van het profiel kunt bevestigen.
* Gebruikers kunnen een map selecteren in de gebruikersinterface van Assets, **[!UICONTROL Properties]** actie gebruiken om het scherm met mapeigenschappen te openen, op de tab **[!UICONTROL Asset Processing]** klikken en in de lijst [!UICONTROL Processing Profile] het juiste verwerkingsprofiel voor die map selecteren. Klik op **[!UICONTROL Save & Close]** om de wijzigingen op te slaan.
  ![ pas verwerkingsprofiel op een omslag van het lusje van de Eigenschappen van Activa toe ](assets/folder-properties-processing-profile.png)

* De gebruikers kunnen omslagen of specifieke activa in het gebruikersinterface van Assets selecteren om een verwerkingsprofiel toe te passen, dan selecteren ![ activa opnieuw verwerkingspictogram ](assets/do-not-localize/reprocess-assets-icon.png) **[!UICONTROL Reprocess Assets]** optie van de opties beschikbaar op de bovenkant.

>[!TIP]
>
>Er kan slechts één verwerkingsprofiel worden toegepast op een map. Als u meer uitvoeringen wilt genereren, voegt u meer renderdefinities toe aan het bestaande verwerkingsprofiel.

Nadat een verwerkingsprofiel is toegepast op een map, worden alle nieuwe elementen die in deze map of een van de submappen van deze map zijn geüpload (of bijgewerkt), verwerkt met behulp van het extra verwerkingsprofiel dat is geconfigureerd. Deze verwerking is een aanvulling op het standaardprofiel.

>[!NOTE]
>
>Een verwerkingsprofiel dat is toegepast op een map, werkt voor de gehele structuur, maar kan worden overschreven door een ander profiel dat is toegepast op een submap. Wanneer middelen aan een omslag worden geupload, controleert de Experience Manager de bevattende omslageigenschappen voor een verwerkingsprofiel. Als er geen toepassing is, wordt gecontroleerd of er een verwerkingsprofiel van toepassing is in een bovenliggende map in de hiërarchie.

Als u wilt controleren of elementen worden verwerkt, bekijkt u een voorvertoning van de gegenereerde uitvoeringen in de weergave [!UICONTROL Renditions] in de linkerrails. Open de voorvertoning van elementen en open de linkerrails voor toegang tot de weergave **[!UICONTROL Renditions]** . De specifieke uitvoeringen in het verwerkingsprofiel, waarvoor het type van het specifieke element overeenkomt met de regels voor het opnemen van het MIME-type, moeten zichtbaar en toegankelijk zijn.

![ extra-vertoningen ](assets/renditions-additional-renditions.png)

*Cijfer: Voorbeeld van twee extra vertoningen die door een verwerkingsprofiel worden geproduceerd dat op de ouderomslag wordt toegepast.*

## Nabewerkingsworkflows {#post-processing-workflows}

In een situatie waarin aanvullende verwerking van elementen vereist is die niet met de verwerkingsprofielen kan worden bereikt, kunnen extra nabewerkingsworkflows aan de configuratie worden toegevoegd. Na de verwerking kunt u volledig aangepaste verwerking toevoegen bovenop de configureerbare verwerking met behulp van asset microservices.

De werkschema&#39;s na verwerking, of [ auto-begin werkschema ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/configuring/auto-start-workflows.html), indien gevormd, worden automatisch uitgevoerd door [!DNL Experience Manager] nadat de microdienstenverwerking eindigt. Het is niet nodig om handmatig starters voor werkstromen toe te voegen om de werkstromen te activeren. De voorbeelden zijn:

* Aangepaste workflowstappen om elementen te verwerken.
* Integraties om metagegevens of eigenschappen toe te voegen aan elementen van externe systemen, bijvoorbeeld product- of procesgegevens.
* Aanvullende verwerking door externe services.

Voer de volgende stappen uit om een workflowconfiguratie voor na verwerking toe te voegen aan [!DNL Experience Manager] :

* Maak een of meer workflowmodellen. Deze douanemodellen worden bedoeld als *post-verwerkende werkschemamodellen* in deze documentatie. Dit zijn reguliere [!DNL Experience Manager] workflowmodellen.
* Voeg de vereiste workflowstappen toe aan deze modellen. Controleer de stappen in de standaardworkflow en voeg alle vereiste standaardstappen toe aan de aangepaste workflow. De stappen worden uitgevoerd op de middelen die op een configuratie van het werkschemamodel worden gebaseerd. Als u bijvoorbeeld automatisch slimme tags wilt toepassen bij het uploaden van elementen, voegt u de stap toe aan het aangepaste workflowmodel voor nabewerking.
* Voeg [!UICONTROL DAM Update Asset Workflow Completed Process] stap aan het einde toe. Het toevoegen van deze stap zorgt ervoor dat de Experience Manager weet wanneer de verwerking beëindigt en het middel als verwerkt kan worden gemerkt, dat *Nieuw* op de activa wordt getoond.
* Creeer een configuratie voor de Dienst van de Runner van het Werkschema van de Douane die toestaat om uitvoering van een model van het post-verwerkingswerkschema of door een weg (omslagplaats) of door een regelmatige uitdrukking te vormen.

Voor details over welke standaardwerkschemastap in het post-verwerkingswerkschema kan worden gebruikt, zie [ werkschemastappen in postverwerkingswerkschema ](developer-reference-material-apis.md#post-processing-workflows-steps) in de ontwikkelaarsverwijzing.

### Workflowmodellen voor naverwerking maken {#create-post-processing-workflow-models}

Workflowmodellen na verwerking zijn standaardworkflowmodellen van [!DNL Experience Manager] . Maak verschillende modellen als u verschillende verwerkingen nodig hebt voor verschillende opslaglocaties of elementtypen.

De verwerkingsstappen worden indien nodig toegevoegd. U kunt zowel de ondersteunde stappen als aangepaste workflowstappen gebruiken.

Zorg ervoor dat de laatste stap van elke naverwerkingsworkflow `DAM Update Asset Workflow Completed Process` is. De laatste stap helpt ervoor te zorgen dat de Experience Manager weet wanneer de activaverwerking wordt voltooid.

### Workflowuitvoering na verwerking configureren {#configure-post-processing-workflow-execution}

Nadat de assetmicroservices de verwerking van de geüploade elementen hebben voltooid, kunt u een workflow voor nabewerking definiëren om de elementen verder te verwerken. Als u naverwerking wilt configureren met behulp van workflowmodellen, kunt u een van de volgende handelingen uitvoeren:

* [ pas een werkschemamodel in omslagEigenschappen ](#apply-workflow-model-to-folder) toe.
* [ vormt de dienst van de Runner van het Werkschema van de Douane ](#configure-custom-workflow-runner-service).

#### Workflowmodel toepassen op een map {#apply-workflow-model-to-folder}

Voor gangbare gebruiksgevallen na verwerking kunt u de methode gebruiken om een workflow toe te passen op een map. Voer de volgende stappen uit om een workflowmodel toe te passen in de map [!UICONTROL Properties] :

1. Maak een workflowmodel.
1. Selecteer een map, klik op **[!UICONTROL Properties]** op de werkbalk en klik op **[!UICONTROL Assets Processing]** tab.
1. Selecteer onder **[!UICONTROL Auto-start Workflow]** de gewenste workflow, geef een titel op voor de workflow en sla de wijzigingen op.

   ![ pas een post-verwerkingswerkschema op een omslag in zijn Eigenschappen ](assets/post-processing-profile-workflow-for-folders.png) toe

#### De service Custom Workflow Runner configureren {#configure-custom-workflow-runner-service}

U kunt de aangepaste workflowrunnerservice configureren voor de geavanceerde configuraties die niet gemakkelijk kunnen worden uitgevoerd door een workflow toe te passen op een map. Bijvoorbeeld een werkstroom die een reguliere expressie gebruikt. De Adobe CQ DAM Custom Workflow Runner (`com.adobe.cq.dam.processor.nui.impl.workflow.CustomDamWorkflowRunnerImpl`) is een OSGi-service. Het verstrekt de volgende twee opties voor configuratie:

* Workflows na verwerking volgens pad (`postProcWorkflowsByPath`): meerdere workflowmodellen kunnen worden weergegeven op basis van verschillende repository paden. Scheid paden en modellen met een dubbele punt. Eenvoudige opslagpaden worden ondersteund. Wijs deze toe aan een werkschemamodel in de `/var` weg. Bijvoorbeeld: `/content/dam/my-brand:/var/workflow/models/my-workflow` .
* Workflows na verwerking op expressie (`postProcWorkflowsByExpression`): er kunnen meerdere workflowmodellen worden weergegeven op basis van verschillende reguliere expressies. Expressies en modellen moeten worden gescheiden door een dubbele punt. De reguliere expressie moet rechtstreeks naar het knooppunt Asset verwijzen en niet naar een van de uitvoeringen of bestanden. Bijvoorbeeld: `/content/dam(/.*/)(marketing/seasonal)(/.*):/var/workflow/models/my-workflow` .

Om te weten hoe te om een configuratie op te stellen OSGi, zie [ aan  [!DNL Experience Manager]](/help/implementing/deploying/overview.md) opstellen.

#### Uitvoering van workflow na verwerking uitschakelen

Wanneer post-verwerking niet nodig is, creeer en gebruik een &quot;leeg&quot;Model van het Werkschema in de __auto-begin van het Werkschema__ selectie.

##### Het workflowmodel voor automatisch opstarten van uitgeschakelde systemen maken

1. Ga aan __Hulpmiddelen > Werkschema > Modellen__
1. Selecteer __creeer > creeer Model__ van de hoogste actiebar
1. Geef een titel en naam op voor het nieuwe workflowmodel, bijvoorbeeld:
   * Titel: Auto-start Workflow uitschakelen
   * Naam: disable-auto-start-workflow
1. Selecteer __Gereed__ om het Model van het Werkschema tot stand te brengen
1. __Uitgezochte__ en __geeft__ het gecreeerde Model van het Werkschema uit
1. In de Modelredacteur van het Werkschema, uitgezochte __Stap 1__ van de modeldefinitie en schrap het
1. Open het __Zijpaneel__, en selecteer __Stappen__
1. Sleep de __voltooide 1} stap van het Activum van de Update DAM in de modeldefinitie__
1. Selecteer de __knoop van de Informatie van de Pagina__ (naast __zijComité__ knevel), en selecteer __Open Eigenschappen__
1. Onder het __Basis__ lusje, uitgezochte __Voorbijgaande Werkschema__
1. Selecteer __sparen &amp; Sluiten__ van de hoogste actiebar
1. Selecteer __Synchronisatie__ in de hoogste actiebar
1. Sluit de Redacteur van het Model van het Werkschema

##### Het workflowmodel voor automatisch opstarten van uitgeschakelde systemen toepassen

Volg de stappen die in [ worden geschetst een werkschemamodel op een omslag ](#apply-workflow-model-to-folder) toepassen en __onbruikbaar maken Auto-Begin Werkschema__ aangezien __Auto-begin Werkschema__ voor omslagen geen post-verwerking van activa vereist.

## Aanbevolen werkwijzen en beperkingen {#best-practices-limitations-tips}

* Houd rekening met uw behoeften aan alle typen uitvoeringen wanneer u workflows ontwerpt. Als u in de toekomst geen uitvoering nodig hebt, verwijdert u de aanmaakstap uit de workflow. Uitvoeringen kunnen daarna niet bulksgewijs worden verwijderd. Ongewenste vertoningen kunnen na langdurig gebruik van [!DNL Experience Manager] veel opslagruimte in beslag nemen. Voor afzonderlijke elementen kunt u uitvoeringen handmatig uit de gebruikersinterface verwijderen. Voor meerdere elementen kunt u [!DNL Experience Manager] aanpassen om specifieke vertoningen te verwijderen of de elementen verwijderen en deze opnieuw uploaden.
* Momenteel is de ondersteuning beperkt tot het genereren van uitvoeringen. Het genereren van nieuwe elementen wordt niet ondersteund.
* De maximale bestandsgrootte voor het uitnemen van metagegevens is momenteel ongeveer 15 GB. Wanneer u zeer grote elementen uploadt, mislukt het uitnemen van metagegevens soms.

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Publish Assets naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [ Inleiding aan de Dienst van de Asset compute ](https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html).
>* [ begrijp rekbaarheid en wanneer om het ](https://experienceleague.adobe.com/docs/asset-compute/using/extend/understand-extensibility.html) te gebruiken.
>* [ hoe te om douanetoepassingen ](https://experienceleague.adobe.com/docs/asset-compute/using/extend/develop-custom-application.html) tot stand te brengen.
>* [ Gesteunde types MIME voor diverse gebruiksgevallen ](/help/assets/file-format-support.md).

<!-- TBD: 
* How/where can admins check what's already configured and provisioned.
* How/where to request for new provisioning/purchase.
-->
