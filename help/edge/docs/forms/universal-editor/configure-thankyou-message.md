---
title: Hoe te om een Redirect Pagina te vormen of Dank u bericht
description: Leer hoe gebruikers een bedankt-uw-bericht kunnen worden getoond of aan een webpagina kunnen worden opnieuw gericht die de vormauteurs kunnen vormen terwijl het creëren van het formulier.
feature: Adaptive Forms, Edge Delivery Services
role: User
level: Intermediate
exl-id: cacd7b0a-aad0-4b5d-a6a0-e4bac4cb196d
source-git-commit: fd3c53cf5a6d1c097a5ea114a831ff626ae7ad7e
workflow-type: tm+mt
source-wordcount: '1139'
ht-degree: 0%

---

# Uw berichten voor bedankt configureren en URL&#39;s omleiden

De ervaringen na verzending hebben een aanzienlijke invloed op de tevredenheid van de gebruiker en het voltooiingspercentage van het formulier. Adobe Universal Editor biedt uitgebreide opties voor het configureren van wat gebruikers zien na het verzenden van formulieren, hetzij via persoonlijke dankwagens, hetzij via strategische omleidingen naar specifieke pagina&#39;s.

Dit artikel bevat gedetailleerde instructies voor het implementeren van zowel bedankberichten als omleidings-URL&#39;s, waaronder technische overwegingen, aanbevolen procedures en richtlijnen voor gebruikerservaring om de doeltreffendheid van uw formulierverzendingen te maximaliseren.

## Vereisten

Voordat u ervaringen na verzending configureert, moet u ervoor zorgen dat:

**Technische opstelling:**

- Toegang tot de universele editor met de juiste machtigingen
- Een bestaand adaptief formulier dat is gemaakt in de Universal Editor
- Inzicht in de URL-vereisten voor omleiding van uw organisatie

**planningsoverwegingen:**

- **strategie van het Bericht**: Bepaal de toon, de lengte, en de specifieke informatie om in dankweldingen te omvatten
- **Redirect strategie**: Identificeer doelpagina&#39;s en zorg ervoor zij voor post-vormvoltooiingservaringen worden geoptimaliseerd
- **de integratie van Analytics**: Plan hoe te om gebruikersinteractie met dank te volgen u berichten of opnieuw richt bestemmingen

## Berichten met dankbetuigingen configureren

Dank u berichten verstrekken onmiddellijk erkenning van succesvolle vormvoorlegging en kunnen gepersonaliseerde inhoud, volgende stappen, of belangrijke informatie omvatten relevant voor de voorlegging van de gebruiker.

### Wanneer je berichten via Bedankt wilt gebruiken

Dank u berichten het beste werken wanneer:

- **Eenvoudige erkenning**: De gebruikers hebben bevestiging zonder extra navigatievereisten nodig
- **Instructionele inhoud**: U moet specifieke volgende stappen of belangrijke informatie verstrekken
- **de consistentie van het Merk**: Het bericht kan worden gecreeerd om met de communicatiestijl van uw organisatie te richten
- **Enige-paginaervaring**: De gebruikers zouden op de huidige pagina voor werkschemagecontinuïteit moeten blijven

### Implementatiestappen

**1. Formuliereigenschappen openen**

Open uw AanpassingsVorm in Universele Redacteur en klik **geef de pictogram van de Eigenschappen van de Vorm** in de toolbar uit. Hiermee wordt het dialoogvenster met uitgebreide formuliereigenschappen geopend.

![ de eigenschappen van de Vorm pictogram ](/help/forms/assets/ue-form-properties-icon.png)

**2. Navigeer om u configuratie te danken**

In de dialoog van de Eigenschappen van de Vorm, selecteer **Dank u** tabel om tot de opties van de post-voorleggingsconfiguratie toegang te hebben.

![ Universele Eigenschappen van de Vorm van de Redacteur ](/help/forms/assets/ue-form-properties.png)

**3. Vorm berichtvertoning**

Selecteer **Bericht van de Show** van de beschikbare opties.

![ bedankt ](/help/edge/docs/forms/universal-editor/assets/thankyou-ue.png)

**4. Maak uw berichtinhoud**

Op het **de inhoudsgebied van het Bericht** gebied, vecht uw dankweld u bericht gebruikend de rijke tekstredacteur. De editor ondersteunt:

