---
title: Browser voor opslagplaats
seo-title: Repository Browser
description: De repository browser biedt een alleen-lezen weergave in de repository voor alle omgevingen op auteur-, publicatie- en voorvertoningslagen.
seo-description: The repository browser provides a read-only view into the repository for all environments on author, publish, and preview tiers.
exl-id: 22473a97-8f7b-4014-b885-1233116aeda6
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 0%

---

# Browser voor opslagplaats {#repository-browser}

>[!NOTE]
>
>De gegevensopslagbrowser is beschikbaar in AEM versie 6582 en hoger.

>[!INFO]
>
>U kunt [ deze klem ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/repository-browser.html) voor een snelle videoinleiding ook letten op hoe te om Browser van de Bewaarplaats te gebruiken om AEM as a Cloud Service te zuiveren.

## Inleiding {#introduction}

De verslagbrowser is een ontwikkelaarshulpmiddel dat een read-only mening in de bewaarplaats voor alle milieu&#39;s op auteur, publiceert, en voorproefrijen verstrekt. Deze is ontworpen om het weergeven van de inhoudsstructuur te vergemakkelijken, zodat u de inhoud beter kunt zien of fouten erin kunt opsporen.

Toegankelijk van [ AEM as a Cloud Service Developer Console ](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console), kan het worden gebruikt om de bewaarplaats van een auteur te doorbladeren of instantie voor een geselecteerd milieu te publiceren.

### Toegangsvoorwaarden {#access-prerequisites}

Aan de volgende voorwaarden moet zijn voldaan om toegang te krijgen tot de AEM as a Cloud Service Developer Console of de browser van de gegevensopslagruimte

Om tot AEM as a Cloud Service Developer Console toegang te hebben, zie {de toegang van 0} Developer Console [.](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console#developer-console-access)

Voor toegang tot de gegevensopslagbrowser gelden dezelfde voorwaarden als voor de AEM as a Cloud Service Developer Console (zie hierboven). U kunt als volgt de inhoud van de Repository Browser voor een bepaalde instantie weergeven:

* Instanties van de auteur: De gebruikers met het Profiel van het Product van de Gebruikers van AEM voor de **instantie van de Auteur** kunnen bewaarplaats browser met minimale leestoegang bekijken; de toestemmingen van de gebruiker worden gerespecteerd wanneer het doorbladeren van de bewaarplaats. Gebruikers met het AEM Beheerders-productprofiel kunnen de browser van de repository bekijken met volledige leestoegang.

* Publiceer instanties: De gebruikers met het Profiel van het Product van de Gebruikers van AEM voor **publiceren instantie** kunnen bewaarplaats browser met minimale leestoegang bekijken. Zonder deze productprofielset navigeert de gebruiker als een anonieme gebruiker en worden sommige paden niet weergegeven vanwege beperkte machtigingen.

Voor meer informatie over vestiging gebruikerstoestemmingen, zie de [ Documentatie van Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/requirements/users-and-roles.html).

### De gegevensopslagbrowser starten {#launching-the-repository-browser}

De browser van de repository kan worden gestart door de onderstaande stappen te volgen.

1. In Cloud Manager, klik de drie punten naast het milieu van uw keus, en selecteer **Developer Console**

   ![ repobrowser1 ](/help/implementing/developing/tools/assets/repobrowser1.png)

1. Daarna, klik Browser van de Bewaarplaats **lusje van 0}**
1. Kies om het even welke peul die aan auteur, publiceert, of voorproef door de **Peul** drop-down lijst te klikken.

   ![ repobrowser2 ](/help/implementing/developing/tools/assets/repobrowser2.png)

1. Lanceer bewaarplaatsbrowser door de **Open Browser van de Bewaarplaats** verbinding verder te klikken. De browser die correspondeert met een representatieve instantie (pod) voor de gekozen laag wordt gestart. U kunt de specifieke pod voor de laag die wordt gestart niet besturen.

## Functies {#features}

### Navigeren door de hiërarchie {#navigate-the-hierarchy}

U kunt het navigatievenster aan de linkerkant gebruiken om door de inhoudshiërarchie te navigeren. Als u op elke map of elk knooppunt klikt, worden de onderliggende items van dat knooppunt weergegeven. De mappenstructuur weerspiegelt de boomstructuur Sling Resource, een superset van de JCR Node-structuur.

![ repobrowser3 ](/help/implementing/developing/tools/assets/repobrowser3.png)

Alternatief, kunt u rechtstreeks aan een weg navigeren door het op het **gebied van de Weg** in te gaan, zoals hieronder getoond. Dit pad vergroot ook de locatie in de weergave met de inhoudshiërarchie aan de linkerkant.

