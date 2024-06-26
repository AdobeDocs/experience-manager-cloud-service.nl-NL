---
title: Hoe te om DocuSign met een Aangepast Vorm te integreren?
description: Leer hoe u DocuSign met een adaptief formulier kunt gebruiken om e-handtekeningen te verzamelen.
exl-id: fb2e75d6-e454-4999-a079-f663af79051f
feature: Adaptive Forms, Acrobat Sign
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '1413'
ht-degree: 0%

---

# DocuSign gebruiken met een adaptief formulier {#integrate-aem-forms-with-DocuSign}

DocuSign is een belangrijke oplossing voor e-handtekeningen. U kunt deze gebruiken om een overeenkomst elektronisch te ondertekenen. U kunt DocuSign integreren met een adaptief formulier. Hiermee kunt u een adaptief formulier voor e-handtekeningen naar meerdere ontvangers verzenden. Met e-handtekeningen kunt u:

- Sluit overeenkomsten van om het even welk apparaat met volledig geautomatiseerde voorstel, citaat, en contractprocessen.
- Voltooi processen voor menselijke hulpbronnen sneller en geef uw werknemers de digitale ervaring.
- Verkort de duur van de contractcyclus en neem sneller aan boord van uw leveranciers.

AEM Forms as a Cloud Service biedt een [aangepaste verzendactie voor DocuSign](#deploy-custom-submit-action). Met de verzendactie kunt u de adaptieve formulieren voor e-handtekeningen verzenden met DocuSign API&#39;s.

| U kunt ook Adobe Sign, de oplossing voor e-handtekeningen van Adobe, gebruiken om een adaptief formulier elektronisch te ondertekenen. AEM Forms heeft een veel diepere integratie met Adobe Sign en verstrekt veel fijnere controles zoals opeenvolgend en parallel ondertekenen, veelvoudige authentificatiemethodes, in-vorm het ondertekenen ervaring en meer. Zie voor meer informatie [Adobe Sign gebruiken in een adaptief formulier](working-with-adobe-sign.md). |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

## Vereisten {#prerequisites}

Voor de integratie van DocuSign met AEM Forms is het volgende vereist:

- Een DocuSign [ontwikkelingsaccount](https://developers.docusign.com/platform/account/)
- Een DocuSign-toepassing
- Referenties (client-id en clientgeheim) van DocuSign API-toepassing.
- [Aangepaste verzendactie en cloudservice voor DocuSign](https://github.com/adobe/aem-forms-docusign-sample)
- (Alleen voor lokale ontwikkelomgeving) [Document van record instellen](setup-local-development-environment.md#docker-microservices).

## Aangepaste verzendactie en cloudservice voor DocuSign configureren {#deploy-custom-submit-action}

AEM Forms as a Cloud Service biedt een aangepaste verzendactie voor DocuSign. Met de verzendactie kunt u de adaptieve formulieren voor e-handtekeningen verzenden met DocuSign API&#39;s. Code voor aangepaste verzendactie is beschikbaar op [AEM Forms voorbeeldbewaarplaats voor openbare git](https://github.com/adobe/aem-forms-docusign-sample). U kunt de code implementeren zoals deze zich in uw AEM Forms-omgeving bevindt of deze aanpassen aan de vereisten van uw organisatie.

Voer de volgende stappen uit om uit-van-de-doos aangepaste verzendactie en Cloud Service DocuSign te vormen:

1. [Clone your AEM Forms as a Cloud Service project](setup-local-development-environment.md#forms-cloud-service-local-development-environment) of maak een [!DNL Experience Manager Forms] als [!DNL Cloud Service] project gebaseerd op [AEM Archetype 27](https://github.com/adobe/aem-project-archetype) of hoger. Om een [!DNL Experience Manager Forms] als [!DNL Cloud Service] project gebaseerd op AEM Archetype:
   </br> Open de opdrachtprompt en voer de onderstaande opdracht uit om een [!DNL Experience Manager Forms] as a Cloud Service project:

   ```shell
   mvn -B archetype:generate -DarchetypeGroupId=com.adobe.aem -DarchetypeArtifactId=aem-project-archetype -DarchetypeVersion=27 -DaemVersion="cloud" -DappTitle="My Site" -DappId="mysite" -DgroupId="com.mysite" -DincludeForms="y"
   ```

   Ook wijzigen `appTitle`, `appId`, en `groupId`in de bovenstaande opdracht om uw omgeving te weerspiegelen.

1. Klonen met [aem-formulieren-voorbeelden](https://github.com/adobe/aem-forms-docusign-sample) opslagplaats. Deze opslagplaats bevat een aangepaste verzendactie voor DocuSign en configuratiegegevens om verbinding te maken met de DocuSign-server.

1. Open het as a Cloud Service project van AEM Forms dat in Stap 1 voor het uitgeven in winde van uw keus wordt gecreeerd.

1. Open de `[AEM Forms as a Cloud Service project]\pom.xml` te bewerken en de volgende wijzigingen aan te brengen:

   1. Voeg de volgende tekst toe aan het einde van het dialoogvenster `<properties>` tag:

      ```shell
      <repository.location>maven_repository</repository.location>
      ```

   1. Voeg de volgende tekst toe aan het einde van het dialoogvenster `<repositories>` tag:

      ```shell
       <repository>
          <id>project-repository</id>
          <url>file://${project.basedir}/${repository.location}</url>
       </repository>
      ```

      Als er geen `<repositories>` -tag, maakt u de -tag onder de `<properties>` -tag.

   1. Voeg de volgende tekst toe aan het einde van het dialoogvenster `<dependencyManagement>` tag:

      ```shell
       <dependency>
         <groupId>com.adobe.aemforms.samples</groupId>
         <artifactId>forms.integration.docusign.all</artifactId>
         <type>zip</type>
         <version>1.0.0</version>
       </dependency>
      ```

1. Voer de volgende stappen uit in het dialoogvenster `all/pom.xml` bestand beschikbaar in projectmap Cloud Service:

   1. Voeg de volgende tekst toe aan het einde van het dialoogvenster `<embeddeds>` tag:

      ```shell
       <embedded>
          <groupId>com.adobe.aemforms.samples</groupId>
          <artifactId>forms.integration.docusign.all</artifactId>
          <type>zip</type>
          <target>/apps/moonlightprodprogram-vendor-packages/application/install</target>
       </embedded>
      ```

   1. Voeg de volgende tekst toe aan het einde van het dialoogvenster `<dependencies>` tag:

      ```shell
       <dependency>
          <groupId>com.adobe.aemforms.samples</groupId>
          <artifactId>forms.integration.docusign.all</artifactId>
          <type>zip</type>
       </dependency>
      ```

1. De opdrachtprompt openen en naar `aem-forms-samples\forms-integration-docusign` (gekloond in stap 3) en voer het volgende bevel in werking:

   ```shell
   mvn clean install -Dinstall.dir="<AEM Forms as a Cloud Service project path>/maven_repository"
   ```

   `<AEM Forms as a Cloud Service project path>` verwijst naar de naam van de map die in stap 1 van deze procedure is gemaakt.

1. Implementeer het project in uw lokale ontwikkelomgeving. U kunt het volgende bevel gebruiken om aan uw lokale ontwikkelomgeving op te stellen

   `mvn -PautoInstallPackage clean install`

   Nadat u deze stappen hebt uitgevoerd, kunt u een nieuwe aangepaste verzendactie weergeven [Verzenden met DocuSign elektronische handtekeningen](#enabledocusign) beschikbaar in de lijst van indieningsopties voor een adaptief formulier en een [Configuratie van DocuSign-cloudservice](#configure-docusign-with-aem-forms) in uw lokale ontwikkelomgeving.

1. Compileren en [De code implementeren op uw [!DNL AEM Forms] as a Cloud Service omgeving](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#customer-releases).

## Integreren [!DNL DocuSign] with [!DNL AEM Forms] {#configure-docusign-with-aem-forms}

Nadat de eerste vereisten op zijn plaats zijn, voer de volgende stappen uit te integreren [!DNL DocuSign] with [!DNL AEM Forms] op de instanties Auteur.

1. Navigeren naar **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL DocuSign]** en selecteer een map die de configuratie host.

1. Selecteer op de configuratiepagina de optie **[!UICONTROL Create]** om [!DNL DocuSign] in AEM Forms.
1. In de **[!UICONTROL General]** tabblad van het **[!UICONTROL Create DocuSign Configuration]** pagina, geeft u een **[!UICONTROL Name]** voor de configuratie, en selecteer **[!UICONTROL Next]**. U kunt desgewenst een **[!UICONTROL Title]**.

1. Kopieer de URL in het huidige browservenster naar een laptop. De URL is vereist om te configureren [!DNL DocuSign] toepassing met [!DNL AEM Forms] in een latere stap.

1. OAuth-instellingen configureren voor de [!DNL DocuSign] toepassing:

   1. Een browservenster openen en aanmelden bij uw [!DNL DocuSign] [ontwikkelingsaccount](https://admindemo.docusign.com/apps-and-keys).
   1. Open de toepassing die is geconfigureerd voor [!DNL AEM Forms].
   1. In de **[!UICONTROL Redirect URI]** Voeg de URL toe die u in de vorige stap hebt gekopieerd en klik op **[!UICONTROL Save]**.
   1. Noteer de integratietoetsen en de geheime toetsen.

   Voor geleidelijke informatie om montages OAuth voor te vormen [!DNL DocuSign] en verkrijgen de toetsen, zie [Auteursinstellingen voor de toepassing configureren](https://support.docusign.com/guides/ndse-admin-guide-api-and-keys) ontwikkelaarsdocumentatie.

1. Ga terug naar de **[!UICONTROL Create DocuSign Configuration]** pagina. In de **[!UICONTROL Settings]** de **[!UICONTROL OAuth URL]** in field wordt de volgende standaard-URL vermeld:

   `https://account-d.docusign.com/oauth/auth`

1. Geef de **[!UICONTROL Client ID]** (DocuSign Integration Key) en **[!UICONTROL Client Secret]** (Geheime sleutel DocuSign).

1. Selecteer **[!UICONTROL Connect to DocuSign]**. Geef bij de aanwijzing voor referenties de gebruikersnaam en het wachtwoord op van het account dat wordt gebruikt tijdens het maken van [!DNL DocuSign] toepassing. Wanneer gevraagd om toegang te bevestigen voor `your developer account`, klikt u op **[!UICONTROL Allow Access]**. Als de gegevens juist zijn, wordt een succesbericht weergegeven.

1. Selecteren **[!UICONTROL Create]** om de [!DNL DocuSign] configuratie.

1. Selecteer de configuratie en klik op **[!UICONTROL Publish]**, selecteert u de configuratie en klikt u op **[!UICONTROL Publish]**. De configuratie wordt in overeenkomende publicatieomgevingen gerepliceerd.

1. Herhaal alle bovenstaande stappen op uw ontwikkelaar-, werkgebied- en productieinstanties (al naargelang wat er nog over is) om het configureren te voltooien [!DNL DocuSign] with [!DNL AEM Forms] voor uw omgeving.

Nu is uw AEM Forms-omgeving geconfigureerd voor gebruik van DocuSign. Zorg ervoor dat u de configuratiecontainer die voor de Cloud Service wordt gebruikt toevoegt aan alle Adaptive Forms die voor [!DNL DocuSign]. U kunt een configuratiecontainer opgeven met de eigenschappen van een adaptief formulier.

### Gebruiken [!DNL DocuSign] in een adaptieve vorm {#enabledocusign}

U kunt [!DNL DocuSign] voor een bestaand adaptief formulier of een [!DNL DocuSign] Aangepast formulier ingeschakeld. Kies een van de volgende opties:

- [Een [!DNL DocuSign] Aangepast formulier ingeschakeld](#create-an-adaptive-form-for-docusign)
- [Inschakelen [!DNL DocuSign] voor een bestaand adaptief formulier](#editafsign).

#### Een adaptief formulier maken voor DocuSign {#create-an-adaptive-form-for-docusign}

Een adaptief formulier maken dat geschikt is voor ondertekenen:

1. Navigeren naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Selecteren **[!UICONTROL Create]** en selecteert u **[!UICONTROL Adaptive Form]**. Er wordt een lijst met sjablonen weergegeven. Selecteer een sjabloon en selecteer **[!UICONTROL Next]**.
1. In de **[!UICONTROL Basic]** tab:

   1. Geef de **[!UICONTROL Name]** en **[!UICONTROL Title]** voor het adaptieve formulier.

   1. Selecteer de [configuratieconsole](adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) gemaakt tijdens [integreren [!DNL DocuSign] with [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md).

   De configuratiecontainer bevat de [!DNL DocuSign] Cloud Servicen geconfigureerd voor uw omgeving. Deze services zijn beschikbaar voor selectie in de Adaptieve formuliereditor.

1. In de **[!UICONTROL Form Model]** selecteert u een van de volgende opties:

   - Als u een aangepaste formuliersjabloon hebt en een Document of Record op basis van de formuliersjabloon nodig hebt, selecteert u de optie **[!UICONTROL Associate form template as the Document of Record template]** en selecteert u een Document of Record-sjabloon. Als u deze optie gebruikt, worden alleen de velden weergegeven die zijn gebaseerd op de bijbehorende formuliersjabloon die zijn verzonden voor ondertekening. Niet alle velden van het adaptieve formulier worden weergegeven.

   - Als u geen aangepaste formuliersjabloon hebt, selecteert u de optie **[!UICONTROL Generate Document of Record]** -optie. Als u deze optie gebruikt, worden in het document dat voor ondertekening is verzonden alle velden van het adaptieve formulier weergegeven.

1. Selecteren **[!UICONTROL Create.]** Er wordt een adaptief formulier gemaakt dat geschikt is voor ondertekening. U kunt uw [!DNL DocuSign] velden naar het formulier en verzenden voor ondertekening.
1. Open het adaptieve formulier in de bewerkingsmodus. In de **[!UICONTROL Content]** selecteert u de **[!UICONTROL Form Container]** en selecteert u ![Configureren](assets/configure-icon.svg).

1. In de **[!UICONTROL Submission]** sectie, selecteert u **[!UICONTROL Submit with DocuSign electronic signatures]** van de **[!UICONTROL Submit Action]** vervolgkeuzelijst.

1. In de **[!UICONTROL Action Configuration]** sectie, selecteert u **[!UICONTROL Add]** om een ontvanger toe te voegen en het e-mailadres van de ontvanger op te geven. Selecteren **[!UICONTROL Add]** nogmaals om meer ontvangers toe te voegen.

1. Geef het onderwerp voor het e-mailbericht op in het dialoogvenster **[!UICONTROL Email Subject]** veld. Selecteren **Bijlagen opnemen** om bijlagen in het e-mailbericht op te nemen.

1. Selecteren ![Opslaan](assets/save_icon.svg) om de eigenschappen op te slaan.

#### Inschakelen [!DNL DocuSign] voor een adaptief formulier {#editafsign}

Te gebruiken [!DNL DocuSign] in een bestaand adaptief formulier:

1. Navigeren naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Selecteer het adaptieve formulier en selecteer **[!UICONTROL Properties]**.
1. In de **[!UICONTROL Basic]** selecteert u de [configuratieconsole](adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) gemaakt tijdens het integreren [!DNL DocuSign] with [!DNL AEM Forms].
1. In de **[!UICONTROL Form Model]** selecteert u een van de volgende opties:

   - Als u een aangepaste formuliersjabloon hebt en een Document of Record op basis van de formuliersjabloon nodig hebt, selecteert u de optie **[!UICONTROL Associate form template as the Document of Record template]** en selecteert u een Document of Record-sjabloon. Als u deze optie gebruikt, worden alleen de velden weergegeven die zijn gebaseerd op de bijbehorende formuliersjabloon die zijn verzonden voor ondertekening. Niet alle velden van het adaptieve formulier worden weergegeven.

   - Als u geen aangepaste formuliersjabloon hebt, selecteert u de optie **[!UICONTROL Generate Document of Record]** -optie. Als u deze optie gebruikt, worden in het document dat voor ondertekening is verzonden alle velden van het adaptieve formulier weergegeven.

1. Selecteer **[!UICONTROL Save & Close]**. Het adaptieve formulier is ingeschakeld voor [!DNL DocuSign]. Nu kunt u uw [!DNL DocuSign] velden naar het formulier en verzenden voor ondertekening.

1. Open het adaptieve formulier in de bewerkingsmodus. In de **[!UICONTROL Content]** selecteert u de **[!UICONTROL Form Container]** en selecteert u ![Configureren](assets/configure-icon.svg).

1. In de **[!UICONTROL Submission]** sectie, selecteert u **[!UICONTROL Submit with DocuSign electronic signatures]** van de **[!UICONTROL Submit Action]** vervolgkeuzelijst.

1. In de **[!UICONTROL Action Configuration]** sectie, selecteert u **[!UICONTROL Add]** om een ontvanger toe te voegen en het e-mailadres van de ontvanger op te geven. Selecteren **[!UICONTROL Add]** nogmaals om meer ontvangers toe te voegen.

1. Geef het onderwerp voor het e-mailbericht op in het dialoogvenster **[!UICONTROL Email Subject]** veld. Selecteren **Bijlagen opnemen** om bijlagen in het e-mailbericht op te nemen.

1. Selecteren ![Opslaan](assets/save_icon.svg) om de eigenschappen op te slaan.
