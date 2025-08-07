---
title: Hoe kan ik formulieren ontwerpen in AEM?
description: Leer meer over de verschillende formulierontwerpplatforms die beschikbaar zijn in Adobe Experience Manager (AEM) en hoe u de juiste kunt kiezen op basis van uw vereisten.
feature: Edge Delivery Services, Adaptive Forms, Core Components
role: User, Developer
exl-id: bd9cb623-c272-4cdf-ad39-f97043f781a6
hide: true
hidefromToC: true
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '1075'
ht-degree: 0%

---

# Hoe moet Forms in Adobe Experience Manager (AEM) worden geautoriseerd?

Adobe Experience Manager (AEM) biedt een flexibel platform voor het maken van aantrekkelijke, responsieve, dynamische en adaptieve formulieren. Het biedt een intuïtieve gebruikersinterface en een rijke reeks out-of-the-box componenten voor de bouw van en het beheer van Aangepast Forms. Forms kan naar wens worden ontworpen met of zonder een formuliermodel of -schema.

## Belangrijke overwegingen bij het kiezen van een ontwerpplatform

AEM biedt meerdere opties voor het schrijven van formulieren om interactieve en aantrekkelijke formulieren te maken. Houd bij het selecteren van een formulierontwerpomgeving rekening met de volgende factoren:

| 📝 **Overweging** | 💡 **wat te vragen** |
|----------------------|--------------------|
| **Expertise van de Gebruiker** | Wie gaat de formulieren ontwerpen, ontwikkelaars, zakelijke gebruikers of auteurs van inhoud? |
| **Complexiteit van de Vorm** | Heeft het formulier geavanceerde regels, dynamische secties of integraties nodig? |
| **Herbruikbaarheidsbehoeften** | Worden delen van het formulier opnieuw gebruikt in verschillende formulieren of projecten? |
| **Flexibiliteit van het Ontwerp** | Hebt u volledige controle nodig over lay-out, thema&#39;s en stijlen? |
| **Vereisten van de Integratie** | Moet het formulier verbinding maken met gegevensmodellen, workflows of externe systemen? |
| **Versnelling van Gebruik** | Is het platform intuïtief voor het technische vaardigheidsniveau van uw team? |
| **Prestaties &amp; Scalability** | Zal het formulier op schaal of in een omgeving met veel verkeer worden gebruikt? |
| **Omnichannel Levering** | Wordt het formulier gebruikt op websites, mobiele apps, kiosken of meerdere kanalen? |
| **het Publiceren Flexibiliteit** | Waar worden de formulieren gepubliceerd op AEM, Edge Delivery of aangepaste apps? |

## Overzicht van formulierontwerpmethoden in AEM

AEM steunt veelvoudige auteursmethodes, elk geschikt voor verschillende gebruikersbehoeften, technische vaardigheidsniveaus, en het publiceren bestemmingen.

- [ Componenten van de Stichting ](/help/forms/create-adaptive-form-tutorial.md): De Componenten van de Stichting van het gebruik om traditionele, interactieve vormen te bouwen. Deze indeling is het meest geschikt voor formulieren die integreren met verouderde systemen of die vertrouwen op langdurige workflows. Forms die is ontworpen met Foundation Components, kan alleen op AEM worden gepubliceerd en is niet compatibel met Edge Delivery Services.

- [ Componenten van de Kern ](/help/forms/creating-adaptive-form-core-components.md): De Componenten van de Kern van het gebruik om moderne, ontvankelijke, en scalable vormen tot stand te brengen. Ze ondersteunen herbruikbaarheid, toegankelijkheid en betere prestaties. Forms die is ontworpen met Core Components, kan zowel op AEM als op Edge Delivery Services worden gepubliceerd en biedt flexibiliteit op verschillende platforms.

