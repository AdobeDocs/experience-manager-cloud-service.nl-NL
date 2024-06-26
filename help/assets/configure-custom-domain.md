---
title: Aangepast domein voor publicatielaag configureren
description: Leer hoe u een aangepast domein configureert voor een publicatielaag in Adobe Cloud Manager.
source-git-commit: f6c0e8e5c1d7391011ccad5aa2bad4a6ab7d10c3
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Aangepast domein voor publicatielaag configureren{#configure-custom-domain}

In Adobe Cloud Manager kunt u uw website opvallen door een aangepast domein toe te voegen. Als AEM as a Cloud Service wordt geleverd met een standaarddomein, kunt u dit naar wens aanpassen.

## Voordat u begint

* U moet beschikken over een multi-SAN (Subject Alternative Name) TLS- of SSL-certificaat.
* Het SSL-certificaat moet verschillende SAN&#39;s hebben ten opzichte van het certificaat dat is toegewezen voor de publicatielaag in hetzelfde domein.
* Het certificaatbeleid moet of Uitgebreide Bevestiging (EV) of de Bevestiging van de Organisatie (OV), en niet het beleid van de Bevestiging van het Domein naleven (DV).


## Aangepast domein toevoegen

Voer de volgende stappen uit om een aangepast domein voor de publicatielijst te configureren:

1. Ga naar **[!UICONTROL Adobe Cloud Manager]** > **[!UICONTROL Program Overview]** > **[!UICONTROL SSL Certificates]**en voeg uw SSL-certificaat toe.
   ![image](/help/assets/assets/ssl-certificate.png)
Meer informatie over toevoegen [SSL-certificaat](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) in Adobe Cloud Manager.

1. Voeg een aangepast domein toe nadat u het SSL-certificaat hebt toegevoegd. Klikken **[!UICONTROL Domain Settings]** en geeft u het aangepaste domein op tegen de **[!UICONTROL Publish service]** -optie.
Meer informatie over [aangepast domein](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

1. 2 toevoegen [CNAME-records](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) in uw DNS-record die correspondeert met het publiceren van domeinen.
DNS de controle kan een paar uren aan proces wegens DNS propagatievertragingen vergen.

1. Logboek een steungeval om de configuratie van het douanedomein te vergemakkelijken, ervoor zorgen dat het aan de leveringsrij richt.

>[!NOTE]
>
> Voeg het aangepaste domein toe aan de lijst met toegestane omleidings-URL&#39;s in de IMS-client voor de elementenkiezer.<br>Coördineer met het respectieve team van de Adobe om deze taak uit te voeren door het koord van het douanedomein te verstrekken.
