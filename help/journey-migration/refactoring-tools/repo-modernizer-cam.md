---
title: Repository Modernizer (CAM)
description: Leer hoe u bestaande projectpakketten kunt herstructureren en compatibel kunt maken met de projectstructuur die is gedefinieerd voor Adobe Experience Manager as a Cloud Service.
feature: Migration
role: Admin
source-git-commit: 317ee65786d48d7b92d95c7c6b8782f617d6e346
workflow-type: tm+mt
source-wordcount: '1099'
ht-degree: 0%

---


# Repository Modernizer (CAM) {#repo-modernizer-cam}

Repository Modernizer is een hulpprogramma dat is ontwikkeld om bestaande projectpakketten te herstructureren door inhoud en code te scheiden in afzonderlijke pakketten, zodat deze compatibel zijn met de projectstructuur die voor Adobe Experience Manager as a Cloud Service is gedefinieerd.

## Inleiding {#introduction}

Adobe Experience Manager as a Cloud Service voegt veel nieuwe functies en mogelijkheden toe aan uw AEM-projecten. Er zijn echter enkele wijzigingen vereist voor Adobe Experience Manager Maven-projecten om compatibel te zijn met AEM Cloud Service. Op een hoog niveau, vereist AEM een scheiding van **inhoud** en **code** in discrete subpackages om de scheiding tussen veranderlijke en onveranderlijke inhoud te respecteren. Zie [ de Structuur van het Project van AEM ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=nl-NL) voor meer details over de nieuwe het projectstructuur van AEM voor Cloud Service.

Met de Repository Modernizer wordt een compatibele AEM Cloud Service-projectstructuur gemaakt door de volgende implementatiestructuur te maken:

- `ui.apps` -pakket wordt geïmplementeerd in `/apps` en bevat alle code

- `ui.content` wordt geïmplementeerd in runtime schrijfbare gebieden (bijvoorbeeld `/content` , `/conf` , `/home` of iets anders `/apps` ) en bevat alle inhoud en configuratie.

- `all` is een containerpakket dat de subpakketten `ui.apps` en `ui.content` bevat.

