---
title: Levering van activa in Experience Manager beperken
description: Leer hoe u de levering van middelen kunt beperken in [!DNL Experience Manager].
role: User
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---

# Toegang tot elementen in [!DNL Experience Manager] {#restrict-access-to-assets}

Centrale beheer van bedrijfsmiddelen in Experience Manager stelt de DAM-beheerder of -bedrijfsleiders in staat de toegang tot bedrijfsmiddelen te beheren. Zij kunnen de toegang beperken door rollen voor goedgekeurde activa aan de auteurskant, specifiek op de AEM as a Cloud Service auteursinstantie te vormen.

Gebruikers [zoeken](search-assets-api.md) of gebruiken [bezorgings-URL&#39;s](deliver-assets-apis.md) toegang kan krijgen tot beperkte activa wanneer het goedkeuringsproces met succes wordt goedgekeurd.

![Beperkte toegang tot activa](/help/assets/assets/restricted-access.png)

## Beperkte levering met een IMS-token {#restrict-delivery-ims-token}

In de Experience Manager bestaat een beperkte levering via IMS uit twee belangrijke stappen:

* Authoring
* Aflevering

### Authoring {#authoring}

Om de levering van activa te beperken, moeten de rollen voor de activa binnen worden gevormd [!DNL Experience Manager] of [!DNL Experience Manager Assets]. Om rollen te vormen binnen [!DNL Experience Manager]Voer de volgende stappen uit:

1. Ga naar de [!DNL Experience Manager] als DAM-beheerder.
1. Selecteer de activa waarvoor u de rol moet vormen.
1. Navigeren naar **[!UICONTROL Properties]** > **[!UICONTROL Advanced]** en ervoor zorgen dat de **[!UICONTROL Roles]** bestaat in het veld [!UICONTROL Advanced Metadata] tab.

   ![Metagegevens rollen](/help/assets/assets/roles_metadata.jpg)
Als het veld niet beschikbaar is, voert u de volgende stappen uit om het veld toe te voegen:

   1. Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**.
   1. Selecteer het metagegevensschema en klik op **[!UICONTROL Edit _e)_]**.
   1. Voeg een **[!UICONTROL Multi Value Text]** veld van de **[!UICONTROL Build Form]** in de rechterkant van de sectie Metagegevens in het formulier.
   1. Klik op het veld dat u zojuist hebt toegevoegd en voer de volgende updates uit in het dialoogvenster  **[!UICONTROL Settings]** paneel:
      1. Wijzig de **[!UICONTROL Field Label]** tot _Rollen_.
      1. Werk de **[!UICONTROL Map to property]** tot _./jcr:content/metadata/dam:rollen_.

1. Haal de IMS-groepen op die moeten worden toegevoegd aan de metagegevens voor rollen van het element. Voer de volgende stappen uit om de IMS-groepen op te halen:
   1. Aanmelden bij https://adminconsole.adobe.com/.
   1. Ga naar uw respectievelijke organisatie en navigeer naar **[!UICONTROL User Groups]**.
   1. Selecteer de **[!UICONTROL User Group]** u moet toevoegen, en halen **[!UICONTROL orgID]** en **[!UICONTROL userGroupID]** van de URL of gebruik uw organisatie-id, zoals `{orgID}@AdobeOrg:{usergroupID}`.

1. Groeps-id toevoegen aan de **[!UICONTROL Roles]** veld Eigenschappen van element. <br>
De groep-id&#39;s die zijn gedefinieerd in het dialoogvenster **[!UICONTROL Roles]** alleen gebruikers hebben toegang tot het middel . U kunt ook IMS-client-id en IMS-profiel-id toevoegen in het dialoogvenster **[!UICONTROL Roles]** veld. Bijvoorbeeld: `{orgId}@AdobeOrg:{profileId}`.

   >[!NOTE]
   >
   >Voor de nieuwe middelenweergave kunt u alleen toegang verlenen tot het mapniveau en uitsluitend tot groepen in plaats van individuele gebruikers. Meer informatie over [machtigingen beheren in Experience Manager Assets](https://experienceleague.adobe.com/en/docs/experience-manager-assets-essentials/help/get-started-admins/folder-access/manage-permissions).

   >[!VIDEO](https://video.tv.adobe.com/v/3427429)

### Levering van beperkte activa {#delivery-restricted-assets}

De levering van beperkte activa is gebaseerd op een geslaagde toelating tot activa. De autorisatie is gebaseerd op een IMS-token als de aanvraag is verzonden van een AEM auteur of Asset Selector, of is gebaseerd op een speciaal cookie als u aangepaste identiteitsproviders hebt ingesteld in uw instantie Publiceren of Voorvertoning.

#### Levering voor AEM auteur of Asset Selector {#delivery-aem-author-asset-selector}

Om de levering van beperkte activa toe te laten in het geval dat het verzoek van AEM auteursinstantie of de Selecteur van Activa wordt verzonden, is een geldig symbolisch IMS essentieel. Voer de volgende stappen uit:

1. [Een toegangstoken genereren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token).
   * Meld u aan bij de Dev Console van uw AEM as a Cloud Service omgeving.

   * Navigeren naar **[!UICONTROL Environment]** > **[!UICONTROL Integrations]** > **[!UICONTROL Local Token]** > **[!UICONTROL Get Local Development Token]** > **[!UICONTROL Copy accessToken value]**. Meer informatie over [hoe te om tot token en verwante aspecten toegang te hebben](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token)

1. Integreer de verkregen toegangstoken aan **[!UICONTROL Authorization]** header, zodat de waarde ervan vooraf gaat **[!UICONTROL Bearer]**.

1. Valideer de functionaliteit van het toegangstoken door een verzoek in werking te stellen. Het zou een fout 404 in gevallen moeten opleveren waar er geen toegangstoken IMS is, of het verstrekte toegangstoken heeft de zelfde principes of de groepen die in de meta-gegevens van het middel worden toegevoegd.

#### Levering voor aangepaste identiteitsproviders {#delivery-custom-identity-provider}

In het geval van een aangepaste identiteitsprovider die is ingesteld op uw instantie Publiceren of Voorvertoning, kunt u de groep noemen die toegang moet hebben tot beveiligde elementen binnen `groupMembership` tijdens het installatieproces. Wanneer u zich via [SAML-integratie](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/saml-2-0)de `groupMembership` wordt gelezen en gebruikt om een cookie samen te stellen die in alle verzoeken om verificatie wordt verzonden, vergelijkbaar met een IMS-token in het geval van een verzoek van AEM auteur of Asset Selector.

Wanneer een beveiligd element beschikbaar is op een pagina en er een aanvraag wordt gedaan naar de leverings-URL om het element te renderen, controleert AEM de rollen in het cookie of de IMS-token en past het aan met de `dam:roles property` toegepast tijdens het ontwerpen van het actief. Als er een overeenkomst is, wordt het element weergegeven.
