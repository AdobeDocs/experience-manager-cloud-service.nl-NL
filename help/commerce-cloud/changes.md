---
title: Opvallende wijzigingen in de CIF
description: Opvallende wijzigingen van het Commerce integration framework (CIF) in vergelijking met oudere CIF.
exl-id: 5a526960-96a1-421e-9fb0-0825e7df8f32
feature: Commerce Integration Framework
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# Notable Veranderingen in het Commerce integration framework (CIF) toe:voegen{#notable-changes}

Adobe Experience Manager as a Cloud Service biedt veel nieuwe functies en mogelijkheden om uw AEM Projecten te beheren. Om meer over deze mogelijkheden te leren, volg de verbinding voor [ veranderingen in Experience Manager as a Cloud Service ](/help/release-notes/aem-cloud-changes.md).

Dit document benadrukt de belangrijke verschillen tussen de Commerce integration framework (CIF) toe:voegen-op en oude CIF versies, die als CIF Klassiek (QuickStart) en CIF open-source worden bekend.

## Installatie en updates

De AEM CIF-invoegtoepassing wordt geïnstalleerd via Cloud Manager. Voor de installatie is een CIF krediet vereist, behalve voor sandboxen waarin CIF zonder credits kunnen worden geïnstalleerd. Credits worden automatisch ontvangen via de levering van de CIF add-on in uw AEM contract.

De invoegtoepassing wordt automatisch bijgewerkt als onderdeel van de normale AEM as a Cloud Service-update.

**Vorige CIF versies**

* CIF Klassiek: Geen installatie nodig, CIF maakte deel uit van de QuickStart. CIF updates maakten deel uit van regelmatige AEM- of servicepack-updates
* CIF open-source voor AEM op-premissen: Installatie via GitHub. Updates maakten deel uit van handmatige update-/onderhoudswerkzaamheden.
* CIF Open-source voor AEM Adobe Managed Services: Installatie via het accountteam van de Adobe. Updates maakten deel uit van handmatige update-/onderhoudswerkzaamheden.

## Eindpuntconfiguratie

Het eindpunt wordt gevormd en bijgewerkt of via Cloud Manager UI of zijn CLI.

**Vorige CIF versies**

* CIF Klassiek: Via OSGi configuratie in AEM
* CIF Open-source: via CIF Configuration Browser

## Invoering van CIF Venia-project

Project beschikbaar in [ de Bewaarplaats van het Git van Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/integrating-with-git.html?lang=nl-NL) en plaatsing die via [ Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=nl-NL) wordt gedaan

**Vorige CIF versies**

* CIF Classic: als AEM pakket installeren
* CIF Open-source: Via [ Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html?lang=nl-NL)

## Productcatalogusgegevens

De catalogusgegevens van het product worden gevraagd op bestelling via vraag in real time aan een extern eindpunt dat vereiste GraphQL APIs steunt. Deze API&#39;s ondersteunen toegang tot live- of gefaseerde gegevens op een bepaalde datum. Geen replicatie nodig.

**Vorige CIF versies**

* CIF Klassiek: live en gefaseerde productgegevens worden geïmporteerd en in de JCR gecontinueerd op AEM auteur via volledige of delta productimport. Live productgegevens worden gerepliceerd naar AEM Publish.

## De catalogus van het product ervaart met AEM teruggeven

AEM geeft de ervaringen van de productcatalogus direct weer met behulp van AEM catalogussjablonen die zijn toegewezen aan producten en categorieën. Geen replicatie nodig.

**Vorige CIF versies**

* CIF Klassiek: AEM auteur maakt een AEM pagina voor elke categorie/elk product met het gereedschap Catalogusblauwdruk. Deze pagina&#39;s worden gerepliceerd naar AEM Publish.

>[!NOTE]
>
>Voor extra documentatie op hoe te om CIF met AEM Beheerde Dienst of AEM te gebruiken On-premise, zie [ Commerce integration framework ](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html)
