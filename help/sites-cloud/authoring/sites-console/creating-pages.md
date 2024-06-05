---
title: Pagina's maken
description: Leer hoe u nieuwe pagina's voor uw website maakt met de Sites-console.
exl-id: 77264562-e76a-40c8-9878-847a8878fb8e
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Pagina&#39;s maken {#creating-pages}

Leer hoe u met de **Sites** console.

>[!TIP]
>
>Voordat u begint met het maken van nieuwe pagina&#39;s, moet u vertrouwd raken met [hoe uw pagina&#39;s in AEM worden ingedeeld.](/help/sites-cloud/authoring/sites-console/organizing-pages.md)

## Toegangsrechten {#access-privileges}

Uw account heeft de juiste toegangsrechten en machtigingen nodig om pagina&#39;s te maken.

Neem contact op met de systeembeheerder als u problemen ondervindt.

## Een nieuwe pagina maken {#creating-a-new-page}

Tenzij alle pagina&#39;s van tevoren voor u zijn gemaakt, moet u een pagina maken voordat u inhoud kunt gaan maken:

1. Openen [de **Sites** console.](/help/sites-cloud/authoring/sites-console/introduction.md)
1. Navigeer naar de locatie waar u de nieuwe pagina wilt maken.
1. De keuzelijst openen met **Maken** in de werkbalk selecteert u vervolgens **Pagina** in de lijst:

   ![Een pagina maken](/help/sites-cloud/authoring/assets/organizing-create-page.png)

1. Vanaf de eerste fase van de wizard kunt u:

   * Selecteer de sjabloon die u wilt gebruiken om de nieuwe pagina te maken en selecteer vervolgens **Volgende** om verder te gaan.

   * **Annuleren** om het proces af te breken.

   ![Een sjabloon voor een nieuwe pagina selecteren](/help/sites-cloud/authoring/assets/organizing-create-page-template.png)

1. Vanaf het laatste werkgebied van de wizard kunt u:

   * Gebruik de drie tabbladen om de [pagina-eigenschappen](/help/sites-cloud/authoring/sites-console/page-properties.md) u wilt toewijzen aan de nieuwe pagina en selecteert u vervolgens **Maken** om de pagina te maken.

   * Gebruiken **Vorige** om terug te keren naar de sjabloonselectie.

   Hoofdvelden zijn:

   * **Titel**:

      * Dit wordt aan de gebruiker getoond en is verplicht.

   * **Naam**:

      * Hiermee wordt de URI gegenereerd. Indien niet opgegeven, wordt de naam afgeleid van de titel.
      * Als u een pagina **Naam** bij het maken van een pagina, AEM [valideert de naam volgens de conventies](/help/implementing/developing/introduction/naming-conventions.md) opgelegd door AEM en JCR.
      * U **kan geen ongeldige tekens verzenden** in de **Naam** veld. Wanneer AEM ongeldige tekens detecteert, wordt het veld gemarkeerd en wordt een verklarende melding weergegeven om aan te geven welke tekens moeten worden verwijderd/vervangen.

   >[!TIP]
   >
   >Zie [Naamgevingsconventies voor pagina](#page-naming-conventions).

   De minimale informatie die nodig is om een pagina te maken, is de **Titel**.

   ![Paginatitel opgeven](/help/sites-cloud/authoring/assets/organizing-create-page-title.png)

1. Tik of klik op **Maken** om het proces te voltooien en uw nieuwe pagina te maken. In het bevestigingsvenster wordt u gevraagd of u **Openen** de pagina direct of terug naar de console (**Gereed**). Selecteer een optie om het maken van de pagina te beëindigen.

   ![Maken van pagina voltooid](/help/sites-cloud/authoring/assets/organizing-create-page-success.png)

   * Als u **Openen** de **Sites** De console opent de aangewezen redacteur die op het malplaatje van de nieuwe pagina wordt gebaseerd, of:
      * [De pagina-editor](/help/sites-cloud/authoring/page-editor/introduction.md)
      * [De Universal Editor](/help/sites-cloud/authoring/universal-editor/authoring.md)

Als u terugkeert naar de console, kunt u uw nieuwe pagina zien:

![Resulterende nieuwe pagina](/help/sites-cloud/authoring/assets/organizing-create-page-result.png)

>[!NOTE]
>
>Als u een pagina maakt met een naam die al op dezelfde locatie bestaat, maakt AEM de pagina met een variatie in de opgegeven naam door een nummer toe te voegen. Als `beach` bestaat al. De nieuwe pagina wordt `beach1`.

>[!CAUTION]
>
>Nadat een pagina is gemaakt, kan de sjabloon ervan alleen worden gewijzigd als u [een lancering met een nieuw malplaatje creëren](/help/sites-cloud/authoring/launches/creating.md#create-launch-with-new-template), hoewel de bestaande inhoud hierdoor verloren zal gaan.
