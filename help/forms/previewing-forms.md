---
title: Een voorbeeld bekijken van een adaptief formulier?
description: Gebruikers kunnen een voorbeeld van een formulier bekijken voordat ze het publiceren of activeren, om te controleren of het formulier aan de verwachtingen voldoet. Voorvertoningsopties kunnen per ondersteund formuliertype verschillen.
topic-tags: author
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: 72235277-6c34-4341-9a10-02afa753e7f5
source-git-commit: 05548d56d791584781606b02839c5602b4469f7b
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# Een voorbeeld van een formulier bekijken {#previewing-a-form}

## Overzicht {#overview}

In [!DNL AEM Forms] kunt u een voorbeeld bekijken van de formulieren en documenten in de opslagplaats. Met Voorvertoning kunt u precies zien hoe de formulieren eruitzien en zich gedragen wanneer ze worden vrijgegeven aan de eindgebruikers.

Als u een voorbeeld van formulieren bekijkt, worden deze weergegeven in een interactieve interface en kan de gebruiker de formulieren invullen met gegevens. Als u documenten voorvertoont, worden deze in een niet-interactieve modus weergegeven en kan de gebruiker het document alleen bekijken. Voor formulieren is een extra optie voor Aangepaste voorvertoning beschikbaar. Met deze optie kunt u een voorbeeld van het formulier weergeven met gegevens uit een XML-bestand. De gegevens vullen enkele velden, of alle velden, van het formulier waarvan een voorbeeld wordt weergegeven.

In de volgende tabel worden de voorbeeldopties weergegeven die beschikbaar zijn voor verschillende typen ondersteunde formulieren:

<table>
 <tbody>
  <tr>
   <td><strong> Type van Activa </strong><br /> </td>
   <td><strong> Beschikbare voorproefopties </strong><br /> </td>
  </tr>
  <!--<tr>
   <td>Document</td>
   <td>PDF preview</td>
  </tr>-->
  <tr>
   <td>PDF-formulier</td>
   <td>PDF voorproef en Voorproef met Gegevens <br /> </td>
  </tr>
  <tr>
   <td>Adaptief formulier</td>
   <td>HTML-voorvertoning en HTML-voorvertoning met gegevens</td>
  </tr>
  <!--<tr>
   <td>Form Template</td>
   <td>PDF preview, PDF preview with Data, HTML preview, HTML preview with Data<br /> </td>
  </tr>-->
 </tbody>
</table>

## Een voorbeeld van een formulier bekijken {#previewing-a-form-1}

1. Selecteer activa die u wilt voorproef, en klik Voorproef ![&#x200B; aem6forms_preview &#x200B;](assets/aem6forms_preview.png) in de actietoolbar.

   >[!NOTE]
   >
   >Als u een element wilt selecteren, schakelt u over naar de lijstweergave in de standaardkaartweergave. Klik ![&#x200B; aem6forms_viewlist &#x200B;](assets/aem6forms_viewlist.png) of ![&#x200B; aem6forms_viewcard &#x200B;](assets/aem6forms_viewcard.png) om meningen te schakelen.

1. Klik op Voorvertoning om de mogelijke voorvertoningsopties weer te geven die van toepassing zijn op het geselecteerde elementtype. Klik op de gewenste optie om het geselecteerde element op een nieuw tabblad weer te geven.

   U kunt kiezen uit de volgende opties:

   * Voorvertonen als HTML
   * Voorvertonen met gegevens
     <!--* Preview as PDF (available for form templates)-->

## Voorvertonen met gegevens {#preview-with-data}

Wanneer u **Voorproef met Gegevens** selecteert, kunt u zien hoe de vorm met echte gegevens ingegaan in het kijkt. Met de optie Voorvertonen met gegevens kunt u een XML uploaden die voorbeeldgebruikersgegevens bevat. De voorbeeldgebruikersgegevens worden gebruikt om het voorbeeldformulier in de door u gekozen indeling in te vullen.

1. Selecteer een activa, klik Voorproef ![&#x200B; aem6forms_preview &#x200B;](assets/aem6forms_preview.png), en selecteer **Voorproef met Gegevens**.
1. Geef in het dialoogvenster Formulier voorvertonen de formuliergegevens op als een XML-bestand. Klik op Voorbeeld om het formulier te genereren met de samengevoegde gegevens van XML.
