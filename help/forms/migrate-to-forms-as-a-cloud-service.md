---
title: Hoe migreren van een AEM 6.5 Forms en AEM 6.4 Forms naar [!DNL AEM Forms] as a Cloud Service omgeving?
description: Migreren van een [!DNL AEM Forms] Omgeving op locatie naar [!DNL AEM Forms] as a Cloud Service omgeving
contentOwner: khsingh
feature: Adaptive Forms
role: User, Developer
level: Intermediate
topic: Migration
exl-id: 090e77ff-62ec-40cb-8263-58720f3b7558
source-git-commit: ea9d8714dca0d30ba2ff33cef220c8b3f8b3c429
workflow-type: tm+mt
source-wordcount: '1146'
ht-degree: 1%

---

# Migreren naar [!DNL AEM Forms] as a Cloud Service  {#Harden-your-AEM-Forms-as-a-Cloud-Service-environment}

U kunt uw Adaptieve Forms-, thema-, sjablonen- en cloudconfiguraties migreren vanuit <!-- AEM 6.3 Forms--> AEM 6.4 Forms op OSGi en AEM 6.5 Forms op OSGi aan [!DNL AEM] as a Cloud Service. Voordat u deze elementen gaat migreren, gebruikt u het migratiehulpprogramma om de indeling die in de eerdere versies werd gebruikt, om te zetten in de indeling die in [!DNL AEM] as a Cloud Service. Wanneer u het Hulpprogramma voor migratie uitvoert, worden de volgende middelen bijgewerkt:

* Aangepaste componenten voor adaptieve Forms
* Aangepaste Forms-sjablonen en -thema&#39;s
* Cloud-configuraties
* Scripts van de code-editor worden omgezet in herbruikbare functies en toegepast op visuele regels.

## Overwegingen {#consideration}

* De service helpt inhoud alleen te migreren van [!DNL AEM Forms] in OSGi-omgevingen. Inhoud migreren uit [!DNL AEM Forms] op JEE aan een milieu van de Cloud Service wordt niet gesteund.

* (Alleen voor AEM 6.3 Forms of een eerdere versie van de omgeving die is bijgewerkt naar AEM 6.4 Forms of AEM 6.5 Forms) Aangepaste Forms op basis van out-of-the-box sjablonen en thema&#39;s die beschikbaar zijn in AEM 6.3 Forms of vorige versie worden niet ondersteund op [!DNL [!DNL AEM Forms]] as a Cloud Service.

## Vereisten {#prerequisites}

