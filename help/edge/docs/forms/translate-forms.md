---
title: Een AEM Forms Edge Delivery ServicesForm vertalen en lokaliseren
description: Een AEM Forms Edge Delivery ServicesForm vertalen en lokaliseren
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 8a0c826f-8acc-4a00-bd84-7b0df9a82457
role: Admin, Architect, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---


# Een AEM Forms Edge Delivery ServicesForm vertalen en lokaliseren

Bij het vertalen van formulieren in Edge Delivery Services gaat het om het omzetten van formulierinhoud van de ene taal naar de andere, waarbij de nadruk ligt op nauwkeurigheid, helderheid en consistentie. Vertaalde of gelokaliseerde formulieren maken een breder bereik voor het publiek mogelijk op verschillende geografische locaties, waardoor de gebruikerservaring toeneemt en een betere communicatie tussen verschillende taalvoorkeuren mogelijk wordt.


Aan het einde van het artikel leert u:

* [Formulieren vertalen in Google Drive](#translate-form-google-drive)
* [Formulieren vertalen binnen SharePoint-site](#translate-form-sharepoint)

## Formulieren vertalen in Google Drive {#translate-form-google-drive}

De `GOOGLETRANSLATE` -functies in Google-bladen worden formulieren omgezet door te tikken op een ingebouwde vertaaltool, waardoor de tekst van de ene taal rechtstreeks in een Google-blad wordt gewijzigd. Formulieren vertalen in Google Drive:

1. Ga naar de map AEM Project op Google Drive en open uw Google-pagina.
2. De naam van het bestaande blad wijzigen (`shared-default`) naar `shared-en`.
3. Een werkblad met de naam toevoegen `shared-default`. De `shared-default` Het blad bevat de inhoud voor lokalisatie naar een specifieke taal.
4. Voeg de gelokaliseerde inhoud toe in het dialoogvenster `shared-default` blad met behulp van `GOOGLETRANSLATE` functie.
U kunt een formule gebruiken om de inhoud van cel D2 van te vertalen `shared-en` blad in het Frans binnen de `shared-default` blad. Hier volgt de formule:
   `=GOOGLETRANSLATE('shared-en'!D2,"en","fr")`

   ![Sprite-werkblad opvragen](/help/forms/assets/translate-enquiry-spreadsheet.png)

5. Het blad voorvertonen en publiceren met [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

U kunt verwijzen naar de [spreadsheet](/help/forms/assets/enquirytranslate.xlsx) met de formulierdefinitie voor een `enquiry` formulier vertaald van het Engels naar het Frans.

![Vertaald formulier vragen](/help/forms/assets/translate-form-french.png)

Raadpleeg de onderstaande URL waar u het formulier kunt bekijken met de Franse vertaling: https://main—portal—wkndforms.hlx.live/enquirytranslate

## Formulieren vertalen binnen SharePoint-site{#translate-form-sharepoint}

Als u de formulieren wilt vertalen op de Microsoft® SharePoint-site, moet u de labels van de velden handmatig wijzigen met een vertaalservice. De formulieren vertalen binnen de SharePoint-site:

1. Ga naar de map AEM Project op Microsoft® SharePoint en open uw spreadsheet.
2. De naam van het bestaande blad wijzigen (`shared-default`) naar `shared-en`.
3. Een werkblad met de naam toevoegen `shared-default`. De `shared-default` Het blad bevat de inhoud voor lokalisatie naar een specifieke taal.
4. Voeg de gelokaliseerde inhoud toe in het dialoogvenster `shared-default` blad handmatig.

   ![Sprite-werkblad opvragen](/help/forms/assets/translate-enquiry-sp-spreadsheet.png)

5. Het blad voorvertonen en publiceren met [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

Zie de [spreadsheet](/help/forms/assets/enquirytranslate-sp.xlsx) met de formulierdefinitie voor een `enquiry` formulier vertaald van het Engels naar het Frans.

![Vertaald formulier vragen](/help/forms/assets/translate-form-french.png)

Raadpleeg de onderstaande URL waar u het formulier kunt bekijken met de Franse vertaling: https://main—wefinance—wkndforms.hlx.live/enquirytranslate

## Bekende problemen {#known-issues}

* De labels van het formulier worden vertaald naar de opgegeven gelokaliseerde taal in de `shared-default` blad, maar de foutberichten worden in de standaardtaal van de browser weergegeven.

  ![Foutbericht](/help/forms/assets/translate-error-message.png)

* Wanneer u de kalender opent, wordt de kalenderdrop-down getoond in de standaardtaal van browser.

  ![Foutbericht](/help/forms/assets/translate-calender-display.png)


## Veelgestelde vragen {#faq}

**Q**: Hoe kan ik invoer in de opgegeven gelokaliseerde taal in een formulier typen?

**A**: Als u tekst wilt invoeren in een specifieke gelokaliseerde taal, past u de toetsenbordinstellingen op het apparaat aan. Raadpleeg de volgende koppelingen voor instructies over hoe u dit kunt doen:

* [Mac instellen om invoer in een andere taal op te nemen](https://support.apple.com/en-in/guide/mac-help/mchlp1406/mac)
* [Stel uw vensters in om invoer in een andere taal op te nemen](https://support.microsoft.com/en-us/windows/manage-the-input-and-display-language-settings-in-windows-12a10cb4-8626-9b77-0ccb-5013e0c7c7a2#:~:text=Select%20the%20Start%20%3E%20Settings%20%3E%20Time,you%20want%2C%20then%20select%20Options)
* [Stel uw Android- of iPhones/iPads in om invoer in een andere taal te ontvangen](https://support.google.com/gboard/answer/7068494?hl=en&amp;co=GENIE.Platform%3DAndroid)


**Q**: Hoe kan ik een lijst ophalen met landinstellingen die worden gebruikt in het dialoogvenster `GOOGLETRANSLATE` functie?

**A**: U kunt verwijzen naar de [officiële documentatie van Google](https://cloud.google.com/translate/docs/languages) voor een uitgebreide lijst van landinstellingen die in de GOOGLETRANSLATE worden gebruikt.

## Zie ook

{{see-more-forms-eds}}

