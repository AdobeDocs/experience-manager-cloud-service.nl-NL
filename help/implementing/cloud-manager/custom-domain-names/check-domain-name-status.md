---
title: Status domeinnaam controleren
description: Leer hoe u kunt bepalen of uw aangepaste domeinnaam is geverifieerd door Cloud Manager.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
source-git-commit: 878381f9c5780864f218a00a272b1600d578dcca
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---


# Status domeinnaam controleren {#check-status}

U kunt de status van uw aangepaste domeinnaam bepalen in Cloud Manager.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Omgevingen** van het scherm **Overzicht** pagina.

1. Klikken op **Domeininstellingen** in het linkernavigatievenster.

1. Klik op de knop **Status** pictogram voor de domeinnaam.

Cloud Manager controleert het eigendom van het domein via de TXT-waarde en geeft een van de volgende statusberichten weer.

* **Domeinverificatie mislukt** - De TXT-waarde ontbreekt of wordt met fouten gedetecteerd.

   * Volg de instructies die worden gegeven om het probleem op te lossen.
   * Wanneer u klaar bent, moet u de optie **Opnieuw controleren** naast de status.

* **Domeinverificatie wordt uitgevoerd** - De verificatie wordt uitgevoerd.

   * Deze status wordt meestal weergegeven nadat u de optie **Opnieuw controleren** naast de status.

* **Geverifieerd, implementatie mislukt** - De TXT-verificatie is gelukt, maar de CDN-implementatie is mislukt.

   * Neem in dergelijke gevallen contact op met uw Adobe-vertegenwoordiger.

* **Domein geverifieerd en geïmplementeerd** - Deze status geeft aan dat uw aangepaste domeinnaam klaar is om te worden gebruikt.

   * Op dit moment is uw aangepaste domeinnaam klaar om te worden getest en moet deze naar de domeinnaam van Cloud Manager worden verwezen.
   * Raadpleeg het document [DNS-instellingen configureren](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) voor meer informatie.

* **Verwijderen** - De verwijdering van een aangepaste domeinnaam wordt uitgevoerd.

* **Verwijderen mislukt** - Het verwijderen van een aangepaste domeinnaam is mislukt en moet opnieuw worden geprobeerd.

   * Raadpleeg het document [Aangepaste domeinnamen beheren](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) voor meer informatie.

Cloud Manager activeert automatisch een TXT-verificatie wanneer u **Opslaan** over de verificatiestap van de **Aangepast domein toevoegen** wizard. Voor verdere controles, moet u actief selecteren opnieuw verifieert pictogram naast de status.

## Bestaande CDN-configuraties voor aangepaste domeinnamen {#pre-existing-cdn}

Als u een reeds bestaande configuratie CDN voor uw namen van het douanedomein hebt, zal er een informatief bericht op het **Aangepaste domeinnamen** en **Omgeving** pagina&#39;s, die u aanmoedigen om deze configuraties toe te voegen via de gebruikersinterface zodat ze zichtbaar en configureerbaar zijn in Cloud Manager.

Het bericht verdwijnt zodra alle bestaande omgevingsconfiguraties zijn gemigreerd met de interface. Het kan 1-2 werkdagen duren voordat het bericht verdwijnt.

Raadpleeg het document [Een aangepaste domeinnaam toevoegen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) voor meer informatie .
