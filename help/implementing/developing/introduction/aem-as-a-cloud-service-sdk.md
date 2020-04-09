---
title: AEM as a Cloud Service SDK
description: In te vullen
translation-type: tm+mt
source-git-commit: f15d5087a1bcb7691e159db1a595f6cc20f2b2c6

---


# The AEM as a Cloud Service SDK {#aem-as-a-cloud-service-sdk}

De AEM als Cloud Service SDK bestaat uit de volgende artefacten:

* **QuickStart Jar** - De AEM-runtime die wordt gebruikt voor lokale ontwikkeling
* **Java API Jar** - De Java Jar/Maven-afhankelijkheid die alle toegestane Java API&#39;s beschikbaar maakt die kunnen worden gebruikt om zich te ontwikkelen tegen AEM als Cloud Service. Vroeger Uberjar genoemd
* **Javadoc Jar** - De javadocs voor de Java API Jar
* **Dispatcher Tools** - De set gereedschappen die wordt gebruikt om zich te ontwikkelen tegen Dispatcher lokaal. Afzonderlijke artefacten voor unix en vensters

Bovendien zullen sommige klanten die eerder met AEM 6.5 of vroegere versies werden opgesteld de artefacten hieronder gebruiken. Als de lokale compilatie niet werkt met de Quickstart-jar en u vermoedt dat dit te wijten is aan interfaces die zijn verwijderd uit AEM die als Cloud Service zijn geïmplementeerd, neemt u contact op met de Klantenondersteuning om te bepalen of u toegang nodig hebt. Dit zal veranderingen in het achterste eind vereisen.

* **6.5 Vervangen Java API Jar** - een extra set gekoppelde bestanden die zijn verwijderd sinds AEM 6.5
* **6.5 Vervangen Javadoc Jar** - de JavaDocs voor de extra reeks verbonden documenten

## De AEM benaderen als SDK van de Cloud Service {#accessing-the-aem-as-a-cloud-service-sdk}

* U kunt het pictogram **Over Adobe Experience Manager** van de AEM Admin Console controleren om te zien welke versie van AEM u uitvoert op productie.
* De hulpprogramma&#39;s quickstart jar en Dispatcher kunnen als zip-bestand worden gedownload van de [portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)Softwaredistributie. De toegang tot de SDK-aanbiedingen is beperkt tot gebruikers met AEM Managed Services of AEM als een Cloud Service-omgeving.
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

>[!NOTE] Het versieitem voor de SDK moet overeenkomen met de versie van AEM als Cloud Service. U kunt zien welke versie u gebruikt door u aan te melden bij AEM, naar het vraagteken in de rechterbovenhoek van het scherm te gaan en **[!UICONTROL Info over Adobe Experience Manager te selecteren]**

* De externe coördinaat van de beheerde opslagplaats waar het pakket wordt gehost, moet in het pombestand worden opgenomen.

```
<repository>
    <id>adobe-aem-releases</id>
    <name>Adobe AEM Repository</name>
    <url>https://downloads.experiencecloud.adobe.com/content/maven/public</url>
    <releases>
        <enabled>true</enabled>
        <updatePolicy>never</updatePolicy>
    </releases>
    <snapshots>
        <enabled>false</enabled>
    </snapshots>
</repository>
```

## Een lokaal project vernieuwen met een nieuwe SDK-versie {#refreshing-a-local-project-with-a-new-skd-version}

Wanneer wordt het geadviseerd om het lokale project met een nieuwe SDK te verfrissen?

Het wordt *aanbevolen* deze minstens na een maandelijkse onderhoudsrelease te vernieuwen.

Het is *optioneel* om deze na elke dagelijkse onderhoudsrelease te vernieuwen. Klanten worden op de hoogte gesteld wanneer hun productieexemplaar is bijgewerkt naar een nieuwe AEM-versie. Voor de dagelijkse onderhoudsreleases wordt niet verwacht dat de nieuwe SDK aanzienlijk zal zijn veranderd, zo niet in het geheel. Toch wordt aangeraden de lokale AEM-ontwikkelaarsomgeving af en toe te vernieuwen met de nieuwste SDK en de aangepaste toepassing opnieuw te bouwen en te testen. De maandelijkse onderhoudrelease bevat meestal meer ingrijpende wijzigingen en ontwikkelaars moeten deze daarom direct vernieuwen, opnieuw bouwen en testen.