![ repobrowser14 ](/help/implementing/developing/tools/assets/repobrowser14.png)

Wanneer u op een map aan de linkerkant klikt, wordt het veld Pad automatisch gevuld met de locatie. Deze functionaliteit is handig voor het kopiëren en plakken van de waarde voor later gebruik.

Wanneer u op een map klikt, wordt de URL dynamisch gewijzigd en wordt het pad naar die map opgenomen. Deze functionaliteit staat voor boekhandelbare URLs toe.

Voor publiceren, door gebrek, toont Browser van de Bewaarplaats slechts openbare inhoud, daarom zijn bepaalde omslagen zoals `/conf` of `/home` niet zichtbaar.

Ga als volgt te werk om deze locaties zichtbaar te maken.

1. Klik de drie punten naast het milieu van uw keus en selecteer **leiden Toegang**

   ![ repobrowser7 ](/help/implementing/developing/tools/assets/repobrowser7.png)

1. Uw publicatieexemplaar zoeken en erop klikken

   ![ repobrowser8 ](/help/implementing/developing/tools/assets/repobrowser8.png)

1. Een productprofiel maken voor publicatiebeheerders. In het voorbeeld hieronder, wordt het genoemd **DEV - de Beheerders van AEM publiceren**

   ![ repobrowser9 ](/help/implementing/developing/tools/assets/repobrowser9.png)

1. Voeg het nieuwe productprofiel toe aan de gebruikers die overeenkomen met wie u via de browser van de publicatieruimte volledige toegang tot het nieuwe productprofiel kunt navigeren.

   ![ repobrowser10 ](/help/implementing/developing/tools/assets/repobrowser10.png)

1. Wacht op een paar notulen, dan open de **auteur van AEM** console
1. Voeg de groep toe die aan het nieuwe productprofiel als lid van de groep van de beheerder door **Hulpmiddelen - Veiligheid - Groepen op auteur** beantwoordt, dan klikkend de **beheerders** groep. Voeg vervolgens de groep toe zoals hieronder wordt weergegeven

   ![ repobrowser11 ](/help/implementing/developing/tools/assets/repobrowser11.png)

1. Activeer de **beheerders** en nieuwe **DEV - de Beheerders van AEM publiceren** groep zodat zij bij publiceren beschikbaar worden

   ![ repobrowser12 ](/help/implementing/developing/tools/assets/repobrowser12.png)

1. Als goede veiligheidspraktijk, verwijder nieuwe **DEV - de Beheerders van AEM publiceren** groep van de groep van de beheerder op **auteur** zodat wordt de nieuwe groep geïsoleerd om te publiceren

   ![ repobrowser13 ](/help/implementing/developing/tools/assets/repobrowser13.png)

1. Alle mappen zijn zichtbaar wanneer u de browser van de repository opent voor een publicatie-instantie, inclusief `/home` en `/conf` .

### JCR-eigenschappen weergeven {#view-jcr-properties}

Wanneer u op een knooppunt klikt, worden de JCR-eigenschappen van dat knooppunt in het rechterdeelvenster van de navigatiefunctie weergegeven. Hieronder ziet u een voorbeeld van het knooppunt `experience-fragments` .

![ repobrowser4 ](/help/implementing/developing/tools/assets/repobrowser41.png)

### Inhoud weergeven {#view-content}

U kunt de browser van de repository gebruiken om inhoud weer te geven. Klik op een bron in het navigatievenster, zodat u een voorvertoning aan de rechterkant van de browser opent onder een tab die naar de respectievelijke bron wordt genoemd.

![ repobrowser6 ](/help/implementing/developing/tools/assets/repobrowser61.png)

Voorvertoning is beschikbaar voor de volgende afbeeldingstypen:

* apng
* avif
* gif
* jpeg
* png
* svg+xml
* webben
* bmp
* x-icon
* tiff

En voor de volgende op tekst gebaseerde mime-types:

* `"text/*"`
* `'application/javascript'`
* `'application/json'`
* `'application/x-sh'`

### Inhoud downloaden {#download-content}

U kunt ook de browser van de repository gebruiken om inhoud te downloaden. In het voorbeeld hieronder, kunt u de **download** verbinding drukken om `jcr:data` te downloaden verbonden aan de geselecteerde knoop. Deze eigenschap is beschikbaar voor alle binaire eigenschappen door aan de knoop te navigeren die de bezitsdefinitie bevat.

![ repobrowser5 ](/help/implementing/developing/tools/assets/repobrowser52.png)