- **het formatteren van de Tekst**: Vet, cursief, onderstreept, en kleurenopties
- **Lijsten**: Bulleted en genummerde lijsten voor het organiseren van informatie
- **Verbindingen**: Directe verbindingen met relevante middelen of volgende stappen
- **Volledig scherm dat** uitgeeft: Klik het uitvouwpictogram voor een grotere het uitgeven werkruimte

### Technische overwegingen

**de vertoningsgedrag van het Bericht:**

- Berichten worden direct na het verzenden van het formulier weergegeven in een modale overlay
- Inhoud ondersteunt HTML-opmaak en behoudt een responsief ontwerp
- Berichten kunnen door gebruikers worden verworpen of met auto-dichte tijdopnemers worden gevormd

**richtlijnen van de Inhoud:**

- Houd berichten beknopt terwijl het verstrekken van noodzakelijke informatie
- Indien nodig duidelijke volgende stappen opnemen
- Neem bijvoorbeeld referentienummers of bevestigingsgegevens op
- Mobiele opmaak garanderen

### Voorbeeldimplementatie

     Dank u voor uw voorlegging!
    
     Uw toepassing is ontvangen en toegewezen verwijzingsaantal #REF-2024-001234.
    
    **Wat gebeurt er als volgt:**
     - U ontvangt binnen 15 minuten een bevestigingsbericht 
     - Ons team zal uw verzending binnen 2 werkdagen controleren 
     - We zullen rechtstreeks contact met u opnemen als extra informatie nodig is 
    
    **Hulp nodig?** Contact opnemen met ons ondersteuningsteam op support@example.com

## Omleidings-URL&#39;s configureren

URL&#39;s omleiden leidt gebruikers automatisch naar specifieke pagina&#39;s na het verzenden van het formulier, waardoor ze naadloos kunnen worden geïntegreerd met bestaande workflows of gebruikers naar relevante inhoud kunnen leiden.

### Wanneer omleidings-URL&#39;s gebruiken

Omleiding van URL&#39;s is optimaal voor:

- **integratie van het Werkschema**: Het leiden van gebruikers aan dashboards, rekeningspagina&#39;s, of volgende stappen in een proces
- **levering van de Inhoud**: Het tonen van relevante producten, de diensten, of informatie die op vormreacties wordt gebaseerd
- **Analytics die** volgen: Het leiden aan pagina&#39;s met specifieke het volgen implementaties
- **multi-step processen**: Bewegend gebruikers naar de volgende fase van complexe werkschema&#39;s

### Implementatiestappen

**1. Formuliereigenschappen openen**

Open uw AanpassingsVorm in Universele Redacteur en klik **geef de Eigenschappen van de Vorm** pictogram uit om de dialoog van de vormconfiguratie te openen.

![ de eigenschappen van de Vorm pictogram ](/help/forms/assets/ue-form-properties-icon.png)

**2. Navigeer om u configuratie te danken**

Selecteer **Dank u** lusje in de dialoog van de Eigenschappen van de Vorm om tot herleidingsconfiguratieopties toegang te hebben.

![ Universele Eigenschappen van de Vorm van de Redacteur ](/help/forms/assets/ue-form-properties.png)

**3. Omleidingsfunctionaliteit inschakelen**

Kies **Omleiden aan URL** van de beschikbare post-voorleggingsopties.

![ redirect ](/help/edge/docs/forms/universal-editor/assets/redirect-ue.png)

**4. Doel-URL configureren**

Voer in het opgegeven veld de doel-URL in. Het systeem ondersteunt meerdere URL-indelingen voor flexibele implementatie.

### Opties voor URL-configuratie

**Absolute URLs**

Volledige webadressen, inclusief protocol en domein:

     https://www.example.com/thank-you
     https://dashboard.example.com/user/profile 

**Relatieve Wegen**

Paden ten opzichte van uw huidige domein:

    /dank-u 
    /dashboard/user-profile 
     ../confirmation-page.html

**de Verwijzingen van de Pagina van AEM Sites**

Verwijzingen naar andere pagina&#39;s in uw AEM Sites-implementatie:

     /content/mysite/nl/Dankuwel
     /content/mysite/nl/next-stappen 

### Technische overwegingen

**Redirect gedrag:**

