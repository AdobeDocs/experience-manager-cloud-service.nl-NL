---
title: IP-Lijsten van gewenste personen beheren
description: Leer om, de status van IP lijsten van gewenste personen in Cloud Manager te bekijken uit te geven te schrappen en te controleren.
exl-id: 6efabe53-3f45-47d4-ac1f-979cae0ab33e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 0%

---

# IP-Lijsten van gewenste personen beheren {#manage-ip-allow-lists}

Leer om, de status van IP lijsten van gewenste personen in Cloud Manager te bekijken uit te geven te schrappen en te controleren.

## IP-Lijsten van gewenste personen weergeven en bijwerken {#update-ip-allow-lists}

Een gebruiker in de **BedrijfsEigenaar** of **rol van de Manager van de Plaatsing** kan deze stappen volgen en een IP lijst van gewenste personen bijwerken.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.
1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.
1. Navigeer aan het **scherm van Milieu&#39;s** van de **pagina van het Overzicht**.
1. Navigeer aan de **IP Lijsten van gewenste personen** pagina van het **milieu&#39;s** scherm.
1. Identificeer de rij voor de IP lijsten van gewenste personen die u wilt bekijken of bijwerken.
1. Klik op de knop met de ellips rechts van de rij.
1. Selecteer de **Mening &amp; van de Update** optie.
1. De **Mening &amp; van de Update** tovenaar toont de naam, IP adressen (of waaiers) die de regel samen met de milieu&#39;s en de diensten bepalen waarop de regel wordt toegepast.
1. Wijzig desgewenst de naam of het IP-adres en bevestig uw verzending.

Het toevoegen van of het verwijderen van een nieuwe IP waaier aan een IP lijst van gewenste personen past automatisch het op alle overeenkomstige milieu/de diensten toe waarop het eerder werd toegepast.

De updates kunnen niet aan een IP lijst van gewenste personen worden gemaakt terwijl een vroegere update lopend is en niet is voltooid.

## Het controleren van de Status van IP Lijsten van gewenste personen {#check-allow-list-status}

1. Logon aan Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie en het programma.

1. Navigeer aan het **scherm van Milieu&#39;s** van de **pagina van het Overzicht**.

1. Klik het **pictogram van de Status** voor de IP lijst van gewenste personen van de lijst op het **scherm van Milieu&#39;s** en selecteer de **IP Lijsten van gewenste personen** pagina.

1. Cloud Manager toont het statuut van de lijst van gewenste personen zoals die [ in de volgende sectie wordt beschreven.](#status)

### Status van een IP Lijst van gewenste personen {#status}

[ wanneer het controleren van het statuut van IP lijsten van gewenste personen, ](#check-allow-list-status) kunnen zij één van de volgende waarden hebben.

* **Toegepast** - de IP lijst van gewenste personen wordt met succes toegepast op één of meerdere milieu&#39;s.

* **het Bijwerken** - een update aan de IP lijst van gewenste personen is lopend, die één of meerdere toepassing of unapplication van de lijst kan omvatten.

   * Elke toepassing/niet-toepassing is vermeld samen met zijn eigen status van **niet begonnen**, **Bezig**, **Volledig**, of **Ontbroken**.

* **Ontbroken** - één of meerdere toepassing of unapplication proces van een ontbroken update.
   * Elke toepassing en toepassing wordt samen met de status vermeld.
      * De status is **Ontbroken** als één toepassing/unapplication in de update ontbreekt.
      * De status blijft als **Ontbroken** tot alle mislukkingen worden ontruimd.
         * Selecteer **opnieuw** pictogram naast de status zodat kunt u de mislukking ontruimen.
      * U kunt geen IP lijst van gewenste personen met a **bijwerken of schrappen ontbrak** status.

* **het Schrappen** - Een schrapping van een IP lijst van gewenste personen is lopend.
   * Bij verwijderen wordt de lijst uit alle services verwijderd.
   * Elke unapplication wordt vermeld samen met zijn eigen status van **niet Begonnen**, **Bezig**, **Volledig**, of **Ontbroken**.
   * Wanneer de verwijderbewerking is voltooid:
      * De IP lijst van gewenste personen verschijnt niet in de IP lijst van de lijst van gewenste personen.
      * De IP lijst van gewenste personen wordt niet toegepast op om het even welke dienst in het programma in Cloud Manager.

* **Ontbroken Schrapping** - één of meerdere unapplications ontbrak tijdens een schrappingsverrichting.

   * Elke unapplication wordt vermeld samen met de status **Volledige** of **Ontbroken**.
   * De status wordt **Ontbroken Schrapping** als één unapplication ontbreekt.
   * De status blijft als **Ontbroken Schrapping** tot alle mislukkingen worden ontruimd.
      * Selecteer **Schrapping** van het elliptische menu bij uiterst rechts van de rij in de lijst zodat kunt u om het even welke mislukking ontruimen.
   * U kunt geen IP lijst van gewenste personen bijwerken terwijl de status **Ontbroken** is.

## Een IP-Lijst van gewenste personen verwijderen {#delete-allow-list}

Een gebruiker in de **BedrijfsEigenaar** of **rol van de Manager van de Plaatsing** kan deze stappen volgen en een IP lijst van gewenste personen bijwerken.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.
1. Navigeer aan het **scherm van Milieu&#39;s** van de **pagina van het Overzicht**.
1. Navigeer aan de **IP Lijsten van gewenste personen** pagina van het **milieu&#39;s** scherm.
1. Identificeer de rij van de IP lijst van gewenste personen die u wilt schrappen.
1. Selecteer het ellipsmenu helemaal rechts van de rij.
1. Klik **Schrapping**.
1. Bevestig je verzending.

Het schrappen van een IP lijst van gewenste personen maakt automatisch het van alle diensten ongedaan en schrapt het van de lijst.

## Bestaande CDN-configuraties {#pre-existing-cdn}

Als u een reeds bestaande configuratie CDN voor uw IP lijsten van gewenste personen hebt, is er een informatief bericht op de **IP Lijst van gewenste personen** pagina. Het bericht moedigt u aan om deze configuraties als gebruikersinterface toe te voegen zodat zijn zij zichtbaar en configureerbaar in Cloud Manager.

Het bericht verdwijnt zodra alle bestaande omgevingsconfiguraties zijn gemigreerd met de interface. Het kan 1-2 werkdagen duren voordat het bericht verdwijnt.

Zie [ Toevoegend een IP Lijst van gewenste personen ](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) voor meer details.

Een gelijkaardig bericht wordt ook verstrekt op de **SSL Certificaten** en de **milieu&#39;s** pagina&#39;s voor milieu&#39;s die reeds bestaande configuraties CDN voor SSL certificaten of de namen van het douanedomein hebben.
