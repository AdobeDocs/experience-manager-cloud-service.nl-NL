---
title: AEM AS A CLOUD SERVICE SDK
description: Een overzicht van de AEM as a Cloud Service Software Development Kit
exl-id: 06f3d5ee-440e-4cc5-877a-5038f9bd44c6
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 8ccf03ebcb4a96b66a15dc9a1161a857888278a7
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# De SDK van AEM as a Cloud Service {#aem-as-a-cloud-service-sdk}

De SDK van AEM as a Cloud Service bestaat uit de volgende artefacten:

* **QuickStart Jar** - AEM runtime gebruikt voor lokale ontwikkeling
* **Java™ API Jar** - Java™ Jar/Maven Dependency die alle toegestane Java™ APIs blootstelt die kunnen worden gebruikt om tegen AEM as a Cloud Service te ontwikkelen. Vroeger Uberjar genoemd
* **Javadoc Jar** - de javadocs voor Java™ API Jar
* **Hulpmiddelen van Dispatcher** - de reeks hulpmiddelen die worden gebruikt om tegen Dispatcher plaatselijk te ontwikkelen. Afzonderlijke artefacten voor UNIX® en vensters

Bovendien gebruiken sommige klanten die eerder met AEM 6.5 of vroegere versies werden opgesteld de artefacten hieronder. Als de lokale compilatie niet met Quickstart jar werkt, en u vermoedt het van de verwijdering van interfaces van AEM opgesteld as a Cloud Service is, contacteer de Steun van de Klant. Ze kunnen bepalen of u toegang nodig hebt. Het vereist veranderingen in het achterste eind.

* **6.5 Vervangen Java™ API Jar** - een extra reeks verbonden die sinds AEM 6.5 zijn verwijderd
* **6.5 Vervangen Javadoc Jar** - JavaDocs voor de extra reeks van verbonden

