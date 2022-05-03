---
title: Opvallende wijzigingen in Adobe Experience Manager (AEM) as a Cloud Service
description: Opvallende wijzigingen in Adobe Experience Manager (AEM) as a Cloud Service
exl-id: fe11d779-66cd-45aa-aa6b-c819b88d2405
source-git-commit: d3208a9a0785909e9b62d4033437a8ff44f7ba3e
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 8%

---

# Opvallende wijzigingen in Adobe Experience Manager (AEM) as a Cloud Service {#notable-changes-aem-cloud}

AEM Cloud Service biedt veel nieuwe functies en mogelijkheden voor het beheer van uw AEM-projecten. Er zijn echter een aantal verschillen tussen AEM Sites op locatie of in Adobe Managed Service in vergelijking met AEM Cloud Service. In dit document worden de belangrijke verschillen belicht.

>[!CONTEXTUALHELP]
>id="aem_cloud_notable_changes"
>title="Opvallende wijzigingen in AEM as a Cloud Service"
>abstract="Op dit tabblad kunt u inhoud weergeven die u helpt de verschillen te begrijpen tussen AEM op locatie of in Adobe Managed Services in vergelijking met AEM as a Cloud Service."
>additional-url="https://video.tv.adobe.com/v/330543" text="Evolutie van AEM as a Cloud Service"


