---
title: Site maken van sjabloon
description: Leer hoe u snel een AEM site kunt maken met een sitesjabloon.
exl-id: 31bb04c2-b3cc-44ca-b517-5b0d66d9b1fa
solution: Experience Manager Sites
feature: Developing
role: Admin, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1485'
ht-degree: 0%

---

# Site maken van sjabloon {#create-site-from-template}

Leer hoe u snel een AEM site kunt maken met een sitesjabloon.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM Snelle reis van de Plaats, [Begrijp Cloud Manager en de workflow voor snel maken van sites.](cloud-manager.md) U hebt geleerd hoe u Cloud Manager kunt maken en hoe u dit proces kunt koppelen aan het nieuwe proces voor het snel maken van sites. Nu moet u:

* Begrijp hoe AEM Sites en Cloud Manager samenwerken om de ontwikkeling op de voorgrond te vergemakkelijken
* Ontdek hoe de stap voor aanpassing volledig losgekoppeld is van AEM en geen AEM kennis vereist.

Dit artikel bouwt op die grondbeginselen voort zodat kunt u de eerste configuratiestap nemen en een plaats voor een malplaatje tot stand brengen dat u later kunt aanpassen gebruikend voorste-eindhulpmiddelen.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe u snel een AEM site kunt maken met een sitesjabloon. Na het lezen moet u:

* Begrijp hoe u AEM Sitesjablonen kunt verkrijgen.
* Leer hoe u een site maakt met een sjabloon.
* Zie hoe u de sjabloon van uw nieuwe site kunt downloaden en aan de front-end ontwikkelaar kunt leveren.

## Verantwoordelijke rol {#responsible-role}

Dit deel van de reis is op de AEM beheerder van toepassing.

## Sitesjablonen {#site-templates}

Sitesjablonen zijn een manier om basissite-inhoud te combineren tot een handig en herbruikbaar pakket. Sitesjablonen bevatten over het algemeen inhoud en structuur van de basissite en informatie over de siteopmaak om snel met de nieuwe site aan de slag te kunnen gaan. De werkelijke structuur is als volgt:

* `files`: Map met de UI-kit, XD bestand en mogelijk andere bestanden
* `previews`: Map met screenshots van de sitesjabloon
* `site`: Inhoudspakket van de inhoud die wordt gekopieerd voor elke site die met deze sjabloon wordt gemaakt, zoals paginasjablonen, pagina&#39;s enzovoort.
* `theme`: Bronnen van het sjabloonthema om de weergave van de site te wijzigen, zoals CSS, JavaScript enzovoort.

Sjablonen zijn krachtig omdat ze herbruikbaar zijn, zodat de auteurs van de inhoud snel een site kunnen maken. En aangezien u veelvoudige malplaatjes beschikbaar in uw AEM installatie kunt hebben, hebt u de flexibiliteit om aan diverse bedrijfsbehoeften te voldoen.

>[!NOTE]
>
>De sitesjabloon mag niet worden verward met paginasjablonen. Sitesjablonen die hier worden beschreven, definiëren de algemene structuur van een site. Een paginasjabloon definieert de structuur en initiële inhoud van een afzonderlijke pagina.

## Sitesjabloon verkrijgen {#obtaining-template}

