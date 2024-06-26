---
title: Hoe kunnen we Adobe Sign in een adaptieve vorm gebruiken?
description: Gebruik Adobe Sign in een adaptief formulier om ontvangers van formulieren toe te staan een formulier elektronisch te ondertekenen vanaf het apparaat en de plaats van hun keuze.
topic-tags: develop
feature: Adaptive Forms, Foundation Components
role: User, Developer
level: Intermediate
exl-id: cde9523e-5409-4edd-af0f-2c2575cc22ea
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '3071'
ht-degree: 0%

---

# Gebruiken [!DNL Adobe Sign] in een adaptieve vorm {#using-adobe-sign-in-an-adaptive-form}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/creating-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/working-with-adobe-sign.html) |
| AEM as a Cloud Service | Dit artikel |


[!DNL Adobe Sign] maakt workflows voor e-handtekeningen mogelijk voor Adaptive Forms. E-handtekeningen verbeteren werkstromen om documenten voor wettig, verkoop, loonlijst, personeelsbeheer, en meer gebieden te verwerken.

Normaal [!DNL Adobe Sign] en Adaptief Forms-scenario vult een gebruiker een adaptief formulier in om een service aan te vragen waarvoor handtekeningen van een of meer partijen zijn vereist. Een hypotheek- en creditcardaanvraag vereist bijvoorbeeld wettelijke handtekeningen van alle kredietnemers en medekredietnemers. Als u workflows voor elektronische handtekeningen wilt inschakelen voor vergelijkbare scenario&#39;s, kunt u [!DNL Adobe Sign] met een adaptief formulier. U kunt nog een paar voorbeelden gebruiken [!DNL Adobe Sign] tot:

* Sluit overeenkomsten van om het even welk apparaat met volledig geautomatiseerde voorstel, citaat, en contractprocessen.
* Voltooi processen voor menselijke hulpbronnen sneller en geef uw werknemers de digitale ervaring.
* Verkort de duur van de contractcyclus en neem sneller aan boord van uw leveranciers.
* Maak digitale workflows die algemene processen automatiseren.

[!DNL Adobe Sign] integratie met [!DNL AEM Forms] ondersteunt:

* Workflows voor ondertekening van enkelvoudige en meervoudige gebruikers
* Workflows voor opeenvolgende en gelijktijdige ondertekening
* Formulieren ondertekenen als anonieme of aangemelde gebruiker
* Dynamische ondertekeningsprocessen (integratie met [!DNL AEM Forms] Workflow)
* Verificatie via een kennisbasis, telefoon, sociale profielen en de staatsidentiteitskaart
* Rollen toewijzen aan elke ontvanger van de overeenkomst. Adobe Sign voor zakelijke en zakelijke serviceniveaus heeft de mogelijkheid om de [rollen voor ontvangers van overeenkomsten](#addsignerstoanadaptiveform).

<!-- * In-form and out-of-form signing experiences -->

## Vereisten {#prerequisites}

Voor gebruik [!DNL Adobe Sign] in een adaptieve vorm:

* Zorg ervoor dat [!DNL AEM Forms] as a Cloud Service is geconfigureerd voor gebruik van Adobe Sign. Zie voor meer informatie [Adobe Sign integreren met [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md).
* De lijst met ontvangers gereed houden. U hebt ten minste een e-mailadres voor elke ontvanger nodig.

## Configureren [!DNL Adobe Sign] voor een adaptief formulier {#configure-adobe-sign-for-an-adaptive-form}

Om te vormen [!DNL Adobe Sign] voor een adaptief formulier:

1. [Inschakelen [!DNL Adobe Sign] voor een adaptief formulier](#enableadobsignforanadaptiveform)
1. [Toevoegen [!DNL Adobe Sign] velden naar een adaptief formulier](#addadobesignfieldstoanadaptiveform)
1. [Selecteren [!DNL Adobe Sign] Cloud Service voor een adaptief formulier](#select-adobe-sign-cloud-service-and-signing-order)

1. [Toevoegen [!DNL Adobe Sign] ontvanger van een adaptief formulier](#addsignerstoanadaptiveform)
1. [Selecteer Handeling verzenden voor een adaptief formulier](#selectsubmitactionforanadaptiveform)

![Details ontvanger](assets/signer_details_new.png)

### Inschakelen [!DNL Adobe Sign] voor een adaptief formulier  {#enableadobesign}

U kunt [!DNL Adobe Sign] voor een bestaand adaptief formulier of een [!DNL Adobe Sign] Aangepast formulier ingeschakeld. Kies een van de volgende opties:

* [Een [!DNL Adobe Sign] Aangepast formulier ingeschakeld](#create-an-adaptive-form-for-adobe-sign)
* [Inschakelen [!DNL Adobe Sign] voor een bestaand adaptief formulier](#editafsign).

#### Een adaptief formulier maken voor Adobe Sign {#create-an-adaptive-form-for-adobe-sign}

Een adaptief formulier maken dat geschikt is voor ondertekenen:

1. Navigeren naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Selecteren **[!UICONTROL Create]** en selecteert u **[!UICONTROL Adaptive Form]**. Er wordt een lijst met sjablonen weergegeven. Selecteer een sjabloon en selecteer **[!UICONTROL Next]**.
1. In de **[!UICONTROL Basic]** tab:

   1. Geef de **[!UICONTROL Name]** en **[!UICONTROL Title]** voor het adaptieve formulier.

   1. Selecteer de [configuratieconsole](adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) gemaakt tijdens [integreren [!DNL Adobe Sign] with [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md).

   De configuratiecontainer bevat de [!DNL Adobe Sign] Cloud Servicen geconfigureerd voor uw omgeving. Deze services zijn beschikbaar voor selectie in de Adaptieve formuliereditor.

1. In de **[!UICONTROL Form Model]** selecteert u een van de volgende opties:

   * Als u een aangepaste formuliersjabloon hebt en een Document of Record op basis van de formuliersjabloon nodig hebt, selecteert u de optie **[!UICONTROL Associate form template as the Document of Record template]** en selecteert u een Document of Record-sjabloon. Als u deze optie gebruikt, worden alleen de velden weergegeven die zijn gebaseerd op de bijbehorende formuliersjabloon die zijn verzonden voor ondertekening. Niet alle velden van het adaptieve formulier worden weergegeven.

   * Als u geen aangepaste formuliersjabloon hebt, selecteert u de optie **[!UICONTROL Generate Document of Record]** -optie. Als u deze optie gebruikt, worden in het document dat voor ondertekening is verzonden alle velden van het adaptieve formulier weergegeven.

1. Selecteren **[!UICONTROL Create.]** Er wordt een adaptief formulier gemaakt dat geschikt is voor ondertekening. U kunt uw [!DNL Adobe Sign] velden naar het formulier en verzenden voor ondertekening.

#### Inschakelen [!DNL Adobe Sign] voor een adaptief formulier {#editafsign}

Te gebruiken [!DNL Adobe Sign] in een bestaand adaptief formulier:

1. Navigeren naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Selecteer het adaptieve formulier en selecteer **[!UICONTROL Properties]**.
1. In de **[!UICONTROL Basic]** selecteert u de [configuratieconsole](adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) gemaakt tijdens het integreren [!DNL Adobe Sign] with [!DNL AEM Forms].
1. In de **[!UICONTROL Form Mode]** selecteert u een van de volgende opties:

   * Als u een aangepaste formuliersjabloon hebt en een Document of Record op basis van de formuliersjabloon nodig hebt, selecteert u de optie **[!UICONTROL Associate form template as the Document of Record template]** en selecteert u een Document of Record-sjabloon. Als u deze optie gebruikt, worden alleen de velden weergegeven die zijn gebaseerd op de bijbehorende formuliersjabloon die zijn verzonden voor ondertekening. Niet alle velden van het adaptieve formulier worden weergegeven.

   * Als u geen aangepaste formuliersjabloon hebt, selecteert u de optie **[!UICONTROL Generate Document of Record]** -optie. Als u deze optie gebruikt, worden in het document dat voor ondertekening is verzonden alle velden van het adaptieve formulier weergegeven.

1. Selecteer **[!UICONTROL Save & Close]**. Het adaptieve formulier is ingeschakeld voor [!DNL Adobe Sign]. Nu kunt u uw [!DNL Adobe Sign] velden naar het formulier en verzenden voor ondertekening.

### Toevoegen [!DNL Adobe Sign] velden naar een adaptief formulier {#addadobesignfieldstoanadaptiveform}

[!DNL Adobe Sign] heeft verschillende velden die op een adaptief formulier kunnen worden geplaatst. Deze velden accepteren verschillende gegevenstypen, zoals handtekeningen, initialen, bedrijf of titel, en helpen bij het verzamelen van extra informatie tijdens het ondertekenen, samen met de handtekeningen. U kunt de [!DNL Adobe Sign] Component blokkeren om te plaatsen [!DNL Adobe Sign] velden op verschillende locaties in een adaptief formulier.

U voegt als volgt velden toe aan een adaptief formulier en past verschillende opties aan die betrekking hebben op deze velden:

1. Slepen en neerzetten **[!UICONTROL Adobe Sign Block]** van de componentbrowser naar het adaptieve formulier. De [!DNL Adobe Sign] De component Block bevat alle ondersteunde [!DNL Adobe Sign] velden. Standaard wordt een **[!UICONTROL Signature]** naar het adaptieve formulier.

   ![Blok ondertekenen](assets/sign_block_new.png)

   Standaard worden de [!DNL Adobe Sign] Blok is niet zichtbaar in het gepubliceerde adaptieve formulier. Deze is alleen zichtbaar in de ondertekenende documenten. U kunt de zichtbaarheid van [!DNL Adobe Sign] Blok van de eigenschappen van de [!DNL Adobe Sign] De component Blok.

   >[!NOTE]
   >
   >  * Gebruiken [!DNL Adobe Sign] blok is niet verplicht [!DNL Adobe Sign] in een adaptieve vorm. Als u het niet gebruikt [!DNL Adobe Sign] Hiermee worden velden voor de ontvangers gebundeld en toegevoegd. Vervolgens wordt het standaardhandtekeningveld onder aan de ondertekeningsdocumenten weergegeven.
   >  * Gebruiken [!DNL Adobe Sign] alleen blokkeren voor Adaptive Forms die automatisch Document of Record genereren. Als u een aangepaste XDP gebruikt voor het genereren van een document of een op een formuliersjabloon gebaseerd adaptief formulier, [!DNL Adobe Sign] blok wordt niet ondersteund.


1. Selecteer de **[!UICONTROL Adobe Sign Block]** en selecteert u de **[!UICONTROL Edit]** ![Bewerken](assets/Smock_Edit_18_N.svg) pictogram. Er worden opties weergegeven voor het toevoegen van velden en het opmaken van de weergave van een veld.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** Selecteren en toevoegen [!DNL Adobe Sign] velden. **B.** Breid uit [!DNL Adobe Sign] blokkeren naar volledige schermweergave

1. Selecteer de **[!UICONTROL Adobe Sign]** Veld ![Adobe Sign](assets/adobesign.png) pictogram. Er worden opties weergegeven om te selecteren en toe te voegen [!DNL Adobe Sign] velden.

   Breid uit **[!UICONTROL Type]** vervolgkeuzeveld om een [!DNL Adobe Sign] en selecteer Gereed ![Opslaan](assets/save_icon.svg) pictogram om het geselecteerde veld toe te voegen aan [!DNL Adobe Sign] blokkeren. De **[!UICONTROL Type]** De vervolgkeuzelijst bevat de typen Handtekening, Ontvangersinfo en Gegevensveld. [!DNL Adobe Sign] integratie met AEM [!DNL Forms] ondersteuningsvelden die worden vermeld in het dialoogvenster [!UICONTROL Type] alleen vervolgkeuzelijst. Voor gedetailleerde informatie over [!DNL Adobe Sign] velden, zie [Adobe Sign-documentatie](https://helpx.adobe.com/sign/help/field-types.html).

   ![adobe-sign-block-fields-options](assets/adobe-sign-block-fields-options.png)

   U moet een unieke naam opgeven voor een veld. U kunt ook de vereiste optie selecteren om een verplicht veld te markeren. Naast de **[!UICONTROL Name]** en **[!UICONTROL Required]** optie, sommige [!DNL Adobe Sign] veld bevat meer opties. Bijvoorbeeld masker en meerdere regels. Geef bovendien een unieke naam voor elke [!DNL Adobe Sign] veld of de velden zich in hetzelfde of een ander veld bevinden [!DNL Adobe Sign] blokken.

   Als u **[!UICONTROL Digital Signature]** in de vervolgkeuzelijst kunt u digitale handtekeningen toepassen op het adaptieve formulier:

   * Online met cloudhandtekeningen voor ondertekening met een [digitale id](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html) gehost door een vertrouwde serviceprovider.
   * Lokaal door het document te downloaden met Adobe Acrobat of Reader met een smartcard, USB-token of een op een bestand gebaseerde digitale id.

### Inschakelen [!DNL Adobe Sign] voor een adaptief formulier {#enableadobsignforanadaptiveform}

Uit de doos, [!DNL Adobe Sign] is niet ingeschakeld voor een adaptief formulier. U schakelt dit als volgt in:

1. Selecteer in de inhoudbrowser de optie **[!UICONTROL Form Container]** en selecteert u de **[!UICONTROL Configure]** ![vormen](assets/Smock_Wrench_18_N.svg) pictogram. De eigenschappenbrowser wordt geopend en de eigenschappen van de container Adaptief formulier worden weergegeven.
1. Vouw in de eigenschappenbrowser de optie **[!UICONTROL Electronic Signature]** en selecteert u de **[!UICONTROL Enable Adobe Sign]** -optie. Het maakt [!DNL Adobe Sign] voor een adaptief formulier.

### Selecteren [!DNL Adobe Sign] Cloud Service en handtekeningvolgorde {#select-adobe-sign-cloud-service-and-signing-order}

U kunt meerdere [!DNL Adobe Sign] diensten voor een AEM [!DNL Forms]. Het is raadzaam voor elke functie een aparte reeks diensten te hebben (Human Resource, Finance, enzovoort). Hierdoor kunt u ondertekende documenten gemakkelijker bijhouden en rapporteren. Een bank heeft bijvoorbeeld meerdere afdelingen. U kunt een afzonderlijke configuratie voor elke afdeling hebben voor het beter volgen van de documenten.

Een document kan ook meerdere ontvangers hebben. Een creditcardtoepassing kan bijvoorbeeld meerdere aanvragers hebben. Een bank vereist handtekeningen van alle aanvragers voordat de aanvraag wordt verwerkt. Bij scenario&#39;s met meerdere ontvangers kunt u ervoor kiezen het document in volgorde van opeenvolgende of gelijktijdige bewerkingen te ondertekenen.

Een Cloud Service en volgorde voor ondertekening selecteren:

![Cloud-service](/help/forms/assets/adobe-sign-cloud-service.png)

1. Selecteer in de inhoudbrowser de optie **[!UICONTROL Form Container]** en selecteert u de **[!UICONTROL Configure]** ![vormen](assets/Smock_Wrench_18_N.svg) pictogram. De eigenschappenbrowser wordt geopend en de eigenschappen van de container Adaptief formulier worden weergegeven.
1. Vouw in de eigenschappenbrowser de optie **[!UICONTROL Electronic Signature]** en selecteert u de **[!UICONTROL Enable Adobe Sign]** -optie. Het maakt [!DNL Adobe Sign] voor een adaptief formulier.
1. Selecteer een Cloud Service in de lijst met reeds geconfigureerde [!DNL Adobe Sign] Cloud Servicen.

   Als de **[!UICONTROL Adobe Sign Cloud Service]** lijst is leeg, volgt de [Configureren [!DNL Adobe Sign] with [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md) artikel om de dienst te vormen.

   De vervolgkeuzelijst bevat een lijst met Cloud Servicen in het dialoogvenster `global` map in Gereedschappen > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]**. Bovendien worden in de vervolgkeuzelijst ook de Cloud Servicen weergegeven die aanwezig zijn in de map die u selecteert in het dialoogvenster **[!UICONTROL Configuration Container]** wanneer u een adaptief formulier maakt.

1. Selecteer de optie om de verzendactie te configureren met **[!UICONTROL Submit the form]**. U kunt een van de volgende twee opties selecteren:
   * **Het formulier verzenden (en de overeenkomst verzenden voor ondertekening)**: Met deze optie wordt het formulier direct verzonden en vervolgens het formulier voor ondertekening verzonden naar de ontvangers.
   * **Het formulier verzenden (nadat elke ontvanger de ondertekeningsceremonie heeft voltooid)**: Met deze optie wordt Adaptive Forms alleen verzonden nadat alle ondertekenaars het ondertekeningsproces hebben voltooid. U kunt het interval vormen om de het ondertekenen status voor alle ondertekenaars te controleren. Zie voor meer informatie  [Configureren [!DNL Adobe Acrobat Sign] planner](/help/forms/adobe-sign-integration-adaptive-forms.md#configure-dnl-adobe-acrobat-sign-scheduler-to-sync-the-signing-status).

1. Selecteer de handtekeningvolgorde in het menu **[!UICONTROL Recipients can complete]** in. De ontvangers kunnen een adaptief formulier ondertekenen **[!UICONTROL Sequentially]** - een na een andere ontvanger, of **[!UICONTROL Simultaneously]** - in willekeurige volgorde.

   Op volgorde ontvangt één ontvanger de Adobe Sign-overeenkomst tegelijk. Nadat de ontvanger de toegewezen actie voltooit, wordt de overeenkomst verzonden naar de volgende ontvanger, etc.

   Tegelijkertijd ontvangen alle ontvangers de Adobe Sign-overeenkomst en kunnen zij parallel met elkaar handelen.

1. Gebruik het veld Overeenkomst-id om een bindref aan overeenkomst-id (agreementId) te koppelen. Het voegt Overeenkomst ID aan de sectie afBoundData van voorlegt gegevens voor op schema-gebaseerde vormen toe. De overeenkomst-id wordt ook toegevoegd aan het gedeelte afSubmissionInfo in de verzonden gegevens voor alle formulieren die geschikt zijn voor Adobe Sign. U kunt de overeenkomst-id gebruiken voor het bijhouden van de status van de overeenkomst met behulp van aangepaste code (aangepaste implementatie is vereist).

   >[!NOTE]
   >
   > Als een adaptief formulier wordt gemaakt met een formuliergegevensmodel (FDM), wordt het veld Overeenkomst-id weergegeven in het dialoogvenster.

1. [Ontvangers toevoegen aan een adaptief formulier](working-with-adobe-sign.md#addsignerstoanadaptiveform) en selecteer Gereed ![Opslaan](assets/save_icon.svg) om de wijzigingen op te slaan.

### Ontvangers toevoegen aan een adaptief formulier {#addsignerstoanadaptiveform}

U kunt een of meerdere ontvangers voor een Adobe Sign-overeenkomst hebben. Wanneer u een ontvanger toevoegt, kunt u ook verificatiedetails voor de ontvanger configureren en bepalen of de invuller en de ontvanger van het formulier dezelfde persoon zijn. Voer de volgende stappen uit om diverse details over een ontvanger toe te voegen en te verstrekken:

1. Selecteer in de inhoudbrowser de optie **[!UICONTROL Form Container]** en selecteert u de **[!UICONTROL Configure]** ![vormen](assets/Smock_Wrench_18_N.svg) pictogram. De eigenschappenbrowser wordt geopend met de eigenschappen van de container Adaptief formulier.
1. Vouw in de eigenschappenbrowser de optie **[!UICONTROL Electronic Signature]** en selecteert u de **[!UICONTROL Enable Adobe Sign]** -optie. Het maakt [!DNL Adobe Sign] voor een adaptief formulier.
1. Selecteer **[!UICONTROL Add Recipient]**. Hiermee voegt u een ontvanger toe aan het adaptieve formulier. U kunt meerdere ontvangers toevoegen aan een adaptief formulier. Alle ontvangers ontvangen een Adobe Sign-overeenkomst over de indiening van het adaptieve formulier.
   ![telefoongegevens](assets/recipient-settings.png)

1. Klik op de knop **[!UICONTROL Edit]** ![Bewerken](assets/Smock_Edit_18_N.svg) pictogram om de volgende informatie over de ontvanger op te geven:

   * **[!UICONTROL Title]:** Geef een titel op om een ontvanger op unieke wijze te identificeren.

   * **[!UICONTROL Is the recipient and the person filling the form same?]:** Selecteren **[!UICONTROL Yes]**, als de invuller van het formulier en de eerste ontvanger dezelfde persoon zijn. <!-- If the option is set to **No,** then do not use the signature step component in the Adaptive Form. If the form contains a Signature Step component, then the field is automatically set to Yes. -->

   * **[!UICONTROL Recipient Role]:** Selecteer de rol van een ontvanger. Adobe Sign voor zakelijke en zakelijke serviceniveaus heeft de mogelijkheid om de [rollen voor ontvangers van overeenkomsten](https://helpx.adobe.com/sign/using/set-up-signer-approver-roles.html), naast alleen de **Ondertekenaar**, om beter aan hun werkschemavereisten aan te passen.

   * **[!UICONTROL Recipient Email Address]:** Geef het e-mailadres van de ontvanger op. De ontvanger ontvangt de Adobe Sign-overeenkomst over het opgegeven e-mailadres. U kunt ervoor kiezen een e-mailadres te gebruiken dat wordt opgegeven in een formulierveld, in het gebruikersprofiel voor Experience Managers van de aangemelde gebruiker of handmatig een e-mailadres in te voeren. Het is een verplichte stap.

     >[!NOTE]
     >
     >Zorg ervoor dat het e-mailadres van de eerste ontvanger of de enige ontvanger (als er één ontvanger is) niet hetzelfde is als [!DNL Adobe Sign] account gebruikt om AEM Cloud Servicen te configureren.

   * **[!UICONTROL Recipient Authentication Method]:** Geef de methode op voor het verifiëren van een ontvanger voordat u de Adobe Sign-overeenkomst opent. U kunt kiezen tussen telefoon, kennisbasis, sociale op identiteit-gebaseerde authentificatie, en [Overheids-id](https://helpx.adobe.com/sign/using/adobesign-authentication-government-id.html) for [!DNL Adobe Acrobat Sign]. Voor [!DNL Adobe Acrobat Sign for Government] u kunt tussen telefoon en op kennis-gebaseerde authentificatie kiezen.

   >[!NOTE]
   >
   >    * Standaard biedt verificatie op basis van sociale identiteit een optie voor verificatie met behulp van Facebook, Google en LinkedIn. U kunt contact [!DNL Adobe Sign] ondersteuning om andere aanbieders van sociale authenticatie mogelijk te maken.
   >

   * **[!DNL Adobe Sign]velden die moeten worden ingevuld of ondertekend:** Selecteren [!DNL Adobe Sign] velden voor de ontvanger. Een adaptief formulier kan meerdere [!DNL Adobe Sign] velden. U kunt specifieke velden inschakelen voor een ontvanger. In het veld worden alle beschikbare [!DNL Adobe Sign] Blokken. Wanneer u een blok selecteert, worden alle velden van het blok geselecteerd. U kunt het X-pictogram gebruiken om een veld te deselecteren.

   ![gegevens van de ontvanger](assets/signer-details.png)

   De bovenstaande afbeelding heeft twee voorbeelden [!DNL Adobe Sign] Blokken: Personal-Information en Office-details

   Selecteer de ![Opslaan](assets/save_icon.svg) pictogram. De ontvanger wordt toegevoegd.

### Selecteer Handeling verzenden voor een adaptief formulier {#selectsubmitactionforanadaptiveform}

Voeg [!DNL Adobe Sign] velden naar een adaptief formulier inschakelen [!DNL Adobe Sign] vanuit formuliercontainer selecteren [!DNL Adobe Sign] Cloud Service en voeg Adobe Sign-ontvangers toe en selecteer een geschikte verzendactie voor het adaptieve formulier. Voor meer informatie over Adaptive Forms Submit Actions gaat u naar [De handeling Verzenden configureren](configuring-submit-actions.md).

Het ondertekenen en verzenden van een formulier is onafhankelijk van elkaar. Het verzenden van een adaptief formulier vindt plaats zodra een Adobe Sign-overeenkomst is gemaakt nadat een gebruiker een formulier heeft verzonden. [!DNL AEM Forms] as a Cloud Service wachten niet tot de ontvangers andere acties ondertekenen of voltooien om een adaptief formulier te verzenden. Een formulier wordt verzonden zodra een gebruiker op de knop Verzenden klikt of wanneer een stap Overzicht de samenvatting van het formulier weergeeft.

Ook, en [!DNL Adobe Sign] Met Aangepast formulier wordt de Adobe Sign-overeenkomst-id ingesloten voor het verzenden van gegevens. U kunt de overeenkomst-id gebruiken voor het bijhouden van de status van de overeenkomst met behulp van aangepaste code (aangepaste implementatie is vereist).

Adobe Sign Agreement ID (agreementId) is opgenomen in de verzendgegevens van het adaptieve formulier. Standaard is de overeenkomst-id aanwezig in de `afSubmissionInfo` knooppunt van de ingediende gegevens.

```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <afData>
      <afUnboundData>
         <data>
            <textbox1613455050902>ff</textbox1613455050902>
         </data>
      </afUnboundData>
      <afBoundData>
         <data xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/" />
      </afBoundData>
      <afSubmissionInfo>
         <lastFocusItem>guide[0].guide1[0].guideRootPanel[0].textbox1613455050902[0]</lastFocusItem>
         <stateOverrides />
         <signers>
            <signer0>
               <email />
            </signer0>
         </signers>
         <afPath>/content/dam/formsanddocuments/testsign</afPath>
         <afSubmissionTime>20210311031009</afSubmissionTime>
         <agreementId>xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx</agreementId>
      </afSubmissionInfo>
   </afData>
```

U kunt desgewenst ook een bindref aan overeenkomst-id (agreementId) koppelen. Er wordt een Overeenkomst-id toegevoegd aan de sectie afBoundData van de verzonden gegevens. In de volgende verzonden gegevens is de overeenkomst-id bijvoorbeeld gebonden aan `<userName>` knooppunt:

```xml
      <?xml version="1.0" encoding="UTF-8"?>
      <afData>
         <afUnboundData>
            <data />
         </afUnboundData>
         <afBoundData>
            <config xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
               <userName>3AAABLblqZhC2MWu7GFauKh45j_t2ih8mAtmbdIcNSl1HgQubhMJfDaDfylyN7NQiYRam_44ISKm45enIOafHqWZrdaxShf9r</userName>
               <dateOfBirth>0001-01-01</dateOfBirth>
            </config>
         </afBoundData>
         <afSubmissionInfo>
            <lastFocusItem>guide[0].guide1[0].guideRootPanel[0].projectDetails[0]</lastFocusItem>
            <stateOverrides />
            <signers>
               <signer0>
                  <email />
               </signer0>
            </signers>
            <afPath>/content/dam/formsanddocuments/testathon2021-1/gaurav/xsd-based</afPath>
            <afSubmissionTime>20210311095211</afSubmissionTime>
            <agreementId>xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx</agreementId>
         </afSubmissionInfo>
      </afData>
```

<!-- Remove when forms portal goes live
>[!NOTE]
>
>Data of the Adaptive Form is stored temporarily on Forms Portal. Adobe recommends using [custom storage for Forms Portal](/help/forms/using/configuring-draft-submission-storage.md). It ensures that the PII (personally identifiable information) data is not stored on AEM servers. 
-->

Uw ervaring voor het ondertekenen van formulieren is gereed. U kunt een voorbeeld van het formulier bekijken om de ondertekeningservaring te verifiëren. Op het gepubliceerde formulier: [!DNL Adobe Sign] Blokvelden worden weergegeven wanneer een ontvanger het formulier voor ondertekening via een e-mail ontvangt. Wanneer de **[!UICONTROL When Is the recipient and the person filling the form same?]** als deze optie is ingeschakeld en als aan de voorwaarde is voldaan, wordt de gebruiker na verzending omgeleid naar de Adobe Sign-overeenkomst en kan de gebruiker het document direct ondertekenen in plaats van te wachten tot de overeenkomst per e-mail wordt weergegeven.

## Cloud-handtekeningen configureren voor een adaptief formulier {#configure-cloud-signatures-for-an-adaptive-form}

Digitale handtekeningen op basis van cloud of externe handtekeningen zijn een nieuwe generatie digitale handtekeningen die op verschillende computers, mobiele apparaten en het web werken en voldoen aan de hoogste standaarden en waarborgen voor verificatie van ontvangers. U kunt een adaptief formulier ondertekenen met digitale handtekeningen op basis van de cloud.

Na [Adaptief formulier-eigenschappen bewerken voor Adobe Sign](working-with-adobe-sign.md#enableadobesign), voert u de volgende stappen uit om het veld voor een cloudhandtekening toe te voegen aan een adaptief formulier:

1. Slepen en neerzetten **[!UICONTROL Adobe Sign Block]** van de componentbrowser naar het adaptieve formulier. De [!UICONTROL Adobe Sign Block] alle ondersteunde componenten [!DNL Adobe Sign] velden. Standaard wordt een **[!UICONTROL Signature]** naar het adaptieve formulier.

   ![Blok ondertekenen](assets/sign-block-new.png)

1. Selecteer de **[!UICONTROL Adobe Sign Block]** en selecteert u de **[!UICONTROL Edit]** ![Bewerken](assets/Smock_Edit_18_N.svg) pictogram. Er worden opties weergegeven voor het toevoegen van velden en het opmaken van de weergave van een veld.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** Selecteren en toevoegen [!DNL Adobe Sign] velden. **B.** Breid uit [!DNL Adobe Sign] blokkeren naar volledige schermweergave

1. Selecteer de **[!UICONTROL Adobe Sign Field]** ![Adobe Sign](assets/adobesign.png) pictogram. Er worden opties weergegeven om te selecteren en toe te voegen [!DNL Adobe Sign] velden.

   Breid uit **[!UICONTROL Type]** vervolgkeuzelijst die moet worden geselecteerd **[!UICONTROL Digital Signature]** en selecteert u de **[!UICONTROL Done]** pictogram om het geselecteerde veld toe te voegen aan [!DNL Adobe Sign] blokkeren.

   ![Digitale handtekeningen](assets/digital_signatures_new.png)

   U moet een unieke naam opgeven voor een veld.

   Digitale handtekeningen toepassen op het adaptieve formulier met:

   * Cloud-handtekeningen: ondertekenen met een [digitale id](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html) gehost door een vertrouwde serviceprovider.
   * Adobe Acrobat of Reader: Download en open het document met Adobe Acrobat of Reader om het te ondertekenen met een smartcard, USB-token of digitale id op basis van een bestand.

     >[!NOTE]
     >
     > Digitale handtekening is ook van toepassing op [!DNL Adobe Acrobat Sign for Government] maar u kunt dit niet toepassen met gebruik van Cloud-handtekeningen.

   Nadat u het handtekeningveld voor de cloud aan het adaptieve formulier hebt toegevoegd, voert u de volgende stappen uit om het configuratieproces te voltooien:

   * [Adobe Sign inschakelen voor een adaptief formulier](#enableadobsignforanadaptiveform)
   * [Adobe Sign Cloud Service selecteren voor een adaptief formulier](#selectadobesigncloudserviceforanadaptiveform)
   * [Ontvangers toevoegen aan een adaptief formulier](#addsignerstoanadaptiveform)
   * [Selecteer Handeling verzenden voor een adaptief formulier](#selectsubmitactionforanadaptiveform)

### De component voor de prullenbak of overzichtsstap configureren {#configure-the-thank-you-page-or-summary-step-component}

De **[!UICONTROL Summary Step]** wordt het formulier automatisch verzonden, wordt de informatie in de aangepaste overzichtspagina ingevuld en wordt de samenvatting van het verzonden formulier weergegeven. De component SummaryStep gebruikt de volledige breedte die beschikbaar is voor het formulier. Men adviseert om geen andere component op de sectie te hebben die de Summiere component van de Stap bevat.

## Veelgestelde vragen {#frequently-asked-questions}

**V:** U kunt een adaptief formulier insluiten in een ander adaptief formulier. Kan het ingesloten adaptieve formulier worden [!DNL Adobe Sign] ingeschakeld?
**Ans:** Nee, Experience Manager Forms biedt geen ondersteuning voor het gebruik van een adaptief formulier dat een [!DNL Adobe Sign] Aangepast formulier voor ondertekening ingeschakeld

**V:** Wanneer ik een adaptief formulier maak met de geavanceerde sjabloon en dit open voor bewerking, wordt het foutbericht &quot;Elektronische handtekening of ontvangers zijn niet correct geconfigureerd&quot; weergegeven. wordt weergegeven. Hoe kan ik het foutbericht oplossen?
**Ans:** Aangepast formulier dat is gemaakt met de geavanceerde sjabloon is geconfigureerd voor gebruik [!DNL Adobe Sign]. U lost de fout op door een [!DNL Adobe Sign] cloudconfiguratie en [!DNL Adobe Sign] ontvanger voor het adaptieve formulier.

**V:** Kan ik gebruiken [!DNL Adobe Sign] tekstcodes in een statische tekstcomponent van een adaptief formulier?
**Ans:** Ja, u kunt tekstcodes in een tekstcomponent gebruiken om toe te voegen [!DNL Adobe Sign] met velden naar een document of record (alleen bij automatisch gegenereerd document of record) is adaptief formulier ingeschakeld. Ga voor meer informatie over de procedure en regels voor het maken van een tekstlabel naar [Adobe Sign-documentatie](https://helpx.adobe.com/sign/using/text-tag.html). Let ook op: Adaptive Forms biedt beperkte ondersteuning voor tekstcodes. U kunt de tekstlabels gebruiken om alleen die velden te maken die [Adobe Sign Block](working-with-adobe-sign.md#configure-cloud-signatures-for-an-adaptive-form) ondersteunt.

## Problemen oplossen {#troubleshoot}

### [!DNL Adobe Sign] fouten in overeenkomst {#adobe-sign-agreement-failures}

**Probleem**
Wanneer [!DNL Adobe Sign] de dienst wordt gevormd voor een Aangepast Vorm, ontbreekt de dienst om tot een [!DNL Adobe Sign] overeenkomst voor het onderliggende adaptieve formulier.

**Resolutie**

* Controleer de [configuratie van Adobe Sign Cloud Service](adobe-sign-integration-adaptive-forms.md) gebruikt in het adaptieve formulier.
* Zorg ervoor dat de API-toepassing ingeschakeld is [!DNL Adobe Sign] server gebruikt om te vormen [!DNL Adobe Sign] Cloud Service heeft vereiste machtigingen.
* Als u meerdere [!DNL Adobe Sign] Cloud Servicen, wijzen de **[!UICONTROL oAuth URL]** van alle diensten **[!UICONTROL Adobe Sign Shard]**.

* Afzonderlijke e-mailadressen gebruiken om te configureren [!DNL Adobe Sign] en voor de eerste of de enkele ontvanger. Het e-mailadres van de eerste ontvanger of de enige ontvanger (als er één ontvanger is) kan niet gelijk zijn aan [!DNL Adobe Sign] account gebruikt om AEM Cloud Servicen te configureren.

>[!MORELIKETHIS]
>
>* [Integreren [!DNL Adobe Sign] with [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md)
>* [Aanbevolen procedures voor het gebruik [!DNL Adobe Sign] met Adaptive Forms](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684)


## Zie ook {#see-also}

{{see-also}}