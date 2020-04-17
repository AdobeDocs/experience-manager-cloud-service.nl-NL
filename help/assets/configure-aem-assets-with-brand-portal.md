---
title: AEM Assets as a Cloud Service configureren met Brand Portal
description: AEM Assets as a Cloud Service configureren met Brand Portal.
contentOwner: Vishabh Gupta
translation-type: tm+mt
source-git-commit: d644fc348ff6d62c03100941b96c03049f345763

---


# AEM Assets configureren met Brand Portal {#configure-aem-assets-with-brand-portal}

AEM Assets (Adobe Experience Manager) wordt geconfigureerd met Brand Portal via Adobe I/O, dat een IMS-token aanschaft voor autorisatie van uw Brand Portal-tenant.

## Vereisten {#prerequisites}

U hebt het volgende nodig om AEM Assets te configureren met Brand Portal:

* Een actieve en werkende AEM Assets-cloudinstantie.
* URL van Brand Portal-tenant.
* Een gebruiker met systeembeheerdersbevoegdheden op de IMS-organisatie van de Brand Portal-tenant.

**Neem contact op met de ondersteuningsdienst** als u nog vragen hebt.

## Configuratie maken {#create-new-configuration}

U kunt op Adobe I/O een configuratie maken om uw AEM Assets cloud-instantie te configureren met behulp van Brand Portal.

