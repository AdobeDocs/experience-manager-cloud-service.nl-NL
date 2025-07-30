---
title: AI Assistant in Adobe Experience Manager (Beta)
description: Met AI Assistant kunt u zoeken naar antwoorden en problemen oplossen voor de oplossingen die beschikbaar zijn in Adobe Experience Manager.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: false
hidefromtoc: true
exl-id: 6cdf7f65-7112-420a-90c1-564f0ef8ceaf
source-git-commit: 577e15165057fcf6537b4b0b738a1f45e5feb097
workflow-type: tm+mt
source-wordcount: '1308'
ht-degree: 0%

---

# AI Assistant in Adobe Experience Manager {#aem-home}

De AEM (Adobe Experience Manager) AI Assistant biedt een conversatie-interface die is ontworpen om het zoeken naar antwoorden op vragen over Adobe Experience Manager te stroomlijnen. Het helpt u onmiddellijke antwoorden aan uw product-verwante vragen van AEM (*beschikbaar aan alle gebruikers*) krijgen, en de verwezenlijking van het steunkaartje automatiseren (*beschikbaar om Admins* te steunen).

Tijdens de persoonlijke bètaversie biedt de AEM AI Assistant ondersteuning voor AEM as a Cloud Service, inclusief de volgende oplossingen:

* Sites
* Assets
* Dynamische media
* Edge Delivery Services
* Cloud Manager
* Forms

Het is rechtstreeks ingesloten in AEM en toegankelijk vanuit AEM Experience Hub, Cloud Manager en de gebruikersinterface van de auteur.