- Omleidingen vinden direct plaats nadat het formulier is verzonden
- De browsergeschiedenis bevat de omleiding voor de juiste functionaliteit voor de backbutton
- Redirect timing kan met facultatieve vertragingen worden gevormd

**bevestiging URL:**

- Systeem valideert URL-indeling voordat configuratie wordt toegestaan
- Relatieve URL&#39;s worden omgezet in het huidige domein
- Externe URL&#39;s vereisen een juiste CORS-configuratie, indien nodig

## Beste praktijken en Aanbevelingen

### Richtlijnen voor gebruikerservaring

**optimalisering van het Bericht:**

- **Duidelijkheid eerst**: Zorg ervoor de gebruikers onmiddellijk begrijpen hun voorlegging succesvol was
- **toevoeging van de Waarde**: Verstrek informatie die gebruikers van volgende stappen helpt
- **Consistente branding**: Handhaaf de stem en visuele stijl van uw organisatie
- **Mobiele overweging**: De berichten van de test op diverse het schermgrootte

**Redirect optimalisering:**

- **de optimalisering van de Pagina**: Zorg ervoor opnieuw richt bestemmingen voor post-vormbezoekers worden geoptimaliseerd
- **Ladende prestaties**: Verifieer opnieuw richt pagina&#39;s snel laden om gebruikerservaring te handhaven
- **relevantie van de Inhoud**: Zorg ervoor omleiding inhoud relevant voor de vormcontext is

### Beveiligingsoverwegingen

**bevestiging URL:**

- Voer juiste bevestiging voor omleiding URLs uit om kwaadwillige omleiding te verhinderen
- Denk na whitelist benaderingen voor toegestane omleidingsdomeinen
- Omleidingspatronen controleren voor ongebruikelijke activiteiten

**veiligheid van de Inhoud:**

- Onthoud de inhoud van uw berichttekst om scriptinjectie te voorkomen
- Een goed beleid voor inhoudsbeveiliging voor tekstopmaak implementeren
- Regelmatige veiligheidscontroles van doorreisbestemmingen

### Analyse en reeksspatiëring

**Overwegingen van de Implementatie:**

- **Goal die** volgt: De doelstellingen van de opstelling analyseert voor zowel dank u berichtmeningen en redirect voltooit
- **het reisafbeelding van de Gebruiker**: Spoor hoe de gebruikers met post-voorlegging ervaringen in wisselwerking staan
- **optimalisering van de Omzetting**: A/B test verschillende dankweldingen en richt bestemmingen opnieuw.

**strategieën van de Meting:**

- De tijd van de monitor besteed aan dankwoodberichten vóór ontslag
- Houd klikthrough tarieven voor verbindingen binnen dank u berichten bij
- Gebruikersgedrag op doelpagina&#39;s omleiden analyseren

## Controlepunten voor validatie

Na het configureren van uw ervaring na verzending:

**Controle van de Configuratie:**

- Formuliereigenschappen geven de geselecteerde optie Hartelijk dank correct weer
- Berichtinhoud wordt correct weergegeven in de voorvertoningsmodus
- URL&#39;s omleiden heeft de juiste notatie en is toegankelijk
- Alle koppelingen in berichten functioneren correct

**het testen van de gebruikerservaring:**

- Testformulieren verzenden om te controleren of de berichtweergave goed is
- Omleidingsfunctionaliteit testen voor verschillende browsers
- Controleer de mobiele reactiesnelheid van de bedankberichten
- Omleidingsdoelen correct laden bevestigen

**opstelling van Analytics:**

- Trackingcodes die correct zijn geïmplementeerd voor bedankberichten
- Omleiding van tracering geconfigureerd
- Gebeurtenissen voor het voltooien van het doel correct afvuren

## Volgende stappen

Nadat u uw ervaring na verzending hebt geconfigureerd:

- **prestaties van de Monitor**: Analyseanalyse van het overzicht om gebruikersbetrokkenheid met dankweldingen te begrijpen of pagina&#39;s om te leiden
- **herhaalt en verbetert**: De gebruiker van het gebruik koppelt en gegevensinzichten om uw post-voorleggingsstrategie te verfijnen
- **implementatie van de Schaal**: Pas succesvolle patronen over andere vormen in uw organisatie toe

**Verwante documentatie:**

- [Configuratie-handleiding voor verzending van formulieren](submit-action.md)
- [Beste praktijken van de Ervaring van de gebruiker](responsive-layout.md)
