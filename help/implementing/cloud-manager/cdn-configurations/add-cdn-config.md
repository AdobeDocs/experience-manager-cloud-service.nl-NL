---
title: Een CDN-configuratie toevoegen
description: Leer over hoe te om een configuratie CDN voor een plaats van Edge Delivery of een milieu van Cloud Manager toe te voegen.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 672513d7-ee0a-4f6e-9ef0-7a41fabbaf9a
source-git-commit: 2d1382c84d872719332986baa5829d1623d9d9a6
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---


# Een CDN-configuratie (Content Delivery Network) toevoegen {#add-cdn}

Als u een domein wilt koppelen aan een SSL-certificaat op de door Adobe beheerde CDN binnen uw programma, moet u een CDN-configuratie (Content Delivery Network) toevoegen.

Voor Adobe beheerde CDNs, wanneer het gebruiken van DV certificaten, slechts worden de plaatsen met de bevestiging van ACME toegelaten.

>[!IMPORTANT]
>
>Hebt u [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toegevoegd en [ een SSL certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) toegevoegd, respectievelijk? Als niet, moet u deze twee taken voltooien alvorens u een configuratie kunt toevoegen CDN.

**om een configuratie toe te voegen CDN:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Voer afhankelijk van uw gebruiksgeval een van de volgende handelingen uit:

   | Hoofdletters gebruiken | Stappen |
   | --- | --- |
   | Ik wil een configuratie CDN aan een *bestaande* plaats van Edge Delivery in Cloud Manager toevoegen | a. In het linkernavigatievenster, onder **Diensten**, klik **de Plaatsen van Edge Delivery**.<br> b. Klik in de Edge Delivery-tabel aan het einde van een rij waaraan geen domein is gekoppeld, op de ellips.<br> c. Klik **vormen CDN**.  ![ klik vormen CDN voor een plaats van Edge Delivery ](/help/implementing/cloud-manager/assets/cm-eds-config-cdn.png) |
   | Ik wil een configuratie CDN in Cloud Manager toevoegen | a. In het linkernavigatievenster, onder **Diensten**, klik **Configuraties CDN**.<br> b. Dichtbij de hoger-juiste hoek van de CDN pagina van Configuraties, voegt de klik **toe**. |

1. In **vorm CDN** dialoogdoos, in de **Vervolgkeuzelijst van de Oorsprong**, selecteer één van het volgende:

   ![ vorm CDN dialoogdoos ](/help/implementing/cloud-manager/assets/configure-cdn-dialog.png)

   | Oorsprong | Beschrijving |
   | --- | --- |
   | Sites | Selecteer een Edge Delivery-site. |
   | Omgeving | Selecteer een specifieke omgeving voor Cloud Servicen waarop u zich wilt richten binnen de AEM.<br> in de **Rij** drop-down lijst, selecteer één van het volgende:<br>・ Selecteer **Publish** om een levend, productiemilieu te richten waar de inhoud aan eind - gebruikers wordt geleverd.<br>・ Selecteer **Voorproef** voor het opvoeren of niet-productie milieu&#39;s waar u veranderingen test alvorens zij levend gaan. |

1. Selecteer uw type CDN en bijbehorende configuratie door één van het volgende te selecteren:

   | CDN-type | Configuratiedetails |
   | --- | --- |
   | CDN met beheerde Adobe | Onder **details van de Configuratie**, doe het volgende:<br> a. In de **drop-down van het Domein** lijst, selecteer de domeinnaam die u wilt gebruiken.<br> Geen geverifieerde domeinen beschikbaar in de drop-down lijst? Zie [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen.<br> b. In de **SSL certificaat** drop-down lijst, selecteer een certificaat dat u wilt gebruiken.<br> Geen SSL certificaten beschikbaar in de drop-down lijst? Zie [ een SSL certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) toevoegen. |
   | Andere CDN-provider | Selecteer deze optie als u uw eigen leverancier CDN en niet de Adobe beheerde CDN gebruikt die aan u beschikbaar is.<br> onder **details van de Configuratie**, in de **drop-down lijst van het Domein**, selecteer de domeinnaam die u wilt gebruiken.<br> Geen geverifieerde domeinen beschikbaar in de drop-down lijst? Zie [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen. |

1. Klik **sparen**.
