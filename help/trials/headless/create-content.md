---
title: Koploze inhoud maken
description: Gebruik het model Inhoudsfragment dat u eerder hebt gemaakt om inhoud te maken die kan worden gebruikt voor het ontwerpen van pagina's of als basis voor inhoud zonder kop.
hidefromtoc: true
index: false
exl-id: d74cf5fb-4c4a-4363-a500-6e2ef6811e60
feature: Headless
role: Admin, User, Developer
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 0%

---


# Koploze inhoud maken {#create-content}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_create_content"
>title="Inhoud zonder kop maken"
>abstract="Gebruikend het model dat u in de vorige module creeerde, leert u hoe te om inhoud tot stand te brengen die voor paginauteurs, of als basis van uw inhoud zonder kop kan worden gebruikt."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_create_content_guide"
>title="De console voor inhoudsfragmenten starten"
>abstract="Het maken van consistente inhoud van hoge kwaliteit die naadloos werkt in uw apps en websites, leidt tot een geweldige klantervaring. Deze module begeleidt u door het creëren van uw eerste inhoud zonder kop door de console van het Fragment van de Inhoud te gebruiken.<br><br>Start deze module op een nieuw tabblad door op de onderstaande knop te klikken en volg deze handleiding."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_create_content_guide_footer"
>title="Geweldig werk! In deze module hebt u geleerd hoe u koploze inhoud kunt ontwerpen als een inhoudsfragment op basis van het model dat u eerder hebt gemaakt. U begrijpt nu hoe inhoudsteams inhoud kunnen maken en beheren voor apps en websites, onafhankelijk van ontwikkelingscycli."
>abstract=""

## Een inhoudsfragment maken {#create-fragment}

Inhoudsfragmenten vertegenwoordigen uw inhoud zonder kop en zijn gebaseerd op vooraf gedefinieerde structuren, de zogenaamde Content Fragment-modellen. U hebt al een model gemaakt in een vorige module.

In deze module, creeert u een Fragment van de Inhoud dat op dat model door de console van het Fragment van de Inhoud te gebruiken wordt gebaseerd. U kunt de Content Fragment-console beschouwen als een bibliotheek met inhoud zonder kop. Gebruik dit besturingselement om nieuwe inhoudsfragmenten te maken en bestaande fragmenten te beheren.

De console van het Fragment van de Inhoud wordt gebruikt om inhoud zonder kop over leveringskanalen en onafhankelijk van context tot stand te brengen en uit te geven, die de meest efficiënte methode in vele auteursgevallen kan zijn. In een recentere module zullen wij het uitgeven van inhoud zonder titel in context en op zijn plaats onderzoeken.

1. Selecteer de **Maken** knoop bij top-right van de console.

1. De **Nieuw inhoudsfragment** wordt geopend waar u een inhoudsfragment kunt beginnen te maken. **Locatie** wordt automatisch gevuld met de locatie waar de nieuwe inhoud wordt opgeslagen.

1. In de **Inhoudsfragmentmodel** vervolgkeuzelijst, selecteert u de **Adventure** Model voor inhoudsfragment dat u eerder hebt gemaakt.

1. Toevoegen `Tuscany` als beschrijvend **Titel** voor het inhoudsfragment. Hiermee identificeert u het fragment in de console.

1. Selecteren **Maken en openen**.

![Een nieuw inhoudsfragment maken](assets/do-not-localize/create-content.png)

>[!TIP]
>
>Afhankelijk van de browserinstellingen kan het nieuwe browsertabblad worden onderdrukt door een pop-upblokkering. Als het nieuwe fragment niet wordt geopend nadat u op **Maken en openen**, controleer uw browserinstellingen.

## Inhoud toevoegen aan uw inhoudsfragment {#add-content}

Nadat u het nieuwe inhoudsfragment hebt opgeslagen en geopend, wordt de editor voor het inhoudsfragment op een nieuw tabblad geopend. Hier kunt u de inhoud van het nieuwe fragment toevoegen.

1. In de inhoudsfragmenteditor worden de velden weergegeven die u in het geselecteerde model hebt gedefinieerd. Hier kunt u inhoud toevoegen aan elk veld om het inhoudsfragment te voltooien. Uw voortgang wordt automatisch opgeslagen.

1. Geef een **Titel** voor uw fragment door `Tuscan Adventure`.

1. Geef een **Beschrijving** voor het fragment door in de volgende tekst te plakken.

   ```text
   Visiting Tuscany on a bicycle is about experiencing the old world charm of Italy on your own terms. Your efforts on the climbs of Italy's rolling hills during this tour are rewarded with sunny Mediterranean landscapes and unmatched Italian hospitality. Tuscany's natural wonders have always been a well of inspiration for arts and culture. Find out why as you explore the Italian countryside and coastline on bicycle.
   ```

1. Geef een **Prijs** voor uw fragment door in te voeren `$700`.

1. Een **Afbeelding** dat representatief is voor de reis door te tikken of te klikken **Element toevoegen** in de **Afbeelding** veld.

1. Selecteer in het pop-upvenster Middelen de optie **Zoeken in middelen** om te selecteren uit een bestaand element in de bibliotheek met elementen.

   ![Element toevoegen](assets/do-not-localize/add-asset.png)

1. De **Element selecteren** wordt geopend. Navigeer met de structuurnavigator in het linkerdeelvenster naar **Alle elementen** > **aem-demo-assets** > **en** > **avonturen** > **wielrennen**.

1. De inhoud van de **wielrennen** aan de rechterkant. Selecteer de afbeelding `ADOBESTOCK_141786166.JPEG`.

1. Selecteren **Selecteren**.

   ![Element selecteren](assets/do-not-localize/select-asset.png)

1. De geselecteerde afbeelding wordt weergegeven in het inhoudsfragment. De editor slaat de wijzigingen automatisch op.

1. Als u klaar bent met het toevoegen van inhoud, selecteert u de **Publiceren** in de rechterbovenhoek van de editor. Hierdoor is uw inhoudsfragment beschikbaar voor gebruik door externe apps. Selecteer vervolgens **Nu** in de vervolgkeuzelijst. U kunt ook plannen dat de presentatie op een later tijdstip wordt gepubliceerd.

   ![Inhoud publiceren](assets/do-not-localize/publish.png)

1. De **Inhoudsfragmenten publiceren** wordt weergegeven. AEM voert automatisch een verwijzingscontrole uit om ervoor te zorgen dat alle noodzakelijke middelen voor uw Inhoudsfragment worden gepubliceerd. In dit geval moet u ook het model publiceren dat u hebt gemaakt. Selecteren **Publiceren**.

   ![Publiceren en referentiecontrole](assets/do-not-localize/publish-confirm.png)

1. De publicatie wordt bevestigd in een banner.

Uw inhoud is gepubliceerd en kan als een inhoudsfragment aan uw app of website worden geleverd.
