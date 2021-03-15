---
title: Status controleren van een SSL-certificaat - SSL-certificaten beheren
description: Status controleren van een SSL-certificaat - SSL-certificaten beheren
translation-type: tm+mt
source-git-commit: 0b04d43c8b5bb28286e616f0bd902c05ec56ec05
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---


# Status controleren van een SSL-certificaat {#checking-status-an-ssl-certificate}

De status van uw SSL-certificaten kan in één oogopslag worden geïnterpreteerd vanaf de pagina met het SSL-certificaat.

U kunt de status van een SSL-certificaat identificeren aan de hand van de volgende kleurenschema&#39;s:

* ****
GreenGeeft aan dat uw certificaat in de toekomst ten minste 60 dagen geldig is.

* ****
OrangeGeeft aan dat uw certificaat over minder dan 60 dagen verloopt. Het is tijd om ervoor te zorgen dat u een abonnement hebt om uw certificaat te vernieuwen en dit te vervangen via de interface van Cloud Manager om mogelijke toegang tot of uitval van sites te voorkomen. Cloud Manager verzendt regelmatig meldingen in de gebruikersinterface om u te waarschuwen voor het binnenkort verlopen van een certificaat.

* ****
RedGeeft aan dat uw SSL-certificaat ondanks meerdere meldingen is verlopen.

## Bestaande configuraties CDN voor IP Lijsten van gewenste personen {#pre-existing-cdn}

Klanten met milieu&#39;s die reeds bestaande configuraties CDN voor IP Lijsten van gewenste personen, SSL certificaten of de Namen van het Domein van de Douane omvatten zullen het volgende bericht in **IP Lijst van gewenste personen** en **Environment** detailspagina zien. Het bericht dat op UI wordt getoond zal verdwijnen zodra de klant alle reeds bestaande omgevingsconfiguraties via UI volledig heeft gemigreerd en het kan 1-2 werkdagen voor het bericht vergen om te verdwijnen.

![](/help/implementing/cloud-manager/assets/ip-allow-list-1.png)

>[!NOTE]
>Om de reeds bestaande configuraties te zien en te beheren moeten zij via UI worden toegevoegd, zoals aangetoond in hieronder figuur.

![](/help/implementing/cloud-manager/assets/ip-allow-list-2.png)