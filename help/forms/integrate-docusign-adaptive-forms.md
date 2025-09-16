---
title: Hoe te om DocuSign met een Aangepast Vorm te integreren?
description: Leer hoe u DocuSign met een adaptief formulier kunt gebruiken om e-handtekeningen te verzamelen.
exl-id: fb2e75d6-e454-4999-a079-f663af79051f
feature: Adaptive Forms, Acrobat Sign
role: User, Developer
source-git-commit: ab84a96d0e206395063442457a61f274ad9bed23
workflow-type: tm+mt
source-wordcount: '1413'
ht-degree: 0%

---

# DocuSign gebruiken met een adaptief formulier {#integrate-aem-forms-with-DocuSign}

DocuSign is een belangrijke oplossing voor e-handtekeningen. U kunt deze gebruiken om een overeenkomst elektronisch te ondertekenen. U kunt DocuSign integreren met een adaptief formulier. Hiermee kunt u een adaptief formulier voor e-handtekeningen naar meerdere ontvangers verzenden. Met e-handtekeningen kunt u:

- Sluit overeenkomsten van om het even welk apparaat met volledig geautomatiseerde voorstel, citaat, en contractprocessen.
- Voltooi processen voor menselijke hulpbronnen sneller en geef uw werknemers de digitale ervaring.
- Verkort de duur van de contractcyclus en neem sneller aan boord van uw leveranciers.

