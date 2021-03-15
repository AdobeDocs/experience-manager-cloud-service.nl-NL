---
title: Status domeinnaam controleren
description: Status domeinnaam controleren
translation-type: tm+mt
source-git-commit: ddee11fdfa8cadfcd63472fd3c94cd8af555c856
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---


# Status domeinnaam {#check-status} controleren

U kunt bepalen of uw domeinnaam met succes is geverifieerd door op het statuspictogram voor de domeinnaam te klikken in de tabel betreffende omgevingen op de pagina Domeininstellingen.

>[!NOTE]
>Cloud Manager activeert automatisch een TXT-verificatie wanneer u Opslaan selecteert in de verificatiestap van de wizard Aangepast domein toevoegen. Voor verdere controles, moet u actief **verifiëren opnieuw** pictogram naast de status selecteren.

Cloud Manager controleert het eigendom van domeinen via de TXT-waarde en geeft een van de volgende statusberichten weer:

* **Domeinverificatie**
FailedTXT-waarde ontbreekt of wordt met fouten gedetecteerd. Volg de instructies en probeer het opnieuw. Wanneer u klaar bent, moet u de optie 
*Controleer* opnieuw het pictogram naast de status.

* **Domeinverificatie In**
ProgressVerification wordt uitgevoerd. Deze status wordt meestal weergegeven nadat u de optie 
*Controleer* opnieuw het pictogram naast de status.

* **Verified, Deployment**
FailedTXT verification was successfully. De CDN-implementatie is echter mislukt. Een vertegenwoordiger van de Adobe wordt automatisch op de hoogte gesteld.

* **Domein geverifieerd en**
geïmplementeerdDeze status geeft aan dat uw aangepaste domeinnaam klaar is om te worden gebruikt.
   >[!NOTE]
   >Op dit moment is uw aangepaste domeinnaam klaar om te worden getest en moet deze naar de domeinnaam van Cloud Manager worden verwezen. Verwijs naar [Vormende DNS Montages](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) om meer te leren.

* ****
DeletingDeletion of Custom Domain name is in process.

* **Verwijderen**
FailedDeletion of Custom Domain name failed. U moet het opnieuw proberen. Raadpleeg [Een aangepaste domeinnaam verwijderen](/help/implementing/cloud-manager/custom-domain-names/delete-custom-domain-name.md) voor meer informatie.


## Bestaande configuraties CDN voor IP Lijsten van gewenste personen {#pre-existing-cdn}

Klanten met milieu&#39;s die reeds bestaande configuraties CDN voor IP Lijsten van gewenste personen, SSL certificaten of de Namen van het Domein van de Douane omvatten zullen het volgende bericht in **IP Lijst van gewenste personen** en **Environment** detailspagina zien.

![](/help/implementing/cloud-manager/assets/ip-allow-list-1.png)

>[!NOTE]
>Om de reeds bestaande configuraties te zien en te beheren moeten zij via UI worden toegevoegd, zoals aangetoond in hieronder figuur.

![](/help/implementing/cloud-manager/assets/ip-allow-list-2.png)
