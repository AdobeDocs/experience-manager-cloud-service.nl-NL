---
title: Hoe kan ik een adaptief formulier integreren met Microsoft® Power Automate?
description: Een adaptief formulier integreren met Microsoft® Power Automate.
exl-id: a059627b-df12-454d-9e2c-cc56986b7de6
keywords: Sluit AEM formules aan op automatisering, automatisering van Power Automate AEM Forms, integreer stroom automatisch op Adaptive Forms, verzend gegevens van Adaptive Forms naar Power Automate
feature: Adaptive Forms
role: Admin, User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '1071'
ht-degree: 0%

---


# Een adaptief formulier aansluiten met Microsoft® Power Automate {#connect-adaptive-form-with-power-automate}

U kunt een adaptief formulier configureren om een Microsoft® Power Automate Cloud Flow uit te voeren bij verzending. Met het geconfigureerde adaptieve formulier worden vastgelegde gegevens, bijlagen en het document met records naar Power Automate Cloud Flow verzonden voor verwerking. Het helpt u om een aangepaste ervaring op het gebied van gegevensvastlegging op te bouwen en tegelijk de kracht van Microsoft® Power Automate te benutten om bedrijfslogics rond vastgelegde gegevens te bouwen en de workflows van klanten te automatiseren.

De Adaptive Forms-editor biedt de **Een Microsoft® Power Automate-flow aanroepen** verzendt actie om adaptieve formuliergegevens, bijlagen en Document of Record te verzenden naar Power Automate Cloud Flow.

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak Acties verzenden voor het verwerken van verzonden formulieren. Meer informatie over deze opties vindt u in het gedeelte [Handeling Adaptief verzenden van formulier](/help/forms/configure-submit-actions-core-components.md)  artikel.


## Voordelen

Hier volgen enkele voorbeelden van wat u kunt doen na de integratie van een adaptief formulier met Microsoft® Power Automate:

* Adaptieve Forms-gegevens gebruiken in een Power Automate-bedrijfsprocessen
* Gebruik Power Automate om vastgelegde gegevens naar meer dan 500 gegevensbronnen of een openbaar beschikbare API te verzenden
* Complexe berekeningen uitvoeren op vastgelegde gegevens
* Adaptieve Forms-gegevens opslaan naar opslagsystemen volgens een vooraf bepaald schema

## Vereisten

U hebt het volgende nodig om een adaptief formulier te verbinden met Microsoft® Power Automate:

