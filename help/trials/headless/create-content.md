---
title: Koploze inhoud maken
description: Gebruik het model Inhoudsfragment dat u eerder hebt gemaakt om inhoud te maken die kan worden gebruikt voor het ontwerpen van pagina's of als basis voor inhoud zonder kop.
hidefromtoc: true
index: false
exl-id: d74cf5fb-4c4a-4363-a500-6e2ef6811e60
source-git-commit: 6204830f30c28daba3ff87ba60acd0150847b523
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 0%

---

# Koploze inhoud maken {#create-content}

Door de in-product het leren module te volgen, leer hoe te om te gebruiken [De modellen van het Fragment van de Inhoud u eerder creeerde](content-structure.md) om inhoud te maken die kan worden gebruikt voor het ontwerpen van pagina&#39;s of als basis voor inhoud zonder kop. Dit document dient als aanvulling op de interactieve rondleiding, die dezelfde stappen omvat en waar nodig gekoppeld is aan aanvullende middelen.

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_create_content"
>title="Nieuwe inhoud maken"
>abstract="Voortbouwend op de modellen u in module 1 creeerde, zult u leren hoe te om inhoud tot stand te brengen die voor paginauteurs, of als basis van uw inhoud zonder kop kan worden gebruikt."

## Contentfragmenten {#introduction}

In AEM as a Cloud Service zijn inhoudsfragmenten delen inhoud zonder kop op basis van de structuur die is gedefinieerd door een model van een inhoudsfragment. U kunt uw eigen inhoudsfragment maken door te beginnen in de console van het Fragment van de Inhoud. De console van het Fragment van de Inhoud kan als uw bibliotheek van inhoud zonder kop worden beschouwd. Met de console kunt u nieuwe inhoudsfragmenten maken en bestaande fragmenten beheren. Uw console is leeg, dus laten we een nieuw fragment maken!

![De inhoud van het fragment bewerken](assets/create-content/content-fragment-console.png)

Als u buiten de instructies in de app zelf naar de console voor inhoudsfragmenten wilt navigeren, wordt deze gevonden met het Adobe-pictogram linksboven op de pagina. Dit opent de globale navigatie van AEM. Van hier, kiest u **Navigatie** en vervolgens **Inhoudsfragmenten**.

>[!TIP]
>
>Als u meer over navigatie in AEM wilt weten, zie [Sectie Aanvullende bronnen](#additional-resources) van dit document voor meer informatie over AEM basisverwerking.

## Een inhoudsfragment maken {#create-fragment}

Inhoudsfragmenten vertegenwoordigen inhoud zonder kop. Maar ze kunnen alleen worden gemaakt op basis van een vooraf gedefinieerde inhoudsstructuur. Het model voor inhoudsfragmenten dat u eerder hebt gemaakt, fungeert als die structuur.

1. Tik of klik op de knop **Maken** knop rechtsboven in de console om de **Nieuw inhoudsfragment** om een nieuw inhoudsfragment te maken.

   ![Dialoogvenster Inhoudsfragment maken](assets/create-content/create-content-fragment.png)

1. Als u de richtlijnen voor de app volgt, **Locatie** wordt automatisch ingevuld.

   1. Als u zich niet aan de richtlijnen houdt, gebruikt u de padbrowser om uw projectmap te selecteren.

   1. In de **Nieuw inhoudsfragment** tikken of op de knop **Locatie kiezen** (het pictogram dat eruit ziet als een map) in het dialoogvenster **Locatie** veld.

      ![Locatiedialoogvenster kiezen](assets/create-content/choose-location.png)
   * U kunt ook het pad selecteren in het linkernavigatievenster van de Content Fragment-console voordat u op **Maken**.


1. In de **Inhoudsfragmentmodel** Selecteer het model Inhoudsfragment dat u eerder hebt gemaakt in de vervolgkeuzelijst.

1. Voeg een **Titel** voor het inhoudsfragment.

1. Tik of klik op **Maken en openen**.

## Inhoudsfragmenteditor {#edit-fragment}

Nadat u het nieuwe inhoudsfragment hebt opgeslagen, wordt de editor voor het inhoudsfragment geopend. Hier kunt u de feitelijke inhoud van het fragment opgeven.

1. In de editor worden de velden weergegeven die u in het geselecteerde model hebt gedefinieerd. Hier kunt u ze bewerken om het inhoudsfragment te voltooien. Uw voortgang wordt automatisch opgeslagen.

   ![Inhoudsfragmenteditor](assets/create-content/content-fragment-editor.png)

1. Als het model van het inhoudsfragment veel velden bevat, kunt u snel naar elk veld springen met de opdracht **Variabelen** aan de linkerkant van de editor. Velden met fouten worden hier gemarkeerd.

1. Het inhoudsfragment kan alleen door externe apps worden gebruikt als u het publiceert. Tik of klik op de knop **Publiceren** in de rechterbovenhoek van de editor.

1. Selecteren **Nu** in de vervolgkeuzelijst. U kunt ook plannen dat het later wordt gepubliceerd.

   ![Knop Publiceren](assets/create-content/publish.png)

   >[!TIP]
   >
   >Als u meer wilt weten over het publiceren van inhoud in AEM, raadpleegt u de [Sectie Aanvullende bronnen](#additional-resources) van dit document voor meer informatie over publiceren.

1. AEM voert automatisch een verwijzingscontrole uit om ervoor te zorgen dat alle noodzakelijke middelen voor uw Inhoudsfragment worden gepubliceerd. In dit geval moet u ook het model publiceren dat u hebt gemaakt. Tik of klik op **Publiceren**.

   ![Referentiecontrole](assets/create-content/references.png)

1. De publicatie wordt bevestigd in een banner.

   ![Bevestiging van de bekendmaking](assets/create-content/publish-confirm.png)

## U hebt geleerd hoe u een inhoudsfragment kunt maken! {#conclusion}

In deze module hebt u geleerd hoe u een inhoudsfragment kunt maken op basis van het model dat u eerder hebt gemaakt. Op deze manier maakt een auteur van inhoud gestructureerde inhoud zonder kop.

Nu uw inhoud is gemaakt en gepubliceerd, kunt u deze inhoud nu extraheren via Grafiek QL via AEM API&#39;s. U zult over dit in de module leren [Inhoud extraheren via de GraphQL API.](extract-content.md)

U kunt terugkeren naar het beginscherm van de proefversie door op **Oplossingen** rechtsboven op de navigatiebalk en selecteert u **Experience Manager**.

![Thuis navigeren](assets/create-content/home.png)

## Aanvullende bronnen {#additional-resources}

Voor meer informatie over de Fragmenten en de AEM van de Inhoud, overweeg het herzien van deze extra documentatie.

* [Basisverwerking](/help/sites-cloud/authoring/getting-started/basic-handling.md) - Documentatie over het navigeren en gebruiken van AEM voor nieuwe gebruikers
* [Inhoudsfragmenten beheren - Publiceren en verwijzen](/help/assets/content-fragments/content-fragments-managing.md#publishing-and-referencing-a-fragment) - Details over het publiceren van inhoud in AEM
* [Inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md) - Overzicht van inhoudsfragmenten en koppelingen naar volledige documentatie over inhoudsfragmenten
* [Inhoudsfragmenten beheren](/help/assets/content-fragments/content-fragments-managing.md) - Inhoudsfragmenten maken en beheren