Hieronder volgt de aanbevolen procedure voor het vernieuwen van een lokale omgeving:

1. Zorg ervoor dat om het even welke nuttige inhoud of geëngageerd aan het project in broncontrole of beschikbaar in een veranderbaar inhoudspakket voor recentere invoer wordt begaan
1. De inhoud van de test van de lokale ontwikkeling moet afzonderlijk worden opgeslagen zodat het niet als deel van de pijpleiding van de Manager van de Wolk wordt opgesteld. Dat komt omdat het alleen gebruikt moet worden voor lokale ontwikkeling
1. De huidige snelstart stoppen
1. De `crx-quickstart` map naar een andere map verplaatsen om deze veilig te bewaren
1. Let op de nieuwe AEM-versie, die wordt vermeld in Cloud Manager (deze versie wordt gebruikt om de nieuwe QuickStart Jar-versie te identificeren die verder moet worden gedownload).
1. Download QuickStart JAR waarvan de versie overeenkomt met de productie-AEM-versie van de Software Distribution Portal
1. Een gloednieuwe map maken en de nieuwe QuickStart Jar in de map plaatsen
1. Start de nieuwe QuickStart met de gewenste runmodes (bestand hernoemen of doorgeven in runmodes via `-r`).
   * Zorg ervoor dat er geen overblijfsel van de oude snelstart in de map aanwezig is.
1. Uw AEM-toepassing samenstellen
1. Implementeer uw AEM-toepassing op lokale AEM via PackageManager
1. Installeer via PackageManager alle verwisselbare inhoudspakketten die nodig zijn voor het testen van de lokale omgeving
1. De ontwikkeling voortzetten en veranderingen opstellen zoals nodig

Als er inhoud is die met elke nieuwe AEM quickstart versie zou moeten worden geïnstalleerd, omvat het in een inhoudspakket en in de broncontrole van het project. Installeer de toepassing vervolgens telkens.

De aanbeveling is om de SDK regelmatig bij te werken (bijvoorbeeld om de twee weken) en elke dag een volledige lokale staat te verwijderen om niet per ongeluk afhankelijk te zijn van gegevens van een ander land in de toepassing.

Als u van CryptoSupport ([of door de geloofsbrieven van de Diensten van de Wolk of de dienst SMTP van de Post in AEM te vormen of door CryptoSupport API in uw toepassing](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/crypto/CryptoSupport.html)te gebruiken) afhangt, zullen de gecodeerde eigenschappen door een sleutel worden gecodeerd die op de eerste aanvang van een milieu van AEM autogenerated is. Terwijl de cloudsetup ervoor zorgt dat automatisch de milieu-specifieke CryptoKey wordt hergebruikt, is het noodzakelijk om de cryptokey in de lokale ontwikkelomgeving te injecteren.

Standaard is AEM geconfigureerd om de sleutelgegevens op te slaan in de gegevensmap van een map, maar voor het gemak van hergebruik in ontwikkeling kan het AEM-proces bij het eerste opstarten worden geïnitialiseerd met &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;. Hierdoor worden de coderingsgegevens gegenereerd op &quot;`/etc/key`&quot;.

Als u inhoudspakketten met de gecodeerde waarden wilt hergebruiken, moet u de volgende stappen uitvoeren:

* Wanneer u eerst de lokale quickstart.jar start, moet u de onderstaande parameter toevoegen: &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;. Het wordt aanbevolen, maar optioneel, om deze altijd toe te voegen.
* De allereerste keer dat u een instantie opstart, maakt u een pakket dat een filter voor de hoofdmap &quot;`/etc/key`&quot; bevat. Dit zal het geheim houden om over alle milieu&#39;s opnieuw te worden gebruikt waarvoor u hen zou willen hergebruiken
* Exporteer alle gemuteerde inhoud die geheimen bevat of kijk naar de gecodeerde waarden door deze toe te voegen `/crx/de` aan het pakket dat opnieuw wordt gebruikt in alle installaties
* Wanneer u een nieuw exemplaar (of om met een nieuwe versie te vervangen of als veelvoudige dev milieu&#39;s de geloofsbrieven voor het testen zouden moeten delen) uitdraait, installeer het pakket dat in stap 2 en 3 wordt geproduceerd om de inhoud te kunnen opnieuw gebruiken zonder de behoefte om manueel aan te passen. Dit komt omdat de cryptokey nu synchroon is.
