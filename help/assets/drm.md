---
title: Digital Rights Management in [!DNL Assets]
description: Leer hoe u de status van verlopen van middelen en informatie over gelicentieerde middelen beheert in [!DNL Experience Manager] als [!DNL Cloud Service].
contentOwner: AG
feature: Asset Management,DRM
role: User,Admin
exl-id: fa5f94df-1c15-4593-afcb-1d24508da2bf
source-git-commit: f7f60036088a2332644ce87f4a1be9bae3af1c5e
workflow-type: tm+mt
source-wordcount: '1313'
ht-degree: 2%

---

# Digital Rights Management voor digitale middelen {#digital-rights-management-in-assets}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/drm.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

Digitale middelen zijn vaak gekoppeld aan een licentie waarin de gebruiksvoorwaarden en -duur zijn vastgelegd. Met de [!DNL Experience Manager] -platform, kunt u informatie over het verlopen van bedrijfsmiddelen en licentiegegevens efficiënt beheren.

## Vervaldatum van element {#asset-expiration}

Gebruik informatie over het verlopen van elementen om licentievereisten voor elementen af te dwingen. De vervalinformatie zorgt ervoor dat het gepubliceerde element niet gepubliceerd is wanneer het vervalt, wat schending van de licentie voorkomt. Een gebruiker zonder beheerdersmachtigingen kan een verlopen middel niet bewerken, kopiëren, verplaatsen, publiceren en downloaden.

U kunt de vervalstatus van een element op de volgende plaatsen bekijken:

* **Kaartweergave**: Voor een verlopen element geeft een markering op de kaart aan dat deze is verlopen.
* **Lijstweergave**: Voor een verlopen element geldt het **[!UICONTROL Status]** de kolom toont **[!UICONTROL Expired]** banner.
* **Tijdlijn**: U kunt de vervalstatus van een element in de tijdlijn bekijken. Selecteer het element en kies Tijdlijn.
* **Referenties spoorstaaf**: U kunt de vervalstatus van elementen ook weergeven in het dialoogvenster **[!UICONTROL References]** spoorwegen. Het beheert activa vervalstatussen en verhoudingen tussen samengestelde activa en referenced subassets, inzamelingen, en projecten.

Ga als volgt te werk om het verwijzen naar webpagina&#39;s en samengestelde elementen voor een element weer te geven:

1. Ga naar het element, selecteer het element en klik op ![pictogram Verwijzingen naar inhoud links](assets/do-not-localize/content-rail-icon.png). De linkerspoorstaaf opent.
1. Selecteren **[!UICONTROL References]** van de linkerspoorstaaf.
1. Voor verlopen elementen [!UICONTROL References] geeft de vervalstatus weer als **[!UICONTROL Asset is Expired]**. Als het element verlopen is, worden de [!UICONTROL References] spoorstaaf geeft de status **[!UICONTROL Asset has Expired Sub-Assets]**.

### Zoeken in verlopen elementen {#search-expired-assets}

Voer de volgende stappen uit om te zoeken naar een verlopen element, inclusief verlopen subelementen:

1. In de [!DNL Assets] console, klik **[!UICONTROL Search]** in de werkbalk en drukt u op `Enter`.

1. Klik op het pictogram GlobalNav en selecteer het pictogram **[!UICONTROL Expiry Status]** -optie.

1. Selecteer **[!UICONTROL Expired]**. De zoekresultaten geven de verlopen elementen weer.

Wanneer u **[!UICONTROL Expired]** de [!DNL Assets] De console toont slechts de verlopen activa en de subassets die door samengestelde activa van verwijzingen worden voorzien. De samengestelde elementen die verwijzen naar verlopen subelementen worden niet direct weergegeven nadat de subelementen verlopen zijn. In plaats daarvan worden ze weergegeven na [!DNL Experience Manager] ontdekt dat zij verlopen subassets van verwijzingen voorzien de volgende tijd de planner uitvoert.

Het is mogelijk om de vervaldatum van een gepubliceerd actief te wijzigen in een datum vroeger dan de huidige plannercyclus. In het schema wordt echter nog steeds een element gedetecteerd als een verlopen element wanneer het de volgende keer wordt uitgevoerd en [!DNL Experience Manager] geeft de status in zijn verslag weer. De vervaldatum van een element wordt anders weergegeven voor gebruikers in verschillende tijdzones.

Bovendien als een fout de planner verhindert verlopen activa in de huidige cyclus te ontdekken, onderzoekt de planner deze activa in de volgende cyclus opnieuw en ontdekt hun verlopen status.

