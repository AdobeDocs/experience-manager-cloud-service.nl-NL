---
title: AEM - Veelgestelde vragen over de integratie van de Magento met behulp van het kader voor de integratie van de handel
description: AEM - Veelgestelde vragen over de integratie van de Magento met behulp van het kader voor de integratie van de handel
translation-type: tm+mt
source-git-commit: cafe8825fe34f158c74b94b95b7252394de26e4d
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 0%

---


# AEM - Veelgestelde vragen over de integratie van de Magento met behulp van het kader voor de integratie van de handel


## 1. Wordt GraphQL alleen gebruikt voor Magento of is dit beschikbaar voor het opvragen van inhoud die is geschreven op AEM JCR?

Adobe heeft de GraphQL APIs van Magento als zijn officiële handel API voor alle handel verwante gegevens goedgekeurd. Daarom gebruikt AEM GraphQL om handelsgegevens met Magento en met om het even welke handelingsmotor via I/O Runtime uit te wisselen.

## 2. Hoe wordt Adobe I/O in werking gesteld? Spreekt AEM rechtstreeks met Magento?

AEM kan rechtstreeks verbinding maken met Magento zonder I/O-runtimelaag. Als er behoefte is om een niet-Magento handel achterkant (derdeoplossing) met AEM te integreren, kan I/O Runtime platform worden gebruikt om de mappingslaag te ontvangen om Magento GraphQL APIs met om het even welke derde oplossingen APIs te verbinden. Raadpleeg deze [referentie-implementatie](https://github.com/adobe/commerce-cif-graphql-integration-reference)voor meer informatie hierover. Voor oplossingen niet-Magento, zou AEM worden gevormd om aan het I/O Runtime eindpunt te richten.

Het I/O Runtime platform kan ook worden gebruikt om handelsdiensten uit te breiden of aan te passen. Voor dit gebruik-gevallen zou u het I/O Runtime eindpunt roepen dat dan een aangepaste implementatie van de respectieve dienst zal ontvangen. Gebruiksscenario&#39;s voor integratie en extensie kunnen worden gecombineerd.

## 3. Kunnen de activa van het Product (beelden) van AEM via Magento worden opgeslagen en van verwijzingen voorzien admin? Hoe kunnen activa van Dynamic Media worden verbruikt?

Er is op dit moment geen AEM Assets - Magento-integratie. Als tussenoplossing kunt u productelementen (afbeeldingen) opslaan in AEM Assets, maar u moet de element-URL&#39;s handmatig opslaan in Magento. Dynamic Media maken nu deel uit van AEM Assets en zullen op dezelfde manier werken.

## 4. Maakt het uit waar Magento wordt ingezet? (Op prem of in de cloud)

Het maakt niet uit waar Magento wordt ingezet. De integratie en het nieuwe AEM Venia-winkelfront werken ongeacht het implementatiemodel. Nochtans, als het op de goedgekeurde E2E verwijzingsarchitectuur wordt opgesteld, zullen E2E tests tegen prestaties KPIs worden in werking gesteld die werden verzameld die het profiel van een ondernemingsklant vertegenwoordigen. Dit zal u van extra informatie voorzien die u als benchmark kunt gebruiken.

## 5. Hoe worden cataloguspagina&#39;s of productpagina&#39;s in AEM gemaakt? Hoe blijven ze in AEM?

Cataloguspagina&#39;s en productpagina&#39;s worden dynamisch gemaakt en in het cachegeheugen opgeslagen in AEM op basis van algemene catalogussjablonen en productpaginasjablonen. Er worden geen product- of catalogusgegevens geïmporteerd en opgeslagen in AEM.

## 6. Plaats u ook prijzen en andere gegevens in cache via Dispatcher. Vormt dat een veelvuldige uitdaging voor het ongeldig maken van cache?

Dynamische gegevens zoals prijs of voorraad worden niet in de cache opgeslagen op de Dispatcher. Dynamische gegevens worden via GraphQL API&#39;s direct opgehaald aan de clientzijde met webcomponenten. Alleen statische gegevens (zoals product- of categoriegegevens) worden in cache geplaatst op de Dispatcher. Als de productgegevens veranderen, zal er een behoefte aan geheim voorgeheugenbevestiging zijn.

## 7. Hoe werkt cachevalidatie voor AEM Dispatcher met AEM-Magento?

We raden u aan op TTL gebaseerde cachevalidatie in te stellen voor pagina&#39;s die in cache zijn geplaatst op de Dispatcher. Voor dynamische informatie zoals prijs of voorraad raden we aan de datumclient-kant weer te geven. Voor meer informatie over op TTL gebaseerde geheim voorgeheugenongeldigverklaring, gelieve te verwijzen naar [AEM Dispatcher](https://helpx.adobe.com/experience-manager/kb/optimizing-the-dispatcher-cache.html)

## 8. Waarom gebruik je We.Retail niet?

Het Venia-thema (ontwikkeld door Magento) wordt gebruikt en is eerst mobiel en is afgestemd op de PWA van Magento. Het Venia-thema vertegenwoordigt de nieuwste in termen van CSS-opmaak en AEM kerncomponenten.

## 9. Wanneer u productgegevens in Magento bijwerkt, is dat dan een realtime-push naar AEM? Of is het een batchproces?

De toe:voegen-op CIF die met AEM Cloud Service wordt gebruikt laat gegevens toe om van Magento aan AEM op bestelling te stromen. Dit is dus geen realtime-push of batchproces wanneer er een update in Magento is.

## 10 Bestaat er een aanbeveling voor een uniforme zoekopdracht in AEM inhoud met Commerce?

Een verwijzingsimplementatie van het productonderzoek wordt verstrekt maar geen verenigd onderzoek met inhoud. Deze eigenschap is gewoonlijk zeer klantspecifiek en beter opgelost op een project-specifiek niveau.

## 11. Hoe werkt Zoeken met AEM-Magento met CIF?

CIF verstrekt de bar van het Onderzoek en de componenten van het Resultaat van het Onderzoek. De component van de bar van het Onderzoek verzendt een verzoek GraphQL met de onderzoekstermijn naar Magento. Magento retourneert vervolgens een productlijst met productnaam, prijs, SLUG enzovoort. De component van het Resultaat van het Onderzoek toont dan de onderzoeksresultaten in een galeriemening op een pagina van het onderzoeksresultaat die in AEM wordt gecreeerd. De zoekfunctie ondersteunt standaard zoeken in volledige tekst. Wij gebruiken de sleutel SLUG/url om een verwijzing naar PDP te bouwen.

## 11. Hoe kunnen productgegevens in MSM of vertalingen worden gebruikt?

Productgegevens worden meestal al vertaald in PIM of in Magento. De integratie AEM - Magento ondersteunt de verbinding met meerdere Magento-winkels en -winkelweergaven. In een MSM-instelling wordt doorgaans één AEM site gekoppeld aan één Magento-winkelweergave.

## 13. Hoe werkt CIF met andere handelsplatforms?

De integratie met derdeoplossingen zoals andere handelsoplossingen (niet-Magento) wordt gedaan via I/O Runtime platform.  We hebben een [referentie-implementatie](https://github.com/adobe/commerce-cif-graphql-integration-reference) opgesteld om aan te tonen hoe dit gebeurt. Dit laat het hergebruik van de [AEM Schakelaar](https://github.com/adobe/commerce-cif-connector) van de Wolk CIF en de [AEM Componenten](https://github.com/adobe/aem-core-cif-components) van de Kern toe CIF door Magento GraphQL API bovenop om het even welk derde handelsplatform bloot te stellen. Om maximale flexibiliteit en schaalbaarheid te bieden, wordt deze integratielaag geïmplementeerd op het serverloze [Adobe I/O Runtime-platform](https://www.adobe.io/apis/experienceplatform/runtime.html).

## 14. Is er een manier om de productgegevens te verbeteren met commerciële tekst? Waar doe je dit? In AEM of in Magento?

Er zijn meerdere manieren om dit te bereiken en het hangt af van het gebruiksgeval. Een manier zou zijn om met aangepaste kenmerken te werken. Sta AEM auteurs toe om deze gebieden in AEM productredacteur te muteren en de gegevens terug naar PIM te synchroniseren. Een andere mogelijkheid zou zijn AEM Experience Fragments die in de productpagina&#39;s wordt geïnjecteerd.

## 15. Verandert de integratie tussen AEM-Magento wanneer het platform van Adobe I/O Runtime wordt gebruikt?

De klanten die de handelsdiensten willen uitbreiden kunnen de zelfde integratie gebruiken en actiereeksen schrijven die op het I/O Runtime platform worden ontvangen om bedrijfslogica te injecteren en de handelsdiensten te verrijken.

## 16. Aangezien AEM product en cataloguspagina&#39;s dynamisch creeert die op een generisch malplaatje in AEM worden gebaseerd, wat zou ik zien als ik CRXDE Lite zou openen en onder inhoud controleren? Zou ik een hele productboom zien gebaseerd op de producten in Magento? Zo niet, hoe zou een auteur die pagina&#39;s verbeteren?

Er zijn geen JCR-catalogus of productpagina&#39;s meer. Zie vraag 12.

## 17. Zal SPA voorwerk met AEM redacteur van het KUUROORD opslaan?

AEM kan als auteursgereedschap voor om het even welk soort winkelfront worden gebruikt. Momenteel wordt hybride rendering gebruikt voor de nieuwe winkel. In de toekomst, zal AEM voor creatie met SPA en PWA worden gebruikt.

## 18. Hoe speelt PIM in dit kader?

PIM-gegevens worden via GraphQL-verzoeken aan AEM en clients beschikbaar gesteld. Onze aanbeveling is PIM te integreren met de handelscentrale (Magento of andere) zodat PIM-gegevens kunnen worden opgehaald van de commercemotor.

## 19. Hoe kunnen wij naleving PCI verzekeren wanneer het gebruiken van AEM voor de volledige presentatielaag?

Bij het gebruik van AEM op AMS- en Magento-cloudimplementatie is het verplicht om geabstraheerde betalingsmethoden te gebruiken. Dit plaatst de browser cliënt in directe communicatie met de betalingsdienstleverancier zodat noch Adobe of de wolken van de Magento kaarthouder gegevens houden of overgaan. Deze aanpak biedt dekking voor PCI-compatibiliteit voor de technische stapels en datacenters. Nochtans, zijn er extra dingen om als volledig PCI volgzaam te beschouwen zoals hoe de werknemers met het systeem en de gegevens in wisselwerking staan. Voor meer informatie over Magento PCI-compatibiliteit raadpleegt u https://magento.com/pci-compliance

## 20. Hoe kan ik om een I/O Runtime proefvergunning verzoeken?

U kunt een proeflicentie aanvragen om I/O Runtime [hier](https://github.com/AdobeDocs/adobeio-runtime/blob/master/overview/request_a_trial.md)te gebruiken.



