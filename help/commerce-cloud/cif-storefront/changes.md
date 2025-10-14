---
title: Opvallende wijzigingen in de invoegtoepassing Commerce integration framework (CIF)
description: Opvallende wijzigingen in de Commerce integration framework (CIF) ten opzichte van de oude CIF-versies.
exl-id: 5a526960-96a1-421e-9fb0-0825e7df8f32
feature: Commerce Integration Framework
role: Admin
source-git-commit: 856442039fcd25ec675a6258d182f7a35f590c3c
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# Opvallende wijzigingen in de invoegtoepassing Commerce integration framework (CIF) {#notable-changes}

Adobe Experience Manager as a Cloud Service biedt veel nieuwe functies en mogelijkheden om uw AEM-projecten te beheren. Om meer over deze mogelijkheden te leren, volg de verbinding voor [&#x200B; veranderingen in Experience Manager as a Cloud Service.](/help/release-notes/aem-cloud-changes.md)

In dit document worden de belangrijke verschillen tussen de Commerce integration framework (CIF) add-on en de oude CIF-versies, ook wel CIF Classic (Quickstart) en CIF Open-source genoemd, benadrukt.

## Installatie en updates

De invoegtoepassing AEM CIF wordt geïnstalleerd via Cloud Manager. Voor de installatie is een CIF-krediet vereist, behalve voor sandboxen waarin CIF zonder credits kan worden geïnstalleerd. Credits worden automatisch ontvangen via de levering van de invoegtoepassing CIF in uw AEM-contract.

De invoegtoepassing wordt automatisch bijgewerkt als onderdeel van de normale AEM as a Cloud Service-update.

### Vorige CIF-versies {#previous-versions-installation}

* CIF Classic: Geen installatie nodig, CIF was onderdeel van de Quickstart. CIF-updates maakten deel uit van reguliere AEM- of servicepack-updates
* CIF Open-source voor AEM On-premiss: installatie via GitHub. Updates maakten deel uit van handmatige update-/onderhoudswerkzaamheden.
* CIF Open-source voor AEM Adobe Managed Services: installatie via het Adobe-accountteam. Updates maakten deel uit van handmatige update-/onderhoudswerkzaamheden.

## Eindpuntconfiguratie {#endpoint-configuration}

Het eindpunt wordt gevormd en bijgewerkt of via Cloud Manager UI of zijn CLI.

### Vorige CIF-versies {#previous-versions-endpoint}

* CIF Classic: Via OSGi-configuratie in AEM
* CIF Open-source: Via CIF Configuration Browser

## Invoering van het CIF-project van Venia {#venia-project}

Project beschikbaar in [&#x200B; de Bewaarplaats van de Bewaarplaats van de Bezit van Cloud Manager &#x200B;](/help/implementing/cloud-manager/managing-code/integrating-with-git.md) en plaatsing die via [&#x200B; Cloud Manager wordt gedaan.](/help/implementing/deploying/overview.md)

### Vorige CIF-versies {#previous-versions-venia}

* CIF Classic: via AEM-pakket installeren
* CIF open-source: Via [&#x200B; Cloud Manager &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html?lang=nl-NL)

## Productcatalogusgegevens {#product-catalog-data}

De catalogusgegevens van het product worden gevraagd op bestelling via vraag in real time aan een extern eindpunt dat vereiste GraphQL APIs steunt. Deze API&#39;s ondersteunen toegang tot live- of gefaseerde gegevens op een bepaalde datum. Geen replicatie nodig.

### Vorige CIF-versies {#previous-versions-catalog}

* CIF Classic: live en gefaseerde productgegevens worden geïmporteerd in en voortgezet in JCR op AEM Author via volledige of delta productimport. Live-productgegevens worden gerepliceerd naar AEM Publish.

## Ervaringen met productcatalogus met AEM-rendering {#catalog-experiences}

AEM geeft de ervaringen met productcatalogi direct weer met AEM-catalogussjablonen die zijn toegewezen aan producten en categorieën. Geen replicatie nodig.

### Vorige CIF-versies {#previous-cif-versions}

* CIF Classic: AEM Author maakt een AEM-pagina voor elke categorie/elk product met het gereedschap Catalogusblauwdruk. Deze pagina&#39;s worden gerepliceerd naar AEM Publish.

>[!NOTE]
>
>Voor extra documentatie op hoe te om CIF met AEM te gebruiken Beheerde Dienst of AEM op-gebouw, zie [&#x200B; Commerce integration framework.](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html)
