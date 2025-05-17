---
title: Domeintoewijzingen beheren
description: Leer hoe u met Cloud Manager CDN-configuraties voor een Edge Delivery-site of een Cloud Manager-omgeving kunt bewerken en bijwerken of verwijderen.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 2ec16c91-0195-4732-a26d-ac223e10afb9
source-git-commit: c1040572085183f0ddd2a12f159f74e399c12df3
workflow-type: tm+mt
source-wordcount: '1071'
ht-degree: 0%

---

# Domeintoewijzingen beheren {#manage-domain-mappings}

Leer hoe u met Cloud Manager CDN-configuraties voor een Edge Delivery-site of een Cloud Manager-omgeving kunt bewerken of verwijderen.

## Een CDN-configuratie bewerken via de pagina Domeintoewijzingen {#edit-domain-mapping}

In Adobe Cloud Manager kunt u om verschillende redenen een CDN-configuratie (Content Delivery Network) bewerken, inclusief de milieulaag (Publiceren of Voorvertoning) en het SSL-certificaat.

* **de veranderingen van het Milieu**: Het aanpassen van de rijhulp past de montages CDN met het correcte milieu aan, hetzij voor levende productie (publiceren) of het testen (Voorproef).
* **de verhogingen van de Veiligheid**: Het selecteren van een verschillend SSL certificaat kan noodzakelijk zijn wanneer het bijwerken van certificaten of het richten van naleving en veiligheidsbehoeften.
* **Optimaliserend prestaties**: Het uitgeven van de configuratie verzekert de correcte montages CDN voor het leveren van inhoud die op veranderende operationele behoeften wordt gebaseerd.

U kunt een configuratie bewerken zonder de bestaande configuratie volledig te verwijderen. Wijzigingen worden toegepast op de geselecteerde omgeving, bijvoorbeeld in de testfase of de productieomgeving, en kunnen van invloed zijn op de manier waarop inhoud wordt geleverd en beveiligd.

Een gebruiker moet een lid van de **BedrijfsEigenaar** of **rol zijn van de Manager van de Plaatsing** om deze taak te voltooien.

**om een configuratie CDN van de Pagina van Toewijzingen van het Domein uit te geven:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.
1. In het linkerzijmenu, onder **Diensten**, klik ![ het netwerkpictogram van de Sociale Zaken ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Toewijzingen van het Domein**.
1. In de **lijst van Toewijzingen van het Domein**, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) aan het eind van een rij waarvan configuratie CDN u wilt bijwerken.

1. Van het drop-down menu, geeft de klik **&#x200B;**&#x200B;uit.

1. In **geef CDN configuratie** dialoogdoos uit, plaats één of meerdere opties in de respectieve drop-down lijst.

   De opties in de dialoogdoos worden getoond hangen af van of u **Adobe beheerde CDN** of een **Andere CDN leverancier** (klant beheerde CDN) gebruikt.

1. Klik **Update**.

   Het statuut van uitgegeven CDN wordt bijgewerkt in de **Lijst van Toewijzingen van het Domein** om op de veranderingen te wijzen u aanbracht.


## Een CDN-configuratie bewerken via de pagina Omgevingen

De stappen voor het uitgeven van een configuratie CDN van de **pagina van Milieu&#39;s** zijn bijna het zelfde als wanneer [ het uitgeven van een configuratie CDN van de pagina van Toewijzingen van het Domein ](#edit-cdn), maar het ingangspunt verschilt.

**om een configuratie CDN van de pagina van Milieu&#39;s uit te geven:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. In het linkerzijmenu, klik ![ het pictogram van Gegevens ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Milieu&#39;s**.

1. Voor de **pagina van Milieu&#39;s**, selecteer een milieu van belang.

1. Voor de pagina van milieudetails, in de Mappingen van het Domein groeperen, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) dat aan de configuratie beantwoordt CDN u wilt uitgeven.

1. In pop-up menu, geeft de klik **&#x200B;**&#x200B;uit.

1. In **geef de dialoogdoos van de Toewijzing van het Domein uit**, plaats één of meerdere opties in de respectieve drop-down lijst.

   De opties in de dialoogdoos worden getoond hangen af van of u **Adobe beheerde CDN** of een **Andere CDN leverancier** (klant beheerde CDN) gebruikt.

1. Klik **Update**.


## Live gereedheid: DNS-instellingen voor een aangepast domein configureren {#go-live-readiness}

Alvorens een douanedomein verkeer kan dienen, moet u DNS configuratie met uw DNS leverancier voltooien. Na het opstellen van een domeinafbeelding, en het klikken **gaat levend**, toont Cloud Manager een dialoogdoos die u door het DNS proces van de verslagopstelling begeleidt. U kunt live gaan door een recordtype CNAME of een recordtype A toe te voegen.

