---
title: IP-Lijsten van gewenste personen beheren
description: Leer hoe u de status van uw IP-lijsten van gewenste personen in Cloud Manager kunt weergeven, bewerken, verwijderen en controleren.
exl-id: 6efabe53-3f45-47d4-ac1f-979cae0ab33e
source-git-commit: 3080427529bb65e27721e05069012b33579fdd73
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# IP-Lijsten van gewenste personen beheren {#manage-ip-allow-lists}

Leer hoe u de status van uw IP-lijsten van gewenste personen in Cloud Manager kunt weergeven, bewerken, verwijderen en controleren.

## IP-Lijsten van gewenste personen weergeven en bijwerken {#update-ip-allow-lists}

Een gebruiker in de **Zakelijke eigenaar** of **Implementatiebeheer** De rol kan deze stappen volgen om een IP lijst van gewenste personen te bekijken en bij te werken.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.
1. Navigeren naar **Omgevingen** van het scherm **Overzicht** pagina.
1. Ga naar de **IP-Lijsten van gewenste personen** pagina van **Omgevingen** scherm.
1. Identificeer de rij voor de IP lijsten van gewenste personen die u wenst om te bekijken of bij te werken.
1. Klik op de knop met de ellips rechts van de rij.
1. Selecteer **Weergeven en bijwerken** optie.
1. De **Weergeven en bijwerken** De tovenaar zal de naam, IP adressen (of waaiers) tonen die de regel samen met de milieu&#39;s en de dienst bepalen waarop de regel wordt toegepast.
1. Wijzig de naam of het IP-adres en bevestig uw verzending.

Het toevoegen van of het verwijderen van een nieuwe IP waaier aan een IP lijst van gewenste personen zal automatisch het op alle overeenkomstige milieu/de diensten toepassen waarop het eerder werd toegepast.

De updates kunnen niet aan een IP lijst van gewenste personen worden gemaakt terwijl een vroegere update lopend is en niet heeft voltooid.

## Het controleren van de Status van IP Lijsten van gewenste personen {#check-allow-list-status}

Voer de volgende stappen uit om de status van IP-lijsten van gewenste personen te controleren.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Navigeren naar **Omgevingen** van het scherm **Overzicht** pagina.

1. Klik op de knop **Status** pictogram voor de IP lijst van gewenste personen van de lijst op **Omgevingen** en selecteert u de **IP-Lijsten van gewenste personen** pagina.

1. Cloud Manager geeft de status van de lijst van gewenste personen weer zoals beschreven [in de volgende paragraaf.](#status)

### Status van een IP Lijst van gewenste personen {#status}

[Wanneer het controleren van de status van IP lijsten van gewenste personen,](#check-allow-list-status) ze kunnen een van de volgende waarden hebben.

* **Toegepast** - De IP lijst van gewenste personen wordt met succes toegepast op één of meerdere milieu&#39;s.

* **Bijwerken** - Er wordt een update van de IP-lijst van gewenste personen uitgevoerd, die een of meer toepassingen kan bevatten of de toepassing van de lijst kan opheffen.

   * Elke toepassing/niet-toepassing wordt samen met de eigen status van **Niet gestart**, **In uitvoering**, **Voltooid**, of **Mislukt**.

* **Mislukt** - Een of meer toepassings- of niet-toepassingsprocessen van een update zijn mislukt.
   * Elke toepassing en toepassing wordt samen met de status vermeld.
      * De status is **Mislukt** als één toepassing/niet-toepassing in de update mislukt.
      * De status blijft ongewijzigd **Mislukt** totdat alle fouten zijn gewist.
         * U moet de **Opnieuw** pictogram naast de status om de fout te wissen.
      * U kunt geen IP lijst van gewenste personen bijwerken of schrappen met een **Mislukt** status.

* **Verwijderen** - Er wordt een IP-lijst van gewenste personen verwijderd.
   * Bij Verwijderen wordt de lijst niet meer toegepast op alle services.
   * Elke niet-toepassing wordt samen met de eigen status van **Niet gestart**, **In uitvoering**, **Voltooid**, of **Mislukt**.
   * Zodra de schrappingsverrichting wordt voltooid, zal de IP lijst van gewenste personen:
      * Niet meer in de IP lijst van de lijst van gewenste personen verschijnen.
      * Niet meer toepassen op services in het programma in Cloud Manager.

* **Verwijderen is mislukt** - Een of meer niet-toepassingen zijn tijdens het verwijderen mislukt.

   * Elke niet-toepassing wordt samen met de status vermeld **Voltooid** of **Mislukt**.
   * De status **Verwijderen is mislukt** als één niet-toepassing mislukt.
   * De status blijft ongewijzigd **Verwijderen is mislukt** totdat alle fouten zijn gewist.
      * U moet **Verwijderen** in het menu met ovalen helemaal rechts van de rij in de tabel om eventuele fouten te wissen.
   * U kunt geen IP lijst van gewenste personen bijwerken terwijl de status **Mislukt**.

## Een IP-Lijst van gewenste personen verwijderen {#delete-allow-list}

Een gebruiker in de **Zakelijke eigenaar** of **Implementatiebeheer** De rol kan deze stappen volgen om een IP lijst van gewenste personen te bekijken en bij te werken.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.
1. Navigeren naar **Omgevingen** van het scherm **Overzicht** pagina.
1. Ga naar de **IP-Lijsten van gewenste personen** pagina van **Omgevingen** scherm.
1. Identificeer de rij van de IP lijst van gewenste personen die u wenst te schrappen.
1. Selecteer het ellipsmenu helemaal rechts van de rij.
1. Klikken **Verwijderen**.
1. Bevestig je verzending.

Als u een IP-lijst van gewenste personen verwijdert, wordt deze automatisch van alle services verwijderd en uit de tabel verwijderd.

## Bestaande CDN-configuraties {#pre-existing-cdn}

Als u een reeds bestaande configuratie CDN voor uw IP lijsten van gewenste personen hebt, zal er een informatief bericht op het **IP-Lijst van gewenste personen** , waarbij u wordt aangemoedigd deze configuraties toe te voegen via de gebruikersinterface, zodat ze zichtbaar en configureerbaar zijn in Cloud Manager.

Het bericht verdwijnt zodra alle bestaande omgevingsconfiguraties zijn gemigreerd met de interface. Het kan 1-2 werkdagen duren voordat het bericht verdwijnt.

Raadpleeg het document [Een IP-lijst van gewenste personen toevoegen](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) voor meer informatie .

Een soortgelijk bericht wordt ook gegeven op de **SSL-certificaten** en de **Omgevingen** pagina&#39;s voor omgevingen die reeds bestaande CDN-configuraties voor SSL-certificaten of aangepaste domeinnamen hebben.
