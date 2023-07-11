---
title: Elektronische handtekeningen toepassen op een formulier met scripthandtekeningen
seo-title: Apply electronic signatures to a form using scribble signatures
description: Formulieren ondertekenen met behulp van krabbelen
seo-description: Signing forms using scribble
uuid: ffeba886-9b24-4ed1-95c0-e19356ff2f23
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 76d178d1-8e40-41b3-80d4-66b2f8d04211
docset: aem65
google-site-verification: A1dSvxshSAiaZvk0yHu7-S3hJBb1THj0CZ2Uh8N_ck4
exl-id: dc89ecb1-2d9e-4d1d-b85b-af90c550e7d8
source-git-commit: fce6a3dff4136aa9ea94f5fdd03dd7a6341b8a9d
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# Elektronische handtekeningen toepassen op een formulier met scripthandtekeningen{#apply-electronic-signatures-to-a-form-using-deprecated-scribble-signatures}

U kunt de **Krabbelhandtekening** en **Handtekeningstap** te tekenen (krabbelen) handtekening op een adaptief formulier. In de stapcomponent Handtekening wordt een PDF-versie van het adaptieve formulier weergegeven. Als u de stapcomponent Handtekening wilt gebruiken, hebt u een optie Document of Record ingeschakeld of een op een formuliersjabloon gebaseerde Adaptieve Forms nodig.

![Dialoogvenster Krabbelen](assets/scribble-signature.png)

## Verschillende opties beschikbaar in het venster Handtekening

* **A:** Klik op de knop **Tekenpenseel** pictogram om uw handtekening op canvas te tekenen.
* **B:** Klik op de knop **Wissen** pictogram om de handtekening op het canvas te wissen.
* **C:** Klik op de knop **Geolocation** pictogram om geolocatie toe te voegen samen met de handtekening.
* **D:** Klik op de knop **Toetsenbord** pictogram om uw naam op canvas te typen.

Zodra u gereed tikt ![aem_forms_save](assets/aem_forms_save.png) in het venster Krabbelhandtekening kunt u de handtekening niet bewerken. Als u de handtekening wilt bewerken, moet u de huidige handtekening negeren en opnieuw ondertekenen met de bovenstaande optie Penseel/toetsenbord.

U kunt tikken op de knop **Configureren** ![Configuratiepictogram](assets/configure.png) pictogram om de hoogte-breedteverhouding van het canvas voor Krabbelhandtekeningen in te stellen.
* Wanneer de hoogte-breedteverhouding van het canvas voor Krabbelhandtekeningen kleiner is dan 1, worden de gegevens over de geolocatie toegevoegd onder aan het canvas voor Krabbelhandtekeningen.


* Wanneer de hoogte-breedteverhouding van het canvas voor Krabbelhandtekeningen groter is dan 1, wordt de informatie over de geolocatie toegevoegd aan de rechterkant van het canvas voor Krabbelhandtekeningen.


![scripthandtekening onderaan](assets/scribble-signature-aspectratio.PNG)



>[!NOTE]
>
>Handtekeningen worden altijd opgeslagen in de PNG-indeling.
>

## Een adaptief formulier configureren voor het gebruik van een scripthandtekening {#configure-an-adaptive-form-to-use-scribble-signature}

1. Maak een optie Document of Record ingeschakeld of maak een op een formuliersjabloon gebaseerd adaptief formulier. Voor geleidelijke informatie, zie [Een adaptief formulier maken](creating-adaptive-form.md).
1. Sleep de **Krabbelhandtekening** van componentbrowser naar het adaptieve formulier.
1. Tik op de knop **Configureren** ![vormen](assets/configure.png) pictogram. De eigenschappenbrowser wordt geopend en de eigenschappen van de component Krabbelen handtekening worden weergegeven. Configureer eigenschappen van de component Krabbelhandtekening.
1. Sleep de component Signature Step van de componentbrowser naar het Adaptieve formulier.

   >[!NOTE]
   >
   >De component voor de stap Handtekening gebruikt de volledige breedte die beschikbaar is voor het formulier. Het wordt aanbevolen geen andere component op te nemen in de sectie die de component voor de stap Handtekening bevat.

1. Tik in de Inhoudsbrowser op **Formuliercontainer** en tik op de knop **Configureren** ![](assets/configure.png) pictogram. De eigenschappenbrowser wordt geopend en de eigenschappen van de container Adaptief formulier worden weergegeven. Navigeren naar **Aangepaste formuliercontainer** > **Elektronische handtekening** en deselecteer de **Adobe Sign inschakelen** optie. Tik op Gereed ![aem_forms_save](assets/aem_forms_save.png) om de wijzigingen op te slaan.

   >[!NOTE]
   >
   >Wanneer u een component Handtekeningstap toevoegt aan een adaptief formulier, wordt de optie Adobe Sign inschakelen automatisch geselecteerd.

1. Tik op de knop **Configureren** ![vormen](assets/configure.png) pictogram. De eigenschappenbrowser wordt geopend en de eigenschappen voor stap Handtekening worden weergegeven. Configureer de volgende eigenschappen:

   * **Elementnaam**: Geef de naam van de component op.

   * **Titel:** Geef een unieke titel van de component op.
   * **Sjabloonbericht:** Geef het bericht op dat moet worden weergegeven wanneer de PDF van de handtekening wordt geladen. Adobe Sign-services hebben enige tijd nodig om de PDF van de handtekening voor te bereiden en te laden.
   * **Ondertekeningsservice:** Selecteer **Krabbelhandtekening** optie.

   * **CSS-klasse**: Geef eventueel de CSS-klasse van de clientbibliotheek op. Het wordt aanbevolen [thema&#39;s](themes.md) en [inline stijlen](inline-style-adaptive-forms.md) in plaats van CSS-klasse.

   Tik op Gereed ![aem_forms_save](assets/aem_forms_save.png) om de wijzigingen op te slaan. De handtekening is geconfigureerd.

   Wanneer u nu een formulier invult, wordt een PDF-versie van het adaptieve formulier weergegeven en worden opties voor de ondertekening van het PDF-document weergegeven. Zie voor meer informatie [Een adaptief formulier ondertekenen met behulp van een scripthandtekening](signing-forms-using-scribble.md#sign-an-adaptive-form-using-scribble-signature).

## Een adaptief formulier ondertekenen met behulp van een scripthandtekening {#sign-an-adaptive-form-using-scribble-signature}

1. Nadat u een adaptief formulier hebt ingevuld en de pagina Stap handtekening hebt bereikt, wordt het handtekeningscherm weergegeven.

   ![Handtekeningscherm voor EchoSign-pagina](assets/esignscribblesign.jpg)

1. Klik op **[!UICONTROL Sign]**. Het dialoogvenster Scriptteken wordt weergegeven. Onderteken het formulier en klik op Gereed ![aem_forms_save](assets/aem_forms_save.png) pictogram om de handtekening op te slaan.

   ![Dialoogvenster Krabbelen](assets/scribblewidget.png)

1. Klik op Voltooien om het ondertekeningsproces te voltooien.

   ![Voltooi het ondertekeningsproces](assets/scribblecomplete.jpg)

De handtekeningen worden toegevoegd aan het formulier en het formulierbesturingselement gaat naar het volgende venster.
