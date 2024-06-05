---
title: Vertaalregels configureren
description: Leer hoe u vertaalregels definieert om inhoud voor vertaling te identificeren.
index: true
hide: false
hidefromtoc: false
exl-id: 831009b8-8e09-4b0f-b0fd-4e21221c1455
solution: Experience Manager Sites
feature: Translation
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---

# Vertaalregels configureren {#configure-translation-rules}

Leer hoe u vertaalregels definieert om inhoud voor vertaling te identificeren.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM Sites-vertaalreis: [Vertaalaansluiting configureren](configure-connector.md) u leerde hoe te om uw vertaalschakelaar te installeren en te vormen en zou nu moeten:

* Begrijp de belangrijke parameters van het Kader van de Integratie van de Vertaling in AEM.
* Uw eigen verbinding met uw vertaalservice instellen.

Nu uw schakelaar opstelling is, neemt dit artikel u door de volgende stap van het identificeren van welke inhoud u moet vertalen.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe u AEM vertaalregels kunt gebruiken om uw vertaalinhoud te identificeren. Nadat u dit document hebt gelezen, moet u:

* Begrijp wat de vertaalregels doen.
* U kunt uw eigen vertaalregels definiëren.

## Vertaalregels {#translation-rules}

AEM Sites-pagina&#39;s kunnen veel informatie bevatten. Afhankelijk van uw projectbehoeften, is het waarschijnlijk dat niet alle informatie binnen een pagina moet worden vertaald.

In de vertaalregels wordt aangegeven welke inhoud is opgenomen in of uitgesloten van vertaalprojecten. Wanneer de inhoud wordt vertaald, AEM de inhoud uitpakt of oogst die op deze regels wordt gebaseerd. Op die manier wordt alleen inhoud die moet worden vertaald naar de vertaaldienst verzonden.

De vertaalregels bevatten de volgende informatie:

* Het pad van de inhoud waarop de regel van toepassing is
   * De regel is ook van toepassing op de onderliggende elementen van de inhoud
* De namen van de eigenschappen die de te vertalen inhoud bevatten
   * Het bezit kan voor een specifiek middeltype of voor alle middeltypes specifiek zijn

AEM leidt automatisch tot vertaalregels voor plaatspagina&#39;s, maar omdat de vereisten van elk project verschillend zijn, is het belangrijk dat u weet hoe te om de regels zoals vereist aan uw project te herzien en aan te passen.

## Vertaalregels maken {#creating-rules}

Er kunnen meerdere regels worden gemaakt ter ondersteuning van complexe vertaalvereisten. Het ene project waaraan u werkt, vereist bijvoorbeeld dat alle paginagegevens worden vertaald, maar op een andere pagina moeten alleen beschrijvingen worden vertaald terwijl titels onvertaald blijven.

De vertaalregels worden ontworpen om dergelijke scenario&#39;s te behandelen. Nochtans in dit voorbeeld illustreren wij hoe te om regels tot stand te brengen door zich op een eenvoudige, enige configuratie te concentreren.

Er is een **Omzetconfiguratie** console beschikbaar voor het vormen van vertaalregels.

Toegang tot dit bestand:

1. Navigeren naar **Gereedschappen** > **Algemeen**.
1. Selecteren **Omzetconfiguratie**.

AEM maakt automatisch vertaalregels voor alle inhoud. Deze regels weergeven:

1. Selecteer de `/content` context.
1. Selecteer op de werkbalk de optie **Bewerken**.
1. De redacteur van de Regels van de Vertaling opent met de regels die automatisch voor AEM creeerden `/content` pad.

   ![Editor voor vertaalregels](assets/translation-rules-editor.png)

1. De pagina-eigenschappen die worden vertaald, bevinden zich onder de **Algemeen** van de lijst. U kunt bestaande eigenschapsnamen toevoegen of bijwerken die u expliciet wilt opnemen in de vertaling.
   1. In de **Nieuwe eigenschap** voert u de naam van de eigenschap in. De opties **Vertalen** en **Overnemen** worden automatisch ingeschakeld.
   1. Selecteren **Toevoegen**.
   1. Herhaal deze stappen voor alle velden die u moet vertalen.
   1. Selecteren **Opslaan**.

U hebt nu uw vertaalregels geconfigureerd.

>[!NOTE]
>
>AEM maakt automatisch vertaalregels. Voor een eenvoudige vertaalopstelling of om een vertaalwerkschema te testen, is het niet noodzakelijk om nieuwe regels tot stand te brengen of zelfs de bestaande, automatisch gecreeerde regels te wijzigen. De details van deze stappen worden gepresenteerd om uit te leggen hoe de regels werken en om context te geven aan hoe AEM vertalingen verwerkt.

>[!TIP]
>
>Het is ook mogelijk om regels te maken alleen voor uw specifieke pad of project door te tikken op **Context toevoegen** in de console van de Configuratie van de Vertaling. Dit valt buiten het bereik van deze reis.

## Geavanceerd gebruik {#advanced-usage}

Er zijn verscheidene extra eigenschappen die als deel van uw vertaalregels kunnen worden gevormd. Bovendien kunt u uw regels handmatig als XML opgeven, waardoor meer specificiteit en flexibiliteit mogelijk zijn.

Dergelijke functies zijn meestal niet nodig om uw inhoud te lokaliseren, maar u kunt er in het dialoogvenster [Aanvullende bronnen](#additional-resources) als u geïnteresseerd bent.

## Volgende functies {#what-is-next}

Nu u dit deel van de AEM Sites-vertaalreis hebt voltooid, moet u:

* Begrijp wat de vertaalregels doen.
* U kunt uw eigen vertaalregels definiëren.

Gebaseerd op deze kennis en uw AEM Sites-vertaalreis voortzetten door het document opnieuw te bekijken [Inhoud vertalen](translate-content.md) waar u leert hoe uw schakelaar en regels samenwerken om inhoud te vertalen.

## Aanvullende bronnen {#additional-resources}

U kunt het beste naar het volgende gedeelte van de vertaalreis gaan door het document te bekijken [Inhoud vertalen,](translate-content.md) hieronder volgen enkele aanvullende , optionele bronnen die een dieper beeld geven van bepaalde in dit document genoemde concepten , maar die niet verplicht zijn om op de reis verder te gaan .

* [Te vertalen inhoud identificeren](/help/sites-cloud/administering/translation/rules.md) - Leer hoe vertaalregels inhoud identificeren die moet worden vertaald.
