---
title: Status domeinnaam controleren
description: Leer hoe u kunt bepalen of uw aangepaste domeinnaam is geverifieerd door Cloud Manager.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 0%

---


# Status domeinnaam controleren {#check-status}

Leer hoe u kunt bepalen of uw aangepaste domeinnaam is geverifieerd door Cloud Manager.

## Vereisten {#requirements}

U moet aan deze vereisten voldoen voordat u de status van uw domeinnaam in Cloud Manager kunt controleren.

* U moet eerst een verslag TXT voor uw douanedomein toevoegen zoals die in het document [ wordt beschreven Toevoegend een Verslag TXT ](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md).

## De status van uw aangepaste domeinnaam controleren {#how-to}

U kunt de status van uw aangepaste domeinnaam bepalen in Cloud Manager.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Navigeer aan het **scherm van Milieu&#39;s** van de **pagina van het Overzicht**.

1. Klik **Montages van het Domein** in het linkernavigatievenster.

1. Klik het **pictogram van de Status** voor de domeinnaam.

Het statusdetail wordt weergegeven. Uw douanedomein is klaar om te worden gebruikt wanneer het status **Geverifieerde en Geïmporteerde Domein** wordt getoond. Zie de [ volgende sectie ](#statuses) voor details op de verschillende statussen en wat zij betekenen.

>[!NOTE]
>
>Cloud Manager zal automatisch verificatie teweegbrengen wanneer u **** op de verificatiestap van **selecteert creeer de tovenaar van het Domein van de Douane** wanneer [ toevoegend een nieuwe naam van het douanedomein aan Cloud Manager ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). Voor verdere controles, moet u actief selecteren opnieuw verifieert pictogram naast de status.

## Verificatiestatus begrijpen {#statuses}

Cloud Manager zal domeineigendom via de [ TXT waarde ](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) verifiëren en één van de volgende statusberichten toont.

* **Ontbroken Controle van het Domein** - de waarde TXT of mist of met fouten ontdekt.

   * Volg de instructies in het statusbericht om het probleem op te lossen.
   * Wanneer klaar, moet u **opnieuw verifiëren** pictogram naast de status selecteren.

* **Bezig de Verificatie van het Domein 1} - de Verificatie is lopend.**

   * Deze status wordt typisch gezien nadat u **selecteert verifieer opnieuw** pictogram naast de status.
   * DNS de controle kan een paar uren aan proces wegens DNS propagatievertragingen vergen.

* **Verified, Mislukte Plaatsing** - de controle TXT was succesvol, maar de plaatsing CDN ontbrak.

   * Neem in dergelijke gevallen contact op met uw Adobe.

* **Geverifieerd en Geïmporteerd Domein 1} - Deze status wijst erop dat uw naam van het douanedomein klaar is om te worden gebruikt.**

   * Op dit punt is uw aangepaste domeinnaam klaar om te worden getest en moet deze naar de Cloud Manager-domeinnaam worden verwezen.
   * Zie [ Vormend DNS Montages ](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) om meer te leren.

* **Deleting** - de schrapping van een naam van het douanedomein is lopend.

* **Ontbroken Schrapping** - de schrapping van ontbroken naam van het douanedomein en moet opnieuw worden geprobeerd.

   * Zie [ het Leiden Namen van het Domein van de Douane ](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) om meer te leren.

## Fouten in domeinnaam {#domain-error}

Hier volgen enkele algemene fouten bij de verificatie van domeinnamen en de bijbehorende resoluties.

### Fout domein niet geïnstalleerd {#domain-not-installed}

Deze fout kan tijdens domeinbevestiging van het TXT- verslag voorkomen zelfs nadat u hebt gecontroleerd dat het verslag geschikt is bijgewerkt.

#### Fout bij maken {#cause}

Hiermee vergrendelt u snel een domein op de initiële account die het heeft geregistreerd en kan geen enkele andere account een subdomein registreren zonder toestemming te vragen. Bovendien kunt u met Snelheid alleen een apex-domein en bijbehorende subdomeinen toewijzen aan één Fastly-service en -account. Deze fout wordt weergegeven als u een bestaande Fastly-account hebt waarmee dezelfde map en subdomeinen worden gekoppeld die worden gebruikt voor uw AEM Cloud Service-domeinen.

#### Foutresolutie {#resolution}

De fout is als volgt gecorrigeerd:

* Verwijder de apex- en subdomeinen van de bestaande account voordat u het domein in Cloud Manager installeert.

* Gebruik deze optie om het apex-domein en alle subdomeinen te koppelen aan de AEM as a Cloud Service Fastly-account. Zie [ Werkend met Domeinen in de Fastly documentatie ](https://docs.fastly.com/en/guides/working-with-domains) voor extra details.

* Als uw apex-domein meerdere subdomeinen voor AEM as a Cloud Service- en niet-AEM as a Cloud Service-sites heeft die u wilt koppelen aan verschillende snelaccounts, installeert u het domein dan in Cloud Manager. Als de domeininstallatie mislukt, maakt u snel een Customer Support-ticket, zodat de Adobe in uw naam snel een vervolg kan geven aan de installatie.

>[!TIP]
>
>Het oplossen van kwesties van de domeindelegatie met Fastly neemt typisch 1 tot 2 werkdagen. Daarom wordt het ten zeerste aanbevolen de domeinen ruim vóór hun live datum te installeren.

>[!NOTE]
>
>Geef de DNS van uw site niet door aan AEM as a Cloud Service IP&#39;s als het domein niet correct is geïnstalleerd.

## Bestaande CDN-configuraties voor aangepaste domeinnamen {#pre-existing-cdn}

Als u een reeds bestaande configuratie CDN voor uw namen van het douanedomein hebt, is er een informatief bericht op de **Namen van het Domein van de Douane** en **Milieu** pagina&#39;s, die u aanmoedigen om deze configuraties via UI toe te voegen zodat zijn zij zichtbaar en configureerbaar in Cloud Manager.

Het bericht verdwijnt zodra alle bestaande omgevingsconfiguraties zijn gemigreerd met de interface. Het kan 1-2 werkdagen duren voordat het bericht verdwijnt.

Zie [ Toevoegend een Naam van het Domein van de Douane ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) voor meer details.

## Volgende stappen {#next-steps}

Zodra u uw domeinstatus in Cloud Manager hebt geverifieerd, zult u DNS montages moeten vormen door DNS CNAME of verslagen toe te voegen APEX die aan AEM as a Cloud Service richten. Ga aan het document [ Vormende DNS Montages ](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) te werk om vestiging uw naam van het douanedomein te blijven.
