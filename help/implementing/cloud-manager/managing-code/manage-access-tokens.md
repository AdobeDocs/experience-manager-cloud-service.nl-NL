---
title: Toegangstokens beheren voor externe opslagplaatsen in Cloud Manager
description: Leer hoe u de toegangstokens die worden gebruikt voor 'Create Your Own Git' in AEM Cloud Manager kunt weergeven, bewerken en verwijderen.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: bc9f392c-61f5-4d39-972b-4c6c8f9bab4a
source-git-commit: 19fd6713e083826bd9aa621d86805bcd55a6743a
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Toegangstokens beheren voor externe opslagruimten {#manage-access-tokens}

<!-- badge: label="Private beta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#manage-access-tokens" -->

Cloud Manager gebruikt toegangstokens om opslagruimten te beheren die op externe Git-platforms worden gehost. Eerder, als een teken verliep, moest de bijbehorende bewaarplaats opnieuw worden geregistreerd om operationeel te blijven.

Nu, laat **de Tokens van de Toegang beheren** eigenschap u tokens efficiënter beheren. U kunt tokens bekijken, anders noemen of verwijderen die aan gesteunde externe leveranciers van de it, met inbegrip van de Onderneming GitHub, GitLab, Bitbucket, en Azure DevOps worden aangesloten.

Zie ook [&#x200B; Externe Bewaarplaatsen in Cloud Manager &#x200B;](/help/implementing/cloud-manager/managing-code/external-repositories.md) toevoegen.

<!--
>[!NOTE]
>
>The features described in this article are only available through the private beta program. For more details and to sign up for the private beta, see [Bring Your Own Git](/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket).
-->

## Toegangstokens weergeven {#view-access-tokens}

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.
1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma waarvan uw eigen toegangstoken van het Git brengt u wilt beheren.
1. In het zijmenu, onder **Programma**, klik ![&#x200B; het overzichtspictogram van de Omslag &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Bewaarplaatsen**.
1. Vlak de hoger-juiste hoek van de pagina, klik **beheert de Tokens van de Toegang**.

   De **beheert de Tokens van de Toegang** knoop is slechts zichtbaar als uw programma uw eigen eigenschap van de it gebruikt.

   ![&#x200B; beheert de dialoogdoos die van de Tokens van de Toegang één teken dat actief is en één teken dat inactief is &#x200B;](/help/implementing/cloud-manager/managing-code/assets/access-tokens-manage.png)

1. In **beheert de Tokens van de Toegang** dialoogdoos:
   * Alle toegangstokens worden vermeld.
   * U kunt **uitgeven** om het even welk toegangstoken.
   * U kunt **schrappen** slechts die toegangstokens die *niet momenteel in gebruik* zijn. Als een teken in gebruik is, is de ![&#x200B; knoop van het het overzichtspictogram van de Schrapping &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg) gehandicapt.

## Een toegangstoken bewerken {#edit-access-tokens}

1. In **beheert de Tokens van de Toegang** dialoogdoos, rechts van een symbolische naam, klik ![&#x200B; uitgeven pictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg).
1. In **geef Token van de Toegang** dialoogdoos uit, werk de **Symbolische Naam**, of de **Symbolische waarde van de Toegang**, of allebei bij.

   ![&#x200B; geef de Token van de Toegang dialoogdoos uit &#x200B;](/help/implementing/cloud-manager/managing-code/assets/access-tokens-edit.png)

1. Als het **Token van de Toegang** momenteel in gebruik is, verschijnt een bericht waarschuwend u dat alle bijbehorende bewaarplaatsen automatisch na de update worden opnieuw bevestigd.

1. Klik **Update** om de veranderingen te bewaren.

## Een toegangstoken verwijderen {#delete-access-token}

1. In **beheer de Tokens van de Toegang** dialoogdoos, rechts van een symbolische naam, klik ![&#x200B; pictogram van de Schrapping &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg)

   Het pictogram is gehandicapt (![&#x200B; schrap overzichtspictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg)) voor tokens die momenteel in gebruik zijn.

1. In het **Symbolische de dialoogvakje van de Toegang van de Schrapping**, klik **Schrapping** om het teken permanent te verwijderen.
