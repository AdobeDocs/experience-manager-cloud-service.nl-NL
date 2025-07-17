---
title: Formuliersjabloon weergeven voor HTML5-formulieren
description: HTML5-formulierprofielen zijn gekoppeld aan profielrenderingen. Profielrendering zijn JSP-pagina's die verantwoordelijk zijn voor het genereren van HTML-representatie van het formulier door de Forms OSGi-service aan te roepen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: cb75b826-d044-44be-b364-790c046513e0
feature: HTML5 Forms,Mobile Forms
exl-id: 022b9953-2d64-473f-87b7-aac1602f6a7e
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 22aeedaaf4171ad295199a989e659b6bf5ce9834
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# Formuliersjabloon weergeven voor HTML5-formulieren {#rendering-form-template-for-html-forms}

<span class="preview"> De HTML5 Forms-functionaliteit wordt aangeboden als onderdeel van het programma voor vroege toegang. Als u toegang wilt aanvragen, stuurt u een e-mail van uw officiële (werk)e-mailadres naar aem-forms-ea@adobe.com.
</span>

## Eindpunt renderen {#render-endpoint}

HTML5 de vormen hebben het begrip van **Profielen** die als Eindpunten van REST worden blootgesteld om Mobiele Rendering van de Malplaatjes van de Vorm toe te laten. Deze Profielen hebben **Renderer van het Profiel** geassocieerd. Ze zijn JSP-pagina&#39;s die verantwoordelijk zijn voor het genereren van HTML-representatie van het formulier door de Forms OSGi-service aan te roepen. Het JCR-pad van het knooppunt Profile bepaalt de URL van het eindpunt van de renderbewerking. Het standaardrendereindpunt van het formulier dat verwijst naar het standaardprofiel ziet er als volgt uit:

https://&lt;*gastheer*>:&lt; *haven*>/content/xfaforms/profiles/default.html?contentRoot=&lt; *weg van de omslag die vorm xdp* bevat>&amp;template=&lt; *naam van xdp*>

Bijvoorbeeld: `http://localhost:4502/content/xfaforms/profiles/default.html?contentRoot=c:/xdps&template=sampleForm.xdp`

Voor een douaneprofiel, verandert het eindpunt dienovereenkomstig. Het eindpunt voor het aangepaste profiel met de naam Transform is bijvoorbeeld:

`http://localhost:4502/content/xfaforms/profiles/hrforms.html?contentRoot=c:/xdps&template=sampleForm.xdp`

Als uw sjabloon zich in de AEM-opslagplaats bevindt in een toepassing met de naam FormSubmission, is de URI:

```http
http://localhost:4502/content/xfaforms/profiles/default.html?
 contentRoot=crx:///content/dam/formsanddocuments/FormSubmission/1.0
 &template=sampleForm.xdp
```

## Renderparameters {#render-parameters}

De volgende aanvraagparameters worden ondersteund bij het weergeven van het formulier als HTML:

<table>
 <tbody>
  <tr>
   <th><strong>Parameter </strong></th>
   <th><strong>Beschrijving</strong></th>
  </tr>
  <tr>
   <td>template <br /> </td>
   <td>Deze parameter specificeert de naam van het malplaatjedossier.<br /> </td>
  </tr>
  <tr>
   <td>contentRoot <br /> </td>
   <td>Deze parameter specificeert de weg waar het malplaatje en de bijbehorende middelen verblijven. Dit pad kan het systeempad van het serverbestand, een repository pad of http of een ftp pad zijn.<br /> </td>
  </tr>
  <tr>
   <td>submitUrl <br /> </td>
   <td>Deze parameter specificeert url waaraan de xml van vormgegevens wordt gepost.<br /> </td>
  </tr>
 </tbody>
</table>

### Gegevens samenvoegen met formuliersjabloon {#merge-data-with-form-template}

| Parameter | Beschrijving |
|---|---|
| dataRef | Deze parameter specificeert **absolute weg** van het gegevensdossier dat met het malplaatje wordt samengevoegd. Deze parameter kan een URL zijn naar een andere service die de gegevens retourneert in XML-indeling. |
| data | Deze parameter geeft de UTF-8-gecodeerde gegevensbytes aan die met de sjabloon worden samengevoegd. Als deze parameter wordt opgegeven, negeert het HTML5-formulier de parameter dataRef. |

### De renderparameter doorgeven {#passing-the-render-parameter}

HTML5-formulieren ondersteunen drie methoden voor het doorgeven van de renderparameters. U kunt parameters doorgeven via URL&#39;s, sleutel-waardeparen en profielknooppunten. In de renderparameter heeft sleutelwaardepaar de hoogste prioriteit gevolgd door het profielknooppunt. De URL-verzoekparameter heeft de minste prioriteit.

* **URL verzoekparameters**: U kunt teruggeven parameters in URL specificeren. In de URL-aanvraagparameters zijn de parameters zichtbaar voor de eindgebruiker. De volgende verzendings-URL bevat bijvoorbeeld een sjabloonparameter in de URL: `http://localhost:4502/content/xfaforms/profiles/default.html?contentRoot=/Applications/FormSubmission/1.0&template=sampleForm.xdp`

* **SetAttribute verzoekparameters**: U kunt teruggeven parameters als zeer belangrijk-waardepaar specificeren. In de SetAttribute- verzoekparameters, zijn de parameters niet zichtbaar aan het eind - gebruiker. U kunt een verzoek van om het even welk ander JSP aan HTML5 renderer JSP van het vormprofiel door:sturen en *gebruiken setAttribute* op verzoekvoorwerp om alle teruggeeft parameters over te gaan. Deze methode heeft de hoogste prioriteit.

* **de knoopverzoekparameters van het Profiel:** u kunt teruggeven parameters als knoopeigenschappen van een profielknoop specificeren. In de parameters van het profielknooppuntverzoek, zijn de parameters niet zichtbaar aan het eind - gebruiker. Profielknooppunt is het knooppunt waarnaar de aanvraag wordt verzonden. Gebruik de CRXDE-lijst om parameters op te geven als knoopeigenschappen.

### Parameters verzenden {#submit-parameters}

HTML5-formulieren verzenden gegevens, serverscripts en webservices op AEM-servers uitvoeren. Voor gedetailleerde informatie over parameters die worden gebruikt om server-zijde manuscripten en Web-diensten op de servers van AEM uit te voeren, zie {de Volmacht van de Dienst van 0} HTML5 vormen [.](/help/forms/service-proxy.md)
