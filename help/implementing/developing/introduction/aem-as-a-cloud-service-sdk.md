---
title: AEM as a Cloud Service SDK
description: Een overzicht van de AEM als Cloud Service Software Development Kit
exl-id: 06f3d5ee-440e-4cc5-877a-5038f9bd44c6
source-git-commit: a446efacb91f1a620d227b9413761dd857089c96
workflow-type: tm+mt
source-wordcount: '1175'
ht-degree: 1%

---

# De AEM als Cloud Service SDK {#aem-as-a-cloud-service-sdk}

De AEM als Cloud Service SDK bestaat uit de volgende artefacten:

* **QuickStart Jar**  - De AEM-runtime die wordt gebruikt voor lokale ontwikkeling
* **Java API Jar**  - De Java Jar/Maven-afhankelijkheid die alle toegestane Java API&#39;s beschikbaar maakt die kunnen worden gebruikt om zich te ontwikkelen tegen AEM als Cloud Service. Vroeger Uberjar genoemd
* **Javadoc Jar**  - De javadocs voor de Java API Jar
* **Dispatcher Tools** : de set gereedschappen die wordt gebruikt om zich te ontwikkelen tegen Dispatcher lokaal. Afzonderlijke artefacten voor unix en vensters

Bovendien zullen sommige klanten die eerder met AEM 6.5 of vroegere versies werden opgesteld de artefacten hieronder gebruiken. Als de lokale compilatie niet met Quickstart jar werkt en u vermoedt het toe te schrijven is aan interfaces die uit AEM die als Cloud Service worden opgesteld zijn verwijderd, bereik aan de Steun van de Klant om te bepalen als u toegang nodig hebt. Dit zal veranderingen in het achterste eind vereisen.

* **6.5 Verouderde Java API Jar**  - een extra set interfaces die zijn verwijderd sinds AEM 6.5
* **6.5 Vervangen Javadoc Jar**  - de JavaDocs voor de extra reeks van verbonden

## Samenstellen voor de SDK {#building-for-the-sdk}

De AEM als Cloud Service SDK wordt gebruikt om douanecode te bouwen en op te stellen. Raadpleeg de documentatie [AEM Projectarchetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=en) voor meer informatie. Op een hoog niveau worden de volgende stappen uitgevoerd:

* **Compileer code**. Zoals verwacht, wordt de broncode gecompileerd die de resulterende inhoudspakketten produceert
* **Artefacten** maken. Tijdens dit proces worden artefacten gemaakt
* **Analysebundels**. Bundels worden geanalyseerd met de Maven analyzer plug-in, die zoekt naar problemen in het Maven-project, zoals ontbrekende afhankelijkheden
* **Artefacten** implementeren. Artefacten worden opgesteld aan de lokale server.

Dezelfde stappen worden uitgevoerd door Cloud Manager bij de implementatie naar Cloud-omgevingen. Door het lokaal uitvoeren van builds kunnen lokale ontwikkelings- en testprocessen worden uitgevoerd, zodat ontwikkelaars code- of structuurproblemen efficiënt kunnen detecteren voordat ze de broncontrole vastleggen en de implementatie van Cloud Manager activeren. Dit kan langer duren.

## Toegang tot de AEM als Cloud Service SDK {#accessing-the-aem-as-a-cloud-service-sdk}

* U kunt het pictogram van de Admin Console van de AEM **Info over Adobe Experience Manager** controleren om de versie van AEM te weten te komen u op productie loopt.
* De hulpprogramma&#39;s quickstart jar en Dispatcher kunnen als zip-bestand worden gedownload van het [portal Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Let op: toegang tot de SDK-aanbiedingen is beperkt tot gebruikers met AEM Managed Services of AEM als Cloud Service.
* Java API Jar en Javadoc Jar kunnen via gefabriceerde hulpmiddelen, of bevellijn of met uw aangewezen winde worden gedownload.
* De toegewezen projectruimten moeten verwijzen naar het volgende API Jar-pakket. Naar deze afhankelijkheid moet ook worden verwezen in subpakketformulieren.