>[!NOTE]
>Dit document benadrukt de opmerkelijke veranderingen in AEM als geheel. Voor meer informatie en oplossingsspecifieke veranderingen zie:
>
>* [Inleiding tot Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
>* [Nieuwe functies en verschillen](/help/overview/what-is-new-and-different.md) tussen Adobe Experience Manager as a Cloud Service en eerdere versies
>* De [architectuur](/help/overview/architecture.md) van Adobe Experience Manager as a Cloud Service
>* [Belangrijke wijzigingen in AEM Sites as a Cloud Service](/help/sites-cloud/sites-cloud-changes.md)
>* [Belangrijke wijzigingen in AEM Assets as a Cloud Service](/help/assets/assets-cloud-changes.md)


De belangrijkste verschillen zijn te vinden op de volgende gebieden:

* [/apps en /libs zijn onveranderlijk bij runtime](#apps-libs-immutable)

* [OSGi-bundels en -configuraties moeten als code worden behandeld](#osgi)

* [Wijzigingen in publicatieruimte zijn niet toegestaan](#changes-to-publish-repo)

* [Aangepaste runmodi zijn niet toegestaan](#custom-runmodes)

* [Verwijderen van replicatieagents en gerelateerde wijzigingen](#replication-agents)

* [Verwijderen van klassieke gebruikersinterface](#classic-ui)

* [Levering op de website publiceren](#publish-side-delivery)

* [Afhandeling en levering van bedrijfsmiddelen](#asset-handling)

## /apps en /libs zijn onveranderlijk bij runtime {#apps-libs-immutable}

Alle inhoud en submappen in `/apps` en `/libs` is alleen-lezen. Om het even welke eigenschap of douanecode die verwacht om veranderingen daar aan te brengen zal er niet doen. Er wordt een fout geretourneerd dat dergelijke inhoud alleen-lezen is en de schrijfbewerking niet kan worden voltooid. Dit heeft gevolgen voor een aantal AEM:

* Geen wijzigingen in `/libs` zijn überhaupt toegestaan.
   * Dit is geen nieuwe regel, nochtans werd dit niet afgedwongen in vorige on-premise versies van AEM.
* Bedekkingen voor gebieden in `/libs` die mogen worden overschreden, zijn nog steeds toegestaan binnen `/apps`.
   * Dergelijke overlays moeten afkomstig zijn van Git via de CI/CD-leiding.
* Statische het ontwerpinformatie van het Malplaatje die in wordt opgeslagen `/apps` kan niet via UI worden bewerkt.
   * Het wordt aanbevolen bewerkbare sjablonen te gebruiken.
   * Als de Statische Malplaatjes nog worden vereist, moet de configuratieinformatie uit Git via de pijpleiding CI/CD komen.
* MSM de Vervaging en de douaneMSM uitrolconfiguraties moeten van Git via de pijpleiding worden geïnstalleerd CI/CD.
* I18n vertalingsveranderingen moeten van Git via de CI/CD pijpleiding komen.

## OSGi-bundels en -configuraties moeten als code worden behandeld {#osgi}

Wijzigingen in OSGi-bundels en -configuraties moeten via de CI/CD-pijplijn worden aangebracht.

* Nieuwe of bijgewerkte OSGi-bundels moeten via Git via de CI/CD-pijplijn worden geïntroduceerd.
* Wijzigingen in OSGi-configuraties kunnen alleen via de CI/CD-leiding van Git komen.

De console van het Web, die in vorige versies van AEM wordt gebruikt om bundels OSGi en configuraties te veranderen, is niet beschikbaar in AEM Cloud Service.

## Wijzigingen in publicatieruimte zijn niet toegestaan {#changes-to-publish-repo}

Behalve wijzigingen onder de `/home` op de publicatielijst. Directe wijzigingen in de publicatiereserver zijn niet toegestaan op AEM Cloud Service. In eerdere versies van on-premise AEM of AEM op AMS kunnen wijzigingen in de code rechtstreeks worden doorgevoerd in de publicatieopslagplaats. Sommige beperkingen kunnen op de volgende manieren worden beperkt:

* Voor op inhoud en inhoud gebaseerde configuratie: Breng de wijzigingen aan in de auteurinstantie en publiceer deze.
* Voor code en configuratie: de wijzigingen in de GIT-opslagplaats aan te brengen en de CI/CD-pijpleiding uit te voeren.

## Aangepaste runmodi zijn niet toegestaan {#custom-runmodes}

De volgende runmodes worden verstrekt uit-van-de-doos voor AEM Cloud Service:

* `author`
* `publish`
* `prod`
* `author.prod`
* `publish.prod`
* `stage`
* `author.stage`
* `publish.stage`
* `dev`
* `author.dev`
* `publish.dev`

Aanvullende of aangepaste uitvoermodi zijn niet mogelijk in AEM Cloud Service.

## Verwijderen van replicatieagents en gerelateerde wijzigingen {#replication-agents}

In AEM Cloud Service wordt inhoud gepubliceerd met [Distributie van inhoud verkopen](https://sling.apache.org/documentation/bundles/content-distribution.html). De replicatieagenten die in vorige versies van AEM worden gebruikt worden niet meer gebruikt of verstrekt, die de volgende gebieden van bestaande AEM projecten zouden kunnen beïnvloeden:

* Aangepaste workflows die bijvoorbeeld inhoud doorsturen naar replicatieagents van voorvertoningsservers.
* Aanpassing aan replicatieagenten om inhoud om te zetten
* De omgekeerde Replicatie gebruiken om inhoud van te brengen terug naar auteur publiceren

Bovendien merk op dat de pauze en onbruikbaar maken knopen uit de console van het replicatieagentenbeleid zijn verwijderd.

## Verwijderen van klassieke gebruikersinterface {#classic-ui}

De klassieke gebruikersinterface is niet meer beschikbaar in AEM Cloud Service.

## Levering op de website publiceren {#publish-side-delivery}

De versnelling van HTTP met inbegrip van CDN en verkeersbeheer voor auteur en publiceer de diensten worden verstrekt door gebrek in AEM Cloud Service.

Voor project dat van AMS of een op-gebouw Adobe overgaat adviseert sterk leveraging ingebouwde CDN, omdat de eigenschappen binnen AEM Cloud Service voor CDN worden geoptimaliseerd verstrekt.

## Afhandeling en levering van bedrijfsmiddelen {#asset-handling}

Het uploaden, verwerken en downloaden van bedrijfsmiddelen worden geoptimaliseerd in [!DNL Experience Manager Assets] als [!DNL Cloud Service]. [!DNL Assets] is nu efficiënter, maakt meer schaling mogelijk en kunt u sneller uploaden en downloaden. Bovendien is dit van invloed op de bestaande aangepaste code en bepaalde bewerkingen. Voor een lijst met wijzigingen en voor pariteit met [!DNL Experience Manager] 6.5-functies, raadpleegt u de [wijzigingen in [!DNL Assets]](/help/assets/assets-cloud-changes.md).
