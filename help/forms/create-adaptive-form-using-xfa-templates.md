---
title: Hoe maakt u een adaptief formulier op basis van kerncomponenten met behulp van XFA-formuliersjablonen?
description: Leer hoe te om een Aangepast Vorm tot stand te brengen gebruikend  [!DNL Experience Manager Forms]  gebruikend XFA vormmalplaatjes of XDP dossiers.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
exl-id: f3c9b798-8b20-4674-9b96-a3a0b143d947
source-git-commit: 5b55a280c5b445d366c7bf189b54b51e961f6ec2
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 0%

---

# Een adaptief formulier maken (kerncomponenten) op basis van XFA-formuliersjablonen

<span class="preview"> De functie is beschikbaar in het programma voor vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

AEM as a Cloud Service biedt gebruikers de mogelijkheid om Adaptief Forms te maken op basis van Core Components met behulp van XFA (XML Forms Architecture)-formuliersjablonen of `*.XDP` (XML Data Package)-bestanden. Met deze functie kunnen gebruikers tijd besparen door velden van XFA-formuliersjablonen of XDP-bestanden rechtstreeks te migreren naar Adaptive Forms.

U kunt uw XFA-formuliersjablonen of XDP-formuliersjablonen opnieuw gebruiken om adaptieve Forms te maken op basis van kerncomponenten. Als u een XFA-formuliersjabloon of XDP-bestanden opnieuw wilt gebruiken, uploadt en koppelt u deze aan een adaptief formulier. De elementen van de XFA-formuliersjabloon of XDP-bestanden worden beschikbaar voor gebruik in de zoekfunctie voor inhoud tijdens het ontwerpen van adaptieve formulieren. Vanuit de Inhoudszoeker kunt u de formuliersjabloonelementen naar het formulier slepen.

## Voordelen van het maken van formulieren op basis van XFA-formuliersjablonen of XDP-bestanden

Enkele voordelen van het maken van formulieren op basis van XFA-formuliersjablonen of XDP-bestanden zijn:

* **de besparingen van de Tijd**: U kunt bestaande XFA vormmalplaatjes (XDP dossiers) snel opnieuw gebruiken zonder het moeten de vormstructuur opnieuw creëren, die tijd en inspanning tijdens het auteursproces besparen.
* **Efortless migratie**: Als u reeds XFA vormmalplaatjes in gebruik hebt, verstrekt deze optie een gemakkelijke migratieweg aan Adaptief Forms, die u toestaat om uit de voordelen van de moderne Componenten van de Kern van AEM voordeel te halen zonder bestaande vormgegevens en logica te verliezen.
* **Verbeterde gebruikerservaring**: De adaptieve Forms is ontvankelijker en klantgericht dan vormen XFA. Door over te schakelen op Adaptive Forms kunt u een gebruiksvriendelijkere ervaring garanderen voor verschillende apparaten en schermgrootten.
* **Verbeterde integratie**: De adaptieve Forms integreert beter met andere eigenschappen, zoals werkschema&#39;s, gegevensband, en vormverklaringen, toelatend soepelere werkschema&#39;s en beter algemeen vormbeheer.

## Voorwaarden


* Aanbevolen wordt kennis te maken met de volgende gebieden:
   * Een adaptief formulier maken
   * XFA (XML Forms Architecture)

## Hoe maakt u een adaptief formulier met behulp van een XFA-formuliersjablonen of XDP-bestanden?

Voer de volgende stappen uit om een adaptief formulier te maken met behulp van XFA- of XDP-formuliersjablonen:

1. Meld u aan bij de auteurinstantie van [!DNL Experience Manager Forms] .
1. Voer uw referenties in op de Experience Manager-aanmeldingspagina. Nadat u zich hebt aangemeld, selecteert u in de linkerbovenhoek **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .

   ![ Forms en Documenten ](/help/forms/assets/create-fdm.png)

1. Selecteer **[!UICONTROL Create]** > **[!UICONTROL Adaptive Forms]** .

   ![ creeer Aangepaste Vorm ](/help/forms/assets/create-af.png)

   De wizard Formulier maken wordt geopend.
1. In het **Source** lusje, selecteer een malplaatje dat op de Componenten van de Kern wordt gebaseerd.

   ![ Uitgezochte malplaatje ](/help/forms/assets/select-template.png)

   Wanneer u een sjabloon selecteert, wordt de in de sjabloon opgegeven actie voor het thema en het verzenden automatisch geselecteerd en wordt de knop **[!UICONTROL Create]** ingeschakeld.

   ![ Uitgezochte thema ](/help/forms/assets/select-form-theme.png)

1. Selecteer **[!UICONTROL Create]**. Er wordt een dialoogvenster weergegeven waarin u de titel, naam en locatie voor het opslaan van het adaptieve formulier kunt opgeven.
1. Geef de titel, naam en locatie op.
1. Selecteer **[!UICONTROL Create]** .
   ![ verstrekken naam en titel ](/help/forms/assets/create-form.png)

   Er wordt een adaptief formulier gemaakt en geopend in de Adaptive Forms-editor. De redacteur toont de inhoud beschikbaar in het malplaatje.
1. Selecteer ![ de informatie van de Pagina ](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Open Properties]**.

   ![ Open eigenschappen ](/help/forms/assets/form-properties.png)

   De pagina Formuliereigenschappen wordt geopend.
1. Ga naar het **[!UICONTROL Form Model]** lusje en kies **Malplaatjes van de Vorm**.
1. Selecteer het .xdp- dossier van de dropdown lijst.

   ![ Uitgezochte XDP dossier ](/help/forms/assets/select-xdp-file.png)

   Er verschijnt een waarschuwingsvenster op het scherm. Klik **O.K.** om verder te gaan.

   ![ de Dialoog van de Waarschuwing ](/help/forms/assets/fdm-warning.png)

1. Selecteer **[!UICONTROL Save & Close]** om de eigenschappen op te slaan.

   >[!NOTE]
   >
   > Na het selecteren van **Malplaatjes van de Vorm** in het 2} Model **lusje van de Vorm, kan het niet worden veranderd.**


Er wordt een adaptief formulier gemaakt en geopend in de Adaptive Forms-editor. De redacteur toont de inhoud beschikbaar in het malplaatje.  Op basis van het type adaptief formulier worden de formulierelementen in de bijbehorende XFA-formuliersjabloon weergegeven op het tabblad **[!UICONTROL Data Model Objects]** van de **[!UICONTROL Content Browser]** in de zijbalk. U kunt deze elementen ook slepen en neerzetten om het adaptieve formulier te maken.

>[!NOTE]
>
> U kunt scripts voor XDP-formuliervelden uitschakelen met de paneelwerkbalk van het toegevoegde veld. Creeer logics voor de toegevoegde gebieden gebruikend de [ Visuele Redacteur van de Regel ](/help/forms/rule-editor-core-components.md).

