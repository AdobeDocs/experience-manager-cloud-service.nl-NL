---
title: Aangepast domein voor publicatielaag configureren
description: Leer hoe u een aangepast domein configureert voor een publicatielaag in Adobe Cloud Manager.
role: null
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---


# Aangepast domein voor publicatielaag configureren{#configure-custom-domain}

In Adobe Cloud Manager kunt u uw website opvallen door een aangepast domein toe te voegen. AEM as a Cloud Service wordt geleverd met een standaarddomein, maar u kunt het aanpassen aan uw wensen.
<!-- For example, AEM sites can use `sites.custom_domain.com`, and the AEM publish domain can be accessed via `assets.custom_domain.com`. Additionally, getting an SSL certificate for assets.pmi.com with a SAN entry for `delivery.custom_domain.com` improves security and trustworthiness. -->

## Voordat u begint

* U moet beschikken over een multi-SAN (Subject Alternative Name) TLS- of SSL-certificaat.
* Het SSL-certificaat moet verschillende SAN&#39;s hebben ten opzichte van het certificaat dat is toegewezen voor de publicatielaag in hetzelfde domein.
* Het certificaatbeleid moet of Uitgebreide Bevestiging (EV) of de Bevestiging van de Organisatie (OV), en niet het beleid van de Bevestiging van het Domein naleven (DV).


## Aangepast domein toevoegen

Voer de volgende stappen uit om een aangepast domein voor de publicatielijst te configureren:

1. Ga naar **[!UICONTROL Adobe Cloud Manager]** > **[!UICONTROL Program Overview]** > **[!UICONTROL SSL Certificates]**en voeg uw SSL-certificaat toe.
   ![image](/help/assets/assets/ssl-certificate.png)
Meer informatie over toevoegen [SSL-certificaat](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/add-ssl-certificate.html?lang=en) in Adobe Cloud Manager.

1. Voeg een aangepast domein toe nadat u het SSL-certificaat hebt toegevoegd. Klikken **[!UICONTROL Domain Settings]** en geeft u het aangepaste domein op tegen de **[!UICONTROL Publish service]** -optie.
   <br> Meer informatie over [aangepast domein](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name.html?lang=en).

1. Voeg 2 CNAME- verslagen in uw DNS verslag toe die aan publicatiedomeinen beantwoorden.
   <br> DNS de controle kan een paar uren aan proces wegens DNS propagatievertragingen vergen.

1. Logboek een steungeval om de configuratie van het douanedomein te vergemakkelijken, ervoor zorgen dat het aan de leveringsrij richt.

>[!NOTE]
>
> Voeg het aangepaste domein toe aan de lijst met toegestane omleidings-URL&#39;s in de IMS-client voor de elementenkiezer.<br>Coördineer met het respectieve team van de Adobe om deze taak uit te voeren door het koord van het douanedomein te verstrekken.
