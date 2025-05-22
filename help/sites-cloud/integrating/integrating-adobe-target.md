---
title: Integreren met Adobe Target
description: Leer hoe u Adobe Target met AEM as a Cloud Service kunt integreren met de Touch-gebruikersinterface en Adobe Launch.
feature: Integration
role: Admin
exl-id: cf243fb6-5563-427f-a715-8b14fa0b0fc2
solution: Experience Manager Sites
source-git-commit: e5c529ced09a557585681ebf82f40daafc2c4402
workflow-type: tm+mt
source-wordcount: '1080'
ht-degree: 0%

---

# Integreren met Adobe Target{#integrating-with-adobe-target}

Als deel van Adobe Experience Cloud, [ Adobe Target ](https://experienceleague.adobe.com/en/docs/target) laat u inhoudsrelevantie door het richten en het meten over alle kanalen verhogen. Voor de integratie van Adobe Target en AEM as a Cloud Service zijn:

* via de aanraakinterface een doelconfiguratie in AEM as a Cloud Service (vereiste IMS-configuratie) maken.
* het toevoegen van en het vormen van Adobe Target als uitbreiding in [ de Lancering van Adobe ](https://experienceleague.adobe.com/docs/experience-platform/tags/get-started/quick-start.html).

Adobe Launch is nodig voor het beheer van client-side eigenschappen voor zowel Analytics als Target op AEM-pagina&#39;s (JS-bibliotheken/tags). Dat gezegd hebbende, is de integratie met Lancering nodig voor &quot;Ervaring gericht&quot;.

Voor de uitvoer van de Fragmenten van de Ervaring en/of de Fragmenten van de Inhoud naar Doel, hebt u de [ Configuratie van Adobe Target ](#create-configuration), met inbegrip van de [ Integratie IMS ](#ims-configuration) nodig.

>[!NOTE]
>
>Klanten die geen bestaande Target-account hebben, kunnen toegang aanvragen tot het Target Foundation Pack voor Experience Cloud. Het Pak van de Stichting verstrekt volume beperkt gebruik van Doel.

>[!NOTE]
>
>Zie ook de documentatie van Adobe Target: [ integreer Doel met Adobe Experience Manager (AEM) ](https://experienceleague.adobe.com/en/docs/target/using/integrate/aem/aem-target-integration).

## Adobe Target-configuratie maken {#create-configuration}

1. Navigeer aan **Hulpmiddelen** → **de Diensten van de Wolk**.
   ![ Navigatie ](assets/cloudservice1.png " Navigatie ")
2. Selecteer **Adobe Target**.
3. Selecteer **creeer** knoop.
   ![ creeer ](assets/tenant1.png " ")
4. Vul de details (zie hieronder) in, en selecteer **verbinden**.
   ![ verbind ](assets/open_screen1.png " ")

### IMS-configuratie {#ims-configuration}

Voor de integratie van AEM met Adobe Target via de Target Standard API is de configuratie van Adobe IMS (Identity Management System) vereist. De IMS-configuratie van het doel moet worden gemaakt (nadat het doel is ingericht). Zie [ Instelling IMS Integraties voor AEM as a Cloud Service ](/help/security/setting-up-ims-integrations-for-aem-as-a-cloud-service.md) en de video [ Integrating de Lancering van het Platform van de Ervaring en AEM ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-data-collection-tags/overview.html) leren hoe te om de configuratie van Doel te creëren IMS.

>[!NOTE]
>
>[ IMS de integratie wordt nu gevormd met S2S OAuth ](/help/security/setting-up-ims-integrations-for-aem-as-a-cloud-service.md).
>
>De vorige configuraties werden gemaakt met [ geloofsbrieven JWT die nu onderworpen aan verval in Adobe Developer Console ](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md) zijn.

>[!NOTE]
>
>Wanneer het vormen van het project, hangen de productprofielen met worden getoond af van of u hebt:
>
>* Adobe Target Norm - slechts **StandaardWorkspace** is beschikbaar
>* Adobe Target Premium - alle beschikbare werkruimten worden weergegeven, zoals hieronder wordt weergegeven

### Adobe Target Tenant ID and Adobe Target Client Code {#tenant-client}

Houd rekening met het volgende wanneer u de velden Adobe Target Tenant ID en Adobe Target Client Code configureert:

1. Voor de meeste klanten, zijn identiteitskaart van de Aannemer en de Code van de Cliënt het zelfde. Dat wil zeggen dat beide velden dezelfde informatie bevatten en identiek zijn. Zorg ervoor dat u de id van de huurder in beide velden invoert.
2. Voor oudere doeleinden kunt u ook verschillende waarden invoeren in de velden Tenant ID en Client Code.

In beide gevallen:

* Door gebrek, wordt de Code van de Cliënt (als eerst toegevoegd) ook automatisch gekopieerd in het gebied van identiteitskaart van de Aannemer.
* Indien nodig, kunt u de standaard reeks van identiteitskaart van de Huurder veranderen.
* De achtergrond vraag aan Doel is gebaseerd op huuridentiteitskaart en de cliënt zijvraag aan Doel is gebaseerd op de Code van de Cliënt.

Zoals eerder vermeld, is de eerste zaak de meest voorkomende voor AEM as a Cloud Service. Één van beide manier, zorg ervoor dat **beide** gebieden de correcte informatie afhankelijk van uw vereisten bevatten.

>[!NOTE]
>
> Als u een bestaande Configuratie van het Doel wilt veranderen:
>
> 1. Voer de id van de huurder opnieuw in.
> 2. Opnieuw verbinden met doel.
> 3. Sla de configuratie op.

### De doelconfiguratie bewerken {#edit-target-configuration}

Ga als volgt te werk om de doelconfiguratie te bewerken:

1. Selecteer een bestaande configuratie en klik **Eigenschappen**.
2. Bewerk de eigenschappen.
3. Selecteer **opnieuw verbinden met Adobe Target**.
4. Selecteer **sparen en Sluiten**.

### Een configuratie toevoegen aan een site {#add-configuration}

Om een configuratie van de Aanraking UI op een plaats toe te passen, ga naar: **Plaatsen** > **selecteer om het even welke plaatspagina** > **Eigenschappen** > **Geavanceerd** > **Configuratie** > selecteer de configuratiehuurder.

## Adobe Target integreren op AEM-sites met Adobe Launch {#integrate-target-launch}

AEM biedt een out of the box integratie met Experience Platform Launch. Door de Adobe Target-extensie toe te voegen aan Experience Platform Launch, kunt u de functies van Adobe Target op AEM-webpagina&#39;s gebruiken. Doelbibliotheken worden alleen weergegeven met Launch.

>[!NOTE]
>
>Bestaande (verouderde) frameworks werken nog, maar kunnen niet worden geconfigureerd in de aanraakinterface. Adobe raadt u aan de configuraties voor variabele toewijzingen opnieuw samen te stellen in Launch.

Als algemeen overzicht, zijn de integratiestappen:

1. Een opstarteigenschap maken
2. De vereiste extensies toevoegen
3. Een gegevenselement maken (om de parameters van de contexthub vast te leggen)
4. Een paginalijn maken
5. Samenstellen en publiceren

### Een opstarteigenschap maken {#create-property}

Een eigenschap is een container die is gevuld met extensies, regels en gegevenselementen.

1. Selecteer de **Nieuwe knoop van het Bezit**.
2. Geef een naam op voor de eigenschap.
3. Als domein voert u de IP/host in waarop u de opstartafspeelbibliotheek wilt laden.
4. Selecteer **sparen** knoop.
   ![ Launchproperty ](assets/properties_newproperty1.png " Launchproperty ")

### De vereiste extensies toevoegen {#add-extension}

**Uitbreidingen** zijn de container die de montages van de kernbibliotheek beheert. De extensie Adobe Target ondersteunt client-side implementaties door Target JavaScript SDK te gebruiken voor het moderne web, at.js. Voeg zowel de **Adobe Target** als **Adobe ContextHub** uitbreidingen toe.

1. Selecteer de optie Extension Catalog en zoek naar Target in het filter.
2. Selecteer **Adobe Target** at.js en klik op de Install optie.
   ](assets/search_ext1.png " Onderzoek van het 1} Doel van het 0} Doel ")![
3. Selecteer **vormen** knoop. Bericht het configuratievenster met de ingevoerde de rekeningsgeloofsbrieven van het Doel, en de versie at.js voor deze uitbreiding.
4. Selecteer **sparen** om de uitbreiding van het Doel aan uw bezit van de Lancering toe te voegen. U zou de uitbreiding van het Doel moeten kunnen zien onder de **Geïnstalleerde lijst van Uitbreidingen** wordt vermeld die.
   ![ sparen Uitbreiding ](assets/configure_extension1.png " sparen Uitbreiding ")
5. Herhaal de stappen hierboven om naar de **uitbreiding te zoeken Adobe ContextHub** en het te installeren (deze uitbreiding wordt vereist voor de integratie met contexthub parameters, die waarop het richten wordt gedaan).

### Een gegevenselement maken {#data-element}

**elementen van Gegevens** zijn placeholders waaraan u de parameters van de contexthub kunt in kaart brengen.

1. Selecteer **Elementen van Gegevens**.
2. Selecteer **toevoegen het Element van Gegevens**.
3. Geef de naam van het gegevenselement op en wijs dit toe aan een parameter van een contexthub.
4. Selecteer **sparen**.
   ![ Element van Gegevens ](assets/data_elem1.png " het Element van Gegevens ")

### Een paginalijn maken {#page-rule}

In **Regel**, bepaalt het en geeft opdracht tot een opeenvolging van acties, die op plaats in werking worden gesteld, om het richten te bereiken.

1. Voeg een set handelingen toe zoals wordt getoond in de schermafbeelding.
   ![ Acties ](assets/rules1.png " Acties ")
2. In Add Params aan Alle Mboxes, voeg het gegevenselement toe dat vroeger (zie gegevenselement hierboven) wordt gevormd, aan de parameter die in de mbox vraag wordt verzonden.
   ![ Mbox ](assets/map_data1.png " Acties ")

### Samenstellen en publiceren {#build-publish}

Leren hoe te om te bouwen en te publiceren, zie [ pagina ](https://experienceleague.adobe.com/docs/experience-manager-learn/aem-target-tutorial/aem-target-implementation/using-launch-adobe-io.html).

## Wijzigingen in de inhoudsstructuur tussen Klassieke en Touch UI-configuraties {#changes-content-structure}

<table style="table-layout:auto">
  <tr>
    <th>Wijzigen</th>
    <th>Klassieke UI-configuratie</th>
    <th>Touch UI-configuratie</th>
    <th>Gevolgen</th>
  </tr>
  <tr>
    <td>Plaats van de Configuratie van het Doel.</td>
    <td>/etc/cloudservices/testandtarget/</td>
    <td>/conf/huurder/settings/cloudconfigs/target/</td>
    <td> Eerder waren de veelvoudige configuraties aanwezig onder /etc/cloudservices/testandtarget maar nu is één enkele configuratie aanwezig onder een huurder.</td>
  </tr>
</table>

>[!NOTE]
>
>Oudere configuraties worden nog steeds ondersteund voor bestaande klanten (zonder de optie om te bewerken of te maken). Verouderde configuraties maken deel uit van inhoudspakketten die door klanten met VSTS worden geüpload.
