---
title: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.10.0
description: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.10.0
feature: Release Information
exl-id: null
source-git-commit: c6c1d3bef85afda0ff86ec073d0ac91ad532c93b
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.10.0 {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.10.0.

>[!NOTE]
>Klik op [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.10.0 is 14 oktober 2021.


### Wat is er nieuw? {#what-is-new}

* Ter voorbereiding op enkele aanstaande wijzigingen wordt nu in de gebruikersinterface verwezen naar en geëtiketteerd als bestaande implementatiepijplijnen **Volledige stapel** pijpleidingen.

* De kaart van de pijpleiding is verfrist om één enkel, geïntegreerd gezicht te tonen dat zowel productie als niet productiepijpleidingen toont, en de gebruiker kan Looppas/pauze direct selecteren/hervat van het actiemenu verbonden aan elke pijpleiding.

* Een gebruiker in de rol van de Manager van de Plaatsing kan de pijpleiding van de Productie op een zelfbediening manier via UI nu schrappen.

* De ervaring met toevoegen en bewerken van pijpleidingen is vernieuwd en gebruikt nu vertrouwde, moderne modellen.

* Gebruikers van Cloud Manager kunnen nu rechtstreeks vanuit de gebruikersinterface feedback verzenden via de **Feedback** op de rechterbovenhoek van de landingspagina.

* De jaarlijkse SLA-grafieken kunnen nu worden gedownload vanuit de gebruikersinterface van Cloud Manager.

* De kwaliteit van de code en de niet-productiepijpleiding zullen nu een efficiënter oppervlakkig klonen proces tijdens de bouwstijlstap gebruiken, die tot een snellere bouwtijd voor klanten met bijzonder grote git bewaarplaatsen leidt.

* Voeg IP de tovenaar van de Lijst van gewenste personen nu toe zal de gebruiker informeren als maximum toegestaan aantal IP Lijsten van gewenste personen is bereikt.

* De documentatie van de API voor Cloud Manager bevat nu een interactieve speelruimte waarmee aangemelde gebruikers vanuit hun browser kunnen experimenteren met de API. Zie [Afspelen van Cloud Manager-API](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) voor meer informatie .

* De knopinfo op de programmakaart is beschrijfbaarder als een selectieoptie onder &#39;Navigeren naar&#39; is uitgeschakeld. Het toont nu &quot;een productiemilieu bestaat niet.&quot;

### Opgeloste problemen {#bug-fixes}

* In zeldzame situaties, wanneer een personeel van Adobe de omgeving van een klant zou herstellen, werd het herstel als volledig beschouwd alvorens het milieu volledig operationeel was.

* Bepaalde interne verzoeken die tijdens het creëren van het milieu werden gedaan, werden niet opnieuw beproefd.

* Als de plaatsing mislukte fout na de controle van de domeinnaam voorkomt, is het foutenbericht verbeterd om de klant te verzoeken om hun vertegenwoordiger van de Adobe te contacteren.

