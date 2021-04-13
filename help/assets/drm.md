---
title: Digital Rights Management in [!DNL Assets]
description: Leer hoe u de verloopstatus van elementen en informatie voor gelicentieerde elementen beheert in [!DNL Experience Manager] as a [!DNL Cloud Service].
contentOwner: AG
feature: Middelenbeheer,DRM
role: Business Practitioner,Administrator
exl-id: fa5f94df-1c15-4593-afcb-1d24508da2bf
translation-type: tm+mt
source-git-commit: d3c19e460f72a980e058ef6117f6352bda4d1e8a
workflow-type: tm+mt
source-wordcount: '1274'
ht-degree: 7%

---

# Digital Rights Management voor elementen {#digital-rights-management-in-assets}

Digitale middelen zijn vaak gekoppeld aan een licentie die de gebruiksvoorwaarden en -duur bepaalt. Omdat [!DNL Adobe Experience Manager Assets] volledig geïntegreerd is met het [!DNL Experience Manager]-platform, kunt u op efficiënte wijze informatie over de vervaldatum van bedrijfsmiddelen en de status van bedrijfsmiddelen beheren. U kunt ook licentiegegevens aan elementen koppelen.

## Vervaldatum van element {#asset-expiration}

Vervaldatum van activa is een effectieve manier om licentievereisten voor activa af te dwingen. Het zorgt ervoor dat het gepubliceerde element niet gepubliceerd wordt wanneer het vervalt, wat de mogelijkheid van schending van de licentie afsluit. Een gebruiker zonder beheerdersmachtigingen kan een verlopen middel niet bewerken, kopiëren, verplaatsen, publiceren en downloaden.

U kunt de vervalstatus van een element op de volgende plaatsen bekijken:

* **Kaartweergave**: Voor een verlopen element geeft een markering op de kaart aan dat deze is verlopen.
* **Lijstweergave**: Voor verlopen elementen wordt in de  **[!UICONTROL Status]** kolom de  **[!UICONTROL Expired]** banner weergegeven.
* **Tijdlijn**: U kunt de vervalstatus van een element in de tijdlijn bekijken. Selecteer het element en kies Tijdlijn.
* **Referentiespoor**: U kunt de vervalstatus van activa in de  **[!UICONTROL References]** spoorstaaf ook bekijken. Het beheert activa vervalstatussen en verhoudingen tussen samengestelde activa en referenced subassets, inzamelingen, en projecten.

1. Navigeer naar het element waarvan u de verwijzing naar webpagina&#39;s en samengestelde elementen wilt weergeven.
1. Selecteer het element en klik op het [!DNL Experience Manager]-logo.
1. Kies **[!UICONTROL References]** in het menu.
1. Voor verlopen activa, toont de spoorstaaf References de vervalstatus **[!UICONTROL Asset is Expired]** bij de bovenkant. Als het element is verlopen, geeft de verwijzingstag de status **[!UICONTROL Asset has Expired Sub-Assets]** weer.

### Zoeken in verlopen elementen {#search-expired-assets}

In het deelvenster Zoeken kunt u zoeken naar verlopen elementen, waaronder verlopen subelementen.

1. Klik in de [!DNL Assets]-console op **[!UICONTROL Search]** in de werkbalk om het zoekvak [!DNL Experience Manager] weer te geven.

1. Met de curseur in het vakje van Onderzoek, selecteer `Enter` sleutel om de pagina van onderzoeksresultaten te tonen.

1. Klik op het pictogram GlobalNav om het deelvenster Zoeken weer te geven.

1. Klik of tik op de optie **[!UICONTROL Expiry Status]** om deze uit te vouwen.

1. Selecteer **[!UICONTROL Expired]**. De verlopen elementen worden weergegeven in zoekresultaten.

Als u de optie **[!UICONTROL Expired]** kiest, worden in de [!DNL Assets]-console alleen de verlopen elementen en subelementen weergegeven waarnaar wordt verwezen door samengestelde elementen. De samengestelde elementen die verwijzen naar verlopen subelementen worden niet direct weergegeven nadat de subelementen verlopen zijn. In plaats daarvan, worden zij getoond nadat [!DNL Experience Manager] ontdekt dat zij verlopen subassets van verwijzingen voorzien de volgende tijd de planner loopt.

