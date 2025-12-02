---
title: Domeintoewijzing toevoegen
description: Leer hoe u een domeintoewijzing toevoegt voor een Edge Delivery-site of een Cloud Manager-omgeving.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 672513d7-ee0a-4f6e-9ef0-7a41fabbaf9a
source-git-commit: 4935fbf5f0eb10f2f17280fb32f07d99f69eb875
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---


# Een domeintoewijzing toevoegen {#add-domain-mapping}

Als u een domein wilt koppelen aan een SSL-certificaat op de door Adobe beheerde CDN in uw programma, moet u een CDN-configuratie (Content Delivery Network) toevoegen.

Voor door Adobe beheerde CDN&#39;s zijn bij gebruik van een DV SSL-certificaat alleen sites met ACME-validatie toegestaan.

>[!IMPORTANT]
>
>Hebt u [&#x200B; een naam van het douanedomein &#x200B;](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toegevoegd en [&#x200B; een SSL certificaat &#x200B;](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) toegevoegd, respectievelijk? Als niet, moet u deze twee taken voltooien alvorens u een configuratie kunt toevoegen CDN.

Zie ook [&#x200B; Adobe Beheerde CDN &#x200B;](https://www.aem.live/docs/byo-cdn-adobe-managed).

**om een domeinafbeelding toe te voegen:**

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Voer afhankelijk van uw gebruiksgeval een van de volgende handelingen uit:

   | Hoofdletters gebruiken | Stappen |
   | --- | --- |
   | Ik wil een configuratie CDN aan een *bestaande* plaats van Edge Delivery in Cloud Manager toevoegen | a. In het linkerzijmenu, onder **Diensten**, klik ![&#x200B; pictogram Webpagina&#39;s &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **de Plaatsen van Edge Delivery**.<br> b. In de lijst van Edge Delivery, aan het eind van een rij die geen domein verbonden aan het heeft, klik ![&#x200B; Meer pictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).<br> c. Klik **vormen CDN**. |
   | Ik wil een configuratie CDN in Cloud Manager toevoegen | a. In het linkerzijmenu, onder **Diensten**, klik ![&#x200B; het pictogram van het Sociale netwerk &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Toewijzingen van het Domein**.<br> b. Bij de hoger-juiste hoek van de pagina van Toewijzingen van het Domein, voegt de klik **&#x200B;**&#x200B;toe. |

1. In het **Domein van de Kaart aan CDN** dialoogvakje, selecteer één van de volgende types CDN:

   * **Adobe Beheerde CDN (geadviseerd)** - Adobe beheerde CDN wordt gebruikt voor deze configuratie. Het omvat geautomatiseerde opstelling en beheer, en ingebouwde veiligheidseigenschappen.
   * **Andere leverancier CDN** - een zelf-beheerd CDN leveranciersnetwerk wordt gebruikt voor deze configuratie.

1. Gebaseerd op het geselecteerde type CDN in de vorige stap, doe het volgende:

   * **Adobe beheerde CDN**

     ![&#x200B; Domein van de Kaart aan CDN dialoogdoos met Adobe beheerde geselecteerde Keuzerondje CDN &#x200B;](/help/implementing/cloud-manager/assets/cdn/map-domain-to-cdn-adobe-managed.png)

      1. In de **drop-down lijst van de Oorsprong 0&rbrace;, selecteer één van het volgende:**

         | Vervolgkeuzelijst Oorsprong | Beschrijving |
         | --- | --- |
         | Sites | Selecteer een Edge Delivery-site. |
         | Omgeving | Selecteer een specifieke Cloud Service-omgeving waarop u zich wilt richten in uw AEM-configuratie.<br> in de **Rij** drop-down lijst, selecteer één van het volgende:<br>・ Selecteer **publiceren** om een levende, productiemilieu te richten waar de inhoud aan eind - gebruikers wordt geleverd.<br>・ Selecteer **Voorproef** voor het opvoeren of niet-productie milieu&#39;s waar u veranderingen test alvorens zij levend gaan. |

      1. In de **drop-down lijst van het Domein**, selecteer de domeinnaam die u wilt gebruiken.<br> Geen geverifieerde domeinen beschikbaar in de drop-down lijst? Zie [&#x200B; een naam van het douanedomein &#x200B;](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen.

      1. In de **SSL certificaat** drop-down lijst, selecteer een certificaat dat u wilt gebruiken.<br> Geen SSL certificaten beschikbaar in de drop-down lijst? Zie [&#x200B; een SSL certificaat &#x200B;](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) toevoegen.

      1. Klik **sparen**.

   * **Andere leverancier CDN**

     ![&#x200B; Domein van de Kaart aan CDN dialoogdoos met Adobe beheerde geselecteerde Keuzerondje CDN &#x200B;](/help/implementing/cloud-manager/assets/cdn/map-domain-to-cdn-other-provider.png)

     Gebruik de vermelde configuratiestappen om de vereiste montages in uw CDN toe te passen en de afbeelding te bevestigen. Zie ook [&#x200B; een naam van het douanedomein &#x200B;](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen.

      1. Klik **ik heb Mijn CDN** gevormd.

   <!-- OLD IMAGE/UI (/help/implementing/cloud-manager/assets/configure-cdn-dialog.png)-->

   <!-- In the **Domain** field, enter the customer-facing hostname you want to serve (for example, `www.example.com`) -->

1. Adobe raadt u aan de domeintoewijzing te testen.

## De domeintoewijzing testen {#test-domain-mapping}

U kunt verifiëren dat een nieuwe domeinafbeelding op Adobe-Beheerde CDN zonder het wachten op openbare DNS propagatie levend is.

Laad a **krullen** bevel dat DNS resolutie met voeten treedt en richt recht aan de CDN rand:

```bash
curl -svo /dev/null https://www.example.com \
--resolve www.example.com:443:151.101.3.10
```

* Vervang `www.example.com` door uw domein.
* Het IP-adres `151.101.3.10` is een van de IP&#39;s die kan worden gebruikt om toegang te krijgen tot de AEM Cloud Service. Zie ook {het verslag van 0} APEX [.](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#adobe-managed-cert-apex-record)

De markering `--resolve` dwingt het verzoek tot gespecificeerde IP en keert succes slechts terug nadat het certificaat en het verpletteren voor uw domein correct zijn geïnstalleerd.

