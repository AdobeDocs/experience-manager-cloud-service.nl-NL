---
title: Vertaalaansluiting configureren
description: Leer hoe u verbinding AEM maken met een vertaalservice.
source-git-commit: 22ca7c01bfddb407c119de7d9a4d105941772664
workflow-type: tm+mt
source-wordcount: '1083'
ht-degree: 0%

---

# Vertaalaansluiting configureren {#configure-connector}

Leer hoe u verbinding AEM maken met een vertaalservice.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM hoofdloze lokalisatietraject, [Aan de slag met AEM hoofdloze lokalisatie](learn-about.md) hebt u geleerd hoe u uw inhoud zonder kop kunt ordenen en hoe AEM lokalisatieprogramma&#39;s werken. Nu moet u:

* Begrijp het belang van inhoudsstructuur voor localisatie.
* Begrijp hoe AEM inhoud zonder kop opslaat.
* Wees vertrouwd met AEM lokalisatieprogramma&#39;s.

Dit artikel bouwt op die grondbeginselen voort zodat kunt u de eerste configuratiestap nemen en de vertaaldienst opzetten, die u later in de reis zult gebruiken om uw inhoud te vertalen.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe te opstelling een AEM schakelaar aan uw gekozen vertaaldienst. Na het lezen moet u:

* Begrijp de belangrijke parameters van het Kader van de Integratie van de Vertaling in AEM.
* Uw eigen verbinding met uw vertaalservice instellen.

## Het vertaalintegratieframework {#tif}

AEM Translation Integration Framework kan worden geïntegreerd met vertaalservices van derden om de vertaling van AEM inhoud te ordenen. Het gaat om drie basisstappen.

1. Verbind met uw vertaaldienstverlener.
1. Creeer een configuratie van het Kader van de Integratie van de Vertaling.
1. Koppel de configuratie aan uw inhoud.

## Verbinding maken met een vertaalserviceprovider {#connect-translation-provider}

