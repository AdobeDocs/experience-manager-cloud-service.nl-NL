---
title: Status domeinnaam controleren
description: Leer hoe u kunt controleren of Cloud Manager uw aangepaste domeinnaam heeft bevestigd.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 3ff7b76f7892269f6ca001ff2c079bc693c06d93
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---


# Status van domeinnaam controleren {#check-status}

Leer hoe u kunt controleren of Cloud Manager uw aangepaste domeinnaam heeft bevestigd.

## Vereisten {#requirements}

Voldoe aan deze vereisten voordat u de status van uw domeinnaam in Cloud Manager controleert.

* Voeg eerst een TXT- verslag voor uw douanedomein toe zoals die in het document [ wordt beschreven een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegt.

## De status van uw aangepaste domeinnaam controleren {#how-to}

U kunt de status van uw aangepaste domeinnaam in Cloud Manager bepalen.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Navigeer aan het **scherm van Milieu&#39;s** van de **pagina van het Overzicht**.

1. Klik **Montages van het Domein** in het linkernavigatievenster.

1. Klik het **pictogram van de Status** voor de domeinnaam.

Het statusdetail wordt weergegeven. Uw douanedomein is klaar om te worden gebruikt wanneer het status **Geverifieerde en Geïmporteerde Domein** wordt getoond. Zie de [ volgende sectie ](#statuses) voor details op de verschillende statussen en wat zij betekenen.

>[!NOTE]
>
>Cloud Manager brengt automatisch verificatie teweeg wanneer u **** op de verificatiestap van **selecteert creeert de Add tovenaar van het Domein van de Douane** wanneer [ toevoegend een nieuwe naam van het douanedomein aan Cloud Manager ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). Voor verdere controles, moet u actief selecteren opnieuw verifieert pictogram naast de status.

## Verificatiestatus {#statuses}

Cloud Manager verifieert domeineigendom door de [ TXT waarde ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) en toont één van de volgende statusberichten.

| Status | Beschrijving |
| --- | --- |
| Domeinverificatie mislukt | De TXT-waarde ontbreekt of wordt met fouten gedetecteerd.<br> Volg de instructies in het statusbericht om het probleem op te lossen. Wanneer klaar, moet u **opnieuw verifiëren** pictogram naast de status selecteren. |
| Domeinverificatie wordt uitgevoerd | De verificatie wordt uitgevoerd.<br> Deze status wordt typisch gezien nadat u **selecteert verifieer opnieuw** pictogram naast de status. DNS de controle kan een paar uren aan proces wegens DNS propagatievertragingen vergen. |
| Geverifieerd - implementatie mislukt | De TXT-verificatie is gelukt, maar de CDN-implementatie is mislukt.<br> In dergelijke gevallen, contacteer uw Adobe vertegenwoordiger. |
| Geverifieerd en geïmplementeerd domein | Deze status geeft aan dat uw aangepaste domeinnaam klaar is om te worden gebruikt.<br> Op dit punt, is uw naam van het douanedomein klaar voor het testen en om aan de het domeinnaam van Cloud Manager worden gericht. Zie [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen om meer te leren. |
| Verwijderen | De verwijdering van een aangepaste domeinnaam wordt uitgevoerd. |
| Verwijderen is mislukt | Het verwijderen van een aangepaste domeinnaam is mislukt en moet opnieuw worden geprobeerd.<br> zie [ de namen van het douanedomein beheren ](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) om meer te leren. |


## Fouten in domeinnaam {#domain-error}

Hier volgen enkele algemene fouten bij de verificatie van domeinnamen en de bijbehorende resoluties.

### Fout domein niet geïnstalleerd {#domain-not-installed}

Deze fout kan tijdens domeinbevestiging van het TXT- verslag voorkomen zelfs nadat u hebt gecontroleerd dat het verslag geschikt is bijgewerkt.

#### Foutoorzaak {#cause}

Met Fastly wordt een domein vergrendeld op de account die het eerst registreert en met andere accounts moet toestemming worden gevraagd om een subdomein te registreren. Bovendien kunt u met Snelheid alleen een apex-domein en bijbehorende subdomeinen toewijzen aan één Fastly-service en -account. Deze fout wordt weergegeven als u een bestaande Fastly-account hebt waarmee dezelfde map en subdomeinen worden gekoppeld die worden gebruikt voor uw AEM Cloud Service-domeinen.

#### Foutresolutie {#resolution}

De fout is als volgt gecorrigeerd:

* Verwijder de apex- en subdomeinen van de bestaande account voordat u het domein in Cloud Manager installeert.

* Gebruik deze optie om het apex-domein en alle subdomeinen te koppelen aan de AEM as a Cloud Service Fastly-account. Zie [ Werkend met Domeinen in de Fastly documentatie ](https://docs.fastly.com/en/guides/working-with-domains) voor extra details.

* Als uw apex-domein meerdere subdomeinen heeft voor AEM as a Cloud Service en niet-AEM sites die een koppeling moeten maken naar verschillende snelaccounts, probeert u het domein te installeren in Cloud Manager. Met dit proces kunt u subdomeinverbindingen beheren voor verschillende snelaccounts. Als de domeininstallatie mislukt, maakt u snel een klantenondersteuningsticket, zodat de Adobe in uw naam snel een vervolg kan geven.

>[!TIP]
>
>Het oplossen van kwesties van de domeindelegatie met Fastly neemt typisch 1 tot 2 werkdagen. Daarom wordt het ten zeerste aanbevolen de domeinen ruim vóór hun live datum te installeren.

>[!NOTE]
>
>Geef de DNS van uw site niet door aan AEM as a Cloud Service IP&#39;s als het domein niet correct is geïnstalleerd.

## Bestaande CDN-configuraties voor aangepaste domeinnamen {#pre-existing-cdn}

Als u reeds een configuratie CDN voor uw namen van het douanedomein hebt, verschijnt een informatief bericht op de **Namen van het Domein van de Douane** en **Milieu** pagina&#39;s. Het moedigt u aan om deze configuraties via UI toe te voegen zodat zij binnen Cloud Manager kunnen worden beheerd en worden bekeken.

Het bericht verdwijnt nadat alle bestaande omgevingsconfiguraties zijn gemigreerd met de interface. Het kan 1-2 werkdagen duren voordat het bericht verdwijnt.

Zie [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) voor meer details toevoegen.

## Volgende stappen {#next-steps}

Nadat u uw domeinstatus in Cloud Manager hebt geverifieerd, configureert u DNS-instellingen door DNS-, CNAME- of APEX-records toe te voegen die naar AEM as a Cloud Service wijzen. Ga aan het document [ te werk voeg een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toe om vestiging uw naam van het douanedomein voort te zetten.
