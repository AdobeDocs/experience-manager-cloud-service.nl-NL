---
title: Domeintoewijzing toevoegen
description: Leer hoe u een domeintoewijzing toevoegt voor een Edge Delivery-site of een Cloud Manager-omgeving.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 672513d7-ee0a-4f6e-9ef0-7a41fabbaf9a
source-git-commit: 829881a91a6f1c9a020c04ec581ce010b07bae01
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---


# Een domeintoewijzing toevoegen {#add-domain-mapping}

Als u een domein wilt koppelen aan een SSL-certificaat op de door Adobe beheerde CDN in uw programma, moet u een CDN-configuratie (Content Delivery Network) toevoegen.

Voor door Adobe beheerde CDN&#39;s zijn bij gebruik van een DV SSL-certificaat alleen sites met ACME-validatie toegestaan.

>[!IMPORTANT]
>
>Hebt u [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toegevoegd en [ een SSL certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) toegevoegd, respectievelijk? Als niet, moet u deze twee taken voltooien alvorens u een configuratie kunt toevoegen CDN.

Zie ook [ Adobe Beheerde CDN ](https://www.aem.live/docs/byo-cdn-adobe-managed).

**om een domeinafbeelding toe te voegen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Voer afhankelijk van uw gebruiksgeval een van de volgende handelingen uit:

   | Hoofdletters gebruiken | Stappen |
   | --- | --- |
   | Ik wil een configuratie CDN aan een *bestaande* plaats van Edge Delivery in Cloud Manager toevoegen | a. In het linkerzijmenu, onder **Diensten**, klik ![ pictogram Webpagina&#39;s ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **de Plaatsen van Edge Delivery**.<br> b. In de lijst van Edge Delivery, aan het eind van een rij die geen domein verbonden aan het heeft, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).<br> c. Klik **vormen CDN**. |
   | Ik wil een configuratie CDN in Cloud Manager toevoegen | a. In het linkerzijmenu, onder **Diensten**, klik ![ het pictogram van het Sociale netwerk ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Toewijzingen van het Domein**.<br> b. Bij de hoger-juiste hoek van de pagina van Toewijzingen van het Domein, voegt de klik **** toe. |

1. In **vorm CDN** dialoogdoos, in de **Vervolgkeuzelijst van de Oorsprong**, selecteer één van het volgende:

   ![ vorm CDN dialoogdoos ](/help/implementing/cloud-manager/assets/configure-cdn-dialog.png)

   | Oorsprong | Beschrijving |
   | --- | --- |
   | Sites | Selecteer een Edge Delivery-site. |
   | Omgeving | Selecteer een specifieke Cloud Service-omgeving waarop u zich wilt richten in uw AEM-configuratie.<br> in de **Rij** drop-down lijst, selecteer één van het volgende:<br>・ Selecteer **publiceren** om een levende, productiemilieu te richten waar de inhoud aan eind - gebruikers wordt geleverd.<br>・ Selecteer **Voorproef** voor het opvoeren of niet-productie milieu&#39;s waar u veranderingen test alvorens zij levend gaan. |

1. Selecteer uw type CDN en bijbehorende configuratie door één van het volgende te selecteren:

   | CDN-type | Configuratiedetails |
   | --- | --- |
   | Door Adobe beheerde CDN | Onder **details van de Configuratie**, doe het volgende:<br> a. In de **drop-down van het Domein** lijst, selecteer de domeinnaam die u wilt gebruiken.<br> Geen geverifieerde domeinen beschikbaar in de drop-down lijst? Zie [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen.<br> b. In de **SSL certificaat** drop-down lijst, selecteer een certificaat dat u wilt gebruiken.<br> Geen SSL certificaten beschikbaar in de drop-down lijst? Zie [ een SSL certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) toevoegen. |
   | Andere CDN-provider | Selecteer deze optie als u uw eigen CDN-provider gebruikt en niet de door Adobe beheerde CDN die voor u beschikbaar is.<br> onder **details van de Configuratie**, in de **drop-down lijst van het Domein**, selecteer de domeinnaam die u wilt gebruiken.<br> Geen geverifieerde domeinen beschikbaar in de drop-down lijst? Zie [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen. |

1. Klik **sparen**.

   Adobe raadt u aan de domeintoewijzing te testen.

## De domeintoewijzing testen {#test-domain-mapping}

U kunt verifiëren dat een nieuwe domeinafbeelding op Adobe-Beheerde CDN zonder het wachten op openbare DNS propagatie levend is.

Laad a **krullen** bevel dat DNS resolutie met voeten treedt en richt recht aan de CDN rand:

```bash
curl -svo /dev/null https://www.example.com \
--resolve www.example.com:443:151.101.3.10
```

* Vervang **`www.example.com`** door uw domein.
* Vervang **151.101.3.10** door het Edge IP-adres dat in Cloud Manager wordt weergegeven voor deze toewijzing.

De markering `--resolve` dwingt het verzoek tot gespecificeerde IP en keert succes slechts terug nadat het certificaat en het verpletteren voor uw domein correct zijn geïnstalleerd.

