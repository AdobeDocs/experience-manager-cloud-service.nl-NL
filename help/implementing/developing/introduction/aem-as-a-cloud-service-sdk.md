---
title: AEM as a Cloud Service SDK
description: Een overzicht van de AEM as a Cloud Service Software Development Kit.
exl-id: 06f3d5ee-440e-4cc5-877a-5038f9bd44c6
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 82f5078740b2cf6ac481d83df40bbbc4fb3c1a77
workflow-type: tm+mt
source-wordcount: '1242'
ht-degree: 0%

---

# De AEM as a Cloud Service SDK {#aem-as-a-cloud-service-sdk}

De AEM as a Cloud Service SDK bestaat uit de volgende artefacten:

* **QuickStart Jar** - runtime van AEM die voor lokale ontwikkeling wordt gebruikt.
* **Java™ API Jar** - Java™ Jar/Maven Dependency die alle toegestane Java™ APIs blootstelt die kunnen worden gebruikt om tegen AEM as a Cloud Service te ontwikkelen. Vroeger Uberjar genoemd.
* **Javadoc Jar** - de documenten van Java voor Java™ API Jar.
* **Hulpmiddelen van Dispatcher** - de reeks hulpmiddelen die worden gebruikt om tegen Dispatcher plaatselijk te ontwikkelen. Afzonderlijke artefacten voor UNIX® en vensters.

Bovendien gebruiken sommige klanten die eerder werden geïmplementeerd met AEM 6.5 of eerdere versies de onderstaande artefacten. Neem contact op met de Klantenondersteuning als de lokale compilatie niet werkt met de QuickStart Jar en u vermoedt dat dit het gevolg is van het verwijderen van interfaces uit de in AEM geïmplementeerde as a Cloud Service. Ze kunnen bepalen of u toegang nodig hebt. Het vereist veranderingen in het achterste eind.

* **6.5 Vervangen Java™ API Jar** - een extra reeks verbonden die sinds AEM 6.5 zijn verwijderd.
* **6.5 Vervangen Java Jar** - Java docs voor de extra reeks verbonden.

