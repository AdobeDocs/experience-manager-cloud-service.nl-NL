---
title: Thema's maken en gebruiken
description: U kunt thema's gebruiken om een adaptief formulier te stileren en een visuele identiteit te geven met behulp van kerncomponenten. U kunt een thema delen voor elk gewenst aantal Adaptive Forms.
source-git-commit: 1357b36dc3d14d2ceceb6761cb005b592472890a
workflow-type: tm+mt
source-wordcount: '1654'
ht-degree: 0%

---


# Thema&#39;s in adaptieve Forms (kerncomponenten) {#themes-for-af-using-core-components}

U kunt thema&#39;s maken en toepassen om een adaptief formulier te stileren met behulp van kerncomponenten. Een thema bevat opmaakgegevens voor de componenten en deelvensters. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, weerspiegelt de opgegeven stijl de corresponderende componenten. Thema wordt onafhankelijk beheerd zonder verwijzing naar een adaptief formulier.

Wanneer u [een adaptief formulier maken](/help/forms/creating-adaptive-form.md) met behulp van kerncomponenten worden de thema&#39;s Out-of-Box weergegeven onder de **Stijl** tab. Standaard worden alleen de **Canvas** thema is beschikbaar.

>[!NOTE]
>
>Een adaptief formulierthema mag niet worden verward met [Aangepaste formuliersjablonen.](/help/forms/template-editor.md) De thema&#39;s Adaptief formulier bevatten alleen de opmaakgegevens voor een adaptief formulier. Aangepaste formuliersjablonen definiëren de formulierstructuur en de initiële inhoud en bevatten een thema voor het maken van nieuwe [Adaptief formulier.](/help/forms/creating-adaptive-form.md)

## Canvas-thema gebruiken in Adaptief Forms met behulp van kerncomponenten {#using-theme-in-adaptive-form}

De stappen voor het toepassen van thema op een adaptief formulier zijn:

1. Meld u aan bij de AEM Forms-auteur.

1. Tikken **Adobe Experience Manager** > **Forms** > **Forms &amp; Documenten**.

1. Klikken **Maken** > **Adaptieve Forms**. De wizard voor het maken van adaptief formulier wordt geopend.

1. Selecteer de sjabloon voor de kerncomponent in het dialoogvenster **Bron** tab.

   >[!NOTE]
   >
   > Wanneer u een adaptief formulier maakt met kerncomponenten, ziet u het thema Canvas onder het tabblad Stijl. Dit is het enige Out-of-the-Box-thema dat momenteel beschikbaar is. Maar u kunt het thema aan uw het houden van veranderen en het voor toekomstig gebruik bewaren door opstelling een frontend pijpleiding.

1. Selecteer het thema Canvas in het dialoogvenster **Stijl** tab.
1. Klikken **Maken**.

De thema&#39;s Adaptief formulier worden gebruikt als onderdeel van een adaptieve formuliersjabloon om opmaak te definiëren terwijl u een adaptief formulier maakt.

## Het thema aanpassen {#customizing-theme}

Als u een thema wilt aanpassen,

