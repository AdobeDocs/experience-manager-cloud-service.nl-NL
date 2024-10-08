---
title: Integratie van content credentials
description: Content credentials, die in AEM Assets zijn geïntegreerd en in de Assets View zijn opgenomen, kunnen context bieden in de geschiedenis van een middel, zoals hoe het is gemaakt en wie er bij het maken betrokken was. Net als een voedingswaarde-label voor digitale inhoud kunnen Content credentials de transparantie vergroten en vertrouwen opbouwen met het publiek.
role: User
exl-id: 27c25ae0-4477-40c3-85c8-3e0aa725aba7
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# Content credentials {#content-credentials}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Merken maken zich meer dan ooit zorgen over inhoudstransparantie, AI-openbaarmaking en het voorkomen van het knoeien met activa. Het Initiatief van de Authenticiteit van de Inhoud (CAI) bij Adobe bouwt hulpmiddelen volgzaam met de [ Coalitie voor de Technische norm van de Levering van de Inhoud en van Authenticiteit ](https://c2pa.org/specifications/specifications/1.1/specs/C2PA_Specification.html#_trust_model) (C2PA). Content credentials, die een nieuw soort gecodeerde, onvervalsbare metagegevens zijn, kunnen gebruikers helpen de inhoud te begrijpen en de integriteit van merkelementen te garanderen. Ze kunnen een breed scala aan herkomstgegevens bevatten die inzicht bieden in de geschiedenis van een digitaal middel.

Deze informatie kan omvatten:

* **Uitgever of Ondertekenaar:** Informatie over de entiteit of het bedrijf dat de digitale handtekening uitgeeft om de certificatie of de handtekening van de activa te verklaren.
* **Datum van de Uitgave:** de datum waarop Content Credential op de activa werd toegepast.
* **Krediet en Gebruik:** Informatie over de producent van de activa, met inbegrip van naam, sociale media handvatten, of andere op identiteit betrekking hebbende informatie.
* **Proces:** Verslagen van om het even welke uitgeeft of wijzigingen die aan de activa worden aangebracht.
* **Details van het Apparaat:** Informatie over app of apparaat dat wordt gebruikt om tot de activa te leiden of uit te geven.
* **gebruikte Hulpmiddel AI:** als generatieve AI werd gebruikt om activa uit te geven of tot stand te brengen, kan de naam van het gebruikte model worden omvat.
* **Andere Belangrijke Informatie:** De extra gegevens kunnen ook worden omvat helpen meer context over de geschiedenis van een activa aanbieden.

Voor een volledige mening, [ verifieer ](https://contentcredentials.org/verify) een uitvoeriger inzicht in activageschiedenis kan aanbieden.

Adobe Experience Manager Assets biedt nu ondersteuning voor Content credentials, zodat gebruikers Content credentials rechtstreeks kunnen zien in de Assets-weergave van AEM. Wanneer u de elementdetails bekijkt, worden in elke afbeelding met Content credentials (zoals de afbeeldingen die met GenAI-services zijn gemaakt) de manifeste details weergegeven in een speciaal deelvenster. Als het element wordt gedownload, gepubliceerd of gedeeld, blijven de Content credentials intact met het element.

![ activa ](/help/assets/assets/content-credentials.png)

## Toegang tot Content credentials {#access-content-credentials}

1. Ga naar de Mening UI van Assets, en klik **Assets** van de linkerruit.
1. Navigeer naar een map en selecteer het gewenste element.
1. Klik **Details** en selecteer `Cr pin` van de meest rechtse ruit. Op het tabblad Content credentials wordt de volgende informatie over het element weergegeven.
   1. **Gegenereerd Beeld:** Datum en tijd waarin de Content credentials werden toegepast.
   1. **Samenvatting van de Inhoud:** wijst erop of de activa gedeeltelijk of volledig door AI worden geproduceerd, of hoe het werd uitgegeven.
      ![ content credentials ](/help/assets/assets/content-credentials1.png)
   1. **Proces:** Details de toepassing, het apparaat, en het hulpmiddel van AI (zoals Adobe Firefly) dat wordt gebruikt om de activa te produceren, evenals veranderingen die daarna worden aangebracht.
      ![ proces ](/help/assets/assets/CR-Process.png)
   1. **Ongeveer deze Content credentials:** Naam van de uitgever samen met de datum en de tijd van uitgifte.
      ![ uitgever ](/help/assets/assets/CR-issuer.png)
