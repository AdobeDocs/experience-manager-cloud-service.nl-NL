---
title: Opmerkingen bij de release voor Cloud Manager 2025.4.0
description: Meer informatie over de release van Cloud Manager 2025.4.0 in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: fcd9ead02ca5061778001d954ae9a9fc6088d5d1
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2025.4.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

Meer informatie over de release van Cloud Manager 2025.4.0 in AEM (Adobe Experience Manager) as a Cloud Service.


Zie ook de [ huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service ](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Releasedatums {#release-date}

De releasedatum voor Cloud Manager 2025.4.0 in AEM as a Cloud Service is donderdag 10 april 2025.

De volgende geplande release is donderdag 8 mei 2025.

## Nieuwe functies {#what-is-new}

* **(UI) Verbeterde zichtbaarheid van de implementatie**

  De pagina van de details van de pijpleidingsuitvoering in Cloud Manager toont nu een statusbericht (&quot;*Wachten - andere lopende update*&quot;) wanneer een plaatsing op een andere plaatsing wacht te beëindigen. Deze workflow maakt het eenvoudiger om de volgorde tijdens de implementatie van de omgeving te begrijpen.  <!-- CMGR-66890 -->

  ![ de dialoogdoos van de plaatsing van de Ontwikkeling die details en verdeling toont ](/help/implementing/cloud-manager/release-notes/assets/dev-deployment.png)

* **(UI) Verbeterde domeinvalidatie**

  Wanneer het toevoegen van een domein, toont Cloud Manager nu een fout als het domein reeds in een Fastly rekening geïnstalleerd is: &quot;*het domein is reeds geïnstalleerd in een Fastly rekening. Gelieve te verwijderen eerst van daar alvorens aan Cloud Service toe te voegen.*&quot;

## Programma voor vroegtijdige goedkeuring {#early-adoption}

Neem deel aan het Cloud Manager-programma voor vroegtijdige adoptie om exclusieve toegang te krijgen tot de volgende functies voordat ze algemeen worden uitgebracht.

Momenteel zijn de volgende mogelijkheden voor vroegtijdige adoptie beschikbaar:

### Kies voor uw eigen git - nu met ondersteuning voor GitLab en Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**breng Uw Eigen eigenschap van het Git** is uitgebreid om steun voor externe bewaarplaatsen, zoals GitLab en Bitbucket te omvatten. Deze nieuwe steun is naast reeds bestaande steun voor privé en ondernemingsbewaarplaatsen GitHub. Wanneer u deze nieuwe repo&#39;s toevoegt, kunt u deze ook rechtstreeks aan uw pijpleidingen koppelen. U kunt deze opslagruimten hosten op openbare cloudplatforms of binnen uw privécloud of infrastructuur. Deze integratie verwijdert ook de behoefte aan constante codesynchronisatie met de bewaarplaats van Adobe en verstrekt de capaciteit om trekkingsverzoeken te bevestigen alvorens hen in een hoofdtak samen te voegen.

De pijpleidingen die externe bewaarplaatsen gebruiken (exclusief GitHub-ontvangen degenen) en de **Trekker van de Plaatsing** aan **wordt geplaatst op de Veranderingen van het Git** beginnen nu automatisch.

Zie [ externe bewaarplaatsen in Cloud Manager ](/help/implementing/cloud-manager/managing-code/external-repositories.md) toevoegen.

![ voeg de dialoogdoos van de Bewaarplaats ](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png) toe

>[!NOTE]
>
>Momenteel, zijn de uit-van-de-doos controles van de trekkingsverzoekcodekwaliteit exclusief aan GitHub-ontvangen bewaarplaatsen, maar een update om deze functionaliteit tot andere verkopers van het Git uit te breiden is in de werken.

Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ Grp-CloudManager_BYOG@adobe.com ](mailto:grp-cloudmanager_byog@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID. Zorg ervoor dat u ook het Git-platform opgeeft dat u wilt gebruiken en dat u zich in een opslagstructuur van een privéserver, een openbare opslagruimte of een bedrijfsopslagruimte bevindt.

<!--
### AEM Home {#aem-home}

AEM Home introduces a centralized starting point for managing content, assets, and sites within Adobe Experience Manager. Designed to deliver a personalized experience, AEM Home lets you navigate the AEM ecosystem seamlessly according to your roles and goals. Acting as a guide, it provides key insights and recommended actions to help you achieve your objectives efficiently. With a clear, persona-driven layout, AEM Home ensures quick access to essential tools, supporting a streamlined and effective experience across all AEM features.

Available to early adopters, AEM Home offers an optimized experience focused on improving workflows, prioritizing goals, and delivering results. Opting in lets you influence AEM Home's development by providing feedback that helps shape its future and enhances its value for the entire AEM community.

If you are interested in testing this new capability and sharing your feedback, send an email to [Grp-AemHome@adobe.com](mailto:Grp-AemHome@adobe.com) from your email address associated with your Adobe ID. Be sure to include the following information:

* The role that best fits your profile: Content author, Developer, Business owner, Admin, or Other (provide a description).
* Your primary AEM access surface: AEM Sites, AEM Assets, AEM Forms, Cloud Manager, or Other (provide a description). -->

## Bugfixes

* **Uitgave met certificaten ontbrekende het gebied van de Gemeenschappelijke Naam (CN)**

  Cloud Manager genereert niet langer een NullPointerException (NPE) en 500 HTTP- reactie wanneer het verwerken van EV/OV- certificaten die geen Gemeenschappelijke Naam (CN) op het Onderwerpgebied omvatten. Moderne certificaten laten vaak CN weg en gebruiken in plaats daarvan de Alternatieve Naam Onderwerp (San). Deze correctie zorgt ervoor dat het ontbreken van CN niet langer een fout veroorzaakt tijdens het configuratieproces wanneer SAN aanwezig is. <!-- CMGR-67548 -->

* **de verificatiekwestie van het Domein met onjuiste certificaat aanpassing**

  Cloud Manager verifieert domeinen niet meer verkeerd gebruikend de verkeerde certificaten. Eerder gebruikte de bevestigingslogica patroon-gebaseerde aanpassing in plaats van nauwkeurige aanpassing, die domeinen zoals `should-not-be-verified.example.com` ertoe bracht om te verschijnen zoals geverifieerd toe te schrijven aan overlapping met geldige certificaten voor `example.com`. Met deze correctie zorgt u ervoor dat domeinvalidatie nu controleert op exacte overeenkomsten en onjuiste certificaatkoppelingen voorkomt. <!-- CMGR-67225 -->

* **gedwongen uniciteit voor Geavanceerde de voorwaardennamen van de haven van het Voorzien van een netwerk**

  Cloud Manager dwingt nu unieke naamgeving af voor Advanced Networking-poort. Eerder waren dubbele namen toegestaan, wat tot conflicten kon leiden. Deze moeilijke situatie zorgt ervoor dat elke haven voorwaartse ingang een verschillende naam heeft, die op beste praktijken voor de integriteit van de netwerkconfiguratie richt. <!-- CMGR-67082 -->


<!-- ## Known issues {#known-issues} -->

