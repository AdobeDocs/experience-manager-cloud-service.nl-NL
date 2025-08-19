---
title: AI Assistant in AEM
description: Met AI Assistant kunt u zoeken naar antwoorden en problemen oplossen voor de oplossingen die beschikbaar zijn in Adobe Experience Manager.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="Beta" type="Positive"
hide: false
hidefromtoc: true
exl-id: 6cdf7f65-7112-420a-90c1-564f0ef8ceaf
source-git-commit: 86281f539656ccdcb267a2de3aa0d40c0c8e637d
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 0%

---

# AI Assistant in AEM {#aem-home}

De AEM (Adobe Experience Manager) AI Assistant biedt een conversatie-interface die is ontworpen om het zoeken naar antwoorden op vragen over Adobe Experience Manager te stroomlijnen. Het helpt u onmiddellijke antwoorden aan uw product-verwante vragen van AEM (*beschikbaar aan alle gebruikers*) krijgen, en de verwezenlijking van het steunkaartje automatiseren (*beschikbaar om Admins* te steunen).

De AI Assistant ondersteunt AEM as a Cloud Service, inclusief de volgende oplossingen:

* Experience Hub-overzichtspagina
* Edge Delivery Services
* Sites
* Assets
* Forms
* Dynamische media
* Cloud Manager


Het is rechtstreeks ingesloten in AEM en toegankelijk vanuit AEM Experience Hub, Cloud Manager en de gebruikersinterface van de auteur.

De volgende 3 minuten, 39 seconden video levert een geleidelijke analyse van AI Medewerker in AEM.

