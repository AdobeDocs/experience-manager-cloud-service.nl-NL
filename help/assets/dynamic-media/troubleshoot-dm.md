---
title: Problemen met Dynamic Media oplossen
description: Meer informatie over tips voor het oplossen van problemen die u kunt proberen wanneer u werkt met afbeeldingen, sets en viewers in Dynamic Media.
contentOwner: Rick Brough
feature: Troubleshooting,Image Sets,Viewers
role: Admin,User
exl-id: 3e8a085f-57eb-4009-a5e8-1080b4835ae2
source-git-commit: 26afff3a39a2a80c1f730287b99f3fb33bff0673
workflow-type: tm+mt
source-wordcount: '1135'
ht-degree: 0%

---

# Problemen met Dynamic Media oplossen {#troubleshooting-dynamic-media-scene-mode}

In het volgende onderwerp wordt het oplossen van problemen voor Dynamic Media beschreven.

## Nieuwe Dynamic Media-configuratie {#new-dm-config}

Zie [Een nieuwe Dynamic Media-configuratie oplossen](/help/assets/dynamic-media/config-dm.md#troubleshoot-dm-config).

## Algemeen (alle activa) {#general-all-assets}

Hier volgen enkele algemene tips en trucs voor alle elementen.

### Eigenschappen van de status van de activasynchronisatie {#asset-synchronization-status-properties}

De volgende eigenschappen van elementen kunnen in CRXDE Lite worden gecontroleerd om te bevestigen dat de middelen van Adobe Experience Manager naar Dynamic Media zijn gesynchroniseerd:

| **Eigenschap** | **Voorbeeld** | **Beschrijving** |
|---|---|---|
| `<object_node>/jcr:content/metadata/dam:scene7ID` | **`a|364266`** | Algemene indicator dat de knoop met Dynamic Media wordt verbonden. |
| `<object_node>/jcr:content/metadata/dam:scene7FileStatus` | **PublishComplete** of fouttekst | Status van het uploaden van middelen naar Dynamic Media. |
| `<object_node>/jcr:content/metadata/dam:scene7File` | **myCompany/myAssetID** | Moet zijn gevuld om URL&#39;s te genereren naar externe middelen van Dynamic Media. |
| `<object_node>/jcr:content/dam:lastSyncStatus` | **succes** of **mislukt:`<error text>`** | Synchronisatiestatus van sets (centrifuges, afbeeldingssets, enzovoort), voorinstellingen voor afbeeldingen, voorinstellingen voor viewers, updates van afbeeldingen met hyperlinks voor een element of afbeeldingen die zijn bewerkt. |

### Synchronisatie-logboekregistratie {#synchronization-logging}

Synchronisatiefouten en problemen worden aangemeld `error.log` (Servermap Experience Manager `/crx-quickstart/logs/`). Er is voldoende logboekregistratie beschikbaar om de hoofdoorzaak van de meeste problemen te bepalen, maar u kunt het logbestand voor DEBUG op het tabblad `com.adobe.cq.dam.ips` pakket maken via de Sling Console ([https://localhost:4502/system/console/slinglog](https://localhost:4502/system/console/slinglog)) om meer informatie te verzamelen.

### Versiebeheer {#version-control}

Wanneer u een bestaand Dynamic Media-element vervangt (dezelfde naam en locatie), kunt u beide elementen behouden of een versie vervangen/maken:

* Als u beide instellingen behoudt, wordt een element gemaakt met een unieke naam voor de URL van het gepubliceerde element. Bijvoorbeeld: `image.jpg` het oorspronkelijke middel is en `image1.jpg` is het nieuw geüploade element.

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
       <li>Controleren of de voorinstelling in het JCR <code>/etc/dam/presets/viewer/&lt;preset&gt; has lastReplicationAction</code> gedefinieerd. Deze locatie is van toepassing als u een upgrade hebt uitgevoerd van Experience Manager 6.x naar 6.4 en de migratie hebt uitgeschakeld. Anders is de locatie <code>/conf/global/settings/dam/dm/presets/viewer</code>.</li>
       <li>Controleer of het element in de JCR <code>dam:scene7FileStatus</code><strong> </strong>onder Metagegevens wordt weergegeven als <code>PublishComplete</code>.</li>
      </ul> </li>
    </ol> </td>
   <td><p>Pagina vernieuwen/naar een andere pagina navigeren en terugkeren (JSP voor side rail moet opnieuw worden samengesteld)</p> <p>Als dat niet werkt:</p>
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
   <td><p>Controleren of het element bevat <code>dam:scene7File</code> in de eigenschappen van metagegevens (CRXDE Lite)</p> </td>
   <td><p>Controleer of alle elementen zijn verwerkt.</p> </td>
  </tr>
  <tr>
   <td>Geüpload element wordt niet weergegeven in elementkiezer</td>
   <td><p>Element controleren heeft eigenschap <code>jcr:content</code> &gt; <strong><code>dam:assetState</code></strong> = <code>processed</code> (CRXDE Lite)</p> </td>
   <td><p>Controleer of alle elementen zijn verwerkt.</p> </td>
  </tr>
  <tr>
   <td>Banner op kaartpresentaties <strong>Nieuw</strong> wanneer de verwerking van het element niet is begonnen</td>
   <td>Element controleren <code>jcr:content</code> &gt; <code>dam:assetState</code> = if <code>unprocessed</code> het is niet opgepikt door de workflow.</td>
   <td>Wacht tot asset is opgehaald via workflow.</td>
  </tr>
  <tr>
   <td>In afbeeldingen of sets wordt de URL van de viewer of de insluitcode niet weergegeven</td>
   <td>Controleer of de viewervoorinstelling is gepubliceerd.</td>
   <td><p>Ga naar <strong>Gereedschappen</strong> &gt; <strong>Activa</strong> &gt; <strong>Voorinstellingen viewer</strong> en publiceert u de viewervoorinstelling.</p> </td>
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
     <li>Videoprofiel moet meer dan één coderingsvoorinstelling bevatten om een AVS-set te genereren (afzonderlijke coderingen worden behandeld als video-inhoud voor MP4-bestanden; voor niet-ondersteunde bestanden wordt deze voorinstelling op dezelfde manier behandeld als niet-verwerkte bestanden).</li>
     <li>Controleer of de video is verwerkt door te bevestigen <code>dam:scene7FileAvs</code> van <code>dam:scene7File</code> in metagegevens.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Wijs een videoprofiel toe aan de map.</li>
     <li>Bewerk het videoprofiel om meerdere coderingsvoorinstellingen op te nemen.</li>
     <li>Wacht tot de video is verwerkt.</li>
     <li>Voordat u de video opnieuw laadt, moet u controleren of de Dynamic Media Encode Video-workflow niet wordt uitgevoerd.<br/> </li>
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
     <li>Controleer of de Dynamic Media Configuration onder Cloud Servicen correct is ingesteld.</li>
     <li>Controleer of de map een videoprofiel heeft. Controleer ook het videoprofiel.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Videoverwerking duurt te lang</td>
   <td><p>U kunt als volgt bepalen of videocodering nog wordt uitgevoerd of dat er een foutstatus is ingevoerd:</p>
    <ul>
     <li>De videostatus controleren <code>https://localhost:4502/crx/de/index.jsp#/content/dam/folder/videomp4/jcr%3Acontent</code> &gt; <code>dam:assetState</code></li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Video-uitvoering ontbreekt</td>
   <td><p>Wanneer video wordt geüpload, maar er geen gecodeerde vertoningen zijn:</p>
    <ul>
     <li>Controleer of aan de map een videoprofiel is toegewezen.</li>
     <li>Controleer of de video is verwerkt door te bevestigen <code>dam:scene7FileAvs</code> in metagegevens.</li>
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

### Probleem: viewervoorinstellingen worden niet gepubliceerd {#viewers-not-published}

**Foutopsporing**

1. Ga door naar de diagnostische pagina van de voorbeeldmanager: `https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html`.
1. Bekijk berekende waarden. Wanneer correct werkend, ziet u het volgende: `_DMSAMPLE status: 0 unsyced assets - activation not necessary _OOTB status: 0 unsyced assets - 0 unactivated assets`.

   >[!NOTE]
   >
   >Het kan ongeveer 10 minuten duren nadat de Dynamic Media-cloudinstellingen zijn geconfigureerd voor synchronisatie van de viewerelementen.

1. Als er niet-geactiveerde elementen overblijven, selecteert u een van de **Alle niet-geactiveerde elementen weergeven** knoppen om details weer te geven.

**Oplossing**

1. Navigeer naar de lijst met voorinstellingen voor viewers in de beheerprogramma&#39;s: `https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html`
1. Selecteer alle voorinstellingen van de viewer en selecteer **Publiceren**.
1. Navigeer terug naar voorbeeldbeheer en controleer of het aantal niet-geactiveerde elementen nu nul is.

### Probleem: met vooraf ingestelde illustraties van de viewer wordt 404 geretourneerd vanuit Voorvertoning in gegevens over elementen of via URL kopiëren/code insluiten {#viewer-preset-404}

**Foutopsporing**

Ga als volgt te werk bij CRXDE Lite:

1. Navigeren naar `<sync-folder>/_CSS/_OOTB` map in uw Dynamic Media-synchronisatiemap (bijvoorbeeld `/content/dam/_CSS/_OOTB`).
1. Zoek het metagegevensknooppunt van het problematische element (bijvoorbeeld `<sync-folder>/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png/jcr:content/metadata/`).
1. Controleren op de aanwezigheid van `dam:scene7*` eigenschappen. Als het element is gesynchroniseerd en gepubliceerd, ziet u de `dam:scene7FileStatus` set is to **PublishComplete**.
1. Poging om de illustratie rechtstreeks via Dynasmic Media aan te vragen door de waarden van de volgende eigenschappen en letterlijke tekenreeksen samen te voegen:

   * `dam:scene7Domain`
   * `"is/content"`
   * `dam:scene7Folder`
   * `<asset-name>`
Voorbeeld: `https://<server>/is/content/myfolder/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png`

**Oplossing**

Als de voorbeeldbestanden of de vooraf ingestelde illustratie van de viewer niet zijn gesynchroniseerd of gepubliceerd, start u het gehele kopiëren/synchronisatieproces opnieuw:

1. Navigeer naar CRXDE Lite.
1. Verwijderen `<sync-folder>/_CSS/_OOTB`.
1. Navigeer naar de CRX Package Manager: `https://localhost:4502/crx/packmgr/`.
1. Zoeken naar een viewerpakket in de lijst; het begint met `cq-dam-scene7-viewers-content`.
1. Selecteren **Opnieuw installeren**.
1. Onder Cloud Servicen, navigeer aan de pagina van de Configuratie van Dynamic Media, dan open de doos van de configuratiedialoog voor uw configuratie Dynamic Media - S7.
1. Geen wijzigingen aanbrengen, selecteer **Opslaan**.
Deze opslaghandeling activeert de logica opnieuw om de voorbeeldelementen, de CSS met voorinstellingen voor viewers en de illustraties te maken en te synchroniseren.

### Probleem: Voorvertoning van afbeelding wordt niet geladen in ontwerpvoorinstellingen van viewer {#image-preview-not-loading}

**Oplossing**

1. Selecteer in Experience Manager het logo van de Experience Manager voor toegang tot de algemene navigatieconsole en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.
1. Navigeer in de linkertrack naar de map met voorbeeldinhoud op de volgende locatie:

   `/content/dam/_DMSAMPLE`

1. Verwijder de `_DMSAMPLE` map.
1. Navigeer in de linkertrack naar de map met voorinstellingen op de volgende locatie:

   `/conf/global/settings/dam/dm/presets/viewer`

1. Verwijder de `viewer` map.
1. Selecteer in de linkerbovenhoek van de pagina CRXDE Lite de optie **[!UICONTROL Save All]**.
1. Selecteer in de linkerbovenhoek van de pagina CRXDE Lite de optie **Terug naar startpunt** pictogram.
1. Maak opnieuw een [Dynamic Media-configuratie in Cloud Servicen](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).
