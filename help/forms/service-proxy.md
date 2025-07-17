---
title: HTML5-proxy voor formulierservice
description: HTML5 Forms Service Proxy is een configuratie om een proxy voor de verzendservice te registreren. Om de Volmacht van de Dienst te vormen, specificeer URL van de voorleggingsdienst door request parameter submissionServiceProxy.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: HTML5 Forms,Mobile Forms
exl-id: 8f9b10ae-1600-49c2-a061-153a2a89c67e
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 22aeedaaf4171ad295199a989e659b6bf5ce9834
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# HTML5-proxy voor formulierservice{#html-forms-service-proxy}

<span class="preview"> De HTML5 Forms-functionaliteit wordt aangeboden als onderdeel van het programma voor vroege toegang. Als u toegang wilt aanvragen, stuurt u een e-mail van uw officiële (werk)e-mailadres naar aem-forms-ea@adobe.com.
</span>

HTML5 Forms Service Proxy is een configuratie om een proxy voor de verzendservice te registreren. Om de Volmacht van de Dienst te vormen, specificeer URL van de voorleggingsdienst door verzoekparameter *submissionServiceProxy*.

## Voordelen van de Volmacht van de Dienst {#benefits-of-service-proxy-br}

De serviceproxy verwijdert het volgende:

* Voor de workflow voor HTML5-formulieren moet de verzendservice &quot;/content/xfaforms/submission/default&quot; worden geopend voor gebruikers van HTML5-formulieren. AEM-servers worden blootgesteld aan een groter onbedoeld publiek.
* De service-URL is ingesloten in het runtimemodel van het formulier. Het is niet mogelijk om dienstURL weg te veranderen.
* De verzending bestaat uit twee stappen. Voor het verzenden van de formuliergegevens zijn ten minste twee ritten naar de server vereist. Hierdoor wordt de belasting op de server verhoogd.
* HTML5-formulieren verzenden gegevens in de POST-aanvraag in plaats van in de PDF-aanvraag. Voor workflows met zowel PDF- als HTML5-formulieren zijn twee verschillende verwerkingsmethoden voor de verzending vereist.

### Topologieën {#topologies-br}

HTML5-formulieren kunnen de volgende topologieën gebruiken om verbinding te maken met de AEM-servers.

* Een topologie waarbij AEM Server- of HTML5-formulieren gegevens via POST naar de server verzenden.
* Een topologie waar de volmachtsserver POST gegevens naar de server verzendt.

![ HTML5 de topologieën van de de dienstvolmacht van vormen ](assets/topology.png)

HTML5 de volmachtstopologieën van de vormendienst

HTML5-formulieren maken verbinding met de AEM-servers om serverscripts, webservices en verzendingen uit te voeren. De XFA-runtime van de HTML5-formulieren gebruikt Ajax-aanroepen van het eindpunt &quot;/bin/xfaforms/submit&quot; met verschillende parameters om verbinding te maken met de AEM-servers. HTML5-formulieren verbinden AEM-servers om de volgende bewerkingen uit te voeren:

#### Voer Server-zijdig manuscripten en de Diensten van het Web uit {#execute-server-sided-scripts-and-web-services}

