---
title: Status domeinnaam controleren
description: Status domeinnaam controleren
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
source-git-commit: 4533cbc689d69cbe126791b4426123f890754507
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Status domeinnaam controleren {#check-status}

U kunt bepalen of uw domeinnaam met succes is geverifieerd door op het statuspictogram voor de domeinnaam te klikken in de tabel betreffende omgevingen op de pagina Domeininstellingen.

>[!NOTE]
>Cloud Manager activeert automatisch een TXT-verificatie wanneer u Opslaan selecteert in de verificatiestap van de wizard Aangepast domein toevoegen. Voor verdere controles moet u actief selecteren **Opnieuw controleren** naast de status.

Cloud Manager controleert het eigendom van domeinen via de TXT-waarde en geeft een van de volgende statusberichten weer:

* **Domeinverificatie mislukt**
De TXT-waarde ontbreekt of wordt met fouten gedetecteerd. Volg de instructies en probeer het opnieuw. Wanneer u klaar bent, moet u de optie 
*Opnieuw controleren* naast de status.

* **Domeinverificatie wordt uitgevoerd**
Verificatie wordt uitgevoerd. Deze status wordt meestal weergegeven nadat u de optie 
*Opnieuw controleren* naast de status.

* **Geverifieerd, implementatie mislukt**
TXT-verificatie is gelukt. De CDN-implementatie is echter mislukt. Neem contact op met uw Adobe-vertegenwoordiger.

* **Domein geverifieerd en geïmplementeerd**
Deze status geeft aan dat uw aangepaste domeinnaam klaar is om te worden gebruikt.
   >[!NOTE]
   >Op dit moment is uw aangepaste domeinnaam klaar om te worden getest en moet deze naar de domeinnaam van Cloud Manager worden verwezen. Zie [DNS-instellingen configureren](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) voor meer informatie.

* **Verwijderen**
Verwijderen van aangepaste domeinnaam wordt uitgevoerd.

* **Verwijderen mislukt**
Verwijderen van aangepaste domeinnaam is mislukt. U moet het opnieuw proberen. Zie [Een aangepaste domeinnaam verwijderen](/help/implementing/cloud-manager/custom-domain-names/delete-custom-domain-name.md) voor meer informatie.


## Bestaande CDN-configuraties voor aangepaste domeinnamen {#pre-existing-cdn}

Klanten met omgevingen die reeds bestaande CDN-configuraties voor IP-Lijsten van gewenste personen, SSL-certificaten of aangepaste domeinnamen bevatten, zien het volgende bericht in het dialoogvenster **IP-Lijst van gewenste personen** en de **Omgeving** detailpagina. Het bericht dat op UI wordt getoond zal verdwijnen zodra de klant alle reeds bestaande omgevingsconfiguraties via UI volledig heeft gemigreerd en het kan 1-2 werkdagen voor het bericht vergen om te verdwijnen.

>[!NOTE]
>Om de reeds bestaande configuraties te kunnen zien en beheren moeten zij via UI worden toegevoegd. Zie [Een aangepaste domeinnaam toevoegen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) voor meer informatie .

![](/help/implementing/cloud-manager/assets/ip-allow-list-message1.png)

![](/help/implementing/cloud-manager/assets/ip-allow-list-message2.png)