Om het [!DNL Assets] console om de verwijzende samengestelde activa samen met de verlopen subassets te tonen, vorm **[!UICONTROL Adobe CQ DAM Expiry Notification]** workflow in [!DNL Experience Manager]. De op tijd-gebaseerde planner plant een baan om op een specifiek ogenblik te controleren of een activa verlopen subassets heeft. Nadat de taak is voltooid, worden elementen waarvan de subelementen zijn verlopen en waarnaar wordt verwezen, weergegeven als verlopen in de zoekresultaten.

1. Toegang krijgen tot de [!DNL Cloud Manager] Git-opslagplaats gekoppeld aan uw omgeving.
1. Een bestand met de naam vastleggen `com.day.cq.dam.core.impl.ExpiryNotificationJobImpl.cfg.json` in de repository met de volgende inhoud.

   ```json
   {
      "send_email":"false", "asset_expired_limit":"100", "prior_notification_seconds":"86400", "cq.dam.expiry.notification.url.protocol":"http", "cq.dam.expiry.notification.scheduler.istimebased":"true", "cq.dam.expiry.notification.scheduler.period.rule":"10", "cq.dam.expiry.notification.scheduler.timebased.rule":"0 0 0 * * ?"
   }
   ```

1. Volg de instructies van [hoe te om configuratie OSGi in te doen [!DNL Experience Manager] als [!DNL Cloud Service]](/help/implementing/deploying/configuring-osgi.md).

U kunt de planner vormen gebruikend de volgende eigenschappen:

* A `true` waarde van de eigenschap `cq.dam.expiry.notification.scheduler.istimebased` stelt de planner in werking. * De waarde van de eigenschap `cq.dam.expiry.notification.scheduler.timebased.rule` is de reguliere expressie die de tijd definieert. In het bovenstaande voorbeeld wordt de plannertaak op 00 uur gestart.
* Indien `send_email` is ingesteld op `true`, de maker van het actief (de persoon die een bepaald actief uploadt naar [!DNL Assets]) ontvangt een e-mail wanneer het middel vervalt.
* Het maximumaantal activa verliepen in één herhaling van de planner is de waarde van het bezit `asset_expired_limit`.
* Als u de taak periodiek wilt uitvoeren, stelt u de waarde van de eigenschap in `cq.dam.expiry.notification.scheduler.istimebased` als `false` en stelt de waarde van de eigenschap in `cq.dam.expiry.notification.scheduler.period.rule` in seconden.

<!-- TBD: Web Console not available in CS.

1. Open [!DNL Experience Manager] Configuration Manager.
1. Choose **[!UICONTROL Adobe CQ DAM Expiry Notification]**. By default, **[!UICONTROL Time-based Scheduler]** is selected, which 

1. For example, the example expression '0 0 0 &ast; &ast; ?' triggers the job at 0000 hrs.

1. Select **[!UICONTROL send email]** to receive emails when an asset expires.

1. In the **[!UICONTROL Prior notification in seconds]** field, specify the time in seconds before the asset expiry when you want to receive a notification. If you are an administrator or the asset creator, you receive a message before the expiration of the asset. After the asset expiry, you receive another notification that confirms the expiration. In addition, the expired asset is deactivated.

1. Select **[!UICONTROL Save]**.
-->

## Elementstatussen {#asset-states}

De [!DNL Assets] De console kan diverse staten voor activa tonen. Afhankelijk van de huidige status van een bepaald element wordt in de kaartweergave een label weergegeven dat de status beschrijft, bijvoorbeeld Verlopen, Gepubliceerd, Goedgekeurd, Afgewezen enzovoort.

1. In de [!DNL Assets] -interface selecteert u een element.

1. Selecteren **[!UICONTROL Publish]** op de werkbalk. Als u niet ziet [!UICONTROL Publish] in de werkbalk klikt u op **[!UICONTROL More]** op de werkbalk en zoek **[!UICONTROL Publish]** -optie.

1. Kies **[!UICONTROL Publish]** in het menu en sluit vervolgens het bevestigingsvenster.

1. Sluit de selectiemodus. De publicatiestatus voor het element wordt onder aan de elementminiatuur weergegeven in de kaartweergave. In de lijstmening, toont de Gepubliceerde kolom de tijd toen de activa werd gepubliceerd.

1. Als u de pagina met elementdetails wilt weergeven, gaat u naar [!DNL Assets] interface, selecteer een element en klik op **[!UICONTROL Properties]**.

1. In de [!UICONTROL Advanced] een vervaldatum voor het element in te stellen vanaf de **[!UICONTROL Expires]** veld.

1. Klikken **[!UICONTROL Save]** en klik vervolgens op **[!UICONTROL Close]** om de Asset-console weer te geven.

1. De publicatiestatus voor het element geeft aan dat de status is verlopen onder aan de elementminiatuur in de kaartweergave. In de lijstweergave wordt de status van het element weergegeven als **[!UICONTROL Expired]**.

