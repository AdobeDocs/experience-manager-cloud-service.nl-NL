---
title: Levering van activa in Experience Manager beperken
description: Leer hoe u de levering van middelen kunt beperken in [!DNL Experience Manager].
role: User
source-git-commit: 540aa876ba7ea54b7ef4324634f6c5e220ad19d3
workflow-type: tm+mt
source-wordcount: '1051'
ht-degree: 0%

---

# Toegang tot elementen in [!DNL Experience Manager] {#restrict-access-to-assets}

Centrale beheer van bedrijfsmiddelen in Experience Manager stelt de DAM-beheerder of -bedrijfsleiders in staat de toegang tot bedrijfsmiddelen te beheren. Zij kunnen de toegang beperken door rollen voor goedgekeurde activa aan de auteurskant, specifiek op de auteursinstantie van AEM as a Cloud Service te vormen.

Gebruikers [zoeken](search-assets-api.md) of gebruiken [bezorgings-URL&#39;s](deliver-assets-apis.md) toegang kan krijgen tot beperkte activa wanneer het goedkeuringsproces met succes wordt goedgekeurd.

![Beperkte toegang tot activa](/help/assets/assets/restricted-access.png)

## Beperkte levering met een IMS-token {#restrict-delivery-ims-token}

In de Experience Manager bestaat een beperkte levering via IMS uit twee belangrijke stappen:

* Authoring
* Aflevering

### Authoring {#authoring}

U kunt de levering van elementen beperken binnen [!DNL Experience Manager] gebaseerd op rollen. Voer de volgende stappen uit om rollen te configureren:

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
   >Voor de nieuwe Assets-weergave kunt u alleen toegang verlenen tot het mapniveau en alleen tot groepen in plaats van individuele gebruikers. Meer informatie over [machtigingen beheren in Experience Manager Assets](https://experienceleague.adobe.com/en/docs/experience-manager-assets-essentials/help/get-started-admins/folder-access/manage-permissions).

   >[!VIDEO](https://video.tv.adobe.com/v/3427429)

#### Levering van activa beperken met de datum en tijd Aan en Uit {#restrict-delivery-assets-date-time}

DAM-auteurs kunnen ook de levering van activa beperken door een Aan- of Uit-tijd voor activering te definiëren die beschikbaar is in Asset-eigenschappen.

Als u een Aan-tijd definieert voor activering van een element, wordt op het gedefinieerde tijdstip een leverings-URL voor het element gegenereerd. Het element blijft vóór de gedefinieerde tijd inactief. Als u een &#39;Off time&#39; definieert voor een element, wordt het element op het gedefinieerde tijdstip gedeactiveerd en wordt de leverings-URL voor het element niet meer weergegeven.

Voer de volgende stappen uit om de aan- en uittijd voor het element in te stellen:

1. Selecteer het element en klik op **[!UICONTROL Properties]**.

1. In de **[!UICONTROL Scheduled (de) activation]** van de **[!UICONTROL Basic]** op basis van uw vereisten de Aan-tijd of de Uit-tijd definiëren.

Op dezelfde manier kunt u in de Assets-weergave het element selecteren en op **[!UICONTROL Details]** om de eigenschappen van elementen weer te geven en de opties Op tijd en Uit te definiëren.

Het veld is beschikbaar in het standaardmetagegevensformulier. Als uw element niet is gebaseerd op het standaardmetagegevensschema en de velden Aan tijd en Uit tijd niet beschikbaar zijn in de eigenschappen van het element, voert u de volgende stappen uit in de beheerweergave:

1. Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**.
1. Selecteer het metagegevensschema en klik op **[!UICONTROL Edit]**.
1. Voeg een **[!UICONTROL Date]** veld van de **[!UICONTROL Build Form]** in de rechterkant van de sectie Metagegevens in het formulier.
1. Klik op het veld dat u zojuist hebt toegevoegd en voer de volgende updates uit in het dialoogvenster  **[!UICONTROL Settings]** paneel:
   1. Wijzig de **[!UICONTROL Field Label]** tot **Op tijd** of **Uit-tijd**.
   1. Werk de **[!UICONTROL Map to property]** tot _./jcr:content/onTime_ for **Op tijd** veld en _./jcr:content/offTime_ for **Uit-tijd** veld.
1. Klik op **[!UICONTROL Save]**.

Op dezelfde manier voert u voor de weergave Assets de volgende stappen uit als uw element niet is gebaseerd op het standaardmetagegevensschema en de velden Aan tijd en Uit tijd niet beschikbaar zijn in de eigenschappen van het element:

1. Klikken **[!UICONTROL Metadata Forms]** in de **[!UICONTROL Settings]** sectie.
1. Selecteer het metagegevensformulier en klik op **[!UICONTROL Edit]**.
1. Voeg een **[!UICONTROL Date]** veld van de **[!UICONTROL Components]** in het linkerdeelvenster naar het formulier.
1. Klik op het nieuwe veld en wijzig de instelling **[!UICONTROL Label]** tot **Op tijd** of **Uit-tijd**.
1. Werk de **[!UICONTROL Metadata property]** tot _./jcr:content/onTime_ for **Op tijd** veld en _./jcr:content/offTime_ for **Uit-tijd** veld.
1. Klik op **[!UICONTROL Save]**.



### Levering van beperkte activa {#delivery-restricted-assets}

De levering van beperkte activa is gebaseerd op een geslaagde toelating tot activa. De autorisatie is gebaseerd op een IMS-token als het verzoek wordt verzonden van een AEM auteur of Asset Selector, of is gebaseerd op een speciaal cookie als u aangepaste identiteitsproviders hebt ingesteld op uw Publish- of Preview-instantie.

#### Levering voor AEM auteur- of Asset Selector-aanvragen {#delivery-aem-author-asset-selector}

Om de levering van beperkte activa toe te laten in het geval dat het verzoek van AEM auteursinstantie of de Selecteur van Activa wordt verzonden, is een geldig symbolisch IMS essentieel. Voer de volgende stappen uit:

1. [Een toegangstoken genereren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token).
   * Meld u aan bij de Dev Console van uw AEM as a Cloud Service-omgeving.

   * Navigeren naar **[!UICONTROL Environment]** > **[!UICONTROL Integrations]** > **[!UICONTROL Local Token]** > **[!UICONTROL Get Local Development Token]** > **[!UICONTROL Copy accessToken value]**. Meer informatie over [hoe te om tot token en verwante aspecten toegang te hebben](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token)

1. Integreer de verkregen toegangstoken aan **[!UICONTROL Authorization]** header, zodat de waarde ervan vooraf gaat **[!UICONTROL Bearer]**.

1. Valideer de functionaliteit van het toegangstoken door een verzoek in werking te stellen. Het zou een fout 404 in gevallen moeten opleveren waar er geen toegangstoken IMS is, of het verstrekte toegangstoken heeft de zelfde principes of de groepen die in de meta-gegevens van het middel worden toegevoegd.

#### Levering voor aangepaste identiteitsproviders op Publish-instantie {#delivery-custom-identity-provider}

Als een aangepaste identiteitsprovider is ingesteld op uw Publish- of Preview-instantie, kunt u de groep noemen die toegang moet hebben tot beveiligde elementen binnen `groupMembership` tijdens het installatieproces. Wanneer u zich via [SAML-integratie](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/saml-2-0)de `groupMembership` wordt gelezen en gebruikt om een cookie samen te stellen die in alle verzoeken om verificatie wordt verzonden, vergelijkbaar met een IMS-token in het geval van een verzoek van AEM auteur of Asset Selector.

Wanneer een beveiligd element beschikbaar is op een pagina en er een aanvraag wordt gedaan naar de leverings-URL om het element te renderen, controleert AEM de rollen in het cookie of de IMS-token en past het aan met de `dam:roles property` toegepast tijdens het ontwerpen van het actief. Als er een overeenkomst is, wordt het element weergegeven.

>[!NOTE]
>
> In de [supportticket waarmee Dynamic Media met OpenAPI-mogelijkheden wordt geactiveerd](/help/assets/dynamic-media-open-apis-overview.md#how-to-enable-the-dynamic-media-with-openapi-capabilities), vermeld beperkte levering in het geval van gebruik. De Techniek van de Adobe zal met noodzakelijke verduidelijkingen en/of opstellingsproces voor beperkte levering helpen.
