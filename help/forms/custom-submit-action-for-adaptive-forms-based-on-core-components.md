---
title: Hoe te om een Douane te creëren legt Actie voor een Aangepast Vorm voor dat op kerncomponenten wordt gebaseerd?
description: Leer hoe u een aangepaste verzendactie maakt voor een adaptieve Forms om gegevens te verwerken voordat u deze verzendt met de aangepaste verzendactie.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Intermediate
exl-id: a369b585-d148-4b5a-8afe-d5673ea865d0
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 0%

---

# Een aangepaste verzendactie maken voor Adaptive Forms (Core Components)

Met een verzendactie kunnen gebruikers de bestemming selecteren voor de gegevens die in een formulier zijn vastgelegd en aanvullende functionaliteit definiëren die bij het verzenden van het formulier moet worden uitgevoerd. De vorm van AEM steunt veelvoudige [ voorlegt acties uit-van-de-doos (OTB) ](/help/forms/configure-submit-actions-core-components.md), zoals het verzenden van een e-mail of het opslaan van gegevens naar SharePoint of OneDrive.

U kunt een douane ook creëren voorlegt actie om functionaliteit toe te voegen niet inbegrepen in [ uit-van-de-doos opties ](/help/forms/configure-submit-actions-core-components.md#select-and-configure-a-submit-action-for-an-adaptive-form-select-and-configure-submit-action). U kunt bijvoorbeeld de formuliergegevens integreren met een toepassing van een derde of een gepersonaliseerde SMS-melding activeren op basis van de gebruikersinvoer.

<!-- ![Custom Submit Image](/help/forms/assets/custom-submit-action-hero-image.png)
-->

## Voorwaarden

Voordat u begint met het maken van uw eerste aangepaste verzendactie voor Adaptive Forms, moet u het volgende doen:

* **Onbewerkte Redacteur van de Tekst (winde)**: Terwijl om het even welke duidelijke tekstredacteur kan werken, biedt een Geïntegreerde Milieu van de Ontwikkeling (winde) zoals de Code van Microsoft Visual Studio geavanceerde eigenschappen voor het gemakkelijkere uitgeven aan.

* **Git**: Dit systeem van de versiecontrole wordt vereist voor het beheren van codeveranderingen. Als u deze niet hebt geïnstalleerd, kunt u deze downloaden van https://git-scm.com.

## Uw eerste aangepaste verzendactie voor een formulier maken

In het onderstaande diagram worden de stappen beschreven voor het maken van een aangepaste verzendactie voor een adaptieve vorm:

![ Aangepast voorlegt actiewerkschema ](/help/forms/assets/custom-submit-action-workflow.png) &lbrace;width=50%, hoogte-50%)

### Clone AEM as a Cloud Service Git-gegevensopslagruimte.

1. Open de opdrachtregel en kies een map waarin u de AEM as a Cloud Service-opslagplaats wilt opslaan, bijvoorbeeld `/cloud-service-repository/` .

