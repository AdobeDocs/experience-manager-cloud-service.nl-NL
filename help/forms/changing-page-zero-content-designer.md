---
title: Pagina-nulinhoud wijzigen in Designer
seo-title: Changing Page Zero content in Designer
description: Weet u hoe u het bericht kunt wijzigen dat wordt weergegeven op Pagina Nul van een XFA-PDF wanneer u het weergeeft in een niet-Adobe PDF-viewer?
seo-description: Do you know how you can change the message displayed on Page Zero of an XFA PDF when viewing it in a non-Adobe PDF viewer?
uuid: ac23fb21-3f15-48ea-aeeb-4ecc12b771ac
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 56b6a573-8aba-43e7-acb7-c2da45869d95
docset: aem65
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 2%

---


# Pagina-nulinhoud wijzigen in Designer {#changing-page-zero-content-in-designer}

Pagina Nul-inhoud wordt standaard weergegeven wanneer een niet-Adobe PDF-viewer, zoals de standaard PDF-viewer in [!DNL Chrome] of [!DNL Firefox], kan de inhoud van het PDF/XFA-formulier niet lezen. Het standaardbericht Pagina Nul wordt hieronder weergegeven.

![defaultPage0message](assets/defaultpage0message.png)

[!DNL AEM Forms] Met de versie van Designer kunt u het bericht wijzigen dat wordt weergegeven op Pagina Nul. Voer de volgende stappen uit om het bericht Pagina nul te wijzigen:

1. Zorg ervoor dat u beschikt over de [!DNL AEM Forms] versie van Designer geïnstalleerd. U kunt de versie controleren van het ongeveer scherm van ontwerper.

1. Open het formulier waarvoor u de inhoud Pagina nul wilt wijzigen.

1. Klik op **[!UICONTROL File]** > **[!UICONTROL Form Properties]**.

1. In de [!UICONTROL Form Properties] dialoogvenster, klikt u op ![plus](assets/plus.png) (Plus-pictogram) om een aangepaste eigenschap toe te voegen.

1. Opgeven **_pagezerocontent** als de naam van de eigenschap.
1. Voeg het nieuwe bericht Pagina Nul, in Rich Text-indeling, als waarde toe. Bijvoorbeeld:


   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </code></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </code>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </code></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </code>https://www.adobe.com/go/acrreader.</p></body>`

1. Sla het formulier op als PDF.

1. Bekijk het formulier PDF in browser om te bevestigen dat het bericht is bijgewerkt. De bovenstaande voorbeeldwaarde ziet er als volgt uit:

   ![gewijzigd bericht](assets/changedmessage.png)

>[!NOTE]
>
>De aangepaste eigenschap die u zojuist hebt gemaakt, wordt mogelijk niet correct weergegeven in het dialoogvenster Formuliereigenschappen wanneer u het formulier opnieuw opent. Het werkt echter prima en in het formulier wordt het bijgewerkte bericht Pagina nul weergegeven.
