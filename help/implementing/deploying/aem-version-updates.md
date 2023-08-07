---
title: Versie-updates AEM
description: Leer hoe AEM as a Cloud Service ononderbroken integratie en levering (CI/CD) gebruikt om uw projecten op de recentste versie te houden.
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
source-git-commit: dd567c484d71e25de1808f784c455cfb9b124fbf
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 1%

---


# Versie-updates AEM {#aem-version-updates}

Leer hoe AEM as a Cloud Service ononderbroken integratie en levering (CI/CD) gebruikt om uw projecten op de recentste versie te houden.

## CI/CD {#ci-cd}

AEM as a Cloud Service gebruik ononderbroken integratie en ononderbroken levering (CI/CD) om ervoor te zorgen dat uw projecten op de huidigste AEM versie zijn. Met dit proces worden uw productie-, staging- en ontwikkelingsinstanties naadloos bijgewerkt, zonder dat dit uw gebruikers verstoort.

Voordat uw exemplaren automatisch worden bijgewerkt, worden 3-5 dagen van tevoren nieuwe AEM onderhoudsreleases gepubliceerd. Tijdens deze periode kunt u
[triggerhandmatige updates voor uw ontwikkelingsinstanties](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment).
Zodra deze tijd verstrijkt, worden de versie-updates automatisch toegepast op uw ontwikkelomgevingen eerst. Als de update succesvol is, gaat het updateproces naar uw werkgebied en productieinstanties. De ontwikkelings- en staging-instanties fungeren als een automatische kwaliteitspoort, waar uw aangepaste, geschreven tests worden uitgevoerd voordat de update wordt toegepast op uw productieomgeving.

>[!NOTE]
>
> Opmerking: de automatische updates voor ontwikkelomgevingen zullen in 2023 geleidelijk worden ingeschakeld voor alle klanten. Als uw ontwikkelomgevingen niet automatisch worden bijgewerkt, kunt u handmatige updates gebruiken om ze synchroon te houden met uw werkgebied- en productieomgeving.


## Type updates {#update-types}

Er zijn twee typen AEM versie-updates:

* **AEM onderhoudsupdates**

   * Kunnen dagelijks worden uitgebracht.
   * Deze bestanden zijn vooral bedoeld voor onderhoudsdoeleinden, zoals de nieuwste oplossingen voor problemen en beveiligingsupdates.
   * minimaal effect hebben, aangezien de wijzigingen regelmatig worden toegepast.

* **Nieuwe functies bijwerken**

   * worden vrijgegeven op een [voorspelbaar maandelijks schema.](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)

## Update mislukt {#update-failure}

AEM updates doorlopen een intensieve en volledig geautomatiseerde productvalideringspijplijn met meerdere stappen, zodat de service voor alle systemen in productie niet wordt onderbroken.
Gezondheidscontroles worden gebruikt om de gezondheid van de toepassing te controleren.
Als deze controles tijdens een AEM as a Cloud Service update ontbreken, zal de versie niet te werk gaan, en Adobe zal onderzoeken waarom de update dit onverwachte gedrag veroorzaakte.

Wanneer u een nieuwe versie van een douanecode van op uw milieu&#39;s opstelt,
[Product- en aangepaste functionele tests](/help/implementing/cloud-manager/overview-test-results.md#functional-testing)
een cruciale rol spelen bij het waarborgen dat de productiesystemen stabiel en functioneel blijven, ook na een wijziging. Deze tests worden ook gebruikt in het updateproces van de Versie van de AEM.

Als de update naar de productieomgeving mislukt, wordt de testomgeving automatisch teruggedraaid in Cloud Manager. Dit wordt automatisch gedaan om ervoor te zorgen dat nadat een update voltooit, zowel de het opvoeren als productiemilieu&#39;s op de zelfde AEM versie zijn.
Op dezelfde manier als een geautomatiseerde update van een ontwikkelomgeving ontbreekt, zal het opvoeren en de productiemilieu&#39;s niet worden bijgewerkt.

>[!NOTE]
>
>Als de douanecode aan het opvoeren en niet aan productie werd geduwd, zal de volgende AEM update die veranderingen verwijderen om de git markering van de laatste succesvolle klantenversie aan productie te weerspiegelen. Daarom zal de douanecode die slechts op het opvoeren beschikbaar was opnieuw moeten worden opgesteld.

## Composite Node Store {#composite-node-store}

In de meeste gevallen worden updates zonder downtime uitgevoerd, ook voor de ontwerpinstantie, die een cluster met knooppunten is. Rolling-updates zijn mogelijk vanwege [de samengestelde eigenschap van de knoopopslag in Eak.](https://jackrabbit.apache.org/oak/docs/nodestore/compositens.html)

Met deze functie kunnen AEM tegelijkertijd verwijzen naar meerdere opslagplaatsen. In een [stationering,](/help/implementing/deploying/overview.md#how-rolling-deployments-work) de nieuwe AEM bevat een eigen `/libs` (de op TarMK gebaseerde onveranderlijke opslagplaats), verschillend van de oudere AEM versie, hoewel beide verwijzen naar een gedeelde op DocumentMK gebaseerde veranderbare opslagplaats die gebieden zoals `/content` , `/conf` , `/etc` en andere.

Omdat zowel de oude als de nieuwe versie hun eigen versies hebben `/libs`, kunnen zij zowel tijdens de het rollen update actief zijn, en allebei verkeer nemen tot oud volledig door nieuw wordt vervangen.
