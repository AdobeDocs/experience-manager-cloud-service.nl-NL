---
title: AEM Assets op afstand integreren met AEM Sites
description: Leer hoe u AEM-sites kunt configureren en verbinden met Goedgekeurde AEM Assets.
exl-id: 382e6166-3ad9-4d8f-be5c-55a7694508fa
source-git-commit: 2ec0b4125aa0990b6e022350a1f861fe394e6b1f
workflow-type: tm+mt
source-wordcount: '1061'
ht-degree: 0%

---

# AEM Assets op afstand integreren met AEM Sites  {#integrate-approved-assets}

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

Het effectief beheren van digitale middelen is van cruciaal belang voor het aanbieden van aantrekkelijke en consistente merkervaringen op verschillende online platforms. Dynamic Media met OpenAPI-mogelijkheden verbetert het beheer van digitale middelen door naadloze integratie tussen AEM Sites en AEM Assets as a Cloud Service mogelijk te maken. Met deze vernieuwende functie kunt u eenvoudig verschillende typen goedgekeurde digitale middelen delen en beheren in meerdere AEM-omgevingen, waardoor workflows voor siteauteurs en inhoudseditors worden gestroomlijnd.

De dynamische Media met mogelijkheden OpenAPI staat plaatseigenaren toe om activa van verre DAM direct binnen de Redacteur van de Pagina van AEM en [ het Fragment van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/content-fragments/content-fragments.html) te gebruiken, die inhoudsverwezenlijking en beheersprocessen vereenvoudigen.

De gebruikers kunnen veelvoudige instanties van AEM Sites, zonder enige beperkingen op het maximumaantal, met een verre plaatsing verbinden DAM, een opmerkelijk voordeel over de [ Verbonden Assets ](use-assets-across-connected-assets-instances.md) eigenschap.

![afbeelding](/help/assets/assets/connected-assets-rdam.png)

Na de eerste installatie kunnen gebruikers pagina&#39;s op het AEM Sites-exemplaar maken en zo nodig elementen toevoegen. Bij het toevoegen van elementen kunnen ze elementen selecteren die zijn opgeslagen in hun lokale DAM of door de middelen bladeren en gebruiken die beschikbaar zijn in de externe DAM.

Dynamische media met OpenAPI-mogelijkheden bieden verschillende andere voordelen, zoals toegang tot en gebruik van externe middelen in Content Fragment, het ophalen van metagegevens van de externe middelen en nog veel meer. Wis meer over de andere [ voordelen van Dynamische Media met mogelijkheden OpenAPI over Verbonden Assets ](/help/assets/dynamic-media-open-apis-faqs.md).

## Voordat u begint {#pre-requisites-sites-integration}

Ondersteuning voor externe middelen die gebruik maken van Dynamic Media met OpenAPI-mogelijkheden is vereist:

* AEM 6.5 SP 18+ of AEM as a Cloud Service

* Core Components release 2.23.2 of hoger

