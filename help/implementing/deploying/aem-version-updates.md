---
title: Versie-updates AEM
description: 'Versie-updates AEM '
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 5%

---

# Versie-updates AEM {#aem-version-updates}

## Inleiding {#introduction}

AEM as a Cloud Service gebruikt nu Continuous Integration en Continuous Delivery (CI/CD) om ervoor te zorgen dat uw projecten op de huidigste AEM versie zijn. Dit betekent dat de instanties van de Productie en van het Stadium aan de recentste AEM versie zonder enige onderbreking van de dienst voor gebruikers worden bijgewerkt.

>[!NOTE]
>Als de update naar de productieomgeving mislukt, wordt de werkgebiedomgeving automatisch teruggedraaid. Dit wordt automatisch gedaan om ervoor te zorgen dat zowel het werkgebied als de productieomgeving na het voltooien van een update dezelfde AEM versie hebben.

AEM versie-updates zijn van twee typen:

* **AEM Push-updates**

   * Kunnen dagelijks worden uitgebracht.

   * Meestal onderhoud, inclusief de nieuwste oplossingen voor problemen en beveiligingsupdates.

      Aangezien veranderingen regelmatig worden toegepast, is het effect cumulatief, wat minder invloed heeft op uw service.

* **Nieuwe functie-updates**

   * Uitgegeven via een voorspelbaar maandschema.

AEM updates doorlopen een intensieve en volledig geautomatiseerde productvalideringspijplijn met meerdere stappen die ervoor zorgen dat de service voor alle systemen in productie niet wordt onderbroken. Gezondheidscontroles worden gebruikt om de gezondheid van de toepassing te controleren. Als deze controles tijdens een AEM as a Cloud Service update ontbreken, zal de versie niet te werk gaan en Adobe zal onderzoeken waarom de update dit onverwachte gedrag veroorzaakte.

[Producttests en functionele tests van de klant](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/understand-test-results.html#functional-testing) die productupgrades en de druk van de klantencode verhinderen productie te breken worden ook bevestigd tijdens een AEM versie update.

>[!NOTE]
>
>Als de douanecode aan het opvoeren werd geduwd en dan door u werd verworpen, zal de volgende AEM update die veranderingen verwijderen om op de git markering van de laatste succesvolle klantenversie aan productie te wijzen.

## Composite Node Store {#composite-node-store}

Zoals hierboven vermeld, zullen updates in de meeste gevallen nul onderbreking, onder meer voor de auteur, die een cluster van knopen is. Rolling-updates zijn mogelijk vanwege de *opslag van samengestelde knooppunten* in eiken.

Met deze functie kunnen AEM tegelijkertijd verwijzen naar meerdere opslagplaatsen. In een het rollen plaatsing, bevat de nieuwe Groene AEM versie zijn eigen `/libs` (de op TarMK gebaseerde onveranderlijke opslagplaats), verschillend van de oudere Blauwe AEM versie, hoewel beide verwijzen naar een gedeelde op DocumentMK gebaseerde veranderbare opslagplaats die gebieden zoals `/content` , `/conf` , `/etc` en andere. Omdat zowel de Blauwe als de Groenen hun eigen versies hebben `/libs`, kunnen zij allebei actief tijdens de het rollen update zijn, allebei die verkeer opnemen tot het blauw volledig door groen wordt vervangen.
