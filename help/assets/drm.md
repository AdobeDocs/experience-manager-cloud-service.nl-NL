---
title: Digital Rights Management in [!DNL Assets]
description: Leer hoe u de verloopstatus van elementen en informatie voor gelicentieerde elementen beheert in [!DNL Experience Manager] as a [!DNL Cloud Service].
contentOwner: AG
feature: Middelenbeheer,DRM
role: User,Admin
exl-id: fa5f94df-1c15-4593-afcb-1d24508da2bf
source-git-commit: f993148a9f678cfdaf0693e4964f02b9163cf2ff
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 2%

---

# Digital Rights Management voor digitale middelen {#digital-rights-management-in-assets}

Digitale middelen zijn vaak gekoppeld aan een licentie waarin de gebruiksvoorwaarden en -duur zijn vastgelegd. Met het [!DNL Experience Manager]-platform kunt u op efficiënte wijze informatie over de vervaldatum van bedrijfsmiddelen en licentiegegevens beheren.

## Vervaldatum van element {#asset-expiration}

Gebruik informatie over het verlopen van elementen om licentievereisten voor elementen af te dwingen. De vervalinformatie zorgt ervoor dat het gepubliceerde element niet gepubliceerd is wanneer het vervalt, wat schending van de licentie voorkomt. Een gebruiker zonder beheerdersmachtigingen kan een verlopen middel niet bewerken, kopiëren, verplaatsen, publiceren en downloaden.

U kunt de vervalstatus van een element op de volgende plaatsen bekijken:

* **Kaartweergave**: Voor een verlopen element geeft een markering op de kaart aan dat deze is verlopen.
* **Lijstweergave**: Voor een verlopen element geeft de  **[!UICONTROL Status]** kolom de  **[!UICONTROL Expired]** banner weer.
* **Tijdlijn**: U kunt de vervalstatus van een element in de tijdlijn bekijken. Selecteer het element en kies Tijdlijn.
* **Referentiespoor**: U kunt de vervalstatus van activa in de  **[!UICONTROL References]** spoorstaaf ook bekijken. Het beheert activa vervalstatussen en verhoudingen tussen samengestelde activa en referenced subassets, inzamelingen, en projecten.

Ga als volgt te werk om het verwijzen naar webpagina&#39;s en samengestelde elementen voor een element weer te geven:

1. Navigeer naar het element, selecteer het element en klik op ![referentiepictogram voor linkse spoorweginhoud](assets/do-not-localize/content-rail-icon.png). De linkerspoorstaaf wordt geopend.
1. Selecteer **[!UICONTROL References]** van de linkerspoorstaaf.
1. Voor verlopen elementen geeft [!UICONTROL References] de vervalstatus weer als **[!UICONTROL Asset is Expired]**. Als het element verlopen subassets heeft, wordt de status **[!UICONTROL Asset has Expired Sub-Assets]** weergegeven in de [!UICONTROL References]-rail.

### Zoeken in verlopen elementen {#search-expired-assets}

Voer de volgende stappen uit om te zoeken naar een verlopen element, inclusief verlopen subelementen:

1. Klik in de [!DNL Assets]-console op **[!UICONTROL Search]** op de werkbalk en druk op `Enter`.

1. Klik op het pictogram GlobalNav en selecteer de optie **[!UICONTROL Expiry Status]**.

1. Selecteer **[!UICONTROL Expired]**. De zoekresultaten geven de verlopen elementen weer.

Als u de optie **[!UICONTROL Expired]** kiest, worden in de [!DNL Assets]-console alleen de verlopen elementen en subelementen weergegeven waarnaar wordt verwezen door samengestelde elementen. De samengestelde elementen die verwijzen naar verlopen subelementen worden niet direct weergegeven nadat de subelementen verlopen zijn. In plaats daarvan, worden zij getoond nadat [!DNL Experience Manager] ontdekt dat zij verlopen subassets van verwijzingen voorzien de volgende tijd de planner uitvoert.

Het is mogelijk om de vervaldatum van een gepubliceerd actief te wijzigen in een datum vroeger dan de huidige plannercyclus. In het schema wordt een element echter wel als een vervallen element gedetecteerd wanneer het de volgende keer wordt uitgevoerd en [!DNL Experience Manager] geeft de status in het rapport weer. De vervaldatum van een element wordt anders weergegeven voor gebruikers in verschillende tijdzones.

Bovendien als een fout de planner verhindert verlopen activa in de huidige cyclus te ontdekken, onderzoekt de planner deze activa in de volgende cyclus opnieuw en ontdekt hun verlopen status.

