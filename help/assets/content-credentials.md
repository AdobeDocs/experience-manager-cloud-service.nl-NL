---
title: Content Credentials-integratie
description: Content Credentials, dat in AEM Assets is geïntegreerd en in de Assets View is opgenomen, kan context bieden in de geschiedenis van een middel, zoals hoe het is gemaakt en wie er bij het maken betrokken was. Net als een voedingswaarde-label voor digitale inhoud kan Content Credentials helpen de transparantie te vergroten en vertrouwen te kweken bij het publiek.
role: User
exl-id: 27c25ae0-4477-40c3-85c8-3e0aa725aba7
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Content Credentials {#content-credentials}

Merken maken zich meer dan ooit zorgen over inhoudstransparantie, AI-openbaarmaking en het voorkomen van het knoeien met activa. Content Authenticity Initiative (CAI) bij Adobe bouwt hulpmiddelen volgzaam met de [ Coalitie voor de Technische norm van de Levering van de Inhoud en van de Authenticiteit ](https://c2pa.org/specifications/specifications/1.1/specs/C2PA_Specification.html#_trust_model) (C2PA). Content Credentials, een nieuw type gecodeerde, aanvervalsbare metagegevens, kan de kijkers helpen de inhoud te begrijpen en de integriteit van merkelementen te garanderen. Ze kunnen een groot aantal herkomstgegevens bevatten die insight de geschiedenis van een digitaal middel bieden.

Deze informatie kan omvatten:

* **Uitgever of Ondertekenaar:** Informatie over de entiteit of het bedrijf dat de digitale handtekening uitgeeft om de certificatie of de handtekening van de activa te verklaren.
* **Datum van de Uitgave:** de datum waarop Content Credential op de activa werd toegepast.
* **Krediet en Gebruik:** Informatie over de producent van de activa, met inbegrip van naam, sociale media handvatten, of andere op identiteit betrekking hebbende informatie.
* **Proces:** Verslagen van om het even welke uitgeeft of wijzigingen die aan de activa worden aangebracht.
* **Details van het Apparaat:** Informatie over app of apparaat dat wordt gebruikt om tot de activa te leiden of uit te geven.
* **gebruikte Hulpmiddel AI:** als generatieve AI werd gebruikt om activa uit te geven of tot stand te brengen, kan de naam van het gebruikte model worden omvat.
* **Andere Belangrijke Informatie:** De extra gegevens kunnen ook worden omvat helpen meer context over de geschiedenis van een activa aanbieden.

Voor een volledige mening, [ verifieer ](https://contentcredentials.org/verify) een uitvoerigere insight in activageschiedenis kan aanbieden.

Adobe Experience Manager Assets biedt nu ondersteuning voor Content Credentials, zodat gebruikers Content Credentials rechtstreeks kunnen bekijken in de Assets-weergave van AEM. Wanneer u de elementdetails bekijkt, worden in elke afbeelding met Content Credentials (zoals de afbeeldingen die met GenAI-services zijn gemaakt) de manifeste details weergegeven in een speciaal deelvenster. Als het element wordt gedownload, gepubliceerd of gedeeld, blijft de Content Credentials intact bij het element.

![ activa ](/help/assets/assets/content-credentials.png)

## Toegang tot Content Credentials {#access-content-credentials}

1. Ga naar de Mening UI van Assets, en klik **Assets** van de linkerruit.
1. Navigeer naar een map en selecteer het gewenste element.
1. Klik **Details** en selecteer `Cr pin` van de meest rechtse ruit. Op het tabblad Content Credentials wordt de volgende informatie over het element weergegeven.
   1. **Gegenereerd Beeld:** Datum en tijd waarin Content Credentials werd toegepast.
   1. **Samenvatting van de Inhoud:** wijst erop of de activa gedeeltelijk of volledig door AI worden geproduceerd, of hoe het werd uitgegeven.

      ![ inhoudsgeloofsbrieven ](/help/assets/assets/content-credentials1.png)
   1. **Proces:** Details de toepassing, het apparaat, en het hulpmiddel van AI (zoals Adobe Firefly) dat wordt gebruikt om de activa te produceren, evenals veranderingen die daarna worden aangebracht.

      ![ proces ](/help/assets/assets/CR-Process.png)
   1. **Ongeveer dit Content Credentials:** Naam van de uitgever samen met de datum en de tijd van uitgifte.

      ![ uitgever ](/help/assets/assets/CR-issuer.png)
