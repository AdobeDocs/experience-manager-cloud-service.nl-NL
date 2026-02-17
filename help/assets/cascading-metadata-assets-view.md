---
title: Trapsgewijze metagegevens
description: In dit artikel wordt beschreven hoe u trapsgewijze metagegevens voor elementen in de weergave Elementen definieert.
feature: Metadata
role: Admin, User
source-git-commit: 2bb309afc372fe18ce274a2813ed25cba22eb4de
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 0%

---


# Cascading Metadata Assets View{#cascading-metadata-assets-view}

Wanneer gebruikers de metagegevens van een element vastleggen, verschaffen ze informatie in de verschillende beschikbare velden. U kunt specifieke metagegevensvelden of veldwaarden weergeven die afhankelijk zijn van de opties die in de andere velden zijn geselecteerd. Een dergelijke voorwaardelijke weergave van metagegevens wordt trapsgewijze metagegevens genoemd. Met andere woorden, u kunt een afhankelijkheid maken tussen een bepaald metagegevensveld/een bepaalde waarde en een of meer velden en/of hun waarden.

Gebruik Forms voor metagegevens om regels voor de weergave van trapsgewijze metagegevens te definiëren. Als uw metagegevensformulier bijvoorbeeld een elementtypeveld bevat, kunt u een relevante set velden definiëren die moet worden weergegeven op basis van het type element dat de gebruiker selecteert.

Hier volgen enkele gebruiksgevallen waarvoor u trapsgewijze metagegevens kunt definiëren:

* Indien een gebruikerslocatie is vereist, relevante plaatsnaam weergeven op basis van de keuze van het land en de staat van de gebruiker.
* Laad relevante merknamen in een lijst op basis van de door de gebruiker gekozen productcategorie.
* Schakel de zichtbaarheid van een bepaald veld in of uit op basis van de waarde die in een ander veld is opgegeven. Geef bijvoorbeeld afzonderlijke velden voor het verzendadres weer als de gebruiker de verzending op een ander adres wil laten uitvoeren.
* Wijs een veld aan als verplicht op basis van de waarde die in een ander veld is opgegeven.
* Opties wijzigen die voor een bepaald veld worden weergegeven op basis van de waarde die in een ander veld is opgegeven.
* Stel de standaardwaarde voor metagegevens in een bepaald veld in op basis van de waarde die in een ander veld is opgegeven.