<!-- See also [APEX record](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#adobe-managed-cert-cname-record#adobe-managed-cert-apex-record) and [CNAME record](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#adobe-managed-cert-cname-record). -->

**om Go levende bereidheid te vormen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.
1. In het linkerzijmenu, onder **Diensten**, klik ![ het netwerkpictogram van de Sociale Zaken ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Toewijzingen van het Domein**.
1. In de lijst van Toewijzingen van het Domein, klik **gaan levend** dichtbij het eind van een rij die aan CDN beantwoordt waarvan levende gereedheid van de go u wilt vormen.

   ![ ga levende gereedheidsdialoogdoos ](/help/implementing/cloud-manager/assets/domain-mappings-go-live-readiness.png)

1. In **ga levende gereedheid** dialoogdoos, doe één van het volgende:

   | Optie | Stappen |
   | --- | --- |
   | EEN RECORD configureren | Aanbevolen voor hoofddomeinen zoals `example.com`<br><ol><li>Meld u aan bij het portal van uw DNS-serviceprovider.<li>Ga naar de DNS sectie van Verslagen.<li>Creeer een verslag van A om aan alle vermelde IP adressen te richten.</li></ol> |
   | CNAME configureren | Aanbevolen voor aangepaste domeinen zoals `www.example.com`<br><ol><li>Meld u aan bij het portal van uw DMS-serviceprovider.<li>Ga naar de DNS sectie van Verslagen.<li>Wijs `cdn.adobeaemcloud.com` (CNAME-record) toe aan de DNS-record van de DNS-serviceprovider (uw aangepaste domein). Deze afbeelding zorgt ervoor dat de verzoeken die bij het douanedomein worden ontvangen aan Adobe CDN opnieuw worden gericht.</li></ol> |

1. In **ga levende gereedheid** dialoogdoos, klik **O.K.** om het verslag te bewaren.

   Wacht op DNS propagatie; het kan verscheidene notulen aan een paar uren vergen.

   Wanneer de kolom **[!UICONTROL Status]** in de tabel Domeintoewijzingen wordt bijgewerkt naar **[!UICONTROL Verified]** , is het aangepaste domein klaar voor gebruik. U kunt ![ moeten klikken verfrist pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Refresh_18_N.svg) om de status bij te werken.

## Een CDN-configuratie verwijderen {#delete-cdn}

Wanneer u een door Adobe beheerde of klant beheerde CDN-configuratie in Cloud Manager verwijdert, worden de bijbehorende routering- en SSL-certificaatinstellingen van het domein verwijderd. Het domein gebruikt niet meer CDN voor verkeerslevering, en om het even welke veiligheid of prestatiesverhogingen die door CDN worden verstrekt wordt verloren. U kunt de dienstverstoring ervaren tot een nieuwe configuratie opstelling is, of het re-toevoegen van geschrapte CDN of het toevoegen van nieuwe.

Een gebruiker moet een lid van de **BedrijfsEigenaar** of **rol zijn van de Manager van de Plaatsing** om deze taak te voltooien.

**om een configuratie te schrappen CDN:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. In het linkerzijmenu, onder **Diensten**, klik ![ het netwerkpictogram van de Sociale Zaken ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Toewijzingen van het Domein**.

1. In de lijst van Toewijzingen van het Domein, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) aan het eind van een rij die aan CDN beantwoordt u wilt verwijderen, dan **Schrapping** klikken.

1. In de **Toewijzing van het Domein van de Schrapping** dialoogdoos, klik **Schrapping**.

1. Klik **Schrapping** opnieuw om de verwijdering van CDN van de plaats te bevestigen.


## Een CDN-configuratie verwijderen van de pagina Environment

De stappen voor het schrappen van een configuratie CDN van de **pagina van Milieu&#39;s** zijn bijna het zelfde als wanneer [ het schrappen van een configuratie CDN van de pagina van Toewijzingen van het Domein ](#edit-cdn), maar het ingangspunt verschilt.

**om een configuratie CDN van de pagina van Milieu&#39;s te schrappen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. In het linkerzijmenu, klik ![ het pictogram van Gegevens ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Milieu&#39;s**.

1. Voor de **pagina van Milieu&#39;s**, selecteer een milieu van belang.

1. Op de pagina van milieudetails, in de **Toewijzingen van het Domein** groeperen, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) dat aan de configuratie CDN beantwoordt u wilt verwijderen, dan **Schrapping** klikken.

1. In de **Toewijzing van het Domein van de Schrapping** dialoogdoos, klik **Schrapping**.

1. Klik **Schrapping** opnieuw om de verwijdering van CDN van de plaats te bevestigen.
