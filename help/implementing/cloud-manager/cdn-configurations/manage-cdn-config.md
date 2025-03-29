---
title: Domeintoewijzingen beheren
description: Leer hoe u met Cloud Manager CDN-configuraties voor een Edge Delivery-site of een Cloud Manager-omgeving kunt bewerken en bijwerken of verwijderen.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 2ec16c91-0195-4732-a26d-ac223e10afb9
source-git-commit: 41155a724f48ad28a12aac615a3e9a13bb3afa26
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---

# Domeintoewijzingen beheren {#manage-cdn-configurations}

Leer hoe u met Cloud Manager CDN-configuraties voor een Edge Delivery-site of een Cloud Manager-omgeving kunt bewerken of verwijderen.

## Een CDN-configuratie bewerken via de pagina Domeintoewijzingen {#edit-cdn}

In Adobe Cloud Manager kunt u om verschillende redenen een CDN-configuratie (Content Delivery Network) bewerken, inclusief de milieulaag (Publiceren of Voorvertoning) en het SSL-certificaat.

* **de veranderingen van het Milieu**: Het aanpassen van de rijhulp past de montages CDN met het correcte milieu aan, hetzij voor levende productie (publiceren) of het testen (Voorproef).
* **de verhogingen van de Veiligheid**: Het selecteren van een verschillend SSL certificaat kan noodzakelijk zijn wanneer het bijwerken van certificaten of het richten van naleving en veiligheidsbehoeften.
* **Optimaliserend prestaties**: Het uitgeven van de configuratie verzekert de correcte montages CDN voor het leveren van inhoud die op veranderende operationele behoeften wordt gebaseerd.

U kunt een configuratie bewerken zonder de bestaande configuratie volledig te verwijderen. Wijzigingen worden toegepast op de geselecteerde omgeving, bijvoorbeeld in de testfase of de productieomgeving, en kunnen van invloed zijn op de manier waarop inhoud wordt geleverd en beveiligd.

Een gebruiker moet een lid van de **BedrijfsEigenaar** of **rol zijn van de Manager van de Plaatsing** om deze taak te voltooien.

**om een configuratie CDN van de Pagina van Toewijzingen van het Domein uit te geven:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.
1. In het linkerzijmenu, onder **Diensten**, klik ![ het netwerkpictogram van de Sociale Zaken ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Toewijzingen van het Domein**.
1. In de **lijst van Toewijzingen van het Domein**, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) aan het eind van een rij waarvan configuratie CDN u wilt bijwerken.

1. Van het drop-down menu, geeft de klik **** uit.

1. In **geef CDN configuratie** dialoogdoos uit, plaats één of meerdere opties in de respectieve drop-down lijst.

   De opties in de dialoogdoos worden getoond hangen af van of u **Adobe beheerde CDN** of een **Andere CDN leverancier** (klant beheerde CDN) gebruikt.

1. Klik **Update**.

   Het statuut van uitgegeven CDN wordt bijgewerkt in de **Lijst van Toewijzingen van het Domein** om op de veranderingen te wijzen u aanbracht.


## Een CDN-configuratie bewerken via de pagina Omgevingen

De stappen voor het uitgeven van een configuratie CDN van de **pagina van Milieu&#39;s** zijn bijna het zelfde als wanneer [ het uitgeven van een configuratie CDN van de pagina van Toewijzingen van het Domein ](#edit-cdn), maar het ingangspunt verschilt.

**om een configuratie CDN van de pagina van Milieu&#39;s uit te geven:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. In het linkerzijmenu, klik ![ het pictogram van Gegevens ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Milieu&#39;s**.

1. Voor de **pagina van Milieu&#39;s**, selecteer een milieu van belang.

1. Voor de pagina van milieudetails, in de Mappingen van het Domein groeperen, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) dat aan de configuratie beantwoordt CDN u wilt uitgeven.

1. In pop-up menu, geeft de klik **** uit.

1. In **geef CDN de dialoogdoos van de Configuratie** uit, plaats één of meerdere opties in de respectieve drop-down lijst.

   De opties in de dialoogdoos worden getoond hangen af van of u **Adobe beheerde CDN** of een **Andere CDN leverancier** (klant beheerde CDN) gebruikt.

1. Klik **Update**.

<!-- 
## Go live readiness: Configure DNS settings for a custom domain {#go-live-readiness} 

