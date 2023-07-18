---
title: Hoe kan ik de prestaties van grote formulieren verbeteren door ze lui te laden?
description: Leer hoe u de prestaties van grote formulieren kunt verbeteren door ze lui te laden. Lazy loading verbetert de prestaties van grote en complexe Adaptive Forms aanzienlijk door de initialisatie en het laden van formulierfragmenten uit te stellen totdat deze zichtbaar zijn.
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: 0cd38edb-2201-4ca6-8b84-6b5b7f76bd90
source-git-commit: b6dcb6308d1f4af7a002671f797db766e5cfe9b5
workflow-type: tm+mt
source-wordcount: '1002'
ht-degree: 0%

---

# Verbeter de prestaties van grote formulieren met het laden van de formulieren{#improve-performance-of-large-forms-with-lazy-loading}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/lazy-loading-adaptive-forms.html) |
| AEM as a Cloud Service | Dit artikel |


## Inleiding tot wazig laden {#introduction-to-lazy-loading}

Wanneer het formulier groot en complex wordt met honderden en duizenden velden, ervaren eindgebruikers een lange responstijd bij het weergeven van formulieren tijdens runtime. Om de reactietijd te minimaliseren, staat Adaptive Forms u toe om vormen in logische fragmenten te breken en te vormen om initialisering of lading van fragmenten uit te stellen tot het fragment zichtbaar moet zijn. Het wordt genoemd lazy ladend. Bovendien worden de fragmenten die zijn geconfigureerd voor wazig laden verwijderd als de gebruiker naar andere secties in het formulier navigeert en de fragmenten niet meer zichtbaar zijn.

Laten we eerst de vereisten en voorbereidende stappen begrijpen voordat u lazy laden configureert.

## Voorbereiden op het configureren van wazig laden {#preparing-to-configure-lazy-loading}

Voordat u het laden van fragmenten in uw adaptieve vorm configureert, is het belangrijk dat u strategieën definieert om fragmenten te maken, waarden identificeert die in scripts worden gebruikt of die in andere fragmenten worden doorverwezen, en regels definieert om de zichtbaarheid van velden in liefst geladen fragmenten te beheren.

* **Fragmenten identificeren en maken**
U kunt alleen Adaptieve formulierfragmenten configureren voor wazig laden. Een fragment is een zelfstandig segment dat zich buiten een adaptief formulier bevindt en dat in verschillende formulieren opnieuw kan worden gebruikt. De eerste stap bij het implementeren van lui laden is het identificeren van logische secties in een formulier en het omzetten ervan in fragmenten. U kunt een geheel nieuw fragment maken of een bestaand formulierdeelvenster opslaan als fragment.

  <!--For more information about creating fragments, see [Adaptive Form Fragments](adaptive-form-fragments.md).-->

* **Algemene waarden identificeren en markeren**
Bij op Forms gebaseerde transacties worden dynamische elementen gebruikt om relevante gegevens van gebruikers vast te leggen en te verwerken om het invullen van formulieren te vereenvoudigen. Het formulier heeft bijvoorbeeld veld A in fragment X, waarvan de waarde de geldigheid van veld B in een ander fragment bepaalt. In dit geval moet, als fragment X is gemarkeerd voor lui laden, de waarde van veld A beschikbaar zijn om veld B te valideren, zelfs als fragment X niet is geladen. Hiertoe kunt u veld A markeren als globaal, zodat de waarde ervan beschikbaar is voor het valideren van veld B wanneer fragment X niet is geladen.

  Voor informatie over hoe u een veldwaarde globaal kunt maken, raadpleegt u [Lazy laden configureren](lazy-loading-adaptive-forms.md#p-configuring-lazy-loading-p).

* **Regels schrijven om de zichtbaarheid van velden te bepalen**
Forms bevat enkele velden en secties die niet van toepassing zijn op alle gebruikers en onder alle omstandigheden. Forms-auteurs en -ontwikkelaars gebruiken zichtbaarheids- of show-hide-regels om hun zichtbaarheid te bepalen op basis van gebruikersinvoer. Bijvoorbeeld, wordt het gebied van het Adres van het Bureau niet getoond aan de gebruikers die op het gebied van de Status van de Werkgelegenheid in een vorm werkloos kiezen. Voor meer informatie over het schrijven van regels, zie [Regeleditor gebruiken](rule-editor.md).

  U kunt zichtbaarheidsregels gebruiken in de laaggeladen fragmenten, zodat voorwaardelijke velden alleen worden weergegeven wanneer ze vereist zijn. Markeer ook het voorwaardelijke veld globaal om ernaar te verwijzen in de zichtbaarheidsexpressie van het langzaam geladen fragment.

## Lazy laden configureren {#configuring-lazy-loading}

Voer de volgende stappen uit om het laden in een adaptief formulierfragment mogelijk te maken:

1. Open het adaptieve formulier in de ontwerpmodus met het fragment dat u wilt inschakelen voor wazig laden.
1. Selecteer het adaptieve formulierfragment en tik op ![vormen](assets/configure-icon.svg).
1. Schakel in de zijbalk de optie **[!UICONTROL Load fragment lazily]** en tikken **Gereed**.

   ![Lazy loading inschakelen voor het adaptieve formulierfragment](assets/lazy-loading-fragment.png)

   Het fragment is nu ingeschakeld voor wazig laden.

U kunt de waarden van objecten in het laaggeladen fragment als globaal markeren, zodat deze beschikbaar zijn voor gebruik in scripts wanneer het bevattende fragment niet is geladen. Ga als volgt te werk:

1. Open het adaptieve formulierfragment in de ontwerpmodus.
1. Tik op het veld waarvan u de waarde als globaal wilt markeren en tik vervolgens op ![vormen](assets/configure-icon.svg).
1. Schakel in de zijbalk de optie **[!UICONTROL Use value during lazy loading]**.

   ![Lazy loading field in sidebar](assets/enable-lazy-loading.png)

   De waarde wordt nu gemarkeerd als globaal en is beschikbaar voor gebruik in scripts, zelfs als het omvattende fragment wordt verwijderd.

## Overwegingen en aanbevolen procedures voor het configureren van lazy laden {#considerations-and-best-practices-for-configuring-lazy-loading}

Enkele beperkingen, aanbevelingen en belangrijke punten waarmee u rekening moet houden bij het werken met lazy laden zijn:

* Aanbevolen wordt om adaptieve Forms over XFA-gebaseerde Adaptieve Forms op basis van XSD-schema&#39;s te gebruiken voor het configureren van lui laden op grote formulieren. De prestatiewinst als gevolg van de lazy loading-implementatie in op XFA gebaseerde Adaptive Forms is relatief minder dan de toename in op XSD gebaseerde Adaptive Forms.
* Het laden van fragmenten in een adaptieve vorm die gebruikmaken van **[!UICONTROL Responsive -everything on one page without navigation]** layout voor het hoofddeelvenster. Als resultaat van de responsieve lay-outconfiguratie, laden alle fragmenten gelijktijdig in een Adaptief Vorm. Het kan ook leiden tot verminderde prestaties.
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
  guideBridge.resolveNode(guideBridge.getFocus({&quot;focusOption&quot;: &quot;navigablePanel&quot;}).resetData()