Om [!DNL Assets] console toe te laten om de verwijzende samengestelde activa samen met de verlopen subassets te tonen, vorm **[!UICONTROL Adobe CQ DAM Expiry Notification]** werkschema in [!DNL Experience Manager]. De op tijd-gebaseerde planner plant een baan om op een specifiek ogenblik te controleren of een activa verlopen subassets heeft. Nadat de taak is voltooid, worden elementen waarvan de subelementen zijn verlopen en waarnaar wordt verwezen, weergegeven als verlopen in de zoekresultaten.

1. Open de aan uw omgeving gekoppelde [!DNL Cloud Manager] Git-opslagplaats.
1. Leg een bestand met de naam `com.day.cq.dam.core.impl.ExpiryNotificationJobImpl.cfg.json` in de opslagplaats vast met de volgende inhoud.

   ```json
   {
      "send_email":"false", "asset_expired_limit":"100", "prior_notification_seconds":"86400", "cq.dam.expiry.notification.url.protocol":"http", "cq.dam.expiry.notification.scheduler.istimebased":"true", "cq.dam.expiry.notification.scheduler.period.rule":"10", "cq.dam.expiry.notification.scheduler.timebased.rule":"0 0 0 * * ?"
   }
   ```

1. Volg de instructies van [hoe te om configuratie OSGi in [!DNL Experience Manager] as a [!DNL Cloud Service]](/help/implementing/deploying/configuring-osgi.md) te doen.

U kunt de planner vormen gebruikend de volgende eigenschappen:

* Een `true` waarde van het bezit `cq.dam.expiry.notification.scheduler.istimebased` initieert de planner. * De waarde van de eigenschap `cq.dam.expiry.notification.scheduler.timebased.rule` is de reguliere expressie waarmee de tijd wordt gedefinieerd. In het bovenstaande voorbeeld wordt de plannertaak op 00 uur gestart.
* Als `send_email` is ingesteld op `true`, ontvangt de maker van het element (de persoon die een bepaald element uploadt naar [!DNL Assets]) een e-mail wanneer het element vervalt.
* Het maximumaantal activa verliepen in één herhaling van de planner is de waarde van het bezit `asset_expired_limit`.
* Als u de taak periodiek wilt uitvoeren, stelt u de waarde van de eigenschap `cq.dam.expiry.notification.scheduler.istimebased` in als `false` en stelt u de waarde van de eigenschap `cq.dam.expiry.notification.scheduler.period.rule` in met tijd in seconden.

<!-- TBD: Web Console not available in CS.

1. Open [!DNL Experience Manager] Configuration Manager.
1. Choose **[!UICONTROL Adobe CQ DAM Expiry Notification]**. By default, **[!UICONTROL Time-based Scheduler]** is selected, which 

1.  For example, the example expression '0 0 0 &ast; &ast; ?' triggers the job at 0000 hrs.

1. Select **[!UICONTROL send email]** to receive emails when an asset expires.

1. In the **[!UICONTROL Prior notification in seconds]** field, specify the time in seconds before the asset expiry when you want to receive a notification. If you are an administrator or the asset creator, you receive a message before the expiration of the asset. After the asset expiry, you receive another notification that confirms the expiration. In addition, the expired asset is deactivated.

1. Select **[!UICONTROL Save]**.
-->

## Elementstatussen {#asset-states}

De [!DNL Assets] console kan diverse staten voor activa tonen. Afhankelijk van de huidige status van een bepaald element wordt in de kaartweergave een label weergegeven dat de status beschrijft, bijvoorbeeld Verlopen, Gepubliceerd, Goedgekeurd, Afgewezen enzovoort.

1. Selecteer een element in de gebruikersinterface [!DNL Assets].

1. Selecteer **[!UICONTROL Publish]** van de toolbar. Als de optie [!UICONTROL Publish] niet wordt weergegeven op de werkbalk, klikt u op **[!UICONTROL More]** op de werkbalk en zoekt u de optie **[!UICONTROL Publish]**.

1. Kies **[!UICONTROL Publish]** in het menu en sluit vervolgens het bevestigingsvenster.

1. Sluit de selectiemodus. De publicatiestatus voor het element wordt onder aan de elementminiatuur weergegeven in de kaartweergave. In de lijstmening, toont de Gepubliceerde kolom de tijd toen de activa werd gepubliceerd.

1. Als u de pagina met elementdetails wilt weergeven, selecteert u een element in de interface [!DNL Assets] en klikt u op **[!UICONTROL Properties]**.

1. Stel op het tabblad [!UICONTROL Advanced] een vervaldatum voor het element in in het veld **[!UICONTROL Expires]**.

1. Klik **[!UICONTROL Save]** en klik dan **[!UICONTROL Close]** om de console van Activa te tonen.

