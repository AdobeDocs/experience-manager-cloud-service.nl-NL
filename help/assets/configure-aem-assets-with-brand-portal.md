---
title: AEM Assets as a Cloud Service configureren met Brand Portal
description: AEM Assets as a Cloud Service configureren met Brand Portal.
contentOwner: Vishabh Gupta
translation-type: ht
source-git-commit: bbb3327d4bc7cef8eede3169bc14a1d247ee2bdc

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

U kunt een configuratie maken op de Adobe I/O om uw AEM Assets-cloudinstantie te configureren met Brand Portal.

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

1. Meld u aan bij uw AEM Assets-cloudinstantie.

1. Ga vanuit het deelvenster **Tools** ![Tools](assets/tools.png) naar **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.

   ![Gebruikersinterface voor Adobe IMS-accountconfiguratie](assets/ims-configuration1.png)

1. De pagina Adobe IMS Configurations wordt geopend.

   Klik op **[!UICONTROL Create]**.

   Hiermee gaat u naar de pagina **[!UICONTROL Adobe IMS Technical Account Configuration]**.

1. Standaard wordt het tabblad **Certificate** geopend.

   Selecteer in **Cloud Solution** de optie **[!UICONTROL Adobe Brand Portal]**.

1. Schakel het selectievakje **[!UICONTROL Create new certificate]** in en geef een **alias** op voor het certificaat. De alias fungeert als naam voor het dialoogvenster.

1. Klik op **[!UICONTROL Create certificate]**. Er wordt een dialoogvenster weergegeven. Klik op **[!UICONTROL OK]** om het openbare certificaat te genereren.

   ![Create Certificate](assets/ims-config2.png)

