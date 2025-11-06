---
title: Slimme afbeeldingen
description: Leer hoe Smart Imaging met Adobe Sensei AI de unieke weergavekenmerken van elke gebruiker toepast om de juiste afbeeldingen te leveren die automatisch zijn geoptimaliseerd voor hun ervaring, wat resulteert in betere prestaties en betrokkenheid.
contentOwner: Rick Brough
feature: Asset Management,Renditions,Best Practices
role: User
mini-toc-levels: 2
exl-id: 863784d9-0c91-4deb-8edd-1354a21581c3
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '3184'
ht-degree: 0%

---

# Slimme afbeeldingen {#smart-imaging}

Leer hoe Smart Imaging met Adobe Sensei AI de unieke weergavekenmerken van elke gebruiker toepast om de juiste afbeeldingen te leveren die automatisch zijn geoptimaliseerd voor hun ervaring, wat resulteert in betere prestaties en betrokkenheid.


## Slimme afbeeldingen {#about-smart-imaging}

Smart Imaging-technologie past Adobe Sensei AI-mogelijkheden toe en werkt met bestaande &quot;voorinstellingen voor afbeeldingen&quot;. De functie verbetert de prestaties van de afbeeldingslevering door de afbeeldingsindeling, grootte en kwaliteit automatisch te optimaliseren op basis van de mogelijkheden van de clientbrowser.

En nu een betere Google Core Web Vital score voor LCP (Grootste Inhoudelijke Verf) met verbeterde Smart Imaging, die nu zowel met AVIF als WebP steun wordt geleverd.

>[!IMPORTANT]
>
>Voor Smart Imaging moet u de CDN (Content Delivery Network) gebruiken die buiten de box valt en die wordt meegeleverd bij Adobe Experience Manager - Dynamic Media. Een andere aangepaste CDN wordt niet ondersteund met deze functie.