* Opstelling de volgende [ milieuvariabelen ](/help/implementing/cloud-manager/environment-variables.md#add-variables) voor AEM as a Cloud Service:

   * ASSET_DELIVERY_REPOSITORY_ID= &quot;delivery-pxxxxx-eyyyyy.adobeaemcloud.com&quot; <br>

     `pXXXX` verwijst naar de programma-id <br>
     `eYYYY` verwijst naar de milieu-id

  Deze variabelen worden ingesteld via de Cloud Manager-gebruikersinterface van de AEM as a Cloud Service-omgeving die fungeert als uw lokale Sites-instantie.

   * ASSET_DELIVERY_IMS_CLIENT= [ IMSClientId ]: U moet een Adobe steunkaartje voorleggen om identiteitskaart van de Cliënt IMS te krijgen.

     of vorm de [ montages OSGi ](https://experienceleague.adobe.com/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi.html) voor AEM 6.5 in de instantie van AEM Sites door deze stappen te volgen:

   1. Meld u aan bij de console en klik op **[!UICONTROL OSGi]>** of
gebruik de directe URL, bijvoorbeeld: `https://localhost:4502/system/console/configMgr`

   1. Vorm de **Dynamische Configuratie van de Media van de Volgende Generatie** (`NextGenDynamicMediaConfigImpl`) configuratie OSGi als volgt, die de waarden met die van uw verre activa milieu vervangen.

      ```text
        imsClient="<ims-client-ID>"
        enabled=B"true"
        imsOrg="<ims-org>@AdobeOrg"
        repositoryId="<repo-id>.adobeaemcloud.com"
      ```

      `imsOrg` is geen verplichte invoer.
      `repositoryId` = &quot;delivery-pxxxxx-eyyyyy.adobeaemcloud.com&quot;
waarbij `pXXXX` verwijst naar de programma-id
      `eYYYY` verwijst naar de milieu-id

      ![ het Next Generation Dynamische de configuratievenster van Media Config OSGi ](/help/assets/assets/remote-assets-osgi.png)

  Leer meer over [ authentificatie IMS ](https://experienceleague.adobe.com/docs/experience-manager-65/content/security/ims-config-and-admin-console.html).

  Voor details op hoe te om OSGi te vormen, zie de volgende documenten:

   * [ het Vormen OSGi voor Adobe Experience Manager as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html) voor AEM as a Cloud Service
   * [ het Vormen OSGi ](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-osgi.html) voor AEM 6.5

* IMS-toegang om u aan te melden bij een externe DAM AEM as a Cloud Service-instantie. Het verwijst naar de auteur van Plaatsen die IMS toegang tot het verre milieu van DAM heeft.

* Configureer de component Image v3 in de AEM Sites-instantie. Als de component niet aanwezig is, download en installeer het [ inhoudspakket ](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.23.0).

## HTTPS configureren {#https}

Over het algemeen wordt aangeraden al uw productie-AEM-instanties uit te voeren met gebruik van HTTP&#39;s. Uw lokale ontwikkelomgevingen kunnen echter niet als zodanig worden ingesteld. Externe elementen die gebruik maken van Dynamic Media met OpenAPI hebben echter HTTPS nodig om te kunnen functioneren.

[ Gebruik deze gids ](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/use-the-ssl-wizard.html) om HTTPS te vormen waar u wenst om verre activa, met inbegrip van ontwikkelomgevingen te gebruiken.

## Elementen benaderen vanaf externe DAM {#fetch-assets}

Met Dynamic Media met OpenAPI-mogelijkheden hebt u toegang tot de middelen die beschikbaar zijn in uw externe DAM-instantie in uw lokale AEM Sites Page Editor en AEM Content Fragment.

![afbeelding](/help/assets/assets/open-APIs.png)

### Externe middelen openen in AEM Page Editor {#access-assets-page-editor}

Voer de onderstaande stappen uit om externe middelen te gebruiken in de AEM Page Editor op uw AEM Sites-exemplaar. U kunt deze integratie uitvoeren in AEM as a Cloud Service en AEM 6.5.

1. Ga naar **[!UICONTROL Sites]** > _uw website_ waar AEM **[!UICONTROL Page]** aanwezig is waarin u het verre activa moet toevoegen.
1. Selecteer de pagina en klik **[!UICONTROL Edit (_e _)]**. De AEM **[!UICONTROL Page Editor]**&#x200B;wordt geopend.
1. Klik op de container voor lay-out en voeg een component **[!UICONTROL Image]** toe.
1. Klik de **[!UICONTROL Image]** component en klik ![ montagespictogram ](/help/assets/assets/do-not-localize/settings-icon.svg) pictogram.
1. Schakel de optie **[!UICONTROL Inherit featured image from page]** uit.
1. Klik op **[!UICONTROL Pick]** en selecteer **[!UICONTROL Remote]** .
   ![afbeelding](/help/assets/assets/uncheck-inherit-option.jpg)

   U wordt gevraagd u aan te melden.
1. Selecteer het element en klik op **[!UICONTROL Select]** .
1. Voeg een alternatieve tekst toe en klik op **[!UICONTROL Done]** .
   <br> Het externe element wordt weergegeven in de afbeeldingscomponent. U kunt ook de URL van levering van het element controleren wanneer het op de pagina wordt geladen of via het tabblad Voorbeeld. De leverings-URL geeft aan dat het element op afstand wordt benaderd.

U hebt alleen toegang tot externe middelen in de AEM-pagina-editor voor Image Core Component v3 en Teaser Core Component v2. Voor andere componenten, waaronder aangepaste componenten, zijn aanpassingen vereist om Asset Selector met deze componenten te integreren.

#### Video: Externe middelen openen in AEM Page Editor

>[!VIDEO](https://video.tv.adobe.com/v/3427666)

### Externe elementen openen in AEM Content Fragment {#access-assets-content-fragment}

Voer de onderstaande stappen uit om Externe elementen te gebruiken in AEM Content Fragment op uw AEM Sites-exemplaar. U kunt deze integratie uitvoeren in AEM 6.5 en niet in AEM as a Cloud Service.

1. Ga naar **[!UICONTROL Assets]** > **[!UICONTROL Files]** .
1. Selecteer een elementmap waarin het inhoudsfragment zich bevindt.
1. Selecteer het Fragment van de Inhoud en klik **[!UICONTROL Edit (_e _)]**.

   >[!NOTE]
   >
   >Als u geen model van het Fragment van de Inhoud van AEM hebt, kunt u [ moeten tot één ](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/content-fragments/content-fragments-models.html?lang=en) leiden.

1. Klik het ![ controlemerkpictogram ](/help/assets/assets/do-not-localize/checkmark-icon.svg) pictogram naast de tekstcomponent.
1. Selecteer **[!UICONTROL Remote]** om het element op te halen van de externe DAM. <br>
U kunt **[!UICONTROL Local]** - of **[!UICONTROL Remote]** DAM-gegevensopslagruimte kiezen op basis van uw behoeften.

   ![ beeld ](/help/assets/assets/cf-pick.jpg)
U wordt gevraagd u aan te melden.
1. Kies het element en klik op **[!UICONTROL Select]** .
   <br> De URL van het externe element wordt weergegeven in de tekstcomponent.

#### Video: Externe elementen openen in AEM Content Fragment

>[!VIDEO](https://video.tv.adobe.com/v/3427667)

### Externe middelen openen in Edge Delivery Services {#access-assets-eds}

U hebt toegang tot externe middelen tijdens het ontwerpen van inhoud in Microsoft Word, Google Docs of Universal Editor en publiceert de inhoud vervolgens naar Edge Delivery Services. U kunt Dynamic Media met OpenAPI ook gebruiken om door uw merk goedgekeurde middelen te leveren en vele andere voordelen van de toepassing te benutten. Voor meer informatie, zie [ AEM Assets terwijl het ontwerpen van inhoud voor Edge Delivery Services ](/help/assets/integrate-aem-assets-edge-delivery-services.md) integreren.