Voer de volgende stappen in deze volgorde uit:
1. [Openbaar certificaat verkrijgen](#public-certificate)
1. [Adobe I/O-integratie maken](#createnewintegration)
1. [IMS-accountconfiguratie maken](#create-ims-account-configuration)
1. [Cloudservice configureren](#configure-the-cloud-service)
1. [Configuratie testen](#test-configuration)

### IMS-configuratie maken {#create-ims-configuration}

IMS-configuratie verifieert uw Brand Portal-tenant met de AEM Assets-auteurinstantie.

De IMS-configuratie omvat twee stappen:

* [Openbaar certificaat verkrijgen](#public-certificate)
* [IMS-accountconfiguratie maken](#create-ims-account-configuration)

### Openbaar certificaat verkrijgen {#public-certificate}

Met een openbaar certificaat kunt u uw profiel verifiëren op Adobe I/O.

1. Meld u aan bij uw AEM Assets-cloudinstantie..

1. Navigeer vanuit het deelvenster **Gereedschappen** ![Gereedschappen](assets/tools.png) naar **[!UICONTROL Beveiliging]** > **[!UICONTROL Adobe IMS-configuraties]**.

   ![Gebruikersinterface voor Adobe IMS-accountconfiguratie](assets/ims-configuration1.png)

1. De pagina Adobe IMS Configurations wordt geopend.

   Klik op **[!UICONTROL Maken]**.

   Hiermee gaat u naar de pagina Configuratie **[!UICONTROL technische account van]** Adobe IMS.

1. Standaard wordt het tabblad **Certificate** geopend.

   Selecteer in **Cloudoplossing** de optie **[!UICONTROL Adobe Brand Portal]**.

1. Markeer het selectievakje **[!UICONTROL Nieuw certificaat]** maken en geef een **alias** voor het certificaat op. De alias fungeert als naam voor het dialoogvenster.

1. Klik op **[!UICONTROL Certificaat]** maken. Er wordt een dialoogvenster weergegeven. Click **[!UICONTROL OK]** to generate the public certificate.

   ![Create Certificate](assets/ims-config2.png)

1. Click **[!UICONTROL Download Public Key]** and save the *AEM-Adobe-IMS.crt* certificate file on your machine. Het certificaatbestand wordt gebruikt om [Adobe I/O-integratie te maken](#createnewintegration).

   ![Download Certificate](assets/ims-config3.png)

1. Klik op **[!UICONTROL Next]**.

   Maak op het tabblad **Account** het Adobe IMS-account. Hiervoor hebt u echter de integratiedetails nodig. Laat deze pagina voorlopig open.

   Open een nieuw tabblad en [maak een Adobe I/O-integratie](#createnewintegration) om de integratiedetails voor IMS-accountconfiguraties op te halen.

### Adobe I/O-integratie maken {#createnewintegration}

Bij een Adobe I/O-integratie worden de API-sleutel, het clientgeheim en de payload (JWT) gegenereerd die vereist zijn voor het instellen van de IMS-accountconfiguraties.

1. Meld u aan bij Adobe I/O Console met systeembeheerdersbevoegdheden voor de IMS-organisatie van de Brand Portal-tenant.

   Standaard-URL: [https://console.adobe.io/](https://console.adobe.io/)

1. Klik op **[!UICONTROL Integratie]** maken.

1. Selecteer **[!UICONTROL Toegang tot API]**, en klik **[!UICONTROL verdergaan]**.

   ![Create New Integration](assets/create-new-integration1.png)

1. Een pagina voor het maken van een nieuwe integratie wordt geopend.

   Selecteer uw organisatie in de vervolgkeuzelijst.

   Selecteer in **[!UICONTROL Experience Cloud]** de optie **[!UICONTROL AEM Brand Portal]** en klik op **[!UICONTROL Doorgaan]**.

   If the Brand Portal option is disabled for you, ensure that you have selected correct organization from the drop-down box above the **[!UICONTROL Adobe Services]** option. Neem contact op met de beheerder als u uw organisatie niet kent.

   ![Create Integration](assets/create-new-integration2.png)

1. Geef een naam en een beschrijving voor de integratie op. Klik op **[!UICONTROL Een bestand selecteren op uw computer]** en upload het `AEM-Adobe-IMS.crt` bestand dat u hebt gedownload in de sectie [openbare certificaten](#public-certificate) verkrijgen.

1. Selecteer het profiel van uw organisatie.

   Of selecteer het standaardprofiel **[!UICONTROL Assets Brand Portal]** en klik op **[!UICONTROL Integratie]** maken. De integratie wordt gemaakt.

1. Klik op **[!UICONTROL Doorgaan naar integratiegegevens]** om de integratiegegevens weer te geven.

   De **[!UICONTROL API-sleutel kopiëren]**

   Klik op **[!UICONTROL Clientgeheim]** ophalen en kopieer de sleutel Client Secret.

   ![API Key, Client Secret, and payload information of an integration](assets/create-new-integration3.png)

1. Navigeer naar het tabblad **[!UICONTROL JWT]** en kopieer de **[!UICONTROL JWT-lading]**.

   De informatie over de API-sleutel, de sleutel van het clientgeheim en de JWT-payload worden gebruikt om een IMS-accountconfiguratie te maken.

### IMS-accountconfiguratie maken {#create-ims-account-configuration}

Controleer of u de volgende stappen hebt uitgevoerd:

* [Openbaar certificaat verkrijgen](#public-certificate)
* [Adobe I/O-integratie maken](#createnewintegration)

**Stappen om IMS-accountconfiguratie te maken:**

1. Open the IMS Configuration page, **[!UICONTROL Accounts]** tab. U hebt de pagina open gelaten aan het einde van de sectie voor [Openbaar certificaat verkrijgen](#public-certificate).

1. Specify a **[!UICONTROL Title]** for the IMS account.

   In **[!UICONTROL Authorization Server]**, enter the URL: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Plak de API-sleutel, het clientgeheim en de JWT-payload die u hebt gekopieerd aan het einde van [Adobe I/O-integratie maken](#createnewintegration).

   Klik op **[!UICONTROL Maken]**.

   De integratie wordt gemaakt.

   ![IMS Account configuration](assets/create-new-integration6.png)


1. Select the IMS configuration and click **[!UICONTROL Check Health]**. Er wordt een dialoogvenster weergegeven.

   Klik op **[!UICONTROL Controleren]**. Bij een geslaagde verbinding wordt het bericht *Token retrieved successfully* weergegeven.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>U moet slechts één configuratie IMS hebben die de gezondheidscontrole overgaat. Maak geen meerdere IMS-configuraties.
>
>Als de configuratie niet de gezondheidscontrole slaagt, is het ongeldig. U moet het schrappen en een nieuwe, geldige configuratie creëren.



### Cloudservice configureren {#configure-the-cloud-service}

Voer de volgende stappen uit om de configuratie van de Brand Portal-cloudservice te maken:

1. Meld u aan bij uw AEM Assets-cloudinstantie..

1. Navigeer vanuit het deelvenster **Gereedschappen** ![Gereedschappen](assets/tools.png) naar **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**.

   De pagina Brand Portal Configurations wordt geopend.

1. Klik op **[!UICONTROL Maken]**.

1. Specify a **[!UICONTROL Title]** for the configuration.

   Selecteer de IMS-configuratie die u in de stap [IMS-accountconfiguratie maken](#create-ims-account-configuration) hebt gemaakt.

   In **[!UICONTROL Service URL]**, enter your Brand Portal tenant URL.

   ![](assets/create-cloud-service.png)

1. Klik op **[!UICONTROL Opslaan en Sluiten]**. De cloudconfiguratie wordt gemaakt. Uw AEM Assets-cloudinstantie is nu geconfigureerd met de Brand Portal-tenant.

### Configuratie testen {#test-configuration}

1. Meld u aan bij uw AEM Assets-cloudinstantie.

1. Navigeer vanuit het deelvenster **Gereedschappen** ![Gereedschappen](assets/tools.png) naar **[!UICONTROL Implementatie]** > **[!UICONTROL Distributie]**.

   ![](assets/test-bpconfig1.png)

1. De pagina Distribution wordt geopend.

   Een distributieagent van het Portaal van het Merk `bpdistributionagent0` wordt gecreeerd onder **[!UICONTROL Publish aan het Portaal]** van het Merk.

   Klik op **[!UICONTROL Publiceren naar Brand Portal]**.

   ![](assets/test-bpconfig2.png)

   >[!NOTE]
   >
   >Standaard wordt één distributieagent gemaakt voor een Brand Portal-tenant.

1. De pagina Distribution Agent wordt geopend. By default, the **[!UICONTROL Status]** tab opens which populates the distribution queues.

   Een distributieagent bevat twee wachtrijen:
   * **verwerkingswachtrij**: voor de distributie van activa aan Brand Portal.

   * **error-queue**: voor de activa waar de distributie is mislukt.
   >[!NOTE]
   >
   >Het wordt aanbevolen om de fouten te controleren en de **foutopsporingswachtrij** regelmatig te wissen.

   ![](assets/test-bpconfig3.png)

1. To verify the connection between AEM Assets and Brand Portal, click **[!UICONTROL Test Connection]**.

   ![](assets/test-bpconfig4.png)

   Onder aan de pagina wordt een bericht weergegeven dat het testpakket is geleverd.

   >[!NOTE]
   >
   >Schakel de distributieagent niet uit, want dit kan de distributie van de assets (die actief zijn in de wachtrij) doen mislukken.


De AEM Assets cloud-instantie is geconfigureerd met het Brand Portal. U kunt nu:

* [Assets publiceren van AEM Assets naar Brand Portal](publish-to-brand-portal.md)
* [Mappen publiceren van AEM Assets naar Brand Portal](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Verzamelingen publiceren van AEM Assets naar Brand Portal](publish-to-brand-portal.md#publish-collections-to-brand-portal)

Naast het bovenstaande kunt u ook schema&#39;s voor metagegevens, voorinstellingen voor afbeeldingen, zoekfacetten en tags van AEM-middelen naar Brand Portal publiceren.

* [Voorinstellingen, schema&#39;s en facetten publiceren naar Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [Tags publiceren naar Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)


Raadpleeg de documentatie [van het](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) Brand Portal voor meer informatie.


## Distributielogboeken {#distribution-logs}

U kunt de logboeken controleren voor gedetailleerde informatie over de acties die op de distributieagent worden uitgevoerd.

We hebben bijvoorbeeld een asset van AEM Assets naar Brand Portal gepubliceerd om de configuratie te controleren.

1. Follow the steps (Step 1 - 4) as shown in **[!UICONTROL Test Connection]** and navigate to the distribution agent page.

1. Klik op **[!UICONTROL Logboeken]** om de distributielogboeken weer te geven. Hier ziet u de logboeken voor verwerking en fouten.

   ![](assets/test-bpconfig5.png)

De distributieagent genereert de volgende logboeken:

* INFO: Dit is een systeem geproduceerd logboek dat op succesvolle configuratie teweegbrengt die de distributieagent toelaat.
* DSTRQ1 (verzoek 1): Triggers op testverbinding.

Bij het publiceren van de asset worden de volgende aanvraag- en antwoordlogboeken gegenereerd:

**Aanvraag van distributieagent**:
* DSTRQ2 (aanvraag 2): de aanvraag voor het publiceren van de asset wordt geactiveerd.
* DSTRK3 (verzoek 3): Het systeem activeert een andere aanvraag om de map te publiceren waarin het element bestaat en repliceert de map in Brand Portal.

**Antwoord van distributieagent**:
* queue-bpdistributionagent0 (DSTRQ2): de asset wordt gepubliceerd naar Brand Portal.
* queue-bpdistributionagent0 (DSTRQ3): het systeem repliceert de map met de asset in Brand Portal.

In het bovenstaande voorbeeld worden een aanvullende aanvraag en reactie geactiveerd. Het systeem kan de bovenliggende map (ook wel Pad toevoegen genoemd) niet vinden in Brand Portal, omdat het element voor het eerst is gepubliceerd. Daarom wordt een aanvullende aanvraag geactiveerd om een bovenliggende map met dezelfde naam te maken in Brand Portal waar het element wordt gepubliceerd.

>[!NOTE]
>
>Er wordt een aanvullend verzoek gegenereerd als de bovenliggende map niet bestaat in Brand Portal (in het bovenstaande voorbeeld) of als de bovenliggende map is gewijzigd in AEM Assets.



<!--

## Additional information {#additional-information}

Go to `/system/console/slingmetrics` for statistics related to the distributed content:

1. **Counter metrics**
   * sling: `mac_sync_request_failure`
   * sling: `mac_sync_request_received`
   * sling: `mac_sync_request_success`

1. **Time metrics**
   * sling: `mac_sync_distribution_duration`
   * sling: `mac_sync_enqueue_package_duration`
   * sling: `mac_sync_setup_request_duration`

-->

<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->
