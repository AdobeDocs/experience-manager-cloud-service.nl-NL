---
title: Browser voor opslagplaats
seo-title: Repository Browser
description: De repository browser biedt een alleen-lezen weergave in de repository voor alle omgevingen op auteur-, publicatie- en voorvertoningslagen.
seo-description: The repository browser provides a read-only view into the repository for all environments on author, publish, and preview tiers.
exl-id: 22473a97-8f7b-4014-b885-1233116aeda6
source-git-commit: db70857458722f870dad37ac2bee6a19ef54171e
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 1%

---

# Browser voor opslagplaats {#repository-browser}

>[!NOTE]
>
>De gegevensopslagbrowser is beschikbaar voor AEM versie 6582 en hoger.

>[!INFO]
>
>U kunt ook [deze clip](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/repository-browser.html) voor een snelle video-introductie over het gebruik van de Repository Browser voor foutopsporing AEM as a Cloud Service.

## Inleiding {#introduction}

De browser van de repository is een ontwikkelaarsprogramma dat een alleen-lezen weergave in de repository biedt voor alle omgevingen op auteur-, publicatie- en voorvertoningslagen. Het is ontworpen om het weergeven van de inhoudsstructuur te vergemakkelijken, zodat het eenvoudiger wordt om inhoud te zien of er fouten in op te sporen.

Toegankelijk vanuit de ontwikkelaarsconsole, kan deze worden gebruikt om door de opslagplaats van een auteur te bladeren of instantie voor een geselecteerde omgeving te publiceren.

### Toegangsvoorwaarden {#access-prerequisites}

Aan de volgende voorwaarden moet zijn voldaan om toegang te krijgen tot de Developer Console of de Repository-browser

Voor toegang tot Developer Console:

* Voor productieprogramma&#39;s moeten gebruikers beschikken over **Cloud Manager - Rol voor ontwikkelaars** in de Admin Console
* Voor zandbakprogramma&#39;s, is het beschikbaar aan om het even welke gebruiker met een productprofiel die hen toegang tot AEM as a Cloud Service geeft.

Voor toegang tot de Inhoudsbrowser:

* Gebruikers moeten beschikken over de **Cloud Manager - Ontwikkelaar** Rol in de Admin Console om instanties van Auteur en van de Publicatie te bekijken.
* Bovendien kunnen gebruikers met het AEM Gebruikersprofiel de browser van de gegevensopslagruimte met minimale leestoegang bekijken. de machtigingen van de gebruiker worden gerespecteerd bij het bladeren in de opslagplaats. Gebruikers met het productprofiel AEM Beheerders kunnen de browser van de opslagplaats bekijken met volledige leestoegang.

Voor meer informatie over het instellen van gebruikersmachtigingen raadpleegt u de [Documentatie voor Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html).

### De gegevensopslagbrowser starten {#launching-the-repository-browser}

De browser van de repository kan worden gestart door de onderstaande stappen te volgen.

1. Klik in Cloud Manager op de drie punten naast de omgeving van uw keuze en selecteer **Ontwerpconsole**

   ![repobrowser1](/help/implementing/developing/tools/assets/repobrowser1.png)

1. Klik op de knop **Browser voor opslagplaats** tab
1. Kies een pod die overeenkomt met de auteur, de publicatie of de voorvertoning door op de knop **Pod** vervolgkeuzelijst.

   ![repobrowser2](/help/implementing/developing/tools/assets/repobrowser2.png)

1. Start de browser van de repository door te klikken op de knop **Browser voor opslagplaats openen** koppeling verder omlaag. Hiermee wordt de browser gestart die hoort bij een representatieve instantie (pod) voor de gekozen laag. Hiermee wordt de browser gestart die hoort bij een representatieve instantie (pod) voor de gekozen laag. U kunt de specifieke pod voor die laag die wordt gestart niet besturen.

## Functies {#features}

### Navigeren door de hiërarchie {#navigate-the-hierarchy}