Als u de vervaldatum van een gepubliceerd element aan een datum vroeger dan de huidige plannercyclus wijzigt, ontdekt het programma nog dit element als verlopen activa in de volgende tijd het loopt en wijst dienovereenkomstig op status. De vervaldatum van een element wordt anders weergegeven voor gebruikers in verschillende tijdzones.

Bovendien als een glitch of een fout de planner verhindert verlopen activa in de huidige cyclus te ontdekken, onderzoekt de planner deze activa in de volgende cyclus opnieuw en ontdekt hun verlopen status.

Om [!DNL Assets] console toe te laten om de verwijzende samengestelde activa samen met de verlopen subassets te tonen, vorm een **[!UICONTROL Adobe CQ DAM Expiry Notification]** werkschema in [!DNL Experience Manager] de Manager van de Configuratie.

1. Open [!DNL Experience Manager] Configuratiebeheer.
1. Choose **[!UICONTROL Adobe CQ DAM Expiry Notification]**. Standaard is **[!UICONTROL Time based Scheduler]** geselecteerd, die een taak plant om op een bepaald tijdstip te controleren of een element verlopen subassets heeft. Nadat de taak is voltooid, worden elementen waarvan de subelementen zijn verlopen en waarnaar wordt verwezen, weergegeven als verlopen in de zoekresultaten.

1. Als u de taak periodiek wilt uitvoeren, wist u het veld **[!UICONTROL Time Based Scheduler Rule]** en wijzigt u de tijd in seconden in het veld **[!UICONTROL Periodic Scheduler]**. Bijvoorbeeld bij de voorbeeldexpressie &#39;0 0 0 &amp;ast; &amp;ast; ?&#39; wordt de taak om 00 uur gestart.

<!-- 1. Select **[!UICONTROL send email]** to receive emails when an asset expires.

   >[!NOTE]
   >
   >Only the asset creator (the person who uploads a particular asset to AEM Assets) receives an email when the asset expires. See how to configure email notification for additional details around configuring email notifications at the overall AEM level.
-->

1. Geef in het veld **[!UICONTROL Prior notification in seconds]** de tijd op in seconden voordat een element vervalt wanneer u een melding over de vervaldatum wilt ontvangen. Als u een beheerder of de maker van het element bent, ontvangt u een bericht vóór het verlopen van het element om u te laten weten dat het element op het punt staat na de opgegeven tijd te verlopen.

   Nadat het element is verlopen, ontvangt u een ander bericht waarin de vervaldatum wordt bevestigd. Bovendien worden de verlopen activa gedeactiveerd.

1. Klik op **[!UICONTROL Save]**.

## Elementstatussen {#asset-states}

De [!DNL Assets] console kan diverse staten voor activa tonen. Afhankelijk van de huidige status van een bepaald element wordt in de kaartweergave een label weergegeven dat de status beschrijft, bijvoorbeeld Verlopen, Gepubliceerd, Goedgekeurd, Afgewezen enzovoort.

1. Selecteer een element in de gebruikersinterface [!DNL Assets].

1. Klik op **[!UICONTROL Publish]** op de werkbalk. Als u **Publish** op de toolbar niet ziet, klik **[!UICONTROL More]** op de toolbar en bepaal de plaats van **[!UICONTROL Publish]** optie.

1. Kies **[!UICONTROL Publish]** in het menu en sluit vervolgens het bevestigingsvenster.
1. Sluit de selectiemodus. De publicatiestatus voor het element wordt onder aan de elementminiatuur weergegeven in de kaartweergave. In de lijstmening, toont de Gepubliceerde kolom de tijd toen de activa werd gepubliceerd.

1. Als u de pagina met elementdetails wilt weergeven, selecteert u een element in de interface [!DNL Assets] en klikt u op **[!UICONTROL Properties]**.

1. Stel op het tabblad [!UICONTROL Advanced] een vervaldatum voor het element in in het veld **[!UICONTROL Expires]**.

1. Klik **[!UICONTROL Save]** en klik dan **[!UICONTROL Close]** om de console van Activa te tonen.
1. De publicatiestatus voor het element geeft aan dat de status is verlopen onder aan de elementminiatuur in de kaartweergave. In de lijstweergave wordt de status van het element weergegeven als **[!UICONTROL Expired]**.