1. In de [!DNL Assets] Selecteer een map en maak een revisietaak in de map.

1. Reviseer en keur de elementen in de revisietaak goed/verwerp deze en klik op **[!UICONTROL Complete]**.

1. Navigeer naar de map waarvoor u de revisietaak hebt gemaakt. De status voor de middelen die u hebt goedgekeurd/geweigerd, wordt onderaan weergegeven in de kaartweergave. In de lijstweergave worden de goedkeuringsstatus en de vervalstatus weergegeven in de desbetreffende kolommen.

1. Als u wilt zoeken naar elementen op basis van hun status, klikt u op **[!UICONTROL Search]** om de zoekbalk weer te geven.

1. Selecteren `Return` en klik op [!DNL Experience Manager].

1. Klik in het deelvenster Zoeken op **[!UICONTROL Publish Status]** en selecteert u **[!UICONTROL Published]** om te zoeken naar gepubliceerde elementen in [!DNL Assets].

1. Als u naar goedgekeurde of geweigerde elementen wilt zoeken, selecteert u **[!UICONTROL Approval Status]** en selecteert u de gewenste optie.

1. Als u op basis van de vervalstatus naar elementen wilt zoeken, selecteert u **[!UICONTROL Expiry Status]** in het deelvenster Zoeken en selecteer de gewenste optie.

1. U kunt ook naar elementen zoeken op basis van een combinatie van statussen onder verschillende zoekfacetten. U kunt bijvoorbeeld zoeken naar gepubliceerde elementen die zijn goedgekeurd in een controletaak en niet verlopen zijn. Selecteer de gewenste opties in de zoekfacetten om dergelijke elementen te zoeken.

## Digital Rights Management in [!DNL Assets] {#digital-rights-management-in-assets-1}

De DRM-functionaliteit dwingt de acceptatie van de licentieovereenkomst af voordat u een licentie-asset kunt downloaden van [!DNL Assets].

Als u een beveiligd element selecteert en klikt op **[!UICONTROL Download]**, wordt u omgeleid naar een licentiepagina om de licentieovereenkomst te accepteren. Als u de licentieovereenkomst niet accepteert, **[!UICONTROL Download]** is niet beschikbaar.

Als de selectie meerdere beveiligde elementen bevat, selecteert u één element tegelijk, accepteert u de licentieovereenkomst en gaat u verder met het downloaden van het element.

Een actief wordt als beschermd beschouwd indien aan een van deze voorwaarden is voldaan:

* De eigenschap voor metagegevens van het element `xmpRights:WebStatement` verwijst naar het pad van de pagina die de licentieovereenkomst voor het element bevat.
* De waarde van de eigenschap voor metagegevens van het element `adobe_dam:restrictions` is een ruwe HTML die de licentieovereenkomst specificeert.

>[!NOTE]
>
>De locatie `/etc/dam/drm/licences` is gebruikt om licenties op te slaan in de eerdere versies van [!DNL Experience Manager]. De locatie is nu vervangen. Als u licentiepagina&#39;s maakt of wijzigt, of de pagina&#39;s van vorige [!DNL Experience Manager] releases, raadt Adobe u aan dergelijke middelen op te slaan op `/apps/settings/dam/drm/licenses` of `/conf/*/settings/dam/drm/licenses` locaties.

### DRM-beveiligde bestanden downloaden {#downloading-drm-assets}

1. Selecteer in de kaartweergave de elementen die u wilt downloaden en selecteer **[!UICONTROL Download]**.
1. Selecteer op de pagina **[!UICONTROL Copyright Management]** de asset die u uit de lijst wilt downloaden.
1. In de [!UICONTROL License] deelvenster, kiest u **[!UICONTROL Agree]**. Naast het element wordt een vinkje weergegeven. Selecteer de **[!UICONTROL Download]** -optie.

   >[!NOTE]
   >
   >De **[!UICONTROL Download]** is alleen ingeschakeld als u akkoord gaat met de licentieovereenkomst voor een beveiligd element. Als uw selectie echter zowel beveiligde als niet-beveiligde elementen bevat, worden alleen de beveiligde elementen weergegeven in het deelvenster en in het dialoogvenster **[!UICONTROL Download]** is beschikbaar om de niet-beveiligde elementen te downloaden. Als u tegelijkertijd licentieovereenkomsten voor meerdere beveiligde assets wilt accepteren, selecteert u de assets in de lijst en vervolgens kiest u **[!UICONTROL Agree]**.

1. Selecteer **[!UICONTROL Download]** in het dialoogvenster.

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [Elementen HTTP-API](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Middelen publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
