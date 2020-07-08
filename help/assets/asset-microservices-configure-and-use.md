---
title: Elementmicroservices configureren en gebruiken voor de verwerking van bedrijfsmiddelen
description: Leer hoe u de 'cloud-native asset microservices' configureert en gebruikt om assets op schaal te verwerken.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 23349f3350631f61f80b54b69104e5a19841272f
workflow-type: tm+mt
source-wordcount: '1843'
ht-degree: 3%

---


# Aan de slag met microservices voor assets {#get-started-using-asset-microservices}

<!--
* Current capabilities of asset microservices offered. If workers have names then list the names and give a one-liner description. (The feature-set is limited for now and continues to grow. So will this article continue to be updated.)
* How to access the microservices. UI. API. Is extending possible right now?
* Detailed list of what file formats and what processing is supported by which workflows/workers process.
* How/where can admins check what's already configured and provisioned.
* How to create new config or request for new provisioning/purchase.

* [DO NOT COVER?] Exceptions or limitations or link back to lack of parity with AEM 6.5.
-->

Asset microservices bieden een schaalbare en veerkrachtige verwerking van middelen met behulp van cloudservices. Adobe beheert de services voor een optimale verwerking van verschillende elementtypen en verwerkingsopties.

De verwerking van activa hangt van de configuratie binnen af **[!UICONTROL Processing Profiles]**, die een standaardopstelling verstrekken, en een beheerder toestaan om specifiekere configuratie van de activaverwerking toe te voegen. Beheerders kunnen de configuraties van naverwerkingsworkflows maken en onderhouden, inclusief optionele aanpassing. Door workflows aan te passen zijn uitbreidbaarheid en volledige aanpassing mogelijk.

Met Asset microservices kunt u een [groot aantal bestandstypen](/help/assets/file-format-support.md) verwerken die meer indelingen offline bestrijken dan in eerdere versies van Experience Manager. Zo is het nu mogelijk miniatuurextractie van PSD- en PSB-indelingen uit te voeren waarvoor eerder oplossingen van derden, zoals ImageMagick, waren vereist.

<!-- Proposed DRAFT diagram for asset microservices flow - see section "asset-microservices-flow.png (asset-microservices-configure-and-use.md)" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![Een overzicht op hoog niveau van de](assets/asset-microservices-flow.png "verwerking van bedrijfsmiddelenEen overzicht op hoog niveau van de verwerking van bedrijfsmiddelen")

>[!NOTE]
>
>De hier beschreven elementverwerking vervangt het `DAM Update Asset` workflowmodel in de vorige versies van Experience Manager. De meeste stappen voor het genereren van standaardvertoningen en het genereren van metagegevens worden vervangen door de verwerking van de asset microservices. Eventuele resterende stappen kunnen worden vervangen door de configuratie van de workflow na verwerking.

## Aan de slag met middelenverwerking {#get-started}

De verwerking van activa met activa microservices wordt pre-gevormd met een standaardconfiguratie, die ervoor zorgt dat de standaardvertoningen die door het systeem worden vereist beschikbaar zijn. Het zorgt er ook voor dat extractie van metagegevens en tekstextractie beschikbaar zijn. Gebruikers kunnen direct beginnen met het uploaden of bijwerken van elementen en de standaardverwerking is standaard beschikbaar.

Voor specifieke vereisten voor het genereren van vertoningen of het verwerken van elementen, kan een AEM-beheerder extra bestanden maken [!UICONTROL Processing Profiles]. Gebruikers kunnen een of meer van de beschikbare profielen aan specifieke mappen toewijzen om extra verwerkingstijd te krijgen. U kunt bijvoorbeeld specifieke uitvoeringen voor het web, mobiele apparaten en tablets genereren. In de volgende video ziet u hoe u de gemaakte uitvoeringen kunt maken en toepassen [!UICONTROL Processing Profiles] en hoe u deze kunt openen.

