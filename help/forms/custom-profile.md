---
title: Een aangepast profiel maken voor HTML5-formulieren
description: Een HTML5-formulierprofiel is een resourceknooppunt in Apache Sling. Deze vertegenwoordigt een aangepaste versie van de Renderservice voor HTML5-formulieren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 9cd22244-9aa6-4b5f-96cf-c9cb3d6f9c8a
feature: HTML5 Forms,Mobile Forms
exl-id: cf86c810-c466-4894-acc2-d4faf49754cc
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 22aeedaaf4171ad295199a989e659b6bf5ce9834
workflow-type: tm+mt
source-wordcount: '682'
ht-degree: 0%

---

# Een aangepast profiel maken voor HTML5-formulieren {#creating-a-custom-profile-for-html-forms}

<span class="preview"> De HTML5 Forms-functionaliteit wordt aangeboden als onderdeel van het programma voor vroege toegang. Als u toegang wilt aanvragen, stuurt u een e-mail van uw officiële (werk)e-mailadres naar aem-forms-ea@adobe.com.
</span>

Een profiel is een middelknoop in [ Apache Sling ](https://sling.apache.org/). Deze vertegenwoordigt een aangepaste versie van de renderingsservice voor HTML5-formulieren. Met de service HTML5 Forms Rendition kunt u de weergave, het gedrag en de interacties van de HTML5-formulieren aanpassen. Er bestaat een profielknooppunt in de `/content` -map in de JCR-opslagplaats. U kunt het knooppunt rechtstreeks in de map `/content` of in een submap van de map `/content` plaatsen.

De profielknoop heeft **sling:resourceSuperType** bezit en de standaardwaarde is **xfaforms/profiel**. Het renderscript voor het knooppunt staat op /libs/xfaforms/profile.

De Sling-scripts zijn JSP-scripts. Deze JSP-scripts dienen als containers voor het samenstellen van de HTML voor het aangevraagde formulier en de vereiste JS/CSS-artefacten. Deze het Verdelen manuscripten worden ook bedoeld als **manuscripten van Renderer van het Profiel**. De profielrenderer roept de Forms OSGi-service aan om het gevraagde formulier te genereren.

Het profielscript bevindt zich in html.jsp en html.POST.jsp voor GET- en POST-verzoeken. U kunt een of meer bestanden kopiëren en wijzigen om uw aanpassingen te overschrijven en toe te voegen. Breng geen wijzigingen op de plaats aan. Dergelijke wijzigingen worden door de patchupdate overschreven.

Een profiel bevat verschillende modules. De modules zijn formRuntime.jsp, config.jsp, toolbar.jsp, formBody.jsp, nav_footer.jsp, en footer.jsp.

## formRuntime.jsp {#formruntime-jsp-br}

De modules formRuntime.jsp bevat verwijzingen van de cliëntbibliotheken. Het toont ook methodes om scèneinformatie uit het verzoek te halen en de gelokaliseerde berichten in het verzoek te omvatten. U kunt eigen aangepaste JavaScript-bibliotheken of -stijlen opnemen in formRuntime.jsp.

## config.jsp {#config-jsp}

De module config.jsp bevat diverse configuraties zoals registreren, de volmachtsdiensten, en gedragsversie. U kunt uw eigen configuratie en widgetaanpassing aan de module config.jsp toevoegen. U kunt configuraties zoals de registratie van de douanewidget aan de module config.jsp ook toevoegen.

## toolbar.jsp {#toolbar-jsp}

Het bestand toolbar.jsp bevat code waarmee een gekleurde werkbalk wordt gemaakt. Als u de werkbalk wilt verwijderen, verwijdert u toolbar.jsp uit HTML.jsp

## formBody.jsp {#formbody-jsp}

De module formBody.jsp is bedoeld voor de HTML-weergave van het XFA-formulier.

## nav_footer.jsp {#nav-footer-jsp}

In eerste instantie wordt met het HTML5-formulier alleen de eerste pagina van het formulier weergegeven. Wanneer een gebruiker door het formulier schuift, worden de overige formulieren geladen. Hierdoor verloopt het laden sneller. De component nav_footer.jsp bevat alle stijlen en vereiste elementen om het laden van de pagina&#39;s tijdens het schuiven te vergemakkelijken.

## footer.jsp {#footer-jsp}

De module footer.jsp is leeg. Hiermee kunt u scripts toevoegen die alleen voor gebruikersinteractie worden gebruikt.

## Aangepaste profielen maken {#creating-custom-profiles}

Voer de volgende stappen uit om een aangepast profiel te maken:

### Profielknooppunt maken {#create-profile-node}

1. Navigeer naar de CRX DE-interface op de URL: `https://'[server]:[port]'/crx/de` en meld u aan bij de interface met beheerdersreferenties.

1. Navigeer in het linkerdeelvenster naar de locatie */content/xfaforms/profiles* .

1. Kopieer het knoopgebrek, en deeg de knoop in verschillende omslag (*/content/profiles*) met naam *vorm*.

1. Selecteer de nieuwe knoop, *vorm*, en voeg een koordbezit toe: *slepend:resourceType* met waarde: *vorm/demo*.

1. Klik op Alles opslaan in het werkbalkmenu om de wijzigingen op te slaan.

### Het rendererscript voor profielen maken {#create-the-profile-renderer-script}

Nadat u een aangepast profiel hebt gemaakt, voegt u renderinformatie toe aan dit profiel. Als CRX een aanvraag voor het nieuwe profiel ontvangt, wordt gecontroleerd of de map /apps voor de JSP-pagina bestaat. Maak de JSP-pagina in de map /apps.

1. Navigeer in het linkerdeelvenster naar de map `/apps` .
1. Klik met de rechtermuisknop op de `/apps` map en kies een map met de naam **Transform** .
1. Binnen de **transformatie** omslag creeert een genoemde omslag **demo**.
1. Klik **sparen allen** knoop.
1. Navigeer aan `/libs/xfaforms/profile/html.jsp` en kopieer de knoop **html.jsp**.
1. Plak **html.jsp** knoop in de `/apps/hrform/demo` hierboven gecreeerd omslag met zelfde naam **html.jsp** en klik **sparen**.
1. Als u andere componenten van profielmanuscript hebt, volg stap 1-6 om de componenten in /apps/hrform/demo omslag te kopiëren.

1. Open URL `https://'[server]:[port]'/content/xfaforms/profiles/hrform.html` om te controleren of het profiel is gemaakt.

Om uw vormen te verifiëren, **voer uw formulieren** van uw lokaal dossiersysteem in AEM Forms in en [ voorproef de vorm ](/help/forms/previewing-forms.md) op de instantie van de de serverauteur van AEM.
