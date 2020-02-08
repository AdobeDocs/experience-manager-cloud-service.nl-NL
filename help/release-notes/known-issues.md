---
title: Bekende problemen
description: Opmerkingen vrij die specifiek zijn voor de bekende problemen met Adobe Experience Manager als Cloud Service
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# Bekende problemen {#known-issues}

In dit artikel worden de bekende problemen van Adobe Experience Manager weergegeven als een Cloud Service-aanbieding. De lijst wordt herzien en bijgewerkt met elke ononderbroken versie van de Manager van de Ervaring.

[Neem contact op met de ondersteuning](https://helpx.adobe.com/support/experience-manager.html) voor meer informatie over de bekende problemen.

<!-- 
## Platform {#platform}

## Sites {#sites}
-->

## Activa {#assets}

<!-- Jira label: assets-cloud-known-issues -->

Enkele bekende problemen zijn:

* **Metagegevensschema**: De widget voor het beoordelen van bedrijfsmiddelen kan een JSP-compilatiefout veroorzaken. U kunt dit oplossen door de component voor de classificatie van elementen uit het metagegevensschema te verwijderen. <!-- CQ-4282865 -->

Enkele beperkingen van de functionaliteit Elementen zijn:

* Met AEM Assets als Cloud Service werkt de functionaliteit Connected Assets wanneer AEM 6.5-sites worden geïmplementeerd op AMS.

### Mogelijkheden voor toekomstige middelen {#upcoming-assets-capabilities}

Enkele mogelijkheden van Adobe Experience Manager-middelen die afhankelijk zijn van de funderingsmogelijkheden, die nog niet beschikbaar zijn in de Experience Manager als implementatiearchitectuur voor de cloudservice, zullen naar verwachting later worden ingeschakeld:

* Publiceren naar Brand Portal is momenteel niet ingeschakeld. U kunt de implementatie van Commons [voor het delen van](https://adobe-marketing-cloud.github.io/asset-share-commons/) bedrijfsmiddelen uitbreiden en implementeren voor het gebruik van gevallen voor het distribueren van bedrijfsmiddelen.
* De verbeterde functionaliteit voor slimme tags die gebruikmaakt van AI-services van Adobe I/O is momenteel niet beschikbaar.
* Capabilities not enabled in this stage due to dependency on Commerce Integration Framework APIs:
   * Workflowmodellen voor foto&#39;s.
   * Tabblad met productinformatie in de gebruikersinterface voor eigenschappen van elementen is niet ingevuld.
* Mogelijkheden die op dit moment niet zijn ingeschakeld, zijn afhankelijk van de integratie met InDesign Server:
   * Asset Templates en Asset Catalogs.
   * Voorvertoning van InDesign-bestanden op meerdere pagina&#39;s.

>[!MORELIKETHIS]
>
>* [Belangrijke wijzigingen in AEM](aem-cloud-changes.md)
>* [Verouderde en verwijderde functies](deprecated-removed-features.md)
>* [Opmerkingen bij de release](home.md)

