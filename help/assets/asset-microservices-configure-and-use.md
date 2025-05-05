---
title: Elementmicroservices configureren en gebruiken
description: Configureer en gebruik de 'cloud-native asset microservices' om elementen op schaal te verwerken.
contentOwner: AG
feature: Asset Compute Microservices, Asset Processing, Asset Management
role: Architect, Admin
exl-id: 7e01ee39-416c-4e6f-8c29-72f5f063e428
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '2874'
ht-degree: 0%

---

# Middelenmicroservices en verwerkingsprofielen gebruiken {#get-started-using-asset-microservices}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b> integratie van AEM Assets met Edge Delivery Services </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuw </i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b> laat Dynamische Media Prime en Ultimate </b></a> toe
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b> Beste praktijken van Meta-gegevens </b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b> Content Hub </b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b> Dynamische Media met mogelijkheden OpenAPI </b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b> de ontwikkelaarsdocumentatie van AEM Assets </b></a>
        </td>
    </tr>
</table>

Asset microservices zorgen voor schaalbare en veerkrachtige verwerking van middelen met behulp van cloudnative toepassingen (ook wel workers genoemd). Adobe beheert de services voor een optimale afhandeling van verschillende typen bedrijfsmiddelen en verwerkingsopties.

De microdiensten van activa laten u a [ brede waaier van dossiertypes ](/help/assets/file-format-support.md) behandelen die meer formaten uit-van-de-doos dan wat met vorige versies van [!DNL Experience Manager] mogelijk is. Zo is het nu mogelijk miniatuurextractie van PSD- en PSB-indelingen uit te voeren, maar hiervoor zijn oplossingen van derden vereist, zoals [!DNL ImageMagick] .

De verwerking van elementen is afhankelijk van de configuratie in **[!UICONTROL Processing Profiles]** . Experience Manager biedt een standaardconfiguratie en stelt beheerders in staat specifiekere configuratie voor middelenverwerking toe te voegen. Beheerders maken, onderhouden en wijzigen de configuraties van naverwerkingsworkflows, inclusief optionele aanpassing. Door de workflows aan te passen kunnen ontwikkelaars de standaardaanbieding uitbreiden.

<!-- Proposed DRAFT diagram for asset microservices flow - see section "asset-microservices-flow.png (asset-microservices-configure-and-use.md)" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![ Een mening op hoog niveau van activa verwerkend ](assets/asset-microservices-flow.png " een mening op hoog niveau van activa verwerkend ")

>[!NOTE]
>
>De hier beschreven elementverwerking vervangt het `DAM Update Asset` -workflowmodel uit de vorige versies van [!DNL Experience Manager] . De verwerking van asset-microservices vervangt het grootste deel van de standaardrenditie en aan metagegevens gerelateerde stappen en de configuratie van de workflow na verwerking kan de eventuele resterende stappen vervangen.

## Opties voor middelenverwerking begrijpen {#get-started}

In [!DNL Experience Manager] zijn de volgende verwerkingsniveaus mogelijk.