1. Voer de onderstaande opdracht uit om de gegevensopslagruimte te klonen:

   ```
   git clone https://git.cloudmanager.adobe.com/<organization-name>/<app-id>/
   ```

   **waar om deze informatie te vinden?**

   Voor geleidelijke instructies bij de plaats bepalen van deze details, verwijs naar het artikel van de Liga van de Ervaring van Adobe &quot;[ Toegang tot Git ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=nl-NL#accessing-git)&quot;.

   **Uw project is klaar!**

   Wanneer de opdracht met succes is voltooid, ziet u een nieuwe map die in uw lokale map is gemaakt. Deze map krijgt de naam van uw toepassing (bijvoorbeeld app-id). Deze map bevat alle bestanden en code die u hebt gedownload van uw AEM as a Cloud Service Git-opslagplaats. U kunt `<appid>` voor uw AEM-project vinden in het `archetype.properties` -bestand.

   ![ archetype Eigenschappen ](/help/forms/assets/custom-submit-action-archetype-app-id.png)

   In deze handleiding wordt deze map de `[AEMaaCS project directory]` genoemd.

## Nieuwe verzendactie toevoegen

1. Open de opslagplaats map in een editor.

   ![ Gelegelde Bewaarplaats ](/help/forms/assets/custom-submit-action-clone-repo.png)

1. Navigeer naar de volgende map in de `[AEMaaCS project directory]` :

   ```
   /ui.apps/src/main/content/jcr_root/apps/<app-id>/
   ```

   **Belangrijk**: Vervang `<app-id>` met uw daadwerkelijke toepassingsidentiteitskaart

1. Maak een nieuwe map voor uw aangepaste verzendactie en geef deze een door u gewenste naam. Geef de map bijvoorbeeld de naam `customsubmitaction` .

   ![ creeer douane voorlegt actiemap ](/help/forms/assets/custom-submit-action-create-folder.png)

1. Navigeer naar de toegevoegde aangepaste verzendactiemap.

   Navigeer binnen uw `[AEMaaCS project directory]` naar het volgende pad:

   `/ui.apps/src/main/content/jcr_root/apps/<app-id>/customsubmitaction/`

   `Important`: vervang `<app-id>` door de werkelijke toepassings-id.

1. Nieuw configuratiebestand maken.
Maak in de map `customsubmitaction` een nieuw bestand met de naam `.content.xml` .

   ![ creeer Dossier Config ](/help/forms/assets/custom-submit-action-create-config-folder.png)

1. Open dit bestand en plak de volgende inhoud, waarbij u `[customsubmitaction]` vervangt door de naam van de verzendactie

   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
   jcr:description="[customsubmitaction]"
   jcr:primaryType="sling:Folder"
   
   guideComponentType="fd/af/components/guidesubmittype"
   guideDataModel="basic,xfa,xsd"
   submitService="[customsubmitaction]"/>
   ```

   Vervang bijvoorbeeld `[customsubmitaction]` door de aangepaste naam van de verzendactie als `Custom Submit Action` .

   ![ creeer douane voorlegt dossier van de actieconfiguratie ](/help/forms/assets/custom-submit-action-config-file.png)

   >[!NOTE]
   >
   > Herinner de naam van de [ aangepaste voorlegging ], aangezien de zelfde naam in de `Submit action` drop-down lijst terwijl het ontwerpen van een vorm verschijnt.


**Neem de nieuwe map op in`filter.xml`**

1. Navigeer aan het `/ui.apps/src/main/content/META-INF/vault/filter.xml` dossier in uw [ AEMaaCS projectfolder ].

1. Open het bestand en voeg de volgende regel aan het einde toe:

   ```
   <filter root="/apps/<app-id>/[customsubmitaction-folder]"/>
   ```

   Voeg bijvoorbeeld de volgende coderegel toe om de map `customsubmitaction` toe te voegen in het `filter.xml` -bestand:

   ```
   <filter root="/apps/wknd/customsubmitaction"/>
   ```

   ![ voeg de gecreeerde omslagen in filter.xml ](/help/forms/assets/custom-submit-action-filter-xml.png) toe

1. Sla de wijzigingen op.

### Voer de dienst voor de toegevoegde voorlegt actie uit.

1. Navigeer naar de volgende map in de `[AEMaaCS project directory]` :
   `/core/src/main/java/com/<app-id>/core/service/`
   `Important`: vervang `<app-id>` door de werkelijke toepassings-id.
1. Maak een nieuw Java-bestand om de service voor de toegevoegde verzendactie te implementeren. Voeg bijvoorbeeld het nieuwe Java-bestand toe als `CustomSubmitService.java` .

   ![ Douane legt de Omslag van de Actie ](/help/forms/assets/custom-submit-action-custom-submit-folder.png) voor

1. Open dit bestand en voeg de code toe voor de aangepaste verzendactie-implementatie.

   De onderstaande Java-code is bijvoorbeeld een OSGi-service die de formulierverzending afhandelt door de verzonden gegevens te registreren en een status `OK` te retourneren. Voeg de volgende code toe aan het `CustomSubmitService.java` -bestand:

   ```
   package com.wknd.core.service;
   
   import com.adobe.aemds.guide.model.FormSubmitInfo;
   import com.adobe.aemds.guide.service.FormSubmitActionService;
   import java.util.HashMap;
   import java.util.Map;
   import org.osgi.service.component.annotations.Component;
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   
       @Component(
       service = FormSubmitActionService.class,
       immediate = true
           )
       public class CustomSubmitService implements FormSubmitActionService {
   
       private static final String serviceName = "Custom Submit Action";
   
       private static Logger log = LoggerFactory.getLogger(CustomSubmitService.class);
   
       @Override
       public String getServiceName() {
       return serviceName;
       }
   
       @Override
       public Map<String, Object> submit(FormSubmitInfo formSubmitInfo) {
       String data = formSubmitInfo.getData();
       log.info("Using custom submit action service, [data] --> " + data);
       Map<String, Object> result = new HashMap<>();
       result.put("status", "OK");
       return result;
        }
       }
   ```

   ![ de Douane legt de Dienst van de Actie ](/help/forms/assets/custom-submit-action-service.png) voor

1. Sla de wijzigingen op.

### Implementeer de code.

**stel code voor lokaal ontwikkelmilieu** op

* Implementeer de AEM as a Cloud Service `[AEMaaCS project directory]` in uw lokale ontwikkelomgeving om de nieuwe verzendactie op uw lokale computer uit te voeren. Distribueren naar uw lokale ontwikkelomgeving:

   1. Zorg ervoor dat uw lokale ontwikkelomgeving actief is. Als u niet reeds opstelling een lokale ontwikkelomgeving hebt, verwijs naar de gids op [ Opstelling een lokale ontwikkelomgeving voor AEM Forms ](/help/forms/setup-local-development-environment.md).

   1. Open het eindvenster of de bevelherinnering.

   1. Navigeer naar de map `[AEMaaCS project directory]` .

   1. Voer de volgende opdracht uit:

      ```
      mvn -PautoInstallPackage clean install
      ```

      ![ Lokale Plaatsing ](/help/forms/assets/custom-submit-action-local-deployment.png)

**stel de code voor het milieu van Cloud Service** op

* Implementeer de AEM as a Cloud Service `[AEMaaCS project directory]` in uw Cloud Service-omgeving. Distribueren naar uw Cloud Service-omgeving:

   1. Uw wijzigingen vastleggen:

      Nadat u de nieuwe aangepaste configuratie voor het verzenden van handelingen hebt toegevoegd, past u uw wijzigingen toe met een duidelijk Git-bericht. (Bijvoorbeeld &quot;Nieuwe aangepaste verzendactie toegevoegd&quot;).

   1. De bijgewerkte code implementeren:

      Trigger een plaatsing van uw code door de [ bestaande volledig-stapelpijpleiding ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=nl-NL#setup-pipeline). Het bouwt en stelt automatisch de bijgewerkte code met de nieuwe douane op om actiessteun voor te leggen.

      Als u niet reeds opstelling een pijpleiding hebt, verwijs naar de gids op [ hoe te opstelling een pijpleiding voor AEM Forms as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=nl-NL#setup-pipeline).

      ![ Plaatsing van de Wolk ](/help/forms/assets/custom-submit-action-cloud-deployment.png)

      **hoe te om de installatie te bevestigen?**

      Zodra het project is voltooid, wordt de aangepaste verzendactie weergegeven in de vervolgkeuzelijst `Submit action` tijdens het ontwerpen van een formulier.

      ![ de Vervolgkeuzelijst van de Actie van de Douane voorleggen ](/help/forms/assets/custom-submit-action-drop-down-list.png)

  Uw omgeving is nu gereed om de aangepaste verzendactie te gebruiken wanneer u een formulier ontwerpt.

### Een voorbeeld bekijken van een adaptief formulier met de verzendactie die u zojuist hebt toegevoegd

1. Meld u aan bij uw AEM Forms as a Cloud Service-exemplaar.
1. Ga naar **Forms** > **Forms en Documenten**.

   ![ Forms en Documenten ](/help/forms/assets/custom-submit-action-fnd.png)

1. Selecteer een AanpassingsVorm en klik **uitgeven**. Het formulier wordt geopend in de bewerkingsmodus.

   ![ geef Vorm ](/help/forms/assets/custom-submit-action-edit-af.png) uit

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik op de tab **[!UICONTROL Submission]** .
1. Selecteer de verzendactie in de vervolgkeuzelijst **[!UICONTROL Submit Action]** . Selecteer bijvoorbeeld de verzendactie als `Custom Submit Action` .

   ![ de Douane legt Vorm ](/help/forms/assets/custom-submit-action-select-submit-action.png) voor

1. Vul het formulier in en verzend het.

   ![ legt Vorm ](/help/forms/assets/custom-submit-action-submit-form.png) voor

   ![ het bericht van Thanku ](/help/forms/assets/custom-submit-action-thankyou-msg.png)

   Zodra de vorm met succes wordt voorgelegd, kunt u de **Configuratie van de Console van het Web van Adobe Experience Manager** controleren om de actie van douane te verifiëren voorlegt actie in het lokale ontwikkelmilieu.
1. Ga naar `http://<host>:<port>/system/console/configMgr` .

1. Navigeer aan de **Steun van het Logboek van de Console van het Web van Adobe Experience Manager** bij `http://<host>:<port>/system/console/slinglog`.

   ![ ConfigMgr ](/help/forms/assets/custom-submit-action-sling-log.png)

1. Klik op de optie `logs/error.log` .
   ![ Open error.log- dossier ](/help/forms/assets/custom-submit-action-error-log.png)

1. Open het `error.log` -bestand om te controleren of de gegevens eraan zijn toegevoegd.

   ![ error.log dossier ](/help/forms/assets/custom-submit-action-form-data-display.png)

   >[!NOTE]
   >
   > Als u foutenlogboeken in de AEM as a Cloud Service-omgeving wilt weergeven, kunt u Splunk gebruiken.

<!--
## Best practices

 * It is recommended to use the OSGi service approach for creating a custom submit action, as it is faster than the AEM servlet approach. 

## Next steps
-->

## Verwante artikelen

{{af-submit-action}}

<!-- The [Adaptive Forms Core Components](https://github.com/adobe/aem-core-forms-components) repository includes a sample folder, `customsubmission/logsubmit`, to simplify the process of adding new custom submit actions. It also provides the Java service implementation for the `logsubmit` custom submit action, named `CustomAFSubmitService`.java. These resources are available on GitHub. -->
