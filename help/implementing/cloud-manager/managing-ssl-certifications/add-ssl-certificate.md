---
title: Een SSL-certificaat toevoegen
description: Leer hoe u uw eigen SSL-certificaat of een DV-certificaat (Domain Validation) voor Adobe kunt toevoegen met de zelfbedieningsprogramma's van Cloud Manager.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f12392075b71b219bf449f585f63561167ddada9
workflow-type: tm+mt
source-wordcount: '1000'
ht-degree: 0%

---


# Een SSL-certificaat toevoegen {#add-ssl-cert}

Leer hoe u uw eigen SSL-certificaat of een door Adobe beheerd DV-certificaat (Domain Validation) toevoegt met Cloud

>[!NOTE]
>
>Als u een klant beheerde (OV/EV) SSL certificaat en een klant beheerde leverancier CDN gebruikt, kunt u overslaan toevoegend een SSL certificaat en direct gaan [ een configuratie CDN ](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md) toevoegen wanneer klaar.

Het indienen van een certificaat kan enkele dagen in beslag nemen. Daarom raadt de Adobe u aan uw eigen certificaat ruim vóór om het even welke termijn of go-live datum in te richten om vertragingen te vermijden.

Om over het bijwerken van en het beheren van uw SSL certificaten in Cloud Manager te leren, zie [ SSL certificaten beheren ](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md).

Als u kwesties hebt die of uw certificaten toevoegen beheren, zie [ SSL certificaatfouten oplossen ](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md).


## Vereisten {#prerequisites}

