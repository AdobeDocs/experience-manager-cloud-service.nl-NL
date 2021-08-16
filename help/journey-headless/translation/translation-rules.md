---
title: Vertaalregels configureren
description: Leer hoe u vertaalregels definieert om inhoud voor vertaling te identificeren.
source-git-commit: bc56a739d8aa59d8474f47c9882662baacfdda84
workflow-type: tm+mt
source-wordcount: '872'
ht-degree: 0%

---

# Vertaalregels configureren {#configure-translation-rules}

Leer hoe u vertaalregels definieert om inhoud voor vertaling te identificeren.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM hoofdloze vertaaltocht [Configureer de vertaalconnector](configure-connector.md) en u hebt geleerd hoe u uw vertaalconnector kunt installeren en configureren. Dit moet nu:

* Begrijp de belangrijke parameters van het Kader van de Integratie van de Vertaling in AEM.
* Uw eigen verbinding met uw vertaalservice instellen.

Nu uw schakelaar opstelling is, neemt dit artikel u door de volgende stap van het identificeren van welke inhoud u moet vertalen.

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

Omdat de Modellen van het Fragment van de Inhoud, die de structuur van uw Inhoudsfragmenten bepalen, aan uw eigen project uniek zijn, is het essentieel aan opstellingsvertaalregels zodat AEM weet welke elementen van uw inhoudsmodellen om moeten vertalen.

>[!TIP]
>
>Over het algemeen verschaft de contentarchitect de vertaalspecialist de **Eigenschapnaam** s van alle velden die nodig zijn voor vertaling. Deze namen zijn nodig om vertaalregels te configureren. Als vertaalspecialist, kunt u [deze **Naam van bezit** s zoals eerder beschreven in deze reis vinden.](getting-started.md#content-modlels)

## Vertaalregels maken {#creating-rules}

Er kunnen meerdere regels worden gemaakt ter ondersteuning van complexe vertaalvereisten. Het ene project waaraan u werkt, vereist bijvoorbeeld dat alle velden van het model worden vertaald, maar dat andere alleen beschrijvingsvelden worden vertaald terwijl titels niet worden vertaald.

De vertaalregels worden ontworpen om dergelijke scenario&#39;s te behandelen. Nochtans in dit voorbeeld illustreren wij hoe te om regels tot stand te brengen door zich op een eenvoudige, enige configuratie te concentreren.

Er is een **Vertaalconfiguratie** console beschikbaar voor het vormen van vertaalregels. Toegang tot dit bestand:

1. Navigeer naar **Extra** -> **Algemeen**.
1. Tik of klik op **Translation Configuration**.

In **Vertaalconfiguratie** UI, zijn er een aantal opties beschikbaar voor uw vertaalregels. Hier benadrukken wij de meest noodzakelijke en typische stappen die voor een basisconfiguratie zonder kop worden vereist.

1. Tik of klik op **Context toevoegen**, zodat u een pad kunt toevoegen. Dit is het pad van de inhoud waarop de regel van toepassing is.
   ![Context toevoegen](assets/add-translation-context.png)
1. Gebruik de padbrowser om het gewenste pad te selecteren en op de knop **Bevestigen** te klikken om op te slaan. Onthoud dat Content Fragments, die inhoud zonder kop bevatten, zich over het algemeen onder `/content/dam/<your-project>` bevinden.
   ![Het pad selecteren](assets/select-context.png)
1. AEM slaat de configuratie op.
1. U moet de context selecteren u enkel creeerde en dan tikken of **uitgeven** klikt. Dit opent **Vertaalregels Redacteur** om de eigenschappen te vormen.
   ![Editor voor vertaalregels](assets/translation-rules-editor.png)
1. Standaard worden alle configuraties overgeërfd van het bovenliggende pad, in dit geval `/content/dam`. Schakel de optie **Overnemen van`/content/dam`** uit om extra velden aan de configuratie toe te voegen.
1. Als deze optie is uitgeschakeld, voegt u onder de sectie **Algemeen** van de lijst de eigenschapsnamen toe van de modellen van het inhoudsfragment die u eerder hebt geïdentificeerd als velden voor vertaling.](getting-started.md#content-models)[
   1. Typ de naam van de eigenschap in het veld **Nieuwe eigenschap**.
   1. De opties **Translate** en **Inherit** worden automatisch ingeschakeld.
   1. Tik of klik op **Toevoegen**.
   1. Herhaal deze stappen voor alle velden die u moet vertalen.
   1. Tik of klik op **Opslaan**.
      ![Eigenschap toevoegen](assets/add-property.png)

U hebt nu uw vertaalregels geconfigureerd.

## Geavanceerd gebruik {#advanced-usage}

Er zijn een aantal extra eigenschappen die als deel van uw vertaalregels kunnen worden gevormd. Bovendien kunt u uw regels handmatig als XML opgeven, waardoor meer specificiteit en flexibiliteit mogelijk zijn.

Dergelijke functies zijn over het algemeen niet nodig om uw inhoud zonder kop te lokaliseren, maar u kunt over hen in de [Aanvullende Middelen](#additional-resources) sectie lezen als u geinteresseerd bent.

## Volgende functies {#what-is-next}

Nu u dit deel van de reis zonder kop hebt voltooid, moet u:

* Begrijp wat de vertaalregels doen.
* U kunt uw eigen vertaalregels definiëren.

Bouw op deze kennis voort en zet uw AEM onophoudelijke vertaalreis door het document [Inhoud vertalen](translate-content.md) opnieuw te bekijken, waar u zult leren hoe uw schakelaar en regels samenwerken om inhoud zonder kop te vertalen.

## Aanvullende bronnen {#additional-resources}

Hoewel u wordt aangeraden naar het volgende gedeelte van de reis zonder kop door het document [Inhoud vertalen te gaan,](translate-content.md) zijn de volgende aanvullende, optionele bronnen die een diepere duw doen op bepaalde in dit document vermelde concepten, maar die niet nodig zijn om verder te gaan op de tocht zonder kop.

* [Inhoud identificeren voor vertaling](/help/sites-cloud/administering/translation/rules.md)  - Leer hoe vertaalregels inhoud identificeren die moet worden vertaald.
