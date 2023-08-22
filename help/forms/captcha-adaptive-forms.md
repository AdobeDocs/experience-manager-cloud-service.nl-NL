---
title: reCAPTCHA gebruiken in Adaptive Forms
description: Leer hoe u de Google reCAPTCHA-service configureert in Adaptive Forms.
topic-tags: adaptive_forms, author
source-git-commit: ad63083016f0f8c51ea336e37461562e61c02a8f
workflow-type: tm+mt
source-wordcount: '1852'
ht-degree: 0%

---

# reCAPTCHA gebruiken in Adaptive Forms{#using-reCAPTCHA-in-adaptive-forms}

<span class="preview"> Dit is een pre-release functie die toegankelijk is via onze [pre-releasekanaal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features). </span>


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/captcha-adaptive-forms.html) |
| AEM as a Cloud Service | Dit artikel |

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/creating-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

CAPTCHA (Complete Automated Public Turing test to tell Computers and Humans Apart) is een programma dat vaak wordt gebruikt bij online transacties om onderscheid te maken tussen mensen en geautomatiseerde programma&#39;s of bots. Het stelt een uitdaging en evalueert de reactie van de gebruiker om te bepalen of het een mens of bot is die met de site communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige doeleinden posten.

[!DNL AEM Forms] reCAPTCHA ondersteunen in Adaptive Forms. U kunt de reCAPTCHA-service van Google gebruiken om CAPTCHA te implementeren.

>[!NOTE]
>
>* [!DNL AEM Forms] reCaptcha v2 en reCaptcha Enterprise ondersteunen. Andere versies worden niet ondersteund.
>* reCAPTCHA in Adaptive Forms wordt niet ondersteund in de offline modus [!DNL AEM Forms] app.
>

## De reCAPTCHA-service van Google configureren {#google-reCAPTCHA}

