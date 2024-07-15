---
title: SSL-certificaten beheren
description: Leer hoe u Cloud Manager kunt gebruiken om de status van uw SSL-certificaten te controleren en hoe u deze kunt bewerken, vervangen, bijwerken en verwijderen.
exl-id: ad6170f4-93bd-4bac-9c54-63c35a0d4f06
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---


# SSL-certificaten beheren {#managing-ssl-certificates}

Leer hoe u Cloud Manager kunt gebruiken om de status van uw SSL-certificaten te controleren en hoe u deze kunt bewerken, vervangen, bijwerken en verwijderen.

## De status van SSL-certificaten controleren {#checking-status-an-ssl-certificate}

De status van uw SSL-certificaten kan in één oogopslag worden geïnterpreteerd vanaf de pagina met het SSL-certificaat.

* **Groen** - Deze status wijst erop dat uw certificaat voor minstens 14 dagen van de huidige datum geldig is.

* **Oranje** - Deze status wijst erop dat uw certificaat in minder dan 14 dagen zal verlopen.
   * Het wordt tijd om ervoor te zorgen dat u een abonnement hebt om uw certificaat te vernieuwen en dit te vervangen door de gebruikersinterface van Cloud Manager om mogelijke toegang tot of uitval van sites te voorkomen.
   * Cloud Manager stuurt regelmatig meldingen in de gebruikersinterface om u te waarschuwen voor het binnenkort verlopen van een certificaat.

* **Rood** - Deze status wijst erop dat het SSL certificaat is verlopen.

## Een SSL-certificaat bijwerken {#update-ssl-certificate}

Wanneer een certificaat verloopt, werken domeinen die in gebruik zijn met het verlopen certificaat niet meer. Als u uw certificaten bijwerkt via de volgende stappen, zorgt u ervoor dat uw domein naar wens blijft werken.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie
1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.
1. Navigeer aan **Milieu&#39;s** scherm van de **pagina van het Overzicht**.
1. Navigeer aan het **SSL Certificaten** scherm van het **milieu&#39;s** scherm.
1. U ziet een tabel met een rij voor elk SSL-certificaat dat in uw programma is geïnstalleerd. Klik de ellipsis knoop bij uiterst rechts in de rij van het certificaat u **Mening &amp; Update** bijwerken en wilt selecteren.
1. De certificaatdetails worden weergegeven en kunnen worden bijgewerkt.
1. Stel de pijpleiding in werking om het bijgewerkte certificaat op te stellen.

>[!NOTE]
>
>Een gebruiker moet een lid van de **BedrijfsEigenaar** of **rol van de Manager van de Plaatsing** zijn om een SSL certificaat in Cloud Manager bij te werken.

## Een SSL-certificaat vervangen {#replace-ssl-certificate}

Een SSL certificaat kan worden vervangen door de zelfde stappen te volgen zoals die in de sectie [ worden beschreven Bijwerkend een SSL Certificaat.](#update-ssl-certificate)

## Een SSL-certificaat verwijderen {#deleting-an-ssl-certificate}

Het verwijderen van certificaten uit Cloud Manager is een permanente handeling die niet ongedaan kan worden gemaakt. De beste manier is om SSL-bestanden lokaal op te slaan voordat u ze verwijdert in Cloud Manager.

Met Cloud Manager kunt u geen SSL-certificaat verwijderen waaraan een of meer domeinen zijn gekoppeld. Alle bijbehorende domeinen moeten worden geschrapt alvorens het SSL certificaat te schrappen. Zie [ het Leiden Namen van het Domein van de Douane ](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) om meer te leren.

Ga als volgt te werk om een SSL-certificaat te verwijderen.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.
1. Navigeer aan **Milieu&#39;s** scherm van de **pagina van het Overzicht**.
1. Navigeer aan het **SSL Certificaten** scherm van het **milieu&#39;s** scherm.
1. U ziet een tabel met een rij voor elk SSL-certificaat dat in uw programma is geïnstalleerd. Klik de ellips bij uiterst rechts in de rij van het certificaat u **Schrapping** schrappen en wilt selecteren.
1. Bevestig de schrapping in de **SSL van het Certificaat** dialoog van de Schrapping.
1. Stel de pijpleiding in werking om het geschrapte certificaat ongedaan te maken.

>[!NOTE]
>
>Een gebruiker moet een lid van de **BedrijfsEigenaar** of **rol van de Manager van de Plaatsing** zijn om een SSL certificaat in Cloud Manager te schrappen.

## Bestaande CDN-configuraties {#pre-existing-cdn}

Als u een reeds bestaande configuratie CDN voor uw SSL certificaat hebt, is er een informatief bericht op de **SSL Certificaten** pagina, die u aanmoedigt om deze configuraties via UI toe te voegen zodat zijn zij zichtbaar en configureerbaar in Cloud Manager.

Het bericht verdwijnt zodra alle bestaande omgevingsconfiguraties zijn gemigreerd met de interface. Het kan 1-2 werkdagen duren voordat het bericht verdwijnt.

Zie [ Toevoegend een SSL Certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) voor meer details.

Een gelijkaardig bericht wordt ook verstrekt op de **IP Lijst van gewenste personen** en de **milieu&#39;s** pagina&#39;s voor milieu&#39;s die reeds bestaande CDN configuraties voor IP lijsten van gewenste personen of de namen van het douanedomein hebben.