>[!NOTE]
> 
> Er zijn verschillen tussen AEM as a Cloud Service en de SDK, op een aantal verschillende gebieden. Voor situaties waar snelle en herhalende veranderingen nodig zijn, heeft de Adobe snelle-ontwikkelomgevingen ingevoerd. Heb een blik bij [ Snelle Milieu&#39;s van de Ontwikkeling ](/help/implementing/developing/introduction/rapid-development-environments.md) voor meer informatie.

## Samenstellen voor de SDK {#building-for-the-sdk}

De SDK van AEM as a Cloud Service wordt gebruikt om aangepaste code te maken en te implementeren. Zie de [ AEM documentatie van het Archetype van het Project ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html). Op een hoog niveau worden de volgende stappen uitgevoerd:

* **compileert code**. Zoals verwacht, wordt de broncode gecompileerd die de resulterende inhoudspakketten produceert
* **bouwt artefacten**. Tijdens dit proces worden artefacten gemaakt
* **analyseert bundels**. Bundels worden geanalyseerd met de Maven analyzer plug-in, die zoekt naar problemen in het Maven-project, zoals ontbrekende afhankelijkheden
* **stelt artefacten** op. Artefacten worden opgesteld aan de lokale server.

Dezelfde stappen worden uitgevoerd door Cloud Manager bij de implementatie naar Cloud Environment. Het uitvoeren bouwt plaatselijk voor lokale ontwikkeling en het testen toe. Ontwikkelaars kunnen op efficiënte wijze code- of structuurproblemen detecteren voordat ze de broncontrole activeren en Cloud Manager-implementaties activeren. Dit kan langer duren.

>[!NOTE]
>
>AEM as a Cloud Service SDK zou met een distributie en een versie van Java moeten worden gebouwd die door [ wordt gesteund Cloud Manager bouwt milieu ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md). De klanten van AEM as a Cloud Service kunnen het Oracle JDK van het [ portaal van de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) downloaden en hebben Java 11 Uitgebreide Steun tot September 2026 toe te schrijven aan het verlenen van vergunningen en de steunvoorwaarden van de Adobe voor de technologie van Java van het Oracle wanneer gebruikt in de projecten van Adobe Experience Manager.

## De SDK van AEM as a Cloud Service openen {#accessing-the-aem-as-a-cloud-service-sdk}

* U kunt de Admin Console van de AEM **controleren Ongeveer Adobe Experience Manager** pictogram om de versie van AEM te weten te komen u op productie loopt.
* De QuickStart jar en de Hulpmiddelen van Dispatcher kunnen als zip dossier van het [ portaal van de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) worden gedownload. De toegang tot de SDK-lijsten is beperkt tot mensen die omgevingen hebben op AEM Managed Services of AEM as a Cloud Service.
* De Java™ API Jar en Javadoc Jar kunnen worden gedownload met behulp van geoorloofde gereedschappen, opdrachtregelprogramma&#39;s of met uw voorkeurs-IDE.
* De toegewezen projectruimten moeten verwijzen naar het volgende API Jar-pakket. Er moet ook worden verwezen naar de afhankelijkheid van subpakketruimten.

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
>Het versieitem voor de SDK moet overeenkomen met de versie van AEM as a Cloud Service. U kunt zien welke versie u gebruikt door u aan AEM aan te melden. Ga in de rechterbovenhoek van het scherm naar het vraagteken en selecteer **[!UICONTROL About Adobe Experience Manager]** .


## Een lokaal project vernieuwen met een nieuwe SDK-versie {#refreshing-a-local-project-with-a-new-skd-version}

Wanneer wordt het geadviseerd om het lokale project met een nieuwe SDK te verfrissen?

Adobe *adviseert* het verfrissen na een maandelijkse onderhoudsversie.

Het is *facultatief* om het na om het even welke dagelijkse onderhoudsversie te verfrissen. Klanten worden op de hoogte gesteld wanneer hun productieexemplaar is bijgewerkt naar een nieuwe AEM. Voor de dagelijkse onderhoudsreleases wordt niet verwacht dat de nieuwe SDK aanzienlijk is gewijzigd, zo niet in het geheel. Toch wordt aangeraden de lokale AEM ontwikkelaarsomgeving af en toe te vernieuwen met de nieuwste SDK en de aangepaste toepassing opnieuw te bouwen en te testen. De maandelijkse onderhoudrelease bevat meestal meer ingrijpende wijzigingen en ontwikkelaars dienen deze daarom direct te vernieuwen, opnieuw te bouwen en te testen.

Hieronder volgt de aanbevolen procedure voor het vernieuwen van een lokale omgeving:

1. Zorg ervoor dat om het even welke nuttige inhoud of aan het project in broncontrole of beschikbaar in een veranderbaar inhoudspakket voor recentere invoer wordt geëngageerd.
1. De inhoud van de test van de lokale ontwikkeling moet afzonderlijk worden opgeslagen zodat het niet als deel van de pijpleiding van Cloud Manager wordt opgesteld. De reden is dat het alleen wordt gebruikt voor lokale ontwikkeling.
1. Stop de momenteel lopende snelstart.
1. Verplaats de map `crx-quickstart` naar een andere map voor veilig beheer.
1. Noteer de nieuwe AEM die in Cloud Manager wordt vermeld (deze wordt gebruikt om de nieuwe QuickStart Jar-versie aan te duiden die u verder kunt downloaden).
1. Download QuickStart JAR waarvan de versie overeenkomt met de versie AEM de versie van de Software Distribution Portal.
1. Maak een gloednieuwe map en plaats de nieuwe QuickStart Jar in de map.
1. Start de nieuwe QuickStart met de gewenste uitvoermodi (wijzig de naam van het bestand of geef de uitvoeringsmodi door als `-r` ).
   * Zorg ervoor dat er geen overblijfsel van de oude snelstart in de map aanwezig is.
1. Stel uw AEM toepassing samen.
1. Implementeer uw AEM toepassing op lokale AEM via Package Manager.
1. Installeer via Package Manager alle pakketten met verwisselbare inhoud die nodig zijn voor het testen van de lokale omgeving.
1. Ga verder met de ontwikkeling en implementeer indien nodig wijzigingen.

Als er inhoud is die met elke nieuwe AEM quickstart versie zou moeten worden geïnstalleerd, omvat het in een inhoudspakket en in de broncontrole van het project. Installeer de toepassing vervolgens telkens.

De aanbeveling is om de SDK regelmatig bij te werken (bijvoorbeeld om de twee weken) en elke dag een volledige lokale staat te verwijderen om niet per ongeluk afhankelijk te zijn van gegevens van een ander land in de toepassing.

Als u van CryptoSupport ([ afhangt of door de geloofsbrieven van de diensten van de Wolk of de dienst van de Post te vormen SMTP in AEM of door CryptoSupport API in uw toepassing ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/granite/crypto/CryptoSupport.html) te gebruiken), worden de gecodeerde eigenschappen gecodeerd door een sleutel. Deze sleutel wordt automatisch gegenereerd bij de eerste start van een AEM. Terwijl de wolkenopstelling ervoor zorgt om automatisch het milieu-specifieke CryptoKey te hergebruiken, is het noodzakelijk om cryptokey in de lokale ontwikkelomgeving te injecteren.

Door gebrek, AEM wordt gevormd om de belangrijkste gegevens binnen de gegevensomslag van een omslag op te slaan, maar voor gemak van gemakkelijker hergebruik in ontwikkeling, kan het AEM proces bij eerste opstarten met &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;worden geïnitialiseerd. Dit proces produceert de encryptiegegevens bij &quot;`/etc/key`&quot;.

Voer de volgende stappen uit om inhoudspakketten met de gecodeerde waarden opnieuw te kunnen gebruiken:

* Wanneer u eerst omhoog lokale quickstart.jar begint, zorg ervoor om de hieronder parameter toe te voegen: &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;. Het wordt aanbevolen, maar optioneel, om deze altijd toe te voegen.
* De eerste keer u opende een instantie, creeer een pakket dat een filter voor de wortel &quot;`/etc/key`&quot;bevat. Dit pakket bevat het geheim dat opnieuw moet worden gebruikt in alle omgevingen waarvoor u ze opnieuw wilt gebruiken.
* Exporteer alle inhoud met geheimen die kan worden gewijzigd of zoek de gecodeerde waarden op met `/crx/de` , zodat u deze kunt toevoegen aan het pakket dat in de installaties opnieuw wordt gebruikt.
* Wanneer u een nieuwe instantie opspant (om deze te vervangen door een nieuwe versie of als meerdere ontwikkelomgevingen de gegevens voor de test moeten delen), installeert u het pakket dat u in stap 2 en 3 maakt. Dit laat u de inhoud zonder de behoefte opnieuw gebruiken om manueel te vormen. De reden is dat de cryptosleutel nu synchroon is.
