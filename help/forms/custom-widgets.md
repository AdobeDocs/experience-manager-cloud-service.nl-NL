---
title: Aangepaste weergaven maken in HTML5-formulieren
description: U kunt aangepaste widgets aansluiten op een mobiele Forms. U kunt bestaande jQuery-widgets uitbreiden of uw eigen aangepaste widgets ontwikkelen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: HTML5 Forms,Mobile Forms
exl-id: 76bd1e2d-9e65-452c-8cef-123d28886a62
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 22aeedaaf4171ad295199a989e659b6bf5ce9834
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 0%

---

# Aangepaste weergaven maken in HTML5-formulieren{#create-custom-appearances-in-html-forms}

<span class="preview"> De HTML5 Forms-functionaliteit wordt aangeboden als onderdeel van het programma voor vroege toegang. Als u toegang wilt aanvragen, stuurt u een e-mail van uw officiële (werk)e-mailadres naar aem-forms-ea@adobe.com.
</span>

U kunt aangepaste widgets aansluiten op een mobiele Forms. U kunt bestaande jQuery-widgets uitbreiden of uw eigen aangepaste widgets ontwikkelen met het raamwerk voor weergaven. De motor XFA gebruikt diverse widgets, zie [ Kader van de Verschijning voor aanpassings en vormen HTML5 ](/help/forms/custom-widgets.md) voor gedetailleerde informatie.

![ Een voorbeeld van gebrek en douane widget ](assets/custom-widgets.jpg)

Een voorbeeld van de standaard- en aangepaste widget

## Aangepaste widgets integreren met HTML5-formulieren {#integrating-custom-widgets-with-html-forms}

### Een profiel maken  {#create-a-profile-nbsp}

U kunt een profiel maken of een bestaand profiel kiezen om een aangepaste widget toe te voegen. Voor meer informatie bij het creëren van profielen, zie [ Creërend douaneProfiel ](/help/forms/custom-profile.md).

### Een widget maken {#create-a-widget}

HTML5-formulieren bieden een implementatie van het widgetframework dat kan worden uitgebreid om nieuwe widgets te maken. De implementatie is een widget jQuery *abstractWidget* die kan worden uitgebreid om een nieuwe widget te schrijven. De nieuwe widget kan alleen functioneel worden gemaakt door de hieronder vermelde functies uit te breiden of te overschrijven.

<table>
 <tbody>
  <tr>
   <td>Functie/klasse</td>
   <td>Beschrijving</td>
  </tr>
  <tr>
   <td>renderen</td>
   <td>De renderfunctie retourneert het jQuery-object voor het standaard HTML-element van de widget. Het standaard HTML-element moet van het brandpunttype zijn. Bijvoorbeeld &lt;a&gt;, &lt;input&gt; en &lt;li&gt;. Het geretourneerde element wordt gebruikt als $userControl. Als $userControl de bovengenoemde beperking specificeert, dan werken de functies van de klasse AbstractWidget zoals verwacht, anders vereisen sommige gemeenschappelijke APIs (nadruk, klik) veranderingen. </td>
  </tr>
  <tr>
   <td>getEventMap</td>
   <td>Retourneert een kaart om HTML-gebeurtenissen om te zetten in XFA-gebeurtenissen. <br /> <br /> vervagen: XFA_EXIT_EVENT, <br /> <br /> Dit voorbeeld toont aan dat de vervaging een HTML-gebeurtenis is en dat XFA_EXIT_EVENT overeenkomt met XFA-gebeurtenis. </td>
  </tr>
  <tr>
   <td>getOptionsMap</td>
   <td>Retourneert een kaart die gedetailleerde informatie bevat over de handeling die moet worden uitgevoerd bij wijziging van een optie. De sleutels zijn de opties die aan widget worden verstrekt en de waarden zijn de functies die worden geroepen wanneer een verandering in die optie wordt ontdekt. De widget biedt handlers voor alle algemene opties (behalve value en displayValue)</td>
  </tr>
  <tr>
   <td>getCommitValue</td>
   <td>Het widgetframework laadt de functie wanneer de waarde van de widget wordt opgeslagen in het XFAModel (bijvoorbeeld bij afsluitgebeurtenis van een textField). De implementatie moet de waarde retourneren die is opgeslagen in de widget. De handler krijgt de nieuwe waarde voor de optie.</td>
  </tr>
  <tr>
   <td>showValue</td>
   <td>Standaard wordt in XFA bij Enter de rawValue van het veld weergegeven. Deze functie wordt aangeroepen om de rawValue aan de gebruiker te tonen. </td>
  </tr>
  <tr>
   <td>showDisplayValue</td>
   <td>Standaard wordt in XFA bij afsluitgebeurtenis de formattedValue van het veld weergegeven. Deze functie wordt geroepen om formattedValue aan de gebruiker te tonen. </td>
  </tr>
 </tbody>
</table>

Als u uw eigen widget wilt maken, neemt u in het profiel dat hierboven is gemaakt verwijzingen op naar het JavaScript-bestand dat overschreven functies en toegevoegde functies bevat. Bijvoorbeeld, is *sliderNumericFieldWidget* een widget voor numerieke Gebieden. Als u de widget in uw profiel in de koptekstsectie wilt gebruiken, neemt u de volgende regel op:

```javascript
window.formBridge.registerConfig("widgetConfig" , widgetConfigObject);
```

### Aangepaste widget registreren met XFA Scripting Engine  {#register-custom-widget-with-xfa-scripting-engine-nbsp}

Wanneer de code van de douanewidget klaar is, registreer widget met de scripting motor door `registerConfig` API voor [ Vorm Bridge ](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/forms/developer-reference/form-bridge-apis) te gebruiken. Het neemt widgetConfigObject als input.

```javascript
window.formBridge.registerConfig("widgetConfig",
        {
        ".<field-identifier>":"<name-of-the-widget>"
        }
    );
```

#### widgetConfigObject {#widgetconfigobject}

De widgetconfiguratie wordt aangeboden als een JSON-object (een verzameling sleutelwaardeparen), waarbij de sleutel de velden identificeert en de waarde de widget vertegenwoordigt die met deze velden moet worden gebruikt. Een voorbeeldconfiguratie ziet er als volgt uit:

```
*{*

*"identifier1" : "customwidgetname",
"identifier2" : "customwidgetname2",
..
}*
```

waarbij &quot;id&quot; een jQuery CSS-kiezer is die een bepaald veld, een set velden van een bepaald type of alle velden vertegenwoordigt. In het volgende voorbeeld wordt de waarde van de id in verschillende gevallen weergegeven:

| Type id | Id | Beschrijving |
|---|---|---|
| Specifiek veld met naam van veld | Id:&quot;div.fieldName&quot; | Alle velden met de naam &#39;veldnaam&#39; worden weergegeven met de widget. |
| Alle velden van het type ‘type’ (waarbij het type NumericField, DateField enzovoort is).: | Id: &quot;div.type&quot; | Voor Tijdveld en DateTimeField is het type tekstveld omdat deze velden niet worden ondersteund. |
| Alle velden | Id: &quot;div.field&quot; |  |
