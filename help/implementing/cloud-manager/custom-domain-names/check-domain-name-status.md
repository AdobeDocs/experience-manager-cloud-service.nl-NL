---
title: Status domeinnaam controleren
description: Status domeinnaam controleren
translation-type: tm+mt
source-git-commit: 1c51560886515e092680c23db3e128758dcd7d99
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---


# Status domeinnaam {#check-status} controleren

U kunt bepalen of uw domeinnaam met succes is geverifieerd door op het statuspictogram voor de domeinnaam te klikken in de tabel betreffende omgevingen op de pagina Domeininstellingen.

>[!NOTE]
>Cloud Manager activeert automatisch een TXT-verificatie wanneer u Opslaan selecteert in de verificatiestap van de wizard Aangepast domein toevoegen. Voor verdere controles, moet u actief **verifiëren opnieuw** pictogram naast de status selecteren.

Cloud Manager controleert het eigendom van domeinen via de TXT-waarde en geeft een van de volgende statusberichten weer:

* **Domeinverificatie**
FailedTXT-waarde ontbreekt of wordt met fouten gedetecteerd. Volg de instructies en probeer het opnieuw. Wanneer u klaar bent, moet u het pictogram &quot;Opnieuw controleren&quot; naast de status selecteren.

* **Domeinverificatie In**
ProgressVerification wordt uitgevoerd. Deze status wordt meestal weergegeven nadat u het pictogram &quot;Opnieuw controleren&quot; naast de status hebt geselecteerd.

* **Verified, Deployment**
FailedTXT verification was successfully. De CDN-implementatie is echter mislukt. Een vertegenwoordiger van de Adobe wordt automatisch op de hoogte gesteld.

* **Domein geverifieerd en**
geïmplementeerdDeze status geeft aan dat uw aangepaste domeinnaam klaar is om te worden gebruikt. Opmerking: Op dit moment is uw aangepaste domeinnaam klaar om te worden getest en moet deze naar de domeinnaam van Cloud Manager worden verwezen. Ga naar het Vormen DNS Montages leren hoe te om dit te doen.

* ****
DeletingDeletion of Custom Domain name is in process.

* **Verwijderen**
FailedDeletion of Custom Domain name failed. U moet het opnieuw proberen. Ga naar Aangepaste domeinnaam verwijderen voor meer informatie over het onderwerp.

