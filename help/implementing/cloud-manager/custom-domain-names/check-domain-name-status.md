---
title: Status domeinnaam controleren
description: Leer hoe u kunt bepalen of uw aangepaste domeinnaam is geverifieerd door Cloud Manager.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---


# Status domeinnaam controleren {#check-status}

U kunt de status van uw aangepaste domeinnaam bepalen in Cloud Manager.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Op de **[Mijn programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)** -console, selecteert u het programma.

1. Ga naar de **Omgevingen** van het scherm **Overzicht** pagina.

1. Klikken **Domeininstellingen** in het linkernavigatievenster.

1. Klik op de knop **Status** pictogram voor de domeinnaam.

Cloud Manager controleert het eigendom van het domein via de TXT-waarde en geeft een van de volgende statusberichten weer.

* **Domeinverificatie mislukt** - De TXT-waarde ontbreekt of wordt met fouten gedetecteerd.

   * Volg de instructies die worden gegeven om het probleem op te lossen.
   * Wanneer u klaar bent, moet u de optie **Opnieuw controleren** naast de status.

* **Domeinverificatie wordt uitgevoerd** - De verificatie wordt uitgevoerd.

   * Deze status wordt meestal weergegeven nadat u de optie **Opnieuw controleren** naast de status.

* **Geverifieerd, implementatie mislukt** - De TXT-verificatie is gelukt, maar de CDN-implementatie is mislukt.

   * Neem in dergelijke gevallen contact op met uw Adobe.

* **Domein geverifieerd en geïmplementeerd** - Deze status geeft aan dat uw aangepaste domeinnaam klaar is om te worden gebruikt.

   * Op dit moment is uw aangepaste domeinnaam klaar om te worden getest en moet deze naar de domeinnaam van Cloud Manager worden verwezen.
   * Zie [DNS-instellingen configureren](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) voor meer informatie.

* **Verwijderen** - De verwijdering van een aangepaste domeinnaam wordt uitgevoerd.

* **Verwijderen mislukt** - Het verwijderen van een aangepaste domeinnaam is mislukt en moet opnieuw worden geprobeerd.

   * Zie [Aangepaste domeinnamen beheren](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) voor meer informatie.

Cloud Manager activeert automatisch een TXT-verificatie wanneer u **Opslaan** over de verificatiestap van de **Aangepast domein toevoegen** wizard. Voor verdere controles, moet u actief selecteren opnieuw verifieert pictogram naast de status.

## Fouten in domeinnaam {#domain-error}

Hieronder vindt u een aantal fouten met algemene domeinnamen en de bijbehorende resoluties.

### Fout domein niet geïnstalleerd {#domain-not-installed}

Deze fout kan tijdens domeinbevestiging van het TXT- verslag voorkomen zelfs nadat u hebt gecontroleerd dat het verslag geschikt is bijgewerkt.

#### Fout bij maken {#cause}

Hiermee vergrendelt u snel een domein op de initiële account die het heeft geregistreerd en kan geen enkele andere account een subdomein registreren zonder toestemming te vragen. Bovendien kunt u met Snelheid alleen een apex-domein en bijbehorende subdomeinen toewijzen aan één Fastly-service en -account. Deze fout wordt weergegeven als u een bestaande Fastly-account hebt waarmee dezelfde map en subdomeinen worden gekoppeld die worden gebruikt voor uw AEM Cloud Service-domeinen.

#### Foutresolutie {#resolution}

De fout is als volgt gecorrigeerd:

* Verwijder de apex- en subdomeinen van de bestaande account voordat u het domein installeert in Cloud Manager.

* Gebruik deze optie om het apex-domein en alle subdomeinen te koppelen aan de AEM as a Cloud Service snelaccount. Zie [Werken met domeinen in de sneldocumentatie](https://docs.fastly.com/en/guides/working-with-domains) voor meer informatie.

* Als uw apex-domein meerdere subdomeinen heeft voor AEM as a Cloud Service en niet-AEM as a Cloud Service sites die u wilt koppelen aan verschillende snelaccounts, installeert u het domein dan in Cloud Manager. Als de domeininstallatie mislukt, maakt u snel een Customer Support-ticket, zodat de Adobe in uw naam snel een vervolg kan geven aan de installatie.

>[!TIP]
>
>Het oplossen van kwesties van de domeindelegatie met Fastly neemt typisch 1 tot 2 werkdagen. Daarom wordt het ten zeerste aanbevolen de domeinen ruim vóór hun live datum te installeren.

>[!NOTE]
>
>Lijn DNS van uw plaats niet aan AEM as a Cloud Service IPs als het domein niet met succes werd geïnstalleerd.

## Bestaande CDN-configuraties voor aangepaste domeinnamen {#pre-existing-cdn}

Als u een reeds bestaande configuratie CDN voor uw namen van het douanedomein hebt, is er een informatief bericht op **Aangepaste domeinnamen** en **Omgeving** pagina&#39;s, die u aanmoedigen om deze configuraties toe te voegen via de gebruikersinterface zodat ze zichtbaar en configureerbaar zijn in Cloud Manager.

Het bericht verdwijnt zodra alle bestaande omgevingsconfiguraties zijn gemigreerd met de interface. Het kan 1-2 werkdagen duren voordat het bericht verdwijnt.

Zie [Een aangepaste domeinnaam toevoegen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) voor meer informatie .