AEM Forms as a Cloud Service verstrekt a [ douane voorlegt actie voor DocuSign ](#deploy-custom-submit-action). Met de verzendactie kunt u de adaptieve formulieren voor e-handtekeningen verzenden met DocuSign API&#39;s.

| U kunt ook een adaptief formulier elektronisch ondertekenen met de Adobe-oplossing voor e-handtekeningen, Adobe Sign. AEM Forms is veel beter geïntegreerd met Adobe Sign en biedt veel fijnere besturingselementen, zoals sequentiële en parallelle ondertekening, meerdere verificatiemethoden, ervaring met het ondertekenen van formulieren en meer. Voor meer informatie, zie [ Gebruikend het Teken van Adobe in een AanpassingsVorm ](working-with-adobe-sign.md). |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

## Vereisten {#prerequisites}

Voor de integratie van DocuSign met AEM Forms is het volgende vereist:

- Een DocuSign [ ontwikkelaarsrekening ](https://developers.docusign.com/platform/account/)
- Een DocuSign-toepassing
- Referenties (client-id en clientgeheim) van DocuSign API-toepassing.
- [ Eigen voorlegt actie en de dienst van de Wolk voor DocuSign ](https://github.com/adobe/aem-forms-docusign-sample)
- (Alleen voor de lokale ontwikkelomgeving) [ Instellingsdocument van Record ](setup-local-development-environment.md#docker-microservices) .

## Aangepaste verzendactie en cloudservice voor DocuSign configureren {#deploy-custom-submit-action}

AEM Forms as a Cloud Service biedt een aangepaste verzendactie voor DocuSign. Met de verzendactie kunt u de adaptieve formulieren voor e-handtekeningen verzenden met DocuSign API&#39;s. De code voor douane legt actie voor is beschikbaar op [ AEM Forms steekproeven openbare git bewaarplaats ](https://github.com/adobe/aem-forms-docusign-sample). U kunt de code implementeren zoals deze zich in uw AEM Forms-omgeving bevindt of deze aanpassen aan de vereisten van uw organisatie.

Voer de volgende stappen uit om uit-van-de-doos aangepaste verzendactie en DocuSign Cloud Service te vormen:

1. [ Kloon uw project van AEM Forms as a Cloud Service ](setup-local-development-environment.md#forms-cloud-service-local-development-environment) of creeer een [!DNL Experience Manager Forms] als [!DNL Cloud Service] project dat op [ wordt gebaseerd AEM Archetype 27 ](https://github.com/adobe/aem-project-archetype) of later. Een [!DNL Experience Manager Forms] maken als een [!DNL Cloud Service] -project op basis van AEM Archetype:
   </br> Open de opdrachtregel en voer de onderstaande opdracht uit om een [!DNL Experience Manager Forms] as a Cloud Service-project te maken:

   ```shell
   mvn -B archetype:generate -DarchetypeGroupId=com.adobe.aem -DarchetypeArtifactId=aem-project-archetype -DarchetypeVersion=27 -DaemVersion="cloud" -DappTitle="My Site" -DappId="mysite" -DgroupId="com.mysite" -DincludeForms="y"
   ```

   Wijzig ook `appTitle` , `appId` en `groupId` in de bovenstaande opdracht om uw omgeving te weerspiegelen.

1. Kloon de [ aem-vormen-steekproeven ](https://github.com/adobe/aem-forms-docusign-sample) bewaarplaats. Deze opslagplaats bevat een aangepaste verzendactie voor DocuSign en configuratiegegevens om verbinding te maken met de DocuSign-server.

1. Open het AEM Forms as a Cloud Service-project dat in Stap 1 is gemaakt voor bewerking in IDE van uw keuze.

1. Open het `[AEM Forms as a Cloud Service project]\pom.xml` -bestand om het te bewerken en breng de volgende wijzigingen aan:

   1. Voeg de volgende tekst toe aan het einde van de tag `<properties>` :

      ```shell
      <repository.location>maven_repository</repository.location>
      ```

   1. Voeg de volgende tekst toe aan het einde van de tag `<repositories>` :

      ```shell
       <repository>
          <id>project-repository</id>
          <url>file://${project.basedir}/${repository.location}</url>
       </repository>
      ```

      Als er geen tag `<repositories>` is, maakt u de tag onder de tag `<properties>` .

   1. Voeg de volgende tekst toe aan het einde van de tag `<dependencyManagement>` :

      ```shell
       <dependency>
         <groupId>com.adobe.aemforms.samples</groupId>
         <artifactId>forms.integration.docusign.all</artifactId>
         <type>zip</type>
         <version>1.0.0</version>
       </dependency>
      ```

1. Voer de volgende stappen uit in het `all/pom.xml` -bestand dat beschikbaar is in de Cloud Service-projectmap:

   1. Voeg de volgende tekst toe aan het einde van de tag `<embeddeds>` :

      ```shell
       <embedded>
          <groupId>com.adobe.aemforms.samples</groupId>
          <artifactId>forms.integration.docusign.all</artifactId>
          <type>zip</type>
          <target>/apps/moonlightprodprogram-vendor-packages/application/install</target>
       </embedded>
      ```

   1. Voeg de volgende tekst toe aan het einde van de tag `<dependencies>` :

      ```shell
       <dependency>
          <groupId>com.adobe.aemforms.samples</groupId>
          <artifactId>forms.integration.docusign.all</artifactId>
          <type>zip</type>
       </dependency>
      ```

1. Open de opdrachtprompt, navigeer naar `aem-forms-samples\forms-integration-docusign` (gekloond in stap 3) en voer de volgende opdracht uit:

   ```shell
   mvn clean install -Dinstall.dir="<AEM Forms as a Cloud Service project path>/maven_repository"
   ```

   `<AEM Forms as a Cloud Service project path>` verwijst naar de naam van de map die in stap 1 van deze procedure is gemaakt.

1. Implementeer het project in uw lokale ontwikkelomgeving. U kunt het volgende bevel gebruiken om aan uw lokale ontwikkelomgeving op te stellen

   `mvn -PautoInstallPackage clean install`

   Na het uitvoeren van deze stappen, kunt u een nieuwe douane bekijken voorlegt actie [ met elektronische handtekeningen DocuSign ](#enabledocusign) beschikbaar in de lijst van voorstellingsopties voor een adaptieve vorm en de configuratie van de a [ de wolkendienst DocuSign ](#configure-docusign-with-aem-forms) in uw lokale ontwikkelomgeving.

1. Compileer en [ stel de code aan uw  [!DNL AEM Forms]  milieu van as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#customer-releases) op.

## [!DNL DocuSign] integreren met [!DNL AEM Forms] {#configure-docusign-with-aem-forms}

Voer de volgende stappen uit nadat aan de voorwaarden is voldaan om [!DNL DocuSign] te integreren met [!DNL AEM Forms] in de instantie Auteur.

1. Navigeer aan **[!UICONTROL Tools]** ![ hamer ](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL DocuSign]** en selecteer een omslag om de configuratie te ontvangen.

1. Selecteer op de configuratiepagina **[!UICONTROL Create]** om [!DNL DocuSign] -configuratie te maken in AEM Forms.
1. Geef op het tabblad **[!UICONTROL General]** van de **[!UICONTROL Create DocuSign Configuration]** -pagina een **[!UICONTROL Name]** voor de configuratie op en selecteer **[!UICONTROL Next]** . U kunt desgewenst een **[!UICONTROL Title]** opgeven.

1. Kopieer de URL in het huidige browservenster naar een laptop. De URL is vereist als u de [!DNL DocuSign] -toepassing in een latere stap met [!DNL AEM Forms] wilt configureren.

1. Configureer OAuth-instellingen voor de [!DNL DocuSign] -toepassing:

   1. Open een browser venster en teken binnen aan uw [!DNL DocuSign] [ ontwikkelaarsrekening ](https://admindemo.docusign.com/apps-and-keys).
   1. Open de toepassing die voor [!DNL AEM Forms] is geconfigureerd.
   1. Voeg in het vak **[!UICONTROL Redirect URI]** de URL toe die u in de vorige stap hebt gekopieerd en klik op **[!UICONTROL Save]** .
   1. Noteer de integratietoetsen en de geheime toetsen.

   Voor geleidelijke informatie om montages OAuth voor een [!DNL DocuSign] toepassing te vormen en de sleutels te verkrijgen, zie [ montages van Auth voor de 2} de ontwikkelaarsdocumentatie van de toepassing {vormen.](https://support.docusign.com/guides/ndse-admin-guide-api-and-keys)

1. Ga terug naar de **[!UICONTROL Create DocuSign Configuration]** pagina. Op het tabblad **[!UICONTROL Settings]** vermeldt het veld **[!UICONTROL OAuth URL]** de volgende standaard-URL:

   `https://account-d.docusign.com/oauth/auth`

1. Geef de opties **[!UICONTROL Client ID]** (DocuSign Integration Key) en **[!UICONTROL Client Secret]** (DocuSign Secret Key) op.

1. Selecteer **[!UICONTROL Connect to DocuSign]**. Geef bij de aanwijzing voor referenties de gebruikersnaam en het wachtwoord op van het account dat wordt gebruikt bij het maken van de [!DNL DocuSign] -toepassing. Klik op `your developer account` wanneer u wordt gevraagd de toegang voor **[!UICONTROL Allow Access]** te bevestigen. Als de gegevens juist zijn, wordt een succesbericht weergegeven.

1. Selecteer **[!UICONTROL Create]** om de [!DNL DocuSign] -configuratie te maken.

1. Selecteer de configuratie en klik op **[!UICONTROL Publish]** , selecteer de configuratie en klik op **[!UICONTROL Publish]** . De configuratie wordt in overeenkomende publicatieomgevingen gerepliceerd.

1. Herhaal alle bovenstaande stappen op uw ontwikkelaar-, werkgebied- en productieinstanties (afhankelijk van wat er nog over is) om het configureren van [!DNL DocuSign] met [!DNL AEM Forms] voor uw omgeving te voltooien.

Nu is uw AEM Forms-omgeving geconfigureerd voor gebruik van DocuSign. Zorg ervoor dat u de configuratiecontainer die voor de Cloud Service wordt gebruikt, toevoegt aan alle Adaptive Forms die voor [!DNL DocuSign] wordt ingeschakeld. U kunt een configuratiecontainer opgeven met de eigenschappen van een adaptief formulier.

### [!DNL DocuSign] gebruiken in een adaptief formulier {#enabledocusign}

U kunt [!DNL DocuSign] inschakelen voor een bestaand adaptief formulier of een [!DNL DocuSign] -compatibel adaptief formulier maken. Kies een van de volgende opties:

- [Creeer een  [!DNL DocuSign]  toegelaten Aangepaste Vorm](#create-an-adaptive-form-for-docusign)
- [ laat  [!DNL DocuSign]  voor een bestaande Aangepaste Vorm ](#editafsign) toe.

#### Een adaptief formulier maken voor DocuSign {#create-an-adaptive-form-for-docusign}

Een adaptief formulier maken dat geschikt is voor ondertekenen:

1. Navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .
1. Selecteer **[!UICONTROL Create]** en selecteer **[!UICONTROL Adaptive Form]** . Er wordt een lijst met sjablonen weergegeven. Selecteer een sjabloon en selecteer **[!UICONTROL Next]** .
1. Op het tabblad **[!UICONTROL Basic]** :

   1. Geef de waarden **[!UICONTROL Name]** en **[!UICONTROL Title]** op voor het adaptieve formulier.

   1. Selecteer de [ gemaakte configuratiecontainer ](adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) terwijl [ integreren  [!DNL DocuSign]  met  [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md).

   De configuratiecontainer bevat de [!DNL DocuSign] Cloud Services die voor uw omgeving zijn geconfigureerd. Deze services zijn beschikbaar voor selectie in Adaptief formulier Builder.

1. Selecteer op het tabblad **[!UICONTROL Form Model]** een van de volgende opties:

   - Als u een aangepaste formuliersjabloon hebt en een Document of Record vereist op basis van de formuliersjabloon, selecteert u de optie **[!UICONTROL Associate form template as the Document of Record template]** en selecteert u een Document of Record-sjabloon. Als u deze optie gebruikt, worden alleen de velden weergegeven die zijn gebaseerd op de bijbehorende formuliersjabloon die zijn verzonden voor ondertekening. Niet alle velden van het adaptieve formulier worden weergegeven.

   - Als u geen aangepaste formuliersjabloon hebt, selecteert u de optie **[!UICONTROL Generate Document of Record]** . Als u deze optie gebruikt, worden in het document dat voor ondertekening is verzonden alle velden van het adaptieve formulier weergegeven.

1. Selecteer **[!UICONTROL Create]**. Er wordt een adaptief formulier gemaakt dat geschikt is voor ondertekening. U kunt uw [!DNL DocuSign] -velden toevoegen aan het formulier en het verzenden voor ondertekening.
1. Open het adaptieve formulier in de bewerkingsmodus. In het **[!UICONTROL Content]** lusje, selecteer **[!UICONTROL Form Container]** en selecteer ![ vormen ](assets/configure-icon.svg).

1. Selecteer **[!UICONTROL Submission]** in de vervolgkeuzelijst **[!UICONTROL Submit with DocuSign electronic signatures]** in de sectie **[!UICONTROL Submit Action]** .

1. Selecteer in de sectie **[!UICONTROL Action Configuration]** **[!UICONTROL Add]** om een ontvanger toe te voegen en geef het e-mailadres van de ontvanger op. Selecteer nogmaals **[!UICONTROL Add]** om meer ontvangers toe te voegen.

1. Geef het onderwerp voor het e-mailbericht op in het veld **[!UICONTROL Email Subject]** . Selecteer **omvatten Gehechtheid** om gehechtheid in het e-mailbericht te omvatten.

1. Selecteer ![ sparen ](assets/save_icon.svg) om de eigenschappen te bewaren.

#### [!DNL DocuSign] inschakelen voor een adaptief formulier {#editafsign}

[!DNL DocuSign] gebruiken in een bestaand adaptief formulier:

1. Navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .
1. Selecteer het adaptieve formulier en selecteer **[!UICONTROL Properties]** .
1. In het **[!UICONTROL Basic]** lusje, selecteer de [ gemaakte configuratiecontainer ](adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) terwijl het integreren [!DNL DocuSign] met [!DNL AEM Forms].
1. Selecteer op het tabblad **[!UICONTROL Form Model]** een van de volgende opties:

   - Als u een aangepaste formuliersjabloon hebt en een Document of Record vereist op basis van de formuliersjabloon, selecteert u de optie **[!UICONTROL Associate form template as the Document of Record template]** en selecteert u een Document of Record-sjabloon. Als u deze optie gebruikt, worden alleen de velden weergegeven die zijn gebaseerd op de bijbehorende formuliersjabloon die zijn verzonden voor ondertekening. Niet alle velden van het adaptieve formulier worden weergegeven.

   - Als u geen aangepaste formuliersjabloon hebt, selecteert u de optie **[!UICONTROL Generate Document of Record]** . Als u deze optie gebruikt, worden in het document dat voor ondertekening is verzonden alle velden van het adaptieve formulier weergegeven.

1. Selecteer **[!UICONTROL Save & Close]**. Het adaptieve formulier is ingeschakeld voor [!DNL DocuSign] . Nu kunt u uw [!DNL DocuSign] -velden toevoegen aan het formulier en het verzenden voor ondertekening.

1. Open het adaptieve formulier in de bewerkingsmodus. In het **[!UICONTROL Content]** lusje, selecteer **[!UICONTROL Form Container]** en selecteer ![ vormen ](assets/configure-icon.svg).

1. Selecteer **[!UICONTROL Submission]** in de vervolgkeuzelijst **[!UICONTROL Submit with DocuSign electronic signatures]** in de sectie **[!UICONTROL Submit Action]** .

1. Selecteer in de sectie **[!UICONTROL Action Configuration]** **[!UICONTROL Add]** om een ontvanger toe te voegen en geef het e-mailadres van de ontvanger op. Selecteer nogmaals **[!UICONTROL Add]** om meer ontvangers toe te voegen.

1. Geef het onderwerp voor het e-mailbericht op in het veld **[!UICONTROL Email Subject]** . Selecteer **omvatten Gehechtheid** om gehechtheid in het e-mailbericht te omvatten.

1. Selecteer ![ sparen ](assets/save_icon.svg) om de eigenschappen te bewaren.
