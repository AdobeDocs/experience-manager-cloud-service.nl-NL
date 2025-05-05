---
title: Pagina's maken
description: Leer hoe u nieuwe pagina's voor uw website maakt met de Sites-console.
exl-id: 77264562-e76a-40c8-9878-847a8878fb8e
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---


# Pagina&#39;s maken {#creating-pages}

Leer hoe te om nieuwe pagina&#39;s voor uw website tot stand te brengen gebruikend de **console van Plaatsen**.

>[!TIP]
>
>Alvorens u begint creërend nieuwe pagina&#39;s, wordt vertrouwd met [ hoe uw pagina&#39;s in AEM ](/help/sites-cloud/authoring/sites-console/organizing-pages.md) worden georganiseerd.

## Toegangsrechten {#access-privileges}

Uw account heeft de juiste toegangsrechten en machtigingen nodig om pagina&#39;s te maken.

Neem contact op met de systeembeheerder als u problemen ondervindt.

## Een nieuwe pagina maken {#creating-a-new-page}

Tenzij alle pagina&#39;s van tevoren voor u zijn gemaakt, moet u een pagina maken voordat u inhoud kunt gaan maken:

1. Open [ de **2&rbrace; console van Plaatsen ](/help/sites-cloud/authoring/sites-console/introduction.md).**
1. Navigeer naar de locatie waar u de nieuwe pagina wilt maken.
1. Open de drop-down selecteur gebruikend **creeer** in de toolbar, dan selecteer **Pagina** van de lijst:

   ![ Creërend een pagina ](/help/sites-cloud/authoring/assets/organizing-create-page.png)

1. Vanaf de eerste fase van de wizard kunt u:

   * Selecteer het malplaatje u wilt gebruiken om de nieuwe pagina tot stand te brengen, dan selecteren **daarna** te werk te gaan of **annuleert** om het proces af te breken.
   * De malplaatjes worden gesteund voor zowel de [ Redacteur van de Pagina ](/help/sites-cloud/authoring/page-editor/introduction.md) als voor de [ Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/templates.md).

   ![ Selecterend een malplaatje voor een nieuwe pagina ](/help/sites-cloud/authoring/assets/organizing-create-page-template.png)

1. Vanaf het laatste werkgebied van de wizard kunt u:

   * Gebruik de drie lusjes om de [ paginaeigenschappen ](/help/sites-cloud/authoring/sites-console/page-properties.md) in te gaan u aan de nieuwe pagina wilt worden toegewezen, dan **creeer** om de pagina eigenlijk tot stand te brengen.

   * Het gebruik **terug** om op malplaatjeselectie terug te keren.

   Hoofdvelden zijn:

   * **Titel**:

      * Dit wordt aan de gebruiker getoond en is verplicht.

   * **Naam**:

      * Hiermee wordt de URI gegenereerd. Indien niet opgegeven, wordt de naam afgeleid van de titel.
      * Als u een pagina **Naam** wanneer het creëren van een pagina levert, AEM [ bevestigt de naam volgens de overeenkomsten ](/help/implementing/developing/introduction/naming-conventions.md) die door AEM en JCR worden opgelegd.
      * U **kunt geen ongeldige karakters** op het **gebied van de Naam** voorleggen. Wanneer AEM ongeldige tekens detecteert, wordt het veld gemarkeerd en wordt een verklarende melding weergegeven om aan te geven welke tekens moeten worden verwijderd/vervangen.

   >[!TIP]
   >
   >Zie [ Pagina noemende Conventies ](#page-naming-conventions).

   De minimuminformatie die wordt vereist om een pagina tot stand te brengen is de **Titel**.

   ![ Verstrekkend paginatitel ](/help/sites-cloud/authoring/assets/organizing-create-page-title.png)

1. Tik of klik **creeer** om het proces te voltooien en uw nieuwe pagina tot stand te brengen. De bevestigingsdialoog vraagt of u **&#x200B;**&#x200B;de pagina onmiddellijk wilt openen of aan de console terugkeren (**Gedaan**). Selecteer een optie om het maken van de pagina te beëindigen.

   ![ de aanmaaksucces van de pagina ](/help/sites-cloud/authoring/assets/organizing-create-page-success.png)

   * Als u **Open** kiest, opent de **console van Plaatsen** de aangewezen die redacteur op het malplaatje van de nieuwe pagina wordt gebaseerd, of:
      * [De pagina-editor](/help/sites-cloud/authoring/page-editor/introduction.md)
      * [De Universal Editor](/help/sites-cloud/authoring/universal-editor/authoring.md)

Als u terugkeert naar de console, kunt u uw nieuwe pagina zien:

![ Resulterend nieuwe pagina ](/help/sites-cloud/authoring/assets/organizing-create-page-result.png)

>[!NOTE]
>
>Als u een pagina maakt met een naam die al op dezelfde locatie bestaat, maakt AEM de pagina met een variatie in de opgegeven naam door een nummer toe te voegen. Als `beach` bijvoorbeeld al bestaat, wordt de nieuwe pagina `beach1` .

>[!CAUTION]
>
>Zodra een pagina is gecreeerd, kan zijn malplaatje niet worden veranderd tenzij u [ creeert een lancering met een nieuw malplaatje ](/help/sites-cloud/authoring/launches/creating.md#create-launch-with-new-template), hoewel dit om het even welke bestaande inhoud zal verliezen.
