---
title: Wat zijn de verhogingen aan de Invoke dienst VRE voor vormen die op de Componenten van de Kern worden gebaseerd?
description: Verbeteringen aan de Invoke dienst voor de regelredacteur
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
keywords: Roep de dienstverhogingen in VRE aan, bevolkend drop-down opties gebruikend de aanroepdienst, Reeks herhaalbaar paneel gebruikend output van de aanroepdienst, Reeks paneel gebruikend output van de aanroepdienst, de outputparameter van het Gebruik van de aanroepdienst om ander gebied te bevestigen.
exl-id: 2ff64a01-acd8-42f2-aae3-baa605948cdd
source-git-commit: f772a193cce35a1054f5c6671557a6ec511671a9
workflow-type: tm+mt
source-wordcount: '1766'
ht-degree: 0%

---

# Externe API&#39;s integreren met Visual Rule Editor in Core Component Forms

De visuele Redacteur van de Regel in een AanpassingsVorm steunt de **Invoke eigenschap van de Dienst**, toelatend u om met externe APIs door de Modellen van de Gegevens van de Vorm (FDM) te verbinden die voor uw instantie wordt gevormd. U kunt formuliervelden rechtstreeks toewijzen aan de invoerparameters van de service en de optie voor gebeurtenislading gebruiken om de uitvoerparameters toe te wijzen. De visuele Redacteur van de Regel laat u ook regels voor succes en mislukkingsmanagers bepalen die op de reactie van de dienst worden gebaseerd: de succesvolle handlers behandelen succesvolle API vraag, terwijl de mislukkingsmanagers fouten beheren.

Zo kunt u gemakkelijk API-aanvragen van uw formulier verzenden, de API-reacties verwerken en de geretourneerde gegevens dynamisch weergeven of gebruiken in het formulier. Dit zorgt voor een naadloze integratie tussen uw adaptieve formulier en externe systemen of gegevensbronnen.


## Voordelen om de Invoke Service in de de regelredacteur van de vorm te gebruiken

Hier zijn weinig voordelen om de verrichting van de Dienst van de Invoke in de regelredacteur van een Vorm Adaotive te gebruiken:

* **Gestroomlijnde API integratie**: De visuele Redacteur van de Regel vereenvoudigt het proces om de externe diensten of APIs in uw Aangepaste Forms te integreren. Door de **Invoke Dienst** te gebruiken, kunt u vormen aan diverse gegevensbronnen en de diensten zonder de behoefte aan complexe codering gemakkelijk verbinden, die vormintegratie efficiënter maken.

* **Dynamische reactie behandeling**: U kunt succes en foutenreacties beheren die op de outputreacties van de **worden gebaseerd roepen Dienst**, toestaand vormen om dynamisch op verschillende scenario&#39;s te reageren. Het zorgt ervoor dat formulieren op de juiste wijze omgaan met verschillende omstandigheden, waardoor de flexibiliteit en de controle worden verbeterd.

* **Verbeterde gebruikersinteractie**: Het gebruiken van de **roept Dienst** in de regelredacteur toe laat bevestiging in real time binnen uw vormen toe, die een betere gebruikerservaring verstrekken. Het zorgt er ook voor dat gegevens correct worden gevalideerd aan de serverzijde, waardoor fouten worden verminderd en de betrouwbaarheid van formulieren wordt verbeterd.

## De managers van de Dienst van de Vraag voor succes en mislukkingsreacties

>[!NOTE]
>
> U kunt **gebruiken aanhaalt de het succes van de Dienst** en mislukkingsmanagers slechts voor vormen die op kerncomponenten worden gebaseerd. Forms die op stichtingscomponenten wordt gebaseerd steunt niet **het succes van de Dienst van de Invoke** en mislukkingsmanagers.

De visuele regelredacteur staat u toe om regels voor succes en mislukkingsmanagers voor **tot stand te brengen de verrichtingen van de Dienst** aanhalen die op zijn outputreacties worden gebaseerd. Onder beeld toont de **Invoke Dienst** in Visuele regelredacteur voor een Aanpassende Vorm:

![&#x200B; roept de dienstmanagers &#x200B;](/help/forms/assets/invoke-service-rule-editor.png) aan

Als u een geluids- of fouthandler wilt toevoegen, klikt u respectievelijk op **[!UICONTROL Add Success Handler]** of **[!UICONTROL Add Failure Handler]** .

Wanneer u **[!UICONTROL Add Success Handler]** klikt, verschijnt de **[!UICONTROL Invoke Service Success Handler]** regelredacteur, toestaand u om regels of logica te specificeren om de **te beheren aanhaalt de 3&rbrace; outputreactie van de Dienst &lbrace;wanneer de verrichting succesvol is.** U kunt zelfs regels opgeven zonder voorwaarden te definiëren. U kunt echter voorwaarden voor de succeshandler toevoegen door op de optie **[!UICONTROL Add Condition]** te klikken.

![&#x200B; de manager van het de dienstsucces aanhalen &#x200B;](/help/forms/assets/invoke-service-success-handler.png)

U kunt veelvoudige regels toevoegen om succesvolle reacties voor de **te behandelen roept de verrichting van de Dienst** aan:

![&#x200B; Veelvoudige succesmanager &#x200B;](/help/forms/assets/invoke-service-multiple-success-handlers.png){width=50%, height=50%}

Op dezelfde manier kunt u regels toevoegen om **te behandelen roept de uitvoerreactie van de Dienst** aan wanneer de verrichting niet succesvol is. In de onderstaande afbeelding wordt de regeleditor van **[!UICONTROL Invoke Service Failure Handler]** weergegeven:

![&#x200B; de manager van de de dienstmislukking aanhalen &#x200B;](/help/forms/assets/invoke-service-failue-handler.png)

U kunt veelvoudige regels ook toevoegen om mislukte reacties van de **te behandelen roept de verrichting van de Dienst**.

De **laat de Bevestiging van de Fout op de eigenschap van de Server** toe bevestigen die door de auteur worden toegevoegd terwijl het ontwerpen van een Aangepast Vorm om op de server ook te lopen.

## Vereisten om de Invoke Dienst in de regelredacteur te gebruiken

Hieronder zijn de eerste vereisten u moet bevredigen alvorens **de Dienst** in de regelredacteur te gebruiken aanhaalt:

* Zorg ervoor u een gegevensbron hebt gevormd. Voor instructies bij het vormen van een gegevensbron, [&#x200B; klik hier &#x200B;](/help/forms/configure-data-sources.md).
* Maak een formuliergegevensmodel met de geconfigureerde gegevensbron. Voor begeleiding bij het creëren van een Model van de Gegevens van de Vorm, [&#x200B; klik hier &#x200B;](/help/forms/create-form-data-models.md).
* Zorg ervoor dat de Componenten van de Kern voor uw milieu worden toegelaten. Installeer de nieuwste versie om Adaptive Forms Core Components in te schakelen voor uw AEM Cloud Service-omgeving.

## Invoke Service verkennen via verschillende gebruiksgevallen

De Visuele redacteur van de regel **roept Dienst** aan staat u toe om verscheidene nuttige verrichtingen uit te voeren. U kunt het gebruiken om dropdown opties te bevolken, herhaalbare of eenvoudige panelen te plaatsen, en vormgebieden te bevestigen, allen gebaseerd op de outputreactie van de **Invoke Dienst**. Zo vergroot u de flexibiliteit en interactiviteit van uw formulieren.

De lijst beschrijft hieronder een paar scenario&#39;s waarin de **Invoke Dienst** kan worden gebruikt:

| **Geval van het Gebruik** | **Beschrijving** |
|----------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| **bevolkt dropdown opties gebruikend output van de Invoke Dienst** | Bevolkt dropdown opties dynamisch gebaseerd op gegevens die van de Invoke output van de Dienst worden teruggewonnen. [&#x200B; klik hier &#x200B;](#use-case-1-populate-dropdown-values-using-the-output-of-invoke-service), om de implementatie te zien. |
| **plaats herhaalbaar paneel gebruikend output van de Invoke Service** | Vormt een herhaalbaar paneel door gegevens van de Uitvoer van de Dienst van de Invoke te gebruiken, die voor dynamische panelen toestaan. [&#x200B; klik hier &#x200B;](#use-case-2-set-repeatable-panel-using-output-of-invoke-service), om de implementatie te zien. |
| **plaats paneel gebruikend output van de Dienst van de Invoke** | Hiermee stelt u de inhoud of zichtbaarheid van een deelvenster in met specifieke waarden uit de uitvoer Service aanroepen. [&#x200B; klik hier &#x200B;](#use-case-3-set-panel-using-output-of-invoke-service), om de implementatie te zien. |
| **de outputparameter van het Gebruik van de Invoke Dienst om andere gebieden** te bevestigen | Hiermee gebruikt u specifieke uitvoerparameters van de Invoke-service om de formuliervelden te valideren. [&#x200B; klik hier &#x200B;](#use-case-4-use-output-parameter-of-invoke-service-to-validate-other-fields), om de implementatie te zien. |
| **de Payload van de Gebeurtenis van het Gebruik in Navigeer aan Actie in de Invoke Dienst** | Gebruikt de gebeurtenislading om succes en mislukkingsreacties te behandelen en gegevens over te gaan tot Navigeren aan actie tijdens navigatie. [&#x200B; klik hier &#x200B;](#use-case-5-use-event-payload-in-navigate-to-action-in-invoke-service) om de implementatie te zien. |

Maak een `Get Information` -formulier waarmee waarden worden opgehaald op basis van de invoer die u hebt ingevoerd in het tekstvak `Pet ID` . In de onderstaande schermafbeelding ziet u het formulier dat in deze gevallen wordt gebruikt:

![&#x200B; krijgt informatievorm &#x200B;](/help/forms/assets/get-information-form.png)

**Gebieden van de Vorm**

Voeg de volgende velden toe aan het formulier:
* **ga Huisdier identiteitskaart** in: TextBox
* **Uitgezochte Foto URLs**: Dropdown
* **Markeringen**: Comité
   * Naam: TextBox
   * ID: TextBox
* **Categorie**: Comité
   * Naam: TextBox
* **legt** voor: leg knoop voor

>[!NOTE]
>
> In het **Bind 1&rbrace; gebied van de Verwijzing &lbrace;in de** dialoog van Eigenschappen **van de vormgebieden, uitgezochte** folder search_18 ![&#x200B; en navigeer om het binaire bezit te selecteren u in het Model van de Gegevens van de Vorm (FDM) toevoegde.](assets/folder-search-icon.svg)

**het Vormen panelen**

Stel de deelvensters als herhalend in met de volgende beperkingen:
* Minimumwaarde: 1
* Maximumwaarde: 4

U kunt de waarden van de herhalende deelvensters aanpassen aan uw wensen.

**Gegevensbron**

In dit voorbeeld, wordt de [&#x200B; Benzine van de Wagger &#x200B;](https://petstore.swagger.io/) API gebruikt om een gegevensbron te vormen. Het [&#x200B; Model van de Gegevens van de Vorm &#x200B;](/help/forms/create-form-data-models.md) wordt gevormd voor de [&#x200B; getPetById &#x200B;](https://petstore.swagger.io/#/pet/getPetById) dienst, die huisdetails terugwint die op ingegane identiteitskaart worden gebaseerd.

Laat het volgende JSON posten gebruikend de [&#x200B; addPet &#x200B;](https://petstore.swagger.io/#/pet/addPet) dienst in de [&#x200B; Benzine van de Wagger &#x200B;](https://petstore.swagger.io/) API:

```
{
        "id": 101,
        "category": {
            "id": 1,
            "name": "Labrador"
        },
        "name": "Lisa",
        "photoUrls": [
            "https://example.com/photos/lisa1.jpg",
            "https://example.com/photos/lisa2.jpg"
        ],
        "tags": [
            {
                "id": 1,
                "name": "vaccinated"
            },
            {
                "id": 2,
                "name": "friendly"
            },
            {
                "id": 3,
                "name": "house-trained"
            }
        ],
        "status": "available"
    }
```

De regels en de logica worden uitgevoerd gebruikend **roepen de actie van de Dienst** in de regelredacteur op `Pet ID` textbox om de vermelde gebruiksgevallen aan te tonen.

Laten we nu de implementatie van elk gebruiksgeval in detail onderzoeken.

### Gebruik Geval 1: bevolk dropdown waarden gebruikend de output van de Dienst van Invoke

In dit geval wordt getoond hoe u de meerkeuzeopties dynamisch kunt vullen op basis van de uitvoer van een `Invoke Service` .

#### Implementatie

Hiertoe maakt u een regel in het tekstvak `Pet ID` om de service `getPetById` aan te roepen. Stel in de regel de eigenschap `enum` van de `photo-url` dropdown in op `photoUrls` in **[!UICONTROL Add Success Handler]** .

![&#x200B; vastgestelde drop-down waarde &#x200B;](/help/forms/assets/set-dropdownoption.png)

#### Uitvoer

Typ `101` in het tekstvak `Pet ID` om de vervolgkeuzemogelijkheden dynamisch te vullen op basis van de ingevoerde waarde.

![&#x200B; Resultaat &#x200B;](/help/forms/assets/output1.png)

### Hoofdlettergebruik 2: stel een herhaalbaar deelvenster in met uitvoer van Invoke Service

Dit gebruiksgeval toont aan hoe te om herhaalbare panelen dynamisch te bevolken die op de output van een **worden gebaseerd de Dienst van de Invoke**.

#### Overwegingen

* Verzeker de naam van het herhaalbare paneel past de parameter van de **Invoke Dienst** aan waarvoor u het paneel wilt plaatsen.
* Het paneel herhaalt voor het aantal waarden die door het overeenkomstige **zijn teruggekeerd roept de Dienst** gebied van de Dienst.

#### Implementatie

Maak een regel in het tekstvak `Pet ID` om de service `getPetById` aan te roepen. Voeg in **[!UICONTROL Add Success Handler]** nog een succeshandlerreactie toe. Stel de waarde van het deelvenster `tags` in op `tags` in de regel.

![&#x200B; creeer regel voor herhaalbaar paneel &#x200B;](/help/forms/assets/create-rule-repeatable-panel.png)

#### Uitvoer

Typ `101` in het tekstvak `Pet ID` om het herhaalbare deelvenster dynamisch te vullen op basis van de invoerwaarde.

![&#x200B; Output &#x200B;](/help/forms/assets/output2.png)

### Hoofdlettergebruik 3: deelvenster instellen met uitvoer van Invoke Service

Dit gebruiksgeval toont aan hoe te om de waarde van een paneel dynamisch te plaatsen dat op de output van wordt gebaseerd **roept Dienst** aan.

#### Overwegingen

* Verzeker de naam van het paneel de parameter van de **haalt Dienst** aan waarvoor u het paneel wilt plaatsen.
* Het deelvenster wordt herhaald voor het aantal waarden dat wordt geretourneerd door het overeenkomstige veld Invoke Service.

#### Implementatie

Maak een regel in het tekstvak `Pet ID` om de service `getPetById` aan te roepen. Voeg in **[!UICONTROL Add Success Handler]** nog een succeshandlerreactie toe. Stel de waarde van het tekstvak `categoryname` in op `category.name` in de regel.

![&#x200B; creeer regel voor herhaalbaar paneel &#x200B;](/help/forms/assets/set-panel-values.png)

#### Uitvoer

Typ `101` in het tekstvak `Pet ID` om het deelvenster dynamisch te vullen op basis van de invoerwaarde.

![&#x200B; Output &#x200B;](/help/forms/assets/output3.png)

### Hoofdlettergebruik 4: Gebruik uitvoerparameter van Invoke Service om andere velden te valideren

Dit gebruiksgeval toont aan hoe te om de output van **te gebruiken roept de Dienst** aan om andere vormgebieden dynamisch te bevestigen.

#### Implementatie

Maak een regel in het tekstvak `Pet ID` om de service `getPetById` aan te roepen. Voeg in **[!UICONTROL Add Failure Handler]** een antwoord van de mislukkingshandler toe. Verberg **voorleggen** knoop als onjuist `Pet ID` is ingegaan.

![&#x200B; Handler van de Mislukking &#x200B;](/help/forms/assets/create-rule-failure-handler.png)

#### Uitvoer

Ga `102` in het `Pet ID` tekstvakje in, en **voorleggen** knoop is verborgen.

![&#x200B; Output &#x200B;](/help/forms/assets/output4.png)

### Hoofdlettergebruik 5: gebruik Event Payload in Navigeer naar de handeling in Invoke Service

Dit gebruiksgeval toont aan hoe te om een regel op **te vormen voorlegt** knoop die **roept de Invoke Dienst** en richt dan de gebruiker aan een andere pagina opnieuw gebruikend **aan** actie navigeren.

#### Implementatie

Creeer een regel op **voorleggen** knoop om de `redirect-api` API dienst aan te halen. Deze dienst is verantwoordelijk voor het opnieuw richten van de gebruiker aan de **vorm van het Contact van ons**.

U kunt een API rechtstreeks als de API-service `redirect-api` integreren in de Rule Editor met behulp van de JSON-gegevens die hieronder worden vermeld:

```json
{
  "id": "1",
  "path": "/content/dam/formsanddocuments/contact-detail/jcr:content?wcmmode=disabled"
}
```

>[!NOTE]
>
> Leren hoe te om API in de interface van de Redacteur van de Regel direct te integreren, [&#x200B; klik hier &#x200B;](/help/forms/api-integration-in-rule-editor.md) zonder een vooraf bepaald Model van de Gegevens van de Vorm te gebruiken.

In **[!UICONTROL Add Success Handler]**, vorm **navigeer aan** actie om de gebruiker aan de **pagina van het Contact van het Contact** opnieuw te richten gebruikend de `Event Payload` parameter. Hier kan de gebruiker zijn contactgegevens verzenden.

![&#x200B; de Payload van de Gebeurtenis &#x200B;](/help/edge/docs/forms/assets/navigate-to-eventpayload.png)

Naar keuze, vorm een mislukkingsmanager om een foutenmelding te tonen als de de dienstvraag ontbreekt.

#### Uitvoer

Wanneer **voorlegt** knoop wordt geklikt, wordt de `redirect-api` API dienst aangehaald. Op succes, wordt de gebruiker opnieuw gericht aan de **pagina van het Contact van ons**.

![&#x200B; Uitvoer van de gebeurtenislading &#x200B;](/help/forms/assets/output5.gif)

## Veelgestelde vragen

**Q: Wat gebeurt als ik een regel gebruikend de Invoke Dienst en dan verbetering aan de recentste versie van de kerncomponenten heb gecreeerd?**

**A:** wanneer u aan de recentste versie van de kerncomponenten bevordert, **roept de regel van de Dienst** automatisch aan het recentste gebruikersinterface op, aangezien het achterwaarts compatibel is.

**Q: Kan ik veelvoudige regels toevoegen om succesvolle of mislukkingsreacties voor de Invoke verrichting van de Dienst te behandelen?**

**A:** ja, kunt u veelvoudige regels toevoegen om succesvolle of mislukkingsreacties voor de **te behandelen aanhaalt de verrichting van de Dienst**.

## Verwante artikelen

* [Gegevensbronnen configureren](configure-data-sources.md)
* [Formuliergegevensmodel maken (FDM)](create-form-data-models.md)
* [Werken met het formuliergegevensmodel (FDM)](work-with-form-data-model.md)
* [Formuliergegevensmodel (FDM) gebruiken](using-form-data-model.md)


## Aanvullende bronnen

{{see-also-rule-editor}}
