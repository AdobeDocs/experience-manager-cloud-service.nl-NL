---
title: Elementen verwerken met behulp van mediafuncties en workflows
description: Meer informatie over verschillende mediafuncties en hoe u deze kunt gebruiken in workflows om taken uit te voeren op elementen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: f2e257ff880ca2009c3ad6c8aadd055f28309289

---


# Elementen verwerken met behulp van mediafuncties en workflows {#processing-assets-using-media-handlers-and-workflows}

Adobe Experience Manager (AEM) Assets wordt geleverd met een set standaardworkflows en mediahandlers voor het verwerken van middelen. In de workflow worden de algemene taken gedefinieerd die op de elementen moeten worden uitgevoerd en worden de specifieke taken vervolgens gedelegeerd aan de media-handlers, bijvoorbeeld het genereren van miniaturen of het ophalen van metagegevens.

Er kan een workflow worden gedefinieerd die automatisch wordt uitgevoerd wanneer een element van een bepaald type naar de server wordt geüpload. De verwerkingsstappen worden gedefinieerd in een reeks AEM Assets Media Handlers. AEM verstrekt sommige [ingebouwde managers,](#default-media-handlers) en de extra degenen kunnen of [douane worden ontwikkeld](#creating-a-new-media-handler) of worden bepaald door het proces aan een hulpmiddel [van de](#command-line-based-media-handler)bevellijn te delegeren.

Mediahandlers zijn services binnen AEM Assets die specifieke handelingen uitvoeren op elementen. Wanneer bijvoorbeeld een MP3-audiobestand naar AEM wordt geüpload, wordt met een workflow een MP3-handler geactiveerd die de metagegevens extraheert en een miniatuur genereert. Meestal worden media-afhandelingen gebruikt in combinatie met workflows. De meeste gangbare MIME-typen worden ondersteund in AEM. U kunt specifieke taken uitvoeren op elementen door workflows uit te breiden/te maken, media-handlers uit te breiden/te maken of media-handlers uit te schakelen/in te schakelen.

>[!NOTE]
>
>Raadpleeg de pagina met door [Middelen ondersteunde indelingen](file-format-support.md) voor een beschrijving van alle indelingen die door AEM Assets worden ondersteund, en van de functies die voor elke indeling worden ondersteund.

## Standaardmediafuncties {#default-media-handlers}

De volgende media-handlers zijn beschikbaar in AEM Assets en verwerken de meest gebruikte MIME-typen:

<!-- TBD: Apply correct formatting once table is moved to MD.
-->

<table>
 <tbody>
  <tr>
   <td>Naam handler</td>
   <td>Servicenaam (in de systeemconsole)</td>
   <td>Ondersteunde MIME-typen</td>
  </tr>
  <tr>
   <td>TextHandler</td>
   <td><p>com.day.cq.dam.core.impl.handler.TextHandler</p> </td>
   <td>text/plain</td>
  </tr>
  <tr>
   <td>PdfHandler</td>
   <td><p>com.day.cq.dam.handler.standard.pdf.PdfHandler</p> </td>
   <td><p>application/pdf<br /> application/illustrator</p> </td>
  </tr>
  <tr>
   <td>JpegHandler</td>
   <td><p>com.day.cq.dam.core.impl.handler.JpegHandler</p> </td>
   <td>image/jpeg</td>
  </tr>
  <tr>
   <td>Mp3Handler</td>
   <td><p>com.day.cq.dam.handler.standard.mp3.Mp3Handler</p> </td>
   <td><p>audio/mpeg</p> </td>
  </tr>
  <tr>
   <td>ZipHandler</td>
   <td><p>com.day.cq.dam.handler.standard.zip.ZipHandler</p> </td>
   <td><p>application/java-archive</p> <p>application/zip</p> </td>
  </tr>
  <tr>
   <td>PictHandler</td>
   <td><p>com.day.cq.dam.handler.standard.pict.PictHandler</p> </td>
   <td><p>image/pict</p> </td>
  </tr>
  <tr>
   <td>StandardImageHandler</td>
   <td><p>com.day.cq.dam.core.impl.handler.StandardImageHandler</p> </td>
   <td><p>image/gif</p> <p>image/png</p> <p>toepassing/photoshop</p> <p>image/jpeg</p> <p>image/tiff</p> <p>image/x-ms-bmp</p> <p>image/bmp</p> </td>
  </tr>
  <tr>
   <td>MSOfficeHandler</td>
   <td>com.day.cq.dam.handler.standard.msoffice.MSOfficeHandler</td>
   <td>application/msword<br /> </td>
  </tr>
  <tr>
   <td>MSPowerPointHandler</td>
   <td>com.day.cq.dam.handler.standard.msoffice.MSPowerPointHandler</td>
   <td>application/vnd.ms-powerpoint<br /> </td>
  </tr>
  <tr>
   <td>OpenOfficeHandler</td>
   <td>com.day.cq.dam.handler.standard.ooxml.OpenOfficeHandler</td>
   <td>application/vnd.openxmlformats-officedocument.wordprocessingml.document<br /> application/vnd.openxmlformats-officedocument.spreadsheetml.sheet<br /> application/vnd.openxmlformats-officedocument.presentationml.presentation<br /><br /> </td>
  </tr>
  <tr>
   <td>EPubHandler</td>
   <td>com.day.cq.dam.handler.standard.epub.EPubHandler</td>
   <td>application/epub+zip</td>
  </tr>
  <tr>
   <td>GenericAssetHandler</td>
   <td><p>com.day.cq.dam.core.impl.handler.GenericAssetHandler</p> </td>
   <td>fallback als er geen andere handler is gevonden om gegevens uit een element te extraheren</td>
  </tr>
 </tbody>
</table>

Alle managers voeren de volgende taken uit:

* alle beschikbare metagegevens uit het element extraheren.
* een miniatuurafbeelding maken van het element.

Het is mogelijk om de actieve media managers te bekijken:

1. Navigeer in uw browser naar `http://localhost:4502/system/console/components`.
1. Klik op de koppeling `com.day.cq.dam.core.impl.store.AssetStoreImpl`.
1. Er wordt een lijst weergegeven met alle actieve mediamanagers.

## Media-handlers gebruiken in Workflows om taken uit te voeren op middelen {#using-media-handlers-in-workflows-to-perform-tasks-on-assets}

De managers van media zijn de diensten die gewoonlijk in combinatie met werkschema&#39;s worden gebruikt.

AEM beschikt over enkele standaardworkflows om elementen te verwerken. Open de workflowconsole en klik op het tabblad **[!UICONTROL Modellen]** om deze weer te geven: de workflowtitels die beginnen met AEM Assets zijn de assets-specifieke.

Bestaande workflows kunnen worden uitgebreid en nieuwe workflows kunnen worden gemaakt om elementen volgens specifieke vereisten te verwerken.

The following example shows how to enhance the **[!UICONTROL AEM Assets Synchronization]** workflow so that sub-assets are generated for all assets except PDF documents.

### Media Handler uitschakelen/inschakelen {#disabling-enabling-a-media-handler}

De media-handlers kunnen worden uitgeschakeld of ingeschakeld via de Apache Felix Web Management Console. Wanneer de media-handler is uitgeschakeld, worden de taken niet uitgevoerd op de elementen.

Een media-handler in- en uitschakelen:

1. Navigeer in uw browser naar `https://<host>:<port>/system/console/components`.
1. Klik op **[!UICONTROL Uitschakelen]** naast de naam van de media-handler. Bijvoorbeeld: `com.day.cq.dam.handler.standard.mp3.Mp3Handler`.
1. De pagina vernieuwen: naast de mediafunctie wordt een pictogram weergegeven dat aangeeft dat het is uitgeschakeld.
1. Klik naast de naam van de media-handler op **[!UICONTROL Inschakelen]** om de mediafunctie in te schakelen.

### Een nieuwe mediafunctie maken {#creating-a-new-media-handler}

Voor ondersteuning van een nieuw mediatype of voor het uitvoeren van specifieke taken op een element, is het nodig een nieuwe mediafunctie te maken. In dit gedeelte wordt beschreven hoe u verder kunt gaan.

#### Belangrijke klassen en interfaces {#important-classes-and-interfaces}

De beste manier om een implementatie te beginnen is van een verstrekte abstracte implementatie te erven die de meeste dingen behandelt en redelijk standaardgedrag verstrekt: de `com.day.cq.dam.core.AbstractAssetHandler` klasse.

Deze klasse verstrekt reeds een abstracte de dienstbeschrijver. Dus als u overerft van deze klasse en de gemanipuleerde insteekmodule gebruikt, moet u de overervingmarkering instellen op `true`.

Voer de volgende methodes uit:

* `extractMetadata()`: extraheert alle beschikbare metagegevens.
* `getThumbnailImage()`: Hiermee maakt u een miniatuurafbeelding van het doorgegeven element.
* `getMimeTypes()`: retourneert de MIME-typen van het element.

Hier volgt een voorbeeldsjabloon:

`package my.own.stuff; /** * @scr.component inherit="true" * @scr.service */ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // implement the relevant parts } `

De interface en de klassen omvatten:

* `com.day.cq.dam.api.handler.AssetHandler` interface: Deze interface beschrijft de dienst die steun voor specifieke types MIME toevoegt. Als u een nieuw MIME-type wilt toevoegen, moet u deze interface implementeren. De interface bevat methoden voor het importeren en exporteren van de specifieke documenten, voor het maken van miniaturen en het uitnemen van metagegevens.
* `com.day.cq.dam.core.AbstractAssetHandler` klasse: Deze klasse fungeert als basis voor alle andere implementaties van elementenhandlers en biedt veelgebruikte functionaliteit.
* `com.day.cq.dam.core.AbstractSubAssetHandler`-klasse:
   * Deze klasse fungeert als basis voor alle andere implementaties van assethandlers en biedt veelgebruikte functionaliteit plus veelgebruikte functionaliteit voor het extraheren van subassets.
   * De beste manier om een implementatie te beginnen is van een verstrekte abstracte implementatie te erven die de meeste dingen behandelt en redelijk standaardgedrag verstrekt: de klasse com.day.cq.dam.core.AbstractAssetHandler.
   * Deze klasse verstrekt reeds een abstracte de dienstbeschrijver. Dus als u overerft van deze klasse en de gemaven-sling-plugin gebruikt, zorg ervoor dat u de overervingsvlag aan waar plaatst.

De volgende methoden moeten worden toegepast:

* `extractMetadata()`: met deze methode worden alle beschikbare metagegevens geëxtraheerd.
* `getThumbnailImage()`: met deze methode maakt u een miniatuurafbeelding van het doorgegeven element.
* `getMimeTypes()`: Deze methode retourneert het MIME-type(n) van het element.

Hier volgt een voorbeeldsjabloon:

pakket my.own.stuff; /&amp;ast;&amp;ast; &amp;ast; @scr.component inherit=&quot;true&quot;&amp;ast; @scr.service&amp;ast;/ openbare klasse MyMediaHandler breidt com.day.cq.dam.core.AbstractAssetHandler { // implementeert de relevante onderdelen }

De interface en de klassen omvatten:

* `com.day.cq.dam.api.handler.AssetHandler` interface: Deze interface beschrijft de dienst die steun voor specifieke types MIME toevoegt. Als u een nieuw MIME-type wilt toevoegen, moet u deze interface implementeren. De interface bevat methoden voor het importeren en exporteren van de specifieke documenten, voor het maken van miniaturen en het uitnemen van metagegevens.
* `com.day.cq.dam.core.AbstractAssetHandler` klasse: Deze klasse fungeert als basis voor alle andere implementaties van elementenhandlers en biedt veelgebruikte functionaliteit.
* `com.day.cq.dam.core.AbstractSubAssetHandler` klasse: Deze klasse fungeert als basis voor alle andere implementaties van elementenhandlers en biedt veelgebruikte functionaliteit plus veelgebruikte functionaliteit voor het extraheren van subelementen.

<!--
#### Example: create a specific Text Handler {#example-create-a-specific-text-handler}

In this section, you will create a specific Text Handler that generates thumbnails with a watermark.

Proceed as follows:

Refer to [Development Tools](../sites-developing/dev-tools.md) to install and set up Eclipse with a Maven plugin and for setting up the dependencies that are needed for the Maven project.

After you perform the following procedure, when you upload a txt file into AEM, the file's metadata are extracted and two thumbnails with a watermark are generated.

1. In Eclipse, create `myBundle` Maven project:

    1. In the Menu bar, click **[!UICONTROL File > New > Other]**.
    1. In the dialog, expand the Maven folder, select Maven Project and click **[!UICONTROL Next]**.
    1. Check the Create a simple project box and the Use default Workspace locations box, then click **[!UICONTROL Next]**.
    1. Define the Maven project:

        * Group Id: com.day.cq5.myhandler
        * Artifact Id: myBundle
        * Name: My AEM bundle
        * Description: This is my AEM bundle

    1. Click **[!UICONTROL Finish]**.

1. Set the Java Compiler to version 1.5:

    1. Right-click the `myBundle` project, select Properties.
    1. Select Java Compiler and set following properties to 1.5:

        * Compiler compliance level
        * Generated .class files compatibility
        * Source compatibility

    1. Click **[!UICONTROL OK]**. In the dialog window, click Yes.

1. Replace the code in the pom.xml file with the following code:

1. Create the package `com.day.cq5.myhandler` that contains the Java classes under `myBundle/src/main/java`:

    1. Under myBundle, right-click `src/main/java`, select New, then Package.
    1. Name it `com.day.cq5.myhandler` and click Finish.

1. Create the Java class `MyHandler`:

    1. In Eclipse, under `myBundle/src/main/java`, right-click the `com.day.cq5.myhandler` package, select New, then Class.
    1. In the dialog window, name the Java Class MyHandler and click Finish. Eclipse creates and opens the file MyHandler.java.
    1. In `MyHandler.java` replace the existing code with the following and then save the changes:

   ```java
   package com.day.cq5.myhandler;
   import java.awt.Color;
   import java.awt.Rectangle;
   import java.awt.image.BufferedImage;
   import java.io.IOException;
   import java.io.InputStream;
   import java.io.InputStreamReader;
   import javax.jcr.Node;
   import javax.jcr.RepositoryException;
   import javax.jcr.Session;
   import org.apache.commons.io.IOUtils;
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   import com.day.cq.dam.api.metadata.ExtractedMetadata;
   import com.day.cq.dam.core.AbstractAssetHandler;
   import com.day.image.Font;
   import com.day.image.Layer;
   import com.day.cq.wcm.foundation.ImageHelper;

   /**
    * The <code>MyHandler</code> can extract text files
    * @scr.component inherit="true" immediate="true" metatype="false"
    * @scr.service
    *
    **/

   public class MyHandler extends AbstractAssetHandler {
    /** * Logger instance for this class. */
    private static final Logger log = LoggerFactory.getLogger(MyHandler.class);
    /** * Music icon margin */
    private static final int MARGIN = 10;
    /** * @see com.day.cq.dam.api.handler.AssetHandler#getMimeTypes() */
    public String[] getMimeTypes() {
     return new String[] {"text/plain"};
    }

    public ExtractedMetadata extractMetadata(Node asset) {
     ExtractedMetadata extractedMetadata = new ExtractedMetadata();
     InputStream data = getInputStream(asset);
     try {
      // read text data
      InputStreamReader reader = new InputStreamReader(data);
      char[] buffer = new char[4096];
      String text = "";
      while (reader.read(buffer) != -1) {
       text += new String(buffer);
      }
      reader.close();
      long wordCount = this.wordCount(text);
      extractedMetadata.setProperty("text", text);
      extractedMetadata.setMetaDataProperty("Word Count",wordCount);
      setMimetype(extractedMetadata, asset);
     } catch (Throwable t) {
      log.error("handling error: " + t.toString(), t);
     } finally {
      IOUtils.closeQuietly(data);
     }
     return extractedMetadata; }
    // ----------------------< helpers >----------------------------------------
    protected BufferedImage getThumbnailImage(Node node) {
     ExtractedMetadata metadata = extractMetadata(node);
     final String text = (String) metadata.getProperty("text");
     // create text layer
     final Layer layer = new Layer(500, 600, Color.WHITE);
     layer.setPaint(Color.black);
     Font font = new Font("Arial", 12);
     String displayText = this.getDisplayText(text, 600, 12);
     if(displayText!=null && displayText.length() > 0) {
      // commons-gfx Font class would throw IllegalArgumentException on empty or null text
      layer.drawText(10, 10, 500, 600, displayText, font, Font.ALIGN_LEFT, 0, 0);
     }
     // create watermark and merge with text layer
     Layer watermarkLayer;
     try {
      final Session session = node.getSession();
      watermarkLayer = ImageHelper.createLayer(session, "/content/dam/geometrixx/icons/certificate.png");
      watermarkLayer.setX(MARGIN);
      watermarkLayer.setY(MARGIN);
      layer.merge(watermarkLayer);
     } catch (RepositoryException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
     } catch (IOException e) {
      // TODO Auto-generated catch block
      e.printStackTrace(); }
     layer.crop(new Rectangle(510, 600));
     return layer.getImage(); }
    // ---------------< private >-----------------------------------------------
    /**
     * This method cuts lines if the text file is too long..
     * * @param text
     * * text to check
     * * @param height
     * * text box height (px)
     * * @param fontheight
     * * font height (px)
     * * @return the text which will fit into the box
     */
    private String getDisplayText(String text, int height, int fontheight) {
     String trimmedText = text.trim();
     int numOfLines = height / fontheight;
     String lines[] = trimmedText.split("\n");
     if (lines.length <= numOfLines) {
      return trimmedText;
     } else {
      String cuttetText = "";
      for (int i = 0; i < numOfLines; i++) {
       cuttetText += lines[i] + "\n";
      }
      return cuttetText;
     }
    }
    /**
     * * This method counts the number of words in a string
     * * @param text the String whose words would like to be counted
     * * @return the number of words in the string
     * */
    private long wordCount(String text) {
     // We need to keep track of the last character, if we have two white spaces in a row we dont want to double count
     // The starting of the document is always a whitespace
     boolean prevWhiteSpace = true;
     boolean currentWhiteSpace = true;
     char c; long numwords = 0;
     int j = text.length();
     int i = 0;
     while (i < j) {
      c = text.charAt(i++);
      if (c == 0) { break; }
      currentWhiteSpace = Character.isWhitespace(c);
      if (currentWhiteSpace && !prevWhiteSpace) { numwords++; }
      prevWhiteSpace = currentWhiteSpace;
     }
     // If we do not end with a white space then we need to add one extra word
     if (!currentWhiteSpace) { numwords++; }
     return numwords;
    }
   }
   ```

1. Compile the Java class and create the bundle:

    1. Right-click the myBundle project, select **[!UICONTROL Run As]**, then **[!UICONTROL Maven Install]**.
    1. The bundle `myBundle-0.0.1-SNAPSHOT.jar` (containing the compiled class) is created under `myBundle/target`.

1. In CRX Explorer, create a new node under `/apps/myApp`. Name = `install`, Type = `nt:folder`.
1. Copy the bundle `myBundle-0.0.1-SNAPSHOT.jar` and store it under `/apps/myApp/install` (for example with WebDAV). The new text handler is now active in AEM.
1. In your browser, open the Apache Felix Web Management Console. Select the Components tab and disable the default text handler `com.day.cq.dam.core.impl.handler.TextHandler`.

-->

## Media-handler op basis van opdrachtregel {#command-line-based-media-handler}

Met AEM kunt u alle opdrachtregelprogramma&#39;s binnen een workflow uitvoeren om elementen (zoals ImageMagick) om te zetten en de nieuwe uitvoering aan het element toe te voegen. U hoeft het opdrachtregelprogramma alleen te installeren op de schijf die als host fungeert voor de AEM-server en een processtap toe te voegen en te configureren voor de workflow. Met het aangeroepen proces kunt u filteren op basis van specifieke MIME-typen en meerdere miniaturen maken op basis van de nieuwe uitvoering. `CommandLineProcess`

De volgende conversies kunnen automatisch worden uitgevoerd en opgeslagen binnen AEM-elementen:

* EPS- en AI-transformatie met [ImageMagick](https://www.imagemagick.org/script/index.php) en [Ghostscript](https://www.ghostscript.com/)
* FLV-videotranscodering met [Mpeg](https://ffmpeg.org/)
* MP3-codering met [LAME](http://lame.sourceforge.net/)
* Audio verwerken met [SOX](http://sox.sourceforge.net/)

>[!NOTE]
>
>Op niet-Windows-systemen retourneert het FFMpeg-gereedschap een fout tijdens het genereren van uitvoeringen voor een video-element met één aanhalingsteken (&#39;) in de bestandsnaam. Als de naam van het videobestand één aanhalingsteken bevat, verwijdert u het bestand voordat u het uploadt naar AEM.

Het `CommandLineProcess` proces voert de volgende bewerkingen uit in de volgorde waarin deze worden weergegeven:

* Hiermee wordt het bestand gefilterd op basis van specifieke MIME-typen, indien opgegeven.
* Maakt een tijdelijke map op de schijf die als host fungeert voor de AEM-server.
* Hiermee wordt het oorspronkelijke bestand gestroomd naar de tijdelijke map.
* Voert de opdracht uit die door de argumenten van de stap wordt gedefinieerd. De opdracht wordt uitgevoerd in de tijdelijke map met de machtigingen van de gebruiker die AEM uitvoert.
* Hiermee wordt het resultaat weer in de weergavemap van de AEM-server gestroomd.
* Hiermee verwijdert u de tijdelijke map.
* Hiermee maakt u miniaturen op basis van deze uitvoeringen, indien opgegeven. Het aantal en de afmetingen van de miniaturen worden bepaald door de argumenten van de stap.

### Een voorbeeld met ImageMagick {#an-example-using-imagemagick}

In het volgende voorbeeld ziet u hoe u de processtap voor de opdrachtregel instelt, zodat telkens wanneer een element met het mime-type gif of tiff aan /content/dam op de AEM-server wordt toegevoegd, een gespiegelde afbeelding van het origineel samen met drie extra miniaturen (140x100, 48x48 en 10x250) wordt gemaakt.

Hiervoor gebruikt u ImageMagick. ImageMagick is een gratis softwaresuite voor het maken, bewerken en samenstellen van bitmapafbeeldingen. Deze suite wordt doorgaans gebruikt vanaf de opdrachtregel.

Installeer ImageMagick eerst op de schijf die als host fungeert voor de AEM-server:

1. ImageMagick installeren: raadpleeg de [documentatie](https://www.imagemagick.org/script/download.php)van ImageMagick.
1. Stel het gereedschap zo in dat u het op de opdrachtregel kunt omzetten.
1. Als u wilt controleren of het gereedschap op de juiste wijze is geïnstalleerd, voert u de volgende opdracht uit `convert -h` op de opdrachtregel.

   Er wordt een Help-scherm weergegeven met alle mogelijke opties van het gereedschap Omzetten.

   >[!NOTE]
   >
   >In sommige versies van Windows (bijvoorbeeld Windows SE) kan het zijn dat de opdracht Converteren niet wordt uitgevoerd omdat dit een conflict veroorzaakt met het native hulpprogramma voor conversie dat onderdeel is van de installatie van Windows. Vermeld in dit geval het volledige pad voor het hulpprogramma ImageMagick dat wordt gebruikt om afbeeldingsbestanden om te zetten in miniaturen. Bijvoorbeeld, `"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`.

1. Als u wilt controleren of het gereedschap correct wordt uitgevoerd, voegt u een .jpg-afbeelding toe aan de werkmap en voert u de opdracht voor het omzetten `<image-name>.jpg -flip <image-name>-flipped.jpg` op de opdrachtregel uit.

   Er wordt een gespiegelde afbeelding aan de map toegevoegd.

Then, add the command line process step to the **[!UICONTROL DAM Update Asset]** workflow:

1. Ga naar de **[!UICONTROL Workflowconsole]** .
1. Bewerk op het tabblad **[!UICONTROL Modellen]** het model **[!UICONTROL DAM Update Asset]** .
1. Wijzig de instellingen van de renderingstap **[!UICONTROL voor]** Web als volgt:

   **Argumenten**:

   `mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

1. Sla de workflow op.

U kunt de gewijzigde workflow testen door middel van een element aan `/content/dam`te voegen.

1. Haal in het bestandssysteem een .tiff-afbeelding van uw keuze op. Wijzig de naam van het bestand in `myImage.tiff` en kopieer het naar `/content/dam`het bestand, bijvoorbeeld met WebDAV.
1. Ga bijvoorbeeld naar de **[!UICONTROL CQ5 DAM]** -console `http://localhost:4502/libs/wcm/core/content/damadmin.html`.
1. Open het element **[!UICONTROL myImage.tiff]** en controleer of de gespiegelde afbeelding en de drie miniaturen zijn gemaakt.

#### De CommandLineProcess-stap configureren {#configuring-the-commandlineprocess-process-step}

Deze sectie beschrijft hoe u de **procesargumenten** van **CommandLineProcess** kunt instellen.

De waarden van de **procesargumenten** moeten door een komma worden gescheiden en mogen niet beginnen met een spatie.

<table>
 <tbody>
  <tr>
   <td> Argument-formaat</td>
   <td>Beschrijving</td>
  </tr>
  <tr>
   <td> mime:&lt;mime-type&gt;</td>
   <td><p>Optioneel argument. Het proces wordt toegepast als het element hetzelfde MIME-type heeft als het argument.</p> <p>Verschillende mime-typen kunnen worden gedefinieerd.</p> </td>
  </tr>
  <tr>
   <td> tn:&lt;width&gt;:&lt;height&gt;</td>
   <td><p>Optioneel argument. Het proces leidt tot een duimnagel met de afmetingen die in het argument worden bepaald.</p> <p>Er kunnen verschillende miniaturen worden gedefinieerd.<br /> </p> </td>
  </tr>
  <tr>
   <td> cmd: &lt;command&gt;</td>
   <td><p>Definieert de opdracht die wordt uitgevoerd. De syntaxis hangt van het hulpmiddel van de bevellijn af.</p> <p>Er kan slechts één opdracht worden gedefinieerd.</p> <p>U kunt de volgende variabelen gebruiken om de opdracht te maken:<br/></p> <p><code>${filename}</code>: naam van het invoerbestand, bijvoorbeeld 'original.jpg'<br/><code>${file}</code>: de volledige padnaam van het invoerbestand, bijvoorbeeld "/tmp/cqdam0816.tmp/original.jpg"<br/><code>${directory}</code>: map van het invoerbestand, bijvoorbeeld "/tmp/cqdam0816.tmp".<br/> <code>${basename}</code>: naam van het invoerbestand zonder extensie, bijvoorbeeld origineel<br/> <code>${extension}</code>: extensie van het invoerbestand, bijvoorbeeld JPG<br/></p></td>
  </tr>
 </tbody>
</table>

Bijvoorbeeld als ImageMagick is geïnstalleerd op de schijf die als host fungeert voor de AEM-server en als u een processtap maakt met **CommandLineProcess** als Implementation en de volgende waarden als **procesargumenten**:

`mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

Wanneer de workflow vervolgens wordt uitgevoerd, is de stap alleen van toepassing op elementen met een afbeelding/gif of mime:afbeelding/tiff als mime-type, wordt een gespiegelde afbeelding van het origineel gemaakt, omgezet in .jpg en worden drie miniaturen gemaakt met de afmetingen: 140x100, 48x48 en 10x250.

Gebruik de volgende **procesargumenten** om de drie standaardminiaturen te maken met ImageMagick:

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=319x319 -thumbnail "319x319>" -background transparent -gravity center -extent 319x319 -write png:cq5dam.thumbnail.319.319.png -thumbnail "140x100>" -background transparent -gravity center -extent 140x100 -write cq5dam.thumbnail.140.100.png -thumbnail "48x48>" -background transparent -gravity center -extent 48x48 cq5dam.thumbnail.48.48.png`

Gebruik de volgende **procesargumenten** om de voor het web ingeschakelde uitvoering te maken met ImageMagick:

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=1280x1280 -thumbnail "1280x1280>" cq5dam.web.1280.1280.jpeg`

>[!NOTE]
>
>De **stap CommandLineProcess** is alleen van toepassing op elementen (knooppunten van het type `dam:Asset`) of afstammingen van een element.
