---
title: AS A CLOUD SERVICE SDK AEM
description: Een overzicht van de AEM as a Cloud Service Software Development Kit
exl-id: 06f3d5ee-440e-4cc5-877a-5038f9bd44c6
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1209'
ht-degree: 0%

---

# De AEM as a Cloud Service SDK {#aem-as-a-cloud-service-sdk}

De AEM as a Cloud Service SDK bestaat uit de volgende artefacten:

* **QuickStart Jar** - De AEM-runtime die wordt gebruikt voor lokale ontwikkeling
* **Java™ API Jar** - De Java™ Jar/Maven-afhankelijkheid die alle toegestane Java™ API&#39;s beschikbaar maakt die kunnen worden gebruikt om zich te ontwikkelen tegen AEM as a Cloud Service. Vroeger Uberjar genoemd
* **Javadoc Jar** - De javadocs voor de Java™ API Jar
* **Verzendgereedschappen** - De set gereedschappen die wordt gebruikt om zich te ontwikkelen tegen een lokale Dispatcher. Afzonderlijke artefacten voor UNIX® en vensters

Bovendien gebruiken sommige klanten die eerder met AEM 6.5 of vroegere versies werden opgesteld de artefacten hieronder. Als de lokale compilatie niet met Quickstart jar werkt, en u vermoedt het van de verwijdering van interfaces van AEM opgesteld as a Cloud Service is, contacteer de Steun van de Klant. Ze kunnen bepalen of u toegang nodig hebt. Het vereist veranderingen in het achterste eind.

* **6.5 Vervangen Java™ API-jar** - een extra reeks gekoppelde systemen die sinds AEM 6.5 zijn verwijderd
* **6.5 Vervangen Javadoc Jar** - de JavaDocs voor de extra reeks van verbonden

## Samenstellen voor de SDK {#building-for-the-sdk}

De AEM as a Cloud Service SDK wordt gebruikt om aangepaste code te maken en in te voeren. Zie de [AEM documentatie van het type Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html). Op een hoog niveau worden de volgende stappen uitgevoerd:

* **Code compileren**. Zoals verwacht, wordt de broncode gecompileerd die de resulterende inhoudspakketten produceert
* **Artefacten maken**. Tijdens dit proces worden artefacten gemaakt
* **Bundels analyseren**. Bundels worden geanalyseerd met de Maven analyzer plug-in, die zoekt naar problemen in het Maven-project, zoals ontbrekende afhankelijkheden
* **Artefacten implementeren**. Artefacten worden opgesteld aan de lokale server.

Dezelfde stappen worden uitgevoerd door Cloud Manager bij de implementatie naar Cloud Environment. Het uitvoeren bouwt plaatselijk voor lokale ontwikkeling en het testen toe. Ontwikkelaars kunnen op efficiënte wijze code- of structurele problemen detecteren voordat ze de broncontrole activeren en de implementatie van Cloud Manager activeren. Dit kan langer duren.

>[!NOTE]
>
>De AEM as a Cloud Service SDK moet worden gemaakt met een Java-verspreiding en -versie die worden ondersteund door [De buildomgeving van Cloud Manager](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md). AEM as a Cloud Service klanten kunnen het Oracle JDK downloaden van de [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) en u hebt tot september 2026 Java 11 Extended Support vanwege de licentievoorwaarden en ondersteuningsvoorwaarden van de Adobe voor de Oracle Java-technologie bij gebruik in Adobe Experience Manager-projecten.

## Toegang tot de AEM as a Cloud Service SDK {#accessing-the-aem-as-a-cloud-service-sdk}

* U kunt de Admin Console van de AEM controleren **Informatie over Adobe Experience Manager** om te zien welke versie van AEM u gebruikt.
* De gereedschappen QuickStart en Dispatcher kunnen als zip-bestand worden gedownload via het [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). De toegang tot de SDK-lijsten is beperkt tot mensen die omgevingen hebben op AEM Managed Services of AEM as a Cloud Service.
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
>Het versieitem voor de SDK moet overeenkomen met de versie van AEM as a Cloud Service. U kunt zien welke versie u gebruikt door u aan AEM aan te melden. Ga in de rechterbovenhoek van het scherm naar het vraagteken en selecteer **[!UICONTROL About Adobe Experience Manager]**.


## Een lokaal project vernieuwen met een nieuwe SDK-versie {#refreshing-a-local-project-with-a-new-skd-version}

Wanneer wordt het geadviseerd om het lokale project met een nieuwe SDK te verfrissen?

Adobe *beveelt aan* verververfrist deze na een maandelijks onderhoudrelease.

