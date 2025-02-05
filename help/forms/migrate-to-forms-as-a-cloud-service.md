---
title: Hoe kunnen we migreren van AEM 6,5 Forms naar AEM Forms as a Cloud Service?
description: Aan de slag met de Migratiereis naar AEM as a Cloud Service | Adobe Experience Manager. Migreer van een  [!DNL AEM Forms]  (milieu's op locatie en van AMS) aan  [!DNL AEM Forms]  as a Cloud Service milieu.
Keywords: 6.5 forms to cloud service, 6.5 forms to cs, migrate 6.5 forms to CS, migrate 6.5 forms to cloud service, upgrade 6.5 forms to CS, move 6.5 forms to CS, upgrade AEM 6.5 to CS, AEM Forms 6.5 to Cloud Service, AEM form migration to cloud service, Migration Journey to AEM as a Cloud Service | Adobe Experience Manager.
contentOwner: khsingh
feature: Adaptive Forms
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
role: User, Developer
level: Intermediate
topic: Migration
exl-id: 090e77ff-62ec-40cb-8263-58720f3b7558
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1307'
ht-degree: 0%

---

# Migreren van een [!DNL AEM Forms] -omgeving (op locatie en in een AMS-omgeving) naar [!DNL AEM Forms] as a Cloud Service  {#Harden-your-AEM-Forms-as-a-Cloud-Service-environment}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/upgrade-aem-forms/upgrade.html) |
| AEM as a Cloud Service | Dit artikel |

U kunt uw adaptieve Forms-, thema-, sjablonen- en cloudconfiguraties migreren of upgraden van <!-- AEM 6.3 Forms AEM 6.4 Forms on OSGi and --> AEM 6.5 Forms op OSGi naar [!DNL AEM] as a Cloud Service. Voordat u deze middelen migreert, gebruikt u het migratiehulpprogramma om de indeling die in de eerdere versies werd gebruikt, om te zetten in de indeling die in [!DNL AEM] as a Cloud Service wordt gebruikt.
Laten we beginnen met de migratietraject naar AEM as a Cloud Service | Adobe Experience Manager. Wanneer u het Hulpprogramma voor migratie uitvoert, worden de volgende middelen bijgewerkt:

* Aangepaste componenten voor adaptieve Forms
* Aangepaste Forms-sjablonen en -thema&#39;s
* Cloud-configuraties
* Scripts van de code-editor worden omgezet in herbruikbare functies en toegepast op visuele regels.

## Overwegingen bij migratie naar Forms-as a Cloud Service {#consideration}

Om van AEM 6.5 Forms naar AEM Cloud Service te migreren, is het belangrijk rekening te houden met de volgende punten:

* De service helpt inhoud alleen van [!DNL AEM Forms] naar OSGi-omgevingen te migreren. Het migreren van inhoud van [!DNL AEM Forms] op JEE naar een Cloud Service-omgeving wordt niet ondersteund.

* (Alleen voor versies ouder dan AEM 6.5 Forms) Adaptieve Forms op basis van out-of-the-box sjablonen en thema&#39;s die beschikbaar zijn in AEM 6.3 Forms of vorige versie wordt niet ondersteund op [!DNL AEM Forms] as a Cloud Service.

* Adobe Experience Manager Forms as a Cloud Service brengt een aantal opmerkelijke veranderingen in bestaande eigenschappen in vergelijking met Adobe Experience Manager 6.5 Forms (On-Premise en Adobe-Beheerde Dienst) milieu&#39;s. Alvorens met het migreren aan de dienst te werk te gaan, [ leren over deze opmerkelijke veranderingen ](notable-changes.md) en de [ verschillen van het eigenschapniveau ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=en#viewing-report) om te besluiten om gebaseerd op eigenschappen te migreren uw organisatie vereist.




<!-- 
## Difference with AEM 6.5 Forms 

| Feature         | Difference with AEM 6.5 Forms    |
|--------------|-----------|
| HTML5 Forms (Mobile Forms)     | The service does not support HTML5 Forms (Mobile Forms). If you render your XDP-based forms as HTML5 Forms, you can continue using the feature on AEM 6.5 Forms. |
| Adaptive Forms     | <li><b>XSD-Based Adaptive Forms:</b> The service does not support HTML5 Forms (Mobile Forms). If you render your XDP-based forms as HTML5 Forms, you can continue using the feature on AEM 6.5 Forms. </li> <li><b> Adaptive Form templates:</b> Use build pipeline and corresponding Git repository of your program to import existing Adaptive Form templates. </li><li><b>Rule editor:</b> AEM Forms as a Cloud Service provides a hardened [Rule editor](rule-editor.md#visual-rule-editor). The code editor is not available on Forms as a Cloud Service. The migration utility helps you migrate your forms that have custom rules (created in code editor). The utility converts such rules into custom functions supported on Forms as a Cloud Service. You can use the reusable functions with Rule editor to continue obtaining results obtained with rule scripts  The `onSubmitError` or `onSubmitSuccess` functions are now available as actions the Rule Editor. </li> <li><b>Drafts and submissions:</b> The service does not retain metadata for drafts and submitted Adaptive Forms. </li> <li><b> Prefill Service:</b> By default, the prefill service merges data with an Adaptive Form at client as opposed to merging data on Server in AEM 6.5 Forms. The feature helps improve the time required to prefill an Adaptive Form. You can always configure to run the merge action on the Adobe Experience Manager Forms Server. </li><li><b>Submit actions:</b> The **Email as PDF** action is not available. The **Email** submit action provide options to send attachments and attach Document of Record (DoR) with email. </li>|
| Form Data Model | <li>Forms data model supports only HTTP and HTTPs endpoints to submit data. </li><li>Forms as a Cloud Service allows to use Microsoft Azure Blob, Microsoft Sharepoint, Microsoft OneDrive, and services supporting general CRUD (Create, Read, Update, and Delete) operations as data stores. The service does not support JDBC connector, Mutual SSL for Rest connector, and x509 certificate-based authentication for SOAP data sources. </li>|
| Automated Forms Conversion Service     | The service does not provide meta-model for Automated Forms Conversion Service. You can [download it from Automated Forms Conversion Service documentation](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#default-meta-model).|
|Configurations|<li>Email support only HTTP and HTTPs protocols, by default. [Contact the support team](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email) to enable ports for sending emails and to enable SMTP protocol for your environment. </li> <li>If you use custom bundles, recompile your code with latest version of adobe-aemfd-docmanager before using these bundles with Forms as a Cloud Service.</li> |
| Document Manipulation APIs (Assembler Service)| The service does not support operations dependent on other services or applications: <li>Conversion of documents in a non-PDF format to a PDF format is not supported. For example, Microsoft Word to PDF, Microsoft Excel to PDF, and HTML to PDF are not supported</li><li>Adobe Distiller-based conversions are not supported. For example, PostScript(PS) to PDF</li><li>Forms Service-based conversions are not supported. For example, XDP to PDF Forms.</li><li>The service does not support converting a Signed PDF or Transparent PDF to another PDF format.</li>| -->

## Vereisten {#prerequisites}

Voor een soepele overgang van AEM Forms 6.5 naar AEM as a Cloud Service-omgeving is het belangrijk de volgende voorwaarden in overweging te nemen:

* Laat [ Forms toe - de Digitale optie van de Inschrijving ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/setting-up-program.html?#editing-program) voor uw programma van de Cloud Service van Forms en [ stel de pijpleiding ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html) in werking.

  ![ Droog Resultaat van de Looppas ](assets/enable-add-on.png)

* In een Cloud Service-omgeving werkt het migratiehulpprogramma in combinatie met het Content Transfer Tool. Het migratiehulpprogramma maakt [!DNL AEM Forms] -elementen compatibel met Cloud Service en het gereedschap voor het overbrengen van inhoud migreert de inhoud van uw [!DNL AEM Forms] -omgeving naar een [!DNL AEM] as a Cloud Service omgeving. Alvorens het Nut van de Migratie te gebruiken, leer het proces van [ zich het bewegen aan AEM as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/home.html). Voor het proces wordt het volgende gereedschap gebruikt:
   * [ het Hulpmiddel van de Overdracht van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?#cloud-migration): Het hulpmiddel van de Overdracht van de Inhoud helpt u voorbereidingen treffen en inhoud van bestaand milieu overbrengen aan een milieu van de Cloud Service. Hiermee kunnen gebruikers eenvoudig upgraden van AEM Forms naar de cloud-omgeving.
* Accounts met beheerderrechten op [!DNL AEM Forms] as a Cloud Service en uw lokale [!DNL AEM Forms] omgeving.
* De download en installeert Analysator van Beste praktijken, het Hulpmiddel van de Overdracht van de Inhoud, en [!DNL AEM Forms] Nut van de Migratie van [ het Portaal van de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

* Stel het [ hulpmiddel in werking van de Analysator van Beste praktijken ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration) en verhelpt de gemelde kwestie. Voor de mogelijke kwesties met betrekking tot het migreren van Adobe Experience Manager Forms aan Adobe Experience Manager Forms as a Cloud Service, zie [ AEM de Detectie van het Patroon voor Forms as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=en#viewing-report).


<!-- * Download the latest [compatibility package](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=en#aem-65-forms-releases) for your [!DNL AEM Forms] version. -->




## [!DNL AEM 6.5 Forms] elementen migreren naar AEM Cloud Service {#use-the-migration-utility}

Voer de volgende stappen uit om uw [!DNL AEM Forms] -elementen compatibel te maken met Cloud Service en deze over te brengen naar een [!DNL AEM] as a Cloud Service omgeving.

1. Creeer a [ kloon ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/correct-method-to-clone-the-aem-environment/qaq-p/363487) van uw bestaand [!DNL AEM Forms] milieu.

   >[!NOTE]
   >
   > Wanneer u van 6.5 naar de cloudservice migreert, wordt u aangeraden een gekloonde omgeving te gebruiken voor het uitvoeren van het gereedschap Inhoud overbrengen en het migratiehulpprogramma. Met het hulpprogramma voor het overbrengen van inhoud en het migratiehulpprogramma wijzigt u de inhoud en elementen. Voer dus het gereedschap Inhoud overbrengen of het migratiehulpprogramma niet uit in een productieomgeving.

1. Meld u met beheerdersrechten aan bij uw gekloonde omgeving.

1. Download en installeer het [ Hulpmiddel van de Overdracht van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?#cloud-migration) en [!DNL AEM Forms] as a Cloud Service Nut van de Migratie van [ het Portaal van de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) op het gekloonde milieu. U kunt AEM Package Manager gebruiken om het hulpmiddel en het nut te installeren.

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Content Migration]** .

1. Open de **[!UICONTROL Prepare Forms for migration]** -kaart. In de browser worden vijf opties weergegeven:
   * **[!UICONTROL AEM Forms Assets Migration]**
   * **[!UICONTROL Adaptive Forms Custom Components Migration]**
   * **[!UICONTROL Adaptive Forms Templates Migration]**
   * **[!UICONTROL AEM Forms Cloud Configurations Migration]**
   * **[!UICONTROL Code Editor Script Migration]**

1. Gebruik de optie een voor een om uw [!DNL AEM Forms] -elementen compatibel te maken met [!DNL AEM] as a Cloud Service:

   1. Selecteer **[!UICONTROL AEM Forms Assets Migration]** en selecteer **[!UICONTROL Start Migration]** in het volgende scherm. Hiermee worden Adaptieve Forms en thema&#39;s in uw [!DNL AEM Forms] -omgeving compatibel gemaakt met [!DNL AEM] as a Cloud Service.

   1. Selecteer **[!UICONTROL Adaptive Forms Custom Components Migration]** en selecteer **[!UICONTROL Start Migration]** op de pagina Custom Components Migration (Migratie van aangepaste componenten). Elke aangepaste component die is ontwikkeld voor Adaptive Forms en componentoverlays in uw [!DNL AEM Forms] -omgeving, wordt compatibel gemaakt met [!DNL AEM] as a Cloud Service.

   1. Selecteer **[!UICONTROL Adaptive Forms Template Migration]** en selecteer **[!UICONTROL Start Migration]** op de pagina Custom Components Migration (Migratie van aangepaste componenten). Hiermee worden adaptieve formuliersjablonen op `/apps` of `/conf` en gemaakt met AEM Sjablooneditor compatibel gemaakt met [!DNL AEM] as a Cloud Service.

   1. Selecteer **[!UICONTROL AEM Forms Cloud Configurations Migration]** en selecteer vervolgens op de pagina Configuration Migration **[!UICONTROL Start Migration]** . De volgende Cloud Servicen worden bijgewerkt en naar een nieuwe locatie verplaatst:

      * Cloud Service formuliergegevensmodel
      * Google reCAPTCHA Cloud Service
      * [!DNL Adobe Sign] Cloud Service
      * Adobe Fonts Cloud Service

   1. Selecteer **[!UICONTROL Code Editor Script Migration]**, specificeer een plaats om herbruikbare functies te bewaren, en selecteer ** [!UICONTROL Start Migration].

   De Cloud Service ondersteunt geen regeleditorscripts. Met het gereedschap **[!UICONTROL Code editor script migration]** zet u alle regelscripts in uw omgeving om in herbruikbare functies en past u de herbruikbare functies toe op de juiste locatie in de visuele editor. Deze herbruikbare functies worden opgeslagen in de vorm van clientbibliotheken en zorgen ervoor dat de bestaande functionaliteit behouden blijft. Het gereedschap past automatisch de gegenereerde herbruikbare functies toe op de overeenkomstige adaptieve Forms.

   AEM de migratie van de Vorm aan Cloud Service, gebruik de [ Manager van het Pakket ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en#contentmanagement) om de herbruikbare functies (de Bibliotheken van de Cliënt) naar een pakket uit te voeren.

1. [ stelt ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#deploying-content-packages-via-cloud-manager-and-package-manager) het herbruikbare pakket van functies (de Bibliotheken van de Cliënt) op, [ douanecode, componenten, configuraties ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/devops/deploy-code.html#cloud-manager), douane landspecifieke bibliotheken aan uw [!DNL AEM] as a Cloud Service milieu.

   <!-- 1. Install the latest [Compatibility Package](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?#cloud-migration) to your cloned [!DNL AEM Forms] environment. -->

1. Stel het [ Hulpmiddel van de Overdracht van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?#cloud-migration) in werking. Geef bij het opgeven van parameters op het scherm **[!UICONTROL Create Migration Set]** het pad op van Adaptief Forms, thema&#39;s, sjablonen, Form Data Model (FDM), Cloud Servicen, Custom Components (Aangepaste componenten) en andere AEM Forms-specifieke elementen naar de optie **[!UICONTROL Paths to be included]** . Hiermee worden opgegeven [!DNL AEM Forms] elementen toegevoegd aan de migratieset.

## Paden van verschillende AEM Forms-specifieke activa

Wanneer u van AEM Forms 6.5 naar de cloudservice migreert, kunt u de AEM Forms-specifieke middelen vinden op:

* **Aangepaste Forms**: U kunt Aangepaste vormen bij `/content/dam/formsanddocuments/` en `/content/forms/af` vinden. Voeg bijvoorbeeld paden `/content/dam/formsanddocuments/wknd-registration` en `/content/forms/af/wknd-registration` toe voor een adaptief formulier met de naam WKND-registratie.
* **Model van de Gegevens van de Vorm**: U kunt al Model van de Gegevens van de Vorm (FDM) bij `/content/dam/formsanddocuments-fdm` vinden. Bijvoorbeeld `/content/dam/formsanddocuments-fdm/ms-dynamics-fdm` .

* **de bibliotheken van de Cliënt**: De standaardweg van cliëntbibliotheken is `/etc/clientlibs/fd/theme`.

* **Aangepaste malplaatjes van de Vorm**: De standaardweg van malplaatjes is `/conf/<template folder>`. Voor bijvoorbeeld een sjabloon met de naam basic add path `/conf/ReferenceEditableTemplates/settings/wcm/templates/basic` .

* **de Adaptieve thema&#39;s van de Vorm en de bibliotheken van de Cliënt**: De standaardweg van thema&#39;s is ` /content/dam/formsanddocuments-themes/` en de standaardweg van cliëntbibliotheken is `/etc/clientlibs/fd/theme`. Voor een sjabloon met de naam WKND-thema voegt u bijvoorbeeld het pad ` /content/dam/formsanddocuments-themes/wkndtheme` en de clientbibliotheken toe voor het thema in `/etc/clientlibs/reference-themes/wkndtheme-3-0` . U kunt thema&#39;s en cliëntbibliotheken bij andere douanepaden ook hebben.

* **de Configuraties van de Wolk**: U kunt de Configuraties van de Wolk bij `/conf/` vinden. De cloudconfiguratie van het Form Data Model (FDM) bevindt zich bijvoorbeeld op `/conf/global/settings/cloudconfigs/fdm`.

* **Model van het Werkschema**: U kunt AEM Modellen van het Werkschema bij `/conf/global/settings/workflow/models/` vinden. Bijvoorbeeld voor een workflowmodel met de naam WKND-registratie: pad toevoegen `/conf/global/settings/workflow/models/wknd-registration`

U kunt hieronder vermelde mappaden op het hoogste niveau toevoegen of specifieke mappaden zoals hieronder beschreven. Hiermee kunt u een bepaald middel en alle elementen en formulieren tegelijk migreren wanneer u een upgrade uitvoert naar de cloudservice van AEM formulieren 6.5.

* `/content/dam/formsanddocuments-fdm`
* `/content/dam/formsanddocuments/themes`
* `/content/forms/af`
* `/etc/clientlibs/fd/theme`

Wanneer u AEM workflowmodellen van AEM Forms 6.5 naar Cloud Service migreert, geeft u de volgende paden op:

* `/conf/global/settings/workflow/models/`
* `/conf/global/settings/workflow/launcher`
* `/var/workflow/models`

## Zie volgende

* [ Notable veranderingen voor bestaande Adobe Experience Manager 6.5 de gebruikers van Forms ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/forms-overview/notable-changes.html)
* [ Onboard aan AEM Forms as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/setup-forms-cloud-service.html)
* [ creeer uw eerste Aangepaste Vorm op Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form.html)

## Aanvullende informatie

Met het migratiehulpprogramma kunt u Adaptief Forms migreren op basis van stichtingscomponenten. Daarnaast biedt Forms as a Cloud Service ondersteuning voor Adaptive Forms Core Components. U kunt dus:

* [Zelfstandige adaptieve Forms op basis van Core Component maken](/help/forms/creating-adaptive-form-core-components.md)
* [Een adaptief formulier op basis van een Core-component rechtstreeks op een AEM Sites-pagina maken](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)

Meer informatie over AEM Forms as a Cloud Service vindt u in:

* [Inleiding tot AEM Forms Cloud Service](/help/forms/home.md)
* [Innovaties in AEM Forms Cloud Service](/help/forms/latest-innovations.md)