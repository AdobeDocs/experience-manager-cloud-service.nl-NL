---
title: Digital Rights Management in Adobe Experience Manager-middelen
description: Leer hoe u de status van verlopen van middelen en informatie over gelicentieerde middelen in AEM beheert.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Digital Rights Management in Experience Manager Assets {#digital-rights-management-in-assets}

Digitale middelen zijn vaak gekoppeld aan een licentie, waarin de gebruiksvoorwaarden en -duur zijn vastgelegd. Omdat Adobe Experience Manager (AEM)-middelen volledig geïntegreerd zijn met het AEM-platform, kunt u op efficiënte wijze informatie over de vervaldatum van bedrijfsmiddelen en de status van bedrijfsmiddelen beheren. U kunt ook licentiegegevens aan elementen koppelen.

## Vervaldatum van element {#asset-expiration}

Vervaldatum van activa is een effectieve manier om vergunningsvereisten voor activa af te dwingen. Het zorgt ervoor dat het gepubliceerde element niet gepubliceerd wordt wanneer het vervalt, wat de mogelijkheid van schending van de licentie afsluit. Een gebruiker zonder beheerdersrechten kan een verlopen middel niet bewerken, kopiëren, verplaatsen, publiceren en downloaden.

U kunt de vervalstatus van een element op de volgende plaatsen bekijken:

* **Kaartweergave**: Voor een verlopen element geeft een markering op de kaart aan dat deze is verlopen.
* **Lijstweergave**: Voor verlopen elementen wordt in de kolom **[!UICONTROL Status]** de banner **[!UICONTROL Verlopen]** weergegeven.
* **Tijdlijn**: U kunt de vervalstatus van een element in de tijdlijn bekijken. Selecteer het element en kies Tijdlijn.
* **Referentiespoor**: U kunt ook de vervalstatus van elementen bekijken in de **[!UICONTROL References]** -rail. Het beheert activa vervalstatussen en verhoudingen tussen samengestelde activa en referenced subassets, inzamelingen, en projecten.

1. Navigeer naar het element waarvan u de verwijzing naar webpagina&#39;s en samengestelde elementen wilt weergeven.
1. Selecteer het element en klik/tik op het algemene navigatiepictogram.
1. Kies **[!UICONTROL Verwijzingen]** in het menu.
1. Voor verlopen activa, toont de spoorstaaf References het **[!UICONTROL Activum van de vervalstatus bij de bovenkant Verlopen]** . Als het activum is verlopen, geeft de References-rail aan dat het status- **[!UICONTROL element is verlopen subactiva]**.

### Zoeken in verlopen elementen {#search-expired-assets}

In het deelvenster Zoeken kunt u zoeken naar verlopen elementen, waaronder verlopen subelementen.

1. Klik in de middelenconsole op het pictogram Zoeken op de werkbalk om het vak Universeel zoeken weer te geven.

1. Met de curseur in het Universele vakje van het Onderzoek, druk de sleutel van de Terugkeer om de pagina van de Resultaten van het Onderzoek te tonen.

1. Klik op het pictogram GlobalNav om het deelvenster Zoeken weer te geven.

1. Klik op de optie **[!UICONTROL Vervalstatus]** of tik erop om deze uit te vouwen.

1. Selecteer **[!UICONTROL Verlopen]**. De verlopen elementen worden weergegeven in zoekresultaten.

Wanneer u de optie **Verlopen** kiest, worden in de middelenconsole alleen de verlopen elementen en subelementen weergegeven waarnaar wordt verwezen door samengestelde elementen. De samengestelde elementen die verwijzen naar verlopen subelementen worden niet direct weergegeven nadat de subelementen verlopen zijn. In plaats daarvan, worden zij getoond nadat de Middelen van AEM ontdekt dat zij verlopen subassets de volgende tijd van de planner in werking stellen van verwijzingen voorzien.

Als u de vervaldatum van een gepubliceerd element aan een datum vroeger dan de huidige plannercyclus wijzigt, ontdekt het programma nog dit element als verlopen activa in de volgende tijd het loopt en wijst dienovereenkomstig op status.

Bovendien als een glitch of een fout de planner verhindert verlopen activa in de huidige cyclus te ontdekken, onderzoekt de planner deze activa in de volgende cyclus opnieuw en ontdekt hun verlopen status.

Om de middelenconsole in staat te stellen de referentiecomponenten samen met de verlopen submiddelen weer te geven, configureert u een **Adobe CQ DAM-workflow voor meldingen** bij verlopen in AEM Configuration Manager.

1. Open AEM Configuration Manager.
1. Kies Bericht bij verlopen **[!UICONTROL van Adobe CQ DAM]**. Standaard is **[!UICONTROL Tijdgebaseerde planner]** geselecteerd, die een taak plant om op een bepaald tijdstip te controleren of een element verlopen subassets heeft. Nadat de taak is voltooid, worden elementen waarvan de subelementen zijn verlopen en waarnaar wordt verwezen, weergegeven als verlopen in de zoekresultaten.

1. Om de baan periodiek in werking te stellen, ontruim het **[!UICONTROL Op tijd gebaseerde gebied van de Regel]** van de Planner en wijzig de tijd in seconden op het gebied van de **[!UICONTROL Periodieke Planner]** . Bijvoorbeeld de voorbeeldexpressie &#39;0 0 &amp;ast; &amp;ast; ? wordt de taak om 00 uur gestart.
1. Selecteer E-mail **** verzenden om e-mails te ontvangen wanneer een element verloopt.

   >[!NOTE]
   >
   >Alleen de maker van het element (de persoon die een bepaald middel uploadt naar AEM Assets) ontvangt een e-mail wanneer het middel vervalt. Zie hoe u e-mailmeldingen configureert voor meer informatie over het configureren van e-mailmeldingen op algemeen AEM-niveau.

1. In het **[!UICONTROL Voorafgaande bericht in secondengebied]** , specificeer de tijd in seconden voorafgaand aan de tijd een activa verloopt wanneer u een bericht betreffende de vervaldatum wilt ontvangen. Als u een beheerder of de maker van het element bent, ontvangt u een bericht vóór het verlopen van het element om u te laten weten dat het element op het punt staat na de opgegeven tijd te verlopen.

   Nadat het element is verlopen, ontvangt u een ander bericht waarin de vervaldatum wordt bevestigd. Bovendien worden de verlopen activa gedeactiveerd.

1. Click **[!UICONTROL Save]**.

## Elementstatussen {#asset-states}

Op de middelenconsole van Adobe Experience Manager (AEM) Assets kunnen verschillende statussen voor elementen worden weergegeven. Afhankelijk van de huidige status van een bepaald element wordt in de kaartweergave een label weergegeven dat de status beschrijft, bijvoorbeeld Verlopen, Gepubliceerd, Goedgekeurd, Afgewezen enzovoort.

1. Selecteer een element in de gebruikersinterface Elementen.

1. Tik/klik op het pictogram **[!UICONTROL Publiceren]** op de werkbalk. Als u het pictogram **Publiceren** niet kunt zien op de werkbalk, tikt u op **[!UICONTROL Meer]** op de werkbalk en klikt u op het pictogram **[!UICONTROL Publiceren]** .

1. Kies **[!UICONTROL Publiceren]** in het menu en sluit het bevestigingsvenster.
1. Sluit de selectiemodus. De publicatiestatus voor het element wordt onder aan de elementminiatuur weergegeven in de kaartweergave. In de lijstmening, toont de Gepubliceerde kolom de tijd toen de activa werd gepubliceerd.

1. Selecteer een element in de interface Elementen en tik op het pictogram **[!UICONTROL Eigenschappen]** of klik erop om de pagina met de elementdetails weer te geven.

1. Stel op het tabblad Geavanceerd een vervaldatum in voor het element in het veld **[!UICONTROL Verlopen]** onder.

1. Klik op **[!UICONTROL Opslaan]** en vervolgens op **[!UICONTROL Sluiten]** om de Asset-console weer te geven.
1. De publicatiestatus voor het element geeft aan dat de status is verlopen onder aan de elementminiatuur in de kaartweergave. In de lijstweergave wordt de status van het element weergegeven als **[!UICONTROL Verlopen]**.

1. Selecteer in de middelenconsole een map en maak een controletaak in de map.
1. Reviseer, keur/verwerp de activa in de overzichtstaak en klik **[!UICONTROL Voltooien]**.
1. Navigeer naar de map waarvoor u de revisietaak hebt gemaakt. De status voor de middelen die u hebt goedgekeurd/geweigerd, wordt onderaan weergegeven in de kaartweergave. In de lijstweergave worden de goedkeuringsstatus en de vervalstatus weergegeven in de desbetreffende kolommen.

1. Als u naar elementen wilt zoeken op basis van hun status, klikt of tikt u op het pictogram **[!UICONTROL Zoeken]** om de zoekbalk weer te geven.

1. Druk op Return en klik op het pictogram **[!UICONTROL GlobalNav]** om het deelvenster Zoeken weer te geven.
1. Tik in het deelvenster Zoeken op **[!UICONTROL Publicatiestatus]** of klik op Publiceren en selecteer **[!UICONTROL Gepubliceerd]** om te zoeken naar gepubliceerde elementen in AEM-elementen.

1. Tik/klik op **[!UICONTROL Goedkeuringsstatus]** en klik op de gewenste optie om te zoeken naar goedgekeurde of geweigerde middelen.

1. Als u naar elementen wilt zoeken op basis van hun vervalstatus, selecteert u **[!UICONTROL Vervalstatus]** in het deelvenster Zoeken en kiest u de gewenste optie.

1. U kunt ook naar elementen zoeken op basis van een combinatie van statussen onder verschillende zoekfacetten. U kunt bijvoorbeeld zoeken naar gepubliceerde elementen die zijn goedgekeurd in een overzichtstaak en die nog niet zijn verlopen door de juiste opties te selecteren in de zoekfacetten.

## Digital Rights Management in Experience Manager Assets {#digital-rights-management-in-assets-1}

Met deze functie wordt de acceptatie van de licentieovereenkomst afgedwongen voordat u een licentie kunt downloaden van Adobe Experience Manager (AEM) Assets.

Als u een beveiligd element selecteert en op het pictogram **[!UICONTROL Downloaden]** klikt, wordt u omgeleid naar een licentiepagina waar u de licentieovereenkomst accepteert. Als u de licentieovereenkomst niet accepteert, is de knop **[!UICONTROL Downloaden]** uitgeschakeld.

Als de selectie meerdere beveiligde elementen bevat, selecteert u één element tegelijk, accepteert u de licentieovereenkomst en gaat u verder met het downloaden van het element.

Een actief wordt als beschermd beschouwd indien aan een van deze voorwaarden is voldaan:

* De eigenschap voor metagegevens van elementen `xmpRights:WebStatement` verwijst naar het pad van de CQ-pagina die de licentieovereenkomst voor het element bevat.
* De waarde van de eigenschap voor metagegevens van het element `adobe_dam:restrictions` is een onbewerkte HTML die de licentieovereenkomst opgeeft.

>[!NOTE]
>
>De locatie `/etc/dam/drm/licences` die wordt gebruikt voor het opslaan van licenties in eerdere versies van AEM is afgekeurd.
>
>Als u licentiepagina&#39;s maakt of wijzigt of deze van eerdere AEM-versies poort, raadt Adobe u aan de pagina&#39;s op te slaan op `/apps/settings/dam/drm/licenses` of `/conf/*/settings/dam/drm/licenses`.

### DRM-middelen downloaden {#downloading-drm-assets}

1. Selecteer in de kaartweergave de elementen die u wilt downloaden en klik op het pictogram **[!UICONTROL Downloaden]** .
1. Selecteer op de pagina **[!UICONTROL Copyrightbeheer]** het element dat u wilt downloaden in de lijst.
1. Kies **[!UICONTROL Akkoord]** in het venster Licentie. Naast het element waarvoor u de licentieovereenkomst accepteert, wordt een vinkje weergegeven. Tik/klik op de knop **[!UICONTROL Downloaden]** .

   >[!NOTE]
   >
   >De knop **[!UICONTROL Downloaden]** is alleen ingeschakeld als u akkoord gaat met de licentieovereenkomst voor een beveiligd element. Als uw selectie echter zowel beveiligde als niet-beveiligde elementen bevat, worden alleen de beveiligde elementen weergegeven in het linkervenster en wordt de knop **[!UICONTROL Downloaden]** ingeschakeld om de niet-beveiligde elementen te downloaden. Als u tegelijkertijd licentieovereenkomsten voor meerdere beveiligde elementen wilt accepteren, selecteert u de elementen in de lijst en kiest u **[!UICONTROL Akkoord]**.

1. Tik/klik in het dialoogvenster op **[!UICONTROL Downloaden]** om het element of de uitvoeringen te downloaden.
