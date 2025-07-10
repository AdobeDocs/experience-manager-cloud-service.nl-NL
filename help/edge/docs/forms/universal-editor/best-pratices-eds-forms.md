---
title: Aanbevolen procedures voor het ontwerpen van krachtige Forms
description: Leer essentiële beste praktijken voor het creëren van gebruikersvriendelijk, toegankelijk, en hoog-presterende vormen gebruikend AEM Forms. Verbeter de gegevenskwaliteit, de gebruikerservaring en de prestaties bij verzending.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 67b6873b-bb93-4d38-963c-2ca65a1a644b
source-git-commit: 75d8ea4f0913e690e3374d62c6e7dcc44ea74205
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# Aanbevolen procedures voor het maken van Forms

Het bouwen van geweldige formulieren gaat verder dan alleen de technologie. Hieronder wordt beschreven hoe u ervoor kunt zorgen dat uw formulieren gebruiksvriendelijk zijn en hun doelen bereiken:

## Gebruikersvriendelijke en toegankelijke Forms ontwerpen

* **Gebruik Duidelijke, Zichtbare Etiketten:** Elk vormgebied vereist a `<label>`. Vertrouw niet alleen op plaatsaanduidingstekst (tekst in het invoerveld), omdat deze verdwijnt wanneer gebruikers typen en slecht is voor de toegankelijkheid.
   * *Goed:* `<label for="email">Email Address:</label> <input type="email" id="email" placeholder="you@example.com">`
   * *Slecht:* `<input type="email" placeholder="Email Address">`
* **houd het Eenvoudig:** gebruik standaardHTML inputtypes (`<input type="date">`, `<input type="tel">`) waar mogelijk. Ze hebben vaak betere mobiele ondersteuning en toegankelijkheid dan complexe aangepaste widgets.
* **Logische Orde en het Groeperen:** schikt gebieden op een manier die aan de gebruiker steek houdt. Groepeer verwante velden met `<fieldset>` en `<legend>` .
* **verstrekt Duidelijke Instructies:** voor om het even welke gebieden die verwarrend zouden kunnen zijn, bieden beknopte hulptekst of tooltips aan.
* **Navigatie van het Toetsenbord:** zorg ervoor de gebruikers door uw volledige vorm kunnen navigeren gebruikend slechts het toetsenbord (Lusje, Shift+Tab, binnengaan, Spatiebar).
* **de Behandeling van de Fout:** maak fouten duidelijk en gemakkelijk te verbeteren. Geef foutberichten weer naast het desbetreffende veld en leg uit wat er moet worden opgelost.

* **ervoor zorgend Snel Uw Lading van Forms en is Zichtbaar**

   * **Plaats Forms Prominently:** als een vorm belangrijk is, zorg ervoor de gebruikers het zonder teveel het scrollen gemakkelijk kunnen zien (&quot;boven de vouwt&quot; indien mogelijk). Uit Adobe-onderzoek blijkt dat veel formulieren weinig interactie hebben omdat ze verborgen zijn.
   * **Optimize Assets:** houd om het even welke douaneJavaScript of CSS voor uw vormen zo klein mogelijk om snelle ladingstijden te verzekeren. Edge Delivery Services helpt bij het laden van de basispagina, maar zware formulierscripts kunnen de zaken nog steeds vertragen.

* **Verantwoordelijk Behandelend de Gegevens van de Gebruiker**
   * **vraagt slechts wat u nodig hebt:** de minder Persoonlijke Identificeerbare Informatie (PII) u vraagt om, beter. Elk veld kan een gebruiker ertoe aanzetten het formulier af te sluiten.
   * **ben Transparant:** verklaar *duidelijk waarom* u bepaalde informatie nodig hebt en *hoe het* zal worden gebruikt. Link naar uw privacybeleid. Dit bouwt vertrouwen op.

* **het Verbeteren van de Ervaring van de Gebruiker: Alternatieven Captcha**

   * **herdenk Zichtbare Captchas:** die &quot;de golvende tekst&quot;typen of &quot;klikken alle tests van verkeerslichten&quot;kunnen zeer frustrerend voor gebruikers, vooral die met handicaps zijn, en vaak tot hoge dalingstarieven leiden.

* **overweeg Alternatieven:**
   * **Gebieden van de Honeypot:** voeg een verborgen gebied toe dat slechts bommen zouden vullen. Als het gegevens heeft, is de voorlegging waarschijnlijk spam.
   * **op tijd-Gebaseerde Controles:** Meet hoe snel een vorm wordt voorgelegd. Indieningen die te snel zijn, zijn vaak knelpunten.
   * **Onzichtbare reCAPTCHA (v3):** Deze dienst van Google analyseert gebruikersgedrag op de achtergrond en stelt slechts een uitdaging voor als de gebruiker verdacht lijkt. Dit is vaak een veel betere gebruikerservaring.

## Formulierontwerp doet en doet

| ✅ Do - Voor betere Forms | ❌ Niet - vermijd deze |
|----------------------------------------------------------------------|------------------------------------------------------------------|
| Zichtbare `<label>` -tags gebruiken voor alle velden | Alleen plaatsaanduidingstekst gebruiken in plaats van juiste labels |
| Voorkeur voor standaard HTML-invoertypen (bijvoorbeeld `<input type="email">`) | Te complexe aangepaste widgets gebruiken |
| Volledige toetsenbordnavigatie garanderen | Vage of ontbrekende foutberichten opgeven |
| Duidelijke, uitvoerbare foutberichten weergeven | Ongerechtvaardigde verzoeken om buitensporige persoonsgegevens |
| Alleen om de benodigde informatie vragen | Vast-aan-oplossing zichtbare CAPTCHAs gebruiken |
| Uitleggen hoe gegevens worden gebruikt (privacyinformatie of koppelingen) | Het formulier diep op de pagina verbergen |
| Onzichtbare of gedragstechnieken gebruiken |                                                                  |
| Het formulier gemakkelijk op de pagina te vinden maken (opvallende plaatsing) |                                                                  |


## Volgende stappen

Deze handleiding bevat een overzicht van het gebruik van formulieren met AEM Edge Delivery Services. Raadpleeg de officiële documentatie bij Adobe Experience Manager voor gedetailleerde, stapsgewijze instructies over specifieke configuraties:

* [Authoring op basis van documenten met Edge Delivery Services Forms](/help/edge/docs/forms/tutorial.md)
* [Universele editor met Edge Delivery Services Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [ Document Authoring (DA) en het Inbedden Inhoud ](https://www.aem.live/developer/da-tutorial)
* [ de Verzenddienst van AEM Forms ](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)
