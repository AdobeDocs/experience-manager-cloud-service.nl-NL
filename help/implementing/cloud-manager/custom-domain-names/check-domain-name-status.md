---
title: Status van domeinnaam controleren
description: Leer hoe u kunt controleren of Cloud Manager uw aangepaste domeinnaam heeft bevestigd.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 3ecb3f0f49160536ba9abd1261477b0985a03c07
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---


# Status van domeinnaam controleren {#check-status}

Leer hoe u kunt controleren of Cloud Manager uw aangepaste domeinnaam heeft bevestigd.

## De status van een aangepaste domeinnaam controleren {#how-to}

Alvorens uw status van de domeinnaam in Cloud Manager te controleren, zorg ervoor u reeds een klant geleid (OV/EV) SSL certificaat voor uw douanedomein zoals die in [ wordt beschreven toevoegt een klant beheerd SSL certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md##add-customer-managed-ssl-cert).

**om het statuut van een naam van het douanedomein te controleren:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Navigeer aan het **scherm van Milieu&#39;s** van de **pagina van het Overzicht**.

1. Klik **Montages van het Domein** in het linkerzijmenu.

1. Klik het **pictogram van de Status** voor de domeinnaam.

Het statusdetail wordt weergegeven. Uw douanedomein is klaar om te worden gebruikt wanneer het status **Geverifieerde en Geïmporteerde Domein** wordt getoond. Zie de [ volgende sectie ](#statuses) voor details op de verschillende statussen en wat zij betekenen.

>[!NOTE]
>
>Als u een *Adobe beheerde (DV) SSL certificaat* met het domein gebruikt, brengt Cloud Manager automatisch verificatie teweeg wanneer u **** in de Verify doos van de domeindialoog klikt wanneer [ toevoegend een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).
>
>Als u op het gebruiken van a **beheerde klant (OV/EV) SSL certificaat** van plan bent, wordt uw domein geverifieerd *nadat* u [ het OV/EV SSL certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) toevoegt.


## Verificatiestatus {#statuses}

Cloud Manager verifieert domeineigendom via het SSL-certificaat (OV/EV) dat door de klant wordt beheerd. Wanneer gereed, toont het één van de volgende statusberichten:

| Status | Beschrijving |
| --- | --- |
| Domeinverificatie mislukt | Het door de klant beheerde EV/OV-certificaat ontbreekt of wordt met fouten gedetecteerd.<br> Volg de instructies in het statusbericht om het probleem op te lossen. Wanneer klaar, moet u **opnieuw verifiëren** pictogram naast de status selecteren. |
| Domeinverificatie wordt uitgevoerd | De verificatie wordt uitgevoerd.<br> Deze status wordt typisch gezien nadat u **selecteert verifieer opnieuw** pictogram naast de status. DNS de controle kan een paar uren aan proces wegens DNS propagatievertragingen vergen. |
| Geverifieerd - implementatie mislukt | De verificatie van het EV/OV-certificaat is gelukt, maar de CDN-implementatie is mislukt.<br> In dergelijke gevallen, contacteer uw vertegenwoordiger van Adobe. |
| Geverifieerd en geïmplementeerd domein | Deze status geeft aan dat uw aangepaste domeinnaam klaar is om te worden gebruikt.<br> Op dit punt, is uw naam van het douanedomein klaar voor het testen en om aan de het domeinnaam van Cloud Manager worden gericht. Zie [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen om meer te leren. |
| Verwijderen | De verwijdering van een aangepaste domeinnaam wordt uitgevoerd. |
| Verwijderen is mislukt | Het verwijderen van een aangepaste domeinnaam is mislukt en moet opnieuw worden geprobeerd.<br> zie [ de namen van het douanedomein beheren ](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) om meer te leren. |


## Fouten in domeinnaam {#domain-error}

Hier volgen enkele algemene fouten bij de verificatie van domeinnamen en de bijbehorende resoluties.

### Fout domein niet geïnstalleerd {#domain-not-installed}

<!-- This error may occur during domain validation of the EV/OV certificate even after you have checked that the certificate has been updated appropriately. -->

Wanneer u probeert een domeinafbeelding toe te voegen in Cloud Manager, wordt mogelijk het volgende foutbericht weergegeven:

*het domein is reeds geïnstalleerd in een Fastly rekening. Verwijder het bestand eerst uit het bestand voordat u het aan Cloud Service toevoegt.*

<!-- This message indicates that the domain is currently associated with a different Fastly account—typically outside of Adobe's control. To proceed, the domain must be disassociated from the other account before it can be added to the Adobe-managed Cloud Service. This issue usually occurs when the same domain is already mapped to a different origin in a non-Adobe Fastly configuration. -->

**de oorzaak van de Fout**
Met Fastly wordt een domein vergrendeld op de account die het eerst registreert en met andere accounts moet toestemming worden gevraagd om een subdomein te registreren. Bovendien kunt u met Snelheid alleen een apex-domein en bijbehorende subdomeinen toewijzen aan één Fastly-service en -account. Als u een bestaande Fastly-account hebt die dezelfde map en subdomeinen koppelt die worden gebruikt voor uw AEM Cloud Service-domeinen, ziet u deze fout.

**resolutie van de Fout**
De fout is als volgt gecorrigeerd:

* Verwijder de apex- en subdomeinen van de bestaande account voordat u het domein in Cloud Manager installeert.

* Gebruik deze optie om het apex-domein en alle subdomeinen te koppelen aan de AEM as a Cloud Service Fastly-account. Zie [ Werkend met domeinen ](https://www.fastly.com/documentation/guides/getting-started/domains/working-with-domains/working-with-domains/) in de Snelle documentatie voor extra details.

* Als uw apex-domein meerdere subdomeinen heeft voor AEM as a Cloud Service- en niet-AEM-sites die een koppeling moeten maken naar verschillende snelaccounts, probeert u het domein te installeren in Cloud Manager. Met dit proces kunt u subdomeinverbindingen beheren voor verschillende snelaccounts. Als de installatie van het domein mislukt, maakt u snel een Customer Support-ticket, zodat Adobe in uw naam snel een vervolg kan geven.

>[!TIP]
>
>Het oplossen van kwesties van de domeindelegatie met Fastly neemt typisch 1 tot 2 werkdagen. Daarom wordt aangeraden de domeinen ruim vóór hun live datum te installeren.

>[!NOTE]
>
>Geef de DNS van uw site niet door aan AEM as a Cloud Service IP&#39;s als het domein niet correct is geïnstalleerd.

## Bestaande CDN-configuraties voor aangepaste domeinnamen {#pre-existing-cdn}

Als u reeds een CDN (het Netwerk van de Levering van de Inhoud) configuratie voor uw namen van het douanedomein hebt, verschijnt een informatief bericht op de **en** milieu **pagina&#39;s van de Namen van het Domein van 0} Douane.** Het moedigt u aan om deze configuraties via UI toe te voegen zodat zij binnen Cloud Manager kunnen worden beheerd en worden bekeken.

Het bericht verdwijnt nadat alle bestaande omgevingsconfiguraties zijn gemigreerd met de interface. Het kan 1-2 werkdagen duren voordat het bericht verdwijnt.

Zie [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) voor meer details toevoegen.

## Volgende stappen {#next-steps}

Nadat u uw domeinstatus in Cloud Manager hebt geverifieerd, configureert u DNS-instellingen door DNS-, CNAME- of APEX-records toe te voegen die naar AEM as a Cloud Service wijzen. Ga aan het document [ te werk voeg een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toe om vestiging uw naam van het douanedomein voort te zetten.
