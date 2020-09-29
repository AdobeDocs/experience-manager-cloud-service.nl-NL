---
title: Versie-updates AEM
description: 'Versie-updates AEM '
translation-type: tm+mt
source-git-commit: 5032c503be8972879eff82d4919bb07dcff1db2a
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 5%

---


# Versie-updates AEM {#aem-version-updates}

## Inleiding {#introduction}

AEM als Cloud Service gebruikt nu Continuous Integration en Continuous Delivery (CI/CD) om ervoor te zorgen dat uw projecten op de huidigste AEM versie zijn. Dit betekent dat alle verbeteringsverrichtingen volledig geautomatiseerd zijn, zodat vereist geen onderbreking van de dienst voor gebruikers.

>[!NOTE]
>Als de update naar de productieomgeving mislukt, wordt de werkgebiedomgeving automatisch teruggedraaid. Dit wordt automatisch gedaan om ervoor te zorgen dat zowel het werkgebied als de productieomgeving na het voltooien van een update dezelfde AEM versie hebben.

AEM versie-updates zijn van twee typen:

* **AEM Push-updates**

   * Kunnen dagelijks worden uitgebracht.
   * Meestal onderhoud, inclusief de nieuwste oplossingen voor problemen en beveiligingsupdates.

      Aangezien veranderingen regelmatig worden toegepast, is het effect cumulatief, wat minder invloed heeft op uw service.

* **Nieuwe functie-updates**

   * Uitgegeven via een voorspelbaar maandschema.

AEM updates doorlopen een intensieve en volledig geautomatiseerde productvalideringspijplijn met meerdere stappen die ervoor zorgen dat de service voor alle systemen in productie niet wordt onderbroken. Gezondheidscontroles worden gebruikt om de gezondheid van de toepassing te controleren. Als deze controles tijdens een AEM als update van de Cloud Service ontbreken, zal de versie niet te werk gaan en Adobe zal onderzoeken waarom de update dit onverwachte gedrag veroorzaakte.

[Producttests en functionele tests](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/understand-test-results.html#functional-testing) van de Klant die productupgrades en klantencode verhinderen de productie te breken, worden ook gevalideerd tijdens een AEM versie-update.

>[!NOTE]
>
>Als de douanecode aan het opvoeren werd geduwd en dan door u werd verworpen, zal de volgende AEM update die veranderingen verwijderen om op de git markering van de laatste succesvolle klantenversie aan productie te wijzen.

## Composite Node Store {#composite-node-store}

Zoals hierboven vermeld, zullen updates in de meeste gevallen nul onderbreking, onder meer voor de auteur, die een cluster van knopen is. Rolling updates zijn mogelijk vanwege de functie voor *samengestelde knooppuntopslag* in Eak.

Met deze functie kunnen AEM tegelijkertijd verwijzen naar meerdere opslagplaatsen. In een het rollen plaatsing, bevat de nieuwe Groene AEM versie zijn eigen `/libs` (de op TarMK gebaseerde onveranderlijke bewaarplaats), verschillend van de oudere Blauwe AEM versie, hoewel allebei verwijzen naar een gedeelde op DocumentMK gebaseerde veranderbare bewaarplaats die gebieden zoals `/content` , `/conf` , `/etc` en anderen bevat. Omdat blauw en Groen hun eigen versies van hebben, kunnen zij allebei actief tijdens de het rollen update zijn, allebei die verkeer nemen tot het blauw volledig door groen wordt vervangen. `/libs`

