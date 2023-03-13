---
title: Versie-updates AEM
description: Versie-updates AEM
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
source-git-commit: f977c6d8fa3ebd4b082e48da8b248178f9a2f34b
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 2%

---


# Versie-updates AEM {#aem-version-updates}

## Inleiding {#introduction}

AEM as a Cloud Service gebruikt nu ononderbroken integratie en ononderbroken levering (CI/CD) om ervoor te zorgen dat uw projecten op de huidigste AEM versie zijn. Dit betekent dat de productie en het opvoeren instanties aan de recentste AEM versie zonder enige onderbreking van de dienst voor gebruikers worden bijgewerkt.

>[!NOTE]
>
>Als de update naar de productieomgeving mislukt, wordt de testomgeving automatisch teruggedraaid in Cloud Manager. Dit wordt automatisch gedaan om ervoor te zorgen dat nadat een update voltooit, zowel de het opvoeren als productiemilieu&#39;s op de zelfde AEM versie zijn.

Er zijn twee typen AEM versie-updates:

* **Updates voor AEM**

   * Kunnen dagelijks worden uitgebracht.
   * Deze bestanden zijn vooral bedoeld voor onderhoudsdoeleinden, zoals de nieuwste oplossingen voor problemen en beveiligingsupdates.
   * minimaal effect hebben, aangezien de wijzigingen regelmatig worden toegepast.

* **Nieuwe functies bijwerken**

   * Wordt vrijgegeven via een voorspelbaar maandschema.

AEM updates doorlopen een intensieve en volledig geautomatiseerde productvalideringspijplijn met meerdere stappen, zodat de service voor alle systemen in productie niet wordt onderbroken. Gezondheidscontroles worden gebruikt om de gezondheid van de toepassing te controleren. Als deze controles tijdens een AEM as a Cloud Service update ontbreken, zal de versie niet te werk gaan en Adobe zal onderzoeken waarom de update dit onverwachte gedrag veroorzaakte.

[producttests en functionele tests van de klant;](/help/implementing/cloud-manager/overview-test-results.md#functional-testing) die productupgrades en klantcode verhinderen productiesystemen te breken, worden ook gevalideerd tijdens een AEM versie-update.

>[!NOTE]
>
>Als de douanecode aan het opvoeren en niet aan productie werd geduwd, zal de volgende AEM update die veranderingen verwijderen om de git markering van de laatste succesvolle klantenversie aan productie te weerspiegelen. Daarom zal de douanecode die slechts op het opvoeren beschikbaar was opnieuw moeten worden opgesteld.

## Composite Node Store {#composite-node-store}

Updates worden meestal zonder downtime uitgevoerd, ook voor de ontwerpinstantie, die een cluster met knooppunten is. Rolling updates zijn mogelijk vanwege de functie voor samengestelde knooppuntopslag in Eak.

Met deze functie kunnen AEM tegelijkertijd verwijzen naar meerdere opslagplaatsen. In een het rollen plaatsing, bevat de nieuwe groene AEM versie zijn eigen `/libs` (de op TarMK gebaseerde onveranderlijke opslagplaats), verschillend van de oudere blauwe AEM versie, hoewel beide verwijzen naar een gedeelde op DocumentMK gebaseerde veranderbare opslagplaats die gebieden zoals `/content` , `/conf` , `/etc` en andere. Omdat zowel blauw als groen hun eigen versies hebben `/libs`, kunnen zij allebei actief tijdens de het rollen update zijn, allebei die verkeer opnemen tot het blauw volledig door groen wordt vervangen.
