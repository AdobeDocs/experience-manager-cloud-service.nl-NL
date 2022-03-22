---
title: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.6.0
description: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.5.0
feature: Release Information
exl-id: 9a0a53d3-31d4-493d-ba2e-b4bb22f60351
source-git-commit: 4b76fbbb1b58324065b39d6928027759b0897246
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.6.0 {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.6.0.

>[!NOTE]
>Klik op [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.6.0 is 10 juni 2021.

### Wat is er nieuw? {#what-is-new}

* De Voorproefdienst zal op rolbasis aan alle Programma&#39;s worden opgesteld. Klanten worden in-product op de hoogte gesteld wanneer hun programma is ingeschakeld voor de Voorvertoningsservice. Zie [Voorvertoningsservice openen](/help/implementing/cloud-manager/manage-environments.md#access-preview-service) voor meer informatie .

* Geweven Gedeelten die tijdens de bouwstijlstap worden gedownload zullen nu in het voorgeheugen ondergebracht tussen pijpleidinguitvoeringen worden. Deze functie wordt de komende weken ingeschakeld voor klanten.

* De naam van het programma kan nu worden bewerkt in het dialoogvenster Programma bewerken.

* De standaardvertakkingsnaam die tijdens zowel de projectverwezenlijking als in het gebrek wordt gebruikt duw bevel via beheert de werkschema&#39;s van de it is veranderd in `main`.

* De ervaring met het bewerken van programma&#39;s in de gebruikersinterface is vernieuwd.

* De kwaliteitsregel `ImmutableMutableMixCheck` is bijgewerkt om te classificeren `/oak:index` knooppunten als onveranderlijk.

* De kwaliteitsregels `CQBP-84` en `CQBP-84--dependencies` zijn in één regel geconsolideerd. Als onderdeel van deze consolidatie, identificeert het aftasten van gebiedsdelen nauwkeuriger kwesties in derdegebiedsdelen die aan AEM runtime worden opgesteld.

* Om verwarring te voorkomen, zijn de segmentrijen van de AEM Publish en Publish Dispatcher op de pagina van de Details van het Milieu geconsolideerd.

   ![](/help/implementing/cloud-manager/release-notes-cloud-manager/assets/aem-dispatcher.png)

* Er is een nieuwe regel voor de kwaliteit van de code toegevoegd om de structuur van `damAssetLucene` indexen. Zie [Aangepaste DAM-indexen voor luyleen](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-damAssetLucene-sanity-check) voor meer informatie .

* De pagina met omgevingsdetails geeft nu meerdere domeinnamen weer voor de services Publiceren en Voorvertonen (al naargelang van toepassing). Zie [Omgevingsdetails](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=en#viewing-environment) voor meer informatie.

### Opgeloste problemen {#bug-fixes}

* JCR-knooppuntdefinities die een nieuwe regel bevatten nadat de naam van het hoofdelement niet correct is geparseerd.

* De API voor opslagplaatsen weergeven filtert geen verwijderde opslagplaatsen.

* Er is een onjuist foutbericht weergegeven wanneer een ongeldige waarde voor de planningsstap is opgegeven.

* De gebruiker kan soms een groen zien *actief* status naast een IP Lijst van gewenste personen zelfs toen die configuratie niet werd opgesteld.

* Sommige programma&#39;s die opeenvolgingen uitgeven zouden in de onmogelijkheid kunnen resulteren om de productiepijplijn tot stand te brengen of uit te geven.

* Sommige bewerkingsreeksen van programma&#39;s kunnen resulteren in de **Overzicht** pagina met een misleidend bericht om de programma-instelling opnieuw uit te voeren.
