---
title: AEM - Veelgestelde vragen over integratie van de handel met behulp van het kader voor integratie van de handel
description: AEM - Veelgestelde vragen over integratie van de handel met behulp van het kader voor integratie van de handel
translation-type: tm+mt
source-git-commit: ad831b2cc3657666678662eeff0eaf371ce4da49
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 0%

---


# AEM - Veelgestelde vragen over integratie van de handel met behulp van het kader voor integratie van de handel


## 1. Wordt CIF GraphQL slechts gebruikt voor handel of zal dit voor het vragen van inhoud beschikbaar zijn authored op AEM JCR?

Adobe heeft de GraphQL APIs van Magento als zijn officiële handel API voor alle handel verwante gegevens goedgekeurd. Daarom gebruikt AEM GraphQL om handelsgegevens met Magento en met om het even welke handelingsmotor via I/O Runtime uit te wisselen. Deze GraphQL API is onafhankelijk van AEM GraphQL API om tot Inhoudsfragmenten toegang te hebben.

## 2. Hoe komt Adobe I/O in het spel? Spreekt AEM rechtstreeks met Magento?

AEM kan rechtstreeks verbinding maken met Magento zonder I/O-runtimelaag. Als er behoefte is om een niet-Magento handel achterkant (derdeoplossing) met AEM te integreren, kan I/O Runtime platform worden gebruikt om de mappingslaag te ontvangen om Magento GraphQL APIs met om het even welke derde oplossingen APIs te verbinden. Raadpleeg voor meer informatie hierover deze [referentie-implementatie](https://github.com/adobe/commerce-cif-graphql-integration-reference). Voor oplossingen niet-Magento, zou AEM worden gevormd om aan het I/O Runtime eindpunt te richten.

Het I/O Runtime platform kan ook worden gebruikt om handelsdiensten uit te breiden of aan te passen. Voor dit gebruik-gevallen zou u het I/O Runtime eindpunt roepen dat dan een aangepaste implementatie van de respectieve dienst zal ontvangen. Gebruiksscenario&#39;s voor integratie en extensie kunnen worden gecombineerd.

## 3. Kunnen de activa van het Product (beelden) van AEM via Magento worden opgeslagen en van verwijzingen voorzien admin? Hoe kunnen activa van Dynamic Media worden verbruikt?

Er is momenteel geen AEM Assets - Magento-integratie. Als tussenoplossing kunt u productelementen (afbeeldingen) opslaan in AEM Assets, maar u moet de URL&#39;s van de elementen handmatig opslaan in Magento. Dynamic Media maakt nu deel uit van AEM Assets en zal op dezelfde manier werken.

## 4. Maakt het uit waar de handelsoplossing wordt ingezet? (Op prem of in de cloud)

Het maakt niet uit waar uw handelsoplossing wordt opgesteld. De integratie en het nieuwe AEM Venia-winkelfront werken ongeacht het implementatiemodel. Nochtans, als het op de goedgekeurde E2E verwijzingsarchitectuur wordt opgesteld, zullen E2E tests tegen prestaties KPIs worden in werking gesteld die werden verzameld die het profiel van een ondernemingsklant vertegenwoordigen. Dit zal u van extra informatie voorzien die u als benchmark kunt gebruiken.

## 5. Hoe worden cataloguspagina&#39;s of productpagina&#39;s in AEM gemaakt? Hoe blijven ze in AEM?

Cataloguspagina&#39;s en productpagina&#39;s worden dynamisch gemaakt en in het cachegeheugen opgeslagen in AEM op basis van algemene catalogussjablonen en productpaginasjablonen. Er worden geen product- of catalogusgegevens geïmporteerd en opgeslagen in AEM.

## 6. Wanneer u productgegevens in uw handelsoplossing bijwerkt, is dat een duw in real time aan AEM? Of is het een batchproces?

CIF toe:voegen-op gebruikt met AEM Cloud Service laat gegevens toe om van de handelsoplossing aan AEM op bestelling te stromen. Daarom is dit geen real-time duw of een partijproces wanneer er een update in uw handelsoplossing is.

## 7. Welke catalogusgrootte AEM CIF-ondersteuning?

Dit hangt af van een paar extra aspecten die u in overweging moet nemen. Wat is de cacheverhouding van uw catalogusgegevens en -pagina&#39;s? Hoeveel gezamenlijke verzoeken verwacht u tijdens piekuren? Hoe schaalbaar zijn de API&#39;s van uw handelsoplossingen?

## 8. Hoe speelt PIM in dit kader?

PIM-gegevens worden via GraphQL-verzoeken aan AEM en clients beschikbaar gesteld. Onze aanbeveling is om PIM te integreren met de motor van de handel (Magento of anderen) zodat PIM gegevens dan van de handelsinrichting kunnen worden teruggewonnen.

## 9. Verzendt u ook de prijzen en andere gegevens in cache via Dispatcher. Vormt dat een veelvuldige uitdaging voor het ongeldig maken van cache?

Dynamische gegevens zoals prijs of voorraad worden niet in de cache opgeslagen op de Dispatcher. Dynamische gegevens worden via GraphQL API&#39;s direct opgehaald aan de clientzijde met webcomponenten. Alleen statische gegevens (zoals product- of categoriegegevens) worden in cache geplaatst op de Dispatcher. Als de productgegevens veranderen, zal er een behoefte aan geheim voorgeheugenbevestiging zijn.

## 10 Hoe werkt cachevervalsing voor AEM Dispatcher met AEM en handel?

We raden u aan op TTL gebaseerde cachevalidatie in te stellen voor pagina&#39;s die in cache zijn geplaatst op de Dispatcher. Voor dynamische informatie zoals prijs of voorraad raden we aan de datumclient-kant weer te geven. Raadpleeg [AEM Dispatcher](https://helpx.adobe.com/experience-manager/kb/optimizing-the-dispatcher-cache.html) voor meer informatie over op TTL gebaseerde cachedetectie

## 11. Bestaat er een aanbeveling voor een uniforme zoekopdracht in AEM inhoud met Commerce?

Een verwijzingsimplementatie van het productonderzoek wordt verstrekt maar geen verenigd onderzoek met inhoud. Deze eigenschap is gewoonlijk zeer klantspecifiek en beter opgelost op een project-specifiek niveau.

## 12. Hoe werkt Search met AEM en handel die CIF gebruiken?

CIF verstrekt de bar van het Onderzoek en de componenten van het Resultaat van het Onderzoek. De component van de bar van het Onderzoek verzendt een verzoek GraphQL met de onderzoekstermijn naar de handeloplossing die dan een productlijst terugkeert die productnaam, prijs, SLUG, enz. omvat. De component van het Resultaat van het Onderzoek toont dan de onderzoeksresultaten in een galeriemening op een pagina van het onderzoeksresultaat die in AEM wordt gecreeerd. De zoekfunctie ondersteunt standaard zoeken in volledige tekst. Wij gebruiken de sleutel SLUG/url om een verwijzing naar PDP te bouwen.

## 13. Hoe kunnen productgegevens in MSM of vertalingen worden gebruikt?

Productgegevens worden meestal al vertaald in PIM of in Magento. De integratie AEM - Magento ondersteunt de verbinding met meerdere Magento-winkels en -winkelweergaven. In een MSM-instelling wordt doorgaans één AEM site gekoppeld aan één Magento-winkelweergave.

## 14. Hoe werkt CIF met niet-Magento handelsplatforms?

De integratie met derdeoplossingen zoals andere handelsoplossingen (niet-Magento) wordt gedaan via I/O Runtime platform.  Wij hebben een [referentie implementatie](https://github.com/adobe/commerce-cif-graphql-integration-reference) gebouwd om te tonen hoe dit wordt gedaan. Dit laat het hergebruik van [AEM CIF Cloud Connector](https://github.com/adobe/commerce-cif-connector) en [AEM de Componenten van de Kern van CIF](https://github.com/adobe/aem-core-cif-components) toe door Magento GraphQL API bovenop om het even welk derde handelsplatform bloot te stellen. Om maximale flexibiliteit en schaalbaarheid te bieden, wordt deze integratielaag geïmplementeerd op het serverless [Adobe I/O Runtime-platform](https://www.adobe.io/apis/experienceplatform/runtime.html).

## 15. Is er een manier om de productgegevens te verbeteren met commerciële tekst? Waar doe je dit? In AEM of in de handelsoplossing?

We raden u aan om marketinggerelateerde gegevens en inhoud in AEM te beheren. Decoreer productgegevens van uw handelsoplossing met extra attributen gebruikend de Fragmenten van de Inhoud of creeer en verbind de Fragmenten van de Ervaring voor ongestructureerde inhoud met uw producten.

## 16. Verandert de integratie tussen AEM-Magento wanneer het platform van Adobe I/O Runtime wordt gebruikt?

De klanten die de handelsdiensten willen uitbreiden kunnen de zelfde integratie gebruiken en actiereeksen schrijven die op het I/O Runtime platform worden ontvangen om bedrijfslogica te injecteren en de handelsdiensten te verrijken.

## 17. Zal SPA voorwerk opslaan met AEM SPA editor?

AEM kan als auteursgereedschap voor om het even welk soort winkelfront worden gebruikt. Momenteel wordt rendering op de server en op de client (hybride) gebruikt in AEM storefront. Later in 2021 zullen we PWA-ondersteuning beschikbaar stellen voor het ontwerpen van inhoud zonder kop en zonder kop.


## 18. Hoe kunnen wij naleving PCI verzekeren wanneer het gebruiken van AEM voor de volledige presentatielaag?

We raden je aan geabstraheerde betalingsmethoden te gebruiken. Dit zet de browser cliënt in directe communicatie met de leverancier van de betaalgateway zodat noch Adobe of de handelsoplossingen kaarthoudende gegevens houden of overgaan. Deze benadering vereist slechts niveau 3 naleving PCI. Nochtans, zijn er extra dingen om als volledig PCI volgzaam te beschouwen zoals hoe de werknemers met het systeem en de gegevens in wisselwerking staan. Voor meer informatie over Magento PCI-compatibiliteit raadpleegt u https://magento.com/pci-compliance

## 19. Als ik gebruik van AEM en Magento cloud-versies, is deze gezamenlijke oplossing PCI-compatibel?

Ja, de zelfbeoordelingsvragenlijst D en de verklaring van naleving zijn op verzoek beschikbaar.


## 20. Hoe kan ik om een I/O Runtime proefvergunning verzoeken?

U kunt om een proefvergunning verzoeken om I/O Runtime [hier](https://adobeio.typeform.com/to/obqgRm) te gebruiken.
