---
title: Een aangepast domein voor de publicatiereeks configureren
description: Leer hoe u een aangepast domein configureert voor een publicatielaag in Adobe Cloud Manager.
exl-id: cc71c8c5-cf42-4092-b0e0-646a2ed0ee54
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# Een aangepast domein voor de publicatielijst configureren{#configure-custom-domain}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b> integratie van AEM Assets met Edge Delivery Services </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuw </i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b> laat Dynamische Media Prime en Ultimate </b></a> toe
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b> Beste praktijken van Meta-gegevens </b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b> Content Hub </b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b> Dynamische Media met mogelijkheden OpenAPI </b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b> de ontwikkelaarsdocumentatie van AEM Assets </b></a>
        </td>
    </tr>
</table>

>[!AVAILABILITY]
>
>De handleiding Dynamic Media met OpenAPI-mogelijkheden is nu beschikbaar in PDF-indeling. Download de volledige handleiding en gebruik Adobe Acrobat AI Assistant om je vragen te beantwoorden.
>
>[!BADGE &#x200B; Dynamische Media met OpenAPI mogelijkhedenGids PDF &#x200B;]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

In Adobe Cloud Manager kunt u uw website laten opvallen door een aangepast domein toe te voegen. Als AEM as a Cloud Service wordt geleverd met een standaarddomein, kunt u dit naar wens aanpassen.

## Voordat u begint

* U moet beschikken over een multi-SAN (Subject Alternative Name) TLS- of SSL-certificaat.
* Het SSL-certificaat moet verschillende SAN&#39;s hebben ten opzichte van het certificaat dat is toegewezen voor de publicatielaag in hetzelfde domein.
* Het certificaatbeleid moet of Uitgebreide Bevestiging (EV) of de Bevestiging van de Organisatie (OV), en niet het beleid van de Bevestiging van het Domein naleven (DV).


## Een aangepast domein voor de publicatielijst configureren

1. Ga naar **[!UICONTROL Adobe Cloud Manager]** > **[!UICONTROL Program Overview]** > **[!UICONTROL SSL Certificates]** en voeg uw SSL-certificaat toe.
   ![ beeld ](/help/assets/assets/ssl-certificate.png)
Leer hoe te om [ SSL certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) in Adobe Cloud Manager toe te voegen.

1. Voeg een aangepast domein toe nadat u het SSL-certificaat hebt toegevoegd. Klik op **[!UICONTROL Domain Settings]** en geef het aangepaste domein op met de optie **[!UICONTROL Publish service]** .
Leer meer over [ douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

1. Voeg twee [ verslagen van de NAAM ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) in uw DNS verslag toe die aan publiceer domeinen beantwoorden.
DNS de controle kan een paar uren aan proces wegens DNS propagatievertragingen vergen.

1. Logboek een steungeval om de configuratie van het douanedomein te vergemakkelijken, ervoor zorgen dat het aan de leveringsrij richt.

>[!NOTE]
>
>Voeg het aangepaste domein toe aan de lijst met toegestane omleidings-URL&#39;s. De lijst bevindt zich in de IMS-client voor de elementenkiezer.<br> coördinaat met het respectieve team van Adobe om deze taak uit te voeren door het koord van het douanedomein te verstrekken.
