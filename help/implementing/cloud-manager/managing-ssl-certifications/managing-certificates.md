---
title: SSL-certificaten beheren
description: Leer hoe u Cloud Manager kunt gebruiken om de status van uw SSL-certificaten te controleren en hoe u deze kunt bewerken, vervangen, bijwerken en verwijderen.
exl-id: ad6170f4-93bd-4bac-9c54-63c35a0d4f06
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: bf903736e256bb9275bad6c0271b31b8dbdec625
workflow-type: tm+mt
source-wordcount: '1048'
ht-degree: 0%

---


# SSL-certificaten beheren {#managing-ssl-certificates}

Leer hoe u Cloud Manager kunt gebruiken om de status van uw SSL-certificaten te controleren en hoe u deze kunt bewerken, vervangen, bijwerken en verwijderen.

## De status van SSL-certificaten controleren {#checking-status-an-ssl-certificate}

Cloud Manager geeft een overzicht van de status van alle certificaten voor uw programma.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer het aangewezen programma.
1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.
1. In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het zijmenu te openbaren.
1. Onder de **rubriek van de Diensten**, klik ![ Slot gesloten pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL Certificaten**.

De **SSL Certificaten** pagina verstrekt de status van uw SSL certificaten.

| Status van het SSL-certificaat | Beschrijving |
| --- | --- |
| Groen | Het certificaat is ten minste 14 dagen geldig vanaf de huidige datum. |
| Oranje | Het certificaat verloopt over minder dan 14 dagen.<br>・ Zorg ervoor dat u een abonnement hebt om uw certificaat te vernieuwen en dit te vervangen door de gebruikersinterface van Cloud Manager om mogelijke toegang tot of uitval van de site te voorkomen.<br>・ Cloud Manager verzendt regelmatig meldingen in de gebruikersinterface om u te waarschuwen voor een aanstaande vervaldatum van een certificaat. |
| Rood | Het SSL-certificaat is verlopen.<br> zie [ Update een verlopen klant beheerde SSL certificaat ](#update-ssl-certificate) of [ Schrap een SSL certificaat ](#deleting-an-ssl-certificate). |

## Een verlopen door de klant beheerd SSL-certificaat bijwerken {#update-ssl-certificate}

Wanneer een door klant beheerd certificaat verloopt, werken domeinen die in gebruik zijn met het verlopen certificaat niet meer. Als u uw certificaten bijwerkt, blijft uw domein naar wens werken.

Een gebruiker moet een lid van de **BedrijfsEigenaar** of **rol zijn van de Manager van de Plaatsing** om deze taak te voltooien.

>[!IMPORTANT]
>
>Neem het nieuwe certificaat niet op in de certificaatketen wanneer u een SSL-certificaat toevoegt of bijwerkt. Als u deze code opneemt, kan het uploaden niet worden voltooid.

**om een verlopen klant beheerde SSL certificaat bij te werken:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer het aangewezen programma.
1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.
1. In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het zijmenu te openbaren.
1. Onder de **rubriek van de Diensten**, klik ![ Slot gesloten pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL Certificaten**.
1. In de rij van het verlopen klant beheerde certificaat dat u wilt bijwerken, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) bij uiterst rechts, dan klik **Mening en Update**.

   ![ werk een verlopen klant beheerde SSL certificatie bij ](/help/implementing/cloud-manager/assets/ssl/ssl-cert-update.png)

1. In het **de dialoogvakje van de Mening &amp; van het Certificaat van de Update SSL**, doe het volgende:

   * (Facultatief) op het **gebied van de Naam van het Certificaat**, typ een nieuwe naam.
   * Op het **gebied van het Certificaat**, kleef de nieuwe sleutel van de certificaatinhoud.
   * Op het **Privé zeer belangrijke** gebied, werk dit gebied bij slechts als u veranderingen in het certificaat aanbracht.
   * Op het **gebied van de ketting van het Certificaat** (of ketting van vertrouwen), kleef de certificaatketting.

1. Klik **Update** om uw veranderingen te bewaren en hen automatisch toe te passen.


>[!NOTE]
>
>Als twee of meer SAN-certificaten dezelfde SAN-domeinvermelding dekken en een van deze certificaten wordt bijgewerkt, installeert het systeem het bijgewerkte certificaat voor het domein.
>
>Zie [ problemen oplossen SSL van het Certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md#wrong-san-cert) voor meer informatie.

## Een verlopen door de klant beheerd SSL-certificaat vervangen {#replace-ssl-certificate}

Volg de zelfde stappen die in [ worden beschreven Werk een verlopen SSL certificaat ](#update-ssl-certificate) bij om een verlopen, klant beheerde SSL certificaat te vervangen.

## De naam wijzigen van een door Adobe beheerd SSL-certificaat (#rename-an-ssl-certificate)

Hieronder volgen enkele redenen waarom u de naam van een SSL-certificaat wilt wijzigen:

* **Verbeterde organisatie**: Het anders noemen van het certificaat kan helpen zijn doel verduidelijken, zoals het identificeren van welk milieu (bijvoorbeeld, het opvoeren, productie) of domein het voor is.
* **vermijdend verwarring**: Als u veelvoudige certificaten beheert, kan een duidelijke, beschrijvende naam helpen fouten verhinderen, als het toepassen van het verkeerde certificaat op het verkeerde domein.
* **Naleving en controle**: De behoorlijk genoemde certificaten kunnen gemakkelijker zijn om voor veiligheid en controledoeleinden te volgen.

**om een Adobe beheerde SSL certificaat anders te noemen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer het aangewezen programma.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het zijmenu te openbaren.

1. Onder de **rubriek van de Diensten**, klik ![ Slot gesloten pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL Certificaten**.

1. Op de **SSL Certificaten** pagina, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) aan het eind van een rij waarvan **Adobe** SSL certificaat beheerde u wilt anders noemen.

1. In het drop-down menu, klik **anders noemen**.

1. In **noem DV Certificaat** dialoogdoos anders, op het **de naam van het Certificaat** tekstgebied, ga de nieuwe naam van het certificaat in.

1. Klik **anders noemen**.


## Een SSL-certificaat verwijderen {#deleting-an-ssl-certificate}

Het verwijderen van door Adobe beheerde of door de klant beheerde SSL-certificaten uit Cloud Manager is een permanente handeling die niet ongedaan kan worden gemaakt. Het wordt aanbevolen SSL-bestanden lokaal op te slaan voordat u ze verwijdert in Cloud Manager.

>[!NOTE]
>
>U kunt geen door Adobe beheerd SSL-certificaat verwijderen waaraan een of meer actieve domeinen zijn gekoppeld. Alle gekoppelde actieve domeinen moeten worden verwijderd voordat het SSL-certificaat wordt verwijderd. Zie [ de namen van het douanedomein beheren ](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) om meer te leren.

Een gebruiker moet een lid van de **BedrijfsEigenaar** of **rol zijn van de Manager van de Plaatsing** om deze taak te voltooien.

**om een SSL certificaat te schrappen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer het aangewezen programma.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het zijmenu te openbaren.

1. Onder de **rubriek van de Diensten**, klik ![ Slot gesloten pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL Certificaten**.

1. Voor de SSL pagina van Certificaten, in de lijstrij van het certificaat u wilt schrappen, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) bij uiterst rechts, dan klik **Schrapping**.

   Als **Schrapping** een informatiepictogram zoals gezien in het volgende beeld heeft, zie de Nota hierboven.

   ![ knoop van de Schrapping met het pictogram van de Informatie ](/help/implementing/cloud-manager/assets/ssl/ssl-cert-delete-infoicon.png)

1. In het **SSL van de Schrapping** dialoogvakje, klik **Schrapping** om de schrapping te bevestigen.

1. Stel de pijpleiding in werking om het geschrapte certificaat ongedaan te maken.


## Bestaande CDN-configuraties {#pre-existing-cdn}

Als u reeds een configuratie CDN voor uw SSL certificaat hebt, toont de **SSL Certificaten** pagina een informatief bericht. Het moedigt u aan om deze configuraties via UI toe te voegen zodat zij in Cloud Manager zichtbaar en handelbaar zijn.

Het bericht verdwijnt nadat alle bestaande omgevingsconfiguraties zijn gemigreerd met de interface. Het kan een tot twee werkdagen duren voordat het bericht verdwijnt.

Zie [ een SSL certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) voor meer details toevoegen.

Een gelijkaardig bericht wordt ook verstrekt op de **IP Lijst van gewenste personen** en de **milieu&#39;s** pagina&#39;s voor milieu&#39;s die reeds bestaande CDN configuraties voor IP Lijsten van gewenste personen of de namen van het douanedomein hebben.
