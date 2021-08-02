---
title: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2021.5.0
description: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2021.5.0
feature: Geen informatie
exl-id: 42cc9cab-6e66-4976-a3b1-ecb9dbaaabf4
source-git-commit: d7d138c7442ee8bee7a1ad69144b26d74d364eee
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager als Cloud Service 2021.6.0 {#release-notes}

Deze pagina bevat de releaseopmerkingen voor Cloud Manager in AEM als Cloud Service 2021.6.0.

>[!NOTE]
>Om de huidige Nota&#39;s van de Versie voor Adobe Experience Manager als Cloud Service te zien, klik [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2021.6.0 is 10 juni 2021.

### Wat is er nieuw? {#what-is-new}

* De Voorproefdienst zal op rolbasis aan alle Programma&#39;s worden opgesteld. Klanten worden in-product op de hoogte gesteld wanneer hun programma is ingeschakeld voor de Voorvertoningsservice. Raadpleeg [Toegang tot voorvertoningsservice](/help/implementing/cloud-manager/manage-environments.md#access-preview-service) voor meer informatie.

* Geweven Gedeelten die tijdens de bouwstijlstap worden gedownload zullen nu in het voorgeheugen ondergebracht tussen pijpleidinguitvoeringen worden. Deze functie wordt de komende weken ingeschakeld voor klanten.

* De naam van het programma kan nu worden bewerkt in het dialoogvenster Programma bewerken.

* De standaardtaknaam die tijdens zowel project verwezenlijking als in het gebrek wordt gebruikt duw bevel via beheert git werkschema is veranderd in `main`.

* De ervaring met het bewerken van programma&#39;s in de gebruikersinterface is vernieuwd.

* De kwaliteitsregel `ImmutableMutableMixCheck` is bijgewerkt om `/oak:index` knopen als onveranderlijk te classificeren.

* De kwaliteitsregels `CQBP-84` en `CQBP-84--dependencies` zijn geconsolideerd in één enkele regel. Als onderdeel van deze consolidatie, identificeert het aftasten van gebiedsdelen nauwkeuriger kwesties in derdegebiedsdelen die aan AEM runtime worden opgesteld.

* Om verwarring te voorkomen, zijn de segmentrijen van de AEM Publish en Publish Dispatcher op de pagina van de Details van het Milieu geconsolideerd.

   ![](/help/implementing/cloud-manager/release-notes-cloud-manager/assets/aem-dispatcher.png)

* Er is een nieuwe code kwaliteitsregel toegevoegd om de structuur van `damAssetLucene` indexen te valideren. Raadpleeg [Custom DAM Asset Lucene Oak Indexes](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-damAssetLucene-sanity-check) voor meer informatie.

* De pagina met omgevingsdetails geeft nu meerdere domeinnamen weer voor de services Publiceren en Voorvertonen (al naargelang van toepassing). Raadpleeg [Omgevingsdetails](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=en#viewing-environment) voor meer informatie.

### Opgeloste problemen {#bug-fixes}

* JCR-knooppuntdefinities die een nieuwe regel bevatten nadat de naam van het hoofdelement niet correct is geparseerd.

* De API voor opslagplaatsen weergeven filtert geen verwijderde opslagplaatsen.

* Er is een onjuist foutbericht weergegeven wanneer een ongeldige waarde voor de planningsstap is opgegeven.

* Soms kan de gebruiker een groene *actieve* status naast een IP Lijst van gewenste personen zien zelfs wanneer die configuratie niet werd opgesteld.

* Sommige programma&#39;s die opeenvolgingen uitgeven zouden in de onmogelijkheid kunnen resulteren om de productiepijplijn tot stand te brengen of uit te geven.

* Sommige programma&#39;s die opeenvolgingen uitgeven zouden in **Overzicht** pagina kunnen resulteren die een misleidend bericht toont om programma opstelling opnieuw uit te voeren.
