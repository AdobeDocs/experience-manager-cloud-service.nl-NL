---
title: Persoonlijke mappen om elementen te delen
description: Leer hoe te om een privé omslag in  [!DNL Adobe Experience Manager Assets]  tot stand te brengen en het met andere gebruikers te delen en diverse voorrechten aan hen toe te wijzen.
contentOwner: Vishabh Gupta
role: User
feature: Collaboration
exl-id: d48f6daf-af81-4024-bff2-e8bf6d683b0c
source-git-commit: f7f60036088a2332644ce87f4a1be9bae3af1c5e
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 0%

---

# Persoonlijke map in [!DNL Adobe Experience Manager Assets] {#private-folder}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/private-folder.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

In de gebruikersinterface van [!DNL Adobe Experience Manager Assets] kunt u een persoonlijke map maken die exclusief voor u beschikbaar is. U kunt deze persoonlijke map delen met andere gebruikers en deze gebruikers verschillende rechten geven. Op basis van het machtigingsniveau dat u toewijst, kunnen gebruikers verschillende taken op de map uitvoeren, bijvoorbeeld de elementen in de map weergeven of de elementen bewerken.

>[!NOTE]
>
>De privé omslag heeft minstens één lid met de rol van de Eigenaar.
>
>Als u een persoonlijke map wilt maken, hebt u `Read` - en `Modify` -machtigingen nodig voor de bovenliggende map waarin u een persoonlijke map maakt. Als u geen beheerder bent, worden deze machtigingen standaard niet ingeschakeld op `/content/dam` . In dit geval moet u eerst deze machtigingen voor uw gebruikers-id/groep verkrijgen voordat u probeert persoonlijke mappen te maken.

## Persoonlijke map maken en delen  {#create-share-private-folder}

Een persoonlijke map maken en delen:

1. Klik in de [!DNL Assets] -console op de knop **[!UICONTROL Create]** op de werkbalk en selecteer vervolgens **[!UICONTROL Folder]** in het menu.

   ![ creeer activa omslag ](assets/create-folder.png)

1. Voer in het dialoogvenster **[!UICONTROL Create Folder]** een `Title` en `Name` (optioneel) voor de map in.

   Selecteer het selectievakje **[!UICONTROL Private]** en klik op **[!UICONTROL Create]** .

   ![ chlimage_1-413 ](assets/create-private-folder.png)

   Er wordt een persoonlijke map gemaakt. U kunt nu [ activa ](add-assets.md#upload-assets) aan de omslag toevoegen en de omslag met andere gebruikers of groepen delen. De map is pas zichtbaar voor andere gebruikers als u deze deelt en er rechten aan toewijst.

1. Als u de map wilt delen, selecteert u de map en klikt u op **[!UICONTROL Properties]** op de werkbalk.

1. Selecteer op de pagina **[!UICONTROL Folder Properties]** een gebruiker of groep in de lijst **[!UICONTROL Add User]** , wijs een rol ( `Viewer` , `Editor` of `Owner` ) toe aan uw persoonlijke map en klik op **[!UICONTROL Add]** .

   ![ wijs-gebruiker-groep ](assets/assign-permissions-private-folder.png) toe

   U kunt verschillende rollen, zoals `Editor` , `Owner` of `Viewer` , toewijzen aan de gebruiker met wie u de map deelt. Als u een `Owner` rol aan de gebruiker toewijst, heeft de gebruiker `Editor` voorrechten op de omslag. Bovendien kan de gebruiker de map met anderen delen. Als u een `Editor` rol toewijst, kan de gebruiker de activa in uw privé omslag uitgeven. Als u een viewerrol toewijst, kan de gebruiker alleen de elementen in uw persoonlijke map bekijken.

   >[!NOTE]
   >
   >De persoonlijke omslag heeft minstens één lid met `Owner` rol. Daarom kan de beheerder niet alle leden van de eigenaar uit een privé omslag verwijderen. Nochtans, om de bestaande eigenaars (en beheerder zelf) uit de privé omslag te verwijderen moet de beheerder een andere gebruiker als eigenaar toevoegen.

1. Klik op **[!UICONTROL Save & Close]**. Afhankelijk van de rol die u toewijst, wordt aan de gebruiker een reeks rechten toegewezen aan uw persoonlijke map wanneer de gebruiker zich aanmeldt bij [!DNL Assets] .
1. Klik op **[!UICONTROL Ok]** om het bevestigingsbericht te sluiten.
1. De gebruiker met wie u de map deelt, ontvangt een melding voor delen in de gebruikersinterface.

1. Klik op [!UICONTROL Notifications] om een lijst met meldingen te openen.

   ![ bericht ](assets/notification-icon.png)

1. Klik op de vermelding voor de privémap die door de beheerder wordt gedeeld om de map te openen.

## Verwijderen van persoonlijke map {#delete-private-folder}

U kunt een map verwijderen door de map te selecteren en de optie [!UICONTROL Delete] te selecteren in het bovenste menu of door de Backspace-toets op het toetsenbord te gebruiken.

![ schrappingsoptie in hoogste menu ](assets/delete-option.png)

>[!CAUTION]
>
>Als u een privémap uit CRXDE Lite verwijdert, blijven er overbodige gebruikersgroepen over in de opslagplaats.

>[!NOTE]
>
>Als u een map verwijdert met de bovenstaande methode uit de gebruikersinterface, worden ook de bijbehorende gebruikersgroepen verwijderd.
>
>De bestaande overbodige, ongebruikte en automatisch gegenereerde gebruikersgroepen kunnen echter met de `clean` -methode in JMX in de auteurinstantie (`http://[server]:[port]/system/console/jmx/com.day.cq.dam.core.impl.team%3Atype%3DClean+redundant+groups+for+Assets` ) uit de opslagplaats worden verwijderd.

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Publish Assets naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
