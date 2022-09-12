---
title: Integreren met Adobe Target
description: Integreren met Adobe Target
feature: Administering
role: Admin
exl-id: cf243fb6-5563-427f-a715-8b14fa0b0fc2
source-git-commit: 421ad8506435e8538be9c83df0b78ad8f222df0c
workflow-type: tm+mt
source-wordcount: '1036'
ht-degree: 1%

---

# Integreren met Adobe Target{#integrating-with-adobe-target}

Als onderdeel van de Adobe Marketing Cloud kunt u met Adobe Target de relevantie van inhoud vergroten door de inhoud op alle kanalen te richten en te meten. Voor de integratie van Adobe Target en AEM as a Cloud Service is het volgende vereist:

* het gebruiken van Touch UI om een Configuratie van het Doel in AEM as a Cloud Service (vereiste configuratie IMS) tot stand te brengen.
* Adobe Target toevoegen en configureren als extensie in [Adobe starten](https://experienceleague.adobe.com/docs/experience-platform/tags/get-started/quick-start.html).

Adobe Starten is nodig voor het beheer van client-side eigenschappen voor zowel Analytics als Target op AEM pagina&#39;s (JS-bibliotheken/tags). De integratie met Launch is echter noodzakelijk voor &quot;ervaring richtend&quot;. Voor de uitvoer van de Fragmenten van de Ervaring naar Doel, hebt u slechts de Configuratie van Adobe Target en IMS nodig.

>[!NOTE]
>
>De klanten van Adobe Experience Manager as a Cloud Service die geen bestaand rekening van het Doel hebben, kunnen om toegang tot het Pak van de Stichting van het Doel voor Experience Cloud verzoeken. Het Pak van de Stichting verstrekt volume beperkt gebruik van Doel.

## Adobe Target-configuratie maken {#create-configuration}

1. Navigeren naar **Gereedschappen** → **Cloud Services**.
   ![Navigatie](assets/cloudservice1.png "Navigatie")
2. Selecteren **Adobe Target**.
3. Selecteer **Maken** knop.
   ![Maken](assets/tenant1.png "Maken")
4. Vul de details in (zie hieronder), en selecteer **Verbinden**.
   ![Verbinden](assets/open_screen1.png "Verbinden")

### IMS-configuratie {#ims-configuration}

Een configuratie IMS voor zowel de Lancering als Doel is noodzakelijk om Doel met AEM en Lancering behoorlijk te integreren. Terwijl de configuratie IMS voor Lancering vooraf in AEM as a Cloud Service wordt gevormd, moet de configuratie van doel IMS worden gecreeerd (nadat het Doel provisioned is). Zie [deze video](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-launch/overview.html) en [deze pagina](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/integration-ims-adobe-io.html) om te leren hoe te om de configuratie van het Doel te creëren IMS.

### Adobe Target Tenant ID and Adobe Target Client Code {#tenant-client}

Houd rekening met het volgende wanneer u de velden Adobe Target Tenant ID en Adobe Target Client Code configureert:

1. Voor de meeste klanten, zijn identiteitskaart van de Aannemer en de Code van de Cliënt het zelfde. Dit betekent dat beide velden dezelfde informatie bevatten en identiek zijn. Zorg ervoor dat u de id van de huurder in beide velden invoert.
2. Voor oudere doeleinden kunt u ook verschillende waarden invoeren in de velden Tenant ID en Client Code.

Houd er in beide gevallen rekening mee dat:

* Door gebrek, wordt de Code van de Cliënt (als eerst toegevoegd) ook automatisch gekopieerd in het gebied van identiteitskaart van de Aannemer.
* U kunt de standaard huurder-id wijzigen.
* Dienovereenkomstig, zal de achterste vraag aan Doel op identiteitskaart van de Aannemer en de cliënt zijvraag aan Doel worden gebaseerd op de Code van de Cliënt.

Zoals eerder vermeld, is de eerste zaak de meest voorkomende voor AEM as a Cloud Service. Zorg ervoor dat **beide** de velden bevatten de juiste gegevens, afhankelijk van uw vereisten.

>[!NOTE]
>
> Als u een bestaande Configuratie van het Doel wilt veranderen:
>
> 1. Voer de huurder-id opnieuw in.
> 2. Maak opnieuw verbinding met Doel.
> 3. Sla de configuratie op.


### De doelconfiguratie bewerken {#edit-target-configuration}

Ga als volgt te werk om de doelconfiguratie te bewerken:

1. Selecteer een bestaande configuratie en klik op **Eigenschappen**.
2. Bewerk de eigenschappen.
3. Selecteren **Opnieuw verbinding maken met Adobe Target**.
4. Selecteren **Opslaan en sluiten**.

### Een configuratie toevoegen aan een site {#add-configuration}

Ga naar: **Sites** → **Een sitepagina selecteren** → **Eigenschappen** → **Geavanceerd** → **Configuratie** → Selecteer de configuratiehuurder.

## Adobe Target integreren op AEM sites met behulp van Adobe starten {#integrate-target-launch}

AEM biedt een out of the box integratie met Experience Platform Launch. Door de Adobe Target-extensie toe te voegen aan Experience Platform Launch, kunt u de functies van Adobe Target op AEM webpagina&#39;s gebruiken. Doelbibliotheken worden alleen gerenderd met Launch.

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

Een eigenschap is een container die is gevuld met extensies, regels en gegevenselementen.

1. Selecteer **Nieuwe eigenschap** knop.
2. Geef een naam op voor de eigenschap.
3. Als domein voert u de IP/host in waarop u de opstartafspeelbibliotheek wilt laden.
4. Selecteer **Opslaan** knop.
   ![Launchproperty](assets/properties_newproperty1.png "Launchproperty")

### De vereiste extensies toevoegen {#add-extension}

**Extensies** is de container die de kernbibliotheekinstellingen beheert. De extensie Adobe Target ondersteunt client-side implementaties door Target JavaScript SDK te gebruiken voor het moderne web, at.js. U moet beide **Adobe Target** en **Adobe ContextHub** extensies.

1. Selecteer de optie Extension Catalog en zoek naar Target in het filter.
2. Selecteren **Adobe Target** om.js en klik op de Install optie.
   ![Doel zoeken](assets/search_ext1.png "Doel zoeken")
3. Selecteer **Configureren** knop. Bericht het configuratievenster met de ingevoerde de rekeningsgeloofsbrieven van het Doel, en de versie at.js voor deze uitbreiding.
4. Selecteren **Opslaan** om de uitbreiding van het Doel aan uw bezit van de Lancering toe te voegen. U zou de uitbreiding van het Doel moeten kunnen zien onder **Geïnstalleerde extensies** lijst.
   ![Extensie opslaan](assets/configure_extension1.png "Extensie opslaan")
5. Herhaal bovenstaande stappen om te zoeken naar de **Adobe ContextHub** extensie en installeer deze extensie (dit is vereist voor de integratie met contexthub-parameters, op basis waarvan u zich gaat richten).

### Een gegevenselement maken {#data-element}

**Gegevenselementen** zijn placeholders waaraan u de parameters van de contexthub kunt in kaart brengen.

1. Selecteren **Gegevenselementen**.
2. Selecteren **Gegevenselement toevoegen**.
3. Geef de naam van het gegevenselement op en wijs dit toe aan een parameter van een contexthub.
4. Selecteren **Opslaan**.
   ![Gegevenselement](assets/data_elem1.png "Gegevenselement")

### Een paginalijn maken {#page-rule}

In **Regel** we definiëren en ordenen een reeks acties , die ter plaatse worden uitgevoerd , om het doel te bereiken .

1. Voeg een set handelingen toe zoals wordt getoond in de schermafbeelding.
   ![Handelingen](assets/rules1.png "Handelingen")
2. In Add Params aan Alle Mboxes voegt het gegevenselement toe dat vroeger wordt gevormd (zie gegevenselement hierboven), aan de parameter die in de mbox vraag zal worden verzonden.
   ![Mbox](assets/map_data1.png "Handelingen")

### Samenstellen en publiceren {#build-publish}

Raadpleeg deze voor meer informatie over het maken en publiceren van [page](https://experienceleague.adobe.com/docs/experience-manager-learn/aem-target-tutorial/aem-target-implementation/using-launch-adobe-io.html).

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
    <td>/conf/huurder/settings/cloudservices/target/</td>
    <td> Eerder waren de veelvoudige configuraties aanwezig onder /etc/cloudservices/testandtarget maar nu is één enkele configuratie aanwezig onder een huurder.</td>
  </tr>
</table>

>[!NOTE]
>
>Oudere configuraties worden nog steeds ondersteund voor bestaande klanten (zonder de optie om nieuwe configuraties te bewerken of te maken). Oudere configuraties maken deel uit van inhoudspakketten die door klanten met VSTS worden geüpload.