- [ Edge Delivery Services Forms ](/help/edge/docs/forms/overview.md): Edge Delivery Services Forms transformeert de manier de vormen worden authored, uitgevoerd, en verwerkt. Door gebruik te maken van Edge Delivery Services kunnen organisaties snelle, veilige en hoogst beschikbare digitale formulieren maken, waardoor de gebruikerservaring en de operationele efficiëntie worden verbeterd in een snelle ontwikkelomgeving. U kunt de Edge Delivery Services Forms op twee manieren ontwerpen:
   - [ het Authoring van WYSIWYG ](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md): Gebruik de Universele Redacteur voor visuele, belemmering-en-dalings vormverwezenlijking ideaal voor inhoudsauteurs met beperkte technische kennis. Forms die is geschreven met Universal Editor, wordt geleverd met Edge Delivery Services voor snelle, lichtgewichtrendering.
   - [ op document-Gebaseerde Authoring ](/help/edge/docs/forms/tutorial.md): De hulpmiddelen van het gebruik zoals de Bladen van Microsoft Excel of van Google om vormstructuur en inhoud te bepalen. Deze methode is handig voor zakelijke gebruikers die de voorkeur geven aan spreadsheetinvoer. Deze formulieren worden doorgaans via Edge Delivery Services gepubliceerd en zijn geschikt voor eenvoudige, grote gebruiksgevallen.