1. Klik op **[!UICONTROL Download Public Key]** en sla het certificaatbestand *AEM-Adobe-IMS.crt* op uw computer op. Het certificaatbestand wordt gebruikt om [Adobe I/O-integratie te maken](#createnewintegration).

   ![Download Certificate](assets/ims-config3.png)

1. Klik op **[!UICONTROL Next]**.

   Maak op het tabblad **Account** het Adobe IMS-account. Hiervoor hebt u echter de integratiedetails nodig. Laat deze pagina voorlopig open.

   Open een nieuw tabblad en [maak een Adobe I/O-integratie](#createnewintegration) om de integratiedetails voor IMS-accountconfiguraties op te halen.

### Adobe I/O-integratie maken {#createnewintegration}

Bij een Adobe I/O-integratie worden de API-sleutel, het clientgeheim en de payload (JWT) gegenereerd die vereist zijn voor het instellen van de IMS-accountconfiguraties.

1. Meld u aan bij Adobe I/O Console met systeembeheerdersbevoegdheden voor de IMS-organisatie van de Brand Portal-tenant.

   Standaard-URL: [https://console.adobe.io/](https://console.adobe.io/)

1. Klik op **[!UICONTROL Create Integration]**.

1. Selecteer **[!UICONTROL Access an API]** en klik op **[!UICONTROL Continue]**.

   ![Create New Integration](assets/create-new-integration1.png)

1. Een pagina voor het maken van een nieuwe integratie wordt geopend.

   Selecteer uw organisatie in de vervolgkeuzelijst.

   Selecteer in **[!UICONTROL Experience Cloud]** de optie **[!UICONTROL AEM Brand Portal]** en klik op **[!UICONTROL Continue]**.

   Als de optie Brand Portal voor u is uitgeschakeld, controleert u of u de juiste organisatie hebt geselecteerd in het keuzemenu boven de optie **[!UICONTROL Adobe Services]**. Neem contact op met de beheerder als u uw organisatie niet kent.

   ![Create Integration](assets/create-new-integration2.png)

1. Geef een naam en een beschrijving voor de integratie op. Klik op **[!UICONTROL Select a File from your computer]** en upload het bestand `AEM-Adobe-IMS.crt` dat u hebt gedownload in de sectie voor het [verkrijgen van openbare certificaten](#public-certificate).

1. Selecteer het profiel van uw organisatie.

   Of selecteer het standaardprofiel **[!UICONTROL Assets Brand Portal]** en klik op **[!UICONTROL Create Integration]**. De integratie wordt gemaakt.

1. Klik op **[!UICONTROL Continue to integration details]** om de integratiegegevens weer te geven.

   Kopieer de **[!UICONTROL API Key]**

   Klik op **[!UICONTROL Retrieve Client Secret]** en kopieer de sleutel van het clientgeheim.

   ![API Key, Client Secret, and payload information of an integration](assets/create-new-integration3.png)

1. Ga naar het tabblad **[!UICONTROL JWT]** en kopieer de **[!UICONTROL JWT payload]**.

   De informatie over de API-sleutel, de sleutel van het clientgeheim en de JWT-payload worden gebruikt om een IMS-accountconfiguratie te maken.

### IMS-accountconfiguratie maken {#create-ims-account-configuration}

Controleer of u de volgende stappen hebt uitgevoerd:

* [Openbaar certificaat verkrijgen](#public-certificate)
* [Adobe I/O-integratie maken](#createnewintegration)

**Stappen om IMS-accountconfiguratie te maken:**

1. Open op de pagina IMS Configuration het tabblad **[!UICONTROL Accounts]**. U hebt de pagina open gelaten aan het einde van de sectie voor [Openbaar certificaat verkrijgen](#public-certificate).

1. Geef een **[!UICONTROL Title]** op voor het IMS-account.

   Voer in **[!UICONTROL Authorization Server]** de volgende URL in: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Plak de API-sleutel, het clientgeheim en de JWT-payload die u hebt gekopieerd aan het einde van [Adobe I/O-integratie maken](#createnewintegration).

   Klik op **[!UICONTROL Create]**.

   De integratie wordt gemaakt.

   ![IMS Account configuration](assets/create-new-integration6.png)


1. Selecteer de IMS-configuratie en klik op **[!UICONTROL Check Health]**. Er wordt een dialoogvenster weergegeven.

   Klik op **[!UICONTROL Check]**. Bij een geslaagde verbinding wordt het bericht *Token retrieved successfully* weergegeven.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>U kunt slechts één IMS-configuratie hebben. Maak geen meerdere IMS-configuraties.
>
>Zorg ervoor dat de IMS-configuratie slaagt voor de statuscontrole. Als de configuratie niet slaagt voor de statuscontrole, is deze ongeldig. U moet deze dan verwijderen en een nieuwe, geldige configuratie maken.



### Cloudservice configureren {#configure-the-cloud-service}

Voer de volgende stappen uit om de configuratie van de Brand Portal-cloudservice te maken:

1. Meld u aan bij uw AEM Assets-cloudinstantie.

1. Ga vanuit het deelvenster **Tools** ![Tools](assets/tools.png) naar **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**.

   De pagina Brand Portal Configurations wordt geopend.

1. Klik op **[!UICONTROL Create]**.

1. Geef een **[!UICONTROL Title]** op voor de configuratie.

   Selecteer de IMS-configuratie die u in de stap [IMS-accountconfiguratie maken](#create-ims-account-configuration) hebt gemaakt.

   Voer in **[!UICONTROL Service URL]** de URL van uw Brand Portal-tenant in.

   ![](assets/create-cloud-service.png)

1. Klik op **[!UICONTROL Save and Close]**. De cloudconfiguratie wordt gemaakt. Uw AEM Assets-cloudinstantie is nu geconfigureerd met de Brand Portal-tenant.

### Configuratie testen {#test-configuration}

1. Meld u aan bij uw AEM Assets-cloudinstantie.

1. Ga vanuit het deelvenster **Tools** ![Tools](assets/tools.png) naar **[!UICONTROL Deployment]** > **[!UICONTROL Distribution]**.

   ![](assets/test-bpconfig1.png)

1. De pagina Distribution wordt geopend.

   Een Brand Portal-distrubutieagent `bpdistributionagent0` wordt gemaakt onder **[!UICONTROL Publish to Brand Portal]**.

   Klik op **[!UICONTROL Publish to Brand Portal]**.

   ![](assets/test-bpconfig2.png)

   >[!NOTE]
   >
   >Standaard wordt één distributieagent gemaakt voor een Brand Portal-tenant.

1. De pagina Distribution Agent wordt geopend. Standaard wordt het tabblad **[!UICONTROL Status]** geopend waarin de distributiewachtrijen zijn vermeld.

   Een distributieagent bevat twee wachtrijen:
   * **verwerkingswachtrij**: voor de distributie van assets naar Brand Portal.

   * **foutenwachtrij**: voor de assets waarvoor de distributie is mislukt.
   >[!NOTE]
   >
   >Het wordt aanbevolen om de fouten te controleren en de **foutenwachtrij** regelmatig te wissen.

   ![](assets/test-bpconfig3.png)

1. Klik op **[!UICONTROL Test Connection]** om de verbinding tussen AEM Assets en Brand Portal te controleren.

   ![](assets/test-bpconfig4.png)

   Onder aan de pagina wordt een bericht weergegeven dat het testpakket is geleverd.

   >[!NOTE]
   >
   >Schakel de distributieagent niet uit, want dit kan de distributie van de assets (die actief zijn in de wachtrij) doen mislukken.


De AEM Assets-cloudinstantie is geconfigureerd met het Brand Portal. U kunt nu:

* [Assets publiceren van AEM Assets naar Brand Portal](publish-to-brand-portal.md)
* [Mappen publiceren van AEM Assets naar Brand Portal](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Verzamelingen publiceren van AEM Assets naar Brand Portal](publish-to-brand-portal.md#publish-collections-to-brand-portal)

Naast het bovenstaande kunt u ook schema&#39;s voor metadata, voorinstellingen voor afbeeldingen, zoekfacetten en tags van AEM Assets naar Brand Portal publiceren.

* [Voorinstellingen, schema&#39;s en facetten publiceren naar Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [Tags publiceren naar Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)


Raadpleeg de [Brand Portal-documentatie](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) voor meer informatie.


## Distributielogboeken {#distribution-logs}

U kunt de logboeken controleren voor gedetailleerde informatie over de acties die op de distributieagent worden uitgevoerd.

We hebben bijvoorbeeld een asset van AEM Assets naar Brand Portal gepubliceerd om de configuratie te controleren.

1. Volg de stappen (stap 1 tot en met 4) zoals weergegeven in **[!UICONTROL Test Connection]** en ga naar de pagina van de distributieagent.

1. Klik op **[!UICONTROL Logs]** om de distributielogboeken te bekijken. Hier ziet u de logboeken voor verwerking en fouten.

   ![](assets/test-bpconfig5.png)

De distributieagent genereert de volgende logboeken:

* INFO: dit is een door het systeem gegenereerd logboek dat wordt geactiveerd bij een succesvolle configuratie waardoor de distributieagent wordt ingeschakeld.
* DSTRQ1 (aanvraag 1): geactiveerd tijdens testverbinding.

Bij het publiceren van de asset worden de volgende aanvraag- en antwoordlogboeken gegenereerd:

**Aanvraag van distributieagent**:
* DSTRQ2 (aanvraag 2): de aanvraag voor het publiceren van de asset wordt geactiveerd.
* DSTRQ3 (aanvraag 3): het systeem activeert nog een aanvraag om de map met de asset te publiceren en repliceert de map in Brand Portal.

**Antwoord van distributieagent**:
* queue-bpdistributionagent0 (DSTRQ2): de asset wordt gepubliceerd naar Brand Portal.
* queue-bpdistributionagent0 (DSTRQ3): het systeem repliceert de map met de asset in Brand Portal.

In het bovenstaande voorbeeld worden een aanvullende aanvraag en een aanvullend antwoord geactiveerd. Het systeem kan de bovenliggende map (ook wel Pad toevoegen genaamd) niet vinden in Brand Portal, omdat de asset voor het eerst is gepubliceerd. Daarom wordt een extra aanvraag geactiveerd om een bovenliggende map met dezelfde naam te maken in Brand Portal waar de asset wordt gepubliceerd.

>[!NOTE]
>
>Er wordt een aanvullende aanvraag gegenereerd als de bovenliggende map niet bestaat in Brand Portal (in het bovenstaande voorbeeld) of als de bovenliggende map is gewijzigd in AEM Assets.



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