* Een gebruiker moet een lid van de **BedrijfsEigenaar** of **rol van de Manager van de Plaatsing** zijn om een SSL certificaat toe te voegen.
* Als u uw eigen certificaat installeert, zie {de vereisten van het 0} Certificaat **in [ Inleiding aan het Leiden SSL Certificaten ](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md#requirements).**

## Selecteren welk SSL-certificaat moet worden toegevoegd {#which-ssl-to-add}

Na [ toevoegend een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) in AEM Cloud Manager, hangt de volgende stap af van of u verkoos om een Adobe te gebruiken geleid (DV) SSL certificaat (geadviseerd) of een klant beheerde (OV/EV) SSL certificaat.

* **voor een beheerde Adobe (DV) SSL certificaat:**
   * Het proces voor domeinvalidatie wordt uitgevoerd zodra het aangepaste domein is toegevoegd en geverifieerd in Cloud Manager.
   * Nu, moet u [ een beheerde Adobe (DV) SSL certificaat ](#add-adobe-managed-ssl-cert) toevoegen.
Zodra u het DV SSL-certificaat hebt toegevoegd aan Cloud Manager, wacht u tot Adobe het DV SSL-certificaat namens u heeft uitgegeven en geïnstalleerd.
   * Wanneer het certificaat actief is, kunt u het aangepaste domein gebruiken.

* **voor een klant beheerde (OV/EV) SSL certificaat:**

   * Vraag uw OV/EV SSL-certificaat aan bij een certificeringsinstantie. Voor meer details, herzie de [ vereisten voor klant beheerde OV/EV SSL certificaten ](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md#requirements).
   * Na het verwerven van het certificaat, [ voeg uw klant beheerde (OV/EV) SSL certificaat ](#add-customer-manage-ssl-cert) details in Cloud Manager toe.
   * Nadat de aangepaste domeinnaam is toegevoegd, wordt deze gemarkeerd als geverifieerd en wordt het SSL-certificaat toegepast.

In beide gevallen is het aangepaste domein beschikbaar voor veilig gebruik in uw omgeving nadat het certificaat is geverifieerd en geïnstalleerd. Zorg ervoor om [ de status van het domein ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) in de interface van Cloud Manager regelmatig te controleren om alles te bevestigen zoals verwacht werkt.

Zie ook [ Inleiding aan SSL Certificaten ](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md).

## Een DV (Adobe managed SSL)-certificaat toevoegen {#add-adobe-managed-ssl-cert}

Hebt u hulp nodig bij het kiezen of u een door Adobe beheerd SSL-certificaat (aanbevolen) of een door de klant beheerd SSL-certificaat met uw domein wilt gebruiken? Zie [ Kiezen welk SSL certificaat om toe te voegen ](#which-ssl-to-add)

**om een beheerde Adobe (DV) toe te voegen SSL certificaat:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer het aangewezen programma.
1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.
1. In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het zijmenu te openbaren.

1. Onder de **rubriek van de Diensten**, klik ![ Slot gesloten pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL Certificaten**.

   ![ Toevoegend een SSL certificaat ](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. Vlak de hoger-juiste hoek van de SSL pagina van Certificaten, klik **SSL Certificaat** toevoegen.

1. In **voeg SSL certificaat** dialoogdoos toe, die op [ uw bijzonder gebruiksgeval ](#which-ssl-to-add) wordt gebaseerd, uitgezochte **beheerde Adobe (DV)**.

   ![ voeg een DV- certificaat toe ](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)

1. Op het **gebied van de Naam van het Certificaat**, ga een naam in u verbonden aan het DV SSL certificaat wilt.

1. In de **Uitgezochte domeinen** drop-down lijst, selecteer één of meerdere geverifieerde domeinen die u verbonden aan het DV SSL certificaat wilt.
   * Geen domeinen om te selecteren? Als dat het geval is, moet u eerst een aangepaste domeinnaam toevoegen en controleren of deze is geverifieerd voordat u een SSL-certificaat kunt toevoegen.
   * Zie [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen.
   * Wanneer u wordt gebeëindigd toevoegend een naam van het douanedomein, terugkeer aan dit onderwerp en begin opnieuw bij stap 1.

1. In de laag-juiste hoek van de dialoogdoos, klik **sparen**.

   Nadat het SSL certificaat met succes wordt uitgegeven, wordt het getoond met een groen Geldig vinkje in de **SSL Certificaten** lijst.

U hebt nu een werkende Adobe geleid DV SSL certificaat voor uw project toegevoegd. Deze stap is vaak de eerste die een aangepaste domeinnaam instelt.

U bent nu klaar om de configuratie van a [ CDN ](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md) toe te voegen.

## Een door de klant beheerd (OV/ED) SSL-certificaat toevoegen {#add-customer-managed-ssl-cert}

<!-- IF THIS TOPIC GET UPDATED, REMEMBER TO UPDATE THE STEPS ALSO IN THE "MANAGE SSL CERTIFICATES TOPIC TOO -->

Hebt u hulp nodig bij het kiezen of u een door Adobe beheerd SSL-certificaat (aanbevolen) of een door de klant beheerd SSL-certificaat met uw domein wilt gebruiken? Zie [ Kiezen welk SSL certificaat om toe te voegen ](#which-ssl-to-add)

**om een klant beheerde (OV/EV) SSL certificaat toe te voegen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer het aangewezen programma.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het zijmenu te openbaren.

1. Onder de **rubriek van de Diensten**, klik ![ Slot gesloten pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL Certificaten**.

   ![ Toevoegend een SSL certificaat ](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. Vlak de hoger-juiste hoek van de SSL pagina van Certificaten, klik **SSL Certificaat** toevoegen.

1. In **voeg SSL certificaat** dialoogdoos toe, die op [ uw bijzonder gebruiksgeval ](#which-ssl-to-add) wordt gebaseerd, uitgezochte **Beheerde Klant (OV/EV)**.

1. Op het **gebied van de Naam van het Certificaat**, ga een naam voor uw certificaat in.
Dit veld is alleen ter informatie en kan elke naam zijn waarmee u gemakkelijk naar het SSL-certificaat kunt verwijzen.

1. In het **Certificaat**, **Persoonlijke sleutel**, en **de ketting van het Certificaat** gebieden, kopieer de vereiste waarden van uw OV of EV SSL certificaat, en kleef hen in hun respectieve gebieden in de dialoogdoos.

   Eventuele gevonden fouten in waarden worden weergegeven. Voordat u het certificaat kunt opslaan, moet u alle fouten verhelpen. Zie [ de Fouten van het Certificaat ](#certificate-errors) om meer over het oplossen van problemen gemeenschappelijke fouten te leren.

   ![ voeg SSL certificaatdialoogdoos ](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png) toe|

1. In de laag-juiste hoek van de dialoogdoos, klik **sparen**.

   >[!NOTE]
   >
   >* Als u **Klant selecteerde beheerde certificaat** terwijl [ toevoegend een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md), wordt het domein geverifieerd ***nadat*** de klant (OV/EV) SSL certificaat wordt toegevoegd en wordt bewaard. Zie ook [ Controle de status van een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#how-to).

   Nadat het SSL certificaat met succes wordt uitgegeven, wordt het getoond met een groen geverifieerd vinkje in de **SSL Certificaten** lijst.

U hebt nu een werkend SSL-certificaat toegevoegd voor uw project. Deze stap is vaak de eerste die een aangepaste domeinnaam instelt.

U bent nu klaar om de configuratie van a [ CDN ](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md) toe te voegen.























<!--
## Add an SSL certificate {#add-ssl-cert}

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate program.
1. On the **[My Programs](/help/implementing/cloud-manager/navigation.md#my-programs)** console, select the program.
1. In the upper-left corner of the page, click ![Show menu icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) to reveal the side menu. 
1. Under the **Services** heading, click ![Lock closed icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL Certificates**. 

   ![Adding an SSL certificate](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. Near the upper-right corner of the SSL Certificates page, click **Add SSL Certificate**.

1. In the **Add SSL certificate** dialog box, based on [your particular use case](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md), do one of the following:

    | | Use case | Steps |
    | --- | --- | --- |
    | 1 | **Add an Adobe managed (DV) certificate** | **To add an Adobe managed (DV) SSL certificate:**<br>a. In the **Add SSL Certificate** dialog box, select the certificate type **Adobe managed (DV)**.<br>![Add a DV certificate](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)<br>b. In the **Certificate name** field, enter a name you want associated with the certificate.<br>c. In the **Select domains** drop-down list, select one or more domains that you want associated with the DV SSL certificate.<br>No domains to select? If so, it means that you must first add a custom domain name and ensure it is verified before you can add an SSL certificate. See [Add a custom domain name](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). When you are finished adding a custom domain name, return to this topic and begin at step 1 again.<br>d. Continue to step 7. |
    | 2 | **Add a customer managed (OV/EV) certificate** | **To add a customer managed (OV/EV) SSL certificate:**<br>a. In the **Add SSL Certificate** dialog box, select the certificate type **Customer managed (OV/EV)**.<br>b. In the **Certificate name** field, enter a name for your certificate. This field is for informational purposes only and can be any name that helps you reference your SSL certificate easily.<br>c. In the **Certificate**, **Private key**, and **Certificate chain** fields, paste the required values into their respective fields.<br>![Add SSL certificate dialog box](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)<br>Any detected errors in values are displayed. Before you can save your certificate, you must address all errors. See [Certificate Errors](#certificate-errors) to learn more about troubleshooting common errors.<br>d. Continue to step 7. | 

1. In the lower-right corner of the dialog box, click **Save**.

    >[!NOTE]
    >
    >* If you selected **Adobe managed certificate** while [adding a custom domain name](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md), the domain is verified with the added certificate when the custom domain is added. 
    >
    >* If you selected **Customer managed certificate** while [adding a custom domain name](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md), the domain is verified ***after*** the customer managed (OV/EV) SSL certificate is added and saved. See also [Check the status of a custom domain name](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#how-to).

    After the SSL certificate is successfully issued, it is displayed with a green verified check mark in the **SSL Certificates** table. 

    You now have added a working SSL certificate for your project. This step is often the first to set up a custom domain name. 
    

* To learn about updating and managing your SSL certificates in Cloud Manager, see [Manage SSL certificates](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md).

* If you are having issues adding or managing your certificates, see [Troubleshoot SSL certificate errors](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md). -->
