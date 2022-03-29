---
title: SSL-certificaten beheren
description: Leer hoe u Cloud Manager gebruikt om de status van uw SSL-certificaten te controleren en hoe u deze kunt bewerken, vervangen, bijwerken en verwijderen.
source-git-commit: 95539851590456b6b5ecbfeb0df8fc7bc7dde74b
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---


# SSL-certificaten beheren {#managing-ssl-certificates}

Leer hoe u Cloud Manager gebruikt om de status van uw SSL-certificaten te controleren en hoe u deze kunt bewerken, vervangen, bijwerken en verwijderen.

## De status van SSL-certificaten controleren {#checking-status-an-ssl-certificate}

De status van uw SSL-certificaten kan in één oogopslag worden geïnterpreteerd vanaf de pagina met het SSL-certificaat.

* **Groen** - Deze status geeft aan dat uw certificaat ten minste 60 dagen geldig is vanaf de huidige datum.

* **Oranje** - Deze status geeft aan dat uw certificaat over minder dan 60 dagen verloopt.
   * Het is tijd om ervoor te zorgen dat u een abonnement hebt om uw certificaat te vernieuwen en dit te vervangen via de interface van Cloud Manager om mogelijke toegang tot of uitval van sites te voorkomen.
   * Cloud Manager verzendt regelmatig meldingen in de gebruikersinterface om u te waarschuwen voor het binnenkort verlopen van een certificaat.

* **Rood** - Deze status geeft aan dat het SSL-certificaat is verlopen.

## Bestaande CDN-configuraties {#pre-existing-cdn}

Als u een reeds bestaande CDN configuratie voor uw SSL certificaat hebt, zal er een informatief bericht op het **SSL-certificaten** , waarbij u wordt aangemoedigd deze configuraties toe te voegen via de gebruikersinterface, zodat ze zichtbaar en configureerbaar zijn in Cloud Manager.

Het bericht verdwijnt zodra alle bestaande omgevingsconfiguraties zijn gemigreerd met de interface. Het kan 1-2 werkdagen duren voordat het bericht verdwijnt.

Raadpleeg het document [Een SSL-certificaat toevoegen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) voor meer informatie .

Een soortgelijk bericht wordt ook gegeven op de **IP-Lijst van gewenste personen** en de **Omgevingen** pagina&#39;s voor milieu&#39;s die reeds bestaande configuraties CDN voor IP lijsten van gewenste personen of douanedomeinnamen hebben.

## Een SSL-certificaat bijwerken {#update-ssl-certificate}

Wanneer een certificaat verloopt, werken domeinen die in gebruik zijn met het verlopen certificaat niet meer. Als u uw certificaten bijwerkt via de volgende stappen, zorgt u ervoor dat uw domein naar wens blijft werken.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.
1. Navigeren naar **Omgevingen** van het scherm **Overzicht** pagina.
1. Ga naar de **SSL-certificaten** van het scherm **Omgevingen** scherm.
1. Er wordt een tabel met een rij weergegeven voor elk SSL-certificaat dat is geïnstalleerd in uw programma. Klik op de knop met de ovaal helemaal rechts in de rij van het certificaat dat u wilt bijwerken en selecteer **Weergeven en bijwerken**.
1. De certificaatdetails worden weergegeven en kunnen worden bijgewerkt.

>[!NOTE]
>
>Een gebruiker moet lid zijn van **Zakelijke eigenaar** of **Implementatiebeheer** rol om een SSL-certificaat bij te werken in Cloud Manager.

## Een SSL-certificaat vervangen {#replace-ssl-certificate}

Een SSL-certificaat kan worden vervangen door dezelfde stappen uit te voeren als in de sectie worden beschreven [Een SSL-certificaat bijwerken.](#update-ssl-certificate)

## Een SSL-certificaat verwijderen {#deleting-an-ssl-certificate}

Certificaten verwijderen uit Cloud Manager is een permanente handeling die niet ongedaan kan worden gemaakt. U kunt het beste SSL-bestanden lokaal opslaan voordat Adobe ze verwijdert in Cloud Manager.

Met Cloud Manager kunt u geen SSL-certificaat verwijderen waaraan een of meer domeinen zijn gekoppeld. Alle bijbehorende domeinen moeten worden geschrapt alvorens het SSL certificaat te schrappen. Raadpleeg het document [Een aangepaste domeinnaam verwijderen](/help/implementing/cloud-manager/custom-domain-names/delete-custom-domain-name.md) voor meer informatie.

Ga als volgt te werk om een SSL-certificaat te verwijderen.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.
1. Navigeren naar **Omgevingen** van het scherm **Overzicht** pagina.
1. Ga naar de **SSL-certificaten** van het scherm **Omgevingen** scherm.
1. Er wordt een tabel met een rij weergegeven voor elk SSL-certificaat dat is geïnstalleerd in uw programma. Klik op de knop met de ovaal helemaal rechts in de rij van het certificaat dat u wilt verwijderen en selecteer **Verwijderen**.
1. Bevestig de verwijdering in de **SSL-certificaat verwijderen** .

>[!NOTE]
>
>Een gebruiker moet lid zijn van **Zakelijke eigenaar** of **Implementatiebeheer** rol om een SSL-certificaat te verwijderen in Cloud Manager.