- [ Koploze Authoring ](https://experienceleague.adobe.com/en/docs/experience-manager-headless-adaptive-forms/using/tutorial/build-engaging-forms-using-core-components-and-headless-adaptive-forms-aem-forms-cloud-service): Gebruik APIs om formulieren als JSON voor om het even welk front, bijvoorbeeld, React, Angular, mobiele apps, of kiosken, zonder afhankelijk van AEM terug te geven. Momenteel ondersteunen alleen Core Components de levering zonder kop. Zwaarloze formulieren zijn ideaal voor omnichannel gebruiksgevallen en worden gebruikt onafhankelijk van de AEM-rendering van pagina&#39;s, waardoor ze flexibel zijn voor aangepaste front-end implementaties.

### Vergelijkende analyse van AEM-methoden voor formulierontwerp

&#x200B; In de volgende tabel vindt u een beknopte vergelijking van de verschillende methoden voor het schrijven van AEM-formulieren, waarbij de nadruk wordt gelegd op de benaderingen, functies, publicatieopties en ideale gebruikstoepassingen om u te helpen de meest geschikte methode te kiezen die u nodig hebt.

| **Overweging** | **Componenten van de Stichting** | **Componenten van de Kern** | **Universele Redacteur (WYSIWYG)** | **op document-gebaseerde Authoring** | **Headless Authoring** |
|--------------------------|---------------------------------------------------------------------|------------------------------------------------------------------------|-------------------------------------------------------------------------|---------------------------------------------------------------------------|-------------------------------------------------------------------------|
| **ideaal voor** | Oudere formulieren en workflows onderhouden in AEM | Schaalbare, moderne formulieren met complexe workflows en integratie | Formulieren maken voor Edge Delivery Service-sites met complexe vereisten | Snel prototypen maken of basisformulieren zonder geavanceerde verzendservices | Omnichannel-ervaringen op verschillende platforms (web, mobiel, kiosken, enz.) |
| **Expertise van de Gebruiker** | Ontwikkelaars, makers van inhoud | Ontwikkelaars, gevorderde auteurs | Zakelijke gebruikers, makers van inhoud | Zakelijke gebruikers | Ontwikkelaars |
| **Complexiteit van de Vorm** | Basisformulieren | Complexe formulieren met dynamische secties | Complexe formulieren met aangepaste handelingen | Eenvoudige formulieren | Zeer complexe, API-gestuurde formulieren |
| **Flexibiliteit van het Ontwerp** | Beperkt | Hoog (CSS/JS-aanpassing) | Modern (op basis van sjablonen) | Beperkt | High (frontend framework control) |
| **de Mogelijkheid van de Integratie** | Basic AEM-workflows | Geavanceerd (gegevensmodellen, workflows) | Geïntegreerd met externe systemen | Standaard (Google Sheets, Excel) | Volledige besturing via API&#39;s |
| **het Publiceren Methode** | Alleen AEM | AEM en Edge Delivery Services | Edge Delivery Services | Edge Delivery Services | Elke frontend via API&#39;s |
| **Prestaties &amp; SEO** | Standaard | Verbeterd voor Foundation Components | Hoge Google Lighthouders scores voor snellere rendering en betere SEO | Hoge Google Lighthouders scores voor snellere rendering en betere SEO | Afhankelijk van implementatie |
| **Omnichannel Levering** | Beperkt | Gemiddeld | Gemiddeld | Beperkt | Hoog |

<!--
| **Form authoring methods** | **Key Approach** | **Features** | **Publishing Method** | **Use Cases** |
|-----------------------------|------------------|--------------|-----------------------|---------------|
| **Foundation Components** | Classic AEM authoring interface designed for standard web pages. | Includes basic components like text, images, tables, and charts. Limited reuse capabilities and primarily web-based. | Published on AEM only. | Best for maintaining legacy forms and workflows within AEM. |
| **Core Components** | Provides a modern, flexible approach with high customization capabilities. | Component-based authoring within AEM, offering high customization with CSS and JS. Built around accessibility guidelines and integrated with AEM Sites. | Published on AEM and Edge Delivery Services. | Suitable for scalable, modern forms with complex workflows and integrations. |
| **Universal Editor (WYSIWYG)** | Offers a WYSIWYG interface for intuitive form creation. | Forms are designed using an intuitive drag-and-drop interface. These forms inherit look and feel from the configured Edge Delivery Services GitHub repository for the corresponding form. | Published on Edge Delivery Services, achieving high Google Lighthouse scores for faster rendering and better SEO. | Ideal for creating forms for Edge Delivery Service sites and pages, especially scenarios involving complex forms, workflows, custom actions, or integrations with external systems. |
| **Document-based Authoring** | Uses familiar tools like Google Docs and Microsoft Office for form creation. | Forms are designed using spreadsheets, with data directly submitted to Google Sheets or Microsoft Excel. These forms are faster to create and deploy. No prior knowledge of AEM is required to develop custom components and styles for these forms. | Published on Edge Delivery Services, achieving high Google Lighthouse scores for faster rendering and better SEO. | Ideal for quick prototyping or basic forms where advanced submission services are not needed. Well-suited for surveys, registration, or feedback forms requiring data storage in spreadsheets. |
| **Headless Authoring** | Enables API-driven content creation for omnichannel delivery. | Full control via frontend frameworks, allowing content delivery across various platforms through APIs. | Can be integrated with any frontend via APIs. | Ideal for omnichannel experiences across platforms, suitable for web, mobile, kiosks, and more. |-->

### Functievergelijking van ontwerpmethoden voor AEM-formulieren

In de volgende tabel vindt u een gedetailleerde vergelijking van de belangrijkste functies van de verschillende AEM-methoden voor het schrijven van formulieren. Zo kunt u de meest geschikte aanpak voor uw vereisten kiezen. &#x200B;

| **Capability** | **Componenten van de Stichting** | **Componenten van de Kern** | **Universele Redacteur (WYSIWYG)** | **op document-gebaseerde Authoring** | **Headless Authoring** |
|-----------------------------------------|---------------------------|---------------------|-------------------------------|-----------------------------|------------------------|
| **Verenigde Samenstelling met Plaatsen** | ❌ | ✅ | ✅ | ❌ | ❌ |
| **Inbedend de Steun van de Vorm** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Regels (Dynamisch Gedrag)** | Geavanceerde regeleditor met aangepaste functies | Geavanceerde regeleditor met aangepaste functies | Geavanceerde regeleditor met aangepaste functies | Beperkt: tonen/verbergen, waarde berekenen, aangepaste functies | Beperkt: vereist aangepaste implementatie |
| **Steun van de Bijlage** | ✅ | ✅ | ✅ | ℹ️ (Vroege toegang) | ❌ |
| **steun CAPTCHA** | reCAPTCHA v2/Enterprise, hCaptcha (EA), Turnstile (EA) | reCAPTCHA v2/Enterprise, hCaptcha (EA) | reCAPTCHA Enterprise | reCAPTCHA Enterprise | Vereist aangepaste integratie |
| **Eigenschappen van de Verzending** | REST-eindpunt, e-mail, Form Data Model (FDM), Invoke AEM Workflow, SharePoint, OneDrive, Azure Blob Storage, Power Automate, Workfront Fusion (EA) | REST-eindpunt, e-mail, Form Data Model (FDM), Invoke AEM Workflow, SharePoint, OneDrive, Azure Blob Storage, Power Automate, Workfront Fusion (EA) | REST-eindpunt, e-mail, Form Data Model (FDM), Invoke AEM Workflow, SharePoint, OneDrive, Azure Blob Storage, Power Automate, Workfront Fusion (EA) | Alleen werkblad | Aangepaste API-eindpunten |
| **Schema van Gegevens** | FDM, aangepast | FDM, aangepast | FDM, aangepast | Aangepast | Aangepast |
| **pre-fill** | ✅ | ✅ | 💡 (via wizard) | ✅ | Aangepaste implementatie |
| **Fragments** | ✅ | ✅ | ✅ | ✅ | ❌ |
| **Visuele Redacteur van de Regel** | ✅ | ✅ | ✅ | ❌ | ❌ |
| **Localization** | ✅ | ✅ | 💡 (via sites) | ℹ️ (Excel - handleiding, functie Google Sheets) | Aangepaste implementatie |
| **Schema van Gegevens (de Boom van Gegevens)** | ✅ | ✅ | 💡 (via UI-extensie) | ❌ | Aangepaste implementatie |
| **de Steun van het Malplaatje** | ✅ | ✅ | Alleen oorspronkelijke inhoud, geen beleid | ❌ | Aangepaste implementatie |
| **Portaal** | ✅ | ✅ | ❌ | ❌ | ❌ |
| **Authoring DoR** | ✅ | ✅ | 💡 (via Derline) | ❌ | ❌ |
| **Productie DoR** | ✅ | ✅ | 💡 (FORMS-2475 Nieuw) | ❌ | ❌ |
| **Thema** | ✅ | ✅ | ℹ️ (op projectniveau) | ℹ️ (op projectniveau) | Aangepaste implementatie |
| **Component van de Douane** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **OOTB &amp; de Functies van de Douane** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Verwijzing van het Fragment** | ✅ | ❌ | ❌ | ❌ | ❌ |
| **Integratie van het Teken** | ✅ | ❌ | ❌ | ❌ | ❌ |
| **Steun RTL** | ❌ | ✅ | 💡 | 💡 | Aangepaste implementatie |
| **Experimentatie** | ❌ | ❌ | ✅ | ✅ | Aangepaste implementatie |
| **Het Beheer van de Taak via Workfront** | ❌ | ❌ | ✅ | ❌ | ❌ |
| **Uitbreiding van Personalization** | ❌ | ❌ | 💡 | ❌ | Aangepaste implementatie |
| **de Aanpassing van de Redacteur** | ❌ | ❌ | ✅ (via UI-extensie) | ❌ | Aangepaste implementatie |
| **legt Actie** voor | ✅ | ✅ | ✅ | Alleen werkblad | Aangepaste implementatie |


## Verwant artikel

- [Op documenten gebaseerde authoring met Microsoft Excel of Google Sheets](/help/edge/docs/forms/create-forms.md)
- [ Universele Redacteur voor het auteursrecht van WYSIWYG ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring)
- [Een adaptief formulier maken (basiscomponenten)](/help/forms/creating-adaptive-form.md)
- [Een adaptief formulier maken (kerncomponenten)](/help/forms/create-an-adaptive-form.md)
