---
title: Levering van activa in Experience Manager beperken
description: Leer hoe te om de levering van activa in  [!DNL Experience Manager] te beperken.
role: User
exl-id: 3fa0b75d-c8f5-4913-8be3-816b7fb73353
source-git-commit: 16b313a4fb79f915613044d12d29e618209113ec
workflow-type: tm+mt
source-wordcount: '1051'
ht-degree: 0%

---

# Toegang tot elementen beperken in [!DNL Experience Manager] {#restrict-access-to-assets}

Centrale beheer van bedrijfsmiddelen in Experience Manager stelt de DAM-beheerder of -bedrijfsleiders in staat de toegang tot bedrijfsmiddelen te beheren. Zij kunnen de toegang beperken door rollen voor goedgekeurde activa aan de auteurskant, specifiek op de auteursinstantie van AEM as a Cloud Service te vormen.

De gebruikers [ die ](search-assets-api.md) zoeken of gebruiken [ levering URLs ](deliver-assets-apis.md) kan toegang tot beperkte activa verkrijgen wanneer met succes het vergunningsproces overgaan.

![ Beperkte toegang tot activa ](/help/assets/assets/restricted-access.png)

## Beperkte levering met een IMS-token {#restrict-delivery-ims-token}

In Experience Manager Assets bestaat een beperkte levering via IMS uit twee belangrijke stappen:

* Authoring
* Aflevering

### Authoring {#authoring}

U kunt de levering van elementen binnen [!DNL Experience Manager] beperken op basis van rollen. Voer de volgende stappen uit om rollen te configureren:

1. Ga naar [!DNL Experience Manager] als DAM-beheerder.
1. Selecteer de activa waarvoor u de rol moet vormen.
1. Ga naar **[!UICONTROL Properties]** > **[!UICONTROL Advanced]** en controleer of het veld **[!UICONTROL Roles]** bestaat op het tabblad [!UICONTROL Advanced Metadata] .

   ![ de meta-gegevens van Rollen ](/help/assets/assets/roles_metadata.jpg)
Als het veld niet beschikbaar is, voert u de volgende stappen uit om het veld toe te voegen:

   1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]** .
   1. Selecteer het meta-gegevensschema en klik **[!UICONTROL Edit _(e)_]**.
   1. Voeg een veld **[!UICONTROL Multi Value Text]** toe van de sectie **[!UICONTROL Build Form]** rechts naar de sectie Metagegevens in het formulier.
   1. Klik op het veld dat u zojuist hebt toegevoegd en voer de volgende updates uit in het deelvenster **[!UICONTROL Settings]** :
      1. Verander **[!UICONTROL Field Label]** in _Rollen_.
      1. Werk **[!UICONTROL Map to property]** aan _bij./jcr:content/metadata/dam:rollen_.

1. Haal de IMS-groepen op die moeten worden toegevoegd aan de metagegevens voor rollen van het element. Voer de volgende stappen uit om de IMS-groepen op te halen:
   1. Aanmelden bij `https://adminconsole.adobe.com/.`
   1. Ga naar uw respectievelijke organisatie en navigeer naar **[!UICONTROL User Groups]** .
   1. Selecteer de **[!UICONTROL User Group]** die u wilt toevoegen en extraheer de **[!UICONTROL orgID]** en **[!UICONTROL userGroupID]** uit de URL of gebruik uw organisatie-id, zoals `{orgID}@AdobeOrg:{usergroupID}` .

