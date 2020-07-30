---
title: Elementmicroservices configureren en gebruiken voor de verwerking van bedrijfsmiddelen
description: Leer hoe u de 'cloud-native asset microservices' configureert en gebruikt om assets op schaal te verwerken.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 253231d2c9bafbba72696db36e9ed46b8011c9b3
workflow-type: tm+mt
source-wordcount: '2197'
ht-degree: 0%

---


# Middelenmicroservices en verwerkingsprofielen gebruiken {#get-started-using-asset-microservices}

<!--
* Current capabilities of asset microservices offered. If workers have names then list the names and give a one-liner description. (The feature-set is limited for now and continues to grow. So will this article continue to be updated.)
* How to access the microservices. UI. API. Is extending possible right now?
* Detailed list of what file formats and what processing is supported by which workflows/workers process.
* How/where can admins check what's already configured and provisioned.
* How to create new config or request for new provisioning/purchase.

* [DO NOT COVER?] Exceptions or limitations or link back to lack of parity with AEM 6.5.
-->

Middelenmicroservices zorgen voor schaalbare en veerkrachtige verwerking van middelen met behulp van cloudservices. Adobe beheert de services voor een optimale afhandeling van verschillende typen bedrijfsmiddelen en verwerkingsopties.

De verwerking van activa hangt van de configuratie binnen af **[!UICONTROL Processing Profiles]**, die een standaardopstelling verstrekken, en een beheerder toestaan om specifiekere configuratie van de activaverwerking toe te voegen. Beheerders kunnen de configuraties van naverwerkingsworkflows maken en onderhouden, inclusief optionele aanpassing. Door workflows aan te passen zijn uitbreidbaarheid en volledige aanpassing mogelijk.

Met Asset microservices kunt u een [groot aantal bestandstypen](/help/assets/file-format-support.md) verwerken die meer indelingen buiten de box bestrijken dan met eerdere versies van Experience Manager mogelijk is. Zo is het nu mogelijk miniatuurextractie van PSD- en PSB-indelingen uit te voeren waarvoor eerder oplossingen van derden, zoals ImageMagick, waren vereist.

<!-- Proposed DRAFT diagram for asset microservices flow - see section "asset-microservices-flow.png (asset-microservices-configure-and-use.md)" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![Een overzicht op hoog niveau van de](assets/asset-microservices-flow.png "verwerking van bedrijfsmiddelenEen overzicht op hoog niveau van de verwerking van bedrijfsmiddelen")

>[!NOTE]
>
>De hier beschreven elementverwerking vervangt het `DAM Update Asset` workflowmodel in de vorige versies van [!DNL Experience Manager]. De meeste stappen voor het genereren van standaardvertoningen en het genereren van metagegevens worden vervangen door de verwerking van de asset microservices. Eventuele resterende stappen kunnen worden vervangen door de configuratie van de workflow na verwerking.

## Opties voor middelenverwerking begrijpen {#get-started}

Met Experience Manager kunnen de volgende verwerkingsniveaus worden toegepast.

