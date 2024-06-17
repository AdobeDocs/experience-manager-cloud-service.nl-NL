---
title: Elementmicroservices configureren en gebruiken
description: Configureer en gebruik de 'cloud-native asset microservices' om elementen op schaal te verwerken.
contentOwner: AG
feature: Asset Compute Microservices, Asset Processing, Asset Management
role: Architect, Admin
exl-id: 7e01ee39-416c-4e6f-8c29-72f5f063e428
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '2803'
ht-degree: 0%

---

# Middelenmicroservices en verwerkingsprofielen gebruiken {#get-started-using-asset-microservices}

Asset microservices zorgen voor schaalbare en veerkrachtige verwerking van middelen met behulp van cloudnative toepassingen (ook wel workers genoemd). Adobe beheert de services voor een optimale afhandeling van verschillende soorten bedrijfsmiddelen en verwerkingsopties.

Met Asset microservices kunt u een [brede waaier van dossiertypes](/help/assets/file-format-support.md) het behandelen van meer formaten buiten de doos dan wat met vorige versies van mogelijk is [!DNL Experience Manager]. Zo is het nu mogelijk miniatuurextractie van de indelingen PSD en PSB uit te voeren, maar hiervoor zijn oplossingen van derden vereist, zoals [!DNL ImageMagick].

De verwerking van bedrijfsmiddelen is afhankelijk van de configuratie in **[!UICONTROL Processing Profiles]**. De Experience Manager verstrekt een basisstandaardopstelling en laat beheerders specifiekere configuratie van de activaverwerking toevoegen. Beheerders maken, onderhouden en wijzigen de configuraties van naverwerkingsworkflows, inclusief optionele aanpassing. Door de workflows aan te passen kunnen ontwikkelaars de standaardaanbieding uitbreiden.

<!-- Proposed DRAFT diagram for asset microservices flow - see section "asset-microservices-flow.png (asset-microservices-configure-and-use.md)" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![Een overzicht op hoog niveau van de verwerking van bedrijfsmiddelen](assets/asset-microservices-flow.png "Een overzicht op hoog niveau van de verwerking van bedrijfsmiddelen")

>[!NOTE]
>
>De hier beschreven elementverwerking vervangt de `DAM Update Asset` workflowmodel dat bestaat in de vorige versies van [!DNL Experience Manager]. De meeste stappen voor het genereren van standaardvertoningen en het genereren van metagegevens worden vervangen door de verwerking van de asset microservices. Eventuele resterende stappen kunnen worden vervangen door de configuratie van de workflow na verwerking.

## Opties voor middelenverwerking begrijpen {#get-started}

[!DNL Experience Manager] maakt de volgende verwerkingsniveaus mogelijk.

