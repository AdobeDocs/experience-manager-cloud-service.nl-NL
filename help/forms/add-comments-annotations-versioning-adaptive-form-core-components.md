---
title: Voeg versies, opmerkingen en annotaties toe aan een formulier.
description: Gebruik aangepaste basiscomponenten van formulieren om opmerkingen, annotaties en versies toe te voegen aan een adaptief formulier.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Adaptive Forms, Core Components
exl-id: 84b95a19-c804-41ad-8f4b-5868c8444cc0
role: User, Developer, Admin
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 0%

---

# Versioning, revisie en opmerkingen op een adaptief formulier

<!--Before you can use versionings, comments, and annotations in an Adaptive Form, you must ensure you have [enabled Adaptive Form Core Components](
https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/enable-adaptive-forms-core-components).-->

<!--Adaptive Form Core Components facilitates to add versionings, comments, and annotations to a form. These features helps form authors and users to enhance the form development process where they can create multiple versions of a form, collaborate and add their comments to a form, and add annotations to form components.-->

<span class="preview"> Dit is een pre-release functie die toegankelijk is via onze [pre-releasekanaal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features). </span>


Aangepaste componenten van Form Core bieden functionaliteit waarmee auteurs van formulieren versioning, opmerkingen en annotaties kunnen opnemen in formulieren. Deze functies zijn bedoeld om het formulierontwikkelingsproces te stroomlijnen door gebruikers toe te staan meerdere versies van een formulier te maken en te beheren, door middel van opmerkingen aan samenwerkingsbesprekingen deel te nemen en annotaties toe te voegen aan specifieke formuliercomponenten, waardoor de algehele ervaring met het maken van formulieren wordt vergroot.


## Adaptieve formulierversie {#adaptive-form-versioning}

Met een adaptieve formulierversie kunt u versies toevoegen aan een formulier. Formulierauteurs kunnen eenvoudig meerdere versies van een formulier maken en ten slotte het formulier gebruiken dat geschikt is voor de zakelijke doelstellingen. Daarnaast kunnen gebruikers van formulieren het formulier ook terugzetten naar vorige versies. Het vergemakkelijkt auteurs ook om het even welke twee versies van een vorm te vergelijken door hen te previewing, die hen toestaan om vormen uit perspectief UI beter te analyseren. Laten we in detail gaan voor elke adaptieve functionaliteit voor formulierversies:

### Een formulierversie maken {#create-a-form-version}

Voer de volgende stappen uit om een versie van een formulier te maken:

1. Maak een formulier of gebruik een bestaand formulier.
1. Navigeer in AEM UI naar de **[!UICONTROL Form]**>>**[!UICONTROL Forms & Documents]** en selecteer uw **Formulier**.
1. Selecteer in het keuzemenu Selectie in het linkerdeelvenster de optie **[!UICONTROL Versions]**.
   ![Een formulier selecteren](select-a-form.png)
1. Klik op de knop **drie stippen** in het onderste deelvenster aan de linkerkant klikt u op **[!UICONTROL Save as Version]**.
1. Geef nu een label op voor de formulierversie en u kunt informatie over het formulier geven via de opmerking.
   ![Een formulierversie maken](create-a-form-version.png)

### Een formulierversie bijwerken {#update-a-form-version}

Wanneer u het aangepaste formulier bewerkt en bijwerkt, voegt u een nieuwe versie aan het formulier toe. Voer de stappen in de laatste sectie uit om een nieuwe versie van het formulier een naam te geven, zoals wordt weergegeven in de afbeelding:

![Een formulierversie bijwerken](update-a-form-version.png)

### Een formulierversie herstellen {#revert-a-form-version}

Als u de vorige versie van een formulier wilt herstellen, selecteert u een formulierversie en klikt u op **[!UICONTROL Revert to this Version]**.

![Formulierversie herstellen](revert-form-version.png)

### Formulierversies vergelijken {#compare-form-versions}

Formulierauteurs kunnen twee verschillende versies van een formulier vergelijken voor voorbeelddoeleinden. Als u versies wilt vergelijken, selecteert u een formulierversie en klikt u op **[!UICONTROL Compare to Current]**. Er worden twee verschillende formulierversies weergegeven in de voorbeeldmodus.

![Formulierversies vergelijken](compare-form-versions.png)

## Opmerkingen toevoegen {#add-comments}

Een revisie is een mechanisme waarmee een of meer revisoren opmerkingen op formulieren kunnen plaatsen. Elke gebruiker van het formulier kan opmerkingen plaatsen op een formulier of een formulier reviseren via opmerkingen. Als u opmerkingen wilt toevoegen aan een formulier, selecteert u een **[!UICONTROL Form]** en voegt een **[!UICONTROL Comment]** op het formulier.

>[!NOTE]
> Als u opmerkingen gebruikt in de componenten van adaptieve formulieren, zoals hierboven is beschreven, moet u de formulierfunctionaliteit [Revisies maken en beheren op formulieren](/help/forms/create-reviews-forms.md) is uitgeschakeld.


![Opmerkingen toevoegen aan een formulier](form-comments.png)

## Annotaties toevoegen {#adaptive-form-annotations}

In veel gevallen moeten gebruikers van een formuliergroep annotaties toevoegen aan een formulier voor revisiedoeleinden, bijvoorbeeld op een specifiek tabblad van een formulier of onderdelen van een formulier. In dergelijke gevallen kunnen auteurs annotaties gebruiken. Voer de volgende stappen uit om notities aan een formulier toe te voegen:

1. Een formulier openen in het dialoogvenster **[!UICONTROL Edit]** -modus.

1. Klik op de knop **pictogram toevoegen** die zich op de rechterbovenspoorstaaf bevinden, zoals aangegeven in de afbeelding.
   ![Aantekening](annotation.png)

1. Klik op de knop **pictogram toevoegen** die zich op de linkerbovenspoorstaaf bevinden zoals in het beeld wordt gegeven om de aantekening toe te voegen.
   ![Annotatie toevoegen](add-annotation.png)

1. Nu kunt u opmerkingen toevoegen en schetsen met meerdere kleuren tekenen in formuliercomponenten.

1. Als u alle toegevoegde aantekeningen op een formulier wilt bekijken, selecteert u het formulier en ziet u de aantekeningen die aan de linkerkant zijn toegevoegd, zoals in de afbeelding wordt getoond.

   ![Zie toegevoegde annotaties](see-annotations.png)

## Zie ook {#see-also}

{{see-also}}