>[!NOTE]
> 
> Er zijn verschillen tussen AEM as a Cloud Service en SDK op een aantal verschillende gebieden. Voor situaties waarin snelle en herhalende veranderingen nodig zijn, heeft Adobe Rapid Development Environment geïntroduceerd. Heb een blik bij [ Snelle Milieu&#39;s van de Ontwikkeling ](/help/implementing/developing/introduction/rapid-development-environments.md) voor meer informatie.

## Het gebouw voor de SDK {#building-for-the-sdk}

De AEM as a Cloud Service SDK wordt gebruikt om aangepaste code te maken en implementeren. Zie de [ documentatie van het Archetype van het Project van AEM ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/developing/archetype/using). Op een hoog niveau worden de volgende stappen uitgevoerd:

* **compileert code** - de code van Source wordt gecompileerd, die de resulterende inhoudspakketten produceert.
* **bouwt artefacten** - De artefacten worden gebouwd tijdens dit proces.
* **analyseert bundels** - de Bundels worden geanalyseerd gebruikend de Maven analyzer stop, die problemen in het Gemaakt project zoals ontbrekende gebiedsdelen zoekt.
* **stelt artefacten** op - de Artefacten worden opgesteld aan de lokale server.

Cloud Manager voert dezelfde stappen uit bij de implementatie naar Cloud-omgevingen. Het uitvoeren bouwt plaatselijk voor lokale ontwikkeling en het testen toe. Ontwikkelaars kunnen code- of structuurproblemen op efficiënte wijze identificeren voordat ze de broncontrole vastleggen. Dit proces helpt vertragingen te voorkomen die worden veroorzaakt door het activeren van Cloud Manager-implementaties, wat langer kan duren.

>[!NOTE]
>
>AEM as a Cloud Service SDK zou met een distributie en een versie van Java moeten worden gebouwd die door [ wordt gesteund Cloud Manager bouwt milieu ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md). De klanten van AEM as a Cloud Service kunnen Oracle JDK van het [ portaal van de Distributie van de Software downloaden ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Ze hebben tot september 2026 Java 11 Extended Support omdat Adobe licenties en ondersteuningsvoorwaarden voor Oracle Java-technologie in Adobe Experience Manager-projecten heeft .

## Toegang tot de AEM as a Cloud Service SDK {#accessing-the-aem-as-a-cloud-service-sdk}

* U kunt AEM Admin Console **controleren Ongeveer Adobe Experience Manager** pictogram om de versie van AEM te weten te komen u in productie loopt.
* QuickStart Jar en de Hulpmiddelen van Dispatcher kunnen als zip dossier van het [ Portaal van de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) worden gedownload. De toegang tot de SDK-lijsten is beperkt tot mensen die een omgeving hebben op AEM Managed Services of AEM as a Cloud Service.
* De Java™ API Jar en Javadoc Jar kunnen worden gedownload via Maven-gereedschappen, ofwel de opdrachtregel, ofwel de IDE van uw voorkeur.
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
>Het versieitem voor de SDK moet overeenkomen met de versie van AEM as a Cloud Service. U kunt zien welke versie u gebruikt door u aan te melden bij AEM. Ga in de rechterbovenhoek van het scherm naar het vraagteken en klik op **[!UICONTROL About Adobe Experience Manager]** .


## Een lokaal project vernieuwen met een nieuwe SDK-versie {#refreshing-a-local-project-with-a-new-skd-version}

Wanneer wordt het aanbevolen het lokale project te vernieuwen met een nieuwe SDK?

Adobe *adviseert* het verfrissen na een maandelijkse onderhoudsversie.

Het is *facultatief* om het na om het even welke dagelijkse onderhoudsversie te verfrissen. Klanten worden op de hoogte gesteld wanneer hun productieexemplaar is geüpgraded naar een nieuwe AEM-versie. Voor de dagelijkse onderhoudsbeurten wordt niet verwacht dat de nieuwe SDK aanzienlijk is veranderd, of helemaal niet. Toch raadt Adobe u aan de lokale AEM-ontwikkelaarsomgeving af en toe te vernieuwen met de nieuwste SDK, en de aangepaste toepassing opnieuw te bouwen en te testen. De maandelijkse onderhoudrelease bevat meestal meer ingrijpende wijzigingen en ontwikkelaars dienen deze daarom direct te vernieuwen, opnieuw te bouwen en te testen.

**om een lokaal project met een nieuwe versie van SDK te verfrissen:**

1. Zorg ervoor dat alle nuttige inhoud aan broncontrole wordt geëngageerd. Of, opgeslagen in een veranderbaar inhoudspakket voor recentere invoer.
1. De inhoud van de test van de lokale ontwikkeling moet afzonderlijk worden opgeslagen zodat het niet als deel van de pijpleiding van Cloud Manager wordt opgesteld. De reden is dat het alleen wordt gebruikt voor lokale ontwikkeling.
1. Stop de momenteel lopende snelstart.
1. Verplaats de map `crx-quickstart` naar een andere map voor veilig beheer.
1. Let op de nieuwe AEM-versie, die wordt vermeld in Cloud Manager (deze wordt gebruikt om de nieuwe QuickStart Jar-versie te identificeren die verder moet worden gedownload).
1. Download QuickStart Jar van wie versie de versie van de Productie AEM van de Portaal van de Distributie van de Software aanpast.
1. Maak een gloednieuwe map en plaats de nieuwe QuickStart Jar in de map.
1. Start de nieuwe QuickStart met de gewenste uitvoermodi (wijzig de naam van het bestand of geef de uitvoeringsmodi door als `-r` ).
Zorg ervoor dat er geen overblijfsel van de oude snelstart in de map aanwezig is.
1. Maak uw AEM-toepassing.
1. Implementeer uw AEM-toepassing via Package Manager op een lokale AEM.
1. Installeer via Package Manager alle pakketten met inhoud die u nodig hebt voor lokale omgevingstests.
1. Ga verder met de ontwikkeling en implementeer indien nodig wijzigingen.

Als er inhoud is die met elke nieuwe versie van AEM QuickStart zou moeten worden geïnstalleerd, omvat het in een inhoudspakket en in de broncontrole van het project. Installeer de toepassing vervolgens telkens.

Adobe raadt u aan de SDK regelmatig bij te werken, bijvoorbeeld om de twee weken. Gooi de volledige lokale staat dagelijks weg, zodat u niet per ongeluk afhankelijk bent van stateful gegevens in de toepassing.

Als u CryptoSupport for Cloud-services, SMTP Mail-configuratie of de CryptoSupport-API gebruikt, worden de gecodeerde eigenschappen beveiligd met een sleutel. Meer details zijn beschikbaar in de [ CryptoSupport API documentatie ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/granite/crypto/CryptoSupport.html). Deze sleutel wordt automatisch gegenereerd bij de eerste start van een AEM-omgeving. Terwijl de wolkenopstelling ervoor zorgt om automatisch het milieu-specifieke CryptoKey te hergebruiken, is het noodzakelijk om cryptokey in de lokale ontwikkelomgeving te injecteren.

Door gebrek, wordt AEM gevormd om de belangrijkste gegevens binnen de gegevensomslag van een omslag op te slaan, maar voor gemak van gemakkelijker hergebruik in ontwikkeling, kan het proces van AEM bij eerste opstarten met &quot;`-Dcom.adobe.granite.crypto.file.disable=true` worden geïnitialiseerd.&quot; Dit proces produceert de encryptiegegevens bij &quot;`/etc/key`&quot;.

**om inhoudspakketten opnieuw te gebruiken die de gecodeerde waarden bevatten:**

* Wanneer u eerst omhoog lokale quickstart.jar begint, zorg ervoor om de hieronder parameter toe te voegen: &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;. Adobe raadt u desgewenst aan de sjabloon altijd toe te voegen.
* De eerste keer u opende een instantie, creeer een pakket dat een filter voor de wortel &quot;`/etc/key`&quot; bevat. Dit pakket bevat het geheim dat opnieuw moet worden gebruikt in alle omgevingen waarvoor u ze opnieuw wilt gebruiken.
* Exporteer alle inhoud met geheimen die kan worden gewijzigd. Of u kunt de gecodeerde waarden opzoeken met behulp van `/crx/de` zodat u deze kunt toevoegen aan het pakket dat opnieuw wordt gebruikt in verschillende installaties.
* Wanneer u een nieuwe instantie opspant (om deze te vervangen door een nieuwe versie of als meerdere ontwikkelomgevingen de gegevens voor de test moeten delen), installeert u het pakket dat u in stap 2 en 3 maakt. Dit laat u de inhoud zonder de behoefte opnieuw gebruiken om manueel te vormen. De reden is dat de cryptosleutel nu synchroon is.

