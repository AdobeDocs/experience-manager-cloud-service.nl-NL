---
title: Extra Publish-regio's
description: Leer hoe AEM as a Cloud Service extra publicatiegebieden ondersteunt voor een hogere beschikbaarheid en een lagere latentie.
exl-id: b9ac3c6a-eb8b-461d-8f1d-a0356046a3f9
feature: Operations
role: Admin
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 0%

---


# Extra Publish-regio&#39;s {#additional-publish-regions}

Voor aanvullende publicatiegebieden kan een licentie worden verleend en deze kunnen worden ingeschakeld voor programma&#39;s die zijn ingesteld met AEM Sites. Wanneer gevormd, wordt het verkeer op stadium en productiemilieu&#39;s verpletterd aan veelvoudige publicatielandbouwbedrijven, die de volgende voordelen heeft:

* Lagere Latentie - Vereist dat de route van CDN aan de AEM publicatieinstanties aan het dichtstbijzijnde publicatiegebied wordt gericht, dat voor websites en toepassingen voordelig is die door gebruikers in veelvoudige geographies worden bezocht.
* Hogere beschikbaarheid - Als een gebied niet beschikbaar is, stuurt de CDN het verkeer naar de andere beschikbare regio(&#39;s).

Organisaties kunnen maximaal drie extra publicatiegebieden licenties verlenen.

>[!NOTE]
>
>* Deze functie is beschikbaar voor de Sites- en Forms-oplossingen.
>* Deze eigenschap kan niet op [ zandbakprogramma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md) worden toegepast.
>* Voor deze functie moet uw programma worden bijgewerkt naar AEM versie 12142 of hoger.

## Gevallen gebruiken {#use-cases}

Hieronder volgt een aantal gebruiksgevallen waarin organisaties kunnen profiteren van het verlenen van licenties voor extra publicatiegebieden.

1. Voor organisaties die significant of zaken-kritiek verkeer van gebruikers ver weg van het primaire gebied ontvangen, kunnen de extra publicatiegebieden latentie verminderen die door die bezoekers wordt ervaren.
1. Voor organisaties die aanzienlijke monetaire of reputatieschade kunnen lijden wanneer een site niet beschikbaar is, kan dit worden beperkt door extra publicatiegebieden te gebruiken om de AEM publicatielaag veerkrachtiger te maken tegen regionale mislukkingen.
1. Voor organisaties waarvan de inhoudsauteurs zich op een geografische locatie bevinden die ver van de meeste publicatielagen ligt, kan het primaire gebied worden gekozen bij de locatie van de auteur van de inhoud, terwijl in de buurt van het publicatiezijverkeer aanvullende publicatiegebieden kunnen worden geconfigureerd, waarbij beide doelgroepen profiteren van een geoptimaliseerde ervaring.

## Het toelaten en het Vormen {#enabling-and-configuring}

Nadat u een licentie voor een extra publicatiegebied hebt verleend, worden de regio&#39;s geconfigureerd met Cloud Manager. Zie de [ documentatie van Cloud Manager ](/help/implementing/cloud-manager/manage-environments.md#multiple-regions) voor gedetailleerde instructies.

Aanvullende publicatiegebieden worden toegepast op stadium- en productieomgevingen, maar niet op RDE- of ontwikkelomgevingen.

In het geval een gebied niet beschikbaar wordt, te hoeven de klanten niet om het verpletteren van verkeer aan beschikbare gebieden te beheren aangezien het door Adobe CDN wordt beheerd.

Zoals beschreven in de Geavanceerde sectie van de Overwegingen van het Voorzien van een netwerk hieronder, wordt het geadviseerd dat de klanten die geavanceerd voorzien van een netwerk gebruiken het voor elk extra publicatiegebied vormen om beschikbaarheid te handhaven als een gebied niet beschikbaar wordt.


## Geavanceerde overwegingen voor netwerken {#advanced-networking-considerations}

Wanneer een extra publicatiegebied op een programma met geavanceerd reeds gevormd voorzien van een netwerk wordt toegelaten, zal het verkeer in het extra publicatiegebied dat de geavanceerde voorzien van een netwerkregels aanpast door standaardroute door het primaire gebied. Om uit verhoogde beschikbaarheid voordeel te halen, wordt het geadviseerd om geavanceerd voorzien van een netwerk op de extra gebieden toe te laten.

Zie de [ Geavanceerde Configuratie van het Voorzien van een netwerk voor Extra Gebieden van Publish ](/help/security/configuring-advanced-networking.md#advanced-networking-configuration-for-additional-publish-regions) sectie in de Geavanceerde documentatie van het Voorzien van een netwerk voor details, met inbegrip van hoe te om geavanceerde voorzien van een netwerkconfiguraties aan extra gebieden toe te voegen zonder verlies van connectiviteit te veroorzaken.

## Logboekregistratie {#logging}

Als extra publicatiegebieden zijn ingeschakeld, worden afzonderlijke logbestanden voor elk gebied beschikbaar gesteld via Cloud Manager. Voor meer informatie, zie [ Toegang tot en het Leiden Logboeken ](/help/implementing/cloud-manager/manage-logs.md) en [ Logboeken voor de Extra Gebieden van Publish ](/help/implementing/developing/introduction/logging.md#logs-for-additional-publish-regions).

## Beperkingen {#limitations}

Houd rekening met de volgende beperkingen wanneer u overweegt extra publicatiegebieden te gebruiken.

* Aanvullende publicatiegebieden mogen alleen aan AEM Sites of AEM Forms worden toegevoegd.
   * De extra publicatiegebieden strekken zich niet tot andere AEM oplossingen of verwante functionaliteit uit die in het zelfde programma (bijvoorbeeld, AEM Assets of Adobe Learning Manager) worden opgesteld.
   * Deze oplossingen kunnen echter aan een programma worden toegevoegd zolang er ten minste één Sites of Forms-oplossing op van toepassing is.
* Aanvullende regio&#39;s kunnen alleen worden toegevoegd als de bijbehorende rechten beschikbaar en ongebruikt zijn in de huurder.
* Er kunnen maximaal drie extra publicatiegebieden worden toegevoegd aan elke afzonderlijke omgeving.
* Aanvullende regio&#39;s zijn alleen beschikbaar voor productieprogramma&#39;s. De functie is niet beschikbaar in sandboxprogramma&#39;s.
* Aanvullende publicatiegebieden worden alleen toegepast op stadium- en productieomgevingen, niet op RDE- of ontwikkelomgevingen.
* Voor aanvullende publicatiegebieden moet uw programma worden bijgewerkt om versie 12142 of hoger AEM te kunnen uitbrengen.