| Optie | Beschrijving | Gebruikte gevallen |
|---|---|---|
| [ Standaardconfiguratie ](#default-config) | Het is beschikbaar zoals is en kan niet worden gewijzigd. Deze configuratie biedt een basisvermogen voor het genereren van vertoningen. | <ul> <li>Standaardminiaturen die worden gebruikt door de gebruikersinterface van [!DNL Assets] (48, 140 en 319 pixels) </li> <li> Grote voorvertoning (webuitvoering, 1280 pixels) </li><li> Metagegevens en tekstextractie.</li></ul> |
| [ de configuratie van de Douane ](#standard-config) | Gevormd door beheerders als gebruikersinterface. Er zijn meer opties beschikbaar voor het genereren van vertoningen door de standaardoptie uit te breiden. De optie voor het uit-van-de-doos uitbreiden voor verschillende indelingen en uitvoeringen. | <ul><li>FPO (alleen voor plaatsing)-uitvoering. </li> <li>Bestandsindeling en resolutie van afbeeldingen wijzigen</li> <li> Voorwaardelijk van toepassing op gevormde dossiertypes. </li> </ul> |
| [ profiel van de Douane ](#custom-config) | Gevormd door beheerders via gebruikersinterface om douanecode door douanetoepassingen te gebruiken om [ Dienst van Asset Compute ](https://experienceleague.adobe.com/en/docs/asset-compute/using/introduction) te roepen. Ondersteunt complexere vereisten in een cloudnative en schaalbare methode. | Zie [ toegestane gebruiksgevallen ](#custom-config). |

<!-- To create custom processing profiles specific to your custom requirements, say to integrate with other systems, see [post-processing workflows](#post-processing-workflows).
-->

## Ondersteunde bestandsindelingen {#supported-file-formats}

Asset microservices bieden ondersteuning voor een groot aantal verschillende bestandsindelingen voor het verwerken, genereren en extraheren van metagegevens. Zie [ gesteunde dossierformaten ](file-format-support.md) voor de volledige lijst van types MIME en de functionaliteit die voor elk type wordt gesteund.

## Standaardconfiguratie {#default-config}

Sommige standaardwaarden zijn vooraf geconfigureerd om ervoor te zorgen dat de standaarduitvoeringen die in Experience Manager zijn vereist, beschikbaar zijn. De standaardconfiguratie zorgt er ook voor dat extractie van metagegevens en tekstextractie beschikbaar zijn. Gebruikers kunnen direct beginnen met het uploaden of bijwerken van elementen en de standaardverwerking is standaard beschikbaar.

Met de standaardconfiguratie, slechts wordt het meest basisverwerkingsprofiel gevormd. Een dergelijk verwerkingsprofiel is niet zichtbaar in de gebruikersinterface en u kunt het niet wijzigen. Het wordt altijd uitgevoerd om geüploade elementen te verwerken. Een dergelijk standaardverwerkingsprofiel zorgt ervoor dat de basisverwerking die door [!DNL Experience Manager] wordt vereist, op alle elementen wordt voltooid.

<!-- ![processing-profiles-standard](assets/processing-profiles-standard.png)
-->

## Standaardconfiguratie {#standard-config}

[!DNL Experience Manager] biedt mogelijkheden om specifiekere uitvoeringen te genereren voor veelgebruikte indelingen, afhankelijk van de behoeften van de gebruiker. Een beheerder kan aanvullende [!UICONTROL Processing Profiles] maken om het maken van dergelijke vertoningen te vergemakkelijken. Gebruikers wijzen vervolgens een of meer van de beschikbare profielen toe aan specifieke mappen om de extra verwerking te voltooien. De extra verwerking kan bijvoorbeeld uitvoeringen genereren voor het web, mobiele apparaten en tablets. In de volgende video ziet u hoe u [!UICONTROL Processing Profiles] kunt maken en toepassen en hoe u de gemaakte uitvoeringen kunt openen.

* **de breedte en de hoogte van de Vertoning**: De breedte en de hoogtespecificatie van de Vertoning verstrekken maximumgrootte van het geproduceerde uitvoerbeeld. Middelenmicroservices proberen de grootst mogelijke uitvoering te produceren, waarbij de breedte en hoogte niet groter zijn dan respectievelijk de opgegeven breedte en hoogte. De hoogte-breedteverhouding blijft behouden, dat wil zeggen hetzelfde als het origineel. Een lege waarde houdt in dat bij de verwerking van elementen de pixelafmetingen van het origineel worden gebruikt.

* **MIME de regels van de typeopneming**: Wanneer een activa met een specifiek MIME type wordt verwerkt, wordt het MIME type eerst gecontroleerd tegen de uitgesloten MIME typewaarde voor de vertoningsspecificatie. Als deze overeenkomt met die lijst, wordt deze specifieke uitvoering niet gegenereerd voor het element (lijst van gewezen personen). Anders wordt het MIME-type gecontroleerd op basis van het opgenomen MIME-type en als het overeenkomt met de lijst, wordt de vertoning gegenereerd (lijst van gewenste personen).

* **Speciale FPO vertoning**: Wanneer het plaatsen van grote activa van [!DNL Experience Manager] in [!DNL Adobe InDesign] documenten, wacht een creatieve beroeps op een wezenlijke tijd nadat zij [ activa ](https://helpx.adobe.com/indesign/using/placing-graphics.html) plaatsen. Ondertussen kan de gebruiker [!DNL InDesign] niet gebruiken. Dit onderbreekt de creatieve stroom en beïnvloedt de gebruikerservaring negatief. Met Adobe kunt u tijdelijk kleine uitvoeringen in [!DNL InDesign] -documenten plaatsen. Deze kunnen later worden vervangen door middelen voor volledige resolutie. Op aanvraag. [!DNL Experience Manager] biedt uitvoeringen die alleen voor plaatsing worden gebruikt. Deze FPO-uitvoeringen hebben een kleine bestandsgrootte maar hebben dezelfde hoogte-breedteverhouding.

Het verwerkingsprofiel kan een FPO-uitvoering (alleen voor plaatsing) bevatten. Zie [!DNL Adobe Asset Link] [ documentatie ](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html) om te begrijpen als u het voor uw verwerkingsprofiel moet aanzetten. Voor meer informatie, zie de [ volledige documentatie van de Verbinding van de Activa van Adobe ](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html).

### Een standaardprofiel maken {#create-standard-profile}

1. Beheerders openen **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Processing Profiles]** . Klik op **[!UICONTROL Create]**.
1. Geef een naam op waarmee u het profiel op unieke wijze kunt identificeren wanneer u het toepast op een map.
1. Schakel **[!UICONTROL Create FPO Rendition]** in op het tabblad **[!UICONTROL Image]** om FPO-uitvoeringen te genereren. Voer een **[!UICONTROL Quality]** -waarde in van 1-100.
1. Als u andere vertoningen wilt genereren, klikt u op **[!UICONTROL Add New]** en geeft u de volgende informatie op:

   * Bestandsnaam van elke vertoning.
   * Bestandsindeling (PNG, JPEG, GIF of WebP) voor elke uitvoering.
   * Breedte en hoogte in pixels van elke uitvoering. Als de waarden niet worden opgegeven, wordt de volledige pixelgrootte van de oorspronkelijke afbeelding gebruikt.
   * Kwaliteit in procent van elke JPEG- en WebP-uitvoering.
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

[!DNL Asset Compute Service] ondersteunt een groot aantal gebruiksgevallen, zoals standaardverwerking en verwerking van Adobe-specifieke indelingen, zoals Photoshop-bestanden. Het staat ook voor het uitvoeren van douane of organisatie-specifieke verwerking toe. De in het verleden vereiste aanpassing van de DAM-updateworkflow voor middelen wordt automatisch verwerkt of als configuratie Profielen verwerken. Als deze verwerkingsopties niet aan uw bedrijfsbehoeften voldoen, raadt Adobe aan de standaardfuncties uit te breiden met [!DNL Asset Compute Service] . Voor een overzicht, zie [ uitbreidbaarheid begrijpen en wanneer om het ](https://experienceleague.adobe.com/en/docs/asset-compute/using/extend/understand-extensibility) te gebruiken.

>[!NOTE]
>
>Adobe raadt het gebruik van een aangepaste toepassing alleen aan als de zakelijke vereisten niet kunnen worden vervuld met de standaardconfiguraties of het standaardprofiel.

Het kan beeld, video, document, en andere dossierformaten in verschillende vertoningen met inbegrip van duimnagels, gehaalde tekst en meta-gegevens, en archieven omzetten.

De ontwikkelaars kunnen [!DNL Asset Compute Service] gebruiken [ om douanetoepassingen ](https://experienceleague.adobe.com/en/docs/asset-compute/using/extend/develop-custom-application) voor de gesteunde gebruiksgevallen tot stand te brengen. [!DNL Experience Manager] kan deze aangepaste toepassingen vanuit de gebruikersinterface aanroepen met behulp van aangepaste profielen die beheerders configureren. [!DNL Asset Compute Service] biedt ondersteuning voor de volgende gevallen waarin externe services worden aangeroepen:

* Gebruik [ ImageCutout API van 0&rbrace; ](https://developer.adobe.com/photoshop/photoshop-api-docs/) en bewaar het resultaat als vertoning.[!DNL Adobe Photoshop]
* Vraag derdesystemen om veranderingen, bijvoorbeeld, een PIM systeem aan te brengen.
* Met de API van [!DNL Photoshop] kunt u diverse uitvoeringen genereren op basis van de Photoshop-sjabloon.
* Gebruik [ Adobe Lightroom API ](https://developer.adobe.com/photoshop/photoshop-api-docs/) om de opgenomen activa te optimaliseren en hen te bewaren als vertoningen.

>[!NOTE]
>
>U kunt de standaardmetagegevens niet bewerken met de aangepaste toepassingen. U kunt alleen aangepaste metagegevens wijzigen.

### Een aangepast profiel maken {#create-custom-profile}

1. Beheerders openen **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Processing Profiles]** > **[!UICONTROL Create]** .
1. Klik op de pagina Profiel verwerken op de tab **[!UICONTROL Custom]** en klik vervolgens op **[!UICONTROL Add New]** .
1. Typ in het tekstveld Naam de gewenste bestandsnaam van de vertoning en geef vervolgens de volgende informatie op.

   * Bestandsnaam van elke vertoning en een ondersteunde bestandsextensie.
   * [ Eindpunt URL van een aangepaste app van App Builder ](https://experienceleague.adobe.com/en/docs/asset-compute/using/extend/deploy-custom-application). De app moet afkomstig zijn van dezelfde organisatie als de Experience Manager-account.
   * Voeg de Parameters van de Dienst aan [ extra informatie of parameters tot de douanetoepassing ](https://experienceleague.adobe.com/en/docs/asset-compute/using/extend/develop-custom-application#extend) over.
   * MIME-typen zijn opgenomen en uitgesloten om de verwerking te beperken tot een paar specifieke bestandsindelingen.

1. Klik in de rechterbovenhoek van de pagina op **[!UICONTROL Save]**.

De douanetoepassingen zijn hoofd [ App Builder ](https://developer.adobe.com/app-builder/docs/overview/) apps van het Project. Uw aangepaste toepassing haalt alle beschikbare bestanden op als deze zijn ingesteld met een verwerkingsprofiel. De toepassing moet de bestanden filteren.

>[!CAUTION]
>
>Als de App Builder-app en [!DNL Experience Manager] -account niet van dezelfde organisatie afkomstig zijn, werkt de integratie niet.

### Een voorbeeld van een aangepast profiel {#custom-profile-example}

Als u het gebruik van een aangepast profiel wilt illustreren, kunt u het beste een kwestie-case gebruiken om aangepaste tekst toe te passen op campagneafbeeldingen. U kunt een verwerkingsprofiel maken dat de Photoshop API gebruikt om de afbeeldingen te bewerken.

Dankzij de integratie met Asset Compute Service kan Experience Manager deze parameters aan de aangepaste toepassing doorgeven met behulp van het veld [!UICONTROL Service Parameters] . De aangepaste toepassing roept vervolgens de Photoshop API aan en geeft deze waarden door aan de API. U kunt bijvoorbeeld lettertypenaam, tekstkleur, tekstdikte en tekstgrootte doorgeven om aangepaste tekst toe te voegen aan campagneafbeeldingen.

<!-- TBD: Check screenshot against the interface. -->

![ douane-verwerkings-profiel ](assets/custom-processing-profile.png)

*Figuur: Gebruik het [!UICONTROL Service Parameters] gebied om toegevoegde informatie tot vooraf bepaalde parameters over te gaan bouwen in de douanetoepassing. In dit voorbeeld worden de afbeeldingen bijgewerkt met `Jumanji` tekst in `Arial-BoldMT` font.*

## Verwerkingsprofielen gebruiken om elementen te verwerken {#use-profiles}

Maak aanvullende aangepaste verwerkingsprofielen en pas deze toe op specifieke mappen. Met deze workflow kan Experience Manager elementen verwerken die naar deze mappen zijn geüpload of die in deze mappen zijn bijgewerkt. Het standaard ingebouwde standaard verwerkingsprofiel wordt altijd uitgevoerd, maar is niet zichtbaar in de gebruikersinterface. Als u een aangepast profiel toevoegt, worden beide profielen gebruikt om de geüploade elementen te verwerken.

Pas verwerkingsprofielen toe op mappen met een van de volgende methoden:

* Beheerders kunnen een definitie van het verwerkingsprofiel selecteren in **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Processing Profiles]** en de handeling **[!UICONTROL Apply Profile to Folders]** gebruiken. Er wordt een inhoudbrowser geopend waarin u naar specifieke mappen kunt navigeren en deze kunt selecteren en vervolgens de toepassing van het profiel kunt bevestigen.
* Gebruikers kunnen een map selecteren in de Assets-gebruikersinterface en de handeling **[!UICONTROL Properties]** gebruiken om het scherm met de eigenschappen van de map te openen. Op het tabblad **[!UICONTROL Asset Processing]** kunnen ze in de lijst [!UICONTROL Processing Profile] het juiste verwerkingsprofiel voor die map selecteren. Klik op **[!UICONTROL Save & Close]** om de wijzigingen op te slaan.
  ![ pas verwerkingsprofiel op een omslag van het lusje van de Eigenschappen van Activa toe ](assets/folder-properties-processing-profile.png)

* De gebruikers kunnen omslagen of specifieke activa in het gebruikersinterface van Assets selecteren om een verwerkingsprofiel toe te passen, dan selecteren ![ activa opnieuw verwerkingspictogram ](assets/do-not-localize/reprocess-assets-icon.png) **[!UICONTROL Reprocess Assets]** optie van de opties beschikbaar op de bovenkant.

>[!TIP]
>
>Er kan slechts één verwerkingsprofiel worden toegepast op een map. Als u meer uitvoeringen wilt genereren, voegt u meer renderdefinities toe aan het bestaande verwerkingsprofiel.

Nadat een verwerkingsprofiel is toegepast op een map, worden alle nieuwe elementen die in deze map of een van de submappen van deze map zijn geüpload (of bijgewerkt), verwerkt met behulp van het extra verwerkingsprofiel dat is geconfigureerd. Deze verwerking is een aanvulling op het standaardprofiel.

>[!NOTE]
>
>Een verwerkingsprofiel dat is toegepast op een map, werkt voor de gehele structuur, maar kan worden overschreven door een ander profiel dat is toegepast op een submap. Wanneer elementen naar een map worden geüpload, controleert Experience Manager de eigenschappen van de bovenliggende map op een verwerkingsprofiel. Als er geen toepassing is, wordt gecontroleerd of er een verwerkingsprofiel van toepassing is in een bovenliggende map in de hiërarchie.

Als u wilt controleren of elementen worden verwerkt, bekijkt u een voorvertoning van de gegenereerde uitvoeringen in de weergave [!UICONTROL Renditions] in de linkerrails. Open de voorvertoning van het element en open het linkerspoor om de weergave **[!UICONTROL Renditions]** te openen. De specifieke uitvoeringen in het verwerkingsprofiel, waarvoor het type van het specifieke element overeenkomt met de regels voor het opnemen van het MIME-type, moeten zichtbaar en toegankelijk zijn.

![ extra-vertoningen ](assets/renditions-additional-renditions.png)

*Cijfer: Voorbeeld van twee extra vertoningen die door een verwerkingsprofiel worden geproduceerd dat op de ouderomslag wordt toegepast.*

## Nabewerkingsworkflows {#post-processing-workflows}

Voor een situatie waarin extra verwerking van activa wordt vereist die niet kan worden bereikt gebruikend de Profielen van de Verwerking, kunnen de extra postverwerkingswerkschema&#39;s aan de configuratie worden toegevoegd. Na de verwerking kunt u volledig aangepaste verwerking toevoegen bovenop de configureerbare verwerking met behulp van asset microservices.

Nadat de microdiensten verwerking eindigt, [!DNL Experience Manager] automatisch looppas postverwerkingswerkschema&#39;s, of [ auto-begin werkschema&#39;s ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/configuring/auto-start-workflows), als gevormd. Het is niet nodig om handmatig starters voor werkstromen toe te voegen om de werkstromen te activeren. De voorbeelden zijn:

* Aangepaste workflowstappen om elementen te verwerken.
* Integraties om metagegevens of eigenschappen toe te voegen aan elementen van externe systemen, bijvoorbeeld product- of procesgegevens.
* De extra verwerking wordt gedaan door de externe diensten.

Voer de volgende stappen uit om een workflowconfiguratie voor na verwerking toe te voegen aan [!DNL Experience Manager] :

* Maak een of meer workflowmodellen. Deze douanemodellen worden genoemd *post-verwerkings werkschemamodellen* in deze documentatie. Dit zijn reguliere [!DNL Experience Manager] workflowmodellen.
* Voeg de vereiste workflowstappen toe aan deze modellen. Controleer de stappen in de standaardworkflow en voeg alle vereiste standaardstappen toe aan de aangepaste workflow. De stappen worden uitgevoerd op de middelen die op een configuratie van het werkschemamodel worden gebaseerd. Als u bijvoorbeeld automatisch slimme tags wilt toepassen bij het uploaden van elementen, voegt u de stap toe aan het aangepaste workflowmodel voor nabewerking.
* Voeg de stap [!UICONTROL DAM Update Asset Workflow Completed Process] aan het einde toe. Het toevoegen van deze stap zorgt ervoor dat Experience Manager weet wanneer de verwerking beëindigt en de activa als verwerkt kunnen worden gemerkt, die *Nieuw* is wordt getoond op de activa.
* Creeer een configuratie voor de Dienst van de Runner van de Werkschema van de Douane die u uitvoering van een model van het post-verwerkingswerkschema of door een weg (omslagplaats) of door een regelmatige uitdrukking laat vormen.

Voor details over welke standaardwerkschemastap in het post-verwerkingswerkschema kan worden gebruikt, zie [ werkschemastappen in postverwerkingswerkschema ](developer-reference-material-apis.md#post-processing-workflows-steps) in de ontwikkelaarsverwijzing.

### Workflowmodellen voor naverwerking maken {#create-post-processing-workflow-models}

Workflowmodellen na verwerking zijn standaardworkflowmodellen van [!DNL Experience Manager] . Maak verschillende modellen als u verschillende verwerkingen nodig hebt voor verschillende opslaglocaties of elementtypen.

De verwerkingsstappen worden indien nodig toegevoegd. U kunt zowel de ondersteunde stappen gebruiken die beschikbaar zijn als aangepaste workflowstappen.

Zorg ervoor dat de laatste stap van elke naverwerkingsworkflow `DAM Update Asset Workflow Completed Process` is. De laatste stap zorgt ervoor dat Experience Manager opneemt wanneer de verwerking van bedrijfsmiddelen is voltooid.

### Workflowuitvoering na verwerking configureren {#configure-post-processing-workflow-execution}

Nadat de assetmicroservices de verwerking van de geüploade elementen hebben voltooid, kunt u een workflow voor nabewerking definiëren om de elementen verder te verwerken. Als u naverwerking wilt configureren met behulp van workflowmodellen, kunt u een van de volgende handelingen uitvoeren:

* [ pas een werkschemamodel in de omslagEigenschappen ](#apply-workflow-model-to-folder) toe.
* [ vormt de dienst van de Runner van het Werkschema van de Douane ](#configure-custom-workflow-runner-service).

#### Workflowmodel toepassen op een map {#apply-workflow-model-to-folder}

Voor gangbare gebruiksgevallen na verwerking kunt u de methode gebruiken om een workflow toe te passen op een map. Voer de volgende stappen uit om een workflowmodel toe te passen in de map [!UICONTROL Properties] :

1. Maak een workflowmodel.
1. Selecteer een map, klik op **[!UICONTROL Properties]** op de werkbalk en klik op de tab **[!UICONTROL Assets Processing]** .
1. Selecteer onder **[!UICONTROL Auto-start Workflow]** de gewenste workflow, geef een titel op voor de workflow en sla de wijzigingen op.

   ![ pas een post-verwerkingswerkschema op een omslag in zijn Eigenschappen ](assets/post-processing-profile-workflow-for-folders.png) toe

#### De service Custom Workflow Runner configureren {#configure-custom-workflow-runner-service}

U kunt de Dienst van de Runner van de Werkstroom van de Douane voor de geavanceerde configuraties vormen die niet gemakkelijk kunnen worden vervuld door een werkschema op een omslag toe te passen. Bijvoorbeeld een werkstroom die een reguliere expressie gebruikt. Adobe CQ DAM Custom Workflow Runner (`com.adobe.cq.dam.processor.nui.impl.workflow.CustomDamWorkflowRunnerImpl`) is een OSGi-service. Het verstrekt de volgende twee opties voor configuratie:

* Workflows na verwerking volgens pad (`postProcWorkflowsByPath`): meerdere workflowmodellen kunnen worden weergegeven op basis van verschillende repository paden. Scheid paden en modellen met een dubbele punt. Eenvoudige opslagpaden worden ondersteund. Wijs deze toe aan een workflowmodel in het `/var` -pad. Bijvoorbeeld: `/content/dam/my-brand:/var/workflow/models/my-workflow` .
* Workflows na verwerking op expressie (`postProcWorkflowsByExpression`): er kunnen meerdere workflowmodellen worden weergegeven op basis van verschillende reguliere expressies. Scheid expressies en modellen met een dubbele punt. Wijs de reguliere expressie rechtstreeks naar het knooppunt Asset, en niet naar een van de uitvoeringen of bestanden. Bijvoorbeeld: `/content/dam(/.*/)(marketing/seasonal)(/.*):/var/workflow/models/my-workflow` .

Om te weten hoe te om een configuratie op te stellen OSGi, zie [ aan  [!DNL Experience Manager]](/help/implementing/deploying/overview.md) opstellen.

#### Uitvoering van workflow na verwerking uitschakelen

Wanneer post-verwerking niet nodig is, creeer en gebruik een &quot;leeg&quot;Model van het Werkschema in de **auto-begin van het Werkschema** selectie.

##### Het workflowmodel voor automatisch opstarten van uitgeschakelde systemen maken

1. Navigeer aan **Hulpmiddelen** > **Werkschema** > **Modellen**.
1. Klik **creëren** > **creeer Model** van de hoogste actiebar.
1. Geef een titel en naam op voor het nieuwe workflowmodel, bijvoorbeeld:
   * Titel: Auto-start Workflow uitschakelen
   * Naam: disable-auto-start-workflow
1. Klik **Gedaan** om het werkschemamodel tot stand te brengen.
1. Het gemaakte workflowmodel selecteren en bewerken
1. In de redacteur van het werkschemamodel, klik **Stap 1** van de modeldefinitie en schrap het.
1. Van het zijpaneel, klik **Stappen**.
1. Sleep de **voltooide 1&rbrace; stap van het Gegevenswerkschema van de Update DAM in de modeldefinitie.**
1. Klik **de Informatie van de Pagina 0&rbrace; (naast** zijComité **knevel), en klik** Open Eigenschappen **.**
1. Onder het Basis lusje, klik **Voorbijgaande Werkschema**.
1. Van de hoogste actiebar, klik **sparen en sluit**.
1. Van de hoogste actiebar, klik **Synchronisatie**.
1. Sluit de editor voor het workflowmodel.

##### Het workflowmodel voor automatisch opstarten van uitgeschakelde systemen toepassen

Volg de stappen die in [ worden geschetst een werkschemamodel op een omslag ](#apply-workflow-model-to-folder) toepassen en **onbruikbaar maken Auto-Begin Werkschema** als **Auto-begin Werkschema** voor omslagen plaatsen die geen post-verwerking van activa vereisen.

## Aanbevolen werkwijzen en beperkingen {#best-practices-limitations-tips}

* Houd rekening met uw behoeften aan alle typen uitvoeringen wanneer u workflows ontwerpt. Als u in de toekomst geen uitvoering nodig hebt, verwijdert u de aanmaakstap uit de workflow. Uitvoeringen kunnen daarna niet bulksgewijs worden verwijderd. Ongewenste vertoningen kunnen na langdurig gebruik van [!DNL Experience Manager] veel opslagruimte in beslag nemen. Voor afzonderlijke elementen kunt u uitvoeringen handmatig uit de gebruikersinterface verwijderen. Voor meerdere elementen kunt u [!DNL Experience Manager] aanpassen om specifieke vertoningen te verwijderen of de elementen verwijderen en deze opnieuw uploaden.
* Momenteel is de ondersteuning beperkt tot het genereren van uitvoeringen. Het genereren van nieuwe elementen wordt niet ondersteund.
* De maximale bestandsgrootte voor het uitnemen van metagegevens is momenteel ongeveer 15 GB. Bij het uploaden van zeer grote elementen mislukt het extraheren van metagegevens soms.

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
* [Assets publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [ Inleiding aan de Dienst van Asset Compute ](https://experienceleague.adobe.com/en/docs/asset-compute/using/introduction).
>* [ begrijp de rekbaarheid en wanneer om het ](https://experienceleague.adobe.com/en/docs/asset-compute/using/extend/understand-extensibility) te gebruiken.
>* [ hoe te om douanetoepassingen ](https://experienceleague.adobe.com/en/docs/asset-compute/using/extend/develop-custom-application) tot stand te brengen.
>* [ Gesteunde types MIME voor diverse gebruiksgevallen ](/help/assets/file-format-support.md).

<!-- TBD: 
* How/where can admins check what's already configured and provisioned.
* How/where to request for new provisioning/purchase.
-->
