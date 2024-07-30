---
title: Slimme afbeeldingen
description: Leer hoe Smart Imaging met Adobe Sensei AI de unieke weergavekenmerken van elke gebruiker toepast om automatisch de juiste afbeeldingen te leveren die geoptimaliseerd zijn voor hun ervaring, wat resulteert in betere prestaties en betrokkenheid.
contentOwner: Rick Brough
feature: Asset Management,Renditions,Best Practices
role: User
mini-toc-levels: 2
exl-id: 863784d9-0c91-4deb-8edd-1354a21581c3
source-git-commit: 22de8ac77af27114099de2f6b4349232524cb94f
workflow-type: tm+mt
source-wordcount: '3401'
ht-degree: 0%

---

# Slimme afbeeldingen {#smart-imaging}

## Slimme afbeeldingen{#about-smart-imaging}

Smart Imaging-technologie past Adobe Sensei AI-mogelijkheden toe en werkt met bestaande &quot;voorinstellingen voor afbeeldingen&quot;. De functie verbetert de prestaties van de afbeeldingslevering door de afbeeldingsindeling, grootte en kwaliteit automatisch te optimaliseren op basis van de mogelijkheden van de clientbrowser.

En nu een betere Google Core Web Vital score voor LCP (de grootste Inhoudelijke Verf) met verbeterde Smart Imaging die nu met zowel AVIF als WebP steun wordt geleverd.

>[!IMPORTANT]
>
>Voor Smart Imaging moet u de CDN (Content Delivery Network) gebruiken die buiten de box valt en die is meegeleverd bij Adobe Experience Manager - Dynamic Media. Een andere aangepaste CDN wordt niet ondersteund met deze functie.