>[!IMPORTANT]
>Controleer of u de gebruikersovereenkomst hebt gecontroleerd en verzonden, zodat Adobe de functie AI Assistant kan inschakelen zodat u het persoonlijke bètaprogramma kunt uittesten en hieraan kunt deelnemen.
>
>Voor om het even welke vragen, verzend een e-mail naar [ Grp-AEMAIASSISTANT@adobe.com ](mailto:Grp-AEMAIASSISTANT@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID.

## Scope {#scope}

Het huidige bereik van de AEM AI Assistant is gericht op het aanpakken van productkennisvragen voor Adobe Experience Manager as a Cloud Service. Dit bereik omvat uitgebreide ondersteuning voor belangrijke gebieden, zoals Sites, Assets, Forms, Edge Delivery Services en Cloud Manager.

* **Gebieden**: Beschikbaar over AEM Experience Hub, Auteur UI, Cloud Manager.
* **Mogelijkheden**: Product-kennis en eerste-stop voor het oplossen van problemen en begeleiding, geautomatiseerde verwezenlijking van steunkaartjes en raadpleging.
* **Waarde**: Bespart tijd, versnelt het leren en tijd aan waarde, vermindert de behoefte om steunkaartjes manueel tot stand te brengen, en verbetert efficiency in het creëren van steunkaartjes.

## Privacy, beveiliging en bestuur{#privacy-security-governance}

De AEM AI Assistant is ontworpen met een sterke nadruk op privacy, veiligheid en bestuur.

In dit artikel worden de vertrouwde functies beschreven die u kunt verwachten van de AEM AI Assistant:

* AEM AI Assistant gebruikt geen persoonsgegevens, ook niet voor opleidingsdoeleinden.
* AEM AI Assistant heeft geen toegang tot consumentengegevens.
* Expliciete toestemming wordt vereist om met de Medewerker van AEM te communiceren AI.
* Door de gebruiker opgegeven vragen (vragen, query&#39;s enzovoort) worden niet gedeeld met andere klanten.

<!-- See also [Security at Adobe whitepaper](). NEED ACTIVE LINK FROM ADRIAN NICOLAE TANASE. CURRENTLY 404. -->


## Vraag de AEM AI Assistant om productkennis en automatische ondersteuning voor het maken van tickets {#ai-prod-insights}

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

Om de meest nauwkeurige antwoorden van de AEM AI Assistant te ontvangen, is het belangrijk dat u uw vragen duidelijk en in een context plaatst. Gebruik de volgende uiteinden om ervoor te zorgen dat uw vragen duidelijk en goed gestructureerd zijn:

* Geef uw taak of vraag duidelijk beknopt weer.
* Vermijd dubbelzinnige bewoordingen of te complexe syntaxis om het begrip te verbeteren.
* Neem de relevante context van uw taak of vraag op, omdat deze aanpak de AEM AI Assistant helpt preciezere en relevante antwoorden te geven.
In uw vraag helpt het bijvoorbeeld om de AEM-oplossing waarin u werkt, een naam te geven: Sites, Assets, Dynamic Media, Edge Delivery Services, Cloud Manager of Forms.

### Voorbeelden van niet-ondersteunde vragen {#ai-unsupported-questions}

| Gebied | Voorbeelden |
| --- | --- |
| Operationele inzichten | <ul><li>Hoeveel ontwikkelomgevingen bestaan er in mijn huurder?</li><li>Wie is de laatste productiepijplijn begonnen?</li></ul> |
| Problemen oplossen | <ul><li>Waarom schiet mijn productiepijpleiding tekort?</li></ul> |
| Taak en automatisering | <ul><li>Vorm een pijpleiding van de codekwaliteit van een dev tak voor me.</li></ul> |


## AEM AI Assistant gebruiken {#ai-use}

<!-- UNHIDE AFTER BETA or at GA
### Enable AEM AI Assistant access through Admin Console 

To use the AEM AI Assistant, your organization must opt in at the Admin Console level. A product administrator creates (or chooses) a user group and grants it the new "AI Assistant" permission. Anyone added to that group instantly gains access to the Assistant across AEM. If the goal is company-wide availability, the admin simply assigns all users to that group.

![AEM AI Assistant in the Admin Console](/help/implementing/cloud-manager/assets/ai-assistant-admin-console.png)

From an employee's perspective, the process is straightforward: identify the product administrator for Adobe Experience Manager in your organization and request to be added to the AI-enabled user group. Once you appear in that group, the Assistant icon shows up automatically the next time you sign in.

Administrators should keep normal Cloud Manager governance in mind. Hold product administrator rights in the Admin Console to create profiles, manage user groups, or edit permissions. If users also need the Assistant's built-in **Create Support Ticket** feature, add the standard **Support Admin** role (standard Admin Console role) to the same individuals or group.

![Technical support ticket creation in the AEM AI Assistant of the Admin Console](/help/implementing/cloud-manager/assets/ai-assistant-admin-console-support-ticket.png)

For a guided walkthrough of setting up users and groups in AEM as a Cloud Service, see [Configuring access to AEM as a Cloud Service ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/accessing/overview). 

See also [Custom Permissions](/help/implementing/cloud-manager/custom-permissions.md). -->


### Een gesprek starten of opnieuw instellen

U kunt de Medewerker van AEM terugstellen AI en een nieuw gesprek beginnen wanneer u onderwerpen wilt veranderen. Deze capaciteit is vooral nuttig wanneer het oplossen van problemenvragen die ontbreken of onjuiste informatie verstrekken.

![ de gespreksknoop van het Begin ](/help/implementing/cloud-manager/assets/ai-assistant-start-conversation.png)

**om een gesprek te beginnen of terug te stellen:**

1. Voor de Medewerker van AEM AI, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).
1. Om de Medewerker van AEM AI van een nieuw onderwerp of een verandering in onderwerp te informeren, klik **Nieuwe Gesprek van het Begin**.

### Detectie gebruiken

AEM AI Assistant bevat een functie waarmee u de ondersteunde onderwerpen en categorieën kunt verkennen.

![ het gloeilamppictogram van Idea ](/help/implementing/cloud-manager/assets/ai-assistant-idea.png)

**om ontdekkingsbaarheid te gebruiken:**

1. Vlak de hoger-juiste hoek van de Medewerker van AEM AI, klik ![ leren pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Learn_18_N.svg).
1. Selecteer een categorie om een lijst met verwante vragen weer te geven.
1. Kies een vraag om meer inzicht te krijgen in de typen vragen die de AEM AI Assistant kan beantwoorden.

### Feedback geven op de AEM AI Assistant

Met uw invoer verbetert u de AEM AI Assistant voor betere prestaties en nauwkeurigheid.

Deel je feedback op je ervaring met AEM AI Assistant via de volgende opties:

![ duimen omhoog, duimen neer, en vlagpictogrammen ](/help/implementing/cloud-manager/assets/ai-assistant-feedback.png)

| Pictogram | Beschrijving |
| --- | --- |
| ![ duimen omhoog buiten pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbUpOutline_18_N.svg) | Klik om aan te geven wat goed is gegaan en positieve feedback te delen. |
| ![ duimen neer outine pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbDownOutline_18_N.svg) | Klik voor suggesties voor verbetering. Voeg specifieke opmerkingen toe over uw ervaring, die dagelijks worden gecontroleerd. |
| ![ het pictogram van de Vlag ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Flag_18_N.svg) | Klik om zorgen te melden of gedetailleerde feedback over uw interactie met de AEM AI Assistant te geven. |

## Veelgestelde vragen over AEM AI Assistant {#ai-faq}

Hier volgen een aantal veelgestelde vragen over de AI Assistant:

* **wordt de informatie verstrekt door de Medewerker van AEM AI in real time?**\
  Nee. AI Assistant is afkomstig uit documentatie van de Adobe Experience League. Het kan enige tijd duren voordat de inhoud wordt bijgewerkt.
* **Welke toepassingen van Adobe steunt de Hulp van AEM AI?**\
  Op dit moment biedt AI Assistant ondersteuning voor onderzoeken naar productkennis in AEM as a Cloud Service, waaronder Sites, Assets, Dynamic Media, Cloud Manager en Forms.
* **wat zijn de mogelijkheden van de Medewerker van AEM AI?**\
  AEM AI Assistant is ontworpen om vragen te beantwoorden over Adobe-productkennis.
* **gebruikt de Medewerker van AEM AI persoonlijke informatie voor opleidingsgegevens?**\
  Nee. AEM AI Assistant gebruikt geen persoonlijke gegevens voor trainingsdoeleinden. Vermijd het delen van persoonlijke gegevens over uzelf of anderen, waaronder namen of contactgegevens, met de AEM AI Assistant.


## AEM Forms AI Assistant (Forms Experience Builder) {#ai-forms-builder}

Naast algemene AEM AI Medewerker voor productkennis, biedt AEM een gespecialiseerde **[Medewerker van AEM Forms AI (de Bouwer van de Ervaring van Forms)](/help/edge/docs/forms/forms-ai-assistant.md)** aan. Deze uitgebreide assistent kan u actief helpen bij het maken en configureren van formulieren via herinneringen voor natuurlijke talen en het beantwoorden van vragen die specifiek zijn voor formulieren.

### Belangrijkste mogelijkheden

De AEM Forms AI Assistant biedt:

* **het Maken van de Vorm**: Creeer nieuwe vormen van kras gebruikend natuurlijke taalbeschrijvingen.
* **de Invoer van het Ontwerp**: Zet bestaande ontwerpen (PDF, Figma, beelden) in functionele AEM Forms om.
* **Configuratie van de Vorm**: Voeg gebieden, panelen, bevestigingsregels, en voorwaardelijke logica toe.
* **het Beheer van de Lay-out**: Organiseer vormstructuur en optimaliseer voor verschillende apparaten.
* **Opstelling van de Integratie**: Vorm voorlegging en gegevens behandeling vormen.
* **Kennis van het Product**: Antwoord vragen over de eigenschappen van AEM Forms en beste praktijken.

### Waar toegang is

De AEM Forms AI Assistant is als volgt beschikbaar:

* **Universele Redacteur**: Voor de vormen van Edge Delivery Services met visuele het uitgeven mogelijkheden.
* **Aangepaste Redacteur van Forms**: Voor gedetailleerde vormconfiguratie en geavanceerde eigenschappen.
* **het Beheer UI van Forms**: Voor de verwezenlijking en beheerstaken van de vorm op hoog niveau.

### Aan de slag

>[!NOTE]
>
> De AEM Forms AI Assistant (Forms Experience Builder) is beschikbaar in het kader van het persoonlijke bètaprogramma. Verzend een e-mail van uw het werkadres naar [ aem-forms-ea@adobe.com ](mailto:aem-forms-ea@adobe.com) om toegang te verzoeken.

Meer over het gebruiken van de Medewerker van AEM Forms AI leren, zie de [ Medewerker van AEM Forms AI ](/help/edge/docs/forms/forms-ai-assistant.md) documentatie.

### Voorbeelden van gevallen

* **&quot;Creeer een klant terugkoppel vorm met naam, e-mail, classificatie, en commentaargebieden&quot;**
* **&quot;Convert this uploaded PDF application form to a digital adaptive form&quot;**
* **&quot;voeg voorwaardelijke logica toe om de informatie van de echtgeno(o)t slechts te tonen wanneer de huwelijksstatus &quot;Gehuwd&quot;is&quot;**
* **&quot;Vorm dit formulier om gegevens naar het systeem van het Beheer van de Verhouding van de Klant voor te leggen&quot;**

Deze gespecialiseerde AEM Forms AI Assistant vertegenwoordigt de volgende evolutie in het maken van formulieren, waarbij de kracht van AI wordt gecombineerd met robuuste formuliermogelijkheden van AEM om de workflow voor het maken van formulieren te stroomlijnen.
