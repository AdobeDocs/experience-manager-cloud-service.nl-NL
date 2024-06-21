---
title: Vertaalregels configureren voor inhoud zonder kop
description: Leer hoe u vertaalregels definieert om inhoud voor vertaling te identificeren.
exl-id: 878ffd5d-0f10-4990-9779-bdf55cd95fac
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 0%

---

# Vertaalregels configureren {#configure-translation-rules}

Leer hoe u vertaalregels definieert om inhoud voor vertaling te identificeren.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM zonder kop [Vertaalintegratie configureren](configure-connector.md) u hebt geleerd hoe u uw vertaalintegratie kunt installeren en configureren en dat u nu moet doen:

* Begrijp de belangrijke parameters van het Kader van de Integratie van de Vertaling in AEM.
* Uw eigen verbinding met uw vertaalservice instellen.

Nu uw integratie is ingesteld, wordt in dit artikel stapsgewijs vastgesteld welke inhoud u moet vertalen.

>[!CAUTION]
>
>Deze stap van de documentatietraject is alleen nodig als u de **Vertaalbaar** markering op inhoudsfragmenten.
>
>* De **Vertaalbaar** markering maakt automatisch vertaalregels voor u en vereist geen interventie.
>* De **Vertaalbaar** de vlag wordt slechts gebruikt als de configuratie van het Kader van de Integratie van de Vertaling wordt geplaatst aan **[Velden voor inhoudsmodellen inschakelen voor vertaling](/help/sites-cloud/administering/translation/integration-framework.md)**.
>* Het toelaten van deze optie in de configuratie van TIF zal om het even welke manueel-gecreeerde vertaalregels vervangen.|

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe u AEM vertaalregels kunt gebruiken om uw vertaalinhoud te identificeren. Nadat u dit document hebt gelezen, moet u:

* Begrijp wat de vertaalregels doen.
* U kunt uw eigen vertaalregels definiëren.

## Vertaalregels {#translation-rules}

Inhoudsfragmenten, die uw inhoud zonder kop vertegenwoordigen, kunnen veel informatie bevatten die is ingedeeld in gestructureerde velden. Afhankelijk van uw projectbehoeften is het waarschijnlijk dat niet alle velden in een inhoudsfragment moeten worden vertaald.

In de vertaalregels wordt aangegeven welke inhoud is opgenomen in of uitgesloten van vertaalprojecten. Wanneer de inhoud wordt vertaald, AEM de inhoud uitpakt of oogst die op deze regels wordt gebaseerd. Op die manier wordt alleen inhoud die moet worden vertaald naar de vertaaldienst verzonden.

De vertaalregels bevatten de volgende informatie:

* Het pad van de inhoud waarop de regel van toepassing is
   * De regel is ook van toepassing op de onderliggende elementen van de inhoud
* De namen van de eigenschappen die de te vertalen inhoud bevatten
   * Het bezit kan voor een specifiek middeltype of voor alle middeltypes specifiek zijn

Omdat de Modellen van het Fragment van de Inhoud, die de structuur van uw Inhoudsfragmenten bepalen, aan uw eigen project uniek zijn, is het essentieel aan opstellingsvertaalregels zodat AEM weet welke elementen van uw inhoudsmodellen moeten vertalen.

