---
title: Hoe te om de regelredacteur te gebruiken om regels aan vormgebieden toe te voegen om dynamisch gedrag toe te voegen en complexe logica te bouwen aan een adaptieve vorm die op kerncomponenten wordt gebaseerd?
description: Met de Adaptive Forms-regeleditor kunt u dynamisch gedrag toevoegen en complexe logica in formulieren opnemen zonder codes of scripts.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
exl-id: 1292f729-c6eb-4e1b-b84c-c66c89dc53ae
source-git-commit: 780c68f0c21ef94ff6a73ce991370100b1a88db9
workflow-type: tm+mt
source-wordcount: '1176'
ht-degree: 0%

---


# Inleiding aan de Redacteur van de Regel voor Aangepast Vorm dat op de Componenten van de Kern wordt gebaseerd

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service (Core Components) | Dit artikel |
| AEM as a Cloud Service (Foundation Components) | [ klik hier ](/help/forms/rule-editor.md) |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html) |

In een Adaptief formulier dat is gebaseerd op Core Components, biedt de functie voor de regeleditor zowel zakelijke gebruikers als ontwikkelaars de mogelijkheid om regels voor adaptieve formulierobjecten te schrijven. Met deze regels worden acties gedefinieerd die op formulierobjecten worden geactiveerd op basis van vooraf ingestelde voorwaarden, gebruikersinvoer en gebruikersacties op het formulier. Deze functie helpt de ervaring bij het invullen van formulieren verder te stroomlijnen, zodat u zowel nauwkeurigheid als snelheid hebt.

De regeleditor biedt een intuïtieve en vereenvoudigde gebruikersinterface voor het schrijven van regels. Het biedt een visuele redacteur aan die aan alle gebruikers, die hen toestaat om regels tot stand te brengen en te beheren zonder uitgebreide technische kennis te vereisen. Deze visuele aanpak maakt het voor gebruikers gemakkelijker om de gewenste logica in hun formulieren te begrijpen en uit te voeren.

Een aantal belangrijke handelingen die u met behulp van regels kunt uitvoeren op adaptieve formulierobjecten zijn:

* Een object tonen of verbergen
* Een object in- of uitschakelen
* Een waarde instellen voor een object
* De waarde van een object valideren
* Functies uitvoeren om de waarde van een object te berekenen
* Roep de service Form Data Model (FDM) aan en voer een bewerking uit
* Eigenschap van een object instellen

