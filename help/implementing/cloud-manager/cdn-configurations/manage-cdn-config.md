---
title: CDN-configuraties beheren
description: Leer hoe u met Cloud Manager CDN-configuraties voor een Edge Delivery-site of een Cloud Manager-omgeving kunt bewerken en bijwerken of verwijderen.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 02f9b035320bb4b6219d5ed4273554259fc09e59
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 0%

---


# CDN-configuraties beheren {#manage-cdn-configurations}

Leer hoe u met Cloud Manager CDN-configuraties voor een Edge Delivery-site of een Cloud Manager-omgeving kunt bewerken of verwijderen.

## Een CDN-configuratie bewerken via de pagina CDN-configuraties {#edit-cdn}

In Adobe Cloud Manager kunt u om verschillende redenen een CDN-configuratie (Content Delivery Network) bewerken, inclusief de milieulaag (Publish of Preview) en het SSL-certificaat.

* **de veranderingen van het Milieu**: Het aanpassen van de rijhulp past de montages CDN met het correcte milieu aan, hetzij voor levende productie (Publish) of het testen (Voorproef).
* **de verhogingen van de Veiligheid**: Het selecteren van een verschillend SSL certificaat kan noodzakelijk zijn wanneer het bijwerken van certificaten of het richten van naleving en veiligheidsbehoeften.
* **Optimaliserend prestaties**: Het uitgeven van de configuratie verzekert de correcte montages CDN voor het leveren van inhoud die op veranderende operationele behoeften wordt gebaseerd.

U kunt een configuratie bewerken zonder de bestaande configuratie volledig te verwijderen. Wijzigingen worden toegepast op de geselecteerde omgeving, bijvoorbeeld in de testfase of de productieomgeving, en kunnen van invloed zijn op de manier waarop inhoud wordt geleverd en beveiligd.

Een gebruiker moet een lid van de **BedrijfsEigenaar** of **rol zijn van de Manager van de Plaatsing** om deze taak te voltooien.

**om een configuratie CDN uit te geven van de CDN pagina van Configuraties:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.
1. In het zijpaneel, onder **Diensten**, klik ![ het sociale netwerkpictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **CDN Configuraties**.
1. In de **CDN Configuraties** lijst, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) aan het eind van een rij waarvan configuratie CDN u wilt bijwerken.

   ![ Uitgevend een configuratie CDN ](/help/implementing/cloud-manager/assets/cdn-config-edit.png)

1. Van het drop-down menu, geeft de klik **** uit.

1. In **geef CDN configuratie** dialoogdoos uit, plaats één of meerdere opties in de respectieve drop-down lijst.

   De opties die in de dialoogdoos worden getoond hangen af van of u een **beheerde Adobe CDN** of een **Andere leverancier CDN** (klant beheerde CDN) gebruikt.

1. Klik **Update**.

   Het statuut van uitgegeven CDN wordt bijgewerkt in de **CDN Configuratie** lijst om op de veranderingen te wijzen u aanbracht.


## Een CDN-configuratie bewerken via de pagina Omgevingen

De stappen voor het uitgeven van een configuratie CDN van de **pagina van Milieu&#39;s** zijn bijna het zelfde als wanneer [ het uitgeven van een configuratie CDN van de pagina van Configuraties CDN ](#edit-cdn), maar het ingangspunt verschilt.

**om een configuratie CDN van de pagina van Milieu&#39;s uit te geven:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. In het linkerzijmenu, klik **Milieu&#39;s**.

1. Voor de **pagina van Milieu&#39;s**, selecteer een milieu van belang.

1. Voor de pagina van de milieudetails, in de CDN Configuraties groeperen, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) dat aan de configuratie beantwoordt CDN u wilt uitgeven.

   ![ die domeinnaam op de pagina van de Details van het Milieu ingaan ](/help/implementing/cloud-manager/assets/cdn/environments-cdn-config.png)

1. In pop-up menu, geeft de klik **** uit.

1. In **geef CDN de dialoogdoos van de Configuratie** uit, plaats één of meerdere opties in de respectieve drop-down lijst.

De opties die in de dialoogdoos worden getoond hangen af van of u een **beheerde Adobe CDN** of een **Andere leverancier CDN** (klant beheerde CDN) gebruikt.

1. Klik **Update**.


<!-- ## Go live readiness {#go-live-readiness} 

1. ADD STEPS -->


## Een CDN-configuratie verwijderen {#delete-cdn}

Wanneer u een Adobe beheerde of klant beheerde configuratie CDN in Cloud Manager schrapt, worden het bijbehorende verpletteren van het domein en SSL certificaatmontages verwijderd. Het domein gebruikt niet meer CDN voor verkeerslevering, en om het even welke veiligheid of prestatiesverhogingen die door CDN worden verstrekt wordt verloren. U kunt de dienstverstoring ervaren tot een nieuwe configuratie opstelling is, of het re-toevoegen van geschrapte CDN of het toevoegen van nieuwe.

Een gebruiker moet een lid van de **BedrijfsEigenaar** of **rol zijn van de Manager van de Plaatsing** om deze taak te voltooien.

**om een configuratie te schrappen CDN:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. In het linkerzijpaneel, onder **Diensten**, klik **Configuraties CDN**.

1. In de lijst van Configuraties CDN, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) aan het eind van een rij die aan CDN beantwoordt u wilt verwijderen.

   ![ het Schrappen van een configuratie CDN ](/help/implementing/cloud-manager/assets/cdn-config-delete.png)

1. In het drop-down menu, klik **Schrapping**.

1. In het **de dialoogvakje van de Configuratie CDN van de Schrapping**, klik **Schrapping**.

1. Klik **Schrapping** opnieuw om de verwijdering van CDN van de plaats te bevestigen.


## Een CDN-configuratie verwijderen van de pagina Environment

De stappen voor het schrappen van een configuratie CDN van de **pagina van Milieu&#39;s** zijn bijna het zelfde als wanneer [ het schrappen van een configuratie CDN van de pagina van Configuraties CDN ](#edit-cdn), maar het ingangspunt verschilt.

**om een configuratie CDN van de pagina van Milieu&#39;s te schrappen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. In het linkerzijmenu, klik **Milieu&#39;s**.

1. Voor de **pagina van Milieu&#39;s**, selecteer een milieu van belang.

1. Voor de pagina van de milieudetails, in de **groepering van de Configuraties CDN 0}**, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) dat aan de configuratie beantwoordt CDN u wilt verwijderen.

   ![ CDN configuratiegroep op een pagina van het omgevingsdetail ](/help/implementing/cloud-manager/assets/cdn/environments-cdn-config.png)

1. In het drop-down menu, klik **Schrapping**.

1. In het **de dialoogvakje van de Configuratie CDN van de Schrapping**, klik **Schrapping**.

1. Klik **Schrapping** opnieuw om de verwijdering van CDN van de plaats te bevestigen.