>[!TIP]
>
>Over het algemeen verschaft de contentarchitect de vertaalspecialist de **Eigenschapnaam** s van alle velden die nodig zijn voor vertaling. Deze namen zijn nodig om vertaalregels te configureren. Als vertaler [kan deze vinden **Eigenschapnaam** zoals uzelf](getting-started.md#content-modlels) zoals eerder beschreven in deze reis.

## Vertaalregels maken {#creating-rules}

Er kunnen meerdere regels worden gemaakt ter ondersteuning van complexe vertaalvereisten. Het ene project waaraan u werkt, vereist bijvoorbeeld dat alle velden van het model worden vertaald, maar dat andere alleen beschrijvingsvelden worden vertaald terwijl titels niet worden vertaald.

De vertaalregels worden ontworpen om dergelijke scenario&#39;s te behandelen. Nochtans in dit voorbeeld illustreren wij hoe te om regels tot stand te brengen door zich op een eenvoudige, enige configuratie te concentreren.

Er is een **Omzetconfiguratie** console beschikbaar voor het vormen van vertaalregels. Toegang tot dit bestand:

1. Navigeren naar **Gereedschappen** > **Algemeen**.
1. Selecteren **Omzetconfiguratie**.

In de **Omzetconfiguratie** UI, zijn er verscheidene opties beschikbaar voor uw vertaalregels. Hier benadrukken wij de meest noodzakelijke en typische stappen die voor een basisconfiguratie zonder kop worden vereist.

1. Selecteren **Context toevoegen** een pad toevoegen. Dit is het pad van de inhoud waarop de regel van toepassing is.
   ![Context toevoegen](assets/add-translation-context.png)
1. Gebruik de padbrowser om het gewenste pad te selecteren en selecteer **Bevestigen** opslaan. Onthoud dat Content Fragments, die inhoud zonder kop bevatten, zich doorgaans onder `/content/dam/<your-project>`.
   ![Het pad selecteren](assets/select-context.png)
1. Selecteer de context die u hebt gemaakt en selecteer **Bewerken**. Hierdoor wordt het **Editor voor omzettingsregels** om de eigenschappen te configureren.
   ![Editor voor vertaalregels](assets/translation-rules-editor.png)
1. Standaard worden alle configuraties overgenomen van het bovenliggende pad, in dit geval `/content/dam`. Schakel de optie uit **Overnemen van`/content/dam`** zodat kunt u extra gebieden aan de configuratie toevoegen.
1. Als deze optie is uitgeschakeld, onder de knop **Algemeen** in de lijst, voegt u de eigenschapnamen toe van de inhoudsfragmentmodellen die u gebruikt [eerder geïdentificeerd als velden voor vertaling.](getting-started.md#content-models)
   1. In de **Nieuwe eigenschap** voert u de naam van de eigenschap in. De opties **Vertalen** en **Overnemen** worden automatisch ingeschakeld.
   1. Selecteren **Toevoegen**.
   1. Herhaal deze stappen voor alle velden die u moet vertalen.
   1. Selecteren **Opslaan**.
      ![Eigenschap toevoegen](assets/add-property.png)

U hebt nu uw vertaalregels geconfigureerd.

## Geavanceerd gebruik {#advanced-usage}

Er zijn verscheidene extra eigenschappen die als deel van uw vertaalregels kunnen worden gevormd. Bovendien kunt u uw regels handmatig als XML opgeven, waardoor meer specificiteit en flexibiliteit mogelijk zijn.

Dergelijke functies zijn meestal niet nodig om uw inhoud zonder kop te lokaliseren, maar u kunt er meer over lezen in het dialoogvenster [Aanvullende bronnen](#additional-resources) als u geïnteresseerd bent.

## Volgende functies {#what-is-next}

Nu u dit deel van de reis zonder kop hebt voltooid, moet u:

* Begrijp wat de vertaalregels doen.
* U kunt uw eigen vertaalregels definiëren.

Gebaseerd op deze kennis en doorgaan met uw AEM reis zonder hoofd door het document opnieuw te bekijken [Inhoud vertalen](translate-content.md) waar u leert hoe uw integratie en regels samenwerken om inhoud zonder kop te vertalen.

## Aanvullende bronnen {#additional-resources}

U kunt het beste naar het volgende gedeelte van de reis zonder kop gaan door het document te bekijken [Inhoud vertalen,](translate-content.md) hieronder volgen enkele aanvullende , optionele bronnen die dieper ingaan op bepaalde in dit document genoemde concepten , maar die niet nodig zijn om verder te gaan op de weg zonder kop .

* [Te vertalen inhoud identificeren](/help/sites-cloud/administering/translation/rules.md) - Leer hoe vertaalregels inhoud identificeren die moet worden vertaald.