De eenvoudigste manier om aan de slag te gaan is om [download de recentste versie van het AEM StandaardSjabloon van de Plaats van zijn bewaarplaats GitHub.](https://github.com/adobe/aem-site-template-standard/releases)

Nadat u het bestand hebt gedownload, kunt u het net als elk ander pakket uploaden naar de AEM. Zie de [Sectie Aanvullende bronnen](#additional-resources) voor details over hoe te met pakketten te werken als u meer informatie over dit onderwerp nodig hebt.

>[!TIP]
>
>Het AEM Standaard Sjabloon van de Plaats kan worden aangepast aan de behoeften van uw project en kan verdere aanpassing overbodig maken. Dit onderwerp valt echter buiten het bereik van deze reis. Zie de documentatie GitHub van het StandaardMalplaatje van de Plaats voor meer informatie.

>[!TIP]
>
>U kunt het malplaatje van bron als deel van uw projectwerkschema ook verkiezen om te bouwen. Dit onderwerp valt echter buiten het bereik van deze reis. Zie de documentatie GitHub van het StandaardMalplaatje van de Plaats voor meer informatie.

## Sjabloon van site installeren {#installing-template}

Het is eenvoudig om een site te maken met een sjabloon.

1. Onderteken in uw AEM ontwerpomgeving en navigeer naar de Sites-console

   * `https://<your-author-environment>.adobeaemcloud.com/sites.html/content`

1. Selecteren **Maken** rechtsboven in het scherm en in het keuzemenu selecteert u **Site van sjabloon**.

   ![Een nieuwe site maken op basis van een sjabloon](assets/create-site-from-template.png)

1. Selecteer in de wizard Site maken de optie **Importeren** boven aan de linkerkolom.

   ![Wizard Site maken](assets/site-creation-wizard.png)

1. Zoek de sjabloon in de bestandenbrowser [u hebt eerder gedownload](#obtaining-template) en selecteert u **Uploaden**.

1. Zodra het geüpload, verschijnt het in de lijst van beschikbare malplaatjes. Selecteer deze optie om deze te selecteren (zodat ook informatie over de sjabloon in de rechterkolom wordt weergegeven) en selecteer vervolgens **Volgende**.

   ![Een sjabloon selecteren](assets/select-site-template.png)

1. Geef een titel op voor uw site. U kunt een sitenaam opgeven of genereren op basis van de titel, als u deze weglaat.

   * De titel van de site wordt weergegeven in de titelbalk van browsers.
   * De sitenaam wordt onderdeel van de URL.

1. Selecteren **Maken** en de nieuwe site wordt gemaakt van de sitesjabloon.

   ![Details van de nieuwe site](assets/create-site-details.png)

1. Selecteer in het bevestigingsvenster dat wordt weergegeven **Gereed**.

   ![Dialoogvenster Succes](assets/success.png)

1. In de plaatsenconsole, is de nieuwe plaatsen zichtbaar en kan worden genavigeerd om zijn basisstructuur te onderzoeken zoals die door het malplaatje wordt bepaald.

   ![Nieuwe sitestructuur](assets/new-site.png)

Inhoudsauteurs kunnen nu beginnen met ontwerpen.

## Is verdere aanpassing vereist? {#customization-required}

Sitesjablonen zijn zeer krachtig en flexibel en elk gewenst aantal kan worden gemaakt voor een project, zodat u gemakkelijk sitescheidingen kunt maken. Afhankelijk van het niveau van aanpassing die reeds op het plaatsmalplaatje wordt uitgevoerd u gebruikt, kunt u zelfs geen extra front-end aanpassing nodig hebben.

* Gefeliciteerd als uw site geen extra aanpassing vereist! Uw reis eindigt hier!
* Als u nog extra front-end aanpassing nodig hebt, of als u eenvoudig het volledige proces wilt begrijpen voor het geval u toekomstige aanpassing nodig hebt, blijft het lezen.

## Voorbeeld van pagina {#example-page}

Als u extra front-end aanpassing vereist, houd in mening dat de front-end ontwikkelaar niet met de details van uw inhoud vertrouwd kan zijn. Daarom is het een goed idee om de ontwikkelaar van een weg aan typische inhoud te voorzien die als basis van verwijzing kan worden gebruikt aangezien het thema wordt aangepast. Een typisch voorbeeld is de homepage voor de hoofdtaal van de plaats.

1. Navigeer in de browser sites naar de homepage van de hoofdtaal van de site en selecteer vervolgens de pagina die u wilt selecteren en selecteer vervolgens **Bewerken** in de menubalk.

   ![Standaardstartpagina](assets/home-page-in-console.png)

1. Selecteer in de editor de optie **Pagina-informatie** in de werkbalk en vervolgens **Weergeven als gepubliceerd**.

   ![De startpagina bewerken](assets/home-page-edit.png)

1. Kopieer op het tabblad dat wordt geopend het pad van de inhoud van de adresbalk. Het zal er ongeveer zo uitzien `/content/<your-site>/en/home.html?wcmmode=disabled`.

   ![Homepage](assets/home-page.png)

1. Sla het pad op dat u later aan de front-end ontwikkelaar wilt geven.

## Het thema downloaden {#download-theme}

Nu de site is gemaakt, kan het thema van de site dat door de sjabloon wordt gegenereerd, worden gedownload en aan de front-end ontwikkelaar worden doorgegeven voor aanpassing.

1. Op de plaatsenconsole, toon **Site** spoorwegen.

   ![Trapper plaatsen](assets/show-site-rail.png)

1. Selecteer de hoofdmap van uw nieuwe site en selecteer **Themabronnen downloaden** in het terrein.

   ![Themabronnen downloaden](assets/download-theme-sources.png)

U hebt nu een kopie van de bronbestanden voor thema&#39;s in uw downloadbestanden.

## Proxy-gebruiker instellen {#proxy-user}

Als u wilt dat de ontwikkelaar aan de voorzijde de aanpassingen voorvertoont met behulp van werkelijke AEM inhoud van uw site, moet u een proxygebruiker instellen.

1. Ga in AEM van hoofdnavigatie naar **Gereedschappen** > **Beveiliging** > **Gebruikers**.
1. Selecteer in de gebruikersbeheerconsole de optie **Maken**.

   ![Gebruikersbeheerconsole](assets/user-management-console.png)
1. In de **Nieuwe gebruiker maken** venster moet u minstens verstrekken:
   * **ID** - Neem nota van deze waarde aangezien u het aan de front-end ontwikkelaar moet verstrekken.
   * **Wachtwoord** - Sla deze waarde veilig op in een wachtwoordkluis omdat u deze aan de front-end ontwikkelaar moet doorgeven.

   ![Nieuwe gebruikersgegevens](assets/new-user-details.png)

1. Op de **Groepen** -tab, voegt u de proxygebruiker toe aan de `contributors` groep.
   * Typen in de term `contributors` Hiermee wordt AEM functie voor automatisch aanvullen geactiveerd, zodat de groep gemakkelijk kan worden geselecteerd.

   ![Toevoegen aan groep](assets/add-to-group.png)

1. Selecteren **Opslaan en sluiten**.

U hebt de configuratie nu voltooid. Inhoudsauteurs kunnen nu beginnen met het maken van inhoud voor het voorbereiden van de site, zodat ze deze in de volgende stap van de reis op de voorgrond kunnen aanpassen.

## Volgende functies {#what-is-next}

Nu u dit gedeelte van de AEM Quick Site Creation-reis hebt voltooid, moet u:

* Begrijp hoe u AEM Sitesjablonen kunt verkrijgen.
* Leer hoe u een site maakt met een sjabloon.
* Zie hoe u de sjabloon van uw nieuwe site kunt downloaden en aan de front-end ontwikkelaar kunt leveren.

Gebaseerd op deze kennis en doorgaan met uw AEM snelle site-creatie door het document opnieuw te bekijken [Opstelling uw pijpleiding,](pipeline-setup.md) waar u een front-end pijpleiding zult creëren om de aanpassing van het thema van uw plaats te beheren.

## Aanvullende bronnen {#additional-resources}

Terwijl u wordt aangeraden naar het volgende gedeelte van de reis Snel site maken te gaan door het document te bekijken [Opstelling uw pijpleiding,](pipeline-setup.md) hieronder volgen enkele aanvullende , optionele bronnen die een dieper beeld geven van bepaalde in dit document genoemde concepten , maar die niet verplicht zijn om op de reis verder te gaan .

* [Standaardsitemplate AEM](https://github.com/adobe/aem-site-template-standard) - Dit is de bewaarplaats GitHub van het AEM Standaardmalplaatje van de Plaats.
* [Pagina&#39;s ordenen](/help/sites-cloud/authoring/sites-console/organizing-pages.md) - In deze handleiding wordt beschreven hoe u de pagina&#39;s van uw AEM site kunt ordenen.
* [Pagina&#39;s maken](/help/sites-cloud/authoring/sites-console/creating-pages.md) - In deze handleiding wordt uitgelegd hoe u nieuwe pagina&#39;s aan uw site kunt toevoegen.
* [Pagina&#39;s beheren](/help/sites-cloud/authoring/sites-console/managing-pages.md) - In deze handleiding wordt beschreven hoe u de pagina&#39;s van uw site kunt beheren, zoals verplaatsen, kopiëren en verwijderen.
* [Hoe te met Pakket werken](/help/implementing/developing/tools/package-manager.md) - Pakketten maken het importeren en exporteren van inhoud in de opslagplaats mogelijk. In dit document wordt uitgelegd hoe u met pakketten werkt in AEM 6.5. Dit geldt ook voor AEMaaCS.
* [Documentatie voor sitebeheer](/help/sites-cloud/administering/site-creation/create-site.md) - Ontdek de technische documentatie bij het maken van de site voor meer informatie over de functies van het gereedschap Snel maken.
* [Formulieren maken of toevoegen aan een AEM Sites-pagina](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md) - Leer stapsgewijze technieken en tips en trucs voor het integreren van formulieren in uw website, zodat u uw digitale ervaringen optimaal kunt benutten.
