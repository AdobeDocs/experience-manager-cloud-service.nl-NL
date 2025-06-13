---
title: Levering van middelen beperken met Dynamic Media met OpenAPI-mogelijkheden
description: Leer hoe u de levering van middelen kunt beperken met OpenAPI-mogelijkheden.
role: User
exl-id: 3fa0b75d-c8f5-4913-8be3-816b7fb73353
source-git-commit: 5db419e674ceb3c861f53a19e7b852c89ebd3702
workflow-type: tm+mt
source-wordcount: '1144'
ht-degree: 0%

---

# Levering van middelen beperken met Dynamic Media met OpenAPI-mogelijkheden {#restrict-access-to-assets}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b> integratie van AEM Assets met Edge Delivery Services </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuw </i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b> laat Dynamische Media Prime en Ultimate </b></a> toe
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b> Beste praktijken van Meta-gegevens </b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b> Content Hub </b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b> Dynamische Media met mogelijkheden OpenAPI </b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b> de ontwikkelaarsdocumentatie van AEM Assets </b></a>
        </td>
    </tr>
</table>

>[!AVAILABILITY]
>
>De handleiding Dynamic Media met OpenAPI-mogelijkheden is nu beschikbaar in PDF-indeling. Download de volledige handleiding en gebruik Adobe Acrobat AI Assistant om je vragen te beantwoorden.
>
>[!BADGE &#x200B; Dynamische Media met OpenAPI mogelijkhedenGids PDF &#x200B;]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

Met centraal beheer van bedrijfsmiddelen in Experience Manager kunnen de DAM-beheerder of -bedrijfsleiders de toegang beheren tot middelen die beschikbaar zijn via Dynamic Media met OpenAPI-mogelijkheden. Zij kunnen levering van goedgekeurde activa (neer aan individuele activa) aan geselecteerde [ Gebruiker of Groepen van het Systeem van Adobe Identity Management van het Systeem van (IMS) ](https://helpx.adobe.com/in/enterprise/using/users.html#user-mgt-strategy) beperken door bepaalde meta-gegevens op activa op hun de auteursdienst van AEM as a Cloud Service te vormen.

Zodra een middel via Dynamische Media met OpenAPIs wordt beperkt, slechts worden de (Adobe IMS bewaakte) gebruikers gemachtigd om tot het genoemde middel toegang te hebben verleend. Om tot de activa toegang te hebben, moet de gebruiker hefboomwerking [ Onderzoek ](search-assets-api.md) en [ Levering ](deliver-assets-apis.md) mogelijkheden van Dynamische Media met OpenAPI.

![ Beperkte toegang tot activa ](/help/assets/assets/restricted-access.png)

In Experience Manager Assets bestaat een beperkte levering via IMS uit twee belangrijke stappen:

* Authoring
* Aflevering

## Authoring {#authoring}

### Beperkte aflevering met gebruik van een IMS-token voor toonder {#restrict-delivery-ims-token}

U kunt de levering van elementen binnen [!DNL Experience Manager] beperken op basis van IMS-gebruikers- en -groepsidentiteiten.

>[!NOTE]
>
> Dit vermogen is momenteel niet zelfbediening. Om activalevering voor IMS [ Gebruikers ](https://helpx.adobe.com/in/enterprise/using/manage-directory-users.html) en [ Groepen ](https://helpx.adobe.com/in/enterprise/using/user-groups.html) te beperken, bereik uit aan uw team van de Steun van de Onderneming voor begeleiding op hoe te om de informatie terug te winnen die voor het beperken van toegang van [ Adobe Admin Console ](https://adminconsole.adobe.com/) wordt vereist portaal en hoe te om toegang in de de auteursdienst van AEM as a Cloud Service te vormen.

### Levering van activa beperken met de datum en tijd Aan en Uit {#restrict-delivery-assets-date-time}

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



## Levering van beperkte activa {#delivery-restricted-assets}

De levering van beperkte activa is gebaseerd op een geslaagde toelating tot activa. De vergunning is of door [ IMS Dragertokens ](https://developer.adobe.com/developer-console/docs/guides/authentication/UserAuthentication/) (toepassing voor verzoeken die van [ de Kiezer van de Activa van AEM ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector) worden in werking gesteld), of veilig-koekje (als u de leveranciers van de douaneidentiteit opstelling op uw AEM hebt publiceren/de diensten van de Voorproef, en opstelling de koekjesverwezenlijking en opneming op de pagina&#39;s).

### Levering voor AEM-auteur- of Asset Selector-verzoeken {#delivery-aem-author-asset-selector}

Om de levering van beperkte activa mogelijk te maken voor het geval dat het verzoek van de auteursdienst van AEM of de Selecteur van de Activa van AEM wordt verzonden, is een geldige token van de IMS Betoonder essentieel.\
Op de auteur-services van AEM Cloud Service en Asset Selector wordt de token IMS Beonder automatisch gegenereerd en gebruikt voor aanvragen na een geslaagde aanmelding.

>[!NOTE]
>
>Neem contact op met de Enterprise Support voor meer informatie over hoe u IMS-verificatie kunt inschakelen bij de op AEM Asset Selector gebaseerde integratie

1. AEM as a Cloud Service en Dynamic Media met OpenAPI-mogelijkheden ondersteunen momenteel API-integratie aan de serverzijde en kunnen IMS-tokens voor toonder genereren.
   * Volg de instructies [ hier ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis#the-server-to-server-flow) om dienst-aan-server API integratie uit te voeren die de tokens IMS van de Drager door [ AEM as a Cloud Service Developer Console ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines#crxde-lite-and-developer-console) kan terugwinnen
   * Voor beperkte duur, kan de lokale ontwikkelaarstoegang (niet bedoeld voor de gevallen van het productiegebruik), de korte - levende tokens IMS van de Drager voor de gebruiker die op [ AEM as a Cloud Service Developer Console ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines#crxde-lite-and-developer-console) wordt voor authentiek verklaard door de instructies [ hier ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis#developer-flow) te volgen

1. Terwijl het maken van [ Onderzoek ](search-assets-api.md) en [ levering ](deliver-assets-apis.md) API verzoeken, voeg het verkregen token IMS Betower aan de **[!UICONTROL Authorization]** kopbal van het HTTP- verzoek toe (zorg ervoor dat zijn waarde met **[!UICONTROL Bearer]** vooraf bepaald is).

1. Als u de toegangsbeperking wilt valideren, start u een API-aanvraag voor levering met en zonder de header **[!UICONTROL Authorization]** .
   * De reactie levert een `404` foutstatuscode op in gevallen waarin er geen IMS Betoonder-token is, of de opgegeven IMS Betoonder-token behoort niet tot de gebruiker aan wie toegang tot het element is verleend (rechtstreeks of via groepslidmaatschap).
   * De reactie levert een `200` successtatus-code op met de binaire inhoud van het element als het token IMS Betoonder een van de gebruikers of groepen is die toegang tot het element hebben gekregen.

### Levering voor aangepaste identiteitsproviders bij de publicatieservice {#delivery-custom-identity-provider}

AEM Sites-, AEM Assets- en Dynamic Media met OpenAPI-licenties kunnen samen worden gebruikt, zodat beperkte levering van middelen kan worden geconfigureerd op websites die worden gehost op de AEM-service Publiceren of Voorvertoning. De veilige leveringsstroom gebruikt browser koekjes om de toegang van de gebruiker te vestigen en het hebben van een douanedomein voor leveringsrij die subdomein van publiceer domein is is een vereiste voor het uitvoeren van dit gebruiksgeval. In het geval dat de de Publicatie en diensten van de Voorproef van AEM Sites worden gevormd om a [ leverancier van de douaneidentiteit (IdP) ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/authentication/saml-2-0) te gebruiken, moet een nieuw koekje genoemd `delivery-token` het inkapselen van de groepslidmaatschap van de gebruiker op de authentificatie van de publicatiepost van het domein worden geplaatst. De leveringsrij haalt het vergunningsmateriaal uit veilig-koekje en bevestigt de toegang. Gelieve te registreren een [ kaartje van de ondernemingssteun ](/help/assets/dynamic-media-open-apis-overview.md#how-to-enable-the-dynamic-media-with-openapi-capabilities) voor meer details.
