---
title: Hoe kunnen we de prestaties van grote formulieren verbeteren door ze lui te laden?
description: Leer hoe u de prestaties van grote formulieren kunt verbeteren door ze lui te laden. Lazy loading verbetert de prestaties van grote en complexe Adaptive Forms aanzienlijk door de initialisatie en het laden van formulierfragmenten uit te stellen totdat deze zichtbaar zijn.
feature: Adaptive Forms, Foundation Components
role: User, Developer
level: Intermediate
exl-id: 0cd38edb-2201-4ca6-8b84-6b5b7f76bd90
source-git-commit: b5340c23f0a2496f0528530bdd072871f0d70d62
workflow-type: tm+mt
source-wordcount: '1048'
ht-degree: 0%

---

# Verbeter de prestaties van grote formulieren met het laden van de formulieren{#improve-performance-of-large-forms-with-lazy-loading}

>[!NOTE]
>
> De Adobe adviseert het gebruiken van de moderne en verlengbare gegevens vangt [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/creating-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten.

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/lazy-loading-adaptive-forms.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |


## Inleiding tot wazig laden {#introduction-to-lazy-loading}

Wanneer het formulier groot en complex wordt met honderden en duizenden velden, ervaren eindgebruikers een lange responstijd bij het weergeven van formulieren tijdens runtime. Om de reactietijd te minimaliseren, laat Adaptive Forms u vormen in logische fragmenten breken en vormen om initialisering of lading van fragmenten uit te stellen tot het fragment zichtbaar moet zijn. Het wordt genoemd lazy ladend. Bovendien worden de fragmenten die zijn geconfigureerd voor wazig laden verwijderd wanneer de gebruiker naar andere secties in het formulier navigeert en de fragmenten niet meer zichtbaar zijn.

Laten we eerst de vereisten en voorbereidende stappen begrijpen voordat u lazy laden configureert.

## Voorbereiden op het configureren van wazig laden {#preparing-to-configure-lazy-loading}

Voordat u het laden van fragmenten in uw adaptieve vorm configureert, is het belangrijk dat u strategieën definieert om fragmenten te maken, waarden identificeert die in scripts worden gebruikt of die in andere fragmenten worden doorverwezen, en regels definieert om de zichtbaarheid van velden in liefst geladen fragmenten te beheren.

* **identificeer en creeer fragmenten**
U kunt alleen Adaptieve formulierfragmenten configureren voor wazig laden. Een fragment is een zelfstandig segment dat zich buiten een adaptief formulier bevindt en dat in verschillende formulieren opnieuw kan worden gebruikt. De eerste stap bij het implementeren van lui laden is het identificeren van logische secties in een formulier en het omzetten ervan in fragmenten. U kunt een geheel nieuw fragment maken of een bestaand formulierdeelvenster opslaan als fragment.

  <!--For more information about creating fragments, see [Adaptive Form Fragments](adaptive-form-fragments.md).-->

* **identificeer en merk globale waarden**
Bij op Forms gebaseerde transacties worden dynamische elementen gebruikt om relevante gegevens van gebruikers vast te leggen en te verwerken om het invullen van formulieren te vereenvoudigen. Het formulier heeft bijvoorbeeld veld A in fragment X, waarvan de waarde de geldigheid van veld B in een ander fragment bepaalt. In dit geval moet, als fragment X is gemarkeerd voor lui laden, de waarde van veld A beschikbaar zijn om veld B te valideren, zelfs als fragment X niet is geladen. Hiertoe kunt u veld A markeren als globaal, zodat de waarde ervan beschikbaar is voor het valideren van veld B wanneer fragment X niet is geladen.

  Voor informatie over hoe te om een gebiedswaarde globaal te maken, zie [ Vormend lui ladend ](lazy-loading-adaptive-forms.md#p-configuring-lazy-loading-p).

* **schrijf regels om zicht van gebieden** te controleren
Forms bevat enkele velden en secties die niet van toepassing zijn op alle gebruikers en onder alle omstandigheden. Forms-auteurs en -ontwikkelaars gebruiken zichtbaarheids- of show-hide-regels om hun zichtbaarheid te bepalen op basis van gebruikersinvoer. Bijvoorbeeld, wordt het gebied van het Adres van het Bureau niet getoond aan de gebruikers die op het gebied van de Status van de Werkgelegenheid in een vorm werkloos kiezen. Voor meer informatie over het schrijven van regels, zie [ Gebruikend regelredacteur ](rule-editor.md).

  U kunt zichtbaarheidsregels gebruiken in de laaggeladen fragmenten, zodat voorwaardelijke velden alleen worden weergegeven wanneer ze vereist zijn. Markeer ook het voorwaardelijke veld globaal om ernaar te verwijzen in de zichtbaarheidsexpressie van het langzaam geladen fragment.

## Lazy laden configureren {#configuring-lazy-loading}

Voer de volgende stappen uit om het laden in een adaptief formulierfragment mogelijk te maken:

1. Open het adaptieve formulier in de ontwerpmodus met het fragment dat u wilt inschakelen voor wazig laden.
1. Selecteer het Adaptieve Fragment van de Vorm en selecteer ![ vormen ](assets/configure-icon.svg).
1. In sidebar, laat **[!UICONTROL Load fragment lazily]** toe en selecteer **Gedaan**.

   ![ laat luie lading voor het Aangepaste Fragment van de Vorm toe ](assets/lazy-loading-fragment.png)

   Het fragment is nu ingeschakeld voor wazig laden.

U kunt de waarden van objecten in het laaggeladen fragment als globaal markeren, zodat deze beschikbaar zijn voor gebruik in scripts wanneer het bevattende fragment niet is geladen. Ga als volgt te werk:

1. Open het adaptieve formulierfragment in de ontwerpmodus.
1. Selecteer het gebied waarvan waarde u als globaal wilt merken, en dan selecteren ![ ](assets/configure-icon.svg) vormt.
1. Schakel in het zijpaneel **[!UICONTROL Use value during lazy loading]** in.

   ![ Lazy ladend gebied in sidebar ](assets/enable-lazy-loading.png)

   De waarde wordt nu gemarkeerd als globaal en is beschikbaar voor gebruik in scripts, zelfs als het omvattende fragment wordt verwijderd.

## Overwegingen en aanbevolen procedures voor het configureren van lazy laden {#considerations-and-best-practices-for-configuring-lazy-loading}

Enkele beperkingen, aanbevelingen en belangrijke punten waarmee u rekening moet houden bij het werken met lazy laden zijn:

* Adobe raadt u aan om Adaptieve Forms met XSD-schema&#39;s te gebruiken in Adaptief Forms over XFA-gebaseerde indeling voor het configureren van lui laden op grote formulieren. De prestatiewinst als gevolg van de lazy loading-implementatie in op XFA gebaseerde Adaptive Forms is relatief minder dan de toename in op XSD gebaseerde Adaptive Forms.
* Configureer lui laden niet voor fragmenten in een adaptief formulier met **[!UICONTROL Responsive -everything on one page without navigation]** -indeling voor het hoofddeelvenster. Als resultaat van de responsieve lay-outconfiguratie, laden alle fragmenten gelijktijdig in een Adaptief Vorm. Het kan ook leiden tot verminderde prestaties.
* Het wordt aanbevolen om het laden van fragmenten in het eerste deelvenster dat wordt weergegeven bij het laden van het adaptieve formulier, niet te configureren.
* Lazy loading wordt ondersteund tot twee niveaus in de fragmenthiërarchie.
* Zorg ervoor dat velden die zijn gemarkeerd als globaal, uniek zijn in een adaptief formulier.
* U kunt zichtbaarheidsregels schrijven voor fragmenten die op basis van een voorwaarde moeten worden weergegeven of verborgen. U kunt bijvoorbeeld het fragment Gegevens echtgenoot weergeven of verbergen op basis van de staat van het huwelijk die een gebruiker heeft opgegeven.
* Componenten voor bestandsbijlagen en Algemene voorwaarden worden niet ondersteund in laaggeladen fragmenten.

### Aanbevolen procedures voor het schrijven van scripts voor het configureren van lazy loading {#scripting-best-practices-for-configuring-lazy-loading}

Belangrijke aandachtspunten bij het ontwikkelen van scripts voor luie laadvensters zijn:

* Zorg ervoor dat de initialisatie en de berekening van manuscripten die op de gebieden van een lui geladen fragment worden gebruikt in de aard van de epidemie zijn. Onbetrouwbare scripts zijn scripts die hetzelfde effect hebben, zelfs na meerdere uitvoeringen.
* Met de algemeen beschikbare eigenschap van velden maakt u de waarde van velden in een wazig venster voor laden beschikbaar voor alle andere deelvensters van een formulier.
* Verwijs geen verwijzingswaarde van een gebied binnen een lui paneel ongeacht gebied door zich globaal over fragmenten wordt duidelijk of niet.
* Met de functie voor het opnieuw instellen van deelvensters kunt u alle zichtbare elementen in het deelvenster opnieuw instellen met de volgende klikexpressie.\
  guideBridge.resolveNode(guideBridge.getFocus({&quot;focusOption&quot;: &quot;navigablePanel&quot;})).resetData()


## Zie ook {#see-also}

{{see-also}}