Before a custom domain can serve traffic in Adobe Cloud Manager, you must complete DNS configuration with your DNS provider. After deploying a domain mapping and clicking **Go live**, Cloud Manager displays a dialog box that guides you through the DNS record setup process. You have the option to go live by adding either a CNAME record type or an A record type representing Fastly's IPs, simplifying domain routing. This ability eliminates the restriction of relying solely on CNAME records for domain setup with Fastly.

MAYBE There is support for A record types to improve Go Live readiness for domains using CDN configurations in AEM Cloud Manager. MAYBE

See also [APEX record](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#adobe-managed-cert-cname-record#adobe-managed-cert-apex-record) and [CNAME record](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#adobe-managed-cert-cname-record).

**To configure Go live readiness:**

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. In the left side menu, under **Services**, click ![Social network icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Domain Mappings**.

1. In the Domain Mappings table, click **Go live** near the end of a row that corresponds to a CDN whose Go Live readiness you want to configure. 

1. In the Go live readiness dialog box, do one of the following:

    | Configure  | Steps |
    | --- | --- |
    | A RECORD | Recommended for root domains like `example.com`<br><ol><li>Log in to your DNS service provider's portal.<li>Go to the DNS Records section.<li>Create an A record to point to all the listed IP addresses.<li>In the Go live readiness dialog box, click **OK**.<li>In the Domain Mappings table, under the **Status** column, click ![Refresh icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Refresh_18_N.svg).<br>The status is updated to **Verified** when the resolution is complete.</li></ol> |
    | CNAME | Recommended for custom domains like `www.example.com`<br><ol><li>Log in to your DMS service provider's portal.<li>Go to the DNS Records section.<li>Map [cdn.adobeaemcloud.com](http://cdn.adobeaemcloud.com/) (CNAME record) in the DNS record of the DNS service provider (your custom domain). This mapping ensures that requests received at the custom domain are redirected to Adobe's CDN.<li>In the **Go live readiness** dialog box, click **OK** to save the record.<br>Wait for DNS propogation (may take several minutes to a few hours). When the **[!UICONTROL Status]** column in the Domamin Mappings table updates to **[!UICONTROL Verified]**, the custom domain is ready to use. You may need to click ![Refresh icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Refresh_18_N.svg) to refresh the status.</li></ol> | 
    
-->

## Een CDN-configuratie verwijderen {#delete-cdn}

Wanneer u een door Adobe beheerde of klant beheerde CDN-configuratie in Cloud Manager verwijdert, worden de bijbehorende routering- en SSL-certificaatinstellingen van het domein verwijderd. Het domein gebruikt niet meer CDN voor verkeerslevering, en om het even welke veiligheid of prestatiesverhogingen die door CDN worden verstrekt wordt verloren. U kunt de dienstverstoring ervaren tot een nieuwe configuratie opstelling is, of het re-toevoegen van geschrapte CDN of het toevoegen van nieuwe.

Een gebruiker moet een lid van de **BedrijfsEigenaar** of **rol zijn van de Manager van de Plaatsing** om deze taak te voltooien.

**om een configuratie te schrappen CDN:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. In het linkerzijmenu, onder **Diensten**, klik ![ het netwerkpictogram van de Sociale Zaken ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Toewijzingen van het Domein**.

1. In de lijst van Toewijzingen van het Domein, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) aan het eind van een rij die aan CDN beantwoordt u wilt verwijderen, dan **Schrapping** klikken.

1. In het **de dialoogvakje van de Configuratie CDN van de Schrapping**, klik **Schrapping**.

1. Klik **Schrapping** opnieuw om de verwijdering van CDN van de plaats te bevestigen.


## Een CDN-configuratie verwijderen van de pagina Environment

De stappen voor het schrappen van een configuratie CDN van de **pagina van Milieu&#39;s** zijn bijna het zelfde als wanneer [ het schrappen van een configuratie CDN van de pagina van Toewijzingen van het Domein ](#edit-cdn), maar het ingangspunt verschilt.

**om een configuratie CDN van de pagina van Milieu&#39;s te schrappen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. In het linkerzijmenu, klik ![ het pictogram van Gegevens ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Milieu&#39;s**.

1. Voor de **pagina van Milieu&#39;s**, selecteer een milieu van belang.

1. Op de pagina van milieudetails, in de **Toewijzingen van het Domein** groeperen, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) dat aan de configuratie CDN beantwoordt u wilt verwijderen, dan **Schrapping** klikken.

1. In het **de dialoogvakje van de Configuratie CDN van de Schrapping**, klik **Schrapping**.

1. Klik **Schrapping** opnieuw om de verwijdering van CDN van de plaats te bevestigen.
