---
title: Hoe een adaptief formulier ter controle verzenden?
description: Een adaptief formulier delen voor revisie met een of meer revisoren.
uuid: 58c8c8fb-9262-4c37-b9b2-e46fe21b77d9
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 71d1aa10-d191-49bc-a50f-1098324f1cfe
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: 937bd4653e454beea3111cfc7ef7b4bbc1ace193
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---


# Verzendrevisoren koppelen aan een formulier {#associating-submission-reviewers-with-a-form}

Wanneer u een formulier maakt, kunt u gebruikers die de verzendingen van het formulier bekijken, via de portal Formulieren opgeven en feedback geven. Uw organisatie kan feedback verzamelen en de ingediende formulieren opnieuw bewerken.

Met [!DNL AEM Forms] kunt u een revisorgroep aan een formulier koppelen. Gebruikers die aan een revisiegroep van een formulier zijn toegevoegd, zien de verzendingen van dit formulier en geven feedback.

Revisieersgroepen die aan een formulier zijn toegewezen, kunnen alleen de verzendingen van het opgegeven formulier bekijken.

## Vereiste {#prerequisite}

### Groepseigenschap van de revisorgroep voor verzending inschakelen voor Adaptief Forms met behulp van schema-editor voor metagegevens {#enabling-submission-reviewer-groups-property-for-adaptive-forms-using-metadata-schema-editor}

Als u een revisorgroep aan een formulier wilt koppelen, bewerkt u het metagegevensschema van Adaptive Forms. Standaard kunt u geen revisorgroep toevoegen aan een verzonden formulier.

Het schema voor metagegevens bewerken:

1. Op de auteurswijze, onder Experience Manager, klik **Hulpmiddelen** > **Assets** > **Schema&#39;s van Meta-gegevens**.
1. In de pagina van Forms van het Schema, navigeer aan **Forms** > **Forms die in AEM wordt geschreven.**

   De URL van de pagina is:

   ```html
   https://<hostname>:<port>/mnt/overlay/dam/gui/content/metadataschemaeditor/
    schemalist.html/forms/aem-authored
   ```

1. Selecteer **Aangepaste Vorm** en klik **uitgeven**.
1. In de Edit pagina van de Vorm, klik **Geavanceerd**.
1. In het Geavanceerde lusje, belemmering-en-daling de **Enige component van de Tekst van de Lijn** beschikbaar onder Bouw Vorm.
1. Selecteer de toegevoegde tekstcomponent om zijn montages te zien.

   Voer onder Instellingen `./jcr:content/metadata/form-submission-reviewer-group` in het veld Toewijzen aan eigenschap in.

   Het groepsveld Verzendrevisor in de eigenschappen Geavanceerd van het adaptieve formulier wordt ingeschakeld met de naam die u opgeeft onder Veldlabel.

## Verzendrevisoren koppelen aan een formulier {#associating-submission-reviewers-with-a-form-1}

Als u revisoren wilt koppelen aan een adaptief formulier, maakt u een revisorgroep en voegt u gebruikers toe. Voeg de gemaakte revisorgroep toe onder het veld revisor voor formulierverzending in de geavanceerde eigenschappen van het formulier.
Met gebruikersgroepen kunt u verschillende sets revisoren aan verschillende Adaptieve Forms koppelen. Met deze functie voorkomt u dat een niet-geautoriseerde gebruiker een verzendcontrole uitvoert.

Alvorens u de volgende stappen uitvoert, zie [ Vereiste ](adding-reviewers-form.md#prerequisite).

Om een groep tot stand te brengen en leden aan het toe te voegen, navigeer aan **Hulpmiddelen** > **Verrichtingen** > **Veiligheid** > **Groepen**.
Voor meer informatie, zie [ Beleid van de Gebruiker en de Diensten ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html?lang=nl-NL).
Zorg ervoor dat u de groep toevoegt u als lid van de uit-van-de-doos gebruikersgroep creeert: **vorm-voorlegging-recensenten**. Deze gebruikersgroep wordt geleverd met [!DNL AEM Forms] en zorgt ervoor dat gebruikers worden toegevoegd als revisoren voor verzending.

Gebruikersgroepen koppelen aan een adaptief formulier:

1. Op de auteurswijze, navigeer aan **Forms** > **Forms &amp; Documenten**.
1. Gebruik **Selecteer &#x200B;** optie om een Aangepaste Vorm te selecteren, en **Eigenschappen van de Mening** te klikken.
1. In het venster van Eigenschappen van de vorm, geeft de klik **&#x200B;**&#x200B;uit, en klikt dan **GEAVANCEERD**.
1. Ga de groep op het gebied van de de vraagcontroleersgroep in, en klik **Gereed**.

   Het groepsveld Verzendrevisor wordt weergegeven met de naam die u hebt opgegeven in het bewerkte metagegevensschema van Adaptive Forms.

>[!NOTE]
>
>Repliceer gebruikers en formulieren om ervoor te zorgen dat de gebruikers en formulieren beschikbaar zijn in de externe implementatie van [!DNL AEM Forms] .
>
>Zorg ervoor dat alle gebruikers worden gerepliceerd als reviserende leden van de gebruikersgroepen in de externe implementatie.

>[!MORELIKETHIS]
>
>* [ Creërend en het leiden overzichten aan vormen ](/help/forms/create-reviews-forms.md)
>* [ creeer en beheer overzichten voor een Aanpassings Vorm ](/help/forms/review-adaptiveforms-in-sites-page.md)