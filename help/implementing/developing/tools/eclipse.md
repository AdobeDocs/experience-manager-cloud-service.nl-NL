---
title: AEM Developer Tools for Eclipse
description: Leer hoe u de AEM Developer Tools for Eclipse, een Eclipse-plug-in op basis van de Eclipse-plug-in voor Apache Sling, gebruikt.
exl-id: 7f9c0f99-e230-440a-8bc9-a0ab7465e3bf
feature: Developing
role: Admin, Architect, Developer
source-git-commit: ba42d58a4e55efdada35cc7706d736a7314ba743
workflow-type: tm+mt
source-wordcount: '1138'
ht-degree: 0%

---

# AEM Developer Tools for Eclipse{#aem-developer-tools-for-eclipse}

![&#x200B; Experience Manager Developer Tools for Eclipse logo &#x200B;](assets/eclipse-logo.png)

## Overzicht {#overview}

_Experience Manager de Hulpmiddelen van de Ontwikkelaar voor Verduistering_ is een stop van de Verduistering die op de [&#x200B; wordt gebaseerd de stop van de Verduistering voor Apache die &#x200B;](https://sling.apache.org/documentation/development/ide-tooling.html) onder Vergunning 2 wordt vrijgegeven Apache.

Het biedt verschillende functies die de ontwikkeling van AEM vereenvoudigen:

* Naadloze integratie met AEM-instanties via Eclipse Server Connector
* Synchronisatie voor zowel inhoud als OSGi-bundels
* Ondersteuning voor foutopsporing met functie voor hot-swapping van code
* Eenvoudige Bootstrap van AEM-projecten via een specifieke wizard voor het maken van projecten
* Eenvoudig bewerken van JCR-eigenschappen

## Vereisten {#requirements}

Voordat u de AEM Developer Tools kunt gebruiken, moet u:

* Download en installeer [&#x200B; Eclipse winde voor de Ontwikkelaars van Java™ van de Onderneming &lbrace;](https://www.eclipse.org/downloads/packages/).
* Vorm uw eclipse installatie om ervoor te zorgen dat u minstens 1 GB van heapgeheugen door uw `eclipse.ini` configuratiedossier te uitgeven zoals die in [&#x200B; wordt beschreven Veelgestelde vragen van de Verduistering.](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse%3F)

>[!NOTE]
>
>Op macOS, moet u **Eclipse.app** met de rechtermuisknop aanklikken, en dan selecteren **toont de Inhoud van het Pakket** om uw `eclipse.ini`**te vinden.**

## AEM Developer Tools for Eclipse installeren {#how-to-install-the-aem-developer-tools-for-eclipse}

Wanneer u aan de [&#x200B; vereisten &#x200B;](#requirements) hierboven hebt voldaan, kunt u de stop als volgt installeren:

1. Open de [&#x200B; Website van de Hulpmiddelen van de Ontwikkelaar van AEM &#x200B;](https://eclipse.adobe.com/).

<!-- had to update the link again - was https://eclipse.adobe.com/com.adobe.granite.ide.p2update-1.3.0.zip -->
<!-- RB: OLD URL was (https://eclipse.adobe.com/aem/dev-tools/) This URL is generating a 404 error in the experience-manager-cloud-service.en LinkCheckExl report . The website appears to be dead; no redirects at all. Clicking "Installation Link" does not do anything. Only the link "Download archive" works. The "Online Documentation" link just takes you to the AEM Docs home page. Not sure if this topic is still needed?? -->

1. Kopieer de **Verbinding van de Installatie**.

   U kunt ook een archief downloaden in plaats van de installatiekoppeling te gebruiken. Deze methode staat offlineinstallatie toe maar u ontvangt geen automatische updatedeclaraties op deze manier.

1. In Verduistering, open het **menu van de Hulp**.
1. Klik **installeer Nieuwe Software**.
1. Klik **toevoegen...**.
1. Op het **gebied van de Naam**, ga `AEM Developer Tools` in.
1. Op het **gebied van de Plaats**, kopieer de installatie URL.
1. Klik **toevoegen**.
1. Controle zowel **AEM** als **het Verdelen** stoppen.
1. Klik op **Next**.
1. In **installeer Details** venster, klik **daarna** opnieuw.
1. Accepteer de vergunningsovereenkomsten en klik **Afwerking**.
1. Klik **RestartNow** om Eclipse opnieuw te beginnen.

## Het AEM-perspectief {#the-aem-perspective}

In Eclipse, bepaalt het Perspectief de acties en de meningen beschikbaar binnen een venster en laat taakgerichte interactie met middelen in Verduistering toe. Voor meer details over Perspectief, zie de [&#x200B; documentatie van de Verduistering &#x200B;](https://help.eclipse.org/latest/index.jsp).

_de Ontwikkelingshulpmiddelen van Experience Manager voor Verduistering_ verstrekken een Perspectief van AEM dat u volledige controle over uw Projecten en instanties van AEM aanbiedt. Het AEM-perspectief openen:

1. Van de het menubar van de Verduistering, uitgezocht **Venster** Perspectief **>** Open Perspectief **>** Andere **.**
1. Selecteer **AEM** in de dialoog en klik **Open**.

![&#x200B; het perspectief van AEM in Verduistering &#x200B;](assets/eclipse-aem-perspective.png)

## Monster nemen van meermoduleproject {#sample-multi-module-project}

De _Hulpmiddelen van de Ontwikkelaar van Experience Manager voor Verduistering_ komt met een steekproef, multi-moduleproject dat u snel met een projectopstelling in Verduistering helpt omhoog krijgen. Het fungeert ook als gids voor beste praktijken voor verschillende functies van AEM. [&#x200B; leer meer over het Archetype van het Project &#x200B;](https://github.com/adobe/aem-project-archetype).

Ga als volgt te werk om het voorbeeldproject te maken:

1. In het **Dossier** > **Nieuw** > **het menu van het Project**, doorblader aan de **sectie van AEM** en selecteer **de Steekproef van AEM Multi-Module Project**.

   ![&#x200B; de Steekproef van AEM Multi-Module Project &#x200B;](assets/aem-sample-project.png)

1. Klik op **Next**.

   >[!NOTE]
   >
   >Deze stap kan even duren omdat m2eclipse de catalogi van archetype moet aftasten.

1. Kies `com.adobe.granite.archetypes : sample-project-archetype : <highest-number>` van het menu, dan klik **daarna**.

   ![&#x200B; Uitgezochte archetype versie &#x200B;](assets/select-archetype.png)

1. Geef de volgende velden op voor het voorbeeldproject:

   * **Naam**
   * **Identiteitskaart van de Groep**
   * **Artefact identiteitskaart**
   * **appId** - u kunt de **Geavanceerde** opties moeten uitbreiden om deze waarde te plaatsen.
   * **appTitle** - u kunt de **Geavanceerde** opties moeten uitbreiden om deze waarde te plaatsen.
   * **Pakket** - u kunt de **Geavanceerde** opties moeten uitbreiden om deze waarde te plaatsen.

   ![&#x200B; bepaalt archetype eigenschappen &#x200B;](assets/archetype-properties.png)

1. Klik op **Next**.

1. Vervolgens configureert u een AEM-server waarmee Eclipse verbinding maakt.

   Als u de functie voor foutopsporing wilt gebruiken, moet u AEM hebben gestart in de foutopsporingsmodus. Dit kan worden bereikt door het volgende toe te voegen aan de opdrachtregel:

   ```text
       -nofork -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=10123
   ```

   ![&#x200B; verbind met de server van AEM &#x200B;](assets/connect-server.png)

1. Klik **Afwerking**. De projectstructuur wordt gemaakt.

   >[!NOTE]
   >
   >Op een nieuwe installatie (meer specifiek, wanneer bepaalde gebiedsdelen nooit zijn gedownload) zou u het project kunnen krijgen dat met fouten wordt gecreeerd. In dit geval, volg de procedure die in [&#x200B; wordt beschreven het Oplossen van Ongeldige Definitie van het Project &#x200B;](#resolving-invalid-project-definition).

## Bestaande projecten importeren {#how-to-import-existing-projects}

U kunt de **Nieuwe eigenschap van het Project** gebruiken om de juiste structuur voor u tot stand te brengen:

1. Volg de instructies om tot het Project van de Monster van de a [&#x200B; Monster Multi-Module &#x200B;](#sample-multi-module-project) te leiden en u hebt de volgende die projecten voor u worden gecreeerd, die een gezonde scheiding van zorgen toelaten:

   * `PROJECT.ui.apps` voor `/apps` en `/etc` inhoud
   * `PROJECT.ui.content` for `/content` dat is gemaakt
   * `PROJECT.core` voor Java™-bundels (deze worden interessant wanneer u Java™-code wilt toevoegen)
   * `PROJECT.it.launcher` en `PROJECT.it.tests` voor integratietests

1. Vervang de inhoud van het `PROJECT.ui.apps` -project door de mappen `apps` en `etc` van het pakket:

   1. Vouw in het deelvenster Projectverkenner `PROJECT.ui.apps` > `src` > `main` > `content` > `jcr_root` > `apps` uit.
   1. Klik met de rechtermuisknop op de `apps` omslag en kies **Tonen in** > **Ontdekkingsreiziger van het Systeem**.
   1. Verwijder de mappen `apps` en `etc` die u nu moet zien en plaats hier de mappen `apps` en `etc` van het inhoudspakket.
   1. In Verduistering, klik het `PROJECT.ui.apps` project met de rechtermuisknop aan en kies **verfrissen**.

1. Doe dan het zelfde voor `PROJECT.ui.content` en vervang zijn inhoudsomslag met één van uw pakketten:

   1. Vouw in het deelvenster Projectverkenner `PROJECT.ui.content` > `src` > `main` > `content` > `jcr_root` > `content` uit.
   1. Klik de diepere inhoudsomslag met de rechtermuisknop aan en kies **Tonen in** > **Ontdekkingsreiziger van het Systeem**.
   1. Verwijder de inhoudsmap die u nu moet zien en plaats hier de inhoudsmap van het inhoudspakket.
   1. In Verduistering, klik het `PROJECT.ui.content` project met de rechtermuisknop aan en kies **verfrissen**.

1. Nu moet u de `filter.xml` dossiers van deze twee projecten bijwerken om aan de inhoud van uw inhoudspakket te beantwoorden. Open daartoe het `META-INF/vault/filter.xml` -bestand van het inhoudspakket in een aparte tekst-/code-editor.

   * Dit is een voorbeeld van hoe uw `filter.xml` -bestand eruit kan zien:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <workspaceFilter version="1.0">
       <filter root="/apps/foo"/>
       <filter root="/apps/foundation/components/bar"/>
       <filter root="/etc/designs/foo"/>
       <filter root="/content/foo"/>
       <filter root="/content/dam/foo"/>
       <filter root="/content/usergenerated/content/foo"/>
   </workspaceFilter>
   ```

1. Wat de inhoud van het pakket betreft dat in twee projecten is gesplitst, moet u deze filterregels ook in twee splitsen en de `filter.xml` -bestanden van de twee projecten dienovereenkomstig bijwerken.

   1. Open `PROJECT.ui.apps/src/main/content/META-INF/filter.xml` in Eclipse.
   1. Vervang de inhoud van het element `<workspaceFilter>` door de regels van het pakket die beginnen met `/apps` en `/etc`
      * Bijvoorbeeld:

        ```xml
        <?xml version="1.0" encoding="UTF-8"?>
        <workspaceFilter version="1.0">
           <filter root="/apps/foo"/>
           <filter root="/apps/foundation/components/bar"/>
           <filter root="/etc/designs/foo"/>
        </workspaceFilter>
        ```

   1. Open vervolgens `PROJECT.ui.content/src/main/content/META-INF/filter.xml` .
   1. Vervang de regels door de regels in het pakket die beginnen met `/content` .
      * Bijvoorbeeld:

        ```xml
        <?xml version="1.0" encoding="UTF-8"?>
        <workspaceFilter version="1.0">
           <filter root="/content/foo"/>
           <filter root="/content/dam/foo"/>
           <filter root="/content/usergenerated/content/foo"/>
        </workspaceFilter>
        ```

1. Zorg ervoor dat u al uw wijzigingen opslaat. U kunt deze nieuwe inhoud nu synchroniseren met uw AEM-exemplaar.

1. Controleer of in het deelvenster Servers de verbinding is gestart en start deze als dat niet het geval is.
1. Klik **Schoon en publiceer** pictogram.

Als u klaar bent, moet het pakket op de instantie worden uitgevoerd en als u het bestand opslaat, wordt elke wijziging automatisch gesynchroniseerd met de instantie.

Als u een pakket uit uw project wilt re-bouwen, klik `PROJECT.ui.apps` of `PROJECT.ui.content` met de rechtermuisknop aan en kies **Looppas zoals** > **Gemaakt installeert**.

Er is nu een doelmap gemaakt met de pakketmap in die map (bijvoorbeeld `PROJECT.ui.apps-0.0.1-SNAPSHOT.zip` genoemd).

## Problemen oplossen {#troubleshooting}

### Ongeldige projectdefinitie oplossen {#resolving-invalid-project-definition}

Om ongeldige gebiedsdelen en projectdefinitie op te lossen ga als volgt te werk:

1. Selecteer alle gemaakte projecten.
1. Klik met de rechtermuisknop.
1. In het contextmenu, uitgezochte **Gemaakt** > **Projecten van de Update**.
1. Controle **de Updates van de Kracht van Momentopname/Versies**.
1. Klik **OK**.

Eclipse downloadt de vereiste afhankelijkheden. Dit kan even duren.

## Meer informatie {#more-information}

Op de officiële Apache Sling IDE-website voor Eclipse vindt u nuttige informatie:

* [**Apache het Verdelen van winde tooling voor de Gids van de Gebruiker van de Verduistering** &#x200B;](https://sling.apache.org/documentation/development/ide-tooling.html), begeleidt deze documentatie u door de algemene concepten, serverintegratie, en plaatsingsmogelijkheden die door de Hulpmiddelen van de Ontwikkeling van AEM worden gesteund.
* De [&#x200B; sectie van het Oplossen van problemen &#x200B;](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting).
* De [&#x200B; Bekende lijst van kwesties &#x200B;](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues).

De volgende officiële [&#x200B; documentatie van de Verduistering &#x200B;](https://www.eclipse.org/) kan helpen aan opstelling uw milieu:

* [&#x200B; Begonnen het worden met Verduistering &#x200B;](https://eclipseide.org/getting-started/)
* [&#x200B; Eclipse Luna Help System &#x200B;](https://help.eclipse.org/latest/index.jsp)
* [&#x200B; Gemaakt Integratie (m2eclipse) &#x200B;](https://www.eclipse.org/m2e/)
