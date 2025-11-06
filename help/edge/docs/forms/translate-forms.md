---
title: Een Edge Delivery Services voor AEM Forms vertalen en lokaliseren
description: Een Edge Delivery Services voor AEM Forms vertalen en lokaliseren
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 8a0c826f-8acc-4a00-bd84-7b0df9a82457
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---


# Een Edge Delivery Services voor AEM Forms vertalen en lokaliseren

In Edge Delivery Services gaat het bij het vertalen van formulieren om het omzetten van formulierinhoud van de ene taal naar de andere, waarbij de nadruk ligt op nauwkeurigheid, helderheid en consistentie. Vertaalde of gelokaliseerde formulieren maken een breder bereik voor het publiek mogelijk op verschillende geografische locaties, waardoor de gebruikerservaring toeneemt en een betere communicatie tussen verschillende taalvoorkeuren mogelijk wordt.


Aan het einde van het artikel leert u:

- [Formulieren vertalen in Google Drive](#translate-form-google-drive)
- [Formulieren vertalen binnen SharePoint-site](#translate-form-sharepoint)

## Formulieren vertalen in Google Drive {#translate-form-google-drive}

De functie `GOOGLETRANSLATE` in Google-bladen vertaalt formulieren door te tikken op een ingebouwd vertaalprogramma, waardoor de tekst van de ene taal rechtstreeks in een Google-blad wordt gewijzigd. Formulieren vertalen in Google Drive:

1. Ga naar de map AEM Project op Google Drive en open uw Google-pagina.
2. Wijzig de naam van het bestaande blad (`shared-default`) in `shared-en` .
3. Voeg een werkblad met de naam `shared-default` toe. Het `shared-default` -blad bevat de inhoud die u wilt lokaliseren naar een bepaalde taal.
4. Voeg de gelokaliseerde inhoud aan het `shared-default` blad toe gebruikend de functie `GOOGLETRANSLATE`.
U kunt een formule gebruiken om de inhoud van cel D2 van het `shared-en` blad in het Frans te vertalen binnen het `shared-default` blad. Hier volgt de formule:
   `=GOOGLETRANSLATE('shared-en'!D2,"en","fr")`

   ![&#x200B; Vertaal de vraag spreadsheet &#x200B;](/help/forms/assets/translate-enquiry-spreadsheet.png)

5. Voorproef en publiceer het blad gebruikend [&#x200B; AEM Sidekick &#x200B;](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

U kunt naar het [&#x200B; spreadsheet &#x200B;](/help/forms/assets/enquirytranslate.xlsx) verwijzen die de vormdefinitie voor een `enquiry` vorm bevat die van het Engels aan de Franse taal wordt vertaald.

![&#x200B; Vertaalde Vorm van de vraag &#x200B;](/help/forms/assets/translate-form-french.png)

Raadpleeg de onderstaande URL waar u het formulier kunt bekijken met de Franse vertaling:
https://main—portal—wkndforms.hlx.live/enquirytranslate

## Formulieren vertalen binnen SharePoint-site{#translate-form-sharepoint}

Als u de formulieren wilt vertalen op de Microsoft® SharePoint-site, moet u de labels van de velden handmatig wijzigen met een vertaalservice. De formulieren vertalen binnen de SharePoint-site:

1. Ga naar de map AEM Project op Microsoft® SharePoint en open uw spreadsheet.
2. Wijzig de naam van het bestaande blad (`shared-default`) in `shared-en` .
3. Voeg een werkblad met de naam `shared-default` toe. Het `shared-default` -blad bevat de inhoud die u wilt lokaliseren naar een bepaalde taal.
4. Voeg de gelokaliseerde inhoud handmatig toe aan het `shared-default` -werkblad.

   ![&#x200B; Vertaal de vraag spreadsheet &#x200B;](/help/forms/assets/translate-enquiry-sp-spreadsheet.png)

5. Voorproef en publiceer het blad gebruikend [&#x200B; AEM Sidekick &#x200B;](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

Verwijs naar [&#x200B; spreadsheet &#x200B;](/help/forms/assets/enquirytranslate-sp.xlsx) die de vormdefinitie voor een `enquiry` vorm bevat die van het Engels aan de Franse taal wordt vertaald.

![&#x200B; Vertaalde Vorm van de vraag &#x200B;](/help/forms/assets/translate-form-french.png)

Raadpleeg de onderstaande URL waar u het formulier kunt bekijken met de Franse vertaling:
https://main—wefinance—wkndforms.hlx.live/enquirytranslate

## Bekende problemen {#known-issues}

- De labels van het formulier worden vertaald naar de opgegeven gelokaliseerde taal op het `shared-default` -blad, maar de foutberichten worden weergegeven in de standaardtaal van de browser.

  ![&#x200B; het bericht van de Fout &#x200B;](/help/forms/assets/translate-error-message.png)

- Wanneer u de kalender opent, wordt de kalenderdrop-down getoond in de standaardtaal van browser.

  ![&#x200B; het bericht van de Fout &#x200B;](/help/forms/assets/translate-calender-display.png)


## Veelgestelde vragen {#faq}

**Q**: Hoe kan ik input in de gespecificeerde gelokaliseerde taal in een vorm typen?

**A**: Aan inputtekst in een specifieke gelokaliseerde taal, pas de toetsenbordmontages op uw apparaat aan. Raadpleeg de volgende koppelingen voor instructies over hoe u dit kunt doen:

- [&#x200B; opstelling uw Mac om input in een andere taal &#x200B;](https://support.apple.com/en-in/guide/mac-help/mchlp1406/mac) te nemen
- [&#x200B; opstelling uw Vensters om input in een andere taal &#x200B;](https://support.microsoft.com/en-us/windows/manage-the-input-and-display-language-settings-in-windows-12a10cb4-8626-9b77-0ccb-5013e0c7c7a2#:~:text=Select%20the%20Start%20%3E%20Settings%20%3E%20Time,you%20want%2C%20then%20select%20Options) te nemen
- [&#x200B; Opstelling uw Android of iPhones/iPads om input in een andere taal &#x200B;](https://support.google.com/gboard/answer/7068494?hl=en&co=GENIE.Platform%3DAndroid) te nemen


**Q**: Hoe kan ik een lijst van scènes terugwinnen die in de `GOOGLETRANSLATE` functie worden gebruikt?

**A**: U kunt naar de [&#x200B; officiële documentatie van Google &#x200B;](https://cloud.google.com/translate/docs/languages) voor een uitvoerige lijst van scènes verwijzen die in GOOGLETRANSLATE worden gebruikt.