De scripts die zijn gemarkeerd om op de server te worden uitgevoerd, worden serverscripts genoemd. De volgende lijst maakt een lijst van alle parameters die in Server-zijde manuscripten en de Diensten van het Web worden gebruikt.

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p>activiteit</p> </td>
   <td><p>De activiteit bevat de gebeurtenissen die het verzoek teweegbrengen. Bijvoorbeeld klikken, afsluiten of wijzigen</p> </td>
  </tr>
  <tr>
   <td><p>contextSom</p> </td>
   <td><p>contextSom bevat SOM-expressie van het object waar gebeurtenissen worden uitgevoerd.</p> </td>
  </tr>
  <tr>
   <td><p>Sjabloon</p> </td>
   <td><p>De sjabloon bevat de sjabloon die wordt gebruikt om het formulier te genereren.</p> </td>
  </tr>
  <tr>
   <td><p>contentRoot</p> </td>
   <td><p>contentRoot bevat de hoofdmap van de sjabloon die wordt gebruikt om het formulier weer te geven.</p> </td>
  </tr>
  <tr>
   <td><p>Gegevens</p> </td>
   <td><p>Gegevens bevatten batchbytes die worden gebruikt om het formulier te genereren.</p> </td>
  </tr>
  <tr>
   <td><p>formDom</p> </td>
   <td><p>formDom bevat DOM van het HTML5-formulier in JSON-indeling.</p> </td>
  </tr>
  <tr>
   <td><p>packet</p> </td>
   <td><p>Het pakket wordt als formulier opgegeven.</p> </td>
  </tr>
  <tr>
   <td><p>debugDir</p> </td>
   <td><p>debugDir bevat de map voor foutopsporing die wordt gebruikt om het formulier te genereren.</p> </td>
  </tr>
 </tbody>
</table>

#### Gegevens verzenden {#submit-data}

Als HTML5-formulieren op Verzenden klikken, worden gegevens naar de server verzonden. De volgende tabel bevat een lijst met alle parameters die HTML5-formulieren naar de server verzenden.

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p>Sjabloon</p> </td>
   <td><p>Sjabloon waarmee het formulier wordt gegenereerd.</p> </td>
  </tr>
  <tr>
   <td><p>contentRoot</p> </td>
   <td><p>de hoofdmap van de sjabloon die wordt gebruikt om het formulier te genereren.</p> </td>
  </tr>
  <tr>
   <td><p>Gegevens</p> </td>
   <td><p>batchbytes die worden gebruikt om het formulier weer te geven.</p> </td>
  </tr>
  <tr>
   <td><p>formDom</p> </td>
   <td><p>DOM van het HTML5-formulier in JSON-indeling.</p> </td>
  </tr>
  <tr>
   <td><p>voorlegger</p> </td>
   <td><p>De URL waar de gegevens-XML wordt gepost.</p> </td>
  </tr>
  <tr>
   <td><p>debugDir</p> </td>
   <td><p>De map voor foutopsporing die wordt gebruikt om het formulier te genereren.</p> </td>
  </tr>
 </tbody>
</table>

#### Hoe werkt de verzendproxy? {#how-nbsp-the-nbsp-submit-proxy-works}

De verzendserviceproxy fungeert als een pass through als de verzender niet aanwezig is in de parameter request. Het fungeert als een doorbraak. Het verzendt het verzoek naar het /bin/xfaforms/submitAction eindpunt en verzendt de reactie naar runtime XFA.

De voorgelegde de dienstvolmacht selecteert een topologie als voorlegger in de verzoekparameter aanwezig is.

* Als AEM-servers de gegevens posten, fungeert de proxyservice als een pass-through. Het verzendt het verzoek naar het /bin/xfaforms/submitAction eindpunt en verzendt de reactie naar runtime XFA.
* Als de volmacht de gegevens post, gaat de volmachtsdienst alle parameters behalve submitUrl tot het */bin/xfaforms/submitAction* eindpunt over en ontvangt xml bytes in reactiestream. Dan, post de volmachtsdienst de gegevens xml bytes aan submitUrl voor verwerking.

* Voordat gegevens (POST-aanvraag) naar een server worden verzonden, controleren HTML5-formulieren de connectiviteit en beschikbaarheid van de server. HTML-formulieren verzenden een leeg verzoek naar de server om de connectiviteit en beschikbaarheid te controleren. Als de server beschikbaar is, verzendt het HTML5-formulier gegevens (POST-aanvraag) naar de server. Als de server niet beschikbaar is, een foutenmelding, *Kon niet met de server verbinden,* wordt getoond. De detectie vooraf voorkomt dat gebruikers het formulier kunnen bijvullen. De volmachtsservlet behandelt hoofdverzoek en werpen geen uitzondering.