```
<dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>aem-sdk-api</artifactId>
  <version>2019.11.3006.20191108T223635Z-191201</version>
  <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>Het versieitem voor de SDK moet overeenkomen met de versie van AEM als Cloud Service. U kunt zien welke versie u gebruikt door u aan AEM aan te melden, dan naar het vraagteken in de hoogste juiste hoek van het scherm te gaan en **[!UICONTROL About Adobe Experience Manager]** te selecteren


## Een lokaal project vernieuwen met een nieuwe SDK-versie {#refreshing-a-local-project-with-a-new-skd-version}

Wanneer wordt het geadviseerd om het lokale project met een nieuwe SDK te verfrissen?

Het is *aanbevolen* om deze minstens na een maandelijkse onderhoudrelease te vernieuwen.

Het is *optioneel* om het na om het even welke dagelijkse onderhoudsversie te verfrissen. Klanten worden op de hoogte gesteld wanneer hun productieexemplaar is bijgewerkt naar een nieuwe AEM. Voor de dagelijkse onderhoudsreleases wordt niet verwacht dat de nieuwe SDK aanzienlijk zal zijn veranderd, zo niet in het geheel. Toch wordt aangeraden de lokale AEM ontwikkelaarsomgeving af en toe te vernieuwen met de nieuwste SDK en de aangepaste toepassing opnieuw te bouwen en te testen. De maandelijkse onderhoudrelease bevat meestal meer ingrijpende wijzigingen en ontwikkelaars moeten deze daarom direct vernieuwen, opnieuw bouwen en testen.

Hieronder volgt de aanbevolen procedure voor het vernieuwen van een lokale omgeving:

1. Zorg ervoor dat om het even welke nuttige inhoud of geëngageerd aan het project in broncontrole of beschikbaar in een veranderbaar inhoudspakket voor recentere invoer wordt begaan
1. De inhoud van de test van de lokale ontwikkeling moet afzonderlijk worden opgeslagen zodat het niet als deel van de pijpleiding van de Manager van de Wolk wordt opgesteld. Dat komt omdat het alleen gebruikt moet worden voor lokale ontwikkeling
1. De huidige snelstart stoppen
1. De map `crx-quickstart` naar een andere map verplaatsen om deze veilig te bewaren
1. Let op de nieuwe AEM die wordt vermeld in Cloud Manager (deze versie wordt gebruikt om de nieuwe QuickStart Jar-versie aan te duiden die u verder kunt downloaden).
1. Download QuickStart JAR waarvan de versie overeenkomt met de versie van Production AEM van het Software Distribution Portal
1. Een gloednieuwe map maken en de nieuwe QuickStart Jar in de map plaatsen
1. Start de nieuwe QuickStart met de gewenste runmodes (bestand hernoemen of doorgeven in runmodes via `-r`).
   * Zorg ervoor dat er geen overblijfsel van de oude snelstart in de map aanwezig is.
1. Uw AEM ontwikkelen
1. Implementeer uw AEM toepassing op lokale AEM via PackageManager
1. Installeer via PackageManager alle verwisselbare inhoudspakketten die nodig zijn voor het testen van de lokale omgeving
1. De ontwikkeling voortzetten en veranderingen opstellen zoals nodig

Als er inhoud is die met elke nieuwe AEM quickstart versie zou moeten worden geïnstalleerd, omvat het in een inhoudspakket en in de broncontrole van het project. Installeer de toepassing vervolgens telkens.

De aanbeveling is om de SDK regelmatig bij te werken (bijvoorbeeld om de twee weken) en elke dag een volledige lokale staat te verwijderen om niet per ongeluk afhankelijk te zijn van gegevens van een ander land in de toepassing.

Als u van CryptoSupport ([of door de geloofsbrieven van de Diensten van de Wolk of de dienst van de Post te vormen SMTP in AEM of door CryptoSupport API in uw toepassing te gebruiken ](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/adobe/granite/crypto/CryptoSupport.html)) afhangt, zullen de gecodeerde eigenschappen door een sleutel worden gecodeerd die autogenerated op de eerste aanvang van een AEM milieu is. Terwijl de cloudsetup ervoor zorgt dat automatisch de milieu-specifieke CryptoKey wordt hergebruikt, is het noodzakelijk om de cryptokey in de lokale ontwikkelomgeving te injecteren.

Standaard is AEM geconfigureerd om de sleutelgegevens op te slaan in de gegevensmap van een map, maar voor een gebruiksvriendelijker hergebruik in de ontwikkeling kan het AEM worden geïnitialiseerd bij het eerste opstarten met &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;. Hierdoor worden de versleutelingsgegevens gegenereerd op &quot;`/etc/key`&quot;.

Als u inhoudspakketten met de gecodeerde waarden wilt hergebruiken, moet u de volgende stappen uitvoeren:

* Wanneer u eerst de lokale quickstart.jar start, moet u de onderstaande parameter toevoegen: &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;. Het wordt aanbevolen, maar optioneel, om deze altijd toe te voegen.
* De allereerste keer dat u een instantie opstart, maakt u een pakket dat een filter bevat voor de hoofdmap &quot;`/etc/key`&quot;. Dit zal het geheim houden om over alle milieu&#39;s opnieuw te worden gebruikt waarvoor u hen zou willen hergebruiken
* Exporteer alle gemuteerde inhoud die geheimen bevat of kijk de gecodeerde waarden op via `/crx/de` om deze toe te voegen aan het pakket dat opnieuw wordt gebruikt in alle installaties
* Wanneer u een nieuw exemplaar (of om met een nieuwe versie te vervangen of als veelvoudige dev milieu&#39;s de geloofsbrieven voor het testen zouden moeten delen) uitdraait, installeer het pakket dat in stap 2 en 3 wordt geproduceerd om de inhoud te kunnen opnieuw gebruiken zonder de behoefte om manueel aan te passen. Dit komt omdat de cryptokey nu synchroon is.