1. Selecteer in de [!DNL Assets]-console een map en maak een revisietaak in de map.
1. Reviseer, keur/verwerp de activa in de overzichtstaak en klik **[!UICONTROL Complete]**.
1. Navigeer naar de map waarvoor u de revisietaak hebt gemaakt. De status voor de middelen die u hebt goedgekeurd/geweigerd, wordt onderaan weergegeven in de kaartweergave. In de lijstweergave worden de goedkeuringsstatus en de vervalstatus weergegeven in de desbetreffende kolommen.

1. Als u wilt zoeken naar elementen op basis van hun status, klikt u op **[!UICONTROL Search]** om de balk Zoeken weer te geven.

1. Selecteer `Return` en klik [!DNL Experience Manager] om het onderzoekspaneel te tonen.
1. Klik in het zoekvenster op **[!UICONTROL Publish Status]** en selecteer **[!UICONTROL Published]** om te zoeken naar gepubliceerde elementen in [!DNL Assets].

1. Klik **[!UICONTROL Approval Status]** en klik de aangewezen optie om naar goedgekeurde of verworpen activa te zoeken.

1. Als u naar assets wilt zoeken op basis van hun vervalstatus, selecteert u **[!UICONTROL Expiry Status]** in het deelvenster Zoeken en kiest u de juiste optie.

1. U kunt ook naar elementen zoeken op basis van een combinatie van statussen onder verschillende zoekfacetten. U kunt bijvoorbeeld zoeken naar gepubliceerde elementen die zijn goedgekeurd in een overzichtstaak en die nog niet zijn verlopen door de juiste opties te selecteren in de zoekfacetten.

## Digital Rights Management in [!DNL Assets] {#digital-rights-management-in-assets-1}

Deze functie dwingt de acceptatie van de licentieovereenkomst af voordat u een onder licentie gegeven element kunt downloaden van [!DNL Adobe Experience Manager Assets].

Als u een beveiligd element selecteert en op **[!UICONTROL Download]** klikt, wordt u omgeleid naar een licentiepagina om de licentieovereenkomst te accepteren. Als u de licentieovereenkomst niet accepteert, is de optie **[!UICONTROL Download]** niet beschikbaar.

Als de selectie meerdere beveiligde elementen bevat, selecteert u één element tegelijk, accepteert u de licentieovereenkomst en gaat u verder met het downloaden van het element.

Een actief wordt als beschermd beschouwd indien aan een van deze voorwaarden is voldaan:

* De eigenschap voor metagegevens van het element `xmpRights:WebStatement` verwijst naar het pad van de pagina die de licentieovereenkomst voor het element bevat.
* De waarde van de eigenschap voor metagegevens van het element `adobe_dam:restrictions` is een onbewerkte HTML die de licentieovereenkomst opgeeft.

>[!NOTE]
>
>De locatie `/etc/dam/drm/licences` die wordt gebruikt voor het opslaan van licenties in eerdere versies van [!DNL Experience Manager] is afgekeurd.
>
>Als u licentiepagina&#39;s maakt of wijzigt of deze van vorige [!DNL Experience Manager]-releases poort, raadt Adobe u aan deze pagina&#39;s op te slaan onder `/apps/settings/dam/drm/licenses` of `/conf/*/settings/dam/drm/licenses`.

### Met DRM beveiligde middelen downloaden {#downloading-drm-assets}

1. Selecteer in de kaartweergave de elementen die u wilt downloaden en klik op **[!UICONTROL Download]**.
1. Selecteer op de pagina **[!UICONTROL Copyright Management]** de asset die u uit de lijst wilt downloaden.
1. Kies **[!UICONTROL Agree]** in het deelvenster [!UICONTROL License]. Naast het element wordt een vinkje weergegeven. Klik op de optie **[!UICONTROL Download]**.

   >[!NOTE]
   >
   >De optie **[!UICONTROL Download]** is alleen ingeschakeld als u akkoord gaat met de licentieovereenkomst voor een beveiligd element. Als uw selectie echter zowel beveiligde als niet-beveiligde elementen bevat, worden alleen de beveiligde elementen weergegeven in het deelvenster en wordt de optie **[!UICONTROL Download]** ingeschakeld om de niet-beveiligde elementen te downloaden. Als u tegelijkertijd licentieovereenkomsten voor meerdere beveiligde assets wilt accepteren, selecteert u de assets in de lijst en vervolgens kiest u **[!UICONTROL Agree]**.

1. Klik in het dialoogvenster op **[!UICONTROL Download]** om het element of de uitvoeringen te downloaden.