>[!VIDEO](https://video.tv.adobe.com/v/3470354?learn=on)

## Toegang krijgen tot AI Assistant in AEM{#get-access}

1. [ de Klanten moeten de AI van de Gen rijder met Adobe ](https://fieldreadiness-adobe.highspot.com/items/665f831c9f831b011aeda057#1) ondertekenen.

   De GenAI Rider is een juridische overeenkomst tussen een klant en Adobe, die vereist is om de meeste AI- en Angic-mogelijkheden te gebruiken. Neem contact op met de klantenservice van Adobe voor meer informatie.

1. AEM Admin vormt de AI Medewerker voor gebruik in hun organisatie. Zie [ de Medewerker AI in AEM ](/help/implementing/cloud-manager/aem-ai-assistant-admin.md) vormen.

<!--
>[!IMPORTANT]
>Be sure you have reviewed and submitted the user agreement so Adobe can enable the AI Assistant feature for you to test out and participate in the private beta program.
>
>For any questions, send an email to [Grp-AEMAIASSISTANT@adobe.com](mailto:Grp-AEMAIASSISTANT@adobe.com) from your email address associated with your Adobe ID. -->

## Scope {#scope}

Het huidige bereik van de AI Assistant in AEM is gericht op het aanpakken van productkennisvragen voor AEMr. as a Cloud Service. Dit toepassingsgebied omvat uitgebreide steun voor belangrijke gebieden. <!--, such as Sites, Assets, Forms, Edge Delivery Services, Dynamic Media, and Cloud Manager. -->

* **Gebieden**: Beschikbaar over AEM Experience Hub, Auteur UI, Cloud Manager.
* **Mogelijkheden**: Product-kennis en eerste-stop voor het oplossen van problemen en begeleiding, geautomatiseerde verwezenlijking van steunkaartjes en raadpleging.
* **Waarde**: Bespart tijd, versnelt het leren en tijd aan waarde, vermindert de behoefte om steunkaartjes manueel tot stand te brengen, en verbetert efficiency in het creëren van steunkaartjes.

## Privacy, beveiliging en bestuur{#privacy-security-governance}

De AI-assistent in AEM is ontworpen met een sterke nadruk op privacy, veiligheid en bestuur.

In dit artikel worden de vertrouwde functies beschreven die u kunt verwachten van de AI Assistant in AEM:

* AI Assistant gebruikt geen persoonsgegevens in AEM, ook niet voor opleidingsdoeleinden.
* AI Assistant in AEM heeft geen toegang tot consumentengegevens.
* Expliciete toestemming wordt vereist om met AI Medewerker in AEM in wisselwerking te staan.
* Door de gebruiker opgegeven vragen (vragen, query&#39;s enzovoort) worden niet gedeeld met andere klanten.

<!-- See also [Security at Adobe whitepaper](). NEED ACTIVE LINK FROM ADRIAN NICOLAE TANASE. CURRENTLY 404. -->

## Krijg de AI Medewerker in AEM voor productkennis en geautomatiseerde steunkaartenverwezenlijking te kennen {#ai-prod-insights}

De productkennis omvat concepten en onderwerpen die uit de documentatie van de Liga van de Ervaring van Adobe worden afgeleid. Deze vragen kunnen in de volgende subgroepen worden ingedeeld:


| Productkennis | Beschikbaar aan alle gebruikers <br> Voorbeelden |
| :--- | :--- |
| Aanbevolen lessen | <ul><li>Wat is de Universele Redacteur?</li><li>Hoe maak ik een programma in Cloud Manager?</li></ul> |
| Openbare detectie | <ul><li>Hoe gebruik ik de Universal Editor?</li><li>Is er een manier om inhoud van één milieu aan een andere te kopiëren?</li></ul> |
| Problemen oplossen | <ul><li>Waarom heb ik geen toegang tot de Universal Editor?</li><li>Waarom mislukt mijn pijpleiding?</li></ul> |
| **de kaartverwezenlijking van de Steun** | **Beschikbaar om Admins slechts te steunen &#x200B;**<br>**Voorbeelden** |
| Geautomatiseerde steun de verwezenlijking van kaartjes het vangen AI Hulp praatjegeschiedenis en context | <ul><li>Maak een ondersteuningsticket voor mij.</li></ul> |
| Status van ondersteuningsticket ophalen | <ul><li>Toon me alle steunkaartjes die ik heb geopend.</li><li>Toon me de status van kaartje &quot;E—&quot;</li></ul> |

{style="table-layout:auto"}


## Werkelijke vragen stellen {#ai-craft-questions}

Om de meest accurate antwoorden van de AI Assistant in AEM te kunnen ontvangen, is het belangrijk dat u uw vragen duidelijk en in een context plaatst. Gebruik de volgende uiteinden om ervoor te zorgen dat uw vragen duidelijk en goed gestructureerd zijn:

* Geef uw taak of vraag duidelijk beknopt weer.
* Vermijd dubbelzinnige bewoordingen of te complexe syntaxis om het begrip te verbeteren.
* Neem de relevante context van uw taak of vraag op, aangezien deze benadering de AI Assistant in AEM helpt nauwkeuriger en relevantere antwoorden te geven.
In uw vraag helpt het bijvoorbeeld om de AEM-oplossing waarin u werkt, een naam te geven: Sites, Assets, Dynamic Media, Edge Delivery Services, Cloud Manager of Forms.

### Voorbeelden van niet-ondersteunde vragen {#ai-unsupported-questions}

| Gebied | Voorbeelden |
| --- | --- |
| Operationele inzichten | <ul><li>Hoeveel ontwikkelomgevingen bestaan er in mijn huurder?</li><li>Wie is de laatste productiepijplijn begonnen?</li></ul> |
| Problemen oplossen | <ul><li>Waarom schiet mijn productiepijpleiding tekort?</li></ul> |
| Taak en automatisering | <ul><li>Vorm een pijpleiding van de codekwaliteit van een dev tak voor me.</li></ul> |


## AI-assistent gebruiken in AEM {#ai-use}

<!-- UNHIDE AFTER BETA or at GA
### Enable AI Assistant in AEM access through Admin Console 

To use the AI Assistant in AEM, your organization must opt in at the Admin Console level. A product administrator creates (or chooses) a user group and grants it the new "AI Assistant" permission. Anyone added to that group instantly gains access to the Assistant across AEM. If the goal is company-wide availability, the admin simply assigns all users to that group.

![AI Assistant in AEM in the Admin Console](/help/implementing/cloud-manager/assets/ai-assistant-admin-console.png)

From an employee's perspective, the process is straightforward: identify the product administrator for Adobe Experience Manager in your organization and request to be added to the AI-enabled user group. Once you appear in that group, the Assistant icon shows up automatically the next time you sign in.

Administrators should keep normal Cloud Manager governance in mind. Hold product administrator rights in the Admin Console to create profiles, manage user groups, or edit permissions. If users also need the Assistant's built-in **Create Support Ticket** feature, add the standard **Support Admin** role (standard Admin Console role) to the same individuals or group.

![Technical support ticket creation in the AI Assistant in AEM of the Admin Console](/help/implementing/cloud-manager/assets/ai-assistant-admin-console-support-ticket.png)

For a guided walkthrough of setting up users and groups in AEM as a Cloud Service, see [Configuring access to AEM as a Cloud Service ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/accessing/overview). 

See also [Custom Permissions](/help/implementing/cloud-manager/custom-permissions.md). -->


### Een AI-assistent in een AEM-gesprek starten of opnieuw instellen

U kunt de AI Medewerker in AEM terugstellen en een nieuw gesprek beginnen wanneer u onderwerpen wilt veranderen. Deze capaciteit is vooral nuttig wanneer het oplossen van problemenvragen die ontbreken of onjuiste informatie verstrekken.

![ de gespreksknoop van het Begin ](/help/implementing/cloud-manager/assets/ai-assistant-start-conversation.png)

**om een gesprek te beginnen of terug te stellen:**

1. Voor de Medewerker AI in AEM, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).
1. Om de AI Medewerker van een nieuw onderwerp of een verandering in onderwerp te informeren, klik **Nieuwe Gesprek van het Begin**.

### Detectie gebruiken

AI Assistant in AEM bevat een functie voor het opsporen van ontdekkingen waarmee u de ondersteunde onderwerpen en categorieën kunt verkennen.

![ het gloeilamppictogram van Idea ](/help/implementing/cloud-manager/assets/ai-assistant-idea.png)

**om ontdekkingsbaarheid te gebruiken:**

1. Dichtbij de hoger-juiste hoek van de AI Medewerker, klik ![ leer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Learn_18_N.svg).
1. Selecteer een categorie om een lijst met verwante vragen weer te geven.
1. Kies een vraag om meer inzicht te krijgen in de typen vragen die de AI Assistant in AEM kan beantwoorden.

### Feedback geven op de AI Assistant in AEM

Met uw invoer verbetert u de AI Assistant in AEM voor betere prestaties en nauwkeurigheid.

Deel je feedback op je ervaring met AI Assistant in AEM door de volgende opties te kiezen:

![ duimen omhoog, duimen neer, en vlagpictogrammen ](/help/implementing/cloud-manager/assets/ai-assistant-feedback.png)

| Pictogram | Beschrijving |
| --- | --- |
| ![ duimen omhoog buiten pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbUpOutline_18_N.svg) | Klik om aan te geven wat goed is gegaan en positieve feedback te delen. |
| ![ duimen neer outine pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbDownOutline_18_N.svg) | Klik voor suggesties voor verbetering. Voeg specifieke opmerkingen toe over uw ervaring, die dagelijks worden gecontroleerd. |
| ![ het pictogram van de Vlag ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Flag_18_N.svg) | Klik om zorgen te melden of gedetailleerde feedback te geven over uw interactie met de AI Assistant in AEM. |

## Veelgestelde vragen over AI Assistant in AEM {#ai-faq}

Hier volgen een aantal veelgestelde vragen over de AI Assistant:

* **wordt de informatie verstrekt door de Medewerker AI in AEM in real time?**\
  Nee. AI Assistant is afkomstig uit documentatie van de Adobe Experience League. Het kan enige tijd duren voordat de inhoud wordt bijgewerkt.
* **Welke toepassingen van Adobe steunt de Medewerker van AI in AEM?**\
  Op dit moment biedt AI Assistant ondersteuning voor onderzoeken naar productkennis in AEM as a Cloud Service, waaronder Sites, Assets, Dynamic Media, Cloud Manager en Forms.
* **wat zijn de mogelijkheden van AI Medewerker in AEM?**\
  AI Assistant in AEM is ontworpen om vragen te beantwoorden over Adobe-productkennis.
* **gebruikt de AI Medewerker in AEM persoonlijke informatie voor opleidingsgegevens?**\
  Nee. AI Assistant in AEM gebruikt geen persoonlijke informatie voor opleidingsdoeleinden. Vermijd het delen van persoonlijke gegevens over uzelf of anderen, waaronder namen of contactgegevens, met de AI Assistant in AEM.

<!-- IS THE DOCUMENTATION BELOW STILL NEEDED? IF SO, GO AHEAD AND DELETE THE COMMENT TAGS!!

## AEM Forms AI Assistant (Forms Experience Builder) {#ai-forms-builder}

In addition to the general AI Assistant in AEM for product knowledge, AEM offers a specialized **[AEM Forms AI Assistant (Forms Experience Builder)](/help/edge/docs/forms/forms-ai-assistant.md)**. This enhanced assistant can actively help you create and configure forms through natural language prompts and answer questions specific to forms.

### Key capabilities

The AEM Forms AI Assistant provides:

* **Form Creation**: Create new forms from scratch using natural language descriptions.
* **Design Import**: Convert existing designs (PDF, Figma, images) into functional AEM Forms. 
* **Form Configuration**: Add fields, panels, validation rules, and conditional logic.
* **Layout Management**: Organize form structure and optimize for different devices.
* **Integration Setup**: Configure form submissions and data handling.
* **Product Knowledge**: Answer questions about AEM Forms features and best practices.

### Where to access

The AEM Forms AI Assistant is available in the following:

* **Universal Editor**: For Edge Delivery Services forms with visual editing capabilities.
* **Adaptive Forms Editor**: For detailed form configuration and advanced features.
* **Forms Management UI**: For high-level form creation and management tasks.

### Getting started

>[!NOTE]
>
> The AEM Forms AI Assistant (Forms Experience Builder) is available under the private beta program. Send an email from your work address to [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) to request access.

To learn more about using the AEM Forms AI Assistant , see the [AEM Forms AI Assistant](/help/edge/docs/forms/forms-ai-assistant.md) documentation.

### Example Use Cases

* **"Create a customer feedback form with name, email, rating, and comments fields"**
* **"Convert this uploaded PDF application form into a digital adaptive form"**  
* **"Add conditional logic to show spouse information only when marital status is 'Married'"**
* **"Configure this form to submit data to the Customer Relationship Management system"**

This specialized AEM Forms AI Assistant represents the next evolution in form building, combining the power of AI with AEM's robust forms capabilities to streamline your form creation workflow.
