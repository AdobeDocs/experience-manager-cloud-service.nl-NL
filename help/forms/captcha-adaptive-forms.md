---
title: CAPTCHA gebruiken in Adaptive Forms
seo-title: Using CAPTCHA in Adaptive Forms
description: Leer hoe u AEM CAPTCHA- of Google reCAPTCHA-service configureert in Adaptive Forms.
seo-description: Learn how to configure AEM CAPTCHA or Google reCAPTCHA service in Adaptive Forms.
uuid: 0e11e98a-12ac-484c-b77f-88ebdf0f40e5
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: adaptive_forms, author
discoiquuid: 4c53dfc0-25ca-419d-abfe-cf31fc6ebf61
docset: aem65
exl-id: 3fdbe5a3-5c3c-474d-b701-e0182da4191a
source-git-commit: a16da1b11cfe18910b2e57c0b6b668543dba46e3
workflow-type: tm+mt
source-wordcount: '1358'
ht-degree: 0%

---

# CAPTCHA gebruiken in Adaptive Forms{#using-captcha-in-adaptive-forms}

CAPTCHA (Complete Automated Public Turing test to tell Computers and Humans Apart) is een programma dat vaak wordt gebruikt bij online transacties om onderscheid te maken tussen mensen en geautomatiseerde programma&#39;s of bots. Het stelt een uitdaging en evalueert de reactie van de gebruiker om te bepalen of het een mens of bot is die met de site communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige doeleinden posten.

[!DNL AEM Forms] biedt ondersteuning voor CAPTCHA in Adaptive Forms. U kunt de reCAPTCHA-service van Google gebruiken om CAPTCHA te implementeren.

>[!NOTE]
>
>* [!DNL AEM Forms] alleen reCaptcha v2 ondersteunen. Andere versies worden niet ondersteund.
>* CAPTCHA in Adaptive Forms wordt niet ondersteund in de offline modus [!DNL AEM Forms] app.
>

## De reCAPTCHA-service van Google configureren {#google-reCAPTCHA}

