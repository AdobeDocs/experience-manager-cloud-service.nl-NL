---
title: Veelgestelde vragen over de gebruiksduur van de DHTML-viewer
description: Met ingang van 31 januari 2014 zal het DHTML-viewerplatform van Scene7 officieel het einde van de levensduur bepalen. Deze melding geeft u antwoorden op veelgestelde vragen, zodat u zich kunt voorbereiden op deze overgang naar ons nieuwe HTML5-viewerplatform.
translation-type: tm+mt
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6
workflow-type: tm+mt
source-wordcount: '1615'
ht-degree: 1%

---


# Veelgestelde vragen over de gebruiksduur van de DHTML-viewer{#dhtml-viewer-end-of-life-faqs}

Met ingang van 31 januari 2014 zal het DHTML-viewerplatform van Scene7 officieel het einde van de levensduur bepalen. Deze melding geeft u antwoorden op veelgestelde vragen, zodat u zich kunt voorbereiden op deze overgang naar ons nieuwe HTML5-viewerplatform.

**Wat is de verandering?**

Met ingang van 31 januari 2014, zal Scene7 officieel steun aan het eind van de levensduur voor het DHTML- kijkersplatform beëindigen.

**Wat betekent einde van leven?**

Het einde van de levensduur betekent dat (1) Scene7 geen eigenschapverhogingen aan het DHTML- kijkerplatform (2) niet meer zal toevoegen of om het even welke insectenmoeilijke situaties op het DHTML viewer platform zal vrijgeven en (3) de klantenzorg zal niet meer het oplossen van problemen of het verlenen van steun voor om het even welke DHTML- verwante viewerkwesties of vragen.

**Waarom brengt Scene7 deze verandering aan?**

De normen van het Web evolueren constant en DHTML is een oudere technologie van de Webontwikkeling die snel door HTML5 wordt vervangen. De grootste beperking voor DHTML als platform is dat deze niet de rijkdom aan ervaring kan creëren die HTML5 nu consistent en gemakkelijker kan ondersteunen voor verschillende browsers. Voorbeelden van dergelijke beperkingen zijn het gebrek aan ondersteuning voor verschillende browsers voor:

* Aangepaste cursors
* Afgeronde hoeken
* Animaties (zoals pagina spiegelen, zoomen versnellen)
* Effecten (zoals schaduwen, gloed)
* Volledige ondersteuning voor lettertypen
* Video&#39;s zonder insteekmodule afspelen

Specifiek voor het Scene7 DHTML viewer platform, zowel werden de op JSP-Gebaseerde oplossing als Javascript APIs niet geoptimaliseerd voor mobiele apparaten om uit multi-aanraak en gebaarmogelijkheden voordeel te halen. En hoewel DHTML-viewers die in 2011/begin 2012 werden uitgebracht, geoptimaliseerd zijn voor mobiele apparaten, waren ze moeilijk aan te passen en te onderhouden vanwege het ontbreken van een flexibel SDK-ontwikkelframework voor componenten.

Door deze beperkingen op DHTML en de snelle industriestandaard met HTML5 als opkomende norm over zowel Desktop als mobiel, heeft Scene7 besloten in een op HTML5-Gebaseerd kijkersplatform te investeren. Deze investering biedt onze klanten een robuust platform waarmee ze rijkere, boeiendere interactieve viewers kunnen bouwen die gebruikers op meerdere schermen kunnen bereiken, waaronder desktops, iOS en Android-apparaten.

**Hoe weet ik of mijn viewer het DHTML-platform gebruikt?**

Om te bepalen of de viewer die uw bedrijf gebruikt DHTML is en daarom door deze wijziging wordt beïnvloed, moet u controleren of:

1. Uw bedrijf gebruikt een uit-van-doos kijker Scene7 die in deze lijst wordt vermeld waar de &quot;Technologie van de Kijker&quot;als &quot;DHTML&quot;wordt aangewezen:

   [https://help.adobe.com/en_US/scene7/using/WS6E593DEA-7D81-4cd6-84B0-85E8BB274176.html#WS1c46793299cf21d77e926d1613177f0a020-8000](https://help.adobe.com/en_US/scene7/using/WS6E593DEA-7D81-4cd6-84B0-85E8BB274176.html#WS1c46793299cf21d77e926d1613177f0a020-8000)

1. Uw bedrijf gebruikt een kijker die als nieuw vooraf ingesteld werd gecreeerd die van een uit-van-doos kijker Scene7 in deze lijst wordt gebaseerd waar de &quot;Technologie van de Kijker&quot;als &quot;DHTML&quot;wordt aangewezen:

   [https://help.adobe.com/en_US/scene7/using/WS6E593DEA-7D81-4cd6-84B0-85E8BB274176.html#WS1c46793299cf21d77e926d1613177f0a020-8000](https://help.adobe.com/en_US/scene7/using/WS6E593DEA-7D81-4cd6-84B0-85E8BB274176.html#WS1c46793299cf21d77e926d1613177f0a020-8000)

1. Uw bedrijf gebruikt een douaneviewer die van de op JSP-Gebaseerde oplossing DHTML wordt gecreeerd:

   [https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#JSP_Reference](https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#JSP_Reference)

1. Uw bedrijf gebruikt een aangepaste viewer die is gemaakt met de Javascript-API:

   [https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#API_Reference](https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#API_Reference)

1. Uw bedrijf gebruikt een aangepaste viewer die is gemaakt met de meerscherm-API van DHTML:

   [https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#Multi-screen_Flyout_Viewer](https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#Multi-screen_Flyout_Viewer)

1. Uw bedrijf maakt gebruik van een aangepaste viewer die is gemaakt met de DHTML-API voor het uitvouwen van bureaublad:

   [https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#Desktop_Flyout_Viewer](https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#Desktop_Flyout_Viewer)

1. Uw bedrijf gebruikt een bibliotheek voor apparaatdetectie die deel uitmaakt van het DHTML-viewerpakket:

   Zoek naar JS omvat van &quot;sj_deviceDetect.js&quot;in uw code.

   Deze is hier vervangen door de nieuwe JS-code voor apparaatdetectie: [https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#Detecting_devices_and_browsers](https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#Detecting_devices_and_browsers) .

**Wat is het vervangende viewerplatform?**

De vervanging voor DHTML is het Scene7 HTML5 viewerplatform, die uit allebei bestaat:

* HTML5-viewers die uit-van-box-viewers zijn voorzien van voor mobiele apparaten geoptimaliseerde interacties voor verschillende viewertypen, zoals standaardzoomen, uitzoomen, afbeeldingssets, stalensets, multidimensionale draaiing en gemengde media. Voor volledige actuele voorbeelden van deze viewers raadpleegt u: [https://microsite.omniture.com/t2/help/en_US/s7/vlist/vlist.html](https://microsite.omniture.com/t2/help/en_US/s7/vlist/vlist.html)
* De HTML5-viewer SDK, die uitgebreide aanpassingen van Adobe Scene7-viewers voor door HTML5 ondersteunde sites en apparaten (zoals iOS en Android) mogelijk maakt, zorgt voor de maximale flexibiliteit en creativiteit om de weergave en interactiviteit van de viewer te markeren. Het voordeel van herbruikbare componenten die geoptimaliseerd zijn voor optimale prestaties verlaagt de algemene kosten van de ontwikkeling van de viewer en versnelt de ontwikkeling op maat.

**Wanneer heeft het HTML5-viewerplatform de functies die ik nodig heb om over te schakelen van het DHTML-viewerplatform?**

Scene7 bracht eerste HTML5 viewer SDK in Herfst 2011 met de lancering van versie 5.5 vrij. Sindsdien hebben we een groot aantal functies aan het platform toegevoegd en hebben we de ondersteuning voor steeds meer soorten kijkers uitgebreid. Voor de meeste viewervereisten beschikt het HTML5-viewerplatform waarschijnlijk al over de functies die u nu moet migreren. En we blijven agressief investeren in dit viewerplatform met releases per kwartaal.

Raadpleeg de volgende documentatie om te bepalen of vandaag aan uw viewervereisten kan worden voldaan met het HTML5-viewerplatform:

[https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#About_HTML5_Viewers](https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#About_HTML5_Viewers) (voor functies en aanpassingsmogelijkheden van viewers buiten de box)

[https://help.adobe.com/en_US/scene7/using/WSd4272150f67705c11b002eec12fcba4dee6-8000.html](https://help.adobe.com/en_US/scene7/using/WSd4272150f67705c11b002eec12fcba4dee6-8000.html) (voor toegang tot de documentatie van de SDK API)

Als u nog steeds niet zeker weet of de HTML5 viewer SDK aan uw vereisten kan voldoen, neemt u contact op met het team van professionele services.

**Hoe kan ik mijn viewers overbrengen naar het HTML5-platform?**

Scene7 biedt de volgende opties aan om uw kijkers naar het HTML5 platform over te brengen:

1. Gebruik een van de scene7 out-of-box HTML5-viewers, voorbeelden hiervan kunt u hier vinden: [https://microsite.omniture.com/t2/help/en_US/s7/vlist/vlist.html](https://microsite.omniture.com/t2/help/en_US/s7/vlist/vlist.html)
1. Vorm één van de Scene7 uit-van-doos HTML5 kijkers onder de SPS toepassingsopstelling. Zo kunt u bepaalde functies aanpassen, zoals viewergrootte, overgangen, zoomgedrag, enz.: [https://help.adobe.com/en_US/scene7/using/WS6E593DEA-7D81-4cd6-84B0-85E8BB274176.html](https://help.adobe.com/en_US/scene7/using/WS6E593DEA-7D81-4cd6-84B0-85E8BB274176.html)
1. Pas het uiterlijk van de HTML5-viewers uit de box Scene7 aan door CSS aan te passen om het visuele ontwerp te wijzigen, zoals knopillustraties, plaatsing, transparantie, achtergrondkleuren, enz.: [https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#Customizing_HTML5_Viewers](https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#Customizing_HTML5_Viewers)
1. Maak een geheel nieuwe aangepaste HTML5-viewer met de SDK die u hier kunt downloaden: [https://help.adobe.com/en_US/scene7/using/WSd4272150f67705c11b002eec12fcba4dee6-8000.html](https://help.adobe.com/en_US/scene7/using/WSd4272150f67705c11b002eec12fcba4dee6-8000.html). U kunt de aangepaste viewer samenstellen met professionele services of deze laten bouwen door uw eigen webontwikkelingsteam.

**En browsers die geen HTML5 ondersteunen?**

HTML5 wordt ondersteund op veel mobiele apparaten en in webbrowsers en wordt nog steeds getraceerd. Hoewel HTML5 momenteel niet wordt ondersteund door Internet Explorer 8 of lager, heeft Scene7 ons HTML5-viewerplatform vernieuwd om zelfs ondersteuning toe te kennen aan IE 7 en IE 8. Met het Scene7 HTML5 viewerplatform, kunt u de overweldigende meerderheid van zowel Desktop als mobiele gebruikers met één enkel ontwikkelingsplatform bereiken.

De huidige systeemvereisten vanaf HTML5 SDK versie 2.2.1 zijn:

* Microsoft® Windows® XP of hoger, Macintosh® OS X 10.6 of hoger
* Firefox 17, Safari 5.1, Chrome 23, Internet Explorer 7 of hoger
* iOS 3.2.2 of hoger
* Gecertificeerd op iPhone3 of hoger en iPad1 of hoger (native browsers)
* Android OS 2.2 of hoger

Als u wilt controleren of uw browser compatibel is met ons HTML5-viewerplatform, start u de volgende voorbeeldviewer:

[https://s7d1.scene7.com/s7viewers/html5/flyout.html?asset=Scene7SharedAssets/Sample%20Image](https://s7d1.scene7.com/s7viewers/html5/flyout.html?asset=Scene7SharedAssets/Sample%20Image)

Als u de ingezoomde afbeelding ziet door de muis boven de hoofdafbeelding te houden of met uw vinger over de hoofdafbeelding te slepen, is dit een ondersteunde browser of apparaat.

**Welke opties heb ik als ik in productie wil blijven met mijn bestaande DHTML-viewer?**

Hoewel u nog steeds in productie met op DHTML-Gebaseerde kijkers kunt zijn, is het belangrijk om op te merken dat er geen verhogingen, insectenmoeilijke situaties of klantenzorg na 31 Januari, 2014 zullen zijn. Daarom raden we alle klanten sterk aan over te stappen naar ons robuustere HTML5-viewerplatform. . Als uw bedrijfssituatie echter een dergelijke migratie tegen de EOL-datum verhindert, kunt u een contract sluiten met professionele services om de ondersteunde onderhoudsperiode te verlengen. Neem voor meer informatie contact op met uw accountmanager.

**Wie neem ik contact op voor meer informatie?**

Als u geen antwoord op al uw vragen hebt gevonden in deze veelgestelde vragen, neemt u contact op met de ondersteuningsdienst ([s7support@adobe.com](mailto:s7support@adobe.com)) of uw Adobe-accountmanager.
