---
title: Integreren met Adobe Target
description: 'Integreren met Adobe Target '
translation-type: tm+mt
source-git-commit: f2ed74afd2df43e31ff1002cd42a60f372d0b769
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 1%

---


# Integreren met Adobe Target{#integrating-with-adobe-target}

Als onderdeel van de Adobe Marketing Cloud kunt u met Adobe Target de relevantie van inhoud vergroten door de inhoud op alle kanalen te richten en te meten. Voor de integratie van Adobe Target en AEM als Cloud Service is het volgende vereist:

* via de aanraakinterface een Analytics-configuratie in AEM maken als Cloud Service (vereiste IMS-configuratie).
* Adobe Analytics toevoegen en configureren als een extensie in [Adobe Launch](https://docs.adobe.com/content/help/en/launch/using/intro/get-started/quick-start.html).

Adobe starten is nodig voor het beheer van client-side eigenschappen voor zowel Analytics als Target op AEM pagina&#39;s (JS-bibliotheken/tags). De integratie met Launch is echter noodzakelijk voor &quot;ervaring richtend&quot;. Voor het exporteren van Experience Fragments naar Target hebt u alleen de Adobe Target Configuration en IMS nodig.

>[!NOTE]
>
>Adobe Experience Manager als klanten van de Cloud Service die geen bestaande rekening van Target hebben, kan om toegang tot het Pak van de Stichting van Target voor Experience Cloud verzoeken. Foundation Pack biedt een beperkt gebruik van Target voor volumes.

## Adobe Target-configuratie maken {#create-configuration}

1. Navigeer naar **Gereedschappen** → **Cloud Servicen**.
   ![](assets/cloudservice1.png "NavigationNavigation")
2. Selecteer **Adobe Target**.
3. Selecteer de knop **Maken** .
   ![](assets/tenant1.png "CreateCreate")
4. Vul de gegevens in (zie hieronder) en selecteer **Connect**.
   ![](assets/open_screen1.png "Connect")

### IMS-configuratie

Een IMS-configuratie voor zowel Launch als Target is nodig om Target op de juiste manier te integreren met AEM en Launch. Terwijl de configuratie IMS voor Lancering vooraf in AEM als Cloud Service wordt gevormd, moet de configuratie van Target IMS worden gecreeerd (nadat Target provisioned is). Raadpleeg [deze video](https://helpx.adobe.com/experience-manager/kt/sites/using/aem-sites-target-standard-technical-video-understand.html) en [deze pagina](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/integration-ims-adobe-io.html) voor informatie over het maken van de Target IMS-configuratie.

### De Target-configuratie bewerken {#edit-target-configuration}

Ga als volgt te werk om de Target-configuratie te bewerken:

1. Selecteer een bestaande configuratie en klik op **Eigenschappen**.
2. Bewerk de eigenschappen.
3. Selecteer **Opnieuw verbinden met Adobe Target**.
   ![Opnieuw](assets/edit_config_page1.png "verbindenOpnieuw verbinden")
4. Selecteer **Opslaan en Sluiten**.

### Een configuratie toevoegen aan een site {#add-configuration}

Ga naar: **Plaatsen** → **selecteer om het even welke plaatspagina** → **Eigenschappen** → **Geavanceerd** → **Configuratie** → selecteer de configuratiehuurder.

## Adobe Target integreren op AEM sites met behulp van Adobe starten {#integrate-target-launch}

AEM biedt een out of the box integratie met Experience Platform Launch. Door de Adobe Target-extensie toe te voegen aan het Experience Platform Launch, kunt u de functies van Adobe Target op AEM webpagina(&#39;s) gebruiken. Target-bibliotheken worden alleen gerenderd met Launch.

>[!NOTE]
>
>Bestaande (verouderde) frameworks werken nog, maar kunnen niet worden geconfigureerd in de aanraakinterface. Het is raadzaam om de configuraties van de veranderlijke afbeelding in Lancering opnieuw op te bouwen.

Als algemeen overzicht, zijn de integratiestappen:

1. Een opstarteigenschap maken
2. De vereiste extensies toevoegen
3. Een gegevenselement maken (om de parameters van de contexthub vast te leggen)
4. Een paginalijn maken
5. Samenstellen en publiceren

### Een opstarteigenschap maken {#create-property}

Een eigenschap is een container die wordt gevuld met extensies, regels en gegevenselementen.

1. Selecteer de knop **Nieuwe eigenschap** .
2. Geef een naam op voor de eigenschap.
3. Terwijl het domein de IP/host invoert waarop u de startbibliotheek wilt laden.
4. Selecteer de knop **Opslaan** .
   ![](assets/properties_newproperty1.png "LaunchpropertyLaunchproperty")

### De vereiste extensies toevoegen {#add-extension}

**Extensies** is de container die de kernbibliotheekinstellingen beheert. De extensie Adobe Target ondersteunt client-side implementaties door Target JavaScript SDK te gebruiken voor het moderne web, at.js. U moet zowel de uitbreidingen **Adobe Target** als **Adobe ContextHub** toevoegen.

1. Selecteer de optie Extension Catalog en zoek naar Target in het filter.
2. Selecteer **Adobe Target** om.js en klik op de installatieoptie.
   ![Target](assets/search_ext1.png "SearchTarget Search")
3. Selecteer de **Configure** knoop. Let op het configuratievenster met de geïmporteerde Target-accountgegevens en de versie at.js voor deze extensie.
4. Selecteer **Opslaan** om de extensie Doel toe te voegen aan de eigenschap Starten. U zou de uitbreiding van het Doel moeten kunnen zien onder de **Geïnstalleerde lijst van Uitbreidingen** wordt vermeld die.
   ![Extensie](assets/configure_extension1.png "opslaan")
5. Herhaal de stappen hierboven om naar de uitbreiding te zoeken **Adobe ContextHub** en het te installeren (dit wordt vereist voor de integratie met contexthub parameters, die waarop het richten zal worden gedaan).

### Een gegevenselement maken {#data-element}

**De elementen** van gegevens zijn placeholders waaraan u de parameters van de contexthub kunt in kaart brengen.

1. Selecteer **Gegevenselementen**.
2. Selecteer Gegevenselement **** toevoegen.
3. Geef de naam van het gegevenselement op en wijs dit toe aan een parameter van een contexthub.
4. Selecteer **Opslaan**.
   ![Data](assets/data_elem1.png "ElementData")

### Een paginalijn maken {#page-rule}

In **artikel** definiëren en ordenen we een reeks acties, die ter plaatse zullen worden uitgevoerd, om doelgericht te zijn.

1. Voeg een set handelingen toe zoals wordt getoond in de schermafbeelding.
   ![](assets/rules1.png "ActionsActions")
2. In Add Params aan Alle Mboxes voegt het gegevenselement toe dat vroeger wordt gevormd (zie gegevenselement hierboven), aan de parameter die in de mbox vraag zal worden verzonden.
   ![](assets/map_data1.png "MboxActions")

### Samenstellen en publiceren {#build-publish}

Raadpleeg deze [pagina](https://docs.adobe.com/content/help/en/experience-manager-learn/aem-target-tutorial/aem-target-implementation/using-launch-adobe-io.html)voor meer informatie over het samenstellen en publiceren van bestanden.

## Wijzigingen in de inhoudsstructuur tussen Klassieke en Touch UI-configuraties {#changes-content-structure}

| **Wijzigen** | **Klassieke UI-configuratie** | **Touch UI-configuratie** | **Gevolgen** |
|---|---|---|---|
| Locatie van de Target-configuratie. | /etc/cloudservices/testandtarget/ | /conf/huurder/settings/cloudservices/target | Eerder waren de veelvoudige configuraties aanwezig onder /etc/cloudservices/testandtarget maar nu zal één enkele configuratie onder een huurder aanwezig zijn. |

>[!NOTE]
>
>Oudere configuraties worden nog steeds ondersteund voor bestaande klanten (zonder de optie om nieuwe configuraties te bewerken of te maken). Oudere configuraties maken deel uit van inhoudspakketten die door de klant met VSTS zijn geüpload.