1. De publicatiestatus voor het element geeft aan dat de status is verlopen onder aan de elementminiatuur in de kaartweergave. In de lijstweergave wordt de status van het element weergegeven als **[!UICONTROL Expired]**.

1. Selecteer in de [!DNL Assets]-console een map en maak een revisietaak in de map.

1. Reviseer, keur/verwerp de activa in de overzichtstaak en klik **[!UICONTROL Complete]**.

1. Navigeer naar de map waarvoor u de revisietaak hebt gemaakt. De status voor de middelen die u hebt goedgekeurd/geweigerd, wordt onderaan weergegeven in de kaartweergave. In de lijstweergave worden de goedkeuringsstatus en de vervalstatus weergegeven in de desbetreffende kolommen.

1. Als u wilt zoeken naar elementen op basis van hun status, klikt u op **[!UICONTROL Search]** om de zoekbalk weer te geven.

1. Selecteer `Return` en klik [!DNL Experience Manager].

1. Klik in het zoekvenster op **[!UICONTROL Publish Status]** en selecteer **[!UICONTROL Published]** om te zoeken naar gepubliceerde elementen in [!DNL Assets].

1. Als u wilt zoeken naar goedgekeurde of geweigerde elementen, selecteert u **[!UICONTROL Approval Status]** en selecteert u de gewenste optie.

1. Als u op basis van de vervalstatus naar elementen wilt zoeken, selecteert u **[!UICONTROL Expiry Status]** in het zoekvenster en selecteert u de gewenste optie.

1. U kunt ook naar elementen zoeken op basis van een combinatie van statussen onder verschillende zoekfacetten. U kunt bijvoorbeeld zoeken naar gepubliceerde elementen die zijn goedgekeurd in een controletaak en niet verlopen zijn. Als u dergelijke elementen wilt doorzoeken, selecteert u de gewenste opties in de zoekfacetten.

## Digital Rights Management in [!DNL Assets] {#digital-rights-management-in-assets-1}

De DRM-functionaliteit dwingt de acceptatie van de licentieovereenkomst af voordat u een licentie-element kunt downloaden van [!DNL Assets].

Als u een beveiligd element selecteert en op **[!UICONTROL Download]** klikt, wordt u omgeleid naar een licentiepagina om de licentieovereenkomst te accepteren. Als u de licentieovereenkomst niet accepteert, is de optie **[!UICONTROL Download]** niet beschikbaar.

Als de selectie meerdere beveiligde elementen bevat, selecteert u één element tegelijk, accepteert u de licentieovereenkomst en gaat u verder met het downloaden van het element.

Een actief wordt als beschermd beschouwd indien aan een van deze voorwaarden is voldaan:

* De eigenschap voor metagegevens van het element `xmpRights:WebStatement` verwijst naar het pad van de pagina die de licentieovereenkomst voor het element bevat.
* De waarde van de eigenschap voor metagegevens van het element `adobe_dam:restrictions` is een onbewerkte HTML die de licentieovereenkomst opgeeft.

>[!NOTE]
>
>De locatie `/etc/dam/drm/licences` is gebruikt om licenties op te slaan in de eerdere versies van [!DNL Experience Manager]. De locatie is nu vervangen. Als u licentiepagina&#39;s maakt of wijzigt of de pagina&#39;s van vorige [!DNL Experience Manager]-releases plaatst, raadt Adobe u aan deze elementen op te slaan op `/apps/settings/dam/drm/licenses`- of `/conf/*/settings/dam/drm/licenses`-locaties.

### DRM-beveiligde bestanden downloaden {#downloading-drm-assets}

1. Selecteer in de kaartweergave de elementen die u wilt downloaden en selecteer **[!UICONTROL Download]**.
1. Selecteer op de pagina **[!UICONTROL Copyright Management]** de asset die u uit de lijst wilt downloaden.
1. Kies **[!UICONTROL Agree]** in het deelvenster [!UICONTROL License]. Naast het element wordt een vinkje weergegeven. Selecteer de optie **[!UICONTROL Download]**.

   >[!NOTE]
   >
   >De optie **[!UICONTROL Download]** is alleen ingeschakeld als u akkoord gaat met de licentieovereenkomst voor een beveiligd element. Als uw selectie echter zowel beveiligde als niet-beveiligde elementen bevat, worden alleen de beveiligde elementen weergegeven in het deelvenster en is de optie **[!UICONTROL Download]** beschikbaar om de niet-beveiligde elementen te downloaden. Als u tegelijkertijd licentieovereenkomsten voor meerdere beveiligde assets wilt accepteren, selecteert u de assets in de lijst en vervolgens kiest u **[!UICONTROL Agree]**.

1. Selecteer **[!UICONTROL Download]** in het dialoogvenster om het element of de uitvoeringen te downloaden.