* Microsoft® Power Automate Premium-licentie.
* Microsoft® [Stroomvoorziening automatiseren](https://docs.microsoft.com/en-us/power-automate/create-flow-solution) met de `When an HTTP request is received` trigger voor het accepteren van Adaptief verzenden van formulieren.
* Een gebruiker van de Experience Manager met [Forms-auteur](/help/forms/forms-groups-privileges-tasks.md) en [Forms Admin](/help/forms/forms-groups-privileges-tasks.md) rechten
* Account dat wordt gebruikt om verbinding te maken met Microsoft® Power Automate is eigenaar van de Power Automate-flow die is geconfigureerd om gegevens van het adaptieve formulier te ontvangen

## Sluit uw Forms as a Cloud Service instantie aan met Microsoft® Power Automate {#connect-forms-server-with-power-automate}

Voer de volgende handelingen uit om uw Forms as a Cloud Service instantie te verbinden met Microsoft® Power Automate:

1. [Een Microsoft maken](#ms-power-automate-application)
1. [Microsoft maken](#microsoft-power-automate-dataverse-cloud-configuration)
1. [Microsoft maken](#create-microsoft-power-automate-flow-cloud-configuration)
1. [Publish Microsoft](#publish-microsoft-power-automate-dataverse-cloud-configuration)

### Microsoft® Azure Active Directory-toepassing maken {#ms-power-automate-application}

1. Aanmelden bij [Azure Portal](https://portal.azure.com/).
1. Selecteren [!UICONTROL Azure Active Directory] in de linkernavigatie.
1. Selecteer op de pagina Standaardmap de optie [!UICONTROL App registrations] in het linkerdeelvenster.
1. Klik op Nieuwe registraties op de pagina App-registraties.
1. Geef de naam, ondersteunde accounttypen en de URI omleiden op de pagina op. Geef in de URI voor omleiding het volgende op en klik op Opslaan.
   * `https://[Forms as a Cloud Service Server]/libs/fd/powerautomate/content/dataverse/config.html`
   * `https://[Forms as a Cloud Service Server]/libs/fd/powerautomate/content/flowservice/config.html`

   ![Registreer een Azure Active Directory-toepassing](assets/power-automate-application.png)

   >[!NOTE]
   >U kunt desgewenst ook aanvullende URI&#39;s voor omleiding opgeven vanaf de pagina Verificatie.
   > Voor ondersteunde accounttypen selecteert u één huurder, meerdere huurders of persoonlijke Microsoft®-account, afhankelijk van uw gebruiksscenario


1. Schakel op de pagina Verificatie de volgende opties in en klik op Opslaan.


   * Toegangstokens (gebruikt voor impliciete stromen)
   * ID-tokens (gebruikt voor impliciete en hybride stromen)

1. Klik op de pagina met API-machtigingen op Een machtiging toevoegen.
1. Selecteer onder Microsoft® API&#39;s de Flow Service en selecteer de volgende machtigingen.
   * Flows.Manage.All
   * Flows.Read.All

   Klik op Machtigingen toevoegen om de machtigingen op te slaan.
1. Klik op de pagina met API-machtigingen op Een machtiging toevoegen. API&#39;s selecteren die mijn organisatie gebruikt en doorzoeken `DataVerse`.
1. Enable user_imitation en klik toevoegen toestemmingen.
1. (Optioneel) Klik op de pagina Certificates &amp; secrets op Nieuw clientgeheim. Voor Add een Geheim scherm van de Cliënt, verstrek een beschrijving en een tijdspanne voor het geheim om te verlopen, en de klik voegt toe. Er wordt een geheime tekenreeks gegenereerd.
1. Noteer uw specifieke organisatie [URL van dynamische omgeving](https://docs.microsoft.com/en-us/power-automate/web-api#compose-http-requests).

### Microsoft® Power Automated Dataverse Cloud Configuration maken {#microsoft-power-automate-dataverse-cloud-configuration}

1. Navigeer in AEM Forms-auteurinstantie naar **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**.
1. Op de **[!UICONTROL Configuration Browser]** pagina, selecteert u **[!UICONTROL Create]**.
1. In de **[!UICONTROL Create Configuration]** dialoogvenster, geeft u een **[!UICONTROL Title]** voor de configuratie, laat toe **[!UICONTROL Cloud Configurations]** en selecteert u **[!UICONTROL Create]**. Het leidt tot een configuratiecontainer om Cloud Servicen op te slaan. Zorg ervoor dat de mapnaam geen ruimte bevat.
1. Navigeren naar **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft®® Power Automate Dataverse]** en open de configuratiecontainer u in de vorige stap creeerde.


   >[!NOTE]
   >
   >Wanneer u een adaptief formulier maakt, geeft u de naam van de container op in het dialoogvenster **[!UICONTROL Configuration Container]** veld.

1. Selecteer op de configuratiepagina **[!UICONTROL Create]** om [!DNL Microsoft®®® Power Automate Flow Service] in AEM Forms.
1. Op de **[!UICONTROL Configure Dataverse Service for Microsoft®®® Power Automate]** pagina, geeft u de **[!UICONTROL Client ID]** (ook wel toepassings-id genoemd), **[!UICONTROL Client Secret]**, **[!UICONTROL OAuth URL]** en **[!UICONTROL Dynamic Environment URL]**. Gebruik de client-id, clientgeheim, OAuth-URL en dynamische omgeving-URL van [Microsoft® Azure Active Directory-toepassing](#ms-power-automate-application) die u in de vorige sectie hebt gemaakt. De optie Eindpunten van het gebruik in Microsoft® Azure Actieve de toepassingsUI van de Folder om OAuth URL te vinden

   ![Met de optie Eindpunten in de gebruikersinterface van Microsoft Power Automate kunt u OAuth URL zoeken](assets/endpoints.png)

1. Selecteren **[!UICONTROL Connect]** . Meld u desgevraagd aan bij uw Microsoft® Azure-account. Selecteren **[!UICONTROL Save]**.

### Microsoft® Power Automated Flow Service Cloud Configuration maken {#create-microsoft-power-automate-flow-cloud-configuration}

1. Navigeren naar **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® Power Automate Flow Service]** en open de configuratiecontainer u in de vorige sectie creeerde.


   >[!NOTE]
   >
   >Wanneer u een adaptief formulier maakt, geeft u de naam van de container op in het dialoogvenster **[!UICONTROL Configuration Container]** veld.

1. Selecteer op de configuratiepagina **[!UICONTROL Create]** om [!DNL Microsoft® Power Automate Flow Service] in AEM Forms.
1. Op de **[!UICONTROL Configure Dataverse for Microsoft® Power Automate]** pagina, geeft u de **[!UICONTROL Client ID]** (ook wel toepassings-id genoemd), **[!UICONTROL Client Secret]**, **[!UICONTROL OAuth URL]** en **[!UICONTROL Dynamic Environment URL]**. Gebruik identiteitskaart van de Cliënt, Geheime cliënt, OAuth URL, en identiteitskaart van het Milieu van de Dynamiek. Gebruik de optie Eindpunten in de gebruikersinterface van de Microsoft® Azure Active Directory-toepassing om OAuth URL te zoeken. Open de [Mijn stromen](https://us.flow.microsoft.com) en selecteer Mijn stromen gebruiken identiteitskaart die in URL als identiteitskaart van het Milieu van de Dynamiek wordt vermeld.
1. Selecteer **[!UICONTROL Connect]**. Meld u desgevraagd aan bij uw Microsoft® Azure-account. Selecteren **[!UICONTROL Save]**.

### Publish zowel de Microsoft® Power Automate Data verse als de Microsoft® Power Automate Flow Service Cloud Configurations {#publish-microsoft-power-automate-dataverse-cloud-configuration}

1. Navigeren naar **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® Power Automate Dataverse]** en open de configuratiecontainer u in vorige creeerde [Microsoft® Power Automated Dataverse Cloud Configuration maken](#microsoft-power-automate-dataverse-cloud-configuration) sectie.
1. Selecteer de `dataverse` configuratie en selecteer **[!UICONTROL Publish]**.
1. Selecteer op de Publish-pagina de optie **[!UICONTROL All Configurations]** en selecteert u **[!UICONTROL Publish]**. Publish: zowel Power Automate Data verse als Power Automate Flow Service Cloud Configurations.

Uw Forms as a Cloud Service-instantie is nu verbonden met Microsoft® Power Automate. U kunt nu Adaptive Forms-gegevens naar een Power Automate-flow verzenden.

## Gebruik de Invoke a Microsoft® Power Automate flow submit action to send data to a Power Automate Flow {#use-the-invoke-microsoft-power-automate-flow-submit-action}

Na u [Sluit uw Forms as a Cloud Service instantie aan met Microsoft® Power Automate](#connect-forms-server-with-power-automate), voert u de volgende actie uit om uw adaptieve formulier te configureren om vastgelegde gegevens naar een Microsoft®-stroom te verzenden bij het verzenden van het formulier.

1. Meld u aan bij de instantie van uw auteur, selecteer het adaptieve formulier en klik op **[!UICONTROL Properties]**.
1. In de Container van de Configuratie, doorblader en selecteer de container die in sectie wordt gecreeerd [Microsoft® Power Automated Dataverse Cloud Configuration maken](#microsoft-power-automate-dataverse-cloud-configuration)en selecteert u **[!UICONTROL Save and Close]**.
1. Open het adaptieve formulier voor bewerking en navigeer naar **[!UICONTROL Submission]** van de eigenschappen van de container van adaptieve formulieren.
1. In de eigenschappencontainer, voor **[!UICONTROL Submit Actions]** Selecteer de **[!UICONTROL Invoke a Power Automate flow]** en selecteert u een **[!UICONTROL Power Automate flow]**. Selecteer de vereiste stroom en de Adaptieve Forms-gegevens worden bij verzending naar de server verzonden.

   ![Verzendhandeling configureren](assets/submission.png)

>[!NOTE]
>
> Voordat u het adaptieve formulier verzendt, moet u ervoor zorgen dat de `When an HTTP Request is received` trigger met een JSON-schema wordt toegevoegd aan uw Power Automate-flow.

```
        {
            "type": "object",
            "properties": {
                "attachments": {
                    "type": "array",
                    "items": {
                        "type": "object",
                        "properties": {
                            "filename": {
                                "type": "string"
                            },
                            "data": {
                                "type": "string"
                            },
                            "contentType": {
                                "type": "string"
                            },
                            "size": {
                                "type": "integer"
                            }
                        },
                        "required": [
                            "filename",
                            "data",
                            "contentType",
                            "size"
                        ]
                    }
                },
                "templateId": {
                    "type": "string"
                },
                "templateType": {
                    "type": "string"
                },
                "data": {
                    "type": "string"
                },
                "document": {
                    "type": "object",
                    "properties": {
                        "filename": {
                            "type": "string"
                        },
                        "data": {
                            "type": "string"
                        },
                        "contentType": {
                            "type": "string"
                        },
                        "size": {
                            "type": "integer"
                        }
                    }
                }
            }
        }
```

<!--
## See also

* [Create an Adaptive Form](creating-adaptive-form-core-components.md)
* [Configure a Submit Action](configure-submit-actions-core-components.md)
* [Adobe Experience Manager Connector for Microsoft&reg; Power Automate](https://learn.microsoft.com/en-us/connectors/adobeexperiencemanag/)
* [Connect Adaptive Form to Microsoft® Power Automate](/help/forms/configure-submit-actions-core-components.md#microsoft-power-automate)
-->


## Verwante artikelen

{{af-submit-action}}

<!--

>[!MORELIKETHIS]
>
>* [Connect Adaptive Form to Microsoft Power Automate](/help/forms/configure-submit-actions-core-components.md#microsoft-power-automate)

-->