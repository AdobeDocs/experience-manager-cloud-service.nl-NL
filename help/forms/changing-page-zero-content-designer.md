---
title: Hoe wijzigt u de pagina Nulinhoud in Designer?
description: Wijzig het bericht dat wordt weergegeven op Pagina Nul van een XFA PDF voor niet-Adobe PDF-viewers.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
feature: Adaptive Forms
role: User
badgeSaas: label="AEM Forms" type="Positive" tooltip="van toepassing op AEM Forms)."
exl-id: 726ba8a8-bfa4-44ac-8e74-e86a32505f36
source-git-commit: 89b0f2a8ca9d2f60365a5c3962b0b4e826f79b3e
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Pagina-nulinhoud wijzigen in Designer {#changing-page-zero-content-in-designer}

Pagina-inhoud nul wordt standaard weergegeven wanneer een niet-Adobe PDF-viewer, zoals de standaard PDF-viewer in [!DNL Chrome] of [!DNL Firefox] , de inhoud van het PDF/XFA-formulier niet kan lezen. Het standaardbericht Pagina Nul wordt hieronder weergegeven.

![&#x200B; defaultPage0message &#x200B;](assets/defaultpage0message.png)

Met de [!DNL AEM Forms] -versie van Designer kunt u het bericht wijzigen dat wordt weergegeven op Pagina Nul. Voer de volgende stappen uit om het bericht Pagina nul te wijzigen:

1. Zorg ervoor dat de [!DNL AEM Forms] -versie van Designer is geïnstalleerd. U kunt de versie controleren van het ongeveer scherm van ontwerper.

1. Open het formulier waarvoor u de inhoud Pagina nul wilt wijzigen.

1. Klik op **[!UICONTROL File]** > **[!UICONTROL Form Properties]** .

1. In de [!UICONTROL Form Properties] dialoog, klik ![&#x200B; plus &#x200B;](assets/plus.png) (plus pictogram) om een douanebezit toe te voegen.

1. Specificeer **_pagezerocontent** als naam van het bezit.
1. Voeg het nieuwe bericht Pagina Nul, in Rich Text-indeling, als waarde toe. Bijvoorbeeld:


   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </code></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </code>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </code></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </code>https://www.adobe.com/go/acrreader.</p></body>`

1. Sla het formulier op als PDF.

1. Bekijk het PDF-formulier in een browser om te bevestigen dat het bericht is bijgewerkt. De bovenstaande voorbeeldwaarde ziet er als volgt uit:

   ![&#x200B; veranderd bericht &#x200B;](assets/changedmessage.png)

>[!NOTE]
>
>De aangepaste eigenschap die u hebt gemaakt, wordt mogelijk niet correct weergegeven in het dialoogvenster Formuliereigenschappen wanneer u het formulier opnieuw opent. Het werkt echter prima en in het formulier wordt het bijgewerkte bericht Pagina nul weergegeven.

>[!MORELIKETHIS]
>
>* [&#x200B; Download en installeer Forms Designer om Document van de malplaatjes van het Verslag te creëren &#x200B;](/help/forms/installing-configuring-designer.md)
>* [&#x200B; Forms Designer van het gebruik om Document van de malplaatjes en vormfragmenten van het Verslag (van Dor) te creëren?](/help/forms/use-forms-designer.md)