Auteurs van formulieren kunnen de reCAPTCHA-service van Google gebruiken om CAPTCHA te implementeren in Adaptive Forms. Het biedt geavanceerde CAPTCHA-mogelijkheden om uw site te beschermen. Voor meer informatie over hoe reCAPTCHA werkt, zie [Google reCAPTCHA](https://developers.google.com/recaptcha/).

![reCAPTCHA](assets/recaptcha_new.png)

De reCAPTCHA-service implementeren in [!DNL AEM Forms]:

1. Verkrijgen [reCAPTCHA API-sleutelpaar](https://www.google.com/recaptcha/admin) uit Google. De site bevat een sleutel en een geheim.
1. Configuratiecontainer maken voor cloudservices.

   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]**.
      * Zie de [Configuratiebrowser](https://experienceleague.adobe.com/docs/experience-manager-65/administering/introduction/configurations.html?lang=en#introduction) documentatie voor meer informatie.
   1. Ga als volgt te werk om de algemene map voor cloudconfiguraties in te schakelen of sla deze stap over om een andere map voor cloudserviceconfiguraties te maken en te configureren.

      1. In Browser van de Configuratie, selecteer **[!UICONTROL global]** map en tik **[!UICONTROL Properties]**.

      1. Schakel in het dialoogvenster Configuratieeigenschappen de optie **[!UICONTROL Cloud Configurations]**.
      1. Tikken **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

   1. Tik in de configuratiebrowser op **[!UICONTROL Create]**.
   1. Geef in het dialoogvenster Configuratie maken een titel op voor de map en schakel **[!UICONTROL Cloud Configurations]**.
   1. Tikken **[!UICONTROL Create]** om de map te maken die is ingeschakeld voor configuraties van de cloudservice.

1. Configureer de cloudservice voor reCAPTCHA.

   1. Ga naar de Experience Manager auteur ![gereedschappen-1](assets/tools-1.png) > **[!UICONTROL Cloud Services]**.
   1. Tik op **[!UICONTROL reCAPTCHA]**. De pagina Configurations wordt geopend. Selecteer de configuratiecontainer die u in de vorige stap hebt gemaakt en tik op **[!UICONTROL Create]**.
   1. Geef Naam, Sitecode en Geheime sleutel voor de service reCAPTCHA op en tik op **[!UICONTROL Create]** om de configuratie van de cloudservice te maken.
   1. Geef in het dialoogvenster Component bewerken de site en de geheime sleutels op die in stap 1 zijn verkregen. Tikken **[!UICONTROL Save Settings]** en tik vervolgens op **[!UICONTROL OK]** om de configuratie te voltooien.

   Zodra de reCAPTCHA-service is geconfigureerd, is deze beschikbaar voor gebruik in Adaptive Forms. Zie voor meer informatie [CAPTCHA gebruiken in Adaptive Forms](#using-captcha).

## CAPTCHA gebruiken in Adaptive Forms {#using-captcha}

CAPTCHA gebruiken in Adaptive Forms:

1. Open een adaptief formulier in de bewerkingsmodus.

   >[!NOTE]
   >
   > Zorg ervoor dat de configuratiecontainer die is geselecteerd bij het maken van het adaptieve formulier, de reCAPTCHA-cloudservice bevat. U kunt ook de eigenschappen van Adaptief formulier bewerken om de configuratiecontainer die aan het formulier is gekoppeld, te wijzigen.

1. Sleep vanuit de componentbrowser de **[!UICONTROL Captcha]** naar het adaptieve formulier.

   >[!NOTE]
   >
   > * Het gebruik van meerdere Captcha-componenten in een adaptief formulier wordt niet ondersteund. Het wordt ook afgeraden om CAPTCHA te gebruiken in een deelvenster dat is gemarkeerd voor wazig laden of in een fragment.
   > * Captcha is tijdgevoelig en verloopt over ongeveer een minuut. Daarom wordt aangeraden de component Captcha vlak voor de knop Verzenden in het adaptieve formulier te plaatsen.

1. Selecteer de Captcha-component die u hebt toegevoegd en tik op ![cmppr](assets/configure-icon.svg) om de eigenschappen te bewerken.
1. Geef een titel op voor de CAPTCHA-widget. De standaardwaarde is **[!UICONTROL Captcha]**. Selecteren **[!UICONTROL Hide title]** als u de titel niet wilt weergeven.
1. Van de **[!UICONTROL Captcha service]** vervolgkeuzelijst, selecteert u **[!UICONTROL reCAPTCHA]** om de dienst reCAPTCHA toe te laten als u het zoals die in vormde [reCAPTCHA-service van Google](#google-reCAPTCHA). Selecteer een configuratie in het keuzemenu Instellingen.
1. Selecteer de tekst als **[!UICONTROL Normal]** of **[!UICONTROL Compact]** voor de reCAPTCHA-widget. U kunt ook de **[!UICONTROL Invisible]** optie om de CAPTCHA-uitdaging alleen aan te tonen in het geval van een verdachte activiteit. Het symbool dat wordt beveiligd door de reCAPTCHA-badge, hieronder, wordt weergegeven op de beveiligde formulieren.

   ![Google beveiligd door reCAPTCHA-badge](assets/google-recaptcha-v2.png)

   >[!NOTE]
   >
   > Niet selecteren **[!UICONTROL Default]** van de de dienstdrop-down van Captcha aangezien de standaard Experience ManagerCAPTCHA dienst wordt afgekeurd.

1. Sla de eigenschappen op.

De reCAPTCHA-service is ingeschakeld in het Adaptief formulier. U kunt een voorbeeld van het formulier bekijken en de CAPTCHA bekijken.

### CAPTCHA-component tonen of verbergen op basis van regels {#show-hide-captcha}

U kunt de component CAPTCHA weergeven of verbergen op basis van de regels die u toepast op een component in een adaptief formulier. Tik op de component en selecteer ![regels bewerken](assets/edit-rules-icon.svg)en tikken **[!UICONTROL Create]** om een regel te maken. Zie voor meer informatie over het maken van regels [Regeleditor](rule-editor.md).

De component CAPTCHA moet bijvoorbeeld alleen in een adaptief formulier worden weergegeven als het veld Waarde valuta in het formulier een waarde heeft van meer dan 25000.

Tik op de knop **[!UICONTROL Currency Value]** in het formulier en stel de volgende regels in:

![Regels tonen of verbergen](assets/rules-show-hide-captcha.png)

>[!NOTE]
>
> Als u de v2-configuratie reCAPTCHA selecteert met de grootte als [!UICONTROL Invisible] de optie tonen/verbergen is dan niet van toepassing.

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

**Optie 1: Gebruiken [!DNL Experience Manager Forms] De API ValidateCAPTCHA om CAPTCHA te valideren met behulp van een aangepaste verzendactie**

Voer de volgende stappen uit om de `ValidateCAPTCHA` API om CAPTCHA te valideren met behulp van een aangepaste verzendhandeling:

1. Voeg het script toe dat het `ValidateCAPTCHA` API voor aangepaste verzendhandeling. Voor meer informatie over aangepaste verzendhandelingen raadpleegt u [Een aangepaste verzendactie maken voor Adaptieve Forms](custom-submit-action-form.md).
1. Selecteer de naam van de aangepaste handeling Verzenden in het menu **[!UICONTROL Submit Action]** vervolgkeuzelijst in **[!UICONTROL Submission]** eigenschappen van een adaptief formulier.
1. Tik op **[!UICONTROL Submit]**. De CAPTCHA wordt gevalideerd op basis van de voorwaarden die zijn gedefinieerd in `ValidateCAPTCHA` API van de aangepaste handeling Verzenden.

**Optie 2: Gebruiken [!DNL Experience Manager Forms] De API van ValidateCAPTCHA om CAPTCHA op een gebruikersactie te bevestigen alvorens de vorm voor te leggen**

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

`captchaPropertyNodePath` Verwijst naar de middelweg van de component CAPTCHA in de Verschuivende bewaarplaats. Gebruik deze eigenschap om details op te nemen die specifiek zijn voor de component CAPTCHA. Bijvoorbeeld: `captchaPropertyNodePath` omvat informatie voor de reCAPTCHA wolkenconfiguratie die op de component CAPTCHA wordt gevormd. De informatie over de cloudconfiguratie biedt **[!UICONTROL Site Key]** en **[!UICONTROL Secret Key]** instellingen voor de implementatie van de reCAPTCHA-service.

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