Auteurs van formulieren kunnen de reCAPTCHA-service van Google gebruiken om reCAPTCHA te implementeren in Adaptive Forms. Het biedt geavanceerde CAPTCHA-mogelijkheden om uw site te beschermen. Voor meer informatie over hoe reCAPTCHA werkt, zie [Google reCAPTCHA](https://developers.google.com/recaptcha/). De service reCAPTCHA omvat [!DNL reCAPTCHA v2] en [!DNL reCAPTCHA Enterprise] waarin u kunt integreren [!DNL AEM Forms]. Gebaseerd op uw vereiste kunt u de dienst vormen reCAPTCHA om toe te laten:

![reCAPTCHA](/help/forms/assets/recaptcha_new.png)

* [reCAPTCHA Enterprise in AEM Forms](#steps-to-implement-reCAPTCHA-enterprise-in-forms)
* [reCAPTCHA v2 in AEM Forms](#steps-to-implement-reCAPTCHA-v2-in-forms)


### reCAPTCHA Enterprise configureren  {#steps-to-implement-reCAPTCHA-enterprise-in-forms}

1. Maak of selecteer een [Google Cloud-project](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#before-you-begin) en [reCAPTCHA Enterprise API](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#enable-the-recaptcha-enterprise-api).
1. Verkrijg [Project-id](https://support.google.com/googleapi/answer/7014113?hl=en#:~:text=To%20locate%20your%20project%20ID,a%20member%20of%20are%20displayed) en een [API-sleutel](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#create_an_api_key) en [sitecode voor websites](https://cloud.google.com/recaptcha-enterprise/docs/create-key#create-key).
1. Configuratiecontainer maken voor cloudservices.

   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]**.
   1. Selecteer een map of maak een map en schakel de map in voor cloudconfiguraties met behulp van de volgende stappen:
      1. Selecteer de map in de configuratiegrowser en tik op **[!UICONTROL Properties]**.
      1. Schakel in het dialoogvenster Configuratieeigenschappen de optie **[!UICONTROL Cloud Configurations]**.
      1. Tikken **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

1. De cloudservice configureren voor [!DNL reCAPTCHA Enterprise].

   1. Ga naar de Experience Manager authentieke instantie ![gereedschappen-1](assets/tools-1.png) > **[!UICONTROL Cloud Services]**.
   1. Tik op **[!UICONTROL reCAPTCHA]**. De pagina Configurations wordt geopend. Selecteer de configuratiecontainer die u hebt gemaakt en tik op **[!UICONTROL Create]**.
   1. Versie selecteren als [!DNL reCAPTCHA Enterprise] en specificeer Naam, identiteitskaart van het Project, Sleutel van de Plaats, en API sleutel (Verkregen in Stap 2) voor de dienst van de Onderneming reCAPTCHA.
   1. Selecteer sleuteltype, zou het zeer belangrijke type moeten zijn zoals de plaatstoets die u in vormde [Google Cloud-project](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#before-you-begin), bijvoorbeeld **Sitetoets selectievakje** of **Score-gebaseerde sitesleutel**.
   1. Geef een [drempelscore in het bereik 0 tot 1](https://cloud.google.com/recaptcha-enterprise/docs/interpret-assessment#interpret_scores). Scores groter dan of gelijk aan de drempelscores identificeren menselijke interactie, anders beschouwd als beide interactie.
   1. Tikken **[!UICONTROL Create]** om de configuratie van de cloudservice te maken.

<!--
    1. In the Edit Component dialog, specify the name, project ID, site key, API key (obtained in steps 2 and 3), select the key type, and enter the threshold score. Tap **[!UICONTROL Save Settings]** and then tap **[!UICONTROL OK]** to complete the configuration.
-->

Zodra de reCAPTCHA Enterprise-service is ingeschakeld, is deze beschikbaar voor gebruik in adaptieve formulieren. Zie [gebruik van CAPTCHA in adaptieve vormen](#using-reCAPTCHA).

<!--
![reCAPTCHA Enterprise](/help/forms/assets/recaptcha1-enterprise.png)
-->

### Google reCAPTCHA v2 configureren {#steps-to-implement-reCAPTCHA-v2-in-forms}

1. Verkrijgen [reCAPTCHA API-sleutelpaar](https://www.google.com/recaptcha/admin) uit Google. Het omvat een **site-sleutel** en **geheime sleutel**.
1. Configuratiecontainer maken voor cloudservices.
   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]**.
   1. Selecteer een map of maak een map en schakel de map in voor cloudconfiguraties met behulp van de volgende stappen:
      1. Selecteer de map in de configuratiegrowser en tik op **[!UICONTROL Properties]**.
      1. Schakel in het dialoogvenster Configuratieeigenschappen de optie **[!UICONTROL Cloud Configurations]**.
      1. Tikken **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

1. Configureer de cloudservice voor reCAPTCHA v2.

   1. Ga naar de AEM ![gereedschappen-1](assets/tools-1.png) > **Cloud Servicen**.
   1. Tik op **[!UICONTROL reCAPTCHA]**. De pagina Configurations wordt geopend. Selecteer de configuratiecontainer die u hebt gemaakt en tik op **[!UICONTROL Create]**.
   1. Versie selecteren als [!DNL reCAPTCHA v2] , specificeer Naam, de sleutel van de Plaats, en Geheime Sleutel voor de dienst reCAPTCHA (Verkregen in Stap 1) en tik **[!UICONTROL Create]** om de configuratie van de cloudservice te maken.
   1. Geef in het dialoogvenster Component bewerken de site en de geheime sleutels op die in stap 1 zijn verkregen. Tikken **[!UICONTROL Save Settings]** en tikt u vervolgens op **OK** de configuratie voltooien.

   Zodra de reCAPTCHA-service is geconfigureerd, is deze beschikbaar voor gebruik in adaptieve formulieren. Zie voor meer informatie [gebruik van CAPTCHA in adaptieve vormen](#using-reCAPTCHA).

<!--![reCAPTCHA v2](/help/forms/assets/recaptcha-v2.png)-->


## reCAPTCHA gebruiken in adaptieve formulieren {#using-reCAPTCHA}

ReCAPTCHA in adaptieve vorm gebruiken:

1. Open een adaptief formulier in de bewerkingsmodus.

   >[!NOTE]
   >
   >Zorg ervoor dat de configuratiecontainer die is geselecteerd bij het maken van het adaptieve formulier, de reCAPTCHA-cloudservice bevat. U kunt ook adaptieve formuliereigenschappen bewerken om de configuratiecontainer te wijzigen die aan het formulier is gekoppeld.

1. Sleep vanuit de componentbrowser de **Captcha** op het adaptieve formulier.

   >[!NOTE]
   >
   >* Het gebruik van meer dan één Captcha-component in een adaptieve vorm wordt niet ondersteund. Het wordt ook afgeraden om CAPTCHA te gebruiken in een deelvenster dat is gemarkeerd voor wazig laden of in een fragment.
   >* reCaptcha is tijdgevoelig en verloopt over een paar minuten. Daarom wordt aangeraden de component Captcha vlak voor de knop Verzenden in het aangepaste formulier te plaatsen.

1. Selecteer de Captcha-component die u hebt toegevoegd en tik op ![cmppr](assets/cmppr.png) om de eigenschappen te bewerken.
1. Geef een titel op voor de CAPTCHA-widget. De standaardwaarde is **Captcha**. Selecteren **Titel verbergen** als u de titel niet wilt weergeven.
1. Van de **Captcha-service** vervolgkeuzelijst, selecteert u **reCAPTCHA** om de dienst reCAPTCHA toe te laten als u het zoals die in vormde [reCAPTCHA-service van Google](#google-reCAPTCHA).
1. Selecteer een configuratie in het keuzemenu Instellingen voor **reCAPTCHA Enterprise** of **reCAPTCHA v2**
   1. Als u **reCAPTCHA Enterprise** versie, het sleuteltype kan van **selectievakje** of **op basis van score**, is het gebaseerd op uw selectie wanneer u vormt [sitecode voor websites](https://cloud.google.com/recaptcha-enterprise/docs/create-key#create-key):

   >[!NOTE]
   >
   >* In de cloudconfiguratie met **sleuteltype** als **selectievakje** wordt het aangepaste foutbericht weergegeven als een inline-bericht als de validatie van captcha mislukt.
   >* In de cloudconfiguratie met **sleuteltype** als **op basis van score** wordt het aangepaste foutbericht weergegeven als een pop-upbericht als de validatie van Captcha mislukt.

   1. U kunt de grootte selecteren als **[!UICONTROL Normal]** en **[!UICONTROL Compact]**.
   1. U kunt een **[!UICONTROL Bind Reference]**, in **[!UICONTROL Bind Reference]** de ingediende gegevens zijn gebonden, anders zijn het niet-gebonden gegevens. Hieronder volgen XML-voorbeelden van niet-gebonden gegevens en gebonden gegevens (met bind verwijzing als SSN), wanneer een formulier wordt verzonden.

   ```xml
           <?xml version="1.0" encoding="UTF-8" standalone="no"?>
           <afData>
           <afUnboundData>
               <data>
                   <captcha16820607953761>
                       <captchaType>reCaptchaEnterprise</captchaType>
                       <captchaScore>0.9</captchaScore>
                   </captcha16820607953761>
               </data>
           </afUnboundData>
           <afBoundData>
               <Root
                   xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/"
                   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                   <PersonalDetails>
                       <SSN>371237912</SSN>
                       <FirstName>Sarah </FirstName>
                       <LastName>Smith</LastName>
                   </PersonalDetails>
                   <OtherInfo>
                       <City>California</City>
                       <Address>54 Residency</Address>
                       <State>USA</State>
                       <Zip>123112</Zip>
                   </OtherInfo>
               </Root>
           </afBoundData>
           <afSubmissionInfo>
               <stateOverrides/>
               <signers/>
               <afPath>/content/dam/formsanddocuments/captcha-form</afPath>
               <afSubmissionTime>20230608034928</afSubmissionTime>
           </afSubmissionInfo>
           </afData>
   ```

   ```xml
           <?xml version="1.0" encoding="UTF-8" standalone="no"?>
           <afData>
           <afUnboundData>
               <data/>
           </afUnboundData>
           <afBoundData>
               <Root
                   xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/"
                   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                   <PersonalDetails>
                       <SSN>
                           <captchaType>reCaptchaEnterprise</captchaType>
                           <captchaScore>0.9</captchaScore>
                       </SSN>
                       <FirstName>Sarah</FirstName>
                       <LastName>Smith</LastName>
                   </PersonalDetails>
                   <OtherInfo>
                       <City>California</City>
                       <Address>54 Residency</Address>
                       <State>USA</State>
                       <Zip>123112</Zip>
                   </OtherInfo>
               </Root>
           </afBoundData>
           <afSubmissionInfo>
               <stateOverrides/>
               <signers/>
               <afPath>/content/dam/formsanddocuments/captcha-form</afPath>
               <afSubmissionTime>20230608035111</afSubmissionTime>
           </afSubmissionInfo>
           </afData>
   ```

   Als u **reCAPTCHA v2** versie:
   1. U kunt de grootte selecteren als **[!UICONTROL Normal]** of **[!UICONTROL Compact]** voor de reCAPTCHA-widget.
   1. U kunt de **[!UICONTROL Invisible]** optie om de CAPTCHA-uitdaging alleen aan te tonen in het geval van een verdachte activiteit.

   De reCAPTCHA-service is ingeschakeld op het adaptieve formulier. U kunt een voorbeeld van het formulier bekijken en de CAPTCHA bekijken. De **beveiligd door reCAPTCHA** de badge, die hieronder wordt weergegeven, wordt weergegeven op de beveiligde formulieren.
   ![Google beveiligd door reCAPTCHA-badge](/help/forms/assets/google-recaptcha-v2.png)

1. Sla de eigenschappen op.

>[!NOTE]
> 
> Niet selecteren **[!UICONTROL Default]** van de de dienstdrop-down Captcha aangezien de standaard AEM dienst CAPTCHA wordt afgekeurd.

>[!VIDEO](https://video.tv.adobe.com/v/3422641/recaptcha-google-adaptive-forms/?quality=12&learn=on)

### CAPTCHA-component tonen of verbergen op basis van regels {#show-hide-captcha}

U kunt de component CAPTCHA weergeven of verbergen op basis van de regels die u toepast op een component in een adaptief formulier. Tik op de component en selecteer ![regels bewerken](assets/edit-rules-icon.svg)en tikken **[!UICONTROL Create]** om een regel te maken. Zie voor meer informatie over het maken van regels [Regeleditor](rule-editor.md).

De component CAPTCHA moet bijvoorbeeld alleen in een adaptief formulier worden weergegeven als het veld Waarde valuta in het formulier een waarde heeft van meer dan 25000.

Tik op de knop **[!UICONTROL Currency Value]** in het formulier en stel de volgende regels in:

![Regels tonen of verbergen](assets/rules-show-hide-captcha.png)

>[!NOTE]
>
> Wanneer u een reCAPTCHA v2-configuratie selecteert en de grootte is ingesteld op [!UICONTROL Invisible], blijft de optie weergeven/verbergen uitgeschakeld.

### CAPTCHA valideren {#validate-captcha}

U kunt CAPTCHA valideren in een adaptief formulier wanneer u het formulier verzendt of de CAPTCHA-validatie baseert op gebruikersacties en -voorwaarden.

#### CAPTCHA valideren bij het verzenden van formulieren {#validation-form-submission}

Een CAPTCHA automatisch valideren wanneer u een adaptief formulier verzendt:

1. Tik op de component CAPTCHA en selecteer ![cmppr](assets/configure-icon.svg) om de componenteigenschappen weer te geven.
1. In de **[!UICONTROL Validate CAPTCHA]** sectie, selecteert u **[!UICONTROL Validate CAPTCHA at form submission]**.
1. Tikken ![Gereed](assets/save_icon.svg) om de componenteigenschappen op te slaan.

#### CAPTCHA bij gebruikershandelingen en -voorwaarden valideren {#validate-captcha-user-action}

Een CAPTCHA valideren op basis van voorwaarden en gebruikersacties:

1. Tik op de component CAPTCHA en selecteer ![cmppr](assets/configure-icon.svg) om de componenteigenschappen weer te geven.
1. In de **[!UICONTROL Validate CAPTCHA]** sectie, selecteert u **[!UICONTROL Validate CAPTCHA on a user action]**.
1. Tikken ![Gereed](assets/save_icon.svg) om de componenteigenschappen op te slaan.

[!DNL Experience Manager Forms] verstrekt `ValidateCAPTCHA` API om CAPTCHA te valideren met behulp van vooraf gedefinieerde voorwaarden. U kunt de API aanroepen met behulp van een aangepaste verzendactie of door regels voor componenten in een adaptief formulier te definiëren.

Hier volgt een voorbeeld van een `ValidateCAPTCHA` API voor validatie van CAPTCHA met behulp van vooraf gedefinieerde voorwaarden:

```javascript
if (slingRequest.getParameter("numericbox1614079614831").length() >= 5) {
     GuideCaptchaValidatorProvider apiProvider = sling.getService(GuideCaptchaValidatorProvider.class);
        String formPath = slingRequest.getResource().getPath();
        String captchaData = slingRequest.getParameter(GuideConstants.GUIDE_CAPTCHA_DATA);
        if (!apiProvider.validateCAPTCHA(formPath, captchaData).isCaptchaValid()){
            response.setStatus(400);
            return;
        }
    }
```

In het voorbeeld wordt aangegeven dat de `ValidateCAPTCHA` API valideert de CAPTCHA alleen in het formulier als het aantal cijfers in het numerieke vak dat door de gebruiker is opgegeven tijdens het invullen van het formulier groter is dan 5.

**Optie 1: gebruiken [!DNL Experience Manager Forms] De API ValidateCAPTCHA om CAPTCHA te valideren met behulp van een aangepaste verzendactie**

Voer de volgende stappen uit om de `ValidateCAPTCHA` API om CAPTCHA te valideren met behulp van een aangepaste verzendhandeling:

1. Voeg het script toe dat het `ValidateCAPTCHA` API voor aangepaste verzendhandeling. Zie voor meer informatie over aangepaste verzendhandelingen [Een aangepaste verzendactie maken voor Adaptieve Forms](custom-submit-action-form.md).
1. Selecteer de naam van de aangepaste handeling Verzenden in het menu **[!UICONTROL Submit Action]** vervolgkeuzelijst in **[!UICONTROL Submission]** eigenschappen van een adaptief formulier.
1. Tik op **[!UICONTROL Submit]**. De CAPTCHA wordt gevalideerd op basis van de in `ValidateCAPTCHA` API van de aangepaste handeling Verzenden.

**Optie 2: Gebruik [!DNL Experience Manager Forms] De API van ValidateCAPTCHA om CAPTCHA op een gebruikersactie te bevestigen alvorens de vorm voor te leggen**

U kunt ook `ValidateCAPTCHA` API door regels toe te passen op een component in een adaptief formulier.

U voegt bijvoorbeeld een **[!UICONTROL Validate CAPTCHA]** in een adaptief formulier en maak een regel om een service aan te roepen bij het klikken op een knop.

Het volgende cijfer illustreert hoe u de dienst op de klik van een **[!UICONTROL Validate CAPTCHA]** knop:

![CAPTCHA valideren](assets/captcha-validation1.gif)

U kunt de aangepaste servlet die omvat aanroepen `ValidateCAPTCHA` API die de regelredacteur gebruikt en laat of maakt de verzendknoop van het Aangepaste Vorm toe die op het bevestigingsresultaat wordt gebaseerd.

Op dezelfde manier kunt u regeleditor gebruiken om een aangepaste methode op te nemen om CAPTCHA in een adaptief formulier te valideren.

### Aangepaste CAPTCHA-services toevoegen {#add-custom-captcha-service}

[!DNL Experience Manager Forms] verleent reCAPTCHA als dienst CAPTCHA. U kunt echter een aangepaste service toevoegen die u in het dialoogvenster **[!UICONTROL CAPTCHA Service]** vervolgkeuzelijst.

Hieronder volgt een voorbeeldimplementatie van de interface voor het toevoegen van extra CAPTCHA-service aan uw adaptieve formulier:

```javascript
package com.adobe.aemds.guide.service;

import org.osgi.annotation.versioning.ConsumerType;

/**
 * An interface to provide captcha validation at server side in Adaptive Form
 * This interface can be used to provide custom implementation for different captcha services.
 */
@ConsumerType
public interface GuideCaptchaValidator {
    /**
     * This method should define the actual validation logic of the captcha
     * @param captchaPropertyNodePath path to the node with CAPTCHA configurations inside form container
     * @param userResponseToken  The user response token provided by the CAPTCHA from client-side
     *
     * @return  {@link GuideCaptchaValidationResult} validation result of the captcha
     */
     GuideCaptchaValidationResult validateCaptcha(String captchaPropertyNodePath, String userResponseToken);

    /**
     * Returns the name of the captcha validator. This should be unique among the different implementations
     * @return  name of the captcha validator
     */
     String getCaptchaValidatorName();
}
```

`captchaPropertyNodePath` Verwijst naar de middelweg van de component CAPTCHA in de Verschuivende bewaarplaats. Gebruik deze eigenschap om specifieke details voor de component CAPTCHA op te nemen. Bijvoorbeeld: `captchaPropertyNodePath` omvat informatie voor de reCAPTCHA wolkenconfiguratie die op de component CAPTCHA wordt gevormd. De informatie over de cloudconfiguratie biedt **[!UICONTROL Site Key]** en **[!UICONTROL Secret Key]** instellingen voor de implementatie van de reCAPTCHA-service.

`userResponseToken` verwijst naar de `g_recaptcha_response` die wordt gegenereerd nadat een CAPTCHA in een formulier is opgelost.

### reCAPTCHA-servicedomein bewerken {#reCAPTCHA-service-domain}

reCAPTCHA-service gebruikt `https://www.recaptcha.net/` als het standaarddomein. U kunt de in te stellen instellingen wijzigen `https://www.google.com/` of een aangepaste domeinnaam voor het laden, renderen en valideren van de reCAPTCHA-service.

Stel de **[!UICONTROL af.cloudservices.recaptcha.domain]** eigendom van de **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]** te specificeren configuratie `https://www.google.com/` of een andere aangepaste domeinnaam. In het volgende JSON-bestand wordt een voorbeeld weergegeven:

```json
{
  "af.cloudservices.recaptcha.domain": "https://www.google.com/"
}
```

Om waarden van een configuratie te plaatsen, [OSGi-configuraties genereren met de AEM SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart), en [stel de configuratie op](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) naar de instantie Cloud Service.
