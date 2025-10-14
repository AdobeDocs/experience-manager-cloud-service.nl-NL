---
title: Fouten opsporen in HTML5-formulieren
description: In het document staan stappen voor het oplossen van verschillende bekende problemen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 5260d981-da40-40ab-834e-88e091840813
feature: HTML5 Forms,Mobile Forms
exl-id: 7330c03f-7102-43c0-aac6-825cce8a113d
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 22aeedaaf4171ad295199a989e659b6bf5ce9834
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 0%

---

# Fouten opsporen in HTML5-formulieren {#debugging-html-forms}

Dit document bevat verschillende scenario&#39;s voor probleemoplossing. Voor elk scenario, worden sommige stappen verstrekt om het probleem problemen op te lossen. Volg deze stappen en, als het probleem voortduurt, vorm Logger om logboeken voor fouten/waarschuwingen te krijgen en te herzien. Voor meer details over HTML5 vormen registreren, zie [&#x200B; het Produceren Logs voor HTML5 vormen &#x200B;](/help/forms/enable-logs.md).

## Probleem: bij het weergeven van het formulier zie ik de pagina met uitzonderingen org.apache.sling.api.SlingException {#problem-when-rendering-the-form-i-see-org-apache-sling-api-slingexception-exception-page}

In de uitzonderingsdetails, onderzoek naar woord **dat door** wordt veroorzaakt.

De waarschijnlijke reden is dat een of meer parameters in de URL onjuist zijn.

Controleer de volgende parameters:

<table>
 <tbody>
  <tr>
   <td><strong>Parameter</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>template</td>
   <td>De bestandsnaam van de sjabloon</td>
  </tr>
  <tr>
   <td>contentRoot</td>
   <td>Het pad waar de sjabloon en de bijbehorende bronnen zich bevinden</td>
  </tr>
  <tr>
   <td>dataRef</td>
   <td>Absoluut pad van het gegevensbestand dat met de sjabloon is samengevoegd.<br /> Opmerking: het pad definieert het absolute pad van het gegevensbestand.</td>
  </tr>
  <tr>
   <td>data</td>
   <td>UTF-8-gecodeerde gegevensbytes die met de sjabloon worden samengevoegd.</td>
  </tr>
 </tbody>
</table>

## Probleem: Kan een formulier niet genereren (er wordt een foutbericht weergegeven) {#problem-unable-to-render-form}

