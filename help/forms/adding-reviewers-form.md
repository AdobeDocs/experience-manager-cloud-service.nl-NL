---
title: Verzendrevisoren koppelen aan een formulier
seo-title: Associating submission reviewers with a form
description: Leer hoe u revisoren voor verzending aan een formulier kunt koppelen in [!DNL AEM Forms]. Gekoppelde revisoren reviseren een formulier dat via de portal Formulieren is verzonden.
seo-description: Learn how to associate submission reviewers with a form in [!DNL AEM Forms]. Associated reviewers review a form submitted via forms portal.
uuid: 58c8c8fb-9262-4c37-b9b2-e46fe21b77d9
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 71d1aa10-d191-49bc-a50f-1098324f1cfe
docset: aem65
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---


# Verzendrevisoren koppelen aan een formulier {#associating-submission-reviewers-with-a-form}

Wanneer u een formulier maakt, kunt u gebruikers die de verzendingen van het formulier bekijken, via de portal Formulieren opgeven en feedback geven. Uw organisatie kan feedback verzamelen en de ingediende formulieren opnieuw bewerken.

[!DNL AEM Forms] Hiermee kunt u een revisorgroep aan een formulier koppelen. Gebruikers die aan een revisiegroep van een formulier zijn toegevoegd, zien de verzendingen van dit formulier en geven feedback.

Revisieersgroepen die aan een formulier zijn toegewezen, kunnen alleen de verzendingen van het opgegeven formulier bekijken.

## Vereiste {#prerequisite}

### Groepseigenschap van de revisorgroep voor verzending inschakelen voor Adaptief Forms met behulp van schema-editor voor metagegevens {#enabling-submission-reviewer-groups-property-for-adaptive-forms-using-metadata-schema-editor}

Als u een revisorgroep aan een formulier wilt koppelen, bewerkt u het metagegevensschema van Adaptive Forms. Standaard kunt u geen revisorgroep toevoegen aan een verzonden formulier.

Het schema voor metagegevens bewerken:

1. Klik in de modus Schrijver onder Experience Manager op **Gereedschappen** > **Activa** > **Metagegevensschema&#39;s**.
1. Navigeer op de pagina Schema Forms naar **Forms** > **Forms Authored in AEM.**

   De URL van de pagina is:

   ```html
   https://<hostname>:<port>/mnt/overlay/dam/gui/content/metadataschemaeditor/
    schemalist.html/forms/aem-authored
   ```

1. Selecteren **Adaptief formulier** en klik op **Bewerken**.
1. Klik op de pagina Formulier bewerken op **Geavanceerd**.
1. Op het tabblad Geavanceerd kunt u de knop **Tekst met één regel** -component beschikbaar onder Formulier samenstellen.
1. Selecteer de toegevoegde tekstcomponent om zijn montages te zien.

   Voer onder Instellingen `./jcr:content/metadata/form-submission-reviewer-group` in het veld Toewijzen aan eigenschap.

   Het groepsveld Verzendrevisor in de eigenschappen Geavanceerd van het adaptieve formulier wordt ingeschakeld met de naam die u opgeeft onder Veldlabel.

## Verzendrevisoren koppelen aan een formulier {#associating-submission-reviewers-with-a-form-1}

Als u revisoren wilt koppelen aan een adaptief formulier, maakt u een revisorgroep en voegt u gebruikers toe. Voeg de gemaakte revisorgroep toe onder het veld revisor voor formulierverzending in de geavanceerde eigenschappen van het formulier.
Met gebruikersgroepen kunt u verschillende sets revisoren aan verschillende Adaptieve Forms koppelen. Met deze functie voorkomt u dat een niet-geautoriseerde gebruiker een verzendcontrole uitvoert.

Voordat u de volgende stappen uitvoert, raadpleegt u [Vereiste](adding-reviewers-form.md#prerequisite).

Als u een groep wilt maken en er leden aan wilt toevoegen, navigeert u naar **Gereedschappen** > **Bewerkingen** > **Beveiliging** > **Groepen**.
Zie voor meer informatie [Gebruikersbeheer en services](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html).
Zorg ervoor dat u de groep toevoegt u als lid van de uit-van-de-doos gebruikersgroep creeert: **formulierverzendingsrevisoren**. Deze gebruikersgroep wordt geleverd bij [!DNL AEM Forms]en zorgt ervoor dat gebruikers worden toegevoegd als revisoren voor verzending.

Gebruikersgroepen koppelen aan een adaptief formulier:

1. Navigeer in de ontwerpmodus naar **Forms** > **Forms &amp; Documenten**.
1. Selecteer een adaptief formulier met de optie **Selecteren **Selecteren en klik op **Eigenschappen weergeven**.
1. Klik in het venster Eigenschappen van het formulier op **Bewerken** en klik vervolgens op **GEAVANCEERD**.
1. Voer de groep in het groepsveld voor de revisorgroep voor verzending in en klik op **Gereed**.

   Het groepsveld Verzendrevisor wordt weergegeven met de naam die u hebt opgegeven in het bewerkte metagegevensschema van Adaptive Forms.

>[!NOTE]
>
>Repliceer gebruikers en formulieren om ervoor te zorgen dat de gebruikers en formulieren beschikbaar zijn in de externe implementatie van [!DNL AEM Forms].
>
>Zorg ervoor dat alle gebruikers worden gerepliceerd als reviserende leden van de gebruikersgroepen in de externe implementatie.

