---
title: Een aangepast domein voor de Publish-reeks configureren
description: Leer hoe u een aangepast domein configureert voor een publicatielaag in Adobe Cloud Manager.
exl-id: cc71c8c5-cf42-4092-b0e0-646a2ed0ee54
source-git-commit: 8a10634e413ea5c66845dfffa7396a4554a5b3ca
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Een aangepast domein voor de publicatielijst configureren{#configure-custom-domain}

In Adobe Cloud Manager kunt u uw website opvallen door een aangepast domein toe te voegen. Als AEM as a Cloud Service wordt geleverd met een standaarddomein, kunt u dit naar wens aanpassen.

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
>Voeg het aangepaste domein toe aan de lijst met toegestane omleidings-URL&#39;s. De lijst bevindt zich in de IMS-client voor de elementenkiezer.<br> coördinaat met het respectieve team van de Adobe om deze taak uit te voeren door het koord van het douanedomein te verstrekken.