>[!NOTE]
>
> De structuur van het Project is gebaseerd op _Archetype 48_ voor pakketten en hun `pom.xml/filter.xml files`. Zie [ Archetype 48 ](https://github.com/adobe/aem-project-archetype) voor meer details.

De functie Repository Modernizer ondersteunt nu ook de volgende projecttypen:

- **MULTI_PROJECT**: Vertegenwoordigt een multimoduleproject zonder gemeenschappelijke ouderPOM, verzender, en alle modules.
- **SINGLE_PROJECT**: Vertegenwoordigt één enkel project.
- **NESTED_PROJECT**: Vertegenwoordigt een multimoduleproject met gemeenschappelijke ouderPOM, verzender, en alle modules.
- **MONOLITHIC_PROJECT**: Vertegenwoordigt een hoofdproject met één of meerdere subprojecten.

## De Repository Modernizer gebruiken {#using-repo-modernizer}

>[!VIDEO](https://video.tv.adobe.com/v/333057/?quality=12&learn=on)

- De modernizer van de Bewaarplaats wordt nu automatisch aangehaald door de Dienst Refactoring onder het lusje van de Baan Refactoring. De klanten moeten eenvoudig hun project uploaden en refactoring baan-geen extra opstelling teweegbrengen wordt vereist.

## Referentie foutcode

Als u een foutcode tegenkomt tijdens het gebruik van de Repository Modernizer, raadpleegt u de onderstaande tabel voor meer informatie en aanbevolen acties.

| Foutcode | Bericht | Beschrijving | Handeling door gebruiker vereist? |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | --------------------- |
| RM-100 | Fout bij het converteren van het OSGi config-bestand {0} naar de indeling .cfg.json. Valideer het bestaande configuratiebestand voordat u het opnieuw probeert. | Deze fout komt voor wanneer er een kwestie tijdens de transformatie van een OSGi config- dossier aan het.cfg.json formaat is. | Ja |
| RM-101 | Fout bij het kopiëren van inhoud van: {0} | Deze fout treedt op wanneer er een fout optreedt bij het kopiëren van inhoud van de opgegeven bron. | Nee |
| RM-102 | Fout bij het verplaatsen van bestand {0} van {1} naar {2}. | Deze fout treedt op wanneer er een probleem optreedt bij het verplaatsen van een bestand van de ene locatie naar de andere. | Nee |
| RM-103 | Kan opgegeven pad niet omzetten naar een geldig bestand: {0} | Deze fout treedt op wanneer het bestand niet op de opgegeven locatie wordt gevonden. | Nee |
| RM-104 | Er is een fout opgetreden tijdens het herhalen over de inhoud van {0}. | Deze fout treedt op tijdens het doorlopen van bestanden of mappen, wat een probleem met de toegang tot of verwerking van inhoud aangeeft. | Nee |
| RM-105 | Fout bij het parseren van het XML-bestand: {0}. Valideer het XML-bestand voordat u het opnieuw probeert. | Deze fout treedt op wanneer het parseren van het XML-bestand is mislukt. | Ja |
| RM-106 | Fout bij schrijven naar XML-bestand: {0}. | Deze fout treedt op wanneer er een probleem optreedt bij het schrijven naar het XML-bestand. | Nee |
| RM-107 | Geen inhoudspakketten gevonden in bestaand project: {0}. Controleer of het juiste project is geüpload. | Deze fout geeft aan dat er geen inhoudspakketten zijn gevonden in het bestaande project. | Ja |
| RM-108 | POM file not found at the expected path: {0}. Van het project of van de module POM wordt verwacht dat het dossier direct binnen zijn folder als kinddossier wordt gevestigd. | Deze fout treedt op wanneer het POM-bestand niet op de verwachte locatie wordt gevonden. | Ja |
| RM-109 | Fout bij het parseren van het bestand pom.xml: {0}. Valideer het pombestand voordat u het opnieuw probeert. | Deze fout treedt op wanneer er een probleem optreedt bij het parseren van het bestand pom.xml. | Ja |
| RM-110 | Fout bij het schrijven naar het bestand pom.xml: {0}. | Deze fout treedt op wanneer er een probleem optreedt bij het schrijven naar het pombestand. | Nee |
| RM-111 | Fout bij schrijven naar rapportbestand. | Deze fout treedt op wanneer er een fout optreedt tijdens het schrijven naar het rapportbestand. | Nee |
| RM-112 | Kan {0} niet vinden in Pom-bestand met gegevensopslagstructuur op ({1}) | Deze fout komt voor wanneer de verwachte configuratie niet in het het projectarchetype malplaatje van AEM wordt gevonden. | Nee |
| RM-113 | Fout bij het kopiëren van de AEM Project Archetype-sjablonen naar de bestemming. | Deze fout treedt op wanneer er een probleem is met het kopiëren van de AEM Project Archetype-sjablonen naar de bestemming. | Nee |
| RM-115 | Fout bij het maken van verbinding met Azure Blob Storage. | Deze fout treedt op wanneer er een probleem is met de verbinding met Azure Blob Storage. | Nee |
| RM-116 | Fout bij het uploaden van het bestand: {0} naar Azure Blob Storage. | Deze fout treedt op wanneer er een probleem optreedt bij het uploaden van een bestand naar Azure Blob Storage. | Nee |
| RM-117 | Fout bij het downloaden van bestand: {0} van Azure Blob Storage. | Deze fout treedt op wanneer er een probleem optreedt bij het downloaden van een bestand van Azure Blob Storage. | Nee |
| RM-118 | I/O-fout opgetreden bij het verwerken van: {0}. | Deze fout treedt op wanneer er een probleem is bij het lezen van of schrijven naar een projectbestand. | Nee |
| RM-119 | I/O-fout tijdens het archiveren van de resultaten voor uploaden naar Azure. | Deze fout treedt op wanneer er een fout optreedt bij het archiveren van de resultaten die door het proces worden gegenereerd. | Nee |
| RM-120 | I/O-fout tijdens het opheffen van het archiveren van het ZIP-bestand voor het aangeboden project. Controleer of het opgegeven zip-project geldig is. | Deze fout treedt op wanneer er een fout optreedt bij het ongedaan maken van het archiveren van het desbetreffende klantproject. | Ja |
| RM-121 | Fout bij schrijven naar configuratiebestand. | Deze fout treedt op wanneer er een fout optreedt tijdens het schrijven naar het configuratiebestand. | Nee |
| RM-122 | Niet-ondersteund aanvraagtype: {0}. | Deze fout treedt op wanneer het aanvraagtype niet door het systeem wordt ondersteund. Controleer het type aanvraag en probeer het opnieuw. | Nee |

## Prioriteiten van rapport met bevindingen

Wanneer u het onderzoeksrapport downloadt dat door het hulpmiddel van de Modernizer van de Bewaarplaats wordt geproduceerd, wordt elk vinden toegewezen a **prioriteit**. Deze prioriteiten helpen u de urgentie en de impact van elk vraagstuk te begrijpen:

| Prioriteit | Beschrijving |
| -------- | ----------------------------------------------------------------------------------------------- |
| CRITICAL | Moet worden opgelost om het project met succes te bouwen. |
| HOOG | Moet worden opgelost om ervoor te zorgen dat de functionaliteit in AEM niet wordt verbroken. |
| NORMAAL | Er moet een oplossing worden gevonden om de algehele saniteit en volledigheid van de modernisering te waarborgen. |
| LAAG | Voor handmatige verificatie; deze bevindingen zijn ter informatie en vereisen mogelijk geen onmiddellijke actie. |

>[!NOTE]
> 
>Om een soepel moderniserings- en implementatieproces te waarborgen, wordt eerst aanbevolen om bevindingen met hogere prioriteit te behandelen.