Het is *optioneel* om deze na elke dagelijkse onderhoudsrelease te vernieuwen. Klanten worden op de hoogte gesteld wanneer hun productieexemplaar is bijgewerkt naar een nieuwe AEM. Voor de dagelijkse onderhoudsreleases wordt niet verwacht dat de nieuwe SDK aanzienlijk is gewijzigd, zo niet in het geheel. Toch wordt aangeraden de lokale AEM ontwikkelaarsomgeving af en toe te vernieuwen met de nieuwste SDK en de aangepaste toepassing opnieuw te bouwen en te testen. De maandelijkse onderhoudrelease bevat meestal meer ingrijpende wijzigingen en ontwikkelaars dienen deze daarom direct te vernieuwen, opnieuw te bouwen en te testen.

Hieronder volgt de aanbevolen procedure voor het vernieuwen van een lokale omgeving:

1. Zorg ervoor dat om het even welke nuttige inhoud of aan het project in broncontrole of beschikbaar in een veranderbaar inhoudspakket voor recentere invoer wordt geëngageerd.
1. De inhoud van de test van de lokale ontwikkeling moet afzonderlijk worden opgeslagen zodat het niet als deel van de pijpleiding van de Manager van de Wolk wordt opgesteld. De reden is dat het alleen wordt gebruikt voor lokale ontwikkeling.
1. Stop de momenteel lopende snelstart.
1. Verplaats de `crx-quickstart` naar een andere map om veilig te bewaren.
1. Noteer de nieuwe AEM die in Cloud Manager wordt vermeld (deze versie wordt gebruikt om de nieuwe QuickStart Jar-versie aan te duiden die u verder kunt downloaden).
1. Download QuickStart JAR waarvan de versie overeenkomt met de versie AEM de versie van de Software Distribution Portal.
1. Maak een gloednieuwe map en plaats de nieuwe QuickStart Jar in de map.
1. Start de nieuwe QuickStart met de gewenste uitvoermodi (de naam van het bestand wijzigen of de uitvoeringsmodi doorgeven als `-r`).
   * Zorg ervoor dat er geen overblijfsel van de oude snelstart in de map aanwezig is.
1. Stel uw AEM toepassing samen.
1. Implementeer uw AEM toepassing op lokale AEM via Package Manager.
1. Installeer via Package Manager alle pakketten met verwisselbare inhoud die nodig zijn voor het testen van de lokale omgeving.
1. Ga verder met de ontwikkeling en implementeer indien nodig wijzigingen.

Als er inhoud is die met elke nieuwe AEM quickstart versie zou moeten worden geïnstalleerd, omvat het in een inhoudspakket en in de broncontrole van het project. Installeer de toepassing vervolgens telkens.

De aanbeveling is om de SDK regelmatig bij te werken (bijvoorbeeld om de twee weken) en elke dag een volledige lokale staat te verwijderen om niet per ongeluk afhankelijk te zijn van gegevens van een ander land in de toepassing.

Als u van CryptoSupport ([hetzij door de geloofsbrieven van de diensten van de Wolk of de dienst SMTP van de Post in AEM te vormen of door CryptoSupport API in uw toepassing te gebruiken](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/granite/crypto/CryptoSupport.html)), worden de gecodeerde eigenschappen versleuteld door een sleutel. Deze sleutel wordt automatisch gegenereerd bij de eerste start van een AEM. Terwijl de wolkenopstelling ervoor zorgt om automatisch het milieu-specifieke CryptoKey te hergebruiken, is het noodzakelijk om cryptokey in de lokale ontwikkelomgeving te injecteren.

AEM is standaard geconfigureerd om de sleutelgegevens op te slaan in de gegevensmap van een map, maar voor het gemak van hergebruik in de ontwikkeling kan het AEM worden geïnitialiseerd bij het eerste opstarten met &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;. Dit proces genereert de versleutelingsgegevens op &quot;`/etc/key`&quot;.

Voer de volgende stappen uit om inhoudspakketten met de gecodeerde waarden opnieuw te kunnen gebruiken:

* Wanneer u de lokale quickstart.jar voor het eerst start, moet u de onderstaande parameter toevoegen: &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;. Het wordt aanbevolen, maar optioneel, om deze altijd toe te voegen.
* De eerste keer dat u een instantie hebt gestart, maakt u een pakket met een filter voor de hoofdmap &quot;`/etc/key`&quot;. Dit pakket bevat het geheim dat opnieuw moet worden gebruikt in alle omgevingen waarvoor u ze opnieuw wilt gebruiken.
* Exporteer alle inhoud die geheimen bevat of zoek de gecodeerde waarden op via `/crx/de` zodat kunt u het aan het pakket toevoegen dat over installaties opnieuw wordt gebruikt.
* Wanneer u een nieuwe instantie opspant (om deze te vervangen door een nieuwe versie of als meerdere ontwikkelomgevingen de gegevens voor de test moeten delen), installeert u het pakket dat u in stap 2 en 3 maakt. Dit laat u de inhoud zonder de behoefte opnieuw gebruiken om manueel te vormen. De reden is dat de cryptosleutel nu synchroon is.