| Optie | Beschrijving | Gebruikte gevallen |
|---|---|---|
| [Standaardconfiguratie](#default-config) | Het is beschikbaar zoals is en kan niet worden gewijzigd. Deze configuratie biedt de mogelijkheid voor het genereren van zeer eenvoudige vertoningen. | <ul> <li>Standaardminiaturen gebruikt door [!DNL Assets] gebruikersinterface (48, 140 en 319 pixels) </li> <li> Grote voorvertoning (webuitvoering, 1280 pixels) </li><li> Metagegevens en tekstextractie.</li></ul> |
| [Aangepaste configuratie](#standard-config) | Gevormd door beheerders via gebruikersinterface. Biedt meer opties voor het genereren van vertoningen door de standaardoptie uit te breiden. De optie voor het uit-van-de-doos uitbreiden voor verschillende indelingen en uitvoeringen. | <ul><li>FPO-uitvoering. </li> <li>Bestandsindeling en resolutie van afbeeldingen wijzigen</li> <li> Voorwaardelijk van toepassing op gevormde dossiertypes. </li> </ul> |
| [Aangepast profiel](#custom-config) | Gevormd door beheerders via gebruikersinterface om douanecode door douanetoepassingen te gebruiken om te roepen [Asset compute](https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html). Ondersteunt complexere vereisten in een cloudnative en schaalbare methode. | Zie [toegestane gebruiksgevallen](#custom-config). |

<!-- To create custom processing profiles specific to your custom requirements, say to integrate with other systems, see [post-processing workflows](#post-processing-workflows).
-->

## Ondersteunde bestandsindelingen {#supported-file-formats}

Asset microservices bieden ondersteuning voor een groot aantal verschillende bestandsindelingen voor het verwerken, genereren en extraheren van metagegevens. Zie [ondersteunde bestandsindelingen](file-format-support.md) voor de volledige lijst van MIME-typen en de ondersteunde functionaliteit voor elk type.

## Standaardconfiguratie {#default-config}

Sommige standaardwaarden zijn vooraf geconfigureerd om ervoor te zorgen dat de standaarduitvoeringen die in Experience Manager worden vereist, beschikbaar zijn. De standaardconfiguratie zorgt er ook voor dat extractie van metagegevens en tekstextractie beschikbaar zijn. Gebruikers kunnen direct beginnen met het uploaden of bijwerken van elementen en de standaardverwerking is standaard beschikbaar.

Met de standaardconfiguratie, slechts wordt het meest basisverwerkingsprofiel gevormd. Een dergelijk verwerkingsprofiel is niet zichtbaar in de gebruikersinterface en u kunt het niet wijzigen. Het wordt altijd uitgevoerd om geüploade elementen te verwerken. Een dergelijk standaardverwerkingsprofiel zorgt ervoor dat de basisverwerking die vereist is voor [!DNL Experience Manager] is op alle activa voltooid.

<!-- ![processing-profiles-standard](assets/processing-profiles-standard.png)
-->

## Standaardconfiguratie {#standard-config}

[!DNL Experience Manager] bieden mogelijkheden om specifiekere uitvoeringen voor algemene indelingen te genereren naar gelang de behoeften van de gebruiker. Een beheerder kan extra [!UICONTROL Processing Profiles] om het maken van dergelijke vertoningen te vergemakkelijken. Gebruikers wijzen vervolgens een of meer van de beschikbare profielen toe aan specifieke mappen om de extra verwerking te voltooien. De extra verwerking kan bijvoorbeeld uitvoeringen genereren voor het web, mobiele apparaten en tablets. De volgende video laat zien hoe u kunt maken en toepassen [!UICONTROL Processing Profiles] en hoe u de gemaakte uitvoeringen kunt openen.

* **Breedte en hoogte van vertoning**: De specificaties voor de renderingsbreedte en -hoogte bieden maximale grootten voor de gegenereerde uitvoerafbeelding. Middelenmicroservices proberen de grootst mogelijke uitvoering te produceren, waarbij de breedte en hoogte niet groter zijn dan respectievelijk de opgegeven breedte en hoogte. De hoogte-breedteverhouding blijft behouden, dat wil zeggen hetzelfde als het origineel. Een lege waarde houdt in dat bij de verwerking van elementen de pixelafmetingen van het origineel worden gebruikt.

* **MIME-regels voor typeintegratie**: Wanneer een element van een specifiek MIME-type wordt verwerkt, wordt het MIME-type eerst gecontroleerd aan de hand van de waarde van de uitgesloten MIME-typen voor de weergavespecificatie. Als deze overeenkomt met die lijst, wordt deze specifieke uitvoering niet gegenereerd voor het element (lijst van gewezen personen). Anders wordt het MIME-type gecontroleerd op basis van het opgenomen MIME-type en als het overeenkomt met de lijst, wordt de vertoning gegenereerd (lijst van gewenste personen).

* **Speciale FPO-uitvoering**: Bij het plaatsen van grote elementen van [!DNL Experience Manager] in [!DNL Adobe InDesign] documenten, een creatieve beroepsbeoefenaar wacht een lange tijd na [een element plaatsen](https://helpx.adobe.com/indesign/using/placing-graphics.html). Ondertussen wordt de gebruiker verhinderd te gebruiken [!DNL InDesign]. Dit onderbreekt de creatieve stroom en beïnvloedt de gebruikerservaring negatief. Met Adobe kunt u tijdelijk kleine uitvoeringen plaatsen in [!DNL InDesign] te beginnen documenten, die later kunnen worden vervangen door middelen met volledige resolutie. [!DNL Experience Manager] biedt uitvoeringen die alleen voor plaatsing (FPO) worden gebruikt. Deze FPO-uitvoeringen hebben een kleine bestandsgrootte maar hebben dezelfde hoogte-breedteverhouding.

Het verwerkingsprofiel kan een FPO-uitvoering (alleen voor plaatsing) bevatten. Zie [!DNL Adobe Asset Link] [documentatie](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html) om te begrijpen of moet u het voor uw verwerkingsprofiel aanzetten. Zie voor meer informatie [Adobe Asset Link, volledige documentatie](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html).

### Een standaardprofiel maken {#create-standard-profile}

Ga als volgt te werk om een standaard verwerkingsprofiel te maken:

1. Toegang voor beheerders **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Processing Profiles]**. Klik op **[!UICONTROL Create]**.
1. Geef een naam op waarmee u het profiel op unieke wijze kunt identificeren wanneer u het toepast op een map.
1. Als u FPO-uitvoeringen wilt genereren, klikt u op de knop **[!UICONTROL Image]** tab, enable **[!UICONTROL Create FPO Rendition]**. Invoer een **[!UICONTROL Quality]** waarde van 1-100.
1. Als u andere vertoningen wilt genereren, klikt u op **[!UICONTROL Add New]** en verstrekt de volgende informatie:

   * Bestandsnaam van elke vertoning.
   * Bestandsindeling (PNG, JPEG, GIF of WebP) van elke uitvoering.
   * Breedte en hoogte in pixels van elke uitvoering. Als de waarden niet worden opgegeven, wordt de volledige pixelgrootte van de oorspronkelijke afbeelding gebruikt.
   * Kwaliteit in procenten van elke JPEG en vertoning WebP.
   * MIME-typen zijn opgenomen en uitgesloten om de toepasbaarheid van een profiel te definiëren.

   ![verwerkingsprofielen, toevoegen](assets/processing-profiles-image.png)

1. Klik op **[!UICONTROL Save]**.

<!-- TBD: Update the video link when a new video is available from Tech Marketing.

The following video demonstrates the usefulness and usage of standard profile.

>[!VIDEO](https://video.tv.adobe.com/v/29832?quality=9)
-->

<!-- This image was removed per cqdoc-15624, as requested by engineering.
 ![processing-profiles-list](assets/processing-profiles-list.png) 
 -->

## Aangepast profiel en gebruiksscenario&#39;s {#custom-config}

De [!DNL Asset Compute Service] ondersteunt een groot aantal gebruiksgevallen, zoals standaardverwerking, het verwerken van Adobe-specifieke indelingen zoals Photoshop-bestanden en het implementeren van aangepaste of organisatie-specifieke verwerking. De in het verleden vereiste aanpassing van de DAM-updateworkflow voor middelen wordt automatisch verwerkt of als configuratie van verwerkingsprofielen. Als deze verwerkingsopties niet voorzien in de zakelijke behoeften, raadt de Adobe u aan om [!DNL Asset Compute Service] om de standaardmogelijkheden uit te breiden. Zie voor een overzicht [begrijpelijkheid van uitbreidbaarheid en wanneer deze wordt gebruikt](https://experienceleague.adobe.com/docs/asset-compute/using/extend/understand-extensibility.html).

>[!NOTE]
>
>Adobe raadt u aan alleen een aangepaste toepassing te gebruiken als de zakelijke vereisten niet kunnen worden vervuld met de standaardconfiguraties of het standaardprofiel.

Het kan beeld, video, document, en andere dossierformaten in verschillende vertoningen met inbegrip van duimnagels, gehaalde tekst en meta-gegevens, en archieven omzetten.

Ontwikkelaars kunnen de [!DNL Asset Compute Service] tot [aangepaste toepassingen maken](https://experienceleague.adobe.com/docs/asset-compute/using/extend/develop-custom-application.html) voor de ondersteunde gebruiksgevallen. [!DNL Experience Manager] U kunt deze aangepaste toepassingen vanuit de gebruikersinterface aanroepen met behulp van aangepaste profielen die beheerders configureren. [!DNL Asset Compute Service] steunt de volgende gevallen waarin externe diensten worden opgeroepen:

* Gebruiken [!DNL Adobe Photoshop]s [ImageCutout-API](https://developer.adobe.com/photoshop/photoshop-api-docs/) en sla het resultaat op als uitvoering.
* De systemen van de derde vraag om gegevens, bijvoorbeeld, een PIM systeem bij te werken.
* Gebruiken [!DNL Photoshop] API om verschillende uitvoeringen te genereren op basis van de Photoshop-sjabloon.
* Gebruiken [ADOBE LIGHTROOM API](https://developer.adobe.com/photoshop/photoshop-api-docs/) om de opgenomen elementen te optimaliseren en deze als uitvoeringen op te slaan.

>[!NOTE]
>
>U kunt de standaardmetagegevens niet bewerken met de aangepaste toepassingen. U kunt alleen aangepaste metagegevens wijzigen.

### Een aangepast profiel maken {#create-custom-profile}

Ga als volgt te werk om een aangepast profiel te maken:

1. Toegang voor beheerders **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Processing Profiles]**. Klik op **[!UICONTROL Create]**.
1. Klik op het tabblad **[!UICONTROL Custom]**. Klik op **[!UICONTROL Add New]**. Geef de gewenste bestandsnaam van de vertoning op.
1. Geef de volgende informatie op.

   * Bestandsnaam van elke vertoning en een ondersteunde bestandsextensie.
   * [Eindpunt-URL van een aangepaste app App Builder](https://experienceleague.adobe.com/docs/asset-compute/using/extend/deploy-custom-application.html). De app moet afkomstig zijn van dezelfde organisatie als de Experience Manager-account.
   * Serviceparameters toevoegen aan [Geef extra informatie of parameters door aan de aangepaste toepassing](https://experienceleague.adobe.com/docs/asset-compute/using/extend/develop-custom-application.html#extend).
   * MIME-typen zijn opgenomen en uitgesloten om de verwerking te beperken tot een paar specifieke bestandsindelingen.

   Klik op **[!UICONTROL Save]**.

De aangepaste toepassingen zijn zonder kop [Project App Builder](https://developer.adobe.com/app-builder/docs/overview/) apps. Uw aangepaste toepassing krijgt alle beschikbare bestanden als deze zijn ingesteld met een verwerkingsprofiel. De toepassing moet de bestanden filteren.

>[!CAUTION]
>
>Als de app App Builder en [!DNL Experience Manager] -account niet van dezelfde organisatie afkomstig zijn, de integratie werkt niet.

### Een voorbeeld van een aangepast profiel {#custom-profile-example}

Als u het gebruik van een aangepast profiel wilt illustreren, kunt u het beste een kwestie-case gebruiken om aangepaste tekst toe te passen op campagneafbeeldingen. U kunt een verwerkingsprofiel maken dat de Photoshop API gebruikt om de afbeeldingen te bewerken.

De integratie van de Dienst van de asset compute staat Experience Manager toe om deze parameters tot de douanetoepassing over te gaan gebruikend [!UICONTROL Service Parameters] veld. De aangepaste toepassing roept vervolgens de Photoshop API aan en geeft deze waarden door aan de API. U kunt bijvoorbeeld lettertypenaam, tekstkleur, tekstdikte en tekstgrootte doorgeven om aangepaste tekst toe te voegen aan campagneafbeeldingen.

<!-- TBD: Check screenshot against the interface. -->

![aangepast verwerkingsprofiel](assets/custom-processing-profile.png)

*Afbeelding: gebruiken [!UICONTROL Service Parameters] veld voor het doorgeven van toegevoegde informatie aan vooraf gedefinieerde parameters die in de aangepaste toepassing worden opgenomen. In dit voorbeeld worden de afbeeldingen bijgewerkt met `Jumanji` tekst in `Arial-BoldMT` lettertype.*

## Verwerkingsprofielen gebruiken om elementen te verwerken {#use-profiles}

Maak en pas de extra aangepaste verwerkingsprofielen toe op specifieke mappen die Experience Manager kan verwerken voor elementen die zijn geüpload naar of bijgewerkt in deze mappen. Het standaard ingebouwde standaard verwerkingsprofiel wordt altijd uitgevoerd, maar is niet zichtbaar in de gebruikersinterface. Als u een aangepast profiel toevoegt, worden beide profielen gebruikt om de geüploade elementen te verwerken.

Pas verwerkingsprofielen toe op mappen met een van de volgende methoden:

* Beheerders kunnen een definitie van het verwerkingsprofiel selecteren in **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Processing Profiles]** en gebruik **[!UICONTROL Apply Profile to Folders]** handeling. Er wordt een inhoudbrowser geopend waarmee u naar specifieke mappen kunt navigeren, deze kunt selecteren en de toepassing van het profiel kunt bevestigen.
* Gebruikers kunnen een map in de gebruikersinterface Middelen selecteren en **[!UICONTROL Properties]** handeling om het scherm met mapeigenschappen te openen, klikt u op de knop **[!UICONTROL Asset Processing]** en in de [!UICONTROL Processing Profile] selecteert u het juiste verwerkingsprofiel voor die map. Klik op **[!UICONTROL Save & Close]**.
  ![Een verwerkingsprofiel toepassen op een map op het tabblad Eigenschappen van element](assets/folder-properties-processing-profile.png)

* Gebruikers kunnen mappen of specifieke elementen in de gebruikersinterface Middelen selecteren om een verwerkingsprofiel toe te passen. Selecteer vervolgens ![pictogram voor opnieuw verwerken van elementen](assets/do-not-localize/reprocess-assets-icon.png) **[!UICONTROL Reprocess Assets]** van de opties beschikbaar op de bovenkant.

>[!TIP]
>
>Er kan slechts één verwerkingsprofiel worden toegepast op een map. Als u meer uitvoeringen wilt genereren, voegt u meer renderdefinities toe aan het bestaande verwerkingsprofiel.

Nadat een verwerkingsprofiel is toegepast op een map, worden alle nieuwe elementen die in deze map of een van de submappen van deze map zijn geüpload (of bijgewerkt), verwerkt met behulp van het extra verwerkingsprofiel dat is geconfigureerd. Deze verwerking is een aanvulling op het standaardprofiel.

>[!NOTE]
>
>Een verwerkingsprofiel dat is toegepast op een map, werkt voor de gehele structuur, maar kan worden overschreven door een ander profiel dat is toegepast op een submap. Wanneer middelen aan een omslag worden geupload, controleert de Experience Manager de bevattende omslageigenschappen voor een verwerkingsprofiel. Als er geen toepassing is, wordt gecontroleerd of er een verwerkingsprofiel van toepassing is in een bovenliggende map in de hiërarchie.

Als u wilt controleren of elementen worden verwerkt, bekijkt u een voorvertoning van de gegenereerde uitvoeringen in het dialoogvenster [!UICONTROL Renditions] in de linkerspoorstaaf. Elementvoorvertoning openen en linkerspoor openen voor toegang tot de **[!UICONTROL Renditions]** weergeven. De specifieke uitvoeringen in het verwerkingsprofiel, waarvoor het type van het specifieke element overeenkomt met de regels voor het opnemen van het MIME-type, moeten zichtbaar en toegankelijk zijn.

![aanvullende uitvoeringen](assets/renditions-additional-renditions.png)

*Afbeelding: voorbeeld van twee extra vertoningen die worden gegenereerd door een verwerkingsprofiel dat is toegepast op de bovenliggende map.*

## Nabewerkingsworkflows {#post-processing-workflows}

In een situatie waarin aanvullende verwerking van elementen vereist is die niet met de verwerkingsprofielen kan worden bereikt, kunnen extra nabewerkingsworkflows aan de configuratie worden toegevoegd. Na de verwerking kunt u volledig aangepaste verwerking toevoegen bovenop de configureerbare verwerking met behulp van asset microservices.

nabewerkingsworkflows, of [Workflow voor automatisch starten](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/configuring/auto-start-workflows.html), indien geconfigureerd, automatisch uitgevoerd door [!DNL Experience Manager] nadat de verwerking van microservices is voltooid. Het is niet nodig om handmatig starters voor werkstromen toe te voegen om de werkstromen te activeren. De voorbeelden zijn:

* Aangepaste workflowstappen om elementen te verwerken.
* Integraties om metagegevens of eigenschappen toe te voegen aan elementen van externe systemen, bijvoorbeeld product- of procesgegevens.
* Aanvullende verwerking door externe services.

Een workflowconfiguratie voor na verwerking toevoegen aan [!DNL Experience Manager]Voer de volgende stappen uit:

* Maak een of meer workflowmodellen. Deze aangepaste modellen worden *workflowmodellen voor nabewerking* in deze documentatie. Deze zijn regelmatig [!DNL Experience Manager] workflowmodellen.
* Voeg de vereiste workflowstappen toe aan deze modellen. Controleer de stappen in de standaardworkflow en voeg alle vereiste standaardstappen toe aan de aangepaste workflow. De stappen worden uitgevoerd op de middelen die op een configuratie van het werkschemamodel worden gebaseerd. Als u bijvoorbeeld automatisch slimme tags wilt toepassen bij het uploaden van elementen, voegt u de stap toe aan het aangepaste workflowmodel voor nabewerking.
* Toevoegen [!UICONTROL DAM Update Asset Workflow Completed Process] stap aan het einde. Als u deze stap toevoegt, weet de Experience Manager wanneer de verwerking eindigt en het element kan worden gemarkeerd als verwerkt, dat wil zeggen *Nieuw* wordt weergegeven op het element.
* Creeer een configuratie voor de Dienst van de Runner van het Werkschema van de Douane die toestaat om uitvoering van een model van het post-verwerkingswerkschema of door een weg (omslagplaats) of door een regelmatige uitdrukking te vormen.

Voor meer informatie over welke standaardworkflowstap kan worden gebruikt in de naverwerkingsworkflow, raadpleegt u [workflowstappen in de postverwerkingsworkflow](developer-reference-material-apis.md#post-processing-workflows-steps) in de naslaggids voor ontwikkelaars.

### Workflowmodellen voor naverwerking maken {#create-post-processing-workflow-models}

Workflowmodellen na verwerking zijn regelmatig [!DNL Experience Manager] workflowmodellen. Maak verschillende modellen als u verschillende verwerkingen nodig hebt voor verschillende opslaglocaties of elementtypen.

De verwerkingsstappen worden indien nodig toegevoegd. U kunt zowel de ondersteunde stappen als aangepaste workflowstappen gebruiken.

Zorg ervoor dat de laatste stap van elke naverwerkingwerkstroom `DAM Update Asset Workflow Completed Process`. De laatste stap helpt ervoor te zorgen dat de Experience Manager weet wanneer de activaverwerking wordt voltooid.

### Workflowuitvoering na verwerking configureren {#configure-post-processing-workflow-execution}

Nadat de assetmicroservices de verwerking van de geüploade elementen hebben voltooid, kunt u een workflow voor nabewerking definiëren om de elementen verder te verwerken. Als u naverwerking wilt configureren met behulp van workflowmodellen, kunt u een van de volgende handelingen uitvoeren:

* [Workflowmodel toepassen in mapeigenschappen](#apply-workflow-model-to-folder).
* [De service Custom Workflow Runner configureren](#configure-custom-workflow-runner-service).

#### Workflowmodel toepassen op een map {#apply-workflow-model-to-folder}

Voor gangbare gebruiksgevallen na verwerking kunt u de methode gebruiken om een workflow toe te passen op een map. Een workflowmodel toepassen in de map [!UICONTROL Properties]Voer de volgende stappen uit:

1. Maak een workflowmodel.
1. Selecteer een map en klik op **[!UICONTROL Properties]** op de werkbalk en klik vervolgens op **[!UICONTROL Assets Processing]** tab.
1. Onder **[!UICONTROL Auto-start Workflow]** selecteert u de gewenste workflow, geeft u een titel op voor de workflow en slaat u de wijzigingen op.

   ![Een nabewerkingsworkflow toepassen op een map in de eigenschappen ervan](assets/post-processing-profile-workflow-for-folders.png)

#### De service Custom Workflow Runner configureren {#configure-custom-workflow-runner-service}

U kunt de aangepaste workflowrunnerservice configureren voor de geavanceerde configuraties die niet gemakkelijk kunnen worden uitgevoerd door een workflow toe te passen op een map. Bijvoorbeeld een werkstroom die een reguliere expressie gebruikt. Adobe CQ DAM Custom Workflow Runner (`com.adobe.cq.dam.processor.nui.impl.workflow.CustomDamWorkflowRunnerImpl`) is een OSGi-service. Het verstrekt de volgende twee opties voor configuratie:

* Nabewerkingsworkflows per pad (`postProcWorkflowsByPath`): Meerdere workflowmodellen kunnen worden weergegeven op basis van verschillende repository paden. Scheid paden en modellen met een dubbele punt. Eenvoudige opslagpaden worden ondersteund. Deze toewijzen aan een workflowmodel in het dialoogvenster `/var` pad. Bijvoorbeeld: `/content/dam/my-brand:/var/workflow/models/my-workflow`.
* Workflows na verwerking op expressie (`postProcWorkflowsByExpression`): Meerdere workflowmodellen kunnen worden weergegeven op basis van verschillende reguliere expressies. Expressies en modellen moeten worden gescheiden door een dubbele punt. De reguliere expressie moet rechtstreeks naar het knooppunt Asset verwijzen en niet naar een van de uitvoeringen of bestanden. Bijvoorbeeld: `/content/dam(/.*/)(marketing/seasonal)(/.*):/var/workflow/models/my-workflow`.

Om te weten hoe te om een configuratie op te stellen OSGi, zie [implementeren voor [!DNL Experience Manager]](/help/implementing/deploying/overview.md).

#### Uitvoering van workflow na verwerking uitschakelen

Als naverwerking niet nodig is, maakt en gebruikt u een &quot;leeg&quot; workflowmodel in het dialoogvenster __Workflow automatisch starten__ selectie.

##### Het workflowmodel voor automatisch opstarten van uitgeschakelde systemen maken

1. Navigeren naar __Extra > Workflow > Modellen__
1. Selecteren __Maken > Model maken__ van de bovenste actiebalk
1. Geef een titel en naam op voor het nieuwe workflowmodel, bijvoorbeeld:
   * Titel: Auto-start Workflow uitschakelen
   * Naam: disable-auto-start-workflow
1. Selecteren __Gereed__ om het workflowmodel te maken
1. __Selecteren__ en __Bewerken__ het gemaakte workflowmodel
1. Selecteer in de werkstroommodeleditor de optie __Stap 1__ uit de modeldefinitie en deze verwijderen
1. Open de __Zijpaneel__ en selecteert u __Stappen__
1. Sleep de __DAM Update Asset Workflow voltooid__ stap in de modeldefinitie
1. Selecteer de __Pagina-informatie__ (naast de knop __Zijpaneel__ schakelen) en selecteren __Eigenschappen openen__
1. Onder de __Basis__ tab, selecteert u __Tijdelijke workflow__
1. Selecteren __Opslaan en sluiten__ van de bovenste actiebalk
1. Selecteren __Sync__ in de bovenste actiebalk
1. Sluit de Redacteur van het Model van het Werkschema

##### Het workflowmodel voor automatisch opstarten van uitgeschakelde systemen toepassen

Voer de stappen uit die in [een workflowmodel toepassen op een map](#apply-workflow-model-to-folder) en stelt de __Workflow automatisch starten uitschakelen__ als de __Workflow automatisch starten__ voor mappen hoeft u geen elementen achteraf te verwerken.

## Aanbevolen werkwijzen en beperkingen {#best-practices-limitations-tips}

* Houd rekening met uw behoeften aan alle typen uitvoeringen wanneer u workflows ontwerpt. Als u in de toekomst geen uitvoering nodig hebt, verwijdert u de aanmaakstap uit de workflow. Uitvoeringen kunnen daarna niet bulksgewijs worden verwijderd. Ongewenste vertoningen kunnen grote hoeveelheden opslagruimte innemen na langdurig gebruik van [!DNL Experience Manager]. Voor afzonderlijke elementen kunt u uitvoeringen handmatig uit de gebruikersinterface verwijderen. Voor meerdere elementen kunt u ofwel [!DNL Experience Manager] om specifieke vertoningen te verwijderen of de activa te schrappen en die opnieuw te uploaden.
* Momenteel is de ondersteuning beperkt tot het genereren van uitvoeringen. Het genereren van nieuwe elementen wordt niet ondersteund.
* De maximale bestandsgrootte voor het uitnemen van metagegevens is momenteel ongeveer 15 GB. Wanneer u zeer grote elementen uploadt, mislukt het uitnemen van metagegevens soms.

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [Elementen HTTP-API](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Middelen publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [Inleiding tot Asset compute Service](https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html).
>* [Begrijp rekbaarheid en wanneer om het te gebruiken](https://experienceleague.adobe.com/docs/asset-compute/using/extend/understand-extensibility.html).
>* [Aangepaste toepassingen maken](https://experienceleague.adobe.com/docs/asset-compute/using/extend/develop-custom-application.html).
>* [Ondersteunde MIME-typen voor verschillende gebruiksgevallen](/help/assets/file-format-support.md).

<!-- TBD: 
* How/where can admins check what's already configured and provisioned.
* How/where to request for new provisioning/purchase.
-->