1. Controleer of de opgegeven parameters correct zijn. Voor gedetailleerde informatie over parameters, zie [&#x200B; Parameters &#x200B;](#problem-when-rendering-the-form-i-see-org-apache-sling-api-slingexception-exception-page) teruggeven.
1. Meld u aan bij CRX Package Manager (op https://&lt;server>:&lt;port>/crx/packmgr/index.jsp) en controleer of de volgende pakketten correct zijn geïnstalleerd:

   * adobe-lc-forms-content-pkg-&lt;version>.zip
   * adobe-lc-forms-runtime-pkg-&lt;version>.zip

1. Meld u aan bij de CQ-webconsole (Felix Console) op https://&lt;server>:&lt;port>/system/console/bundles.

   Zorg ervoor dat de status van de volgende bundels &quot;actief&quot; is:

   * scala-lang.bundle [ osgi ]

   (com.adobe.livecyclescala-lang.bundle)

   * Adobe XFA Forms Renderer

   (com.adobe.livecycle.adobe-lc-forms-core)

   * Adobe XFA Forms LC Connector

   (com.adobe.livecycle.adobe-lc-forms-lc-connector)

## Probleem: formulierweergaven zonder stijlen {#problem-form-renders-without-styles}

1. In uw browser, open **Hulpmiddelen van de Ontwikkelaar**. Controleer of profile.css beschikbaar is.
1. Als het bestand profile.css niet beschikbaar is, meldt u zich aan bij CRX DE op https://&lt;server>:&lt;port>/crx/de.
1. Navigeer in de mappenhiërarchie links naar /etc/clientlibs/fd/xfaforms/. Open css.txt- dossiers die in de omslagen worden vermeld.

   * profiel
   * runtime
   * scrollnav
   * werkbalk
   * xfalib

1. Controleer of de bestanden die in het bestand css.txt worden vermeld, aanwezig zijn in de CRX DE-lijst op /libs/fd/xfaforms/clientlibs/xfalib/css.

   ```css
   #base=css
   application.css
   dialog.css
   datepicker.css
   scribble.css
   listboxwidget.css
   ```

1. Als de vermelde bestanden niet beschikbaar zijn, installeert u het pakket adobe-lc-forms-runtime-pkg-&lt;version>.zip opnieuw.

### Probleem: onverwachte fout aangetroffen {#problem-unexpected-error-encountered}

1. Voeg in de formulier-URL een queryparameter debugClientLibs toe en stel de waarde ervan in op true (bijvoorbeeld: https://&lt;server>:&lt;port>/content/xfaforms/profiles/test.html?contentRoot=&lt;some path>&amp;template=&lt;name of xdp file>&amp;log=1-a9-b9-c9&amp;debugClientLibs=true)
1. Ga in de desktopbrowser, zoals chroom, naar Developer Tools > Console.
1. Open de logboeken om het type van fout te identificeren. Voor gedetailleerde informatie over logboeken, zie [&#x200B; logboeken voor vormen HTML5 &#x200B;](/help/forms/enable-logs.md).
1. Ga naar Developer Tools > Console. Gebruik stacktracering om de code te zoeken die de fout veroorzaakt. Foutopsporing de fout om het probleem op te lossen.

   >[!NOTE]
   >
   >Als het script is mislukt, controleert u of hetzelfde probleem optreedt tijdens de PDF-uitvoering van het formulier. Zo ja, dan is er een probleem in de logica van het formulierscript.

## Probleem: kan het formulier niet verzenden {#problem-unable-to-submit-the-form}

1. Zorg ervoor dat u toegangsrechten hebt tot de AEM-server en dat u verbinding hebt met de server.
1. Controleer of de parameter submitUrl correct is.
1. Laat de cliënt zijlogboeken zoals vermeld bij [&#x200B; Logboeken voor de vormen HTML5 &#x200B;](/help/forms/enable-logs.md) toe gebruikend zuiveren optie zoals **1-a5-b5-c5**. Geef het formulier vervolgens weer en klik op Verzenden. Open browser zuivert console en controleer als er een fout is.
1. Zoek de serverlogboeken zoals vermeld bij [&#x200B; Logboeken voor de vormen HTML5 &#x200B;](/help/forms/enable-logs.md). Controleer of er tijdens de verzending een fout is opgetreden in de serverlogboeken.

## Probleem: gelokaliseerde foutberichten worden niet weergegeven {#problem-localized-error-messages-do-not-display}

1. Render de vorm met extra vraagparameter **debugClientLibs=true** in Desktopbrowser, en ga dan naar de Hulpmiddelen van de Ontwikkelaar > Middelen en controleer het dossier I18N.css.
1. Als het bestand niet beschikbaar is, meldt u zich aan bij CRX DE op https://&lt;server>:&lt;port>/crx/de.
1. Navigeer in de mappenhiërarchie links naar /libs/fd/xfaforms/clientlibs/I18N en zorg ervoor dat de volgende bestanden en mappen bestaan:

   * Namespace.js
   * LogMessages.js
   * Mappen voor talen

1. Als om het even welke bovengenoemde dossiers of omslagen niet bestaan, installeer opnieuw **adobe-lc-forms-runtime-pkg-&lt;version>.zip** pakket.
1. Navigeer naar de map met dezelfde naam als de naam van de landinstelling en controleer de inhoud ervan. De map moet de volgende bestanden bevatten:

   * I18N.js
   * js.txt

1. Controleer de inhoud van js.txt en zorg ervoor dat het de volgende ingangen heeft.

   ```javascript
   ../Namespace.js
   I18N.js
   ../LogMessages.js
   ```

## Probleem: afbeelding wordt niet weergegeven {#problem-image-not-showing-up}

1. Controleer of de URL van de afbeelding juist is.
1. Controleer of uw browser dit type afbeelding ondersteunt.
1. In de uitzonderingsdetails, onderzoek naar woord **dat door** wordt veroorzaakt.

   De waarschijnlijke reden is dat een of meer parameters in de URL onjuist zijn.

   Controleer de volgende parameters:
Staptekst

<table>
 <tbody>
  <tr>
   <td><strong>Parameter</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>template</td>
   <td>De bestandsnaam van de sjabloon</td>
  </tr>
  <tr>
   <td>contentRoot</td>
   <td>Het pad waar de sjabloon en de bijbehorende bronnen zich bevinden</td>
  </tr>
  <tr>
   <td>dataRef</td>
   <td>Absoluut pad van het gegevensbestand dat met de sjabloon is samengevoegd.<br /> Opmerking: het pad definieert het absolute pad van het gegevensbestand.</td>
  </tr>
  <tr>
   <td>data</td>
   <td>UTF-8-gecodeerde gegevensbytes die met de sjabloon worden samengevoegd.</td>
  </tr>
 </tbody>
</table>

1. Ga in de desktopbrowser naar Developer Tools > Resources.

   Schakel de linkerzijde in Frames in als die afbeelding wordt weergegeven.
