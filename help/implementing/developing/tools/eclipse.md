---
title: AEM Developer Tools for Eclipse
description: AEM Developer Tools for Eclipse
translation-type: tm+mt
source-git-commit: c40d668cb6dcf5c3e2d09504b547457306a99c85
workflow-type: tm+mt
source-wordcount: '1182'
ht-degree: 1%

---


# AEM Developer Tools for Eclipse{#aem-developer-tools-for-eclipse}

![](assets/eclipse-logo.png)

## Overzicht {#overview}

De AEM Developer Tools for Eclipse is een Eclipse-plug-in die is gebaseerd op de [Eclipse-plug-in voor Apache Sling](https://sling.apache.org/documentation/development/ide-tooling.html) die is uitgebracht onder de Apache-licentie 2.

Het biedt verschillende functies die AEM ontwikkeling vergemakkelijken:

* Naadloze integratie met AEM instanties via Eclipse Server Connector
* Synchronisatie voor zowel inhoud als OSGi-bundels
* Ondersteuning voor foutopsporing met functie voor hot-swapping van code
* Eenvoudige laarzentrekker van AEM projecten via een specifieke Tovenaar van de Aanmaak van het Project
* Eenvoudig bewerken van JCR-eigenschappen

## Vereisten {#requirements}

Voordat u de AEM Developer Tools kunt gebruiken, moet u:

* Download en installeer [Eclipse IDE voor Enterprise Java Developers](https://www.eclipse.org/downloads/packages/).
* Configureer uw excapse-installatie om ervoor te zorgen dat u ten minste 1 gigabyte heapgeheugen hebt door uw `eclipse.ini` configuratiebestand te bewerken, zoals beschreven in de veelgestelde vragen over [Eclipse](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse).

>[!NOTE]
>
>In MacOS moet u met de rechtermuisknop op **Eclipse.app** klikken en vervolgens **Pakketinhoud** tonen selecteren om uw `eclipse.ini`**.**

## Hoe te om de Hulpmiddelen van de Ontwikkelaar van de AEM voor Eclipse te installeren {#how-to-install-the-aem-developer-tools-for-eclipse}

Nadat u aan de bovenstaande [vereisten](#requirements) hebt voldaan, kunt u de insteekmodule als volgt installeren:

1. Open de website [AEM Developer Tools.](https://eclipse.adobe.com/aem/dev-tools/)

1. Kopieer de **installatiekoppeling**.

   U kunt ook een archief downloaden in plaats van de installatiekoppeling te gebruiken. Hierdoor kunt u offline installeren, maar op deze manier gaan automatische updatemeldingen verloren.

1. Open het menu **Help** in Eclipse.
1. Klik op **Nieuwe software** installeren.
1. Click **Add...**.
1. Voer in **Naam** `AEM Developer Tools`.
1. Kopieer de installatie-URL in **Locatie** .
1. Click **Add**.
1. Controleer zowel de **AEM** als de **slingerplug** .
1. Klik op **Next**.
1. Klik nogmaals in het venster Details **** installeren op **Volgende** .
1. Accepteer de licentieovereenkomsten en klik op **Voltooien**.
1. Klik op **Opnieuw starten** om Eclipse opnieuw te starten.

## Het AEM perspectief {#the-aem-perspective}

In Eclipse bepaalt een perspectief de acties en meningen beschikbaar binnen een venster en laat taakgerichte interactie met middelen in Verduistering toe. Raadpleeg de documentatie bij [Eclipse voor meer informatie over Perspectief.](https://help.eclipse.org)

De hulpmiddelen van de Ontwikkeling van de AEM voor Verduistering verstrekt een AEM Perspectief dat u volledige controle over uw AEM projecten en instanties biedt. Het AEM perspectief openen:

1. Selecteer in de menubalk Eclipse de optie **Venster** -> **Perspectief** -> **Perspectief** openen -> **Overige**.
1. Selecteer **AEM** in het dialoogvenster en klik op **Openen**.

![Het AEM perspectief in Eclipse](assets/eclipse-aem-perspective.png)

## Monster nemen van project met meerdere modules {#sample-multi-module-project}

De AEM Hulpmiddelen van de Ontwikkelaar voor Eclipse komen met een steekproef, multi-moduleproject dat u snel aan snelheid met een projectopstelling in Verduistering helpt, evenals dienst als best-praktijkgids aan verscheidene AEM eigenschappen. [Meer informatie over het Projectarchetype](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

Ga als volgt te werk om het voorbeeldproject te maken:

1. Blader in het menu **Bestand** > **Nieuw** > **Project** naar de sectie **AEM** en selecteer **AEM Monster nemen van project** met meerdere modules.

   ![AEM Monster nemen van project met meerdere modules](assets/aem-sample-project.png)

1. Klik op **Next**.

   >[!NOTE]
   >
   >Deze stap kan even duren omdat m2eclipse de archetype catalogi moet scannen.

1. Kies `com.adobe.granite.archetypes : sample-project-archetype : <highest-number>` in het menu en klik op **Volgende**.

   ![Versie van archetype selecteren](assets/select-archetype.png)

1. Geef de volgende velden op voor het voorbeeldproject:

   * **Naam**
   * **Groep-id**
   * **Artefact-id**
   * **appId** - Mogelijk moet u de **geavanceerde** opties uitvouwen om deze waarde in te stellen.
   * **appTitle** - Mogelijk moet u de **geavanceerde** opties uitvouwen om deze waarde in te stellen.
   * **Pakket** - Mogelijk moet u de opties voor **Geavanceerd** uitvouwen om deze waarde in te stellen.

   ![Eigenschappen archetype definiëren](assets/archetype-properties.png)

1. Klik op **Next**.

1. Vervolgens configureert u een AEM server waarmee Eclipse verbinding maakt.

   Om de debugger eigenschap te gebruiken, moet u AEM op zuivert wijze begonnen zijn - die kan worden bereikt bijvoorbeeld door het volgende aan de bevellijn toe te voegen:

   ```text
       -nofork -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=10123
   ```

   ![Verbinding maken met AEM server](assets/connect-server.png)

1. Click **Finish**. De projectstructuur wordt gemaakt.

   >[!NOTE]
   >
   >Op een nieuwe installatie (meer specifiek, wanneer bepaalde gebiedsdelen nooit zijn gedownload) zou u het project kunnen krijgen dat met fouten wordt gecreeerd. In dit geval volgt u de procedure die wordt beschreven in [Ongeldige projectdefinitie](#resolving-invalid-project-definition)oplossen.

## Bestaande projecten importeren {#how-to-import-existing-projects}

Met de functie **Nieuw project** kunt u de juiste structuur voor u maken:

1. Volg de instructies om een Project [van de Meervoudige Module van de](#sample-multi-module-project) Steekproef tot stand te brengen en u zult de volgende projecten hebben die voor u worden gecreeerd, die gezonde scheiding van zorgen zal toestaan:

   * `PROJECT.ui.apps` voor `/apps` en `/etc` inhoud
   * `PROJECT.ui.content` waarvoor `/content` dat is geschreven
   * `PROJECT.core` voor Java-bundels (deze worden interessant zodra u Java-code wilt toevoegen)
   * `PROJECT.it.launcher` en `PROJECT.it.tests` integratietests

1. Vervang de inhoud van uw `PROJECT.ui.apps` project door de `apps` en `etc` mappen van het pakket:

   1. Ontgrendel in het deelvenster Projectverkenner `PROJECT.ui.apps` > `src` > `main` > `content` > `jcr_root` > `apps`.
   1. Klik met de rechtermuisknop op de `apps` map en kies **Tonen in** > **Systeemverkenner**.
   1. Verwijder de `apps` en `etc` mappen die u nu moet zien en plaats hier de `apps` en `etc` mappen van het inhoudspakket.
   1. Klik in Eclipse met de rechtermuisknop op het `PROJECT.ui.apps` project en kies **Vernieuwen**.

1. Doe dan het zelfde voor de `PROJECT.ui.content` en vervang zijn inhoudsomslag met één van uw pakket:

   1. Ontgrendel in het deelvenster Projectverkenner `PROJECT.ui.content` > `src` > `main` > `content` > `jcr_root` > `content`.
   1. Klik met de rechtermuisknop op de diepere inhoudsmap en kies **Tonen in** -> **Systeemverkenner**.
   1. Verwijder de inhoudsmap die u nu moet zien en plaats hier de inhoudsmap van het inhoudspakket.
   1. Klik in Eclipse met de rechtermuisknop op het `PROJECT.ui.content` project en kies **Vernieuwen**.

1. Nu moet u de `filter.xml` bestanden van deze twee projecten bijwerken zodat deze overeenkomen met de inhoud van het inhoudspakket. Open daartoe het `META-INF/vault/filter.xml` bestand van het inhoudspakket in een aparte tekst/code-editor.

   * Dit is een voorbeeld van hoe uw `filter.xml` bestand eruit kan zien:

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

1. Wat de inhoud van uw pakket betreft dat in twee projecten werd gesplitst, zult u deze filterregels in twee moeten verdelen en dienovereenkomstig de `filter.xml` dossiers van de twee projecten bijwerken.

   1. Open Eclipse `PROJECT.ui.apps/src/main/content/META-INF/filter.xml`.
   1. Vervang de inhoud van het `<workspaceFilter>` element door de regels van het pakket waarmee begint `/apps` en `/etc`
      * Bijvoorbeeld:

         ```xml
         <?xml version="1.0" encoding="UTF-8"?>
         <workspaceFilter version="1.0">
            <filter root="/apps/foo"/>
            <filter root="/apps/foundation/components/bar"/>
            <filter root="/etc/designs/foo"/>
         </workspaceFilter>
         ```
   1. Open vervolgens `PROJECT.ui.content/src/main/content/META-INF/filter.xml`.
   1. Vervang de regels door de regels uit het pakket waarmee u begint `/content`.
      * Bijvoorbeeld:

         ```xml
         <?xml version="1.0" encoding="UTF-8"?>
         <workspaceFilter version="1.0">
            <filter root="/content/foo"/>
            <filter root="/content/dam/foo"/>
            <filter root="/content/usergenerated/content/foo"/>
         </workspaceFilter>
         ```


1. Sla al uw wijzigingen op. U kunt die nieuwe inhoud nu synchroniseren met uw AEM.

1. Controleer of in het deelvenster Servers de verbinding is gestart en start deze als dat niet het geval is.
1. Klik op het pictogram **Reinigen en Publiceren** .

Als u klaar bent, moet het pakket op de instantie worden uitgevoerd en als u het bestand opslaat, wordt elke wijziging automatisch gesynchroniseerd met de instantie.

Als u een pakket opnieuw wilt maken uit uw project, klikt u met de rechtermuisknop op het project `PROJECT.ui.apps` of `PROJECT.ui.content` en kiest u **Uitvoeren als** -> **Geïmporteerde installatie**.

Er is nu een doelmap gemaakt met uw pakket in de map (bijvoorbeeld `PROJECT.ui.apps-0.0.1-SNAPSHOT.zip`).

## Problemen oplossen {#troubleshooting}

### Ongeldige projectdefinitie oplossen {#resolving-invalid-project-definition}

Om ongeldige gebiedsdelen en projectdefinitie op te lossen ga als volgt te werk:

1. Selecteer alle gemaakte projecten.
1. Klik met de rechtermuisknop.
1. Selecteer **Geweven** -> **Projecten** bijwerken in het contextmenu.
1. Controleer **de updates van momentopnamen/releases** forceren.
1. Click **OK**.

Eclipse downloadt de vereiste afhankelijkheden. Dit kan even duren.

## Meer informatie {#more-information}

Op de officiële Apache Sling IDE-website voor Eclipse vindt u nuttige informatie:

* Met de [**Apache Sling IDE-tooling voor Eclipse** User Guide](https://sling.apache.org/documentation/development/ide-tooling.html), begeleidt deze documentatie u door de algemene concepten, serverintegratie en implementatiemogelijkheden die worden ondersteund door de AEM Development Tools.
* De sectie [](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting)Problemen oplossen.
* De lijst met [bekende problemen](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues).

De volgende officiële [Eclipse](https://eclipse.org/) -documentatie kan u helpen uw omgeving in te stellen:

* [Aan de slag met Eclipse](https://eclipse.org/users/)
* [Help-systeem Eclipse Luna](https://help.eclipse.org/luna/index.jsp)
* [Maven Integration (m2eclipse)](https://www.eclipse.org/m2e/)