>[!TIP]
>
>Probeer uit en ontdek de voordelen van Dynamische het beeldbepalingen van Media en Slim Beeld, gebruikend Dynamische Momentopname van Media [__ &#x200B;](https://snapshot.scene7.com/).
>
>Momentopname is een visueel demonstratieprogramma dat is ontworpen om de kracht van dynamische media te illustreren voor geoptimaliseerde en dynamische beeldlevering. Experimenteer met testafbeeldingen of dynamische media-URL&#39;s om de uitvoer van verschillende dynamische media-afbeeldingsmodifiers visueel te bekijken en optimalisaties voor Smart Imaging voor het volgende:
>
>* Bestandsgrootte (met WebP en AVIF levering)
>* Netwerkbandbreedte
>* DPR (Pixelverhouding apparaat)
>
>Om te leren hoe gemakkelijk het Momentopname moet gebruiken, speel de [&#x200B; video van de de opleidingsopleiding van de Momentopname &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot) (3 minuten en 17 seconden).

Smart Imaging profiteert van de extra prestatieverhoging door volledig te zijn geïntegreerd met de eersteklas CDN-service (Content Delivery Network) van Adobe. Deze dienst vindt de optimale route van Internet tussen servers, netwerken, en peerpunten. Het vindt een route die de laagste latentie en het laagste tarief van het pakketverlies in plaats van het gebruiken van de standaardroute op Internet heeft.

De volgende voorbeelden van afbeeldingselementen geven de toegevoegde optimalisatie van Smart Imaging aan:

| Afbeelding (URL) | Miniatuur | Grootte (JPEG) | Grootte (WebP) met slimme beeldverwerking | Grootte (AVIF) met Smart Imaging | % reductie met WebP | % reductie met AVIF |
|---|---|---|---|---|---|---|
| [&#x200B; Beeld 1 &#x200B;](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_6?hei=500&fmt=jpg&qlt=85&resmode=bisharp&op_usm=5,0.125,5,0) | ![&#x200B; picture1 &#x200B;](/help/assets/assets-dm/picture1.png) | 145 kB | 106 kB | 90,2 kB | 26,89% | 37,79% |
| [&#x200B; Beeld 2 &#x200B;](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_3?hei=500&fmt=jpg&qlt=85&resmode=bisharp&op_usm=5,0.125,5,0) | ![&#x200B; picture2 &#x200B;](/help/assets/assets-dm/picture2.png) | 412 kB | 346 kB | 113 kB | 16,01% | 72,57% |
| [&#x200B; Beeld 3 &#x200B;](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_2?hei=500&fmt=jpg&qlt=85&resmode=bisharp&op_usm=5,0.125,5,0) | ![&#x200B; picture3 &#x200B;](/help/assets/assets-dm/picture3.png) | 221 kB | 189 kB | 87,1 kB | 14,47% | 60,58% |
| [&#x200B; Beeld 4 &#x200B;](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_1?hei=500&qlt=85&resmode=bisharp&op_usm=5,0.125,5,0) | ![&#x200B; picture4 &#x200B;](/help/assets/assets-dm/picture4.png) | 594 kB | 545 kB | 286 kB | 8,25% | 51,85% |

Evenals in het bovenstaande voerde Adobe ook een test uit met een grotere set monsters. De indeling AVIF gaf een extra reductie van 20% ten opzichte van WebP, wat een reductie van 27% ten opzichte van JPEG mogelijk maakte. Allemaal met dezelfde visuele kwaliteit. In totaal biedt AVIF in vergelijking met JPEG een gemiddelde reductie van 41%.

Vergelijk WebP en AVIF met PNG, kunt u een 84% groottevermindering met WebP en 87% met AVIF zien. En omdat zowel WebP- als AVIF-indelingen transparantie en meerdere afbeeldingsanimaties ondersteunen, is dit een goede vervanging voor transparante PNG- en GIF-bestanden.

Zie ook [&#x200B; Optimalisering van het Beeld met Formaten van het Beeld van Next-gen (WebP en AVIF) &#x200B;](https://blog.developer.adobe.com/image-optimisation-with-next-gen-image-formats-webp-and-avif-248c75afacc4)

<!-- HIDDEN ON MAY 19, 2022 BASED ON CQDOC-19280 On the mobile web, the challenges are compounded by two factors:

* Large variety of devices with different form factors and high-resolution displays.
* Constrained network bandwidth.

In terms of images, the goal is to serve the best quality images as efficiently as possible. -->

**Voordelen van Slimme Beeldvorming**

Met Slimme afbeeldingen verbetert u de levering van afbeeldingen door de bestandsgrootte automatisch te optimaliseren op basis van de browser, de apparaatweergave en de netwerkvoorwaarden van de gebruiker. Deze aanpak zorgt voor snellere laadtijden en een betere kijkervaring in verschillende omgevingen. Omdat de beelden de meeste ladingstijd van een pagina vormen, kan om het even welke prestatiesverbetering een diepgaande invloed op zaken KPIs zoals het volgende hebben:

* Hogere conversiesnelheden.
* Tijd doorgebracht op een site.
* Lagere stuitpercentages voor de site.

De nieuwste belangrijkste voordelen van de nieuwste Smart Imaging zijn onder andere:

* Ondersteunt de AVIF-indeling van de volgende generatie.
* PNG naar WebP en AVIF ondersteunen nu omzetting met verlies. Omdat PNG een indeling zonder verlies is, gaan eerdere WebP- en AVIF-bewerkingen verloren.
* [Conversie browserindeling](#bfc)
* [Pixelverhouding apparaat](#dpr)
* [Netwerkbandbreedte](#bandwidth)

### Omzetting in browserindeling {#bfc}

Als u Omzetting browserformaat inschakelt door `bfc=on` aan de URL van de afbeelding toe te voegen, worden JPEG en PNG voor verschillende browsers automatisch omgezet in AVIF, WebP met verlies, JPEGXR met verlies en JPEG2000 met verlies. Voor browsers die deze indelingen niet ondersteunen, blijft Smart Imaging de JPEG of PNG gebruiken. Met Slimme afbeeldingen wordt de kwaliteit van de nieuwe indeling samen met de indelingswijziging opnieuw berekend.

U kunt Smart Imaging uitschakelen door `bfc=off` aan de URL van de afbeelding toe te voegen.

Zie ook [&#x200B; bfc &#x200B;](https://experienceleague.adobe.com/nl/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-bfc) in het Dynamische Beeld van Media die en API teruggeven dienen.

### Optimalisatie van apparaatpixelverhoudingen {#dpr}

De pixelverhouding van het apparaat (DPR), ook wel CSS-pixelverhouding genoemd, vertegenwoordigt de relatie tussen de fysieke pixels van een apparaat en logische pixels. Met de opkomst van Retina-schermen neemt de pixelresolutie van moderne mobiele apparaten snel toe.

Als u de pixelverhouding van het apparaat inschakelt, wordt de afbeelding weergegeven met de oorspronkelijke resolutie van het scherm, waardoor deze scherp wordt.

Momenteel is de pixeldichtheid van het beeldscherm afkomstig van Akamai CDN-headerwaarden.

| Toegestane waarden in de URL van een afbeelding | Beschrijving |
|---|---|
| `dpr=off` | Schakel DPR-optimalisatie op individueel afbeeldings-URL-niveau uit. |
| `dpr=on,dprValue` | Overschrijf de DPR-waarde die door Smart Imaging wordt gedetecteerd, met een aangepaste waarde (zoals wordt gedetecteerd door elke logica aan de clientzijde of andere methode). Toegestane waarde voor `dprValue` is een getal groter dan 0. |

>[!NOTE]
>
>* U kunt `dpr=on,dprValue` ook gebruiken als de DPR-instelling op bedrijfsniveau is uitgeschakeld.
>* Als de resulterende afbeelding door DPR-optimalisatie groter is dan de instelling MaxPix Dynamic Media, wordt de breedte van MaxPix altijd herkend door de hoogte-breedteverhouding van de afbeelding te behouden. —>

| Aangevraagde afbeeldingsgrootte | Waarde van pixelverhouding van apparaat (dpr) | Afgeleverde afbeeldingsgrootte |
|---|---|---|
| 816 x 500 | 1 | 816 x 500 |
| 816 x 500 | 2 | 1632 x 1000 |

Zie ook [&#x200B; wanneer het werken met beelden &#x200B;](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#when-working-with-images) en [&#x200B; wanneer het werken met Slim Uitsnijden &#x200B;](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#when-working-with-smart-crop).

### Informatie over netwerkbandbreedteoptimalisatie {#bandwidth}

Als u netwerkbandbreedte inschakelt, wordt automatisch de beeldkwaliteit aangepast die wordt aangeboden op basis van de werkelijke netwerkbandbreedte. Voor een slechte netwerkbandbreedte wordt DPR (Device Pixel Ratio)-optimalisatie automatisch uitgeschakeld, zelfs als deze al is ingeschakeld.

Uw bedrijf kan optimalisatie van de netwerkbandbreedte voor afzonderlijke afbeeldingen uitschakelen door `network=off` aan de afbeeldings-URL toe te voegen.

| Toegestane waarde in de URL van een afbeelding | Beschrijving |
|---|---|
| `network=off` | Hiermee schakelt u netwerkoptimalisatie op individueel afbeeldings-URL-niveau uit. |

DPR en de waarden van de netwerkbandbreedte zijn gebaseerd op de ontdekte cliënt-zijwaarden van gebundelde CDN. Deze waarden zijn soms onjuist. IPhone5 met DPR=2 en iPhone12 met `dpr=3` bijvoorbeeld, beide tonen `dpr=2` . Voor apparaten met hoge resolutie is het echter beter `dpr=2` te verzenden dan `dpr=1` te verzenden. De beste manier om deze onnauwkeurigheid te overwinnen, is echter door DPR op de client-side te gebruiken om u 100% nauwkeurige waarden te geven. En het werkt voor elk apparaat, of het nu Apple is of een ander apparaat dat gelanceerd werd. Zie [&#x200B; het Slimme Beelden van het Gebruik met cliënt-kant de Verhouding van het Pixel van het Apparaat &#x200B;](/help/assets/dynamic-media/client-side-dpr.md).

**Extra zeer belangrijke voordelen van Slimme Beeldvorming**

* Verbeterde Google SEO-classificatie voor webpagina&#39;s die gebruikmaken van de nieuwste Smart Imaging.
* Hiermee wordt geoptimaliseerde inhoud direct (bij uitvoering) weergegeven.
* Gebruikt Adobe Sensei-technologie voor conversie op basis van de kwaliteit (`qlt`) die is opgegeven in de afbeeldingsaanvraag.
* onafhankelijk van TTL (Time to Live). Eerder was een minimale TTL van 12 uur verplicht voor Smart Imaging.
* Eerder waren zowel de oorspronkelijke als de afgeleide afbeeldingen in het cachegeheugen opgeslagen. Het was een proces van twee stappen om de cache ongeldig te maken. In de nieuwste Smart Imaging worden alleen de derivaten in het cachegeheugen opgeslagen, zodat een cachevalidatieproces in één stap mogelijk is.
* Klanten die aangepaste koppen in hun linialen gebruiken, profiteren van de nieuwste functie voor Smart Imaging, omdat deze koppen, in tegenstelling tot de vorige versie van Smart Imaging, niet worden geblokkeerd.

## Hoe Smart Imaging werkt{#how-smart-imaging-works}

Wanneer een consument om een afbeelding vraagt, analyseert Smart Imaging de gebruikerskenmerken en zet deze om in de juiste indeling op basis van de browser. Deze formaatomzettingen worden gedaan op een manier die geen visuele getrouwheid degradeert. Met Slimme afbeeldingen worden afbeeldingen op de volgende manier automatisch omgezet in verschillende indelingen op basis van browsermogelijkheden.

* Automatisch converteren naar AVIF als uw browser de indeling ondersteunt
* Automatisch converteren naar WebP als AVIF-conversie niet gunstig was of de browser AVIF niet ondersteunt
* Automatisch converteren naar JPEG2000 als WebP niet wordt ondersteund door Safari
* Automatisch converteren naar JPEGXR voor IE 9+ of als Edge WebP niet ondersteunt

  | Afbeeldingsindeling | Ondersteunde browsers |
  |---|---|
  | AVIF | [&#x200B; https://caniuse.com/avif](https://caniuse.com/avif) |
  | WebP | [&#x200B; https://caniuse.com/webp](https://caniuse.com/webp) |
  | JPEG 2000 | [&#x200B; https://caniuse.com/jpeg2000](https://caniuse.com/jpeg2000) |
  | JPEGXR | [&#x200B; https://caniuse.com/jpegxr](https://caniuse.com/jpegxr) |

* Voor browsers die deze indelingen niet ondersteunen, wordt de oorspronkelijk aangevraagde afbeeldingsindeling weergegeven.

Als de oorspronkelijke afbeelding kleiner is dan het resultaat van Smart Imaging, wordt de oorspronkelijke afbeelding weergegeven.

## Ondersteuning voor afbeeldingsindelingen in Smart Imaging{#image-format-support}

De volgende afbeeldingsindelingen worden ondersteund voor Smart Imaging:

* JPEG
* PNG

Met Slimme afbeeldingen wordt de kwaliteit van JPEG-afbeeldingsbestandsindelingen opnieuw berekend wanneer deze worden geconverteerd naar een nieuwe indeling.

Voor afbeeldingsbestandsindelingen die transparantie ondersteunen, zoals PNG, kunt u Smart Imaging configureren om AVIF en WebP met verlies te leveren. Voor het omzetten van indelingen met verlies gebruikt Smart Imaging de kwaliteit die wordt vermeld in de URL van de afbeelding, of anders de kwaliteit die is geconfigureerd in het bedrijf Dynamic Media.

## Ondersteuning van de opdracht Beeldserving in Smart Imaging{#imaging-serving-command-support}

De opdrachten Afbeeldingsserver `fmt` en `qlt` worden niet ondersteund. Alle resterende opdrachten worden ondersteund.

## Veelgestelde vragen over Smart Imaging{#smart-imaging-faq}

+++**zijn er vergunningskosten verbonden aan Slimme Beeldvorming?**

Nee. Smart Imaging wordt meegeleverd bij uw bestaande licentie. Deze regel geldt voor Dynamic Media Classic of Experience Manager - Dynamic Media (On-prem, AMS en Experience Manager as a Cloud Service).

>[!IMPORTANT]
>
>Smart Imaging is niet beschikbaar voor Dynamic Media - Hybride klanten.

+++

+++**kan het Slimme Beeld voor om het even welk verzoek worden uitgezet?**

Ja. U kunt Smart Imaging uitschakelen door een van de volgende opties toe te voegen:

* `bfc=off` om Browser Format Conversion uit te schakelen. Zie ook [&#x200B; Browser de Omzetting van het Formaat &#x200B;](#bfc).
* `dpr=off` om de pixelverhouding van het apparaat uit te schakelen. Zie ook {de Verhouding van het Pixel van 0} Apparaat [.](#dpr)
* `network=off` om netwerkbandbreedte uit te schakelen. Zie ook [&#x200B; Bandbreedte van het Netwerk &#x200B;](#network).

+++

+++**is het mogelijk om &quot;Slim Beeld te &quot;stemmen?**

Ja. Slimme afbeeldingen hebben drie opties die u kunt in- of uitschakelen.

* [Conversie browserindeling](#bfc)
* [Pixelverhouding apparaat](#dpr)
* [Netwerkbandbreedte](#network)

+++

+++**werkt het Slimme Beeld met mijn bestaand beeld vooraf instelt?**

Slimme afbeeldingen worden naadloos geïntegreerd met uw bestaande voorinstellingen voor afbeeldingen, waarbij alle afbeeldingsinstellingen worden gerespecteerd.

De enige aanpassingen hebben betrekking op de afbeeldingsindeling, de kwaliteit of beide. Tijdens het omzetten van indelingen behoudt Smart Imaging de volledige visuele getrouwheid op basis van de vooraf ingestelde instellingen, maar het bestand wordt kleiner. U kunt deze functie alleen inschakelen door `bfc=on` , `dpr=on,dprValue` , `network=on` of alle drie parameterinstellingen toe te voegen aan uw bestaande URL&#39;s of voorinstellingen.

Een voorinstelling voor afbeeldingen geeft bijvoorbeeld een JPEG-indeling op van 500 × 500 pixels, met `quality=85` en `unsharp mask=0.1,1,5` . Smart Imaging detecteert of de gebruiker zich in een Chrome-browser bevindt. Vervolgens wordt de afbeelding omgezet in een webpagina met dezelfde afmetingen (500 × 500) en een onscherp masker dat overeenkomt met de JPEG-instellingen. Het systeem vergelijkt dan de dossiergrootte van WebP en de versies van JPEG en dient kleinere aan de gebruiker.

+++

<!-- OLD VERSION BELOW AS PER CQDOC-22085>
Yes. Smart Imaging works with your existing image presets and observes all your image settings. What changes is the image format, or the quality setting, or both. For format conversion, Smart Imaging maintains full visual fidelity as defined by your image preset settings, but at a smaller file size.

For example, suppose that an image preset is defined with JPEG format, size 500 x 500, quality=85, and unsharp mask=0.1,1,5. When Smart Imaging detects that a user is on a Chrome browser, the image is converted to WebP format, with size 500 x 500. And, unsharp mask=0.1,1,5 is at a WebP quality that matches a JPEG quality of 85 as close as possible. The footprint of that WebP conversion is compared with the JPEG, and the smaller of the two is returned. -->

<!-- QUESTION BELOW WAS REMOVED AS PER CQDOC-22085

+++**Do I have to change any URLs, image presets, or deploy new code on my site?**

No. Smart Imaging works seamlessly with your existing image URLs and image presets. In addition, Smart Imaging does not require you to add code to your website to detect a user's browser. All of this functionality is handled automatically.

<!-- Smart Imaging works seamlessly with your existing image URLs and image presets if you configure Smart Imaging on your existing custom domain. In addition, Smart Imaging does not require you to add any code on your website to detect a user's browser. It is all handled automatically.

In case you must configure a new custom domain to use Smart Imaging, the URLs must be updated to reflect this custom domain.

To understand pre-requisites for Smart Imaging, see [Am I eligible to use Smart Imaging?](#am-i-eligible-to-use-smart-imaging) -->

<!-- OLD As mentioned earlier, Smart Imaging supports only JPEG and PNG image formats. For other formats, you need to append the `bfc=off` modifier to the URL as described earlier. 

-->

+++**werkt het Slimme Beelden met HTTPS? Hoe zit het met HTTP/2?**

Ja, op beide vragen. Slimme afbeeldingen werken met afbeeldingen die via HTTP of HTTPS worden geleverd. Bovendien werkt het ook via HTTP/2.
+++

+++**Ben ik verkiesbaar om Slimme Beelden te gebruiken?**

Smart Imaging is klaar om direct voor alle klanten te worden gebruikt. Als u van de voordelen ervan wilt genieten, voegt u `bfc=on` of `dpr=on,dprValue` , of `network=on` , of alle drie parameterinstellingen toe aan uw bestaande URL&#39;s of voorinstellingen.

Als u Smart Imaging wilt activeren, moet de Dynamic Media Classic- of Dynamic Media-account van uw bedrijf de Adobe-gebundelde CDN (Content Delivery Network) opnemen in uw licentie.

+++

+++**wat is het proces om Slim Beeld op een rekening toe te laten?**

Als u Smart Imaging wilt gaan gebruiken, voegt u `bfc=on` , `dpr=on,dprValue` of `network=on` of alle drie parameterinstellingen toe aan uw bestaande URL&#39;s of voorinstellingen. Als u deze wijzigingen liever niet handmatig doorvoert, kunt u Smart Imaging standaard inschakelen door een ondersteuningscase te maken.

Geef bij het maken van de draagtas op welke functies voor Smart Imaging u op uw account wilt activeren:

* Conversie browserindeling (WebP of AVIF)
* Optimalisatie van netwerkbandbreedte

>[!NOTE]
>
>DPR vereist aanpassingen aan de client-side om het juiste `dprValue` te bepalen. Daarom raadt Adobe aan DPR via URL&#39;s in te schakelen door `dpr=on,dprValue` toe te voegen.

**om een steungeval tot stand te brengen om Slimme Beeldvorming op uw rekening toe te laten:**

1. [&#x200B; Gebruik Admin Console om de verwezenlijking van een nieuw steungeval &#x200B;](https://helpx.adobe.com/nl/enterprise/using/support-for-experience-cloud.html) te beginnen.
1. Geef de volgende informatie op in uw ondersteuningsgeval:

   * **Primaire contactdetails:**

      * Geef uw naam, e-mail en telefoonnummer op.

   * **Slimme het Bewaren eigenschappen om toe te laten:**

      * Geef een overzicht van de mogelijkheden die u voor uw account wilt:

         * Conversie van browserindeling: WebP of AVIF
         * Optimalisatie van netwerkbandbreedte
         * DPR: DPR vereist aanpassingen aan de clientzijde om het juiste `dprValue` te bepalen. Daarom raadt Adobe aan DPR via URL&#39;s in te schakelen door `dpr=on,dprValue` toe te voegen.

   * **Domein voor Slimme Beeldvorming:**

      * Alle relevante domeinen weergeven, zoals *`company.com`* of *`mycompany.scene7.com`*
      * Smart Imaging ondersteunt zowel algemene als aangepaste domeinen.
      * Om uw domeinen te identificeren, open de [&#x200B; Desktoptoepassing van Dynamic Media Classic &#x200B;](https://experienceleague.adobe.com/nl/docs/dynamic-media-classic/using/getting-started/signing-out#getting-started) en teken binnen aan uw bedrijfrekening.

         1. Navigeer naar **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL General Settings]** .
         1. Zoek het veld **[!UICONTROL Published Server Name]** om uw domein te bevestigen.
         1. Controleer of u de Adobe CDN gebruikt in plaats van een CDN die door een andere provider wordt beheerd.

   * **wijs HTTP/2 steun aan:**

      * Geef op of u Smart Imaging nodig hebt om te werken via HTTP/2.

1. Adobe Klantenondersteuning biedt standaard de vereiste functies voor Smart Imaging, zodat het niet nodig is om handmatig parameters aan URL&#39;s toe te voegen.
1. Adobe raadt u aan om de tijd voor live (TTL) in te stellen op ten minste 24 uur om de prestaties te maximaliseren door caching.
De TTL aanpassen:

   1. **voor Dynamic Media Classic:**
      1. Navigeer naar **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL Publish Setup]** > **[!UICONTROL Image Server]** .
      1. Stel de waarde van **[!UICONTROL Default Client Cache Time To Live]** in op 24 uur of meer.
   1. **voor Dynamische Media op Adobe Experience Manager:**
      1. Volg [&#x200B; deze instructies &#x200B;](/help/assets/dynamic-media/config-dm.md).
      1. Stel de waarde **[!UICONTROL Expiration]** in op 24 uur of langer.

+++

+++**wanneer is een rekening die met Slimme Beelden wordt toegelaten?**

De processen van de Steun van de klant verzoeken in de orde dat zij hen, na de Lijst van de Wacht ontvangen.

>[!NOTE]
>
>Er kan een lange aanlooptijd zijn, omdat het inschakelen van Smart Imaging inhoudt dat Adobe de cache wist. Daarom kunnen slechts een paar klantenovergangen op elk bepaald ogenblik worden behandeld.

+++

+++**zijn er risico&#39;s met het gebruiken van Slimme Beeldvorming?**

Er is geen risico voor een klantenwebpagina. Bij de overgang naar Smart Imaging wordt de CDN-cache echter wel gewist. Bij deze bewerking gaat u naar een nieuwe configuratie van Dynamic Media Classic of Dynamic Media op Experience Manager.

Tijdens de eerste overgang raakten de niet-in cache opgeslagen afbeeldingen rechtstreeks op de oorspronkelijke Adobe-servers totdat het cachegeheugen opnieuw wordt opgebouwd. Als zodanig is Adobe van plan om enkele klantovergangen tegelijk af te handelen, zodat acceptabele prestaties behouden blijven wanneer verzoeken van de oorsprong worden opgehaald. Voor de meeste klanten, wordt het geheime voorgeheugen volledig opnieuw opgebouwd bij CDN binnen ongeveer één tot twee dagen.

+++

+++**kan ik verifiëren als het Slimme Beeld werkt?**

Ja. U kunt het volgende doen:

1. Wanneer uw account is geconfigureerd met Smart Imaging, laadt u een URL voor een Dynamic Media Classic- of Adobe Experience Manager-afbeelding - Dynamic Media in de browser.
1. Open het Chrome-ontwikkelaarsvenster door in de browser naar **[!UICONTROL View]** > **[!UICONTROL Developer]** > **[!UICONTROL Developer Tools]** te gaan. Of kies een ander browserontwikkelaarsgereedschap van uw keuze.

1. Zorg ervoor dat de cache is uitgeschakeld wanneer de ontwikkelprogramma&#39;s zijn geopend.

   * In Windows® navigeert u naar de instellingen in het deelvenster voor ontwikkelaars en schakelt u het selectievakje **[!UICONTROL Disable cache (while devtools is open)]** in.
   * Selecteer in macOS onder het tabblad **[!UICONTROL Network]** in het deelvenster Ontwikkelaar de optie **[!UICONTROL disable cache]** .

1. Waarnemen dat het inhoudstype wordt omgezet in de juiste indeling. In de volgende schermafbeelding ziet u een PNG-afbeelding die op Chrome dynamisch wordt omgezet in WebP. Als voor uw domein AVIF is ingeschakeld, kunt u ook AVIF in het Inhoudstype zien.
1. Herhaal deze test voor verschillende browsers en gebruikersomstandigheden.

>[!NOTE]
>
>Niet alle afbeeldingen worden omgezet. Smart Imaging bepaalt of de conversie de prestaties kan verbeteren. Soms wordt de afbeelding niet geconverteerd als er geen verwachte prestatieverbetering is of de indeling niet JPEG of PNG is.

![&#x200B; image2017-11-14_15398 &#x200B;](assets/image2017-11-14_15398.png)

+++

+++**is er een manier om de voordelen van Slim Beeld te kennen?**

Ja. De koptekst Slimme afbeeldingen bepaalt de voordelen van Slimme afbeeldingen. Wanneer Slimme afbeeldingen is ingeschakeld, kunt u na een verzoek om een afbeelding onder de kop **[!UICONTROL Response Headers]** `-X-Adobe-Smart-Imaging` zien zoals in het volgende gemarkeerde voorbeeld:

![&#x200B; Slimme beeldende kopbal &#x200B;](/help/assets/dynamic-media/assets/smartimagingheader.png)

Deze koptekst geeft het volgende aan:

* Smart Imaging werkt voor het bedrijf.
* Een positieve waarde betekent dat de conversie is gelukt. In dit geval wordt een nieuwe WebP-afbeelding geretourneerd.
* Een negatieve waarde betekent dat de conversie niet is gelukt. In dat geval wordt de oorspronkelijke opgevraagde afbeelding geretourneerd (standaard JPEG, indien niet opgegeven).
* Een positieve waarde geeft het verschil in bytes tussen de gevraagde afbeelding en de nieuwe afbeelding aan. In het bovenstaande voorbeeld zijn de opgeslagen bytes `75048` of ongeveer 75 KB voor één afbeelding.
* Een negatieve waarde betekent dat de gevraagde afbeelding kleiner is dan de nieuwe afbeelding. Het verschil in negatieve grootte wordt getoond, maar het bediende beeld is het originele gevraagde beeld slechts.

>[!NOTE]
>
>**x-Adobe-Smart-Imaging = -1 met WebP die wordt geleverd**
>
>Als de waarde van `X-Adobe-Smart-Imaging` -1 is en WebP nog steeds wordt geleverd, is Smart Imaging actief. De groottevoordelen zijn echter niet berekend vanwege een verouderde cache. U kunt `cache=update` (slechts één keer) in de URL van de afbeelding gebruiken om dit probleem op te lossen.
>Een voorbeeld van de modifier:
>`https://smartimaging.scene7.com/is/image/SmartImaging/sample1?cache=update`
>Als u de gehele cache wilt ongeldig maken, moet u een ondersteuningscase maken.

+++

+++**kan ik optimalisering AVIF in Slimme Beeldvorming onbruikbaar maken?**

Ja. Als u terug naar het dienen WebP door gebrek wilt schakelen, creeer een steungeval voor het zelfde. Zoals gebruikelijk, kunt u Smart Imaging uitzetten door de parameter `bfc=off` aan URL van het beeld toe te voegen. U kunt WebP of AVIF echter niet selecteren in de URL-optie voor Smart Imaging. Deze mogelijkheid blijft behouden op het niveau van uw bedrijfsaccount.

+++

+++**waarom mijn verzoek ontbreekt wanneer ik een URL met fmt=tif op Webbrowser van Chrome heb?**

Deze fout treedt niet op als Smart Imaging niet is ingeschakeld voor uw account. Slimme afbeeldingen werken alleen in JPEG- of PNG-indeling.

U kunt deze fout voorkomen door:

* Geef JPEG of PNG op, of
* Gebruik de optie `fmt` helemaal niet, of
* Gebruik een browservoorkeursindeling die wordt gedefinieerd door Smart Imaging. U kunt bijvoorbeeld WebP gebruiken voor de Chrome-webbrowser.

+++

+++**Kan ik een beeld van TIFF van URL van een beeld downloaden?**

Ja. Voeg `fmt=tif` en `bfc=off` toe aan het URL-pad van de afbeelding.

+++

+++**beheert het Slimme Beeld beeldformaat en de montages van de beeldkwaliteit?**

Ja. Voor Smart Imaging worden zowel de indeling als de kwaliteit gebruikt. De overige parameters blijven ongewijzigd, indien gevraagd in de URL van de afbeelding.

+++

+++**kan ik een minimum en maximumkwaliteit plaatsen die?**

Nee. Op dit moment bestaat een dergelijke voorziening niet.

+++

+++**past Slimme Beeldvorming de percenten kwaliteitsuitvoer aan die plaatsen?**

Ja. Met Slimme afbeeldingen wordt het kwaliteitspercentage automatisch aangepast. Deze kwaliteit wordt bepaald met behulp van een computerleeralgoritme dat door Adobe is ontwikkeld. Dit percentage is niet bereikspecifiek.

+++

+++**worden slechts JPEG en PNG vervangen door Slimme Beeldvorming?**

Ja. Deze functionaliteit werkt alleen voor JPEG en PNG.

+++

+++**waarom is JPEG soms teruggekeerd aan Chrome in plaats van WebP?**

Slimme afbeeldingen bepalen of de conversie nuttig is. Het retourneert alleen de nieuwe afbeelding van de conversie.

+++

+++**waarom werkt de Verhouding van het Pixel van het Apparaat (dpr) niet met samengestelde beelden?**

Als een samengestelde afbeelding te veel lagen bevat, kan de dpr-functionaliteit worden beïnvloed wanneer u een positiewijziging gebruikt. Dit probleem is bekend en wordt opgelost in toekomstige versies van Smart Imaging. Als andere functies voor Smart Imaging niet naar behoren werken, kunt u een ondersteuningscase maken om het probleem te melden.

+++

+++**waarom zet het Slimme Beeld PNG in lossless WebP/AVIF om?**

Omdat PNG een indeling zonder gegevensverlies is, zijn eerdere WebP- en AVIF-bewerkingen zonder gegevensverlies uitgevoerd. Hierdoor is het bestand groter dan u had verwacht. Smart Imaging ondersteunt nu omzetten met verlies. U kunt de optie `cache=update` (slechts één keer) in een afbeeldingsaanvraag gebruiken om dit probleem op te lossen. Een voorbeeld van het gebruik van deze modifier:

`https://smartimaging.scene7.com/is/image/SmartImaging/sample1?cache=update`

Om het volledige geheime voorgeheugen ongeldig te maken, moet u een steungeval creëren die om zulk een inspanning verzoekt.

+++

+++**kan ik blijven gebruikend PNG aan verliesloze omzetting in Slimme Beeldvorming?**

Ja. Smart Imaging ondersteunt nu verliesconversie op basis van het kwaliteitsniveau. U kunt de omzetting zonder verlies blijven gebruiken door de kwaliteit in te stellen op 100, via de instellingen van uw bedrijf of door `qlt=100` toe te voegen aan het URL-pad van de afbeelding.

+++







<!-- ## If Smart Imaging manages the quality settings, are there minimums and maximums I can set? For example, is it possible to set "no lower than 60" and "no greater than 80 quality"? {#minimum-maximum}

There is no such provisioning ability in the current Smart Imaging. -->

<!-- ## Sometimes a JPEG image is returned to Chrome instead of a WebP image. Why does that change happen? {#jpeg-webp}

Smart Imaging determines if the conversion is beneficial or not. It returns the new image only if the conversion results in a smaller file size with comparable quality.

How does Smart Imaging DPR optimization work with Adobe Experience Manager Sites components and Dynamic Media viewers?

* Experience Manager Sites Core Components are configured by default for DPR optimization. To avoid oversized images owing to server-side Smart Imaging DPR optimization, `dpr=off` is always added to Experience Manager Sites Core Components Dynamic Media images.
* Given Dynamic Media Foundation Component is configured by default for DPR optimization, to avoid oversized images owing to server-side Smart Imaging DPR optimization, `dpr=off` is always added to Dynamic Media Foundation Component images. Even if customer deselects DPR optimization in DM Foundation Component, server-side Smart Imaging DPR does not kick in. In summary, in the DM Foundation Component, DPR optimization comes into effect based on DM Foundation Component level setting only.
* Any viewer side DPR optimization works in tandem with server-side Smart Imaging DPR optimization, and does not result in over-sized images. In other words, wherever DPR is handled by the viewer, such as the main view only in a zoom-enabled viewer, the server-side Smart Imaging DPR values are not triggered. Likewise, wherever viewer elements, such as swatches and thumbnails, do not have DPR handling, the server-side Smart Imaging DPR value is triggered.

See also [When working with images](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#when-working-with-images) and [When working with Smart Crop](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#when-working-with-smart-crop).

>[!MORELIKETHIS]
>
>* [Image optimization with next generation image formats WebP and AVIF](https://medium.com/adobetech/image-optimisation-with-next-gen-image-formats-webp-and-avif-248c75afacc4). 
-->
