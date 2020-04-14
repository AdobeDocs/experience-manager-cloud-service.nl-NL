---
title: AEM Assets-cloudservice configureren met Brand Portal
description: AEM Assets cloud service configureren met Brand Portal.
contentOwner: Vishabh Gupta
translation-type: tm+mt
source-git-commit: f57731e4ab30af1bfcd93a12b2cf80e63efdac79

---


# AEM-middelen configureren met Brand Portal {#configure-aem-assets-with-brand-portal}

Adobe Experience Manager-middelen (AEM) worden geconfigureerd met Brand Portal via Adobe I/O, dat een IMS-token aanschaft voor toestemming van uw Brand Portal-huurder.

## Vereisten {#prerequisites}

U hebt het volgende nodig om AEM-middelen te configureren met Brand Portal:

* Een AEM Assets-cloudinstantie die wordt uitgevoerd.
* URL van medewerker van Brand Portal.
* Een gebruiker met de bevoegdheden van de systeembeheerder op de IMS-organisatie van de Poorthuurder van het Merk.

**Neem contact op met de ondersteuningsafdeling** voor meer informatie.

## Configuratie maken {#create-new-configuration}

U kunt een nieuwe configuratie maken op de Adobe I/O om uw AEM Assets cloud-instantie te configureren met behulp van Brand Portal.

