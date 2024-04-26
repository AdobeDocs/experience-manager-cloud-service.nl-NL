---
title: IP-Lijsten van gewenste personen beheren
description: Leer om, de status van IP lijsten van gewenste personen in de Manager van de Wolk te bekijken uit te geven te schrappen en te controleren.
exl-id: 6efabe53-3f45-47d4-ac1f-979cae0ab33e
source-git-commit: d1b2226a1deec2e71056c43c84672cb4a358bc8c
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 0%

---

# IP-Lijsten van gewenste personen beheren {#manage-ip-allow-lists}

Leer om, de status van IP lijsten van gewenste personen in de Manager van de Wolk te bekijken uit te geven te schrappen en te controleren.

## IP-Lijsten van gewenste personen weergeven en bijwerken {#update-ip-allow-lists}

Een gebruiker in het dialoogvenster **Zakelijke eigenaar** of **Implementatiebeheer** De rol kan deze stappen volgen om een IP lijst van gewenste personen te bekijken en bij te werken.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.
1. Op de **[Mijn programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)** -console, selecteert u het programma.
1. Ga naar de **Omgevingen** van het scherm **Overzicht** pagina.
1. Ga naar de **IP-Lijsten van gewenste personen** pagina van de **Omgevingen** scherm.
1. Identificeer de rij voor de IP lijsten van gewenste personen die u wilt bekijken of bijwerken.
1. Klik op de knop met de ellips rechts van de rij.
1. Selecteer de **Weergeven en bijwerken** -optie.
1. De **Weergeven en bijwerken** de tovenaar toont de naam, IP adressen (of waaiers) die de regel samen met de milieu&#39;s en de diensten bepalen waarop de regel wordt toegepast.
1. Wijzig desgewenst de naam of het IP-adres en bevestig uw verzending.

Het toevoegen van of het verwijderen van een nieuwe IP waaier aan een IP lijst van gewenste personen past automatisch het op alle overeenkomstige milieu/de diensten toe waarop het eerder werd toegepast.

De updates kunnen niet aan een IP lijst van gewenste personen worden gemaakt terwijl een vroegere update lopend is en niet is voltooid.

## Het controleren van de Status van IP Lijsten van gewenste personen {#check-allow-list-status}

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Omgevingen** van het scherm **Overzicht** pagina.

1. Klik op de knop **Status** pictogram voor de IP lijst van gewenste personen van de lijst op **Omgevingen** en selecteert u de **IP-Lijsten van gewenste personen** pagina.

1. Cloud Manager geeft de status van de lijst van gewenste personen weer zoals beschreven [in de volgende paragraaf.](#status)

### Status van een IP Lijst van gewenste personen {#status}

[Wanneer het controleren van de status van IP lijsten van gewenste personen,](#check-allow-list-status) ze kunnen een van de volgende waarden hebben.

* **Toegepast** - De IP lijst van gewenste personen wordt met succes toegepast op één of meerdere milieu&#39;s.

* **Bijwerken** - Er wordt een update van de IP-lijst van gewenste personen uitgevoerd, die een of meer toepassingen of het niet toepassen van de lijst kan omvatten.

   * Elke toepassing/niet-toepassing wordt samen met de eigen status van **Niet gestart**, **In uitvoering**, **Voltooid**, of **Mislukt**.

* **Mislukt** - Een of meer toepassings- of verwijderingsprocedures van een update zijn mislukt.
   * Elke toepassing en toepassing wordt samen met de status vermeld.
      * De status is **Mislukt** als één toepassing/niet-toepassing in de update mislukt.
      * De status blijft ongewijzigd **Mislukt** totdat alle fouten zijn gewist.
         * Selecteer de **Opnieuw** pictogram naast de status zodat u de fout kunt wissen.
      * U kunt geen IP lijst van gewenste personen bijwerken of schrappen met een **Mislukt** status.

* **Verwijderen** - Een schrapping van een IP lijst van gewenste personen is lopend.
   * Bij verwijderen wordt de lijst uit alle services verwijderd.
   * Elke unapplication wordt vermeld samen met zijn eigen status van **Niet gestart**, **In uitvoering**, **Voltooid**, of **Mislukt**.
   * Wanneer de verwijderbewerking is voltooid:
      * De IP lijst van gewenste personen verschijnt niet in de IP lijst van de lijst van gewenste personen.
      * De IP lijst van gewenste personen wordt niet toegepast op om het even welke dienst in het programma in de Manager van de Wolk.

* **Verwijderen is mislukt** - Een of meer toepassingen zijn tijdens het verwijderen mislukt.

   * Elke unapplication wordt samen met de status vermeld **Voltooid** of **Mislukt**.
   * De status wordt **Verwijderen is mislukt** als één unapplication ontbreekt.
   * De status blijft ongewijzigd **Verwijderen is mislukt** totdat alle fouten zijn gewist.
      * Selecteren **Verwijderen** in het menu met ovalen helemaal rechts van de rij in de tabel, zodat u eventuele fouten kunt wissen.
   * U kunt geen IP lijst van gewenste personen bijwerken terwijl de status is **Mislukt**.

## Een IP-Lijst van gewenste personen verwijderen {#delete-allow-list}

Een gebruiker in het dialoogvenster **Zakelijke eigenaar** of **Implementatiebeheer** De rol kan deze stappen volgen om een IP lijst van gewenste personen te bekijken en bij te werken.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.
1. Ga naar de **Omgevingen** van het scherm **Overzicht** pagina.
1. Ga naar de **IP-Lijsten van gewenste personen** pagina van de **Omgevingen** scherm.
1. Identificeer de rij van de IP lijst van gewenste personen die u wilt schrappen.
1. Selecteer het ellipsmenu helemaal rechts van de rij.
1. Klikken **Verwijderen**.
1. Bevestig je verzending.

Het schrappen van een IP lijst van gewenste personen maakt automatisch het van alle diensten ongedaan en schrapt het van de lijst.

## Bestaande CDN-configuraties {#pre-existing-cdn}

Als u een reeds bestaande configuratie CDN voor uw IP lijsten van gewenste personen hebt, is er een informatief bericht op het **IP-Lijst van gewenste personen** pagina. In dit bericht wordt u aangeraden deze configuraties via de gebruikersinterface toe te voegen, zodat ze zichtbaar en configureerbaar zijn in Cloud Manager.

Het bericht verdwijnt zodra alle bestaande omgevingsconfiguraties zijn gemigreerd met de interface. Het kan 1-2 werkdagen duren voordat het bericht verdwijnt.

Zie [Een IP-Lijst van gewenste personen toevoegen](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) voor meer informatie .

Een soortgelijk bericht wordt ook gegeven op de **SSL-certificaten** en de **Omgevingen** pagina&#39;s voor omgevingen die reeds bestaande CDN-configuraties voor SSL-certificaten of aangepaste domeinnamen hebben.