* [Forms inschakelen - Digitale inschrijving](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/setting-up-program.html?#editing-program) voor uw Forms Cloud Service-programma en [de pijpleiding in werking stellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html).

![Droog resultaat](assets/enable-add-on.png)

* In een Cloud Service-omgeving werkt het migratiehulpprogramma samen met het Hulpprogramma voor het toewijzen van gebruikersgegevens en het gereedschap voor het overbrengen van inhoud. Het migratiehulpprogramma maakt [!DNL AEM Forms] elementen die compatibel zijn met Cloud Service en het gereedschap voor inhoudsoverdracht migreren de inhoud van uw [!DNL AEM Forms] milieu aan een [!DNL AEM] as a Cloud Service omgeving. Voordat u het migratiehulpprogramma gaat gebruiken, moet u het proces van [verplaatsen naar AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/home.html). Het proces heeft twee gereedschappen:
   * [Gereedschap Toewijzing gebruiker](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#cloud-migration): Met het gereedschap Toewijzing gebruiker kunt u uw gebruikers toewijzen met de bijbehorende Adobe IMS-gebruikersaccounts.
   * [Inhoud overbrengen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?#cloud-migration): Met het gereedschap Inhoud overbrengen kunt u inhoud voorbereiden en overbrengen van een bestaande omgeving naar een Cloud Service-omgeving.
* Accounts met beheerdersrechten op [!DNL AEM Forms] as a Cloud Service en lokaal [!DNL AEM Forms] milieu.
* Download en installeer Best Practice Analyzer, Content Transfer Tool en [!DNL AEM Forms] Hulpprogramma voor migratie van [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)

* Voer de [Analysator van best practices](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration) en verhelpt u het gerapporteerde probleem.

<!-- * Download the latest [compatibility package](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=en#aem-65-forms-releases) for your [!DNL AEM Forms] version. -->

## Migreren [!DNL AEM Forms] elementen  {#use-the-migration-utility}

Voer de volgende stappen uit om uw [!DNL AEM Forms] activa die verenigbaar zijn met de Cloud Service en deze overdragen aan een [!DNL AEM] as a Cloud Service omgeving.

1. Een [klonen](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/correct-method-to-clone-the-aem-environment/qaq-p/363487) van uw bestaande [!DNL AEM Forms] milieu.

   Gebruik altijd de gekloonde omgeving om het gereedschap Inhoud overbrengen en het migratiehulpprogramma uit te voeren. Met het hulpprogramma voor het overbrengen van inhoud en het migratiehulpprogramma wijzigt u de inhoud en elementen. Voer dus het gereedschap Inhoud overbrengen en het migratiehulpprogramma niet uit in een productieomgeving.

1. Meld u met beheerdersrechten aan bij uw gekloonde omgeving.

1. Voer de [Gereedschap Toewijzing gebruiker](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#cloud-migration) om uw gebruikers toe te wijzen aan de overeenkomstige Adobe IMS-gebruikersaccounts. Adobe IMS-gebruikersaccounts moeten zich aanmelden bij een [!DNL AEM Forms] as a Cloud Service instantie.

1. Download en installeer de [Inhoud overbrengen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?#cloud-migration) en [!DNL AEM Forms] as a Cloud Service migratiehulpprogramma van [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) over de gekloonde omgeving. U kunt AEM Package Manager gebruiken om het hulpmiddel en het nut te installeren.

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Content Migration]**.

1. Open de **[!UICONTROL Prepare Forms for migration]** kaart. In de browser worden vijf opties weergegeven:
   * **[!UICONTROL AEM Forms Assets Migration]**
   * **[!UICONTROL Adaptive Forms Custom Components Migration]**
   * **[!UICONTROL Adaptive Forms Templates Migration]**
   * **[!UICONTROL AEM Forms Cloud Configurations Migration]**
   * **[!UICONTROL Code Editor Script Migration]**

1. Gebruik de optie een voor een om uw [!DNL AEM Forms] activa die verenigbaar zijn met [!DNL AEM] as a Cloud Service:

   1. Tikken **[!UICONTROL AEM Forms Assets Migration]** en tikt u in het volgende scherm op **[!UICONTROL Start Migration]**. Het maakt Adaptieve Forms en thema&#39;s op uw [!DNL AEM Forms] omgeving die compatibel is met [!DNL AEM] as a Cloud Service .

   1. Tikken **[!UICONTROL Adaptive Forms Custom Components Migration]** en tikt u op de pagina Custom Components Migration op **[!UICONTROL Start Migration]**. Elke aangepaste component die is ontwikkeld voor Adaptive Forms en componentoverlays op uw [!DNL AEM Forms] omgeving die compatibel is met [!DNL AEM] as a Cloud Service .

   1. Tikken **[!UICONTROL Adaptive Forms Template Migration]** en tikt u op de pagina Custom Components Migration op **[!UICONTROL Start Migration]**. Hiermee worden adaptieve formuliersjablonen op /apps of /conf gemaakt en gemaakt met AEM Sjablooneditor compatibel met [!DNL AEM] as a Cloud Service .

   1. Tikken **[!UICONTROL AEM Forms Cloud Configurations Migration]** en tikt u vervolgens op de pagina Configuration Migration **[!UICONTROL Start Migration]**. De volgende Cloud Services worden bijgewerkt en naar een nieuwe locatie verplaatst:

      * Cloud Service formuliergegevensmodel
      * Google reCAPTCHA Cloud Service
      * [!DNL Adobe Sign] Cloud Service
      * Adobe Fonts Cloud Service
   1. Tikken **[!UICONTROL Code Editor Script Migration]**, geeft u een locatie op waar herbruikbare functies moeten worden opgeslagen en tikt op **[!UICONTROL Start Migration].

   De Cloud Service steunt geen manuscripten van de regelredacteur. De **[!UICONTROL Code editor script migration]** het hulpmiddel zet alle regelmanuscripten op uw milieu in herbruikbare functies om en past de herbruikbare functies op visuele redacteur op aangewezen plaats toe. Deze herbruikbare functies worden opgeslagen in de vorm van clientbibliotheken en zorgen ervoor dat de bestaande functionaliteit behouden blijft. Het gereedschap past automatisch de gegenereerde herbruikbare functies toe op de overeenkomstige adaptieve Forms.

   Gebruik de [Pakketbeheer](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en#contentmanagement) om de herbruikbare functies (Clientbibliotheken) naar een pakket te exporteren.

1. [Implementeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#deploying-content-packages-via-cloud-manager-and-package-manager) het pakket herbruikbare functies (Client Libraries); [aangepaste code, componenten, configuraties](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/devops/deploy-code.html#cloud-manager), aangepaste, landspecifieke bibliotheken voor uw [!DNL AEM] as a Cloud Service omgeving.

   <!-- 1. Install the latest [Compatibility Package](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?#cloud-migration) to your cloned [!DNL AEM Forms] environment. -->

1. Voer de [Inhoud overbrengen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?#cloud-migration). Terwijl het specificeren van parameters op **[!UICONTROL Create Migration Set]** het scherm, specificeer de weg van Adaptive Forms, thema&#39;s, malplaatjes, de Modellen van de Gegevens van de Vorm, Cloud Services, de Componenten van de Douane en andere AEM Forms-specifieke activa aan het **[!UICONTROL Paths to be included]** optie. Opgegeven [!DNL AEM Forms] te migreren elementen.

## Paden van verschillende AEM Forms-specifieke activa

* **Adaptieve Forms**: U vindt adaptieve formulieren op `/content/dam/formsanddocuments/`en /content/forms/af. Voeg bijvoorbeeld paden toe voor een adaptief formulier met de naam WKND-registratie `/content/dam/formsanddocuments/wknd-registration` en `/content/forms/af/wknd-registration`.
* **Formuliergegevensmodus**: U kunt alle modellen van de Gegevens van het Vorm vinden bij `/content/dam/formsanddocuments-fdm`. Bijvoorbeeld, `/content/dam/formsanddocuments-fdm/ms-dynamics-fdm`.

* **Clientbibliotheken**: Het standaardpad van clientbibliotheken is `/etc/clientlibs/fd/theme`.

* **Aangepaste formuliersjablonen**: Het standaardpad van sjablonen is `/conf/<template folder>`. Voor een sjabloon met de naam basis voegt u bijvoorbeeld een pad toe `/conf/ReferenceEditableTemplates/settings/wcm/templates/basic`.

* **Adaptieve formulierthema&#39;s en clientbibliotheken**: Het standaardpad van thema&#39;s is ` /content/dam/formsanddocuments-themes/` en het standaardpad van de clientbibliotheken is `/etc/clientlibs/fd/theme`. Voor een sjabloon met de naam WKND-thema voegt u bijvoorbeeld een pad toe ` /content/dam/formsanddocuments-themes/wkndtheme` en clientbibliotheken voor het thema op `/etc/clientlibs/reference-themes/wkndtheme-3-0`. U kunt thema&#39;s en cliëntbibliotheken bij andere douanepaden ook hebben.

* **Cloudconfiguraties**: U vindt Cloud Configurations op `/conf/`. De cloudconfiguratie van het formuliergegevensmodel bevindt zich bijvoorbeeld op `/conf/global/settings/cloudconfigs/fdm`.

* **Workflowmodel**: U vindt AEM workflowmodellen op `/conf/global/settings/workflow/models/`. Bijvoorbeeld voor een workflowmodel met de naam WKND-registratie: pad toevoegen `/conf/global/settings/workflow/models/wknd-registration`

U kunt hieronder vermelde mappaden op het hoogste niveau toevoegen of specifieke mappaden zoals hieronder beschreven. Hiermee kunt u bepaalde elementen en alle elementen en formulieren tegelijk migreren.

* /content/dam/formsanddocuments-fdm
* /content/dam/formsanddocuments/thems
* /content/forms/af
* /etc/clientlibs/fd/theme

Als u AEM workflowmodellen wilt migreren, geeft u de volgende paden op:

* /conf/global/settings/workflow/models/
* /conf/global/settings/workflow/launch
* /var/workflow/models