Voer de volgende stappen in de vermelde reeks uit:
1. [Openbaar certificaat verkrijgen](#public-certificate)
1. [Adobe I/O-integratie maken](#createnewintegration)
1. [IMS-accountconfiguratie maken](#create-ims-account-configuration)
1. [Cloudservice configureren](#configure-the-cloud-service)
1. [Testconfiguratie](#test-configuration)

### IMS-configuratie maken {#create-ims-configuration}

IMS-configuratie verifieert uw Brand Portal-huurder met de auteur-instantie van AEM Assets.

De IMS-configuratie omvat twee stappen:

* [Openbaar certificaat verkrijgen](#public-certificate)
* [IMS-accountconfiguratie maken](#create-ims-account-configuration)

### Openbaar certificaat verkrijgen {#public-certificate}

Met een openbaar certificaat kunt u uw profiel verifiëren op Adobe I/O.

1. Aanmelden bij de cloud-instantie van AEM Assets

1. Navigeer vanuit het deelvenster **Gereedschappen** ![Gereedschappen](assets/tools.png) naar **[!UICONTROL Beveiliging]** > **[!UICONTROL Adobe IMS-configuraties]**.

   ![Gebruikersinterface voor configuratie van Adobe IMS-account](assets/ims-configuration1.png)

1. De pagina Adobe IMS Configurations wordt geopend.

   Klik op **[!UICONTROL Maken]**.

   Hiermee gaat u naar de pagina Configuratie **[!UICONTROL technische account van]** Adobe IMS.

1. Standaard wordt het tabblad **Certificaat** geopend.

   Selecteer in **Cloudoplossing** de optie **[!UICONTROL Adobe Brand Portal]**.

1. Markeer het selectievakje **[!UICONTROL Nieuw certificaat]** maken en geef een **alias** voor het certificaat op. De alias fungeert als naam voor het dialoogvenster.

1. Klik op **[!UICONTROL Certificaat]** maken. Er wordt een dialoogvenster weergegeven. Klik op **[!UICONTROL OK]** om het openbare certificaat te genereren.

   ![Certificaat maken](assets/ims-config2.png)

1. Klik op Openbare sleutel **** downloaden en sla het certificaatbestand *AEM-Adobe-IMS.crt* op uw computer op. Het certificaatbestand wordt gebruikt om Adobe I/O-integratie [te](#createnewintegration)maken.

   ![Certificaat downloaden](assets/ims-config3.png)

1. Click **[!UICONTROL Next]**.

   Op het tabblad **Account** maakt u het Adobe IMS-account, maar hiervoor hebt u de integratiegegevens nodig. Laat deze pagina voorlopig open.

   Open een nieuw tabblad en [maak Adobe I/O-integratie](#createnewintegration) om de integratiegegevens voor IMS-accountconfiguraties op te halen.

### Adobe I/O-integratie maken {#createnewintegration}

Bij de integratie met Adobe I/O worden API-sleutel, clientgeheim en Payload (JWT) gegenereerd die vereist zijn voor het instellen van de IMS-accountconfiguraties.

1. Meld u aan bij de Adobe I/O-console met systeembeheerdersrechten voor de IMS-organisatie van de Poorthuurder van het merk.

   Standaard-URL: [https://console.adobe.io/](https://console.adobe.io/)

1. Klik op **[!UICONTROL Integratie]** maken.

1. Selecteer **[!UICONTROL Toegang tot API]**, en klik **[!UICONTROL verdergaan]**.

   ![Nieuwe integratie maken](assets/create-new-integration1.png)

1. Maak een nieuwe integratiepagina die wordt geopend.

   Selecteer uw organisatie in de vervolgkeuzelijst.

   Selecteer in **[!UICONTROL Experience Cloud]** de optie **[!UICONTROL AEM Brand Portal]** en klik op **[!UICONTROL Doorgaan]**.

   Als de optie Brand Portal voor u is uitgeschakeld, controleert u of u de juiste organisatie hebt geselecteerd in het keuzemenu boven de optie **[!UICONTROL Adobe Services]** . Neem contact op met de beheerder als u uw organisatie niet kent.

   ![Integratie maken](assets/create-new-integration2.png)

1. Geef een naam en beschrijving voor de integratie op. Klik op **[!UICONTROL Een bestand selecteren op uw computer]** en upload het `AEM-Adobe-IMS.crt` bestand dat u hebt gedownload in de sectie [openbare certificaten](#public-certificate) verkrijgen.

1. Selecteer het profiel van uw organisatie.

   Of selecteer het standaardprofiel **[!UICONTROL Assets Brand Portal]** en klik op **[!UICONTROL Integratie]** maken. De integratie wordt tot stand gebracht.

1. Klik op **[!UICONTROL Doorgaan naar integratiegegevens]** om de integratiegegevens weer te geven.

   De **[!UICONTROL API-sleutel kopiëren]**

   Klik op **[!UICONTROL Clientgeheim]** ophalen en kopieer de sleutel Client Secret.

   ![API-sleutel, clientgeheim en payload-informatie van een integratie](assets/create-new-integration3.png)

1. Navigeer naar het tabblad **[!UICONTROL JWT]** en kopieer de **[!UICONTROL JWT-lading]**.

   De API Sleutel, de Geheime sleutel van de Cliënt, en JWT ladinginformatie zullen worden gebruikt om IMS rekeningsconfiguratie tot stand te brengen.

### IMS-accountconfiguratie maken {#create-ims-account-configuration}

Controleer of u de volgende stappen hebt uitgevoerd:

* [Openbaar certificaat verkrijgen](#public-certificate)
* [Adobe I/O-integratie maken](#createnewintegration)

**Stappen om IMS-accountconfiguratie te maken:**

1. Open de IMS-configuratiepagina, tabblad **[!UICONTROL Accounts]** . U hebt de pagina geopend aan het einde van de sectie. [Overheidscertificaat](#public-certificate)verkrijgen.

1. Geef een **[!UICONTROL titel]** op voor de IMS-account.

   Voer in **[!UICONTROL Autorisatieserver]** de URL in: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Plak de API-sleutel, de clientgeheim en de JWT-payload die u hebt gekopieerd aan het einde van de [Adobe I/O-integratie](#createnewintegration)maken.

   Klik op **[!UICONTROL Maken]**.

   De integratie wordt gecreeerd.

   ![IMS-accountconfiguratie](assets/create-new-integration6.png)


1. Selecteer de IMS-configuratie en klik op **[!UICONTROL Health]** controleren. Er wordt een dialoogvenster weergegeven.

   Klik op **[!UICONTROL Controleren]**. Bij een geslaagde verbinding wordt het bericht *Met succes* opgehaalde token weergegeven.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>Maak slechts één geldige IMS-configuratie.
>
> Zorg ervoor dat de configuratie gezond is. Als de configuratie ongezond is, verwijdert u deze en maakt u een nieuwe, gezonde configuratie.


### Cloudservice configureren {#configure-the-cloud-service}

Voer de volgende stappen uit om de configuratie van de Brand Portal-cloudservice te maken:

1. Aanmelden bij de cloud-instantie van AEM Assets

1. Navigeer vanuit het deelvenster **Gereedschappen** ![Gereedschappen](assets/tools.png) naar **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**.

   De pagina van de Configuraties van het Merk Portaal opent.

1. Klik op **[!UICONTROL Maken]**.

1. Geef een **[!UICONTROL titel]** op voor de configuratie.

   Selecteer de IMS-configuratie die u in de stap hebt gemaakt, [maak de IMS-accountconfiguratie](#create-ims-account-configuration).

   Voer in **[!UICONTROL Service-URL]** de URL van de huurder van uw Brand Portal in.

   ![](assets/create-cloud-service.png)

1. Klik op **[!UICONTROL Opslaan en Sluiten]**. De cloudconfiguratie wordt gemaakt. Uw AEM-middelenwolkeninstantie is nu geconfigureerd met de Brand Portal-gebruiker.

### Testconfiguratie {#test-configuration}

1. Meld u aan bij uw AEM Assets cloud-instantie.

1. Navigeer vanuit het deelvenster **Gereedschappen** ![Gereedschappen](assets/tools.png) naar **[!UICONTROL Implementatie]** > **[!UICONTROL Distributie]**.

   ![](assets/test-bpconfig1.png)

1. De pagina Distribution wordt geopend.

   Een distributieagent van het Portaal van het Merk `bpdistributionagent0` wordt gecreeerd onder **[!UICONTROL Publish aan het Portaal]** van het Merk.

   Klik op **[!UICONTROL Publiceren naar Brand Portal]**.

   ![](assets/test-bpconfig2.png)

   >[!NOTE]
   >
   >Door gebrek, wordt één distributieagent gecreeerd voor een huurder van het Portaal van het Merk.

1. De pagina van de distributieagent opent. Standaard wordt het tabblad **[!UICONTROL Status]** geopend, waarin de distributielijnen worden gevuld.

   Een distributieagent bevat twee rijen:
   * A processing queue for distribution of assets to Brand Portal.
   * Een foutwachtrij voor de elementen waarbij de distributie is mislukt.
   ![](assets/test-bpconfig3.png)

1. Klik op Verbinding **[!UICONTROL testen om de verbinding tussen AEM-middelen en Brand Portal te controleren]**.

   ![](assets/test-bpconfig4.png)

   Onder aan de pagina wordt een bericht weergegeven dat het testpakket is geleverd.

   >[!NOTE]
   >
   >Vermijd het onbruikbaar maken van de distributieagent, aangezien het de distributie van de activa (lopende-in-rij) kan veroorzaken om te ontbreken.


De AEM Assets cloud-instantie is geconfigureerd met het Brand Portal. U kunt nu:

* [Elementen publiceren van AEM Assets naar Brand Portal](publish-to-brand-portal.md)
* [Mappen publiceren van AEM Assets naar Brand Portal](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Verzamelingen publiceren van AEM Assets naar Brand Portal](publish-to-brand-portal.md#publish-collections-to-brand-portal)

Naast het bovenstaande kunt u ook schema&#39;s voor metagegevens, voorinstellingen voor afbeeldingen, zoekfacetten en tags van AEM-middelen naar Brand Portal publiceren.

* [Voorinstellingen, schema&#39;s en facetten publiceren naar Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [Tags publiceren naar Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)


Raadpleeg de documentatie [van het](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) Brand Portal voor meer informatie.


## Distributielogboeken {#distribution-logs}

U kunt de logboeken voor gedetailleerde informatie over de acties controleren die op de verdelingsagent worden uitgevoerd.

We hebben bijvoorbeeld een middel van AEM Assets naar Brand Portal gepubliceerd om de configuratie te controleren.

1. Volg de stappen (Stap 1 tot 4) zoals aangetoond in de Verbinding **[!UICONTROL van de]** Test en navigeer aan de pagina van de distributiegagent.

1. Klik op **[!UICONTROL Logboeken]** om de distributielogboeken weer te geven. Hier ziet u de logboeken voor verwerking en fouten.

   ![](assets/test-bpconfig5.png)

De distributieagent produceert de volgende logboeken:

* INFO: Dit is een systeem geproduceerd logboek dat op succesvolle configuratie wordt teweeggebracht die de distributieagent toelaat.
* DSTRQ1 (verzoek 1): Trigged on test connection.

Bij het publiceren van het element worden de volgende aanvraag- en responslogboeken gegenereerd:

**Verzoek** van distributieagent:
* DSTRQ2 (verzoek 2): De aanvraag voor het publiceren van activa wordt geactiveerd.
* DSTRK3 (verzoek 3): Het systeem activeert een andere aanvraag om de map te publiceren waarin het element bestaat en repliceert de map in Brand Portal.

**Respons** van de distributieagent:
* queue-bpdistributionagent0 (DSTRQ2): Het middel wordt gepubliceerd aan het Portaal van het Merk.
* queue-bpdistributionagent0 (DSTRQ3): Het systeem repliceert de map met het element in Brand Portal.

In het bovenstaande voorbeeld wordt een aanvullende aanvraag en reactie geactiveerd. Het systeem kan de bovenliggende map (ook wel Pad toevoegen genoemd) niet vinden in Brand Portal, omdat het element voor het eerst is gepubliceerd. Daarom wordt een extra aanvraag geactiveerd om een bovenliggende map met dezelfde naam te maken in Brand Portal waar het element wordt gepubliceerd.

>[!NOTE]
>
>Er wordt een aanvullend verzoek gegenereerd als de bovenliggende map niet bestaat in Brand Portal (in het bovenstaande voorbeeld) of als de bovenliggende map is gewijzigd in AEM Assets.


## Extra informatie {#additional-information}

Ga naar `/system/console/slingmetrics` voor statistieken met betrekking tot de verdeelde inhoud:

1. **Metriek**
   * sling: `mac_sync_request_failure`
   * sling: `mac_sync_request_received`
   * sling: `mac_sync_request_success`

1. **Tijdsmetriek**
   * sling: `mac_sync_distribution_duration`
   * sling: `mac_sync_enqueue_package_duration`
   * sling: `mac_sync_setup_request_duration`



<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->