Met het navigatievenster aan de linkerkant kunt u de inhoudshiërarchie doorlopen. Als u op elke map of elk knooppunt klikt, worden de onderliggende items van de map of het knooppunt weergegeven. De mappenstructuur weerspiegelt de boomstructuur Sling Resource, een superset van de JCR Node-structuur.

![repobrowser3](/help/implementing/developing/tools/assets/repobrowser3.png)

Voor publiceren, door gebrek, zal Browser van de Bewaarplaats slechts openbare inhoud tonen, zo bepaalde omslagen zoals `/conf` of `/home` is niet zichtbaar.

Om deze locaties zichtbaar te maken, moet u de onderstaande procedure volgen.

1. Klik op de drie stippen naast de omgeving van uw keuze en selecteer **Toegang beheren**

   ![repobrowser7](/help/implementing/developing/tools/assets/repobrowser7.png)

1. Uw publicatieexemplaar zoeken en erop klikken

   ![repobrowser8](/help/implementing/developing/tools/assets/repobrowser8.png)

1. Maak een nieuw productprofiel voor publicatiebeheerders. In het onderstaande voorbeeld wordt het **DEV - AEM Beheerders publiceren**

   ![repobrowser9](/help/implementing/developing/tools/assets/repobrowser9.png)

1. Voeg het nieuwe productprofiel toe aan de gebruikers die overeenkomen met wie u via de browser van de publicatieruimte volledige toegang tot het nieuwe productprofiel kunt navigeren.

   ![repobrowser10](/help/implementing/developing/tools/assets/repobrowser10.png)

1. Wacht een paar minuten en open vervolgens de knop **AEM auteur** console
1. Voeg de groep die overeenkomt met het nieuwe productprofiel toe als lid van de beheerdersgroep. U kunt dit doen door op **Gereedschappen - Beveiliging - Groepen op auteur** klikt u vervolgens op de knop **beheerders** groep. Voeg vervolgens de groep toe zoals hieronder wordt weergegeven

   ![repobrowser11](/help/implementing/developing/tools/assets/repobrowser11.png)

1. De **beheerders** en de nieuwe **DEV - AEM Beheerders publiceren** groeperen zodat deze beschikbaar zijn voor publicatie

   ![repobrowser12](/help/implementing/developing/tools/assets/repobrowser12.png)

1. Als goede veiligheidspraktijk, verwijder nieuwe **DEV - AEM Beheerders publiceren** groep met beheerders in **auteur** de nieuwe groep is dus geïsoleerd om te publiceren

   ![repobrowser13](/help/implementing/developing/tools/assets/repobrowser13.png)

1. Alle mappen zijn zichtbaar wanneer u de browser van de repository opent voor een publicatie-instantie, inclusief `/home` en `/conf`.

### JCR-eigenschappen weergeven {#view-jcr-properties}

Als u op een knooppunt klikt, worden de JCR-eigenschappen van dat knooppunt weergegeven in het rechterdeelvenster van de navigatiefunctie. Hieronder ziet u een voorbeeld voor de `experience-fragments` knooppunt.

![repobrowser4](/help/implementing/developing/tools/assets/repobrowser41.png)

### Inhoud weergeven {#view-content}

U kunt de browser van de gegevensopslagruimte gebruiken om inhoud te bekijken door op een bron in het navigatievenster te klikken. Hiermee wordt een voorvertoning aan de rechterkant van de browser geopend onder een tab die naar de desbetreffende bron is vernoemd.

![repobrowser6](/help/implementing/developing/tools/assets/repobrowser61.png)

Voorvertoning is momenteel beschikbaar voor afbeeldingstypen in de onderstaande lijst:

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

U kunt ook de browser van de repository gebruiken om inhoud te downloaden. In het onderstaande voorbeeld kunt u op de knop **downloaden** koppeling om de `jcr:data` is gekoppeld aan het geselecteerde knooppunt. Deze eigenschap is beschikbaar voor alle binaire eigenschappen door aan de knoop te navigeren die de bezitsdefinitie bevat.

![repobrowser5](/help/implementing/developing/tools/assets/repobrowser52.png)
