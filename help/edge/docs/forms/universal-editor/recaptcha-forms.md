---
title: Bescherm uw Forms met reCAPTCHA - een visuele gids
description: Leer hoe u eenvoudig Google reCAPTCHA aan uw Edge Delivery Services-formulieren kunt toevoegen om spam en beide verzendingen te voorkomen
feature: Edge Delivery Services
keywords: reCAPTCHA in formulieren, met reCAPTCHA in de Universal Editor, voeg reCAPTCHA toe in formulieren, formulierbeveiliging, spambeveiliging
role: Developer
exl-id: 1f28bd13-133f-487e-8b01-334be7c08a3f
source-git-commit: babddee34b486960536ce7075684bbe660b6e120
workflow-type: tm+mt
source-wordcount: '1085'
ht-degree: 0%

---


# Bescherm uw Forms tegen spam met Google reCAPTCHA

<span class="preview"> Deze functie is beschikbaar via het programma voor vroege toegang. Om toegang te verzoeken, verzend een e-mail van uw officieel adres naar <a href="mailto:aem-forms-ea@adobe.com"> aem-forms-ea@adobe.com </a> met uw GitHub organisatienaam en bewaarplaatsnaam.</span>



## Waarom gebruikt u reCAPTCHA in uw formulieren?

| ![ Veiligheid ](/help/edge/docs/forms/universal-editor/assets/security.svg) | ![ Bot Bescherming ](/help/edge/docs/forms/universal-editor/assets/bot-protection.svg) | ![&#128279;](/help/edge/docs/forms/universal-editor/assets/user-experience.svg) Ervaring van 0&rbrace; Gebruiker |
|:-------------:|:-------------:|:-------------:|
| **Verbeterde Veiligheid** | **Bot &amp; Preventie Spam** | **Naadloze Ervaring van de Gebruiker** |
| Bescherm uw formulieren tegen frauduleuze activiteiten en kwaadaardige aanvallen | Stop automatische bots om uw formulieren te overstromen met irrelevante of schadelijke inhoud | De onzichtbare reCAPTCHA werkt achter de schermen zonder legitieme gebruikers te verstoren |

Een formulier voor belastingberekening met gevoelige financiële informatie moet bijvoorbeeld worden beschermd tegen misbruik. reCAPTCHA controleert of de inzendingen afkomstig zijn van echte gebruikers, niet van geautomatiseerde systemen.

## Kies uw reCAPTCHA-oplossing

Edge Delivery Services Forms ondersteunt twee Google reCAPTCHA-opties:

| ![ reCAPTCHA Onderneming ](/help/edge/docs/forms/universal-editor/assets/enterprise.svg) | ![ reCAPTCHA Standaard ](/help/edge/docs/forms/universal-editor/assets/standard.svg) |
|:-------------:|:-------------:|
| [**reCAPTCHA Onderneming**](#set-up-recaptcha-enterprise) | [**reCAPTCHA Standaard**](#set-up-recaptcha-standard) |
| Prestatiegeld, fraude-detectie op bedrijfsniveau met extra functies en aanpassingen | Gratis service met op score gebaseerde detectie die onzichtbaar op de achtergrond werkt |
| Meest geschikt voor: grote organisaties met complexe beveiligingsbehoeften | Meest geschikt voor: kleine tot middelgrote projecten met elementaire beschermingsbehoeften |

Beide opties gebruiken op score gebaseerde detectie (0,0 tot 1,0) om interactie tussen mens en bot te identificeren zonder de gebruikerservaring te verstoren.

## reCAPTCHA Enterprise instellen

### Stap 1: Vraag uw Google Cloud-referenties aan

Voordat u reCAPTCHA Enterprise configureert, hebt u het volgende nodig:

- A [ het project van de Wolk van Google ](https://cloud.google.com/recaptcha/docs/prepare-environment#before-you-begin) met uw [ identiteitskaart van het Project ](https://support.google.com/googleapi/answer/7014113)
- [ reCAPTCHA Onderneming API toegelaten ](https://cloud.google.com/recaptcha/docs/prepare-environment#enable-api) voor uw project
- Een [ API sleutel ](https://console.cloud.google.com/apis/credentials) voor authentificatie
- A [ plaats sleutel ](https://console.cloud.google.com/security/recaptcha) voor uw domein

### Stap 2: Een container voor cloudconfiguratie maken

![ de geleidelijke opstelling van de wolkenconfiguratie ](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)

1. Aanmelden bij de instantie van AEM-auteur
2. Navigeer aan **Hulpmiddelen** > **Algemeen** > **Browser van de Configuratie**
3. Vind uw vorm en selecteer **Eigenschappen**
4. Laat **de Configuraties van de Wolk** in de dialoog toe
5. Uw configuratie opslaan en publiceren

### Stap 3: Configure reCAPTCHA Enterprise Service

![ reCAPTCHA het configuratiescherm van de Onderneming ](/help/edge/docs/forms/universal-editor/assets/recaptcha-enterprise.png)

1. Ga naar **Hulpmiddelen** > **de Diensten van de Wolk** > **reCAPTCHA**
2. Navigeer aan uw vorm en klik **creëren**
3. In het dialoogvenster:
   - Selecteer **versie van de Onderneming ReCAPTCHA**
   - Voer een titel en naam in
   - Voeg uw project-id, site-sleutel en API-sleutel toe
   - Selecteer **Score-Gebaseerde plaats sleutel** als Zeer belangrijk type
   - Een drempelscore (0-1) instellen om mensen te onderscheiden van bots
4. Klik **creëren** en publiceer uw configuratie

## RECAPTCHA-standaard instellen

### Stap 1: Haal uw API-toetsen op

Alvorens te beginnen, [ verkrijg een reCAPTCHA API zeer belangrijk paar ](https://www.google.com/recaptcha/admin) (de sleutel van de Plaats en de Geheime sleutel) van de Console van Google reCAPTCHA.

>[!IMPORTANT]
>
>Edge Delivery Services Forms steunt slechts **versie 0&rbrace; reCAPTCHA op basis van de Score.**

### Stap 2: Een container voor cloudconfiguratie maken

Volg dezelfde stappen als in de versie van de Onderneming om een container van de wolkenconfiguratie tot stand te brengen en te publiceren.

### Stap 3: Vorm reCAPTCHA StandaardDienst

![ reCAPTCHA Standaard configuratiescherm ](/help/edge/docs/forms/universal-editor/assets/recaptcha.png)

1. Ga naar **Hulpmiddelen** > **de Diensten van de Wolk** > **reCAPTCHA**
2. Navigeer aan uw vorm en klik **creëren**
3. In het dialoogvenster:
   - Selecteer **ReCAPTCHA v2** versie
   - Voer een titel en naam in
   - Sitecode en geheime sleutel toevoegen
4. Klik **creëren** en publiceer uw configuratie

## reCAPTCHA toevoegen aan uw formulier

Nu u reCAPTCHA hebt geconfigureerd, is het tijd om het aan uw formulier toe te voegen:

![ Toevoegend de reCAPTCHA component aan een vorm ](/help/edge/docs/forms/universal-editor/assets/add-recaptcha-component.png)

1. Uw formulier openen in Universal Editor
2. Navigeren naar de sectie Adaptief formulier in de Inhoudsstructuur
3. Klik **toevoegen** pictogram en selecteren **Captcha (Onzichtbaar)** van de Adaptieve lijst van Componenten van de Vorm
   - *Alternatief, sleep en laat vallen de component in uw vorm*
4. Klik **publiceren** om uw vorm met reCAPTCHA bescherming bij te werken

Uw formulier is nu beveiligd! Weergeven op:
`https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form-name>`

![ Vorm met toegelaten reCAPTCHA bescherming ](/help/edge/docs/forms/universal-editor/assets/form-with-recaptcha.png)

## Uw reCAPTCHA-integratie valideren

Nadat u reCAPTCHA aan het formulier hebt toegevoegd, is het van essentieel belang dat u controleert of het formulier correct werkt. Hieronder wordt beschreven hoe u uw implementatie kunt valideren:

### Visuele controle

Hoewel reCAPTCHA v2 (Score-based) onzichtbaar werkt, kunt u de aanwezigheid ervan bevestigen door:

1. **inspecteer de paginabron**: Klik op uw vormpagina met de rechtermuisknop aan en selecteer &quot;de Pagina van de Mening Source&quot;
   - Zoek naar de reCAPTCHA manuscriptopname met uw plaatstoets
   - Voorbeeld: `<script src="https://www.google.com/recaptcha/api.js?render=YOUR_SITE_KEY"></script>`

2. **de Verzoeken van het Netwerk van de Controle**: Gebruikend browser ontwikkelaarshulpmiddelen (F12)
   - Uw formulier verzenden en netwerkaanvragen indienen bij `google.com/recaptcha`
   - Deze aanvragen geven aan dat reCAPTCHA actief is op uw formulier

### Functionele tests

Om te controleren of reCAPTCHA uw formulier daadwerkelijk beveiligt:

1. **Normale Test van de Verzending**:
   - Het formulier invullen met geldige gegevens
   - Het formulier verzenden in een normale menselijke ruimte
   - Controleren of het formulier is verzonden

2. **Bot-als de Test van het Gedrag**:
   - Open uw formulier in een incognito/Private Browsing-venster
   - Het formulier bijzonder snel invullen (automatisch vergelijkbaar gedrag)
   - Meerdere keren snel na elkaar verzenden
   - Als reCAPTCHA werkt, kunnen deze inzendingen worden geblokkeerd of gemarkeerd

3. **de Verslagen van de Verzending van de Vorm van de Controle**:
   - Controleer uw formulierverzendgegevens
   - Elke verzending moet een reCAPTCHA-score bevatten
   - Scores dichter bij 1,0 geven waarschijnlijke menselijke gebruikers aan
   - Scores dichter bij 0,0 geven potentiële botactiviteit aan

### Google reCAPTCHA-beheerconsole gebruiken

Voor Enterprise-gebruikers biedt de Google Cloud Console gedetailleerde analyses:

1. Ga naar de [ Console van de Wolk van Google ](https://console.cloud.google.com/)
2. Navigeer aan **Veiligheid** > **reCAPTCHA**
3. Sitecode selecteren
4. Evaluatie van de evaluatiekaarten en statistieken
5. Zoeken naar:
   - Verkeerspatronen
   - Score-distributies
   - Mogelijk frauduleuze activiteiten

Voor Standaard reCAPTCHA gebruikers, zijn de basisstatistieken beschikbaar in [ reCAPTCHA Admin Console ](https://www.google.com/recaptcha/admin/).

### De implementatie aanpassen

Gebaseerd op uw validatieresultaten:

- Als legitieme gebruikers worden geblokkeerd, kunt u de drempelscore verlagen
- Als u nog spam ontvangt, denk na verhogend uw drempelscore
- Controleer voor blijvende problemen uw reCAPTCHA-configuratie en controleer of alle toetsen correct zijn ingevoerd

Vergeet niet dat reCAPTCHA automatisch leren gebruikt om in de loop der tijd te verbeteren. Hierdoor kan de doeltreffendheid van het programma toenemen wanneer het de verkeerspatronen van uw site leert.

## Problemen oplossen en veelgestelde vragen

| ![ Vraag ](/help/edge/docs/forms/universal-editor/assets/question.svg) | ![ Antwoord ](/help/edge/docs/forms/universal-editor/assets/answer.svg) |
|:-------------:|:-------------:|
| **wat als ik geen configuratie reCAPTCHA creeer?** | Het systeem zal naar een configuratie in de Globale Container zoeken. Als er niets bestaat, wordt er een fout weergegeven. |
| **wat als ik veelvoudige configuraties creeer?** | Het systeem gebruikt automatisch de eerste gemaakte configuratie. |
| **waarom zijn mijn veranderingen niet zichtbaar op gepubliceerde URL?** | Zorg ervoor dat u het formulier opnieuw publiceert nadat u wijzigingen hebt aangebracht. |
| **welke reCAPTCHA de diensten worden gesteund?** | Edge Delivery Services Forms ondersteunt alleen op score gebaseerde reCAPTCHA-services. |

## Volgende stappen

Nu u uw formulier hebt beveiligd met reCAPTCHA:

- **bevestigt uw implementatie**: Volg de [ bevestigingsstappen ](#-validating-your-recaptcha-integration) om te verzekeren reCAPTCHA correct werkt
- **prestaties van de Monitor**: controleer regelmatig uw Google reCAPTCHA dashboard voor verdachte activiteiten en scoreverdelingen
- **Fijne montages**: Pas uw drempelscore aan die op uw veiligheidsbehoeften en gebruikerservaring wordt gebaseerd terugkoppelen
- **Verblijf bijgewerkt**: Houd uw reCAPTCHA implementatie huidig met Google het recentste veiligheidsaanbevelingen
- **wijs uw team** voor: Deel kennis over hoe reCAPTCHA werkt en hoe te om de analyses te interpreteren
- **verzamel terugkoppelt**: De gebruikerservaring van de monitor om wettige gebruikers te verzekeren wordt niet geblokkeerd

Houd er rekening mee dat effectieve formulierbescherming een doorlopend proces is dat regelmatig moet worden gecontroleerd en aangepast.