>[!TIP]
>
>Probeer uit en ontdek de voordelen van de beeldbepalingen van Dynamic Media en Slimme Beeldvorming, gebruikend de Momentopname van Dynamic Media [__ ](https://snapshot.scene7.com/).
>
> Momentopname is een visueel demonstratieprogramma dat is ontworpen om de kracht van Dynamic Media te illustreren voor geoptimaliseerde en dynamische beeldlevering. Experimenteer met testafbeeldingen of Dynamic Media-URL&#39;s om visueel de uitvoer van verschillende Dynamic Media-afbeeldingsmodifiers en Smart Imaging-optimalisaties te bekijken voor:
>
>* Bestandsgrootte (met WebP en AVIF levering)
>* Netwerkbandbreedte
>* DPR (Pixelverhouding apparaat)
>
>Om te leren hoe gemakkelijk het Momentopname moet gebruiken, speel de [ video van de de opleidingsopleiding van de Momentopname ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot.html?lang=en) (3 minuten en 17 seconden).

De slimme Beeldvorming profiteert van de extra prestatiesverhoging van volledig met de best-in-klasse van de Adobe dienst CDN (het Netwerk van de Levering van de Inhoud) wordt geïntegreerd. Deze dienst vindt de optimale route van Internet tussen servers, netwerken, en peerpunten. Het vindt een route die de laagste latentie en het laagste tarief van het pakketverlies in plaats van het gebruiken van de standaardroute op Internet heeft.

De volgende voorbeelden van afbeeldingselementen geven de toegevoegde optimalisatie van Smart Imaging aan:

| Afbeelding (URL) | Miniatuur | Grootte (JPEG) | Grootte (WebP) met slimme beeldverwerking | Grootte (AVIF) met Smart Imaging | % reductie met WebP | % reductie met AVIF |
|---|---|---|---|---|---|---|
| [ Beeld 1 ](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_6?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![ picture1 ](/help/assets/assets-dm/picture1.png) | 145 kB | 106 kB | 90,2 kB | 26,89% | 37,79% |
| [ Beeld 2 ](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_3?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![ picture2 ](/help/assets/assets-dm/picture2.png) | 412 kB | 346 kB | 113 kB | 16,01% | 72,57% |
| [ Beeld 3 ](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_2?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![ picture3 ](/help/assets/assets-dm/picture3.png) | 221 kB | 189 kB | 87,1 kB | 14,47% | 60,58% |
| [ Beeld 4 ](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_1?hei=500&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![ picture4 ](/help/assets/assets-dm/picture4.png) | 594 kB | 545 kB | 286 kB | 8,25% | 51,85% |

Net als hierboven heeft Adobe ook een test uitgevoerd met een grotere set monsters. Het formaat AVIF verstrekte 20% extra groottevermindering boven WebP, die 27% vermindering boven JPEG verstrekte. Allemaal van dezelfde visuele kwaliteit. In totaal kan AVIF tot 41% gemiddelde grootte verkleinen in vergelijking met JPEG.

Vergelijk WebP en AVIF met PNG, kunt u een 84% groottevermindering met WebP en 87% met AVIF zien. En omdat zowel WebP- als AVIF-indelingen transparantie en meerdere afbeeldingsanimaties ondersteunen, is dit een goede vervanging voor transparante PNG- en GIF-bestanden.

Zie ook [ Optimalisering van het Beeld met Formaten van het Beeld van Next-gen (WebP en AVIF) ](https://blog.developer.adobe.com/image-optimisation-with-next-gen-image-formats-webp-and-avif-248c75afacc4)

<!-- HIDDEN ON MAY 19, 2022 BASED ON CQDOC-19280 On the mobile web, the challenges are compounded by two factors:

* Large variety of devices with different form factors and high-resolution displays.
* Constrained network bandwidth.

In terms of images, the goal is to serve the best quality images as efficiently as possible. -->

**Voordelen van Slimme Beeldvorming**

Slimme afbeeldingen zorgen voor betere prestaties bij het leveren van afbeeldingen doordat de bestandsgrootte van afbeeldingen automatisch wordt geoptimaliseerd op basis van de clientbrowser die wordt gebruikt, de apparaatweergave en de netwerkvoorwaarden. Omdat de beelden het grootste deel van de ladingstijd van een pagina vormen, kan om het even welke prestatiesverbetering een diepgaande invloed op zaken KPIs zoals hogere omzettingspercentages, tijd die aan een plaats wordt doorgebracht, en lagere plaats hebben stuitende tarieven.

De nieuwste belangrijkste voordelen van de nieuwste Smart Imaging zijn onder andere:

* Ondersteuning voor AVIF-indeling van de volgende generatie.
* PNG naar WebP en AVIF ondersteunen nu omzetting met verlies. Omdat PNG een indeling zonder verlies is, gaan eerdere WebP- en AVIF-bewerkingen verloren.
* [Conversie browserindeling](#bfc)
* [Pixelverhouding apparaat](#dpr)
* [Netwerkbandbreedte](#bandwidth)

### Over omzetten in browserindeling {#bfc}

Als u Omzetting browserformaat inschakelt door `bfc=on` aan de URL van de afbeelding toe te voegen, worden JPEG en PNG voor verschillende browsers automatisch omgezet in een wegwerpversie met verlies in AVIF, WebP met verlies, JPEGXR met verlies en JPEG2000 met verlies. Voor browsers die deze indelingen niet ondersteunen, blijft Smart Imaging de JPEG of PNG gebruiken. De kwaliteit van de nieuwe indeling wordt samen met de indeling opnieuw berekend door Slimme afbeeldingen te maken.

U kunt Smart Imaging ook uitschakelen door `bfc=off` aan de URL van de afbeelding toe te voegen.

Zie ook [ bfc ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-bfc.html?lang=en) in het Beeld van Dynamic Media die en API teruggeven.

### Info over de optimalisatie van de pixelverhouding van apparaten {#dpr}

Pixelverhouding van apparaat (DPR) - ook wel CSS-pixelverhouding genoemd - is de relatie tussen de fysieke pixels van een apparaat en logische pixels. Vooral met de komst van Retina-schermen groeit de pixelresolutie van moderne mobiele apparaten snel.

Als u de pixelverhouding van het apparaat inschakelt, wordt de afbeelding weergegeven met de oorspronkelijke resolutie van het scherm, waardoor deze scherp wordt.

Momenteel is de pixeldichtheid van het beeldscherm afkomstig van Akamai CDN-headerwaarden.

| Toegestane waarden in de URL van een afbeelding | Beschrijving |
|---|---|
| `dpr=off` | Schakel DPR-optimalisatie op individueel afbeeldings-URL-niveau uit. |
| `dpr=on,dprValue` | Overschrijf de DPR-waarde die door Smart Imaging wordt gedetecteerd, met een aangepaste waarde (zoals wordt gedetecteerd door elke logica aan de clientzijde of andere methode). Toegestane waarde voor `dprValue` is een getal groter dan 0. |

>[!NOTE]
>
>* U kunt `dpr=on,dprValue` ook gebruiken als de DPR-instelling op bedrijfsniveau is uitgeschakeld.
>* Als de resulterende afbeelding door DPR-optimalisatie groter is dan de Dynamic Media-instelling MaxPix, wordt de breedte van MaxPix altijd herkend door de hoogte-breedteverhouding van de afbeelding te behouden. —>

| Aangevraagde afbeeldingsgrootte | Waarde van pixelverhouding van apparaat (dpr) | Afgeleverde afbeeldingsgrootte |
|---|---|---|
| 816 x 500 | 1 | 816 x 500 |
| 816 x 500 | 2 | 1632 x 1000 |

Zie ook [ wanneer het werken met beelden ](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#when-working-with-images) en [ wanneer het werken met Slim Uitsnijden ](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#when-working-with-smart-crop).

### Info over netwerkbandbreedte optimaliseren {#bandwidth}

Als u Netwerkbandbreedte inschakelt, wordt automatisch de beeldkwaliteit aangepast die wordt aangeboden op basis van de werkelijke netwerkbandbreedte. Voor een slechte netwerkbandbreedte wordt DPR (Device Pixel Ratio)-optimalisatie automatisch uitgeschakeld, zelfs als deze al is ingeschakeld.

Uw bedrijf kan desgewenst de optimalisatie van de netwerkbandbreedte op het afzonderlijke afbeeldingsniveau uitschakelen door `network=off` aan de URL van de afbeelding toe te voegen.

| Toegestane waarde in de URL van een afbeelding | Beschrijving |
|---|---|
| `network=off` | Hiermee schakelt u netwerkoptimalisatie op individueel afbeeldings-URL-niveau uit. |

DPR en de waarden van de netwerkbandbreedte zijn gebaseerd op de ontdekte cliënt-zijwaarden van gebundelde CDN. Deze waarden zijn soms onjuist. IPhone5 met DPR=2 en iPhone12 met `dpr=3` bijvoorbeeld, beide tonen `dpr=2` . Voor apparaten met hoge resolutie is het echter beter `dpr=2` te verzenden dan `dpr=1` te verzenden. De beste manier om deze onnauwkeurigheid te overwinnen, is echter door DPR op de client-side te gebruiken om u 100% nauwkeurige waarden te geven. En het werkt voor elk apparaat, of het nu Apple is of een ander apparaat dat gelanceerd werd. Zie [ het Slimme Beelden van het Gebruik met cliënt-kant de Verhouding van het Pixel van het Apparaat ](/help/assets/dynamic-media/client-side-dpr.md).

**Extra zeer belangrijke voordelen van Slimme Beeldvorming**

* Verbeterde Google SEO-classificatie voor webpagina&#39;s die gebruikmaken van de nieuwste Smart Imaging.
* Hiermee wordt geoptimaliseerde inhoud direct (bij uitvoering) weergegeven.
* Gebruikt Adobe Sensei-technologie voor conversie op basis van de kwaliteit (`qlt`) die is opgegeven in de afbeeldingsaanvraag.
* onafhankelijk van TTL (Time to Live). Eerder was een minimale TTL van 12 uur verplicht voor Smart Imaging.
* Eerder waren zowel de oorspronkelijke als de afgeleide afbeeldingen in het cachegeheugen opgeslagen. Het was een proces van twee stappen om de cache ongeldig te maken. Bij de nieuwste Smart Imaging worden alleen de derivaten in het cachegeheugen opgeslagen, zodat een cachevalidatieproces in één stap mogelijk is.
* Klanten die aangepaste koppen in hun linialen gebruiken, profiteren van de nieuwste functie voor Smart Imaging, omdat deze koppen, in tegenstelling tot de vorige versie van Smart Imaging, niet worden geblokkeerd. Bijvoorbeeld, &quot;het Timing staat Oorsprong&quot;toe, &quot;x-Robot&quot;zoals gesuggereerd in [ voeg een waarde van de douanekopbal aan beeldreacties toe|Dynamic Media Classic ](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/add-custom-header-val-image.html).

## Hoe Smart Imaging werkt{#how-smart-imaging-works}

Wanneer een consument om een afbeelding vraagt, controleert Smart Imaging de gebruikerskenmerken en wordt deze op basis van de gebruikte browser omgezet in de juiste afbeeldingsindeling. Deze formaatomzettingen worden gedaan op een manier die geen visuele getrouwheid degradeert. Met Slimme afbeeldingen worden afbeeldingen op de volgende manier automatisch omgezet in verschillende indelingen op basis van browsermogelijkheden.

* Automatisch converteren naar AVIF als de browser de indeling ondersteunt
* Automatisch converteren naar WebP als AVIF-conversie niet gunstig was of als AVIF niet door de browser wordt ondersteund
* Automatisch converteren naar JPEG2000 als WebP niet wordt ondersteund door Safari
* Automatisch converteren naar JPEGXR voor IE 9+ of als Edge WebP niet ondersteunt

  | Afbeeldingsindeling | Ondersteunde browsers |
  |---|---|
  | AVIF | [ https://caniuse.com/avif](https://caniuse.com/avif) |
  | WebP | [ https://caniuse.com/webp](https://caniuse.com/webp) |
  | JPEG 2000 | [ https://caniuse.com/jpeg2000](https://caniuse.com/jpeg2000) |
  | JPEGXR | [ https://caniuse.com/jpegxr](https://caniuse.com/jpegxr) |

* Voor browsers die deze indelingen niet ondersteunen, wordt de oorspronkelijk aangevraagde afbeeldingsindeling weergegeven.

Als de oorspronkelijke afbeelding kleiner is dan het resultaat van Smart Imaging, wordt de oorspronkelijke afbeelding weergegeven.

## Ondersteuning voor afbeeldingsindelingen in Smart Imaging{#image-format-support}

De volgende afbeeldingsindelingen worden ondersteund voor Smart Imaging:

* JPEG
* PNG

Voor de indeling van JPEG-afbeeldingsbestanden wordt de kwaliteit van de nieuwe indeling opnieuw berekend door Smart Imaging.

Voor afbeeldingsbestandsindelingen die transparantie ondersteunen, zoals PNG, kunt u Smart Imaging configureren om AVIF en WebP met verlies te leveren. Voor de omzetting van de verliesindeling wordt bij Smart Imaging de kwaliteit gebruikt die wordt vermeld in de URL van de afbeelding, of anders de kwaliteit die is geconfigureerd in het Dynamic Media-bedrijfsaccount.

## Ondersteuning van de opdracht Beeldserving in Smart Imaging{#imaging-serving-command-support}

De opdrachten Afbeeldingsserver `fmt` en `qlt` worden niet ondersteund. Alle resterende opdrachten worden ondersteund.

## Veelgestelde vragen over Smart Imaging{#smart-imaging-faq}

+++**zijn er vergunningskosten verbonden aan Slimme Beeldvorming?**

Nee. Smart Imaging wordt meegeleverd bij uw bestaande licentie. Deze regel geldt voor Dynamic Media Classic of Experience Manager - Dynamic Media (On-prem, AMS en as a Cloud Service Experience Manager).

>[!IMPORTANT]
>
>Smart Imaging is niet beschikbaar voor Dynamic Media - Hybride klanten.

+++

+++**kan het Slimme Beeld voor om het even welk verzoek worden uitgezet?**

Ja. U kunt Smart Imaging uitschakelen door een van de volgende opties toe te voegen:

* `bfc=off` om Browser Format Conversion uit te schakelen. Zie ook [ Browser de Omzetting van het Formaat ](#bfc).
* `dpr=off` om de pixelverhouding van het apparaat uit te schakelen. Zie ook {de Verhouding van het Pixel van 0} Apparaat ](#dpr).[
* `network=off` om netwerkbandbreedte uit te schakelen. Zie ook [ Bandbreedte van het Netwerk ](#network).

+++

+++**is het mogelijk om &quot;Slim Beeld te &quot;stemmen?**

Ja. Slimme afbeeldingen hebben drie opties die u kunt in- of uitschakelen.

* [Conversie browserindeling](#bfc)
* [Pixelverhouding apparaat](#dpr)
* [Netwerkbandbreedte](#network)

+++

+++**werkt het Slimme Beeld met mijn bestaand beeld vooraf instelt?**

Ja. Slimme afbeeldingen werken met uw bestaande voorinstellingen voor afbeeldingen en nemen alle afbeeldingsinstellingen in acht. De afbeeldingsindeling, de kwaliteitsinstelling of beide worden gewijzigd. Voor conversie van indelingen behoudt Smart Imaging volledige visuele getrouwheid zoals gedefinieerd door de vooraf ingestelde instellingen van de afbeelding, maar met een kleinere bestandsgrootte.

Stel dat een voorinstelling voor een afbeelding is gedefinieerd met de indeling JPEG, de grootte 500 x 500, de kwaliteit=85 en het onscherpe masker=0,1,1,5. Wanneer bij Smart Imaging wordt vastgesteld dat een gebruiker in een Chrome-browser werkt, wordt de afbeelding omgezet in de WebP-indeling, met een grootte van 500 x 500. Onscherp masker=0,1,1,5 is bij een kwaliteit WebP die een kwaliteit van JPEG van 85 zo dicht mogelijk aanpast. De voetafdruk van die omzetting WebP wordt vergeleken met de JPEG, en kleiner van twee is teruggekeerd.

+++

+++**moet ik om het even welke URLs veranderen, beeld vooraf instelt, of nieuwe code op mijn plaats opstellen?**

Nee. Slimme afbeeldingen werken naadloos met bestaande URL&#39;s voor afbeeldingen en voorinstellingen voor afbeeldingen. Bovendien hoeft u bij Slimme afbeeldingen geen code aan uw website toe te voegen om de browser van een gebruiker te detecteren. Al deze functionaliteit wordt automatisch behandeld.

<!-- Smart Imaging works seamlessly with your existing image URLs and image presets if you configure Smart Imaging on your existing custom domain. In addition, Smart Imaging does not require you to add any code on your website to detect a user's browser. It is all handled automatically.

In case you must configure a new custom domain to use Smart Imaging, the URLs must be updated to reflect this custom domain.

To understand pre-requisites for Smart Imaging, see [Am I eligible to use Smart Imaging?](#am-i-eligible-to-use-smart-imaging) -->

<!-- OLD As mentioned earlier, Smart Imaging supports only JPEG and PNG image formats. For other formats, you need to append the `bfc=off` modifier to the URL as described earlier. -->

+++

+++**werkt het Slimme Beelden met HTTPS? Hoe zit het met HTTP/2?**

Ja, op beide vragen. Slimme afbeeldingen werken met afbeeldingen die via HTTP of HTTPS worden geleverd. Bovendien werkt het ook via HTTP/2.

+++

+++**Ben ik verkiesbaar om Slimme Beelden te gebruiken?**

Het hangt ervan af. Als u Smart Imaging wilt gebruiken, moet de Dynamic Media Classic of Dynamic Media van uw bedrijf op een Experience Manager-account aan de volgende vereisten voldoen:

* Gebruik Adobe-gebundelde CDN (het Netwerk van de Levering van de Inhoud) als deel van uw vergunning.
* Gebruik een toegewezen domein (bijvoorbeeld `images.company.com` of `mycompany.scene7.com` ), geen algemeen domein (bijvoorbeeld `s7d1.scene7.com` , `s7d2.scene7.com` of `s7d13.scene7.com` ).

Om uw domeinen te vinden, open de [ Desktoptoepassing van Dynamic Media Classic ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), dan login aan uw bedrijfrekening of rekeningen.

Ga naar **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL General Settings]** . Zoek het veld met het label **[!UICONTROL Published Server Name]** . Als u momenteel een algemeen domein gebruikt, kunt u verzoeken over te gaan naar uw eigen douanedomein. Voer deze overgangsaanvraag uit wanneer u een ondersteuningskwestie indient.

Voor je eerste aangepaste domein zijn er geen extra kosten verbonden met een Dynamic Media-licentie.

+++

+++**Kan ik Slimme Beeldvorming voor mijn rekening toelaten?**

Nee. U kunt een verzoek indienen om Smart Imaging te gebruiken. Deze optie is niet automatisch ingeschakeld.

Maak een ondersteuningskwestie zoals hieronder wordt beschreven. In het geval van uw steun, zorg ervoor u vermeld welke van de volgende Slimme mogelijkheden van het Beelden (één of meerdere) u op uw rekening wilt toegelaten:

* WebP
* AVIF
* DPR en netwerkbandbreedte optimaliseren
* PNG naar AVIF- of WebP met verlies

Als u Smart Imaging al hebt ingeschakeld met WebP, maar andere nieuwe functies wilt gebruiken zoals hierboven vermeld, moet u een ondersteuningscase maken.

**om een steungeval tot stand te brengen om Slimme Beeldvorming op uw rekening toe te laten:**

1. [ gebruik de Admin Console om de verwezenlijking van een nieuw steungeval ](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html) te beginnen.
1. Geef de volgende informatie op in uw ondersteuningsgeval:

   * Primaire contactpersoon, e-mail, telefoon.

   * Geef aan welke van de volgende mogelijkheden voor Smart Imaging (een of meer) u wilt inschakelen voor uw account:
      * WebP
      * AVIF
      * DPR en netwerkbandbreedte optimaliseren
      * PNG naar AVIF- of WebP met verlies

   * Alle domeinen die moeten worden ingeschakeld voor Smart Imaging (dat wil zeggen `images.company.com` of `mycompany.scene7.com` ).

     Om uw domeinen te vinden, open de [ Desktoptoepassing van Dynamic Media Classic ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), dan login aan uw bedrijfrekening of rekeningen.

     Ga naar **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL General Settings]** .

     Zoek het veld met het label **[!UICONTROL Published Server Name]** .

   * Verifieer dat u CDN door Adobe gebruikt en niet met een directe verhouding wordt beheerd.

   * Controleer of u een speciaal domein zoals `images.company.com` of `mycompany.scene7.com` gebruikt en geen algemeen domein, zoals `s7d1.scene7.com` , `s7d2.scene7.com` of `s7d13.scene7.com` .

     Om uw domeinen te vinden, open de [ Desktoptoepassing van Dynamic Media Classic ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), dan login aan uw bedrijfrekening of rekeningen.

     Ga naar **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL General Settings]** .

     Zoek het veld met het label **[!UICONTROL Published Server Name]** . Als u momenteel een algemeen Dynamic Media Classic-domein gebruikt, kunt u vragen dat u in het kader van deze overgang overschakelt naar uw eigen aangepaste domein.

   * Geef aan of het via HTTP/2 moet werken.

1. De Steun van de Klant van de Adobe voegt u aan de Slimme Lijst van de Wacht van het Beeld toe die op de orde wordt gebaseerd waarin de verzoeken worden voorgelegd.
1. Wanneer de Adobe klaar is om uw verzoek te behandelen, neemt de Steun van de Klant contact u op om een doeldatum te coördineren en te plaatsen.
1. **Facultatief**: U kunt naar keuze Slim Beelden in het Opvoeren testen alvorens de Adobe de nieuwe eigenschap aan productie duwt.
1. Klantenondersteuning stuurt u een melding nadat de service is voltooid.
1. Om de prestatieverbeteringen van Smart Imaging te maximaliseren, raadt de Adobe aan om de tijd in te stellen op Live (TTL) tot 24 uur of langer. De TTL bepaalt hoe lang de activa door CDN in het voorgeheugen worden opgeslagen. Deze instelling wijzigen:

   1. Als u Dynamic Media Classic gebruikt, gaat u naar **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL Publish Setup]** > **[!UICONTROL Image Server]** . Stel de waarde **[!UICONTROL Default Client Cache Time To Live]** in op 24 of hoger.
   1. Als u Dynamic Media gebruikt, volg [ deze instructies ](config-dm.md). Stel de waarde **[!UICONTROL Expiration]** in op 24 uur of langer.

+++

+++**wanneer wordt mijn rekening toegelaten met Slimme Beelden?**

De verzoeken worden verwerkt in de orde waarin zij door de Steun van de Klant, volgens de Wachtlijst worden ontvangen.

>[!NOTE]
>
>Er kan een lange aanlooptijd zijn, omdat het inschakelen van Smart Imaging Adobe vereist voor het wissen van de cache. Daarom kunnen slechts een paar klantenovergangen op elk bepaald ogenblik worden behandeld.

+++

+++**zijn er risico&#39;s met het gebruiken van Slimme Beeldvorming?**

Er is geen risico voor een klantenwebpagina. Bij de overgang naar Smart Imaging wordt de CDN-cache echter wel gewist. Bij deze bewerking gaat u naar een nieuwe configuratie van Dynamic Media Classic of Dynamic Media op Experience Manager.

Tijdens de eerste overgang raken de oorspronkelijke servers van de Adobe rechtstreeks door de niet-cacheafbeeldingen totdat het cachegeheugen opnieuw wordt opgebouwd. Als dusdanig, is de Adobe van plan om een paar klantenovergangen in een tijd te behandelen zodat de aanvaardbare prestaties worden gehandhaafd wanneer het trekken van verzoeken van de oorsprong. Voor de meeste klanten, wordt het geheime voorgeheugen volledig opnieuw opgebouwd bij CDN binnen ongeveer één tot twee dagen.

+++

+++**kan ik verifiëren als het Slimme Beeld werkt?**

Ja. U kunt het volgende doen:

1. Wanneer uw account is geconfigureerd met Smart Imaging, laadt u een Dynamic Media Classic- of Adobe Experience Manager - Dynamic Media-afbeeldings-URL in de browser.
1. Open het Chrome-ontwikkelaarsvenster door in de browser naar **[!UICONTROL View]** > **[!UICONTROL Developer]** > **[!UICONTROL Developer Tools]** te gaan. Of kies een ander browserontwikkelaarsgereedschap van uw keuze.

1. Zorg ervoor dat de cache is uitgeschakeld wanneer de ontwikkelprogramma&#39;s zijn geopend.

   * In Windows® navigeert u naar de instellingen in het deelvenster voor ontwikkelaars en schakelt u het selectievakje **[!UICONTROL Disable cache (while devtools is open)]** in.
   * Selecteer in macOS onder het tabblad **[!UICONTROL Network]** in het deelvenster Ontwikkelaar de optie **[!UICONTROL disable cache]** .

1. Waarnemen dat het inhoudstype wordt omgezet in de juiste indeling. In de volgende schermafbeelding ziet u een PNG-afbeelding die op Chrome dynamisch wordt omgezet in WebP. Als voor uw domein AVIF is ingeschakeld, kunt u ook AVIF in het Inhoudstype zien.
1. Herhaal deze test voor verschillende browsers en gebruikersomstandigheden.

>[!NOTE]
>
>Niet alle afbeeldingen worden omgezet. Smart Imaging bepaalt of de conversie de prestaties kan verbeteren. Soms wordt de afbeelding niet geconverteerd als er geen verwachte prestatieverbetering is of de indeling geen JPEG of PNG is.

![ image2017-11-14_15398 ](assets/image2017-11-14_15398.png)

+++

+++**is er een manier om de voordelen van Slim Beeld te kennen?**

Ja. De koptekst Slimme afbeeldingen bepaalt de voordelen van Slimme afbeeldingen. Wanneer Slimme afbeeldingen is ingeschakeld, kunt u na een verzoek om een afbeelding onder de kop **[!UICONTROL Response Headers]** `-X-Adobe-Smart-Imaging` zien zoals in het volgende gemarkeerde voorbeeld:

![ Slimme beeldende kopbal ](/help/assets/dynamic-media/assets/smartimagingheader.png)

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
>Als de waarde van `X-Adobe-Smart-Imaging` -1 is en WebP nog steeds wordt geleverd, betekent dit dat Slimme beeldverwerking werkt, maar dat de groottevoordelen niet zijn berekend vanwege de oude cache. U kunt `cache=update` (slechts één keer) in de URL van de afbeelding gebruiken om dit probleem op te lossen.
>Een voorbeeld van de modifier:
>`https://smartimaging.scene7.com/is/image/SmartImaging/sample1?cache=update`
>Als u de gehele cache wilt ongeldig maken, moet u een ondersteuningscase maken.

+++

+++**kan ik optimalisering AVIF in Slimme Beeldvorming onbruikbaar maken?**

Ja. Als u terug naar het dienen WebP door gebrek wilt schakelen, creeer een steungeval voor het zelfde. Zoals gebruikelijk, kunt u Smart Imaging uitzetten door de parameter `bfc=off` aan URL van het beeld toe te voegen. U kunt WebP of AVIF echter niet selecteren in de URL-optie voor Smart Imaging. Deze mogelijkheid blijft behouden op het niveau van uw bedrijfsaccount.

+++

+++**waarom mijn verzoek ontbreekt wanneer ik een URL met fmt=tif op Webbrowser van Chrome heb?**

Deze fout treedt niet op als Smart Imaging niet is ingeschakeld voor uw account. Slimme afbeeldingen werken alleen in de indeling JPEG of PNG.

U kunt deze fout voorkomen door:

* Geef JPEG of PNG op, of
* Gebruik de optie `fmt` helemaal niet, of
* Gebruik een browservoorkeursindeling die wordt gedefinieerd door Smart Imaging. U kunt bijvoorbeeld WebP gebruiken voor Chrome-webbrowser.

+++

+++**kan ik een beeld van TIFF van URL van een beeld downloaden?**

Ja. Voeg `fmt=tif` en `bfc=off` toe aan het URL-pad van de afbeelding.

+++

+++**beheert het Slimme Beeld beeldformaat en de montages van de beeldkwaliteit?**

Ja. Voor Smart Imaging worden zowel de indeling als de kwaliteit gebruikt. De overige parameters blijven ongewijzigd, indien gevraagd in de URL van de afbeelding.

+++

+++**kan ik een minimum en maximumkwaliteit plaatsen die?**

Nee. Op dit moment bestaat een dergelijke voorziening niet.

+++

+++**past Slimme Beeldvorming de percenten kwaliteitsuitvoer aan die plaatsen?**

Ja. Met Slimme afbeeldingen wordt het kwaliteitspercentage automatisch aangepast. Dit kwaliteitspercentage wordt bepaald met behulp van een machinaal leeralgoritme dat door Adobe wordt ontwikkeld. Dit percentage is niet bereikspecifiek.

+++

+++**zijn slechts JPEG en PNG vervangen door Slimme Beeldvorming?**

Ja. Deze functionaliteit werkt alleen voor JPEG en PNG.

+++

+++**waarom is JPEG soms teruggekeerd aan Chrome in plaats van WebP?**

Slimme afbeeldingen bepalen of de conversie nuttig is. Het retourneert alleen de nieuwe afbeelding van de conversie.

+++

+++**waarom werkt de Verhouding van het Pixel van het Apparaat (dpr) niet met samengestelde beelden?**

Als een samengestelde afbeelding te veel lagen bevat, kan de dpr-functionaliteit worden beïnvloed wanneer u een positiewijziging gebruikt. Dit probleem is bekend en wordt opgelost in toekomstige versies van Smart Imaging. Als andere functies voor Smart Imaging niet naar behoren werken, kunt u een ondersteuningscase maken om het probleem te melden.

+++

+++**waarom zet het Slimme Beeld PNG in lossless WebP/AVIF om?**

Omdat PNG een indeling zonder verlies is, is de grootte van eerdere WebP- en AVIF-bewerkingen groter dan u had verwacht. Smart Imaging ondersteunt nu omzetten met verlies. U kunt de optie `cache=update` (slechts één keer) in een afbeeldingsaanvraag gebruiken om dit probleem op te lossen. Een voorbeeld van het gebruik van deze modifier:

`https://smartimaging.scene7.com/is/image/SmartImaging/sample1?cache=update`

Om het volledige geheime voorgeheugen ongeldig te maken, moet u een steungeval creëren die om zulk een inspanning verzoekt.

+++

+++**kan ik blijven gebruikend PNG aan verliesloze omzetting in Slimme Beeldvorming?**

Ja. Smart Imaging ondersteunt nu verliesconversie op basis van het kwaliteitsniveau. Als u wilt doorgaan met het omzetten zonder verlies, kunt u een kwaliteit van 100 gebruiken die is ingesteld door de instelling van uw bedrijf of via de URL van de afbeelding met `qlt=100` in het pad.

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
>* [Image optimization with next generation image formats WebP and AVIF.](https://medium.com/adobetech/image-optimisation-with-next-gen-image-formats-webp-and-avif-248c75afacc4) 
-->