>[!IMPORTANT]
>
>De functie Trapsgewijze metagegevens is beschikbaar als functies voor beperkte beschikbaarheid. U kunt [&#x200B; tot stand brengen en een geval van de Steun van de Klant van Adobe voorleggen &#x200B;](https://helpx.adobe.com/nl/enterprise/using/support-for-experience-cloud.html) om het voor uw plaatsing toe te laten.

## Metagegevens met trapsgewijze opmaak configureren in [!DNL Experience Manager] {#configure-cascading-metadata-in-aem}

Overweeg een scenario waarin u trapsgewijze metagegevens wilt weergeven op basis van het geselecteerde type element. Bijvoorbeeld-

* Geef voor een video toepasselijke velden weer, zoals indeling, codec, duur, enzovoort.
* Voor een Word- of PDF-document geeft u velden weer, zoals het aantal pagina&#39;s, de auteur, enzovoort.

Een vervolgkeuzelijst met de naam `Image` wordt gebruikt als voorbeeld voor het indelen van bestanden op basis van het afbeeldingstype. Het vervolgkeuzemenu bevat opties voor ondersteunde afbeeldingsextensies (zoals JPG/JPEG, GIF, enz.). Om ervoor te zorgen dat de gegevens consistent blijven en om te voorkomen dat niet-ondersteunde indelingen worden geselecteerd of verwerkt, wordt een validatieregel toegepast op dit veld. De regel evalueert de geselecteerde dropdown waarde en handhaaft beperkingen die zich aan de toegelaten beeldformaten richten.

>[!IMPORTANT]
>
>U kunt alleen regels maken op basis van vervolgkeuzelijsten.

Geef de copyrightinformatie, ongeacht het gekozen elementtype, weer als een verplicht veld. U kunt de [&#x200B; vooraf bepaalde meta-gegevenscomponenten &#x200B;](metadata-assets-view.md#property-components) gebruiken en [&#x200B; meta-gegevens toewijzen aan een omslag &#x200B;](metadata-assets-view.md#assign-metadata-form-folder).

### Metagegevens van Forms samenstellen {#build-metadata-schema-forms}

Bekijk de onderstaande stappen om een nieuw metagegevensformulier te maken:

1. Selecteer het [!DNL Experience Manager] -logo en ga naar **[!UICONTROL Settings]** > **[!UICONTROL Metadata Forms]** > **[!UICONTROL Create]** .

1. Selecteer in het vervolgkeuzemenu **[!UICONTROL Type]** het juiste formuliertype: **[!UICONTROL File]** , **[!UICONTROL Folder]** of **[!UICONTROL Collection]** .

1. Geef de titel van het metagegevensformulier op in het veld **[!UICONTROL Name]** .

1. U kunt ook een bestaande sjabloon voor metagegevens kiezen in het vervolgkeuzemenu **[!UICONTROL Choose from existing form template]** .

1. Er wordt een leeg formulier met metagegevens weergegeven. Voeg een nieuw tabblad toe.

   ![&#x200B; UI van de Vorm van meta-gegevens &#x200B;](assets/metadata-form-ui.png)

   * **A:** Schakelaar tussen [!UICONTROL Edit] of [!UICONTROL Preview]
   * **B:** [&#x200B; Componenten van de Vorm van Meta-gegevens &#x200B;](metadata-assets-view.md#property-components)
   * **C:** Schakelaar aan andere Vorm van Metagegevens
   * **D:** voeg een nieuw lusje toe
   * **E:** Canvas
   * **F:** Algemene montages voor de geselecteerde component
   * **G:** het lusje van Regels
   * **H:** Eigenschappen van de Component

Bekijk deze video om de opeenvolging van stappen, [&#x200B; Meta-gegevens Forms van de Opstelling &#x200B;](https://video.tv.adobe.com/v/341275) te bekijken.

### Een bestaand metagegevensformulier wijzigen {#modify-existing-metadata-form}

Voer de volgende stappen uit om een bestaand metagegevensformulier te wijzigen:

1. Open een bestaande Vorm van Meta-gegevens en navigeer aan [&#x200B; vooraf bepaalde componenten &#x200B;](metadata-assets-view.md#property-components) die u in de vorm wilt toevoegen en de elementen op uw canvas laten vallen.

   In overeenstemming met het **gebruiksgeval van het Beeld 0&rbrace; &lbrace;, voeg een dropdown gebied toe om beeldactivatypes te bepalen.** Specificeer de naam en bezitspad in **Montages**, en vormen naar keuze het gebied als **[!UICONTROL Read-Only]** of **[!UICONTROL Multiple Selections]**.

1. Geef de opties voor de toetswaarden voor het vervolgkeuzemenu op door deze handmatig in te voeren, een JSON-pad op te geven of een CSV-bestand te importeren.

   * Als u de waarden handmatig wilt opgeven, selecteert u **[!UICONTROL Add Manually]** onder **[!UICONTROL Choices]** en klikt u `Add` . Vervolgens geeft u het label en de waarde van de optie op. Geef bijvoorbeeld de elementtypen Video, PDF en Afbeelding op.

     ![&#x200B; Type van Activa van het Beeld &#x200B;](assets/image-asset-type.png)

   * Als u waarden wilt ophalen van een JSON-pad, selecteert u **[!UICONTROL Add through JSON Path]** en geeft u het pad van het JSON-bestand op.

     >[!NOTE]
     >
     >Sla het JSON-bestand op een gedeelde locatie op die toegankelijk is voor alle DAM-editors en -auteurs.

     ![&#x200B; voeg Keuzen door weg JSON &#x200B;](assets/add-json-choices.png) toe

   * Als u de waarden dynamisch van een CSV-bestand wilt ophalen, klikt u op **[!UICONTROL Import CSV]** en geeft u het pad van het CSV-bestand op. [!DNL Experience Manager] haalt de sleutel-waardeparen in real time op wanneer het formulier aan de gebruiker wordt getoond.

     ![&#x200B; voeg Keuzen door CSV &#x200B;](assets/import-csv-choices.png) toe

   >[!NOTE]
   > 
   >U kunt de opties uit een CSV-bestand niet importeren en ze handmatig bewerken, omdat beide opties elkaar uitsluiten.

1. Als u een afhankelijkheid tussen het afbeeldingsveld en andere velden wilt maken, selecteert u het afhankelijke veld en opent u het tabblad **[!UICONTROL Rules]** . Elke component ondersteunt een specifieke set regels. In dit geval worden de opties voor Type afbeeldingselement gebruikt om de regellogica te definiëren.

   <!--![Image Asset Type Rule](assets/image-asset-type-rule.png)-->

   <!--![rule tab](assets/rule-tab.png)-->

1. Kies onder **[!UICONTROL Required]** de optie **[!UICONTROL Required based on new rule]** . Klik ![&#x200B; plus pictogram &#x200B;](assets/do-not-localize/aem_assets_add_icon.png) om een nieuwe regel toe te voegen.

   ![&#x200B; regel &#x200B;](assets/image-required-rule1.png)

   In het huidige geval van gebruik is het veld Type element vereist als de indeling voor afbeeldingselementen JPG/JPEG, PNG, GIF, TIFF of WEBP is. Bovendien, klik ![&#x200B; uitgeven pictogram &#x200B;](assets/do-not-localize/edit.svg) om de regel opnieuw te bepalen of ![&#x200B; schrappingspictogram &#x200B;](assets/do-not-localize/delete.svg) te klikken om de bepaalde regel te schrappen.

   ![&#x200B; regel &#x200B;](assets/image-required-rule2.png)

1. Kies onder **[!UICONTROL Visibility]** de optie **[!UICONTROL Visible, based on new rule]** . Klik ![&#x200B; plus pictogram &#x200B;](assets/do-not-localize/aem_assets_add_icon.png) om een nieuwe regel toe te voegen.

   >[!NOTE]
   >
   >U kunt de voorwaarde **[!UICONTROL Requirement]** en **[!UICONTROL Visibility]** onafhankelijk van elkaar toepassen.

   ![&#x200B; regel &#x200B;](assets/image-visible-rule1.png)

   In het huidige geval van gebruik is het veld Type element zichtbaar wanneer de indeling voor afbeeldingselementen JPG/JPEG, PNG of GIF is. Bovendien, klik ![&#x200B; uitgeven pictogram &#x200B;](assets/do-not-localize/edit.svg) om de regel opnieuw te bepalen of ![&#x200B; schrappingspictogram &#x200B;](assets/do-not-localize/delete.svg) te klikken om de bepaalde regel te schrappen.

   ![&#x200B; regel &#x200B;](assets/image-visible-rule2.png)

1. Selecteer **[!UICONTROL Choices based on rule]** om een afhankelijkheid te maken en een regel te definiëren. Klik ![&#x200B; plus pictogram &#x200B;](assets/do-not-localize/aem_assets_add_icon.png) om een nieuwe regel toe te voegen.

   ![&#x200B; regel &#x200B;](assets/image-choices-rule1.png)

   Om op regel-gebaseerde keuzen voor het drop-down van het Type van Activa te vormen, creeer een regel en plaats Beeld als afhankelijk gebied. Definieer vervolgens de weergavewaarden voor elke afbeeldingsindeling door Afbeelding te selecteren voor JPG/JPEG, PNG, GIF en TIFF en Video te selecteren voor WEBP. Alleen de gewenste waarden worden voor elke indeling gecontroleerd om de relevante opties dynamisch weer te geven. Bovendien, klik ![&#x200B; uitgeven pictogram &#x200B;](assets/do-not-localize/edit.svg) om de regel opnieuw te bepalen of ![&#x200B; schrappingspictogram &#x200B;](assets/do-not-localize/delete.svg) te klikken om de bepaalde regel te schrappen.

   ![&#x200B; regel &#x200B;](assets/image-choices-rule2.png)

1. Herhaal op dezelfde manier de stappen om afhankelijkheid te maken tussen de andere elementen, zoals PDF en Word in het veld [!UICONTROL Asset Type] en velden zoals [!UICONTROL Page Count] en [!UICONTROL Author] .

1. Klik op **[!UICONTROL Save]**. Pas het metagegevensformulier toe op een map.

1. Navigeer naar de map waarop u het metagegevensformulier hebt toegepast en open de eigenschappenpagina van een element. Afhankelijk van uw keuze in het veld Type element worden relevante trapsgewijze metagegevensvelden weergegeven.

   ![&#x200B; Cascading Metadata de Output van de Vorm &#x200B;](assets/cascading-metadata-form-output.png)

>[!NOTE]
> 
>Om vroege toegang tot de Cascading Meta-gegevens op uw rekening van de Mening van Assets te krijgen, [&#x200B; creeer en verzend een geval van de Steun van de Klant van Adobe &#x200B;](https://helpx.adobe.com/nl/enterprise/using/support-for-experience-cloud.html).

## Volgende stappen {#next-steps}

* [&#x200B; bekijk een video om meta-gegevensvormen in de mening van Assets te beheren &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/assets-essentials/configuring/metadata-forms.html?lang=nl-NL)

* Feedback geven op het product met de optie [!UICONTROL Feedback] die beschikbaar is in de gebruikersinterface van de Assets-weergave

* Verstrek documentatie terugkoppelt gebruikend [!UICONTROL Edit this page] ![&#x200B; uitgeeft de pagina &#x200B;](assets/do-not-localize/edit-page.png) of [!UICONTROL Log an issue] ![&#x200B; creeer een kwestie GitHub &#x200B;](assets/do-not-localize/github-issue.png) beschikbaar op juiste sidebar

* De Zorg van de Klant van het contact [&#128279;](https://experienceleague.adobe.com/nl?support-solution=General#support)

