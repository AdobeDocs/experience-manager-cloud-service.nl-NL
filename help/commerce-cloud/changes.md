---
title: Opvallende wijzigingen van de add-on van het kader voor de integratie van de handel (CIF)
description: Opvallende veranderingen van het Kader voor de Integratie van de Handel (CIF) in vergelijking met de oude CIF-versies.
exl-id: 5a526960-96a1-421e-9fb0-0825e7df8f32
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# Opvallende veranderingen in de toe:voegen-on van het Kader van de Integratie van de Handel (CIF){#notable-changes}

Adobe Experience Manager as a Cloud Service biedt veel nieuwe functies en mogelijkheden om uw AEM projecten te beheren. Als u meer wilt weten over deze mogelijkheden, volgt u de koppeling voor [wijzigingen in as a Cloud Service Experience Manager](/help/release-notes/aem-cloud-changes.md).

In dit document worden de belangrijke verschillen tussen de add-on en oude CIF-versies van het kader voor de integratie van de handel (Commerce Integration Framework, CIF) belicht, die voornamelijk CIF Classic (Quickstart) en CIF Open-source worden genoemd.

## Installatie en updates

De AEM CIF-invoegtoepassing wordt geïnstalleerd via Cloud Manager. Voor de installatie is een CIF-krediet vereist, behalve voor sandboxen waarin CIF zonder credits kan worden geïnstalleerd. Kredieten worden automatisch ontvangen via de levering van de CIF-invoegtoepassing in uw AEM.

De invoegtoepassing wordt automatisch bijgewerkt als onderdeel van de normale AEM as a Cloud Service updates.

**Vorige CIF-versies**

* Klassiek CIF: Geen installatie nodig, CIF maakte deel uit van QuickStart. De updates van CIF maakten deel uit van regelmatige AEM of de updates van het de dienstpak
* CIF Open-source voor AEM op locatie: Installatie via GitHub. Updates maakten deel uit van handmatige update-/onderhoudswerkzaamheden.
* CIF Open-source voor AEM door Adobe beheerde services: Installatie via Customer Success Manager. Updates maakten deel uit van handmatige update-/onderhoudswerkzaamheden.

## Eindpuntconfiguratie

Het eindpunt wordt gevormd en bijgewerkt of via de UI van de Manager van de Wolk of zijn CLI.

**Vorige CIF-versies**

* Klassiek CIF: Via OSGi-configuratie in AEM
* CIF Open-source: Via CIF Configuration Browser

## Plaatsing van het CIF-project van Venia

Project beschikbaar in [Opslagplaats voor wolkenbeheer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html) en implementatie via [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html)

**Vorige CIF-versies**

* Klassiek CIF: Via AEM
* CIF Open-source: Via [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)

## Productcatalogusgegevens

De catalogusgegevens van het product worden gevraagd op bestelling via vraag in real time aan een extern eindpunt dat vereiste GraphQL APIs steunt. Deze API&#39;s ondersteunen toegang tot live- of gefaseerde gegevens op een bepaalde datum. Geen replicatie nodig.

**Vorige CIF-versies**

* Klassiek CIF: Live en gefaseerde productgegevens worden geïmporteerd en in de JCR voortgezet op AEM Author via volledige of delta productimport. Live-productgegevens worden gerepliceerd naar AEM Publish.

## De catalogus van het product ervaart met AEM teruggeven

AEM geeft de ervaringen van de productcatalogus direct weer met behulp van AEM catalogussjablonen die zijn toegewezen aan producten en categorieën. Geen replicatie nodig.

**Vorige CIF-versies**

* Klassiek CIF: AEM-auteur maakt een AEM pagina voor elke categorie/elk product met het gereedschap Catalogusblauwdruk. Deze pagina&#39;s worden gerepliceerd naar AEM Publish.

>[!NOTE]
>
>Voor extra documentatie over hoe te om CIF met AEM Beheerde Dienst of AEM On-premisse te gebruiken, verwijs naar [Kader voor integratie in de handel](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html)