* [Een pijplijn instellen in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#setup-pipeline)
* Een gebruiker configureren met de [contributierol](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/assign-profiles-aem.html).
* U moet een [basiskennis van Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#accessing-git) en Cloud Service Git repositories.

Een Canvasthema aanpassen:
1. [Het thema Canvas klonen](#1-download-canvas-theme-download-canvas-theme)
1. [De structuur van het thema begrijpen](#2-understand-structure-of-the-canvas-theme-structure-of-canvas-theme)
1. [Naam wijzigen in package.json en package_lock.json](#changename-packagelock-packagelockjson)
1. [Maak de ](#3-create-the-env-file-in-a-theme-folder-creating-env-file-theme-folder)
1. [De lokale proxyserver starten](#4-start-a-local-proxy-server-starting-a-local-proxy-server)
1. [Het thema aanpassen](#customize-the-theme-customizing-theme)
1. [De wijzigingen vastleggen](#6-committing-the-changes-committing-the-changes)
1. [De pijplijn implementeren](#7-deploying-the-customized-theme-deploy-customized-theme)

### 1. Het thema Canvas klonen {#download-canvas-theme}

Open de opdrachtprompt en voer de volgende opdracht uit om het canvasthema te klonen:

```
git clone https://github.com/adobe/aem-forms-theme-canvas
```

>[!NOTE]
>
> Op het tabblad Stijl van de wizard Formulier maken wordt dezelfde themanaam weergegeven als in het bestand package.json.

### 2. De structuur van het thema begrijpen {#structure-of-canvas-theme}

Een adaptief formulierthema is een pakket met de CSS-, JavaScript- en statische bronnen die de opmaak van uw formulier definiëren en die voldoet aan de structuur van een adaptief formulierthema. Een adaptief thema van de Vorm heeft de volgende structuur typisch voor een front-end project:

* `src/components`: JavaScript- en CSS-bestanden die specifiek zijn voor AEM kerncomponenten
* `src/resources`: Statische bestanden zoals pictogrammen, logo&#39;s en lettertypen
* `src/site`: JavaScript- en CSS-bestanden die van toepassing zijn op de gehele AEM Sites-pagina
* `src/theme.ts`: Het belangrijkste ingangspunt van uw thema JavaScript en CSS
* `src\theme.scss`: JavaScript- en CSS-bestanden die van toepassing zijn op het hele thema

De `src/components` de map bevat JavaScript- en CSS-bestanden die specifiek zijn voor alle AEM kerncomponenten, zoals knop, selectievakje, container, voettekst enzovoort. U kunt een stijl voor de knop of het selectievakje instellen door het CSS-bestand te bewerken dat specifiek is voor de AEM.

![Het thema bewerken](/help/forms/assets/theme_structure.png)

Als u het thema wilt aanpassen, kunt u de lokale proxyserver starten om de themaaanpassingen in real-time weer te geven op basis van de werkelijke AEM.

### 3. Naam wijzigen in het thema package.json en package_lock.json van Canvas {#changename-packagelock-packagelockjson}

De naam en versie van het Canvas-thema bijwerken in het dialoogvenster `package.json` en `package_lock.json` bestanden.

>[!NOTE]
>
> Namen mogen niet `@aemforms` tag. Het moet eenvoudige tekst zijn als door de gebruiker opgegeven naam.

![Canvasthema-onderwerp](/help/forms/assets/changename_canvastheme.png)

### 4. Het .env-bestand maken in een themamap {#creating-env-file-theme-folder}

Een `.env` in de themamap en voeg de volgende parameters toe:

* **AEM URL**
AEM_URL=https://[auteur-instance]

* **AEM sitenaam**
AEM_ADAPTIVE_FORM=Form_name

* **Proxypoort AEM**
AEM_PROXY_PORT=7000


![Structuur van canvasthema](/help/forms/assets/env-file-canvas-theme.png)

### 5. Een lokale proxyserver starten {#starting-a-local-proxy-server}

1. Navigeer vanaf de opdrachtregel naar de basis van het thema op uw lokale computer.
1. Uitvoeren `npm install` en npm wint gebiedsdelen terug en installeert het project.
1. Uitvoeren `npm run live` en de proxyserver wordt gestart.

   ![npm live](/help/forms/assets/theme_proxy.png)


1. Tik of klik op **LOKAAL AANMELDEN (ALLEEN TAKEN BEHEREN)** en meld u aan met de gegevens van de proxygebruiker die u van de AEM beheerder hebt ontvangen.

   ![Lokaal aanmelden](/help/forms/assets/local_signin.png)

   >[!NOTE]
   >
   > * Maak een lokale gebruiker om zich lokaal aan te melden. Bied de rol van contribuant aan de themaontwerper.
   > * Als u de AEM-URL opgeeft als `http://localhost:[port]/` in de `.env` bestand met Canvas-thema. U wordt rechtstreeks omgeleid naar de browser.


1. Als u zich eenmaal hebt aangemeld, wijzigt u de URL in de browser zodat deze verwijst naar het pad naar de voorbeeldinhoud die de AEM aan u heeft gegeven.

   * Als het opgegeven pad bijvoorbeeld `/content/formname.html?wcmmode=disabled`wijzigt u de URL in `http://localhost:[port]/content/forms/af/formname.html?wcmmode=disabled`

   ![Inhoud van proxy&#39;s](/help/forms/assets/sample_af.png)

Navigeer naar een adaptief formulier om het Canvas-thema weer te geven dat is toegepast op een adaptief formulier.

### 6. Het thema aanpassen {#customize-theme}

1. Open het bestand in de editor `<your-theme-sources>/src/site/_variables.scss`.

   >[!NOTE]
   >
   > U kunt alle componenten van het Adaptief formulier in een site rechtstreeks opmaken door het gereedschap `site/_variables.scss` bestand.

1. De variabele voor de `font colour` tot `red`.

   ![Thema bewerken](/help/forms/assets/edit_theme.png)

   **Stijl de verschillende AEM componenten**

   U kunt de verschillende componenten van een adaptief formulier opmaken door het CSS-bestand ervan in de editor te wijzigen. Er zijn verschillende CSS-mappen voor elke kerncomponent Adaptief formulier in de map Canvasthema.

   ![Basiscomponent](/help/forms/assets/theme-component.png)

   Als u stijlen voor een specifieke component in de themaeditor wilt opgeven, kunt u de CSS in een themamap bewerken. Als u bijvoorbeeld de randkleur van een tekstvakveld wilt wijzigen, opent u het CSS-bestand in de editor en wijzigt u de randkleur.

   ![CSS van tekstvak bewerken](/help/forms/assets/edit_color_textbox.png)

1. Wanneer u het bestand opslaat, herkent de proxyserver de wijziging via de regel `[Browsersync] File event [change]`.

   ![Proxy browsersync](/help/forms/assets/browser_sync.png)

1. Als u terugschakelt naar uw browser van de lokale proxyserver, is de wijziging direct zichtbaar.

   ![AF-thema wijzigen](/help/forms/assets/edit_theme_af.png)

De themaontwerper bekijkt de veranderingen in de lokale volmachtsserver en past het thema volgens de vereisten voor verschillende AEM componenten aan.

Voordat u de wijzigingen doorvoert in de AEM Git-opslagplaats, hebt u toegang nodig tot uw [Gegevens opslagplaats ophalen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git).

### 7. De wijzigingen vastleggen {#committing-the-changes}

Nadat u wijzigingen in het thema hebt aangebracht en het met een lokale proxyserver hebt getest, past u de wijzigingen toe op de Git-opslagplaats van uw AEM Forms-Cloud Service. Het maakt het aangepaste thema beschikbaar in uw Forms Cloud Service-omgeving voor gebruik door Adaptive Forms-auteurs.

Voordat u wijzigingen aanbrengt in de Git-opslagplaats van uw AEM Forms-Cloud Service, hebt u een kloon van de opslagplaats op uw lokale computer nodig. De gegevensopslagruimte klonen:

1. Maak een nieuwe themaopslagplaats door op de knop **[!UICONTROL Repositories]** optie.

   ![nieuwe themarepo maken](/help/forms/assets/createrepo_canvastheme.png)

1. Klikken **[!UICONTROL Add Repository]** en de **Naam opslagplaats** in de **Opslagplaats toevoegen** in. Klik op **[!UICONTROL Save]**.

   ![Repo Canvasthema toevoegen](/help/forms/assets/addcanvasthemerepo.png)

1. Klikken **[!UICONTROL Copy Repository URL]** om de URL van de gemaakte opslagplaats te kopiëren.

   ![URL van Canvasthema](/help/forms/assets/copyurl_canvastheme.png)

1. Open de opdrachtprompt en kloon de hierboven gemaakte cloudopslagplaats.

   ```
   git clone https://git.cloudmanager.adobe.com/aemforms/Canvasthemerepo/
   ```

1. Verplaats de bestanden van de themaopslagplaats die u bewerkt naar de cloudopslagplaats met een opdracht die lijkt op
   `cp -r [source-theme-folder]/* [destination-cloud-repo]`
Gebruik bijvoorbeeld deze opdracht 
`cp -r [C:/cloned-git-canvas/*] [C:/cloned-repo]`
1. Wijs in de directory van de cloudopslagplaats de themabestanden waar u naartoe hebt verplaatst toe met de volgende opdrachten.

   ```text
   git add .
   git commit -a -m "Adding theme files"
   git push
   ```

1. De aanpassingen worden doorgestuurd naar de Git-opslagplaats.

   ![Toegestane wijzigingen](/help/forms/assets/cmd_git_push.png)

Uw aanpassingen worden nu veilig opgeslagen in de Git-opslagplaats.


### 8. De frontend pijpleiding in werking stellen {#deploy-pipeline}

1. Creeer de front-end pijpleiding om het aangepaste thema op te stellen. Meer informatie [hoe te opstelling een frontline pijpleiding om aangepast thema op te stellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#setup-pipeline).
1. Stel de gecreeerde frontend pijpleiding in werking om aangepaste themamap onder te stellen **[!UICONTROL Style]** van een wizard voor het maken van adaptieve formulieren.

>[!NOTE]
>
>In de toekomst als u om het even welke wijzigingen in de de themamap van het Canvas aanbrengt, moet u de bovengenoemde pijpleiding opnieuw uitvoeren. Daarom moet de naam van de pijpleiding in herinnering worden gebracht.

## Voorbeeld om het thema aan te passen {#example-to-customize-a-theme}

1. Meld u aan bij de AEM Forms-auteur.
1. Open een adaptief formulier dat is gemaakt met behulp van kerncomponenten.
1. Start de lokale proxyserver met de opdrachtprompt en klik op **LOKAAL AANMELDEN (ALLEEN TAKEN BEHEREN)**.
1. Nadat u zich hebt aangemeld, wordt u omgeleid naar de browser en ziet u het toegepaste thema.
1. Download de [Canvasthema](https://github.com/adobe/aem-forms-theme-canvas) en extraheer de gedownloade ZIP-map.
1. Open de uitgepakte ZIP-map in de gewenste editor.
1. Een `.env` bestand in de themamap en voeg parameters toe: **URL AEM**, **AEM_ADAPTIVE_FORM** en **AEM_PROXY_PORT**.
1. Open het CSS-bestand van het tekstvak in de themamap Canvas en wijzig de kleur van de rand in &#39;&#39;Zeg&#39;&#39; `red` kleur en sla de wijzigingen op.
1. Open de browser opnieuw en u ziet dat de wijzigingen direct zichtbaar zijn in een adaptief formulier.
1. Verplaats de canvasthemamap in uw gekloonde opslagplaats.
1. Leg de wijzigingen vast en voer de pijplijn naar voren uit.

Zodra de pijpleiding wordt uitgevoerd, is het thema beschikbaar onder het lusje van de Stijl.

## Aanbevolen procedures {#best-practices}

* **Elementen uit een ander thema verwijderen**

   Wanneer u een thema bewerkt, kunt u door elementen (zoals afbeeldingen) bladeren en elementen uit andere thema&#39;s toevoegen. U bewerkt bijvoorbeeld de achtergrond van een pagina. Wanneer u bijvoorbeeld **[!UICONTROL Page]** ![bewerken, knop](assets/edit-button.png)> **[!UICONTROL Background]** > **[!UICONTROL Add]** > **[!UICONTROL Image]** Er wordt een dialoogvenster weergegeven waarin u afbeeldingen in andere thema&#39;s kunt zoeken en toevoegen.

   U kunt problemen met uw huidige thema oplossen als een element wordt toegevoegd uit een ander thema en het andere thema wordt verplaatst of verwijderd. U wordt aangeraden te voorkomen dat u bladeren en elementen uit andere thema&#39;s toevoegt.

* **De lay-outbreedte van het containervenster wijzigen**

   Het wordt niet aanbevolen de lay-outbreedte van het containervenster te wijzigen. Wanneer u de breedte van een containerdeelvenster opgeeft, wordt het statisch en wordt het niet aangepast aan verschillende weergaven.

* **Formuliereditor of themaeditor gebruiken voor het werken met kop- en voettekst**

   Gebruik de themaeditor als u koptekst en voettekst wilt opmaken met opmaakopties zoals letterstijl, achtergrond en transparantie.
Gebruik de opties voor de formuliereditor als u informatie wilt opgeven, zoals een logoafbeelding, een bedrijfsnaam in de koptekst en copyrightinformatie in de voettekst.