| Configuratie | Beschrijving | Gebruikte gevallen |
|---|---|---|
| [Standaardconfiguratie](#default-config) | Het is beschikbaar zoals is en kan niet worden gewijzigd. Deze configuratie biedt de mogelijkheid voor het genereren van zeer eenvoudige vertoningen. | Standaardminiaturen die worden gebruikt door de [!DNL Assets] gebruikersinterface (48, 140 en 319 px); Grote voorvertoning (webuitvoering, 1280 px); Metagegevens en tekstextractie. |
| [Standaardconfiguratie](#standard-config) | Alleen geconfigureerd door beheerders via gebruikersinterface. Biedt meer opties voor het genereren van vertoningen dan de bovenstaande standaardconfiguratie. | Wijzig de indeling en resolutie van afbeeldingen; FPO-uitvoeringen genereren. |
| [Aangepaste configuratie](#custom-config) | Door beheerders geconfigureerd via gebruikersinterface om aangepaste workers aan te roepen die complexere vereisten ondersteunen. Gebruikt een eigen cloud [!DNL Asset Compute Service]. | Zie de [toegestane gebruiksgevallen](#custom-config). |

Zie [nabewerkingsworkflows](#post-processing-workflows)voor informatie over het maken van aangepaste verwerkingsprofielen die specifiek zijn voor uw aangepaste vereisten.

## Ondersteunde bestandsindelingen {#supported-file-formats}

Middelenmicroservices bieden ondersteuning voor een groot aantal verschillende bestandsindelingen voor het genereren van uitvoeringen of het extraheren van metagegevens. Zie [ondersteunde bestandsindelingen](file-format-support.md) voor de volledige lijst.

## Standaardconfiguratie {#default-config}

Sommige standaardwaarden zijn vooraf geconfigureerd om ervoor te zorgen dat de standaarduitvoeringen die in Experience Manager worden vereist, beschikbaar zijn. De standaardconfiguratie zorgt er ook voor dat extractie van metagegevens en tekstextractie beschikbaar zijn. Gebruikers kunnen direct beginnen met het uploaden of bijwerken van elementen en de standaardverwerking is standaard beschikbaar.

Met de standaardconfiguratie, slechts wordt het meest basisverwerkingsprofiel gevormd. Een dergelijk verwerkingsprofiel is niet zichtbaar in de gebruikersinterface en u kunt het niet wijzigen. Het wordt altijd uitgevoerd om geüploade elementen te verwerken. Een dergelijk standaardverwerkingsprofiel zorgt ervoor dat de vereiste basisverwerking voor alle elementen [!DNL Experience Manager] is voltooid.

<!-- ![processing-profiles-standard](assets/processing-profiles-standard.png)
-->

## Standaardprofiel {#standard-config}

[!DNL Experience Manager] bieden mogelijkheden om specifiekere uitvoeringen voor algemene indelingen te genereren naar gelang de behoeften van de gebruiker. Een beheerder kan aanvullende informatie maken [!UICONTROL Processing Profiles] om het maken van dergelijke vertoningen te vergemakkelijken. Gebruikers wijzen vervolgens een of meer van de beschikbare profielen toe aan specifieke mappen om de extra verwerking te voltooien. De extra verwerking kan bijvoorbeeld uitvoeringen genereren voor het web, mobiele apparaten en tablets. In de volgende video ziet u hoe u de gemaakte uitvoeringen kunt maken en toepassen [!UICONTROL Processing Profiles] en hoe u deze kunt openen.

* **Breedte en hoogte** van vertoning: De specificaties voor de uitvoerbreedte en -hoogte bieden maximale grootten van de gegenereerde uitvoerafbeelding. Middelenmicroservices proberen de grootst mogelijke uitvoering te produceren, waarbij de breedte en hoogte niet groter zijn dan respectievelijk de opgegeven breedte en hoogte. De hoogte-breedteverhouding blijft behouden, dat wil zeggen hetzelfde als het origineel. Een lege waarde houdt in dat bij de verwerking van elementen de pixelafmetingen van het origineel worden gebruikt.

* **MIME-regels voor** typeintegratie: Wanneer een element van een specifiek MIME-type wordt verwerkt, wordt het MIME-type eerst gecontroleerd aan de hand van de waarde van de uitgesloten MIME-typen voor de weergavespecificatie. Als deze overeenkomt met die lijst, wordt deze specifieke uitvoering niet gegenereerd voor het element (lijst van afgewezen personen). Anders wordt het MIME-type gecontroleerd op basis van het opgenomen MIME-type en als het overeenkomt met de lijst, wordt de vertoning gegenereerd (lijst van gewenste personen).

* **Speciale FPO-uitvoering**: Bij het plaatsen van grote activa van [!DNL Experience Manager] in [!DNL Adobe InDesign] documenten wacht een creatieve beroeps een lange tijd nadat zij [activa](https://helpx.adobe.com/indesign/using/placing-graphics.html)plaatsen. Ondertussen kan de gebruiker het niet gebruiken [!DNL InDesign]. Dit onderbreekt de creatieve stroom en beïnvloedt de gebruikerservaring negatief. Met Adobe kunt u tijdelijk kleine uitvoeringen in [!DNL InDesign] documenten plaatsen. Deze kunnen later op verzoek worden vervangen door elementen met volledige resolutie. [!DNL Experience Manager] biedt uitvoeringen die alleen voor plaatsing (FPO) worden gebruikt. Deze FPO-uitvoeringen hebben een kleine bestandsgrootte maar hebben dezelfde hoogte-breedteverhouding.

Het verwerkingsprofiel kan een FPO-uitvoering (alleen voor plaatsing) bevatten. Zie de [!DNL Adobe Asset Link] documentatie [](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html) om te begrijpen of moet u het voor uw verwerkingsprofiel aanzetten. Voor meer informatie, zie de volledige documentatie [van de Verbinding van Activa van](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)Adobe.

### Standaardprofiel maken {#create-standard-profile}

Voer de volgende stappen uit om een standaardverwerkingsprofiel te maken:

1. Beheerders openen **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Processing Profiles]**. Klik op **[!UICONTROL Create]**.
1. Geef een naam op waarmee u het profiel op unieke wijze kunt identificeren wanneer u het toepast op een map.
1. Schakel op het **[!UICONTROL Standard]** tabblad FPO-uitvoeringen in om FPO-uitvoeringen te genereren **[!UICONTROL Create FPO Rendition]**. Voer een **[!UICONTROL Quality]** waarde in tussen 1 en 100.
1. Als u andere vertoningen wilt genereren, klikt u op de volgende informatie **[!UICONTROL Add New]** en geeft u deze op:

   * Bestandsnaam van elke vertoning.
   * Bestandsindeling (PNG, JPEG of GIF) van elke uitvoering.
   * Breedte en hoogte in pixels van elke uitvoering. Als de waarden niet worden opgegeven, wordt de volledige pixelgrootte van de oorspronkelijke afbeelding gebruikt.
   * Kwaliteit in procenten van elke JPEG-uitvoering.
   * MIME-typen zijn opgenomen en uitgesloten om de toepasbaarheid van een profiel te definiëren.

![verwerkingsprofielen, toevoegen](assets/processing-profiles-adding.png)

1. Klik op **[!UICONTROL Save]**.

In de volgende video ziet u het nut en het gebruik van het standaardprofiel.

>[!VIDEO](https://video.tv.adobe.com/v/29832?quality=9)

<!-- Removed per cqdoc-15624 request by engineering.
 ![processing-profiles-list](assets/processing-profiles-list.png) 
 -->

## Aangepast profiel en gebruik hoofdletters en kleine letters {#custom-config}

**TBD-items**:

* Globale cross-linking met de uitbreidbaarheidsinhoud.
* Geef aan hoe de URL van de worker moet worden opgehaald. Worker-URL voor ontwikkelings-, werkgebied- en Prod-omgevingen.
* Meningstoewijzing van de dienstparameters. Link naar compute service article.
* Herziening vanuit stroomperspectief gedeeld in Jira-ticket.

Sommige complexe situaties waarin gebruik wordt gemaakt van middelenverwerking kunnen niet worden verwezenlijkt met standaardconfiguraties omdat de behoeften van de organisaties verschillend zijn. Adobe biedt [!DNL Asset Compute Service] dergelijke gebruiksgevallen aan. Het is een schaalbare en uitbreidbare service voor het verwerken van digitale elementen. Het kan beeld, video, document en andere dossierformaten in verschillende vertoningen met inbegrip van duimnagels, gehaalde tekst &amp; meta-gegevens en archieven omzetten.

Ontwikkelaars kunnen de Asset Compute Service gebruiken om gespecialiseerde aangepaste workers te maken die omgaan met vooraf gedefinieerde, complexe gebruiksgevallen. [!DNL Experience Manager] U kunt deze douanearbeiders van het gebruikersinterface aanhalen door douaneprofielen te gebruiken die de beheerders vormen. [!DNL Asset Compute Service] ondersteunt de volgende gebruiksgevallen:

* Met Adobe Sensei aangepaste verbeterde slimme tags voor digitale elementen genereren.
* Uitsnijdmasker van een onderwerp genereren met Adobe Sensei.
* Haal metagegevens van producten op van het PIM-systeem en maak de metagegevens onderdeel van binaire elementen tijdens de opname van elementen.
* Wijzig de achtergrondkleur van een transparante afbeelding met behulp van [!DNL Adobe Photoshop] API.
* Retoucheren van een afbeelding met behulp van [!DNL Photoshop] API.
* Een afbeelding rechttrekken met behulp van [!DNL Adobe Lightroom] API.

>[!NOTE]
>
>U kunt de standaardmetagegevens niet bewerken met de aangepaste workers. U kunt alleen aangepaste metagegevens wijzigen.

### Een aangepast profiel maken {#create-custom-profile}

Ga als volgt te werk om een aangepast profiel te maken:

1. Beheerders hebben toegang **[!UICONTROL Tools > Assets > Processing Profiles]**. Klik op **[!UICONTROL Create]**.
1. Klik op het tabblad **[!UICONTROL Custom]**. Klik op **[!UICONTROL Add New]**. Geef de gewenste bestandsnaam van de vertoning op.
1. Geef de volgende informatie op en klik op **[!UICONTROL Save]**.

   * Bestandsnaam van elke vertoning en een ondersteunde bestandsextensie.
   * Eindpunt-URL van een Firefly-aangepaste app. De app moet afkomstig zijn van dezelfde organisatie als de Experience Manager-account.
   * Voeg de Parameters van de Dienst toe zoals vereist.
   * MIME-typen zijn opgenomen en uitgesloten om de toepasbaarheid van een profiel te definiëren.

![aangepast verwerkingsprofiel](assets/custom-processing-profile.png)

>[!CAUTION]
>
>Als de Firefly-app en - [!DNL Experience Manager] account niet van dezelfde organisatie afkomstig zijn, werkt de integratie niet.

## Verwerkingsprofielen gebruiken om elementen te verwerken {#use-profiles}

Maak en pas de extra aangepaste verwerkingsprofielen toe op specifieke mappen die Experience Manager kan verwerken voor elementen die zijn geüpload naar of bijgewerkt in deze mappen. Het standaard ingebouwde standaard verwerkingsprofiel wordt altijd uitgevoerd, maar is niet zichtbaar in de gebruikersinterface. Als u een aangepast profiel toevoegt, worden beide profielen gebruikt om de geüploade elementen te verwerken.

Pas verwerkingsprofielen toe op mappen met een van de volgende methoden:

* Beheerders kunnen een definitie van het verwerkingsprofiel selecteren in **[!UICONTROL Tools > Assets > Processing Profiles]** en **[!UICONTROL Apply Profile to Folder(s)]** actie gebruiken. Er wordt een inhoudbrowser geopend waarmee u naar specifieke mappen kunt navigeren, deze kunt selecteren en de toepassing van het profiel kunt bevestigen.
* Users can select a folder in the Assets user interface, use **[!UICONTROL Properties]** action to open folder properties screen, click on the **[!UICONTROL Processing Profiles]** tab, and in the popup list, select the correct processing profile for that folder. Klik op **[!UICONTROL Save & Close]** om de wijzigingen op te slaan.

>[!NOTE]
>
>Er kan slechts één verwerkingsprofiel worden toegepast op een specifieke map. Als u meer uitvoeringen wilt genereren, voegt u meer renderdefinities toe aan het bestaande verwerkingsprofiel.

Nadat een verwerkingsprofiel op een map is toegepast, worden alle nieuwe elementen die in deze map of een van de submappen van deze map zijn geüpload (of bijgewerkt), verwerkt met behulp van het extra verwerkingsprofiel dat is geconfigureerd. Deze verwerking is een aanvulling op het standaardprofiel. Als u meerdere profielen toepast op een map, worden de geüploade of bijgewerkte elementen verwerkt met elk van deze profielen.

>[!NOTE]
>
>Een verwerkingsprofiel dat is toegepast op een map, werkt voor de gehele structuur, maar kan worden overschreven door een ander profiel dat is toegepast op een submap. Wanneer middelen aan een omslag worden geupload, controleert de Experience Manager de bevattende omslageigenschappen voor een verwerkingsprofiel. Als er geen toepassing is, wordt gecontroleerd of er een verwerkingsprofiel van toepassing is in een bovenliggende map in de hiërarchie.

Gebruikers kunnen controleren of de verwerking daadwerkelijk heeft plaatsgevonden door een nieuw geüpload element te openen waarvoor de verwerking is voltooid, een voorvertoning van het element te openen en op de **[!UICONTROL Renditions]** weergave van het linkerspoor te klikken. De specifieke uitvoeringen in het verwerkingsprofiel, waarvoor het type van het specifieke element overeenkomt met de regels voor het opnemen van het MIME-type, moeten zichtbaar en toegankelijk zijn.

![aanvullende uitvoeringen](assets/renditions-additional-renditions.png)

*Afbeelding: Voorbeeld van twee extra vertoningen die worden gegenereerd door een verwerkingsprofiel dat wordt toegepast op de bovenliggende map.*

## Nabewerkingsworkflows {#post-processing-workflows}

Voor situaties waarin aanvullende verwerking van activa vereist is die niet met de verwerkingsprofielen kan worden bereikt, kunnen extra naverwerkingsworkflows aan de configuratie worden toegevoegd. Zo kunt u volledig aangepaste verwerking toevoegen bovenop de configureerbare verwerking met behulp van asset microservices.

De nabewerkingsworkflows, indien geconfigureerd, worden automatisch uitgevoerd door AEM nadat de verwerking van de microservices is voltooid. Het is niet nodig om werkstroomlanceerinrichtingen handmatig toe te voegen om ze te activeren. De voorbeelden zijn:

* Aangepaste workflowstappen om elementen te verwerken.
* Integraties om metagegevens of eigenschappen toe te voegen aan elementen van externe systemen, bijvoorbeeld product- of procesgegevens.
* Aanvullende verwerking door externe services.

Het toevoegen van een workflowconfiguratie na verwerking aan Experience Manager bestaat uit de volgende stappen:

* Maak een of meer workflowmodellen. De documenten noemen het als *post-verwerkings werkschemamodellen*, maar dat zijn regelmatige Experience Manager werkschemamodellen.
* Voeg specifieke workflowstappen toe aan deze modellen. De stappen worden uitgevoerd op de activa die op een configuratie van het werkschemamodel worden gebaseerd.
* Voeg [!UICONTROL DAM Update Asset Workflow Completed Process] stap aan het einde toe. Als u deze stap toevoegt, weet de Experience Manager wanneer de verwerking eindigt en kan het element worden gemarkeerd als verwerkt. *Nieuw* wordt dus weergegeven op het element.
* Creeer een configuratie voor de Dienst van de Runner van het Werkschema van de Douane die toestaat om uitvoering van een model van het post-verwerkingswerkschema of door een weg (omslagplaats) of door een regelmatige uitdrukking te vormen.

### Workflowmodellen voor naverwerking maken {#create-post-processing-workflow-models}

Workflowmodellen na verwerking zijn reguliere AEM workflowmodellen. Maak verschillende modellen als u verschillende verwerkingen nodig hebt voor verschillende opslaglocaties of elementtypen.

Verwerkingsstappen moeten op basis van behoeften worden toegevoegd. U kunt alle ondersteunde stappen gebruiken die beschikbaar zijn, maar ook alle aangepaste workflowstappen.

Zorg ervoor dat de laatste stap van elke naverwerkingwerkstroom is `DAM Update Asset Workflow Completed Process`. De laatste stap helpt ervoor te zorgen dat de Experience Manager weet wanneer de activaverwerking wordt voltooid.

### Workflowuitvoering na verwerking configureren {#configure-post-processing-workflow-execution}

Om de workflowmodellen na verwerking te configureren die moeten worden uitgevoerd voor elementen die in het systeem zijn geüpload of bijgewerkt nadat de verwerking van de asset microservices is voltooid, moet de Custom Workflow Runner-service worden geconfigureerd.

De dienst van de Runner van het Werkschema van de Douane (`com.adobe.cq.dam.processor.nui.impl.workflow.CustomDamWorkflowRunnerImpl`) is de dienst OSGi en verstrekt twee opties voor configuratie:

* Nabewerkingsworkflows per pad (`postProcWorkflowsByPath`): Meerdere workflowmodellen kunnen worden weergegeven op basis van verschillende repository paden. Paden en modellen moeten worden gescheiden door een dubbele punt. Eenvoudige opslagpaden worden ondersteund en moeten worden toegewezen aan een workflowmodel in het `/var` pad. Bijvoorbeeld: `/content/dam/my-brand:/var/workflow/models/my-workflow`.
* Workflows na verwerking op expressie (`postProcWorkflowsByExpression`): Meerdere workflowmodellen kunnen worden weergegeven op basis van verschillende reguliere expressies. Expressies en modellen moeten worden gescheiden door een dubbele punt. De reguliere expressie moet rechtstreeks naar het knooppunt Asset verwijzen en niet naar een van de uitvoeringen of bestanden. Bijvoorbeeld: `/content/dam(/.*/)(marketing/seasonal)(/.*):/var/workflow/models/my-workflow`.

>[!NOTE]
>
>De configuratie van de Runner van het Werkschema van de Douane is een configuratie van de dienst OSGi. Zie [opstellen aan Experience Manager](/help/implementing/deploying/overview.md) voor informatie over hoe te om een configuratie op te stellen OSGi.
>OSGi Webconsole, in tegenstelling tot in on-premise en beheerde de dienstenplaatsingen van AEM, is niet direct beschikbaar in de plaatsingen van de wolkendienst.

Zie [workflowstappen in de naverwerkingsworkflow](developer-reference-material-apis.md#post-processing-workflows-steps) in de naslaggids voor meer informatie over de standaardworkflowstap die u kunt gebruiken in de naverwerkingsworkflow.

## Aanbevolen werkwijzen en beperkingen {#best-practices-limitations-tips}

* Houd rekening met uw behoeften aan alle typen uitvoeringen wanneer u workflows ontwerpt. Als u in de toekomst geen uitvoering nodig hebt, verwijdert u de aanmaakstap uit de workflow. Uitvoeringen kunnen daarna niet bulksgewijs worden verwijderd. Ongewenste vertoningen kunnen veel opslagruimte innemen na langdurig gebruik van [!DNL Experience Manager]. Voor afzonderlijke elementen kunt u uitvoeringen handmatig uit de gebruikersinterface verwijderen. Voor meerdere elementen kunt u aanpassen [!DNL Experience Manager] om specifieke vertoningen te verwijderen of de elementen verwijderen en deze opnieuw uploaden.
