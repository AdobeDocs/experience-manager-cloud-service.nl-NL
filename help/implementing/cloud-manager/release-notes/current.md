---
title: Opmerkingen bij de release voor Cloud Manager 2025.6.0
description: Meer informatie over de release van Cloud Manager 2025.6.0 in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 52c8745d3a3cc4bc41003a258a85a817e7ccb48b
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2025.6.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

Meer informatie over de release van Cloud Manager 2025.6.0 in AEM (Adobe Experience Manager) as a Cloud Service.

Zie ook de [ huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service ](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Releasedatums {#release-date}

De releasedatum voor Cloud Manager 2025.6.0 in AEM as a Cloud Service is donderdag 5 juni 2025.

De volgende geplande release is donderdag 10 juli 2025.

## Nieuwe functies {#what-is-new}

* **dashboard van de Vergunning omvat nu de vergunning van Edge Delivery Services**

  Het gebruik van Edge Delivery Services-licenties wordt nu weergegeven op het licentiedashboard, zodat u uw rechten en status duidelijker kunt zien. <!-- CMGR-67686 -->

  ![ Dashboard van de Vergunning ](/help/implementing/cloud-manager/assets/license-dashboard.png)

  Zie [ dashboard van de Vergunning ](/help/implementing/cloud-manager/license-dashboard.md).

* **bijgewerkte de plaatsconfiguratie van Edge Delivery**

  Vereenvoudigde de stroom voor het toevoegen van een plaats van Edge Delivery door om de **Oorsprong van Edge Delivery** in plaats van **Repository URL** te verzoeken, makend aan boord gaan en opstelling sneller en intuïtiever <!-- CMGR-67686 -->

  ![ voeg de dialoogdoos van de plaats van Edge Delivery toe ](/help/implementing/cloud-manager/release-notes/assets/add-edge-delivery-site.png)

  Zie [ een Plaats van Edge Delivery ](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md) toevoegen.

* **de favorieten van de Pijpleiding**

  In deze versie, introduceert Cloud Manager de capaciteit om favoriete pijpleidingen vast te zetten, toestaand u om specifieke pijpleidingen als favorieten te merken zodat verschijnen zij bij de bovenkant van de lijst op de **pagina van de Pijpleidingen**. Deze verbetering maakt vaak betreden pijpleidingen gemakkelijker te vinden en te lopen. <!-- CMGR-68293 -->

  ![ Pijpleidingen duidelijk als favorieten ](/help/implementing/cloud-manager/release-notes/assets/pipeline-favorites.png) *Twee pijpleidingen duidelijk als favorieten.*

  Zie [ pijpleidingsfavorieten van het Teken ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#pipeline-favorites).


## Programma voor vroegtijdige adoptie {#early-adoption}

Neem deel aan het Cloud Manager-programma voor vroege adoptie om exclusieve toegang te krijgen tot de volgende functies voordat ze algemeen worden uitgebracht.

Momenteel zijn de volgende mogelijkheden voor vroege adoptie beschikbaar:


### Speciale testomgeving {#specialized-test-environment}

Cloud Manager steunt nu de toevoeging van een nieuw milieutype genoemd **Gespecialiseerde het Testen Milieu**. De omgeving is ontworpen om teams te helpen functies onder bijna-productieomstandigheden te valideren voordat ze live gaan. Dit omgevingstype is verschillend van *Productie + Stadium*, *Ontwikkeling*, of *Snelle Ontwikkeling* milieu&#39;s en biedt een geconcentreerde ruimte voor het runnen van geavanceerde bevestigingsscenario&#39;s aan.

Zie [ een Gespecialiseerde het Testen Milieu ](/help/implementing/cloud-manager/specialized-test-environment.md) toevoegen.

![ voeg milieu dialoogdoos met Gespecialiseerde het Testen van Milieu geselecteerde radioknoop ](/help/implementing/cloud-manager/release-notes/assets/specialized-test-environment.png) toe

Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ grp-earlyadopter_cs_advtestenvironment@adobe.com ](mailto:grp-earlyadopter_cs_advtestenvironment@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID.


### Kies voor uw eigen git (BYOG) - nu met ondersteuning voor Azure DevOps {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Klanten kunnen nu hun Azure DevOps Git-opslagruimten in Cloud Manager aan boord nemen, met ondersteuning voor zowel moderne Azure DevOps- als oudere VSTS-opslagruimten (Visual Studio Team Services).

* Voor Edge Delivery Services-gebruikers kan de ingebouwde opslagplaats worden gebruikt voor het synchroniseren en implementeren van sitecode.
* Voor AEM as a Cloud Service- en Adobe Managed Services-gebruikers (AMS) kan de opslagplaats worden gekoppeld aan zowel full-stack als frontend pijpleidingen.

De steun voor extra pijpleidingstypes en trekverzoekbevestiging door pijpleidingen van de codekwaliteit komt binnenkort.

Zie [ externe bewaarplaatsen in Cloud Manager ](/help/implementing/cloud-manager/managing-code/external-repositories.md) toevoegen.

![ voeg de dialoogdoos van de Bewaarplaats ](/help/implementing/cloud-manager/release-notes/assets/azure-repo.png) toe

Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ Grp-CloudManager_BYOG@adobe.com ](mailto:grp-cloudmanager_byog@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID. Zorg ervoor dat u ook het Git-platform opgeeft dat u wilt gebruiken en dat u zich in een opslagstructuur van een privéserver, een openbare opslagruimte of een bedrijfsopslagruimte bevindt.


**vaak gestelde vragen over BYOG**

| Vraag | Antwoord |
|---|---|
| *hoe kan een projectschakelaar terug naar de Adobe-Beheerde bewaarplaats van het Git indien nodig?* | Het is eenvoudig om terug te schakelen. [ werk de pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) bij om aan de bewaarplaats van Adobe te richten en de externe bewaarplaats te verwijderen als het niet meer vereist is. |
| *is het mogelijk om verschillende bewaarplaatsen voor verschillende milieu&#39;s (bijvoorbeeld, niet-productie tegenover productie) te vormen om het testen in niet productie eerst toe te staan?* | Ja, verschillende opslagruimten kunnen worden geconfigureerd voor afzonderlijke omgevingen. De ontwikkelings- of codekwaliteitspijplijn kan bijvoorbeeld naar een externe opslagplaats verwijzen terwijl de productiepijplijn verbonden blijft met de Adobe-opslagplaats. Zorg ervoor dat de synchronisatietaak tussen de twee opslagruimten actief blijft tijdens deze configuratie. |
| *blijven de bestaande montages zoals IP lijsten van gewenste personen werken?* | Ja, blijven de bestaande IP lijsten van gewenste personen zoals gebruikelijk werken. Nochtans, als de externe bewaarplaats van het Git door een firewall wordt beschermd, moeten de noodzakelijke [ adressen van Adobe IP aan de lijst van gewenste personen ](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) worden toegevoegd. |
| *Werken al bewaarplaats GitLab URLs? De repository URL in gebruik volgt de notatie `https://gitlab_dedicated_url.com/path/repo-name.git` , die afwijkt van het voorbeeld in de documentatie.* | Ja, om het even welke bewaarplaats GitLab die API V3 of V4 steunt wordt gesteund, met inbegrip van zelf-ontvangen GitLab URLs als die in [ wordt beschreven voeg externe bewaarplaatsen in Cloud Manager ](/help/implementing/cloud-manager/managing-code/external-repositories.md) toe (`https://git-vendor-name.com/org-name/repo-name.git`). |


#### Toegangstokens beheren{#manage-access-tokens}

Het gebruik **beheert de Tokens van de Toegang** in Cloud Manager aan mening, hernoemt, en schrapt toegangstokens verbonden aan externe bewaarplaatsen BYOG, zoals Onderneming GitHub, GitLab, Bitbucket, en Azure DevOps.

Zie [ de Tokens van de Toegang beheren ](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md).

Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ Grp-CloudManager_BYOG@adobe.com ](mailto:grp-cloudmanager_byog@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID.


### Edge Delivery Config Pipet toevoegen {#add-eds-pipeline}

Config Pipelines worden nu ondersteund voor sites die met Edge Delivery Services zijn gebouwd en deze mogelijkheid uitbreiden tot buiten de Cloud Service-omgevingen. U kunt **Pijpleidingen Config** gebruiken om montages zoals verkeer het filtreren regels en configuraties van de Firewall van de Toepassing van het Web (WAF) te beheren, waar toepasselijk. Zie [ Ondersteunde Configuraties ](/help/operations/config-pipeline.md#configurations).

![ voeg de pijpleiding van Edge Delivery in Add drop-down lijst van de Pijpleiding ](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add.png) toe *toevoegend een pijpleiding van Edge Delivery van de **pagina van het Overzicht van het Programma**,**Pipelines**kaart.*

![ voeg de pijpleidingsdialoogdoos van Edge Delivery toe ](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add-dialogbox.png) *voeg de pijpleidingsdialoogdoos van Edge Delivery toe.*

Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ grp-aemeds-config-pipeline-adopter@adobe.com ](mailto:grp-aemeds-config-pipeline-adopter@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID.


## Bugfixes

* Sandbox-omgevingen die eerder als `HIBERNATED` waren gemarkeerd, blijven niet meer vastzitten in die status, waardoor de uitvoering of implementatie van de pijpleiding kan worden voortgezet zoals verwacht. <!-- CMGR-67705 -->
* AEM Cloud Manager wijst nu correct Maven bouwstijlmislukkingen in kaart die door 409 fouten (conflicten) worden veroorzaakt wanneer het halen van klantartefacten aan een klant-veroorzaakt mislukking. Deze verandering verbetert foutenoverseinen door tussen interne fouten en kwesties met betrekking tot de opstelling van het klantenmilieu te onderscheiden. <!-- CMGR-66673 -->


<!-- ## Known issues {#known-issues} -->

