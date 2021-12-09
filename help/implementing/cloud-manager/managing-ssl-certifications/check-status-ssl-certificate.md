---
title: Status controleren van een SSL-certificaat - SSL-certificaten beheren
description: Status controleren van een SSL-certificaat - SSL-certificaten beheren
exl-id: 59d81356-2fa9-43db-bfa5-c2896c530eaa
source-git-commit: 828490e12d99bc8f4aefa0b41a886f86fee920b4
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Status van een SSL-certificaat controleren {#checking-status-an-ssl-certificate}

De status van uw SSL-certificaten kan in één oogopslag worden geïnterpreteerd vanaf de pagina met het SSL-certificaat.

U kunt de status van een SSL-certificaat identificeren aan de hand van de volgende kleurenschema&#39;s:

* **Groen**
Hiermee geeft u aan dat uw certificaat ten minste 60 dagen geldig is in de toekomst.

* **Oranje**
Geeft aan dat uw certificaat over minder dan 60 dagen verloopt. Het is tijd om ervoor te zorgen dat u een abonnement hebt om uw certificaat te vernieuwen en dit te vervangen via de interface van Cloud Manager om mogelijke toegang tot of uitval van sites te voorkomen. Cloud Manager verzendt regelmatig meldingen in de gebruikersinterface om u te waarschuwen voor het binnenkort verlopen van een certificaat.

* **Rood**
Geeft aan dat uw SSL-certificaat ondanks meerdere meldingen is verlopen.

## Bestaande CDN-configuraties {#pre-existing-cdn}

Klanten met omgevingen die reeds bestaande CDN-configuraties voor IP-Lijsten van gewenste personen, SSL-certificaten of aangepaste domeinnamen bevatten, zien het volgende bericht in het dialoogvenster **IP-Lijst van gewenste personen** en de **Omgeving** detailpagina. Het bericht dat op UI wordt getoond zal verdwijnen zodra de klant alle reeds bestaande omgevingsconfiguraties via UI volledig heeft gemigreerd en het kan 1-2 werkdagen voor het bericht vergen om te verdwijnen.

>[!NOTE]
>Om de reeds bestaande configuraties te kunnen zien en beheren moeten zij via UI worden toegevoegd. Zie [Een SSL-certificaat toevoegen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) voor meer informatie .

![](/help/implementing/cloud-manager/assets/ip-allow-list-message1.png)

![](/help/implementing/cloud-manager/assets/ip-allow-list-message2.png)