<!-- Rule editor replaces the scripting capabilities in [!DNL Experience Manager 6.1 Forms] and earlier releases. However, your existing scripts are preserved in the new rule editor. For more information about working with existing scripts in the rule editor, see [Impact of rule editor on existing scripts](rule-editor.md#p-impact-of-rule-editor-on-existing-scripts-p). -->

Gebruikers die aan de groep `forms-power-users` zijn toegevoegd, kunnen scripts maken en bestaande scripts bewerken. Gebruikers in de groep [!DNL forms-users] kunnen de scripts gebruiken, maar maken of bewerken geen scripts.

Verwijs naar het [ Verschil tussen de Redacteur van de Regel van de Stichting en het artikel van de Redacteur van de Regel van de Component van de Kern ](/help/forms/rule-editor-core-components-difference-tables.md) voor een gedetailleerde vergelijking.

<!--
## Difference between Rule editor in Core Components and Rule Editor in Foundation Components

{{rule-editor-diff}}

>[!NOTE]
>
> To see how to create and use custom functions in detail, refer to [Custom functions in Adaptive Forms (Core Components)](/help/forms/create-and-use-custom-functions.md) article.

-->

## Een regel begrijpen {#understanding-a-rule}

Een regel is een combinatie van handelingen en voorwaarden. In de regeleditor omvatten handelingen zoals verbergen, weergeven, inschakelen, uitschakelen of de waarde van een object in een formulier berekenen. Voorwaarden zijn Booleaanse expressies die worden geëvalueerd door controles en bewerkingen uit te voeren op de status, waarde of eigenschap van een formulierobject. Handelingen worden uitgevoerd op basis van de waarde ( `True` of `False` ) die wordt geretourneerd door een voorwaarde te evalueren.

De regelredacteur verstrekt een reeks vooraf bepaalde regeltypes, zoals wanneer, tonen, verbergen, toelaten, onbruikbaar maken, Vastgestelde Waarde van, en Valideren om u te helpen regels schrijven. Elk regeltype laat u voorwaarden en acties in een regel bepalen. Het document verklaart verder elk regeltype in detail.

Een regel volgt doorgaans een van de volgende constructies:

**voorwaarde-actie** In deze constructie, bepaalt een regel eerst een voorwaarde die door een actie wordt gevolgd om teweeg te brengen. De constructie is vergelijkbaar met de if-then instructie in programmeertalen.

In regelredacteur, **wanneer** regeltype de voorwaarde-actie constructie afdwingt.

**actie-Voorwaarde** in deze constructie, bepaalt een regel eerst een actie om te teweegbrengen die door voorwaarden voor evaluatie wordt gevolgd. Een andere variatie van deze constructie is actie-voorwaarde-afwisselende actie, die ook een afwisselende actie bepaalt om te teweegbrengen als de voorwaarde Vals terugkeert.

Toon, verberg, laat toe, maak onbruikbaar, plaats Waarde van, en bevestig regeltypes in de regelredacteur afdwingen de actie-voorwaarde regelconstructie. Standaard is de alternatieve actie voor Tonen Verbergen en voor Inschakelen Uitgeschakeld en de tegenovergestelde manier. U kunt de alternatieve standaardhandeling niet wijzigen.

>[!NOTE]
>
>De beschikbare regeltypen, inclusief de voorwaarden en handelingen die u in de regeleditor definieert, zijn ook afhankelijk van het type formulierobject waarop u een regel maakt. In de regeleditor worden alleen geldige regeltypen en opties weergegeven voor het schrijven van voorwaarde- en handelingsinstructies voor een bepaald type formulierobject. U ziet bijvoorbeeld geen typen Valideren en Waarde instellen voor een deelvensterobject.

Voor meer informatie over regeltypes beschikbaar in de regelredacteur, zie [ Beschikbare regeltypes in regelredacteur ](rule-editor.md#p-available-rule-types-in-rule-editor-p).

### Richtlijnen voor het kiezen van een regelconstructie {#guidelines-for-choosing-a-rule-construct}

Hoewel u de meeste gebruiksgevallen kunt bereiken door om het even welke regelconstructie te gebruiken, zijn hier sommige richtlijnen om één constructie over een andere te kiezen. Voor meer informatie over de beschikbare regels in regelredacteur, zie [ Beschikbare regeltypes in regelredacteur ](rule-editor.md#p-available-rule-types-in-rule-editor-p).

* Een typische regel van het duim wanneer het creëren van een regel is het denken over het in de context van het voorwerp waarop u een regel schrijft. Denk eraan dat u veld B wilt verbergen of weergeven op basis van de waarde die een gebruiker in veld A heeft opgegeven. In dit geval evalueert u een voorwaarde in veld A en activeert u een actie in veld B op basis van de waarde die de voorwaarde retourneert.

  Daarom als u een regel op gebied B (het voorwerp schrijft waarop u een voorwaarde) evalueert, gebruik de voorwaarde-actie constructie of het wanneer regeltype. Op dezelfde manier gebruikt u de handeling-voorwaarde constructie of toont of verbergt regeltype op gebied A.

* Soms moet u meerdere handelingen uitvoeren op basis van één voorwaarde. In dergelijke gevallen wordt aangeraden de voorwaarde-actieconstruct te gebruiken. In deze constructie, kunt u een voorwaarde eens evalueren en veelvoudige actieverklaringen specificeren.

  Als u bijvoorbeeld velden B, C en D wilt verbergen op basis van de voorwaarde die controleert of de waarde is opgegeven in veld A, schrijft u één regel met een construct voor voorwaarde-actie of wanneer-regeltype op veld A en geeft u handelingen op om de zichtbaarheid van velden B, C en D te bepalen. Anders hebt u drie aparte regels nodig voor de velden B, C en D, waar elke regel de voorwaarde controleert en het desbetreffende veld weergeeft of verbergt. In dit voorbeeld is het efficiënter om het regeltype Wanneer op één object te schrijven in plaats van het regeltype Tonen of Verbergen op drie objecten.

* Als u een actie wilt activeren op basis van meerdere voorwaarden, kunt u het beste een handeling-voorwaarde-construct gebruiken. Als u bijvoorbeeld veld A wilt weergeven en verbergen door de voorwaarden in de velden B, C en D te evalueren, gebruikt u het regeltype Tonen of Verbergen in veld A.
* Gebruik een voorwaarde-handeling of handeling als de regel één handeling voor één voorwaarde bevat.
* Als een regel op een voorwaarde controleert en een actie onmiddellijk bij het verstrekken van een waarde op een gebied of het weggaan van een gebied uitvoert, wordt het geadviseerd om een regel met een voorwaarde-actie constructie of het wanneer regeltype op het gebied te schrijven waarop de voorwaarde wordt geëvalueerd.
* De voorwaarde in wanneer regel wordt geëvalueerd wanneer een gebruiker de waarde van het voorwerp verandert waarop wanneer regel wordt toegepast. Als u echter wilt dat de actie wordt geactiveerd wanneer de waarde aan de serverzijde verandert, bijvoorbeeld bij het vooraf invullen van de waarde, kunt u het beste een When-regel schrijven die de actie activeert wanneer het veld wordt geïnitialiseerd.
* Wanneer u regels schrijft voor vervolgkeuzelijsten, keuzerondjes of selectievakjes, worden de opties of waarden van deze formulierobjecten in het formulier vooraf ingevuld in de regeleditor.

## Volgende stap

Om te begrijpen hoe te om het gebruikersinterface voor het schrijven van en het leiden van regels in een Redacteur van de Regel te gebruiken, verwijs naar het [ Gebruikersinterface van de Redacteur van de Regel voor Aangepast Forms dat op het artikel van de Componenten van de Kern wordt gebaseerd ](/help/forms/rule-editor-core-components-user-interface.md).

## Zie ook

{{see-also-rule-editor}}