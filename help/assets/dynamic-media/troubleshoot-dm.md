---
title: Problemen met Dynamic Media oplossen
description: Tips voor het oplossen van problemen bij het gebruik van Dynamic Media.
topic: "Administrator,Business Practitioner"
role: Administrator,Business Practitioner
exl-id: 3e8a085f-57eb-4009-a5e8-1080b4835ae2
translation-type: tm+mt
source-git-commit: 6b232ab512a6faaf075faa55c238dfb10c00b100
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 1%

---

# Problemen met Dynamic Media oplossen {#troubleshooting-dynamic-media-scene-mode}

In het volgende onderwerp wordt het oplossen van problemen voor Dynamic Media beschreven.

## Nieuwe Dynamic Media-configuratie {#new-dm-config}

Zie [Problemen met een nieuwe Dynamic Media-configuratie oplossen](/help/assets/dynamic-media/config-dm.md#troubleshoot-dm-config).

## Algemeen (alle activa) {#general-all-assets}

Hier volgen enkele algemene tips en trucs voor alle elementen.

### Eigenschappen voor de synchronisatie van bedrijfsmiddelen {#asset-synchronization-status-properties}

De volgende eigenschappen van elementen kunnen in CRXDE Lite worden gecontroleerd om te bevestigen dat de middelen van Adobe Experience Manager naar Dynamic Media zijn gesynchroniseerd:

| **Eigenschap** | **Voorbeeld** | **Beschrijving** |
|---|---|---|
| `<object_node>/jcr:content/metadata/dam:scene7ID` | **`a|364266`** | Algemene indicator dat de knoop met Dynamic Media wordt verbonden. |
| `<object_node>/jcr:content/metadata/dam:scene7FileStatus` | **Tekst van** fout PublishComplete | Status van het uploaden van middelen naar Dynamic Media. |
| `<object_node>/jcr:content/metadata/dam:scene7File` | **myCompany/myAssetID** | Moet zijn gevuld om URL&#39;s te genereren naar externe middelen van Dynamic Media. |
| `<object_node>/jcr:content/dam:lastSyncStatus` | **** opvolger  **is mislukt:`<error text>`** | Synchronisatiestatus van sets (centrifuges, afbeeldingssets, enzovoort), voorinstellingen voor afbeeldingen, voorinstellingen voor viewers, updates van afbeeldingen met hyperlinks voor een element of afbeeldingen die zijn bewerkt. |

### Synchronisatie-logboekregistratie {#synchronization-logging}

Synchronisatiefouten en -problemen worden `error.log` aangemeld (servermap `/crx-quickstart/logs/` van de Experience Manager). Er is voldoende logboekregistratie beschikbaar om de hoofdoorzaak van de meeste problemen te bepalen. U kunt echter het logbestand voor DEBUG verhogen in het `com.adobe.cq.dam.ips`-pakket via de Sling Console ([https://localhost:4502/system/console/slinglog](https://localhost:4502/system/console/slinglog)) om meer informatie te verzamelen.

### Versiebeheer {#version-control}

Bij het vervangen van een bestaand Dynamic Media-element (dezelfde naam en locatie) kunt u beide elementen behouden of een versie vervangen/maken:

* Als u beide instellingen behoudt, wordt een element gemaakt met een unieke naam voor de URL van het gepubliceerde element. `image.jpg` is bijvoorbeeld het oorspronkelijke element en `image1.jpg` is het net geüploade element.

* Het maken van een versie wordt niet ondersteund in Dynamic Media. De nieuwe versie vervangt het bestaande element in levering.

## Afbeeldingen en sets {#images-and-sets}

Raadpleeg de volgende richtlijnen voor het oplossen van problemen als u problemen hebt met afbeeldingen en sets.

<table>
 <tbody>
  <tr>
   <td><strong>Probleem</strong></td>
   <td><strong>Foutopsporing</strong></td>
   <td><strong>Oplossing</strong></td>
  </tr>
  <tr>
   <td>Kan de knop Kopie-URL/Insluiten niet openen in de weergave met elementdetails</td>
   <td>
    <ol>
     <li><p>Ga naar CRX/DE:</p>
      <ul>
       <li>Controleer of de voorinstelling in het JCR <code>/etc/dam/presets/viewer/&lt;preset&gt; has lastReplicationAction</code> is gedefinieerd. Deze locatie is van toepassing als u een upgrade hebt uitgevoerd van Experience Manager 6.x naar 6.4 en de migratie hebt uitgeschakeld. Anders is de locatie <code>/conf/global/settings/dam/dm/presets/viewer</code>.</li>
       <li>Controleer of het element in de JCR <code>dam:scene7FileStatus</code><strong> </strong>onder Metagegevens wordt weergegeven als <code>PublishComplete</code>.</li>
      </ul> </li>
    </ol> </td>
   <td><p>Pagina vernieuwen/naar een andere pagina navigeren en terugkeren (JSP voor side rail moet opnieuw worden gecompileerd)</p> <p>Als dat niet werkt:</p>
    <ul>
     <li>Middelen publiceren.</li>
     <li>Elementen opnieuw laden en publiceren.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>De carrouselhotspot beweegt zich rond na het schakelen tussen dia's</td>
   <td><p>Controleer of alle dia's even groot zijn.</p> </td>
   <td><p>Gebruik voor de carrousel alleen afbeeldingen met dezelfde grootte.</p> </td>
  </tr>
  <tr>
   <td>De afbeelding wordt niet voorvertoond met de Dynamic Media-viewer</td>
   <td><p>Controleer of het element <code>dam:scene7File</code> bevat in de metagegevenseigenschappen (CRXDE Lite)</p> </td>
   <td><p>Controleer of alle elementen zijn verwerkt.</p> </td>
  </tr>
  <tr>
   <td>Geüpload element wordt niet weergegeven in elementkiezer</td>
   <td><p>Element controleren heeft eigenschap <code>jcr:content</code> &gt; <strong><code>dam:assetState</code></strong> = <code>processed</code> (CRXDE Lite)</p> </td>
   <td><p>Controleer of alle elementen zijn verwerkt.</p> </td>
  </tr>
  <tr>
   <td>Banner op kaartweergave toont <strong>Nieuw</strong> wanneer het element nog niet is verwerkt</td>
   <td>Activeer <code>jcr:content</code> &gt; <code>dam:assetState</code> = als <code>unprocessed</code> niet door de workflow is opgepikt.</td>
   <td>Wacht tot asset is opgehaald via workflow.</td>
  </tr>
  <tr>
   <td>In afbeeldingen of sets wordt de URL van de viewer of de insluitcode niet weergegeven</td>
   <td>Controleer of de viewervoorinstelling is gepubliceerd.</td>
   <td><p>Ga naar <strong>Gereedschappen</strong> &gt; <strong>Middelen</strong> &gt; <strong>Viewer-voorinstellingen</strong> en publiceer de viewervoorinstelling.</p> </td>
  </tr>
 </tbody>
</table>

## Video {#video}

Raadpleeg de volgende richtlijnen voor het oplossen van problemen als u problemen hebt met video.

<table>
 <tbody>
  <tr>
   <td><strong>Probleem</strong></td>
   <td><strong>Foutopsporing</strong></td>
   <td><strong>Oplossing</strong></td>
  </tr>
  <tr>
   <td>Video kan niet worden voorvertoond</td>
   <td>
    <ul>
     <li>Controleer of aan de map een videoprofiel is toegewezen (als de bestandsindeling niet wordt ondersteund). Als deze optie niet wordt ondersteund, wordt alleen een afbeelding weergegeven.</li>
     <li>Het videoprofiel moet meer dan één coderingsvoorinstelling bevatten om een AVS-set te genereren (enkele coderingen worden behandeld als video-inhoud voor MP4-bestanden). voor niet-ondersteunde bestanden, op dezelfde manier behandeld als niet-verwerkte bestanden).</li>
     <li>Controleer of de video is verwerkt door <code>dam:scene7FileAvs</code> van <code>dam:scene7File</code> in metagegevens te bevestigen.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Wijs een videoprofiel toe aan de map.</li>
     <li>Bewerk het videoprofiel om meerdere coderingsvoorinstellingen op te nemen.</li>
     <li>Wacht tot de video is verwerkt.</li>
     <li>Voordat u de video opnieuw laadt, moet u ervoor zorgen dat de Dynamic Media Encode Video-workflow niet wordt uitgevoerd.<br/> </li>
     <li>Laad de video opnieuw.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Video is niet gecodeerd</td>
   <td>
    <ul>
     <li>Controleer of Dynamic Media Cloud Service is geconfigureerd.</li>
     <li>Controleer of een videoprofiel is gekoppeld aan de uploadmap.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Controleer of de Dynamic Media-configuratie onder Cloud Services correct is ingesteld.</li>
     <li>Controleer of de map een videoprofiel heeft. Controleer ook het videoprofiel.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Videoverwerking duurt te lang</td>
   <td><p>U kunt als volgt bepalen of videocodering nog wordt uitgevoerd of dat er een foutstatus is ingevoerd:</p>
    <ul>
     <li>Controleer de videostatus <code>https://localhost:4502/crx/de/index.jsp#/content/dam/folder/videomp4/jcr%3Acontent</code> &gt; <code>dam:assetState</code></li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Video-uitvoering ontbreekt</td>
   <td><p>Wanneer video wordt geüpload, maar er geen gecodeerde vertoningen zijn:</p>
    <ul>
     <li>Controleer of aan de map een videoprofiel is toegewezen.</li>
     <li>Controleer of de video is verwerkt door <code>dam:scene7FileAvs</code> in metagegevens te bevestigen.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Wijs een videoprofiel toe aan de map.</li>
     <li>Wacht tot de video is verwerkt.<br /> </li>
    </ol> </td>
  </tr>
 </tbody>
</table>

## Viewers {#viewers}

Raadpleeg de volgende richtlijnen voor het oplossen van problemen als u problemen hebt met viewers.

<table>
 <tbody>
  <tr>
   <td><strong>Probleem</strong></td>
   <td><strong>Foutopsporing</strong></td>
   <td><strong>Oplossing</strong></td>
  </tr>
  <tr>
   <td>Voorinstellingen van viewer worden niet gepubliceerd</td>
   <td><p>Ga door naar de diagnostische pagina van de voorbeeldmanager: <code>https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html</code></p> <p>Berekende waarden observeren. Wanneer correct werkend, ziet u:</p> <p><code>_DMSAMPLE status: 0 unsyced assets - activation not necessary
       _OOTB status: 0 unsyced assets - 0 unactivated assets</code></p> <p><strong>Opmerking</strong>: Het kan ongeveer 10 minuten duren nadat de Dynamic Media-cloudinstellingen zijn geconfigureerd voor synchronisatie van de viewerelementen.</p> <p>Als er niet-geactiveerde elementen overblijven, klikt u op een van de <strong>Alle niet-geactiveerde elementen weergeven</strong> knoppen om details weer te geven.</p> </td>
   <td>
    <ol>
     <li>Navigeer naar de lijst met voorinstellingen voor viewers in de beheerprogramma's: <code>https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html</code></li>
     <li>Selecteer alle viewervoorinstellingen en klik op <strong>Publiceren</strong>.</li>
     <li>Navigeer terug naar voorbeeldbeheer en controleer of het aantal niet-geactiveerde elementen nu nul is.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Vooraf ingestelde illustraties van de viewer retourneren 404 vanaf de voorvertoning in elementdetails of kopiëren, URL- en insluitcode</td>
   <td><p>Ga als volgt te werk bij CRXDE Lite:</p>
    <ol>
     <li>Navigeer naar de map <code>&lt;sync-folder&gt;/_CSS/_OOTB</code> in de Dynamic Media-synchronisatiemap (bijvoorbeeld <code>/content/dam/_CSS/_OOTB</code>),</li>
     <li>Zoek het metagegevensknooppunt van het problematische element (bijvoorbeeld <code>&lt;sync-folder&gt;/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png/jcr:content/metadata/</code>).</li>
     <li>Controleer of <code>dam:scene7*</code>-eigenschappen aanwezig zijn. Als het element is gesynchroniseerd en gepubliceerd, ziet u dat de <code>dam:scene7FileStatus</code>-set is ingesteld op <strong>PublishComplete</strong>.</li>
     <li>Poging om de illustratie rechtstreeks vanuit Dynamic Media aan te vragen door de waarden van de volgende eigenschappen en letterlijke tekenreeksen samen te voegen
      <ul>
       <li><code>dam:scene7Domain</code></li>
       <li><code>"is/content"</code></li>
       <li><code>dam:scene7Folder</code></li>
       <li><code>&lt;asset-name&gt;</code></li>
       <li>Voorbeeld: <code>https://&lt;server&gt;/is/content/myfolder/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png</code></li>
      </ul> </li>
    </ol> </td>
   <td><p>Als de voorbeeldbestanden of de vooraf ingestelde illustratie van de viewer niet zijn gesynchroniseerd of gepubliceerd, start u het gehele kopiëren/synchronisatieproces opnieuw:</p>
    <ol>
     <li>Ga naar <code>/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html</code>
     </li>
     <li>Selecteer in volgorde de volgende handelingen:
      <ol>
       <li>Synchronisatiemappen verwijderen.</li>
       <li>Map met voorinstellingen verwijderen (onder <code>/conf</code>).
       <li>Trigger DM Setup Async Job.</li>
      </ol> </li>
     <li>Wacht op melding van succesvolle synchronisatie in uw Experience Manager Inbox.
     </li>
    </ol> </td>
  </tr>
 </tbody>
</table>