>[!VIDEO](https://video.tv.adobe.com/v/29832?quality=9)

Zie [configuraties voor de assetmicroservices](#configure-asset-microservices)voor informatie over het wijzigen van het bestaande profiel.
Zie [nabewerkingsworkflows](#post-processing-workflows)voor informatie over het maken van aangepaste verwerkingsprofielen die specifiek zijn voor uw aangepaste vereisten.

## Configuraties voor assetmicroservices {#configure-asset-microservices}

Beheerders kunnen de gebruikersinterface van de configuratie onder gebruiken om de elementmicroservices te configureren. **[!UICONTROL Tools > Assets > Processing Profiles]**

### Standaardconfiguratie {#default-config}

Met de standaardconfiguratie, slechts wordt het standaardverwerkingsprofiel gevormd. Het standaardverwerkingsprofiel is niet zichtbaar in de gebruikersinterface en u kunt het niet wijzigen. Het wordt altijd uitgevoerd om geüploade elementen te verwerken. Een standaard verwerkingsprofiel zorgt ervoor dat alle basisverwerkingsprocessen die door Experience Manager worden vereist, op alle assets zijn voltooid.

<!-- ![processing-profiles-standard](assets/processing-profiles-standard.png) -->

Het standaardverwerkingsprofiel biedt de volgende verwerkingsconfiguratie:

* Standaardminiaturen die worden gebruikt door de gebruikersinterface van Asset (48, 140 en 319 px)
* Grote voorvertoning (webuitvoering, 1280 px)
* Metagegevensextractie
* Tekst extraheren

### Ondersteunde bestandsindelingen {#supported-file-formats}

Middelenmicroservices bieden ondersteuning voor een groot aantal verschillende bestandsindelingen voor het genereren van uitvoeringen of het extraheren van metagegevens. Zie [ondersteunde bestandsindelingen](file-format-support.md) voor de volledige lijst.

### Extra verwerkingsprofielen toevoegen {#processing-profiles}

Met de **[!UICONTROL Create]** handeling kunt u aanvullende verwerkingsprofielen toevoegen.

Elke configuratie met het verwerkingsprofiel bevat een lijst met uitvoeringen. Voor elke vertoning kunt u het volgende opgeven:

* Naam van vertoning.
* Ondersteunde renditie-indeling, zoals JPEG, PNG of GIF.
* Breedte en hoogte van vertoning in pixels. Als deze optie niet is opgegeven, wordt de volledige pixelgrootte van de oorspronkelijke afbeelding gebruikt.
* Uitvoerkwaliteit van JPEG in procenten.
* MIME-typen zijn opgenomen en uitgesloten om de toepasbaarheid van een profiel te definiëren.

![verwerkingsprofielen, toevoegen](assets/processing-profiles-adding.png)

Wanneer u een nieuw verwerkingsprofiel maakt en opslaat, wordt dit toegevoegd aan de lijst met geconfigureerde verwerkingsprofielen. U kunt deze verwerkingsprofielen toepassen op mappen in de mappenhiërarchie om ze effectief te maken voor het uploaden van elementen en het verwerken van elementen.

<!-- Removed per cqdoc-15624 request by engineering.
 ![processing-profiles-list](assets/processing-profiles-list.png) -->

#### Breedte en hoogte van vertoning {#rendition-width-height}

De specificaties voor de uitvoerbreedte en -hoogte bieden maximale grootten van de gegenereerde uitvoerafbeelding. Asset microservice probeert een zo groot mogelijke uitvoering te produceren, waarbij de breedte en hoogte niet groter zijn dan respectievelijk de opgegeven breedte en hoogte. De hoogte-breedteverhouding blijft behouden, dat wil zeggen hetzelfde als het origineel.

Een lege waarde houdt in dat bij de verwerking van elementen de pixelafmetingen van het origineel worden gebruikt.

#### MIME-regels voor typeintegratie {#mime-type-inclusion-rules}

Wanneer een element van een specifiek MIME-type wordt verwerkt, wordt het MIME-type eerst gecontroleerd aan de hand van de waarde van de uitgesloten MIME-typen voor de weergavespecificatie. Als deze overeenkomt met die lijst, wordt deze specifieke uitvoering niet gegenereerd voor het element (lijst van afgewezen personen).

Anders wordt het MIME-type gecontroleerd op basis van het opgenomen MIME-type en als het overeenkomt met de lijst, wordt de vertoning gegenereerd (lijst van gewenste personen).

#### Speciale FPO-uitvoering {#special-fpo-rendition}

Wanneer u grote middelen van AEM in Adobe InDesign-documenten plaatst, moet een creatieve professional een lange tijd wachten nadat ze een middel [hebben](https://helpx.adobe.com/indesign/using/placing-graphics.html)geplaatst. Ondertussen kan de gebruiker InDesign niet gebruiken. Dit onderbreekt de creatieve stroom en beïnvloedt de gebruikerservaring negatief. Met Adobe kunt u tijdelijk kleine uitvoeringen in InDesign-documenten plaatsen. U kunt deze later op verzoek vervangen door middelen met volledige resolutie. Experience Manager biedt uitvoeringen die alleen voor plaatsing (FPO) worden gebruikt. Deze FPO-uitvoeringen hebben een kleine bestandsgrootte maar hebben dezelfde hoogte-breedteverhouding.

Het verwerkingsprofiel kan een FPO-uitvoering (alleen voor plaatsing) bevatten. Raadpleeg de [documentatie](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html) bij Adobe Asset Link als u deze nodig hebt voor uw verwerkingsprofiel. Zie de volledige documentatie [van](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)Adobe Asset Link voor meer informatie.

## Middelenmicroservices gebruiken om elementen te verwerken {#use-asset-microservices}

Maak en pas de extra aangepaste verwerkingsprofielen toe op specifieke mappen die Experience Manager kan verwerken voor elementen die zijn geüpload naar of bijgewerkt in deze mappen. Het standaard ingebouwde standaard verwerkingsprofiel wordt altijd uitgevoerd, maar is niet zichtbaar in de gebruikersinterface. Als u een aangepast profiel toevoegt, worden beide profielen gebruikt om de geüploade elementen te verwerken.

Er zijn twee manieren om verwerkingsprofielen toe te passen op mappen:

* Beheerders kunnen een definitie van het verwerkingsprofiel selecteren in **[!UICONTROL Tools > Assets > Processing Profiles]** en **[!UICONTROL Apply Profile to Folder(s)]** actie gebruiken. Er wordt een inhoudbrowser geopend waarmee u naar specifieke mappen kunt navigeren, deze kunt selecteren en de toepassing van het profiel kunt bevestigen.
* Gebruikers kunnen een map selecteren in de gebruikersinterface voor assets, de actie **[!UICONTROL Properties]** gebruiken om het scherm met mapeigenschappen te openen, op het tabblad **[!UICONTROL Processing Profiles]** klikken en in de vervolgkeuzelijst het juiste verwerkingsprofiel voor die map selecteren. De keuze wordt opgeslagen bij een actie **[!UICONTROL Save & Close]**.

>[!NOTE]
>
>Er kan slechts één verwerkingsprofiel worden toegepast op een specifieke map. Als u meer vertoningen wilt genereren, kunt u meer renditiedefinities aan het verwerkingsprofiel toevoegen.

Nadat een verwerkingsprofiel op een map is toegepast, worden alle nieuwe elementen die in deze map of een van de submappen van deze map zijn geüpload (of bijgewerkt), verwerkt met behulp van het extra verwerkingsprofiel dat is geconfigureerd. Deze extra verwerking is een aanvulling op het standaardprofiel. Als u meerdere profielen toepast op een map, worden de geüploade of bijgewerkte elementen verwerkt met elk van deze profielen.

>[!NOTE]
>
>Wanneer elementen naar een map worden geüpload, controleert Experience Manager de eigenschappen van de bovenliggende map op een verwerkingsprofiel. Als er niets is toegepast, gaat het omhoog in de mappenstructuur totdat er een toegepast verwerkingsprofiel wordt gevonden en wordt het gebruikt voor het element. Dat betekent dat een verwerkingsprofiel dat is toegepast op een map, werkt voor de gehele structuur, maar kan worden overschreven door een ander profiel dat is toegepast op een submap.

Gebruikers kunnen controleren of de verwerking daadwerkelijk heeft plaatsgevonden door een nieuw geüpload element te openen waarvoor de verwerking is voltooid, een voorvertoning van het element te openen en op de **[!UICONTROL Renditions]** weergave van het linkerspoor te klikken. De specifieke uitvoeringen in het verwerkingsprofiel, waarvoor het type van het specifieke element overeenkomt met de regels voor het opnemen van het MIME-type, moeten zichtbaar en toegankelijk zijn.

![extra-renditions](assets/renditions-additional-renditions.png)*Figure: Voorbeeld van twee extra vertoningen die worden gegenereerd door een verwerkingsprofiel dat wordt toegepast op de bovenliggende map*

## Nabewerkingsworkflows {#post-processing-workflows}

Voor situaties waarin aanvullende verwerking van activa vereist is die niet met de verwerkingsprofielen kan worden bereikt, kunnen extra naverwerkingsworkflows aan de configuratie worden toegevoegd. Zo kunt u volledig aangepaste verwerking toevoegen bovenop de configureerbare verwerking met behulp van asset microservices.

De workflows na verwerking, indien geconfigureerd, worden automatisch uitgevoerd door AEM nadat de verwerking van de microservices is voltooid. Het is niet nodig om werkstroomlanceerinrichtingen handmatig toe te voegen om ze te activeren. De voorbeelden zijn:

* Aangepaste workflowstappen om elementen te verwerken.
* Integraties om metagegevens of eigenschappen toe te voegen aan elementen van externe systemen, bijvoorbeeld product- of procesgegevens.
* Aanvullende verwerking door externe services.

Het toevoegen van een workflowconfiguratie na verwerking aan Experience Manager bestaat uit de volgende stappen:

* Maak een of meer workflowmodellen. In de documenten wordt het als workflowmodellen *voor* naverwerking genoemd, maar dit zijn standaard Experience Manager-workflowmodellen.
* Voeg specifieke workflowstappen toe aan deze modellen. De stappen worden uitgevoerd op de activa die op een configuratie van het werkschemamodel worden gebaseerd.
* Voeg [!UICONTROL DAM Update Asset Workflow Completed Process] stap aan het einde toe. Als u deze stap toevoegt, weet Experience Manager wanneer de verwerking eindigt en kan het element worden gemarkeerd als verwerkt. Dit is *Nieuw* en wordt weergegeven op het element.
* Creeer een configuratie voor de Dienst van de Runner van het Werkschema van de Douane die toestaat om uitvoering van een model van het post-verwerkingswerkschema of door een weg (omslagplaats) of door een regelmatige uitdrukking te vormen.

### Workflowmodellen voor naverwerking maken {#create-post-processing-workflow-models}

Workflowmodellen na verwerking zijn gewone AEM-workflowmodellen. Maak verschillende modellen als u verschillende verwerkingen nodig hebt voor verschillende opslaglocaties of elementtypen.

Verwerkingsstappen moeten op basis van behoeften worden toegevoegd. U kunt alle ondersteunde stappen gebruiken die beschikbaar zijn, maar ook alle aangepaste workflowstappen.

Zorg ervoor dat de laatste stap van elke naverwerkingwerkstroom is `DAM Update Asset Workflow Completed Process`. Met de laatste stap weet Experience Manager wanneer de verwerking van bedrijfsmiddelen is voltooid.

### Workflowuitvoering na verwerking configureren {#configure-post-processing-workflow-execution}

Om de workflowmodellen na verwerking te configureren die moeten worden uitgevoerd voor elementen die in het systeem zijn geüpload of bijgewerkt nadat de verwerking van de asset microservices is voltooid, moet de Custom Workflow Runner-service worden geconfigureerd.

De dienst van de Runner van het Werkschema van de Douane (`com.adobe.cq.dam.processor.nui.impl.workflow.CustomDamWorkflowRunnerImpl`) is de dienst OSGi en verstrekt twee opties voor configuratie:

* Nabewerkingsworkflows per pad (`postProcWorkflowsByPath`): Meerdere workflowmodellen kunnen worden weergegeven op basis van verschillende repository paden. Paden en modellen moeten worden gescheiden door een dubbele punt. Eenvoudige opslagpaden worden ondersteund en moeten worden toegewezen aan een workflowmodel in het `/var` pad. Bijvoorbeeld: `/content/dam/my-brand:/var/workflow/models/my-workflow`.
* Workflows na verwerking op expressie (`postProcWorkflowsByExpression`): Meerdere workflowmodellen kunnen worden weergegeven op basis van verschillende reguliere expressies. Expressies en modellen moeten worden gescheiden door een dubbele punt. De reguliere expressie moet rechtstreeks naar het knooppunt Asset verwijzen en niet naar een van de uitvoeringen of bestanden. Bijvoorbeeld: `/content/dam(/.*/)(marketing/seasonal)(/.*):/var/workflow/models/my-workflow`.

>[!NOTE]
>
>De configuratie van de Runner van het Werkschema van de Douane is een configuratie van de dienst OSGi. Zie [opstellen aan Experience Manager](/help/implementing/deploying/overview.md) voor informatie over hoe te om een configuratie op te stellen OSGi.
>OSGi-webconsole is, in tegenstelling tot on-premise en beheerde services-implementaties van AEM, niet rechtstreeks beschikbaar in de cloudservice-implementaties.

Zie [workflowstappen in de naverwerkingsworkflow](developer-reference-material-apis.md#post-processing-workflows-steps) in de naslaggids voor meer informatie over de standaardworkflowstap die u kunt gebruiken in de naverwerkingsworkflow.

## Aanbevolen werkwijzen en beperkingen {#best-practices-limitations-tips}

* Houd rekening met uw behoeften aan alle typen uitvoeringen wanneer u workflows ontwerpt. Als u in de toekomst geen uitvoering nodig hebt, verwijdert u de aanmaakstap uit de workflow. Uitvoeringen kunnen daarna niet bulksgewijs worden verwijderd. Ongewenste vertoningen kunnen veel opslagruimte innemen na langdurig gebruik van [!DNL Experience Manager]. Voor afzonderlijke elementen kunt u uitvoeringen handmatig uit de gebruikersinterface verwijderen. Voor meerdere elementen kunt u aanpassen [!DNL Experience Manager] om specifieke vertoningen te verwijderen of de elementen verwijderen en deze opnieuw uploaden.
