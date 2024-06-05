---
title: AEM Developer Tools for Eclipse
description: Leer hoe u de AEM Developer Tools for Eclipse, een Eclipse-plug-in op basis van de Eclipse-plug-in voor Apache Sling, gebruikt.
exl-id: 7f9c0f99-e230-440a-8bc9-a0ab7465e3bf
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1138'
ht-degree: 0%

---

# AEM Developer Tools for Eclipse{#aem-developer-tools-for-eclipse}

![Experience Manager Developer Tools for Eclipse-logo](assets/eclipse-logo.png)

## Overzicht {#overview}

_Experience Manager Developer Tools for Eclipse_ is een Eclipse-insteekmodule op basis van de [Eclipse-insteekmodule voor Apache Sling](https://sling.apache.org/documentation/development/ide-tooling.html) vrijgegeven onder de Apache-licentie 2.

Het biedt verschillende functies die AEM ontwikkeling vergemakkelijken:

* Naadloze integratie met AEM instanties via Eclipse Server Connector
* Synchronisatie voor zowel inhoud als OSGi-bundels
* Ondersteuning voor foutopsporing met functie voor hot-swapping van code
* Eenvoudige Bootstrap van AEM Projecten door middel van een specifieke Tovenaar van de Aanmaak van het Project
* Eenvoudig bewerken van JCR-eigenschappen

## Vereisten {#requirements}

Voordat u de AEM Developer Tools kunt gebruiken, moet u:

* Downloaden en installeren [Eclipse IDE voor Enterprise Java™-ontwikkelaars](https://www.eclipse.org/downloads/packages/).
* Configureer de lipse-installatie om ervoor te zorgen dat u ten minste 1 GB heapgeheugen hebt door uw `eclipse.ini` configuratiebestand als beschreven in [Veelgestelde vragen over Eclipse](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse).

>[!NOTE]
>
>In macOS moet u met de rechtermuisknop klikken **Eclipse.app** en selecteer vervolgens **Toon de Inhoud van het Pakket** om uw `eclipse.ini`**.**

## Hoe te om de Hulpmiddelen van de Ontwikkelaar van de AEM voor Eclipse te installeren {#how-to-install-the-aem-developer-tools-for-eclipse}

Wanneer u aan [vereisten](#requirements) hierboven kunt u de plug-in als volgt installeren:

1. Open de [Website AEM Developer Tools](https://eclipse.adobe.com/com.adobe.granite.ide.p2update-1.3.0.zip). <!-- RB: OLD URL was (https://eclipse.adobe.com/aem/dev-tools/) This URL is generating a 404 error in the experience-manager-cloud-service.en LinkCheckExl report . The website appears to be dead; no redirects at all. Clicking "Installation Link" does not do anything. Only the link "Download archive" works. The "Online Documentation" link just takes you to the AEM Docs home page. Not sure if this topic is still needed?? -->

1. De **Installatiekoppeling**.

   U kunt ook een archief downloaden in plaats van de installatiekoppeling te gebruiken. Deze methode staat offlineinstallatie toe maar u ontvangt geen automatische updatedeclaraties op deze manier.

1. Open in Eclipse de **Help** -menu.
1. Klikken **Nieuwe software installeren**.
1. Klikken **Toevoegen...**.
1. In de **Naam** veld, Enter `AEM Developer Tools`.
1. In de **Locatie** , kopieert u de installatie-URL.
1. Klikken **Toevoegen**.
1. Beide controleren **AEM** en **Sling** plug-ins.
1. Klik op **Next**.
1. In de **Details installeren** venster, klikt u op **Volgende** opnieuw.
1. Accepteer de licentieovereenkomsten en klik op **Voltooien**.
1. Klikken **Opnieuw startenNu** om Eclipse opnieuw te starten.

## Het AEM perspectief {#the-aem-perspective}

In Eclipse, bepaalt het Perspectief de acties en de meningen beschikbaar binnen een venster en laat taakgerichte interactie met middelen in Verduistering toe. Zie voor meer informatie over Perspectief de [Eclipse-documentatie.](https://help.eclipse.org/latest/index.jsp)

_Experience Manager Development Tools for Eclipse_ Geef een AEM perspectief dat u volledige controle over uw AEM Projecten en instanties biedt. Het AEM perspectief openen:

1. Selecteer in de menubalk Eclipse de optie **Venster** > **Perspectief** > **Perspectief openen** > **Overige**.
1. Selecteren **AEM** in het dialoogvenster en klik op **Openen**.

![Het AEM perspectief in Eclipse](assets/eclipse-aem-perspective.png)

## Monster nemen van meermoduleproject {#sample-multi-module-project}

De _Experience Manager Developer Tools for Eclipse_ komt met een steekproef, multi-moduleproject dat u snel met een projectopstelling in Verduistering helpt te versnellen. Het dient ook als gids voor beste praktijken aan verscheidene AEM eigenschappen. [Meer informatie over de projectarchetype](https://github.com/adobe/aem-project-archetype).

Ga als volgt te werk om het voorbeeldproject te maken:

1. In de **Bestand** > **Nieuw** > **Project** , bladert u naar de **AEM** en selecteert u **AEM Monster nemen van meermoduleproject**.

   ![AEM Monster nemen van meermoduleproject](assets/aem-sample-project.png)

1. Klik op **Next**.

   >[!NOTE]
   >
   >Deze stap kan even duren omdat m2eclipse de catalogi van archetype moet aftasten.

1. Kies `com.adobe.granite.archetypes : sample-project-archetype : <highest-number>` in het menu en klik vervolgens op **Volgende**.

   ![Versie van archetype selecteren](assets/select-archetype.png)

1. Geef de volgende velden op voor het voorbeeldproject:

   * **Naam**
   * **Groep-id**
   * **Artefact-id**
   * **appId** - Het kan nodig zijn om de **Geavanceerd** opties om deze waarde in te stellen.
   * **appTitle** - Het kan nodig zijn om de **Geavanceerd** opties om deze waarde in te stellen.
   * **Pakket** - Het kan nodig zijn om de **Geavanceerd** opties om deze waarde in te stellen.

   ![Eigenschappen archetype definiëren](assets/archetype-properties.png)

1. Klik op **Next**.

1. Vervolgens configureert u een AEM server waarmee Eclipse verbinding maakt.

   Om de debugger eigenschap te gebruiken, moet u AEM op zuivert wijze begonnen zijn - die kan worden bereikt, voor door het volgende aan de bevellijn toe te voegen:

   ```text
       -nofork -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=10123
   ```

   ![Verbinding maken met AEM server](assets/connect-server.png)

1. Klikken **Voltooien**. De projectstructuur wordt gemaakt.

   >[!NOTE]
   >
   >Op een nieuwe installatie (meer specifiek, wanneer bepaalde gebiedsdelen nooit zijn gedownload) zou u het project kunnen krijgen dat met fouten wordt gecreeerd. In dit geval volgt u de in [Ongeldige projectdefinitie oplossen](#resolving-invalid-project-definition).

## Bestaande projecten importeren {#how-to-import-existing-projects}

U kunt de **Nieuw project** functie om de juiste structuur voor u te maken:

1. Volg de instructies om een [Monster nemen van meermoduleproject](#sample-multi-module-project) en u hebt de volgende projecten gecreeerd voor u, die een gezonde scheiding van zorgen toelaten:

   * `PROJECT.ui.apps` for `/apps` en `/etc` content
   * `PROJECT.ui.content` for `/content` die is gemaakt
   * `PROJECT.core` voor Java™-pakketten (deze worden interessant wanneer u Java™-code wilt toevoegen)
   * `PROJECT.it.launcher` en `PROJECT.it.tests` voor integratietests

1. Vervang de inhoud van uw `PROJECT.ui.apps` met de `apps` en `etc` mappen van het pakket:

   1. In het paneel van de Ontdekkingsreiziger van het Project, ontvouw `PROJECT.ui.apps` > `src` > `main` > `content` > `jcr_root` > `apps`.
   1. Klik met de rechtermuisknop op de knop `apps` map en kies **Tonen in** > **Systeemverkenner**.
   1. Verwijder de `apps` en `etc` mappen die u nu moet zien en hier plaatsen `apps` en `etc` mappen van het inhoudspakket.
   1. Klik in Eclipse met de rechtermuisknop op de knop `PROJECT.ui.apps` project en kies **Vernieuwen**.

1. Doe dan het zelfde voor `PROJECT.ui.content` en vervang de inhoudsmap door een van de pakketten:

   1. In het paneel van de Ontdekkingsreiziger van het Project, ontvouw `PROJECT.ui.content` > `src` > `main` > `content` > `jcr_root` > `content`.
   1. Klik met de rechtermuisknop op de diepere inhoudsmap en kies **Tonen in** > **Systeemverkenner**.
   1. Verwijder de inhoudsmap die u nu moet zien en plaats hier de inhoudsmap van het inhoudspakket.
   1. Klik in Eclipse met de rechtermuisknop op de knop `PROJECT.ui.content` project en kies **Vernieuwen**.

1. Nu moet u de `filter.xml` De bestanden van deze twee projecten komen overeen met de inhoud van het inhoudspakket. Open daarvoor de `META-INF/vault/filter.xml` bestand van het inhoudspakket in een aparte tekst/code-editor.

   * Dit is een voorbeeld van hoe uw `filter.xml` bestand kan er uitzien:

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

1. Wat de inhoud van het pakket betreft dat in twee projecten is gesplitst, moet u deze filterregels ook in twee splitsen en dienovereenkomstig bijwerken `filter.xml` bestanden van de twee projecten.

   1. Open in Eclipse `PROJECT.ui.apps/src/main/content/META-INF/filter.xml`.
   1. De inhoud van de `<workspaceFilter>` element met de regels van uw pakket waarmee begint `/apps` en `/etc`
      * Bijvoorbeeld:

        ```xml
        <?xml version="1.0" encoding="UTF-8"?>
        <workspaceFilter version="1.0">
           <filter root="/apps/foo"/>
           <filter root="/apps/foundation/components/bar"/>
           <filter root="/etc/designs/foo"/>
        </workspaceFilter>
        ```

   1. Vervolgens openen `PROJECT.ui.content/src/main/content/META-INF/filter.xml`.
   1. Vervang de regels door de regels in het pakket waarmee u begint `/content`.
      * Bijvoorbeeld:

        ```xml
        <?xml version="1.0" encoding="UTF-8"?>
        <workspaceFilter version="1.0">
           <filter root="/content/foo"/>
           <filter root="/content/dam/foo"/>
           <filter root="/content/usergenerated/content/foo"/>
        </workspaceFilter>
        ```

1. Zorg ervoor dat u al uw wijzigingen opslaat. U kunt die nieuwe inhoud nu synchroniseren met uw AEM.

1. Controleer of in het deelvenster Servers de verbinding is gestart en start deze als dat niet het geval is.
1. Klik op de knop **Reinigen en publiceren** pictogram.

Als u klaar bent, moet het pakket op de instantie worden uitgevoerd en als u het bestand opslaat, wordt elke wijziging automatisch gesynchroniseerd met de instantie.

Als u een pakket uit uw project wilt opnieuw bouwen, klik met de rechtermuisknop aan `PROJECT.ui.apps` of `PROJECT.ui.content` en kiest u **Uitvoeren als** > **Maven Install**.

Er is nu een doelmap gemaakt met het pakket in de map (bijvoorbeeld `PROJECT.ui.apps-0.0.1-SNAPSHOT.zip`).

## Problemen oplossen {#troubleshooting}

### Ongeldige projectdefinitie oplossen {#resolving-invalid-project-definition}

Om ongeldige gebiedsdelen en projectdefinitie op te lossen ga als volgt te werk:

1. Selecteer alle gemaakte projecten.
1. Klik met de rechtermuisknop.
1. Selecteer in het contextmenu **Maven** > **Projecten bijwerken**.
1. Controleren **Updates van momentopname/releases forceren**.
1. Klikken **OK**.

Eclipse downloadt de vereiste afhankelijkheden. Dit kan even duren.

## Meer informatie {#more-information}

Op de officiële Apache Sling IDE-website voor Eclipse vindt u nuttige informatie:

* De [**Apache Sling IDE-gereedschap voor Eclipse** Handboek](https://sling.apache.org/documentation/development/ide-tooling.html), begeleidt deze documentatie u door de algemene concepten, serverintegratie, en plaatsingsmogelijkheden die door de Hulpmiddelen van de Ontwikkeling van de AEM worden gesteund.
* De [Sectie Problemen oplossen](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting).
* De [Lijst met bekende problemen](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues).

De volgende ambtenaar [Eclipse](https://www.eclipse.org/) documentatie kan u helpen uw omgeving in te stellen:

* [Aan de slag met Eclipse](https://eclipseide.org/getting-started/)
* [Help-systeem Eclipse Luna](https://help.eclipse.org/latest/index.jsp)
* [Maven Integration (m2eclipse)](https://www.eclipse.org/m2e/)
