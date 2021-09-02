---
title: Vertaalregels configureren
description: Leer hoe u vertaalregels definieert om inhoud voor vertaling te identificeren.
index: true
hide: false
hidefromtoc: false
source-git-commit: 08127d72c84d6f47f5058ef631dc3128114f1953
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 0%

---


# Vertaalregels configureren {#configure-translation-rules}

Leer hoe u vertaalregels definieert om inhoud voor vertaling te identificeren.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM Sites-vertaalreis [Configureer de vertaalconnector](configure-connector.md) en u hebt geleerd hoe u uw vertaalconnector kunt installeren en configureren. Nu moet u:

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

Er is een **Vertaalconfiguratie** console beschikbaar voor het vormen van vertaalregels.

Toegang tot dit bestand:

1. Navigeer naar **Extra** -> **Algemeen**.
1. Tik of klik op **Translation Configuration**.

AEM maakt automatisch vertaalregels voor alle inhoud. Deze regels weergeven:

1. Selecteer de context `/content` en dan de **Edit** optie van de toolbar.
1. De Redacteur van de Regels van de Vertaling opent met de regels die automatisch voor `/content` weg AEM gecreeerd.

   ![Editor voor vertaalregels](assets/translation-rules-editor.png)

1. Pagina-eigenschappen die worden vertaald, bevinden zich onder de sectie **Algemeen** van de lijst. U kunt bestaande eigenschapsnamen toevoegen of bijwerken die u expliciet wilt opnemen in de vertaling.
   1. Typ de naam van de eigenschap in het veld **Nieuwe eigenschap**.
   1. De opties **Translate** en **Inherit** worden automatisch ingeschakeld.
   1. Tik of klik op **Toevoegen**.
   1. Herhaal deze stappen voor alle velden die u moet vertalen.
   1. Tik of klik op **Opslaan**.

U hebt nu uw vertaalregels geconfigureerd.

>[!NOTE]
>
>AEM maakt automatisch vertaalregels. Voor een eenvoudige vertaalopstelling of om een vertaalwerkschema te testen, is het niet noodzakelijk om nieuwe regels tot stand te brengen of zelfs de bestaande, automatisch gecreeerde regels te wijzigen. De details van deze stappen worden gepresenteerd om uit te leggen hoe de regels werken en om context te geven aan hoe AEM vertalingen verwerkt.

>[!TIP]
>
>Het is ook mogelijk om regels enkel voor uw bepaalde weg of project tot stand te brengen door te tikken of de **knoop toe te voegen Context** in de console van de Configuratie van de Vertaling te klikken. Dit valt buiten het bereik van deze reis.

## Geavanceerd gebruik {#advanced-usage}

Er zijn een aantal extra eigenschappen die als deel van uw vertaalregels kunnen worden gevormd. Bovendien kunt u uw regels handmatig als XML opgeven, waardoor meer specificiteit en flexibiliteit mogelijk zijn.

Dergelijke eigenschappen zijn over het algemeen niet nodig om begonnen te worden met het lokaliseren van uw inhoud, maar u kunt over hen in [Extra Middelen](#additional-resources) sectie lezen als u geinteresseerd bent.

## Volgende functies {#what-is-next}

Nu u dit deel van de AEM Sites vertaalreis hebt voltooid, moet u:

* Begrijp wat de vertaalregels doen.
* U kunt uw eigen vertaalregels definiëren.

Bouw op deze kennis voort en vervolg uw AEM Sites-vertaalreis door het document [Inhoud vertalen](translate-content.md) opnieuw te bekijken, waar u leert hoe uw connector en regels samenwerken om inhoud te vertalen.

## Aanvullende bronnen {#additional-resources}

Hoewel u wordt aangeraden naar het volgende gedeelte van de vertaalreis te gaan door het document [Inhoud vertalen,](translate-content.md) hieronder volgen enkele aanvullende, optionele bronnen die een diepere duw doen op bepaalde in dit document vermelde concepten, maar die niet nodig zijn om verder te gaan op de reis.

* [Inhoud identificeren voor vertaling](/help/sites-cloud/administering/translation/rules.md)  - Leer hoe vertaalregels inhoud identificeren die moet worden vertaald.