1. Voeg de Group-id toe aan het veld **[!UICONTROL Roles]** met de eigenschappen van Asset. <br>
De groep-id&#39;s die in het veld **[!UICONTROL Roles]** zijn gedefinieerd, zijn de enige gebruikers die toegang hebben tot het element. U kunt ook IMS-client-id en IMS-profiel-id toevoegen in het veld **[!UICONTROL Roles]** . Bijvoorbeeld `{orgId}@AdobeOrg:{profileId}` .

   >[!NOTE]
   >
   >Voor de nieuwe Assets-weergave kunt u alleen toegang verlenen tot het mapniveau en alleen tot groepen in plaats van individuele gebruikers. Leer meer over [ het leiden toestemmingen binnen Experience Manager Assets ](https://experienceleague.adobe.com/en/docs/experience-manager-assets-essentials/help/get-started-admins/folder-access/manage-permissions).

   >[!VIDEO](https://video.tv.adobe.com/v/3427429)

#### Levering van activa beperken met de datum en tijd Aan en Uit {#restrict-delivery-assets-date-time}

DAM-auteurs kunnen ook de levering van activa beperken door een Aan- of Uit-tijd voor activering te definiëren die beschikbaar is in Asset-eigenschappen.

Als u een Aan-tijd definieert voor activering van een element, wordt op het gedefinieerde tijdstip een leverings-URL voor het element gegenereerd. Het element blijft vóór de gedefinieerde tijd inactief. Als u een &#39;Off time&#39; definieert voor een element, wordt het element op het gedefinieerde tijdstip gedeactiveerd en wordt de leverings-URL voor het element niet meer weergegeven.

Voer de volgende stappen uit om de aan- en uittijd voor het element in te stellen:

1. Selecteer het element en klik op **[!UICONTROL Properties]** .

1. Definieer in de sectie **[!UICONTROL Scheduled (de) activation]** van het tabblad **[!UICONTROL Basic]** de Aan-tijd of de Uit-tijd op basis van uw vereisten.

Op dezelfde manier kunt u in de Assets-weergave het element selecteren en op **[!UICONTROL Details]** klikken om de eigenschappen van het element weer te geven en de opties Op tijd en Uit te definiëren.

Het veld is beschikbaar in het standaardmetagegevensformulier. Als uw element niet is gebaseerd op het standaardmetagegevensschema en de velden Aan tijd en Uit tijd niet beschikbaar zijn in de eigenschappen van het element, voert u de volgende stappen uit in de beheerweergave:

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]** .
1. Selecteer het metagegevensschema en klik op **[!UICONTROL Edit]** .
1. Voeg een veld **[!UICONTROL Date]** toe van de sectie **[!UICONTROL Build Form]** rechts naar de sectie Metagegevens in het formulier.
1. Klik op het veld dat u zojuist hebt toegevoegd en voer de volgende updates uit in het deelvenster **[!UICONTROL Settings]** :
   1. Verander **[!UICONTROL Field Label]** in **op Tijd** of **van Tijd**.
   1. Werk **[!UICONTROL Map to property]** aan _bij./jcr:content/onTime_ voor **Op het gebied van de Tijd** en _./jcr:content/offTime_ voor **Van tijd** gebied.
1. Klik op **[!UICONTROL Save]**.

Op dezelfde manier voert u voor de weergave Assets de volgende stappen uit als uw element niet is gebaseerd op het standaardmetagegevensschema en de velden Aan tijd en Uit tijd niet beschikbaar zijn in de eigenschappen van het element:

1. Klik op **[!UICONTROL Metadata Forms]** in de sectie **[!UICONTROL Settings]** .
1. Selecteer het metagegevensformulier en klik op **[!UICONTROL Edit]** .
1. Voeg een veld **[!UICONTROL Date]** van de sectie **[!UICONTROL Components]** in het linkerdeelvenster toe aan het formulier.
1. Klik het onlangs toegevoegde gebied en verander **[!UICONTROL Label]** aan **Op Tijd** of **van Tijd**.
1. Werk **[!UICONTROL Metadata property]** aan _bij./jcr:content/onTime_ voor **Op het gebied van de Tijd** en _./jcr:content/offTime_ voor **Van tijd** gebied.
1. Klik op **[!UICONTROL Save]**.



### Levering van beperkte activa {#delivery-restricted-assets}

De levering van beperkte activa is gebaseerd op een geslaagde toelating tot activa. De autorisatie is gebaseerd op een IMS-token als het verzoek wordt verzonden van een AEM auteur of Asset Selector, of is gebaseerd op een speciaal cookie als u aangepaste identiteitsproviders hebt ingesteld op uw Publish- of Preview-instantie.

#### Levering voor AEM auteur- of Asset Selector-aanvragen {#delivery-aem-author-asset-selector}

Om de levering van beperkte activa toe te laten in het geval dat het verzoek van AEM auteursinstantie of de Selecteur van Activa wordt verzonden, is een geldig symbolisch IMS essentieel. Voer de volgende stappen uit:

1. [ produceer een toegangstoken ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token).
   * Meld u aan bij de Dev Console van uw AEM as a Cloud Service-omgeving.

   * Navigeer naar **[!UICONTROL Environment]** > **[!UICONTROL Integrations]** > **[!UICONTROL Local Token]** > **[!UICONTROL Get Local Development Token]** > **[!UICONTROL Copy accessToken value]** . Leer meer over [ hoe te om tot token en verwante aspecten toegang te hebben ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token)

1. Integreer het verkregen toegangstoken in de **[!UICONTROL Authorization]** header en zorg ervoor dat de waarde ervan voorafgaat aan **[!UICONTROL Bearer]** .

1. Valideer de functionaliteit van het toegangstoken door een verzoek in werking te stellen. Het zou een fout 404 in gevallen moeten opleveren waar er geen toegangstoken IMS is, of het verstrekte toegangstoken heeft de zelfde principes of de groepen die in de meta-gegevens van het middel worden toegevoegd.

#### Levering voor aangepaste identiteitsproviders op Publish-instantie {#delivery-custom-identity-provider}

In het geval van een aangepaste identiteitsprovider die is ingesteld op uw Publish- of Preview-instantie, kunt u de groep noemen die tijdens het installatieproces toegang moet hebben tot beveiligde elementen in het `groupMembership` -kenmerk. Wanneer u het programma opent aan de leverancier van de douaneidentiteit via [ integratie SAML ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/saml-2-0), wordt het `groupMembership` attribuut gelezen en gebruikt om een koekje te construeren, dat in alle verzoeken om authentificatie, gelijkend op een teken IMS in het geval van een verzoek van AEM auteur of de Selecteur van Activa wordt verzonden.

Wanneer een beveiligd element beschikbaar is op een pagina en er een aanvraag wordt gedaan naar de leverings-URL om het element te renderen, controleert AEM de rollen in het cookie of de IMS-token en stemt het overeen met de `dam:roles property` die tijdens het ontwerpen van het element is toegepast. Als er een overeenkomst is, wordt het element weergegeven.

>[!NOTE]
>
> In het [ steunkaartje om Dynamic Media met mogelijkheden te activeren OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md#how-to-enable-the-dynamic-media-with-openapi-capabilities), vermeld beperkte levering in het gebruiksgeval. De Techniek van de Adobe zal met noodzakelijke verduidelijkingen en/of opstellingsproces voor beperkte levering helpen.