De eerste stap bestaat uit het kiezen van de vertaalservice die u wilt gebruiken. Er zijn vele keuzen voor mensen en machine vertaaldiensten beschikbaar aan AEM. Zie de sectie [Aanvullende bronnen](#additional-resources) voor een selectie van beschikbare opties.

De meeste providers zullen een vertaalpakket aanbieden dat moet worden geïnstalleerd. Voor deze reis, zullen wij de Vertaler van Microsoft gebruiken die van AEM voorziet van een proefvergunning uit-van-de-doos. Zie de sectie [Aanvullende bronnen](#additional-resources) voor meer informatie over deze provider.

Als u een andere leverancier kiest, moet u het aansluitingspakket installeren volgens de instructies van de vertaalservice.

>[!NOTE]
>
>Het gebruiken van de uit-van-de-doos Vertaler van Microsoft in AEM vereist geen extra opstelling en werkt zoals-is zonder extra schakelaarconfiguratie.
>
>Als u ervoor kiest om de schakelaar van de Vertaler van Microsoft voor testdoeleinden te gebruiken, te hoeven u niet om de stappen in de volgende twee secties uit te voeren, maar wordt geadviseerd om hen te lezen zodat u vertrouwd bent voor wanneer u uw aangewezen schakelaar moet aansluiten.
>
>De proefvergunning van de schakelaar van de Vertaler van Microsoft is niet voorgenomen voor productiedoeleinden en als u besluit om het vergunning te verlenen, zult u de volgende stappen moeten volgen die in [de sectie van Aanvullende Middelen](#additional-resources) aan het eind van dit document worden gedetailleerd om die vergunning te vormen.

## Een configuratie voor vertaalintegratie maken {#create-config}

Eerst moet u een configuratie van het vertaalintegratieframework maken om op te geven hoe u uw inhoud wilt vertalen. De configuratie bevat de volgende informatie:

* Welke vertaalserviceprovider moet worden gebruikt
* Of het vertalen van mensen of machines moet worden uitgevoerd
* Of andere inhoud die aan het inhoudsfragment is gekoppeld, zoals tags, moet worden vertaald

Een nieuwe vertaalconfiguratie maken:

1. Klik of tik in het algemene navigatiemenu op **Gereedschappen** -> **Cloud Services** -> **Vertaal Cloud Services**.
1. Navigeer naar de plaats waar u de configuratie in uw inhoudsstructuur wilt maken. Dit is vaak gebaseerd op een bepaald project of kan globaal zijn.
   * In dit geval zou een configuratie globaal kunnen worden gemaakt om op alle inhoud, of enkel voor het WKND project van toepassing te zijn.

   ![Locatie vertaalconfiguratie](assets/translation-configuration-location.png)

1. Geef de volgende informatie op in de velden en klik of tik op **Maken**.
   1. Selecteer **Configuratietype** in de vervolgkeuzelijst. Selecteer **Translation Integration** in de lijst.
   1. Ga **Titel** voor uw configuratie in. De **Title** identificeert de configuratie in de **Cloud Services** console evenals in de drop-down lijsten van het paginabezit.
   1. Typ desgewenst een **Naam** die u wilt gebruiken voor het opslagknooppunt dat de configuratie opslaat.

   ![Vertaalconfiguratie maken](assets/create-translation-configuration.png)

1. Tik of klik op **Maken** en het venster **Configuratie bewerken** verschijnt waar u de configuratie-eigenschappen kunt configureren.

1. Inhoudsfragmenten worden opgeslagen als elementen in AEM. Tik of klik op het tabblad **Middelen**.

![Eigenschappen van vertaalconfiguratie](assets/translation-configuration.png)

1. Geef de volgende informatie op.

   1. **Omzettingsmethode**  - Selecteer  **Machine** Translation of  **Human** Translation, afhankelijk van uw vertaalbureau. In het kader van deze reis zullen we kiezen voor automatische vertaling.
   1. **Vertaalproviders**  - Selecteer in de lijst de aansluiting die u voor uw vertaalservice hebt geïnstalleerd.
   1. **Inhoudscategorie**  - Selecteer de meest geschikte categorie om de vertaling beter te richten (alleen voor automatische vertaling).
   1. **Elementen**  van inhoudsfragmenten omzetten - ???
   1. **Elementen**  vertalen - Schakel deze optie in om de elementen te vertalen.
   1. **Metagegevens**  vertalen - Controleer dit om metagegevens van elementen te vertalen.
   1. **Tags**  vertalen: schakel deze optie in om codes te vertalen die aan het element zijn gekoppeld.
   1. **Automatisch omzetten**  - Schakel deze eigenschap in als u wilt dat vertalingen automatisch naar de vertaalservice worden verzonden.

1. Tik of klik op **Opslaan en sluiten**.

U hebt nu de schakelaar aan uw vertaaldienst gevormd.

## De configuratie koppelen aan uw inhoud {#associate}

AEM is een flexibel en krachtig hulpmiddel en steunt veelvoudige, gelijktijdige vertaaldiensten via veelvoudige schakelaars en veelvoudige configuraties. Het plaatsen van dit omhoog is voorbij het werkingsgebied van deze reis, maar betekent dat u moet specificeren welke schakelaars en configuratie zouden moeten worden gebruikt om uw inhoud te vertalen.

Navigeer hiertoe naar de hoofdtaalmap van de inhoud. Voor ons voorbeelddoel is dit

```text
/content/dam/<your-project>/en
```

1. Ga naar de globale navigatie en ga naar **Navigation** -> **Middelen** -> **Bestanden**.
1. Selecteer in de middelenconsole de hoofdtaal die u wilt configureren en klik of tik op **Eigenschappen**.
1. Tik of klik op het tabblad **Cloud Services**.
1. Onder **Cloud Service Configurations** in **Add Configuratie** dropdown, selecteer uw schakelaar. Het zou in dropdown moeten verschijnen wanneer u zijn pakket zoals [eerder beschreven ](#connect-translation-provider) hebt geïnstalleerd.
1. Onder **Cloud Service Configurations** in **Add Configuratie** dropdown, selecteer ook uw configuratie.
1. Tik of klik op **Opslaan en sluiten**.

![Cloudserviceconfiguraties selecteren](assets/select-cloud-service-configurations.png)

## Volgende functies {#what-is-next}

Nu u dit gedeelte van de reis zonder kop hebt voltooid, moet u:

* Begrijp de belangrijke parameters van het Kader van de Integratie van de Vertaling in AEM.
* Uw eigen verbinding met uw vertaalservice instellen.

Voortbouwen op deze kennis en doorgaan met uw AEM tocht naar een hoofdloze lokalisatie door het document [vertaalregels configureren](translation-rules.md) opnieuw te bekijken, waarin u leert hoe u kunt definiëren welke inhoud moet worden vertaald.

## Aanvullende bronnen {#additional-resources}

Terwijl wordt geadviseerd dat u zich op het volgende deel van de hoofdloze lokalisatietraject door het document [te herzien vertaalregels ](translation-rules.md) vormt zijn het volgende enkele extra, facultatieve middelen die een diepere duik op sommige die concepten in dit document worden vermeld, maar zij worden niet vereist om op de headless reis verder te gaan.

* [Het Vormen van het Kader](/help/sites-cloud/administering/translation/integration-framework.md)  van de Integratie van de Vertaling - leer hoe te om het Kader van de Integratie van de Vertaling te vormen om met de diensten van de derdevertaling te integreren.
* [Verbinding maken met Microsoft Translator](/help/sites-cloud/administering/translation/connect-ms-translator.md)  - AEM biedt een proefaccount voor Microsoft Translation voor testdoeleinden.
