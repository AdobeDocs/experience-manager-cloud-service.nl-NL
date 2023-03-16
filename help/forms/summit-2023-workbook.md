---
title: Forms inschakelen met behulp van kerncomponenten en zonder hoofd
seo-title: Build Engaging Forms Using Core Components and Headless
description: Forms inschakelen met behulp van kerncomponenten en zonder hoofd
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
hide: true
hidefromtoc: true
source-git-commit: a4d46fd14805bf68a40ffdbee9d2e5fcfdee2f95
workflow-type: tm+mt
source-wordcount: '4625'
ht-degree: 0%

---


# Forms inschakelen met behulp van kerncomponenten en zonder hoofd

## Overzicht van Lab

In dit hands-on laboratorium, leert u:

Hoe u AEM Forms kunt gebruiken om gemakkelijk adaptieve formulieren te maken met de nieuwste kerncomponenten die consistent zijn met AEM Sites, waardoor het mogelijk wordt om gegevens op te halen door de adaptieve formulieren als headless formulieren aan het web, mobiele apparaten en chatten te leveren. U leert ook beste praktijken rond het stileren, aanpassingen, en front-end ontwikkeling.

## Toetsen

* **Bedrijfsflexibiliteit**: Als zakelijke gebruiker kan ik gemakkelijk Form Experience voor meerdere kanalen schrijven.

* **Kracht voor ontwikkelaar vooraf**: Als frontend ontwikkelaar, kan ik de eindgebruikerervaring controleren gebruikend koploze vormen.

* **Snelheid ontwikkelaar**: Als ontwikkelaar kan ik eenvoudig en consistent Sites en Forms-componenten aanpassen.

## Vereisten


+++AEM Forms als Cloud Service sandbox


    &lt;table>
    &lt;thead>
    &lt;tr>&lt;th>name&lt;/th>&lt;th>username&lt;/th>&lt;th>Author instance URL&lt;/th>&lt;th>Publish Instance URL&lt;/th>&lt;/tr>
    &lt;/thead>
    &lt;tbody>
    &lt;tr>&lt;td>L716001&lt;/td>&lt;td>L716+001@summitlab.us&lt;/td>&lt;td>https://author-p105303-e986623.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p105303-e986623.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716002&lt;/td>&lt;td>L716+002@summitlab.us&lt;/td>&lt;td>https://author-p106405-e993047.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106405-e993047.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716003&lt;/td>&lt;td>L716+003@summitlab.us&lt;/td>&lt;td>https://author-p106406-e993049.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106406-e993049.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716004&lt;/td>&lt;td>L716+004@summitlab.us&lt;/td>&lt;td>https://author-p106398-e993114.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106398-e993114.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716005&lt;/td>&lt;td>L716+005@summitlab.us&lt;/td>&lt;td>https://author-p106407-e993048.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106407-e993048.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716006&lt;/td>&lt;td>L716+006@summitlab.us&lt;/td>&lt;td>https://author-p106408-e993155.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106408-e993155.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716007&lt;/td>&lt;td>L716+007@summitlab.us&lt;/td>&lt;td>https://author-p106343-e993067.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106343-e993067.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716008&lt;/td>&lt;td>L716+008@summitlab.us&lt;/td>&lt;td>https://author-p106399-e993108.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106399-e993108.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716009&lt;/td>&lt;td>L716+009@summitlab.us&lt;/td>&lt;td>https://author-p106344-e993064.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106344-e993064.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716010&lt;/td>&lt;td>L716+010@summitlab.us&lt;/td>&lt;td>https://author-p106409-e993051.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106409-e993051.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716011&lt;/td>&lt;td>L716+011@summitlab.us&lt;/td>&lt;td>https://author-p106345-e993060.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106345-e993060.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716012&lt;/td>&lt;td>L716+012@summitlab.us&lt;/td>&lt;td>https://author-p106346-e993061.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106346-e993061.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716013&lt;/td>&lt;td>L716+013@summitlab.us&lt;/td>&lt;td>https://author-p106410-e993153.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106410-e993153.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716014&lt;/td>&lt;td>L716+014@summitlab.us&lt;/td>&lt;td>https://author-p106502-e993073.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106502-e993073.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716015&lt;/td>&lt;td>L716+015@summitlab.us&lt;/td>&lt;td>https://author-p106401-e993112.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106401-e993112.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716016&lt;/td>&lt;td>L716+016@summitlab.us&lt;/td>&lt;td>https://author-p106452-e993115.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106452-e993115.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716017&lt;/td>&lt;td>L716+017@summitlab.us&lt;/td>&lt;td>https://author-p106453-e993113.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106453-e993113.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716018&lt;/td>&lt;td>L716+018@summitlab.us&lt;/td>&lt;td>https://author-p106411-e993050.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106411-e993050.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716019&lt;/td>&lt;td>L716+019@summitlab.us&lt;/td>&lt;td>https://author-p106454-e993116.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106454-e993116.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716020&lt;/td>&lt;td>L716+020@summitlab.us&lt;/td>&lt;td>https://author-p106347-e993063.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106347-e993063.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716021&lt;/td>&lt;td>L716+021@summitlab.us&lt;/td>&lt;td>https://author-p106455-e993109.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106455-e993109.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716022&lt;/td>&lt;td>L716+022@summitlab.us&lt;/td>&lt;td>https://author-p106456-e993110.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106456-e993110.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716023&lt;/td>&lt;td>L716+023@summitlab.us&lt;/td>&lt;td>https://author-p106466-e993291.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106466-e993291.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716024&lt;/td>&lt;td>L716+024@summitlab.us&lt;/td>&lt;td>https://author-p106413-e993156.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106413-e993156.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716025&lt;/td>&lt;td>L716+025@summitlab.us&lt;/td>&lt;td>https://author-p106348-e993066.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106348-e993066.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716026&lt;/td>&lt;td>L716+026@summitlab.us&lt;/td>&lt;td>https://author-p106414-e993154.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106414-e993154.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716027&lt;/td>&lt;td>L716+027@summitlab.us&lt;/td>&lt;td>https://author-p106349-e993065.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106349-e993065.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716028&lt;/td>&lt;td>L716+028@summitlab.us&lt;/td>&lt;td>https://author-p106415-e993152.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106415-e993152.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716029&lt;/td>&lt;td>L716+029@summitlab.us&lt;/td>&lt;td>https://author-p106350-e993068.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106350-e993068.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716030&lt;/td>&lt;td>L716+030@summitlab.us&lt;/td>&lt;td>https://author-p106351-e993062.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106351-e993062.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716031&lt;/td>&lt;td>L716+031@summitlab.us&lt;/td>&lt;td>https://author-p106417-e993158.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106417-e993158.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716032&lt;/td>&lt;td>L716+032@summitlab.us&lt;/td>&lt;td>https://author-p106418-e993159.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106418-e993159.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716033&lt;/td>&lt;td>L716+033@summitlab.us&lt;/td>&lt;td>https://author-p106503-e993080.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106503-e993080.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716034&lt;/td>&lt;td>L716+034@summitlab.us&lt;/td>&lt;td>https://author-p106457-e993125.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106457-e993125.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716035&lt;/td>&lt;td>L716+035@summitlab.us&lt;/td>&lt;td>https://author-p106504-e993081.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106504-e993081.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716036&lt;/td>&lt;td>L716+036@summitlab.us&lt;/td>&lt;td>https://author-p106458-e993120.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106458-e993120.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716037&lt;/td>&lt;td>L716+037@summitlab.us&lt;/td>&lt;td>https://author-p106419-e993160.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106419-e993160.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716038&lt;/td>&lt;td>L716+038@summitlab.us&lt;/td>&lt;td>https://author-p106420-e993162.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106420-e993162.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716039&lt;/td>&lt;td>L716+039@summitlab.us&lt;/td>&lt;td>https://author-p106517-e993235.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106517-e993235.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716040&lt;/td>&lt;td>L716+040@summitlab.us&lt;/td>&lt;td>https://author-p106506-e993079.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106506-e993079.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716041&lt;/td>&lt;td>L716+041@summitlab.us&lt;/td>&lt;td>https://author-p106507-e993074.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106507-e993074.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716042&lt;/td>&lt;td>L716+042@summitlab.us&lt;/td>&lt;td>https://author-p106508-e993075.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106508-e993075.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716043&lt;/td>&lt;td>L716+043@summitlab.us&lt;/td>&lt;td>https://author-p106421-e993163.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106421-e993163.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716044&lt;/td>&lt;td>L716+044@summitlab.us&lt;/td>&lt;td>https://author-p106459-e993121.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106459-e993121.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716045&lt;/td>&lt;td>L716+045@summitlab.us&lt;/td>&lt;td>https://author-p106467-e993292.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106467-e993292.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716046&lt;/td>&lt;td>L716+046@summitlab.us&lt;/td>&lt;td>https://author-p106518-e993234.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106518-e993234.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716047&lt;/td>&lt;td>L716+047@summitlab.us&lt;/td>&lt;td>https://author-p106511-e993076.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106511-e993076.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716048&lt;/td>&lt;td>L716+048@summitlab.us&lt;/td>&lt;td>https://author-p106512-e993077.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106512-e993077.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716049&lt;/td>&lt;td>L716+049@summitlab.us&lt;/td>&lt;td>https://author-p106460-e993124.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106460-e993124.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716050&lt;/td>&lt;td>L716+050@summitlab.us&lt;/td>&lt;td>https://author-p106519-e993237.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106519-e993237.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716051&lt;/td>&lt;td>L716+051@summitlab.us&lt;/td>&lt;td>https://author-p106513-e993084.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106513-e993084.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716052&lt;/td>&lt;td>L716+052@summitlab.us&lt;/td>&lt;td>https://author-p106461-e993122.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106461-e993122.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716053&lt;/td>&lt;td>L716+053@summitlab.us&lt;/td>&lt;td>https://author-p106514-e993082.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106514-e993082.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716054&lt;/td>&lt;td>L716+054@summitlab.us&lt;/td>&lt;td>https://author-p106462-e993123.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106462-e993123.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716055&lt;/td>&lt;td>L716+055@summitlab.us&lt;/td>&lt;td>https://author-p106463-e993127.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106463-e993127.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716056&lt;/td>&lt;td>L716+056@summitlab.us&lt;/td>&lt;td>https://author-p106515-e993083.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106515-e993083.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716057&lt;/td>&lt;td>L716+057@summitlab.us&lt;/td>&lt;td>https://author-p106464-e993126.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106464-e993126.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716058&lt;/td>&lt;td>L716+058@summitlab.us&lt;/td>&lt;td>https://author-p106520-e993236.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106520-e993236.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716059&lt;/td>&lt;td>L716+059@summitlab.us&lt;/td>&lt;td>https://author-p106423-e993161.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106423-e993161.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716060&lt;/td>&lt;td>L716+060@summitlab.us&lt;/td>&lt;td>https://author-p106516-e993078.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106516-e993078.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716061&lt;/td>&lt;td>L716+061@summitlab.us&lt;/td>&lt;td>https://author-p106521-e993240.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106521-e993240.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716062&lt;/td>&lt;td>L716+062@summitlab.us&lt;/td>&lt;td>https://author-p106424-e993308.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106424-e993308.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716063&lt;/td>&lt;td>L716+063@summitlab.us&lt;/td>&lt;td>https://author-p106468-e993295.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106468-e993295.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716064&lt;/td>&lt;td>L716+064@summitlab.us&lt;/td>&lt;td>https://author-p106425-e993309.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106425-e993309.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716065&lt;/td>&lt;td>L716+065@summitlab.us&lt;/td>&lt;td>https://author-p106426-e993314.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106426-e993314.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716066&lt;/td>&lt;td>L716+066@summitlab.us&lt;/td>&lt;td>https://author-p106469-e993293.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106469-e993293.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716067&lt;/td>&lt;td>L716+067@summitlab.us&lt;/td>&lt;td>https://author-p106522-e993238.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106522-e993238.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716068&lt;/td>&lt;td>L716+068@summitlab.us&lt;/td>&lt;td>https://author-p106470-e993299.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106470-e993299.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716069&lt;/td>&lt;td>L716+069@summitlab.us&lt;/td>&lt;td>https://author-p106427-e993311.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106427-e993311.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716070&lt;/td>&lt;td>L716+070@summitlab.us&lt;/td>&lt;td>https://author-p106428-e993310.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106428-e993310.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716071&lt;/td>&lt;td>L716+071@summitlab.us&lt;/td>&lt;td>https://author-p106471-e993298.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106471-e993298.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716072&lt;/td>&lt;td>L716+072@summitlab.us&lt;/td>&lt;td>https://author-p106429-e993315.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106429-e993315.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716073&lt;/td>&lt;td>L716+073@summitlab.us&lt;/td>&lt;td>https://author-p106523-e993239.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106523-e993239.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716074&lt;/td>&lt;td>L716+074@summitlab.us&lt;/td>&lt;td>https://author-p106472-e993300.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106472-e993300.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716075&lt;/td>&lt;td>L716+075@summitlab.us&lt;/td>&lt;td>https://author-p106430-e993312.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106430-e993312.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716076&lt;/td>&lt;td>L716+076@summitlab.us&lt;/td>&lt;td>https://author-p106524-e993241.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106524-e993241.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716077&lt;/td>&lt;td>L716+077@summitlab.us&lt;/td>&lt;td>https://author-p106431-e993313.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106431-e993313.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716078&lt;/td>&lt;td>L716+078@summitlab.us&lt;/td>&lt;td>https://author-p106473-e993294.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106473-e993294.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716079&lt;/td>&lt;td>L716+079@summitlab.us&lt;/td>&lt;td>https://author-p106474-e993297.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106474-e993297.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716080&lt;/td>&lt;td>L716+080@summitlab.us&lt;/td>&lt;td>https://author-p106475-e993296.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106475-e993296.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716081&lt;/td>&lt;td>L716+081@summitlab.us&lt;/td>&lt;td>https://author-p106476-e993353.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106476-e993353.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716082&lt;/td>&lt;td>L716+082@summitlab.us&lt;/td>&lt;td>https://author-p106525-e993247.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106525-e993247.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716083&lt;/td>&lt;td>L716+083@summitlab.us&lt;/td>&lt;td>https://author-p106526-e993244.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106526-e993244.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716084&lt;/td>&lt;td>L716+084@summitlab.us&lt;/td>&lt;td>https://author-p106527-e993243.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106527-e993243.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716085&lt;/td>&lt;td>L716+085@summitlab.us&lt;/td>&lt;td>https://author-p106477-e993356.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106477-e993356.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716086&lt;/td>&lt;td>L716+086@summitlab.us&lt;/td>&lt;td>https://author-p106478-e993355.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106478-e993355.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716087&lt;/td>&lt;td>L716+087@summitlab.us&lt;/td>&lt;td>https://author-p106528-e993245.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106528-e993245.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716088&lt;/td>&lt;td>L716+088@summitlab.us&lt;/td>&lt;td>https://author-p106432-e993316.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106432-e993316.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716089&lt;/td>&lt;td>L716+089@summitlab.us&lt;/td>&lt;td>https://author-p106529-e993242.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106529-e993242.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716090&lt;/td>&lt;td>L716+090@summitlab.us&lt;/td>&lt;td>https://author-p106436-e993320.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106436-e993320.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716091&lt;/td>&lt;td>L716+091@summitlab.us&lt;/td>&lt;td>https://author-p106480-e993301.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106480-e993301.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716092&lt;/td>&lt;td>L716+092@summitlab.us&lt;/td>&lt;td>https://author-p106530-e993246.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106530-e993246.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716093&lt;/td>&lt;td>L716+093@summitlab.us&lt;/td>&lt;td>https://author-p106481-e993352.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106481-e993352.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716094&lt;/td>&lt;td>L716+094@summitlab.us&lt;/td>&lt;td>https://author-p106482-e993354.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106482-e993354.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716095&lt;/td>&lt;td>L716+095@summitlab.us&lt;/td>&lt;td>https://author-p106531-e993248.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106531-e993248.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716096&lt;/td>&lt;td>L716+096@summitlab.us&lt;/td>&lt;td>https://author-p106483-e993357.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106483-e993357.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716097&lt;/td>&lt;td>L716+097@summitlab.us&lt;/td>&lt;td>https://author-p106433-e993318.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106433-e993318.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716098&lt;/td>&lt;td>L716+098@summitlab.us&lt;/td>&lt;td>https://author-p106532-e993249.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106532-e993249.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716099&lt;/td>&lt;td>L716+099@summitlab.us&lt;/td>&lt;td>https://author-p106434-e993317.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106434-e993317.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716100&lt;/td>&lt;td>L716+100@summitlab.us&lt;/td>&lt;td>https://author-p106435-e993319.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106435-e993319.adobeaemcloud.com&lt;/td>&lt;/tr>
    &lt;/tbody>
    &lt;/table>

+++

## Les 1

### Doelstelling

Verken uzelf met de as a Cloud Service AEM Forms-omgeving.

### Lessencontext

In deze les, vertrouwt u zich met het as a Cloud Service milieu van AEM Forms door het gebruikersinterface te navigeren.

### Uitoefening

1. Open uw browser en ga URL van het auteursmilieu van de Cloud Service in. Bijvoorbeeld:
   [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/start.html](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/start.html)

1. Meld u aan bij de ontwikkelomgeving van de Cloud Service volgens de gedeelde referenties. Bijvoorbeeld: Gebruikersnaam: [L716+001@summitlab.us](mailto:L716%2B001@summitlab.us)
Wachtwoord: 
**Adobe123!**

1. Nadat u bent aangemeld, navigeert u naar de gebruikersinterface van AEM Forms. Klikken **Forms**.

   ![](/help/forms/assets/screenshot2028113829.png)

1. Klikken **Forms &amp; Documenten**. Pop-ups met betrekking tot voorkeuren of gegevens negeren.

   ![](/help/forms/assets/screenshot2028113929.png)

   Alle beschikbare formulieren worden weergegeven.

   ![](/help/forms/assets/screenshot2028114029.png)

## Les 2

### Doelstelling

Ontwerp een adaptief formulier met de nieuwste kerncomponenten, configureer het formulier en verzend het.

### Lessencontext

In deze les zult u als zakelijke gebruiker een adaptief formulier ontwerpen voor meerdere kanalen, zoals web, mobiel en chatten met behulp van adaptieve formulieren die zijn ontworpen met gestandaardiseerde OTB-kerncomponenten voor het vastleggen van gegevens.

### Uitoefening

1. Maak een verzendeindpunt voor het formulier:

   1. Openen <https://requestbin.com/> in een nieuw browsertabblad.
      ![](/help/forms/assets/screenshot2028114329.png)

   1. Klikken **Een openbare map maken** en kopieer de URL van het eindpunt.
      ![](/help/forms/assets/screenshot202023-03-0120at206.10.0020pm.png)

1. Ontwerp een adaptief formulier met de wizard-interface:

   1. Navigeer in het browsertabblad dat wordt gebruikt in Les 1 naar AEM Forms als Cloud Service-webinterface en navigeer naar Forms en Documenten.
      ![](/help/forms/assets/screenshot2028114029.png)

   1. Klikken **Maken** en selecteer Adaptief formulier.
      ![](/help/forms/assets/screenshot2028114629.png)

   1. Selecteer **Leeg met kerncomponenten** sjabloon in het scherm Sjabloonselectie, zoals hieronder wordt weergegeven:
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.1520pm.png)

   1. Klik op de knop **Stijl** en selecteert u de **wknd-thema** thema zoals hieronder getoond:
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.2320pm.png)

   1. Klik op de knop **Indiening** en selecteert u de **Verzenden naar REST-eindpunt** en geeft u de openbare map op in het dialoogvenster
      **URL voor het verzoek van de POST** veld zoals hieronder weergegeven:
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.5320pm.png)

   1. Klikken **Maken**. Geef een naam en titel op voor het formulier. Bijvoorbeeld: **contactus**. Klikken **Maken**.
      ![](/help/forms/assets/screenshot2028123329.png)

   1. De aangepaste formuliereditor wordt geopend. Pop-ups of dialoogvensters voor voorkeuren of informatie negeren. Klik op de componentenbrowser op de linkerrails en voeg de **Voettekst** onder aan het lege formulier.
      ![](/help/forms/assets/screenshot2028121929.png)

   1. De koptekst maakt deel uit van de adaptieve formuliersjabloon. Hierdoor is een eenvoudige manier om een consistente kop-/voettekst te bieden voor alle adaptieve formulieren. U kunt er ook voor kiezen om de tekst bewerkbaar te houden in het formulier, zoals u in de volgende stap ziet voor de component Voettekst.

   1. Voeg een **Titel** in het midden van het formulier.
      ![](/help/forms/assets/screenshot2028122129.png)

   1. Voeg een **Tekstinvoer** na de titelcomponent.
      ![](/help/forms/assets/screenshot2028122329.png)

   1. Voeg een **Nummerinvoer** component.
      ![](/help/forms/assets/screenshot2028122429.png)

   1. Voeg een **Verzendknop** aan het formulier.
      ![](/help/forms/assets/screenshot2028122529.png)

   1. Klik op de knop **Titel** component zodat **pop-upmenu** wordt weergegeven. Klik op de knop **Pictogram Bewerken** in het menu om de label te bewerken.
      ![](/help/forms/assets/screenshot2028122629.png)

   1. Enter `Contact Us` als de titeltekst.
      ![](/help/forms/assets/screenshot2028122829.png)

   1. Klik op de knop **Tekstinvoer** zodat het pop-upmenu wordt weergegeven. Klik op de knop **Pictogram Bewerken** in het menu om de label te bewerken.
      ![](/help/forms/assets/screenshot2028122929.png)

   1. Enter **Volledige naam** als veldlabel.
      ![](/help/forms/assets/screenshot2028123029.png)

   1. Klik op de knop **Nummerinvoer** zodat het pop-upmenu wordt weergegeven. Klik op de knop **Pictogram Bewerken** in het menu om de label te bewerken.
      ![](/help/forms/assets/screenshot2028123129.png)

   1. Voer de **Telefoonnummer** als veldlabel.
      ![](/help/forms/assets/screenshot2028123829.png)


1. Validaties toevoegen aan formulier:

   1. Klik op de knop **Telefoonnummer** zodat het pop-upmenu wordt weergegeven. Klik op de knop **Perictogram** in het menu om het veld te configureren.
      ![](/help/forms/assets/screenshot2028123429.png)

   1. Open de **validatie, tabblad** markeren **Vereist** en klik op **Gereed**. Het succesbericht wordt weergegeven.
      ![](/help/forms/assets/screenshot2028123529.png)

      ![](/help/forms/assets/screenshot2028123629.png)

   1. Klikken **Voorvertoning** om een voorbeeld van het formulier te bekijken vanuit het perspectief van de eindgebruiker.
      ![](/help/forms/assets/screenshot2028125529.png)

   1. Het formulier vullen met dummygegevens
      ![](/help/forms/assets/screenshot2028125629.png)

   1. Het formulier verzenden
      ![](/help/forms/assets/screenshot2028125729.png)

   1. Controleer de verzonden gegevens op het tabblad Aanvraagvak.
      ![](/help/forms/assets/screenshot2028125829.png)

Gebruik nu voor de resterende bewerking een vooraf gemaakt registratieformulier.

1. Open bijvoorbeeld de AEM Forms-beheerinterface. `https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments`en selecteert u het registratieformulier.

   ![](/help/forms/assets/screenshot2028115529.png)

1. Klikken **Publiceren**.

   ![](/help/forms/assets/screenshot2028115629.png)

   Het succesbericht wordt weergegeven.

   ![](/help/forms/assets/screenshot2028115729.png)

   De publicatie-URL van het formulier lijkt op `https://publish-p105303-e986623.adobeaemcloud.com/content/forms/af/registration.html`.

1. Als u het gepubliceerde formulier wilt weergeven, vervangt u de programma-id (pXXXXXX) en de milieu-id (eXXXXXX) in de bovenstaande URL door id&#39;s van uw omgeving.

## Les 3

### Doelstelling

Werk stijlen bij met behulp van best practices voor ontwikkeling vooraf.

### Lessencontext

In deze les leert u als front-end ontwikkelaar hoe u de opmaak van het eerder gemaakte adaptieve formulier eenvoudig kunt bijwerken.

### Uitoefening

Stel de lokale opslagruimte van het thema in:

1. Open de Herinnering of shell van het Bevel met beheerderrechten:

   ![](/help/forms/assets/screenshot2028115829.png)

1. Voor de Herinnering van het Bevel, gebruik het volgende bevel om te navigeren aan **c:\git** map

   ```Shell
   cd c:\git
   ```

1. Gebruik de volgende opdracht om de themafrontend-code te klonen:

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```


1. Gebruik de volgende opdracht in de vermelde volgorde om naar de **aem-forms-theme-canvas** directory en open de Code van Visual Studio.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/forms/assets/screenshot2028126029.png)

1. Selecteren **De auteurs van alle bestanden in de bovenliggende map vertrouwen** en klik op **Ja, ik vertrouw de auteurs**.

   ![](/help/forms/assets/screenshot2028116229.png)

1. Als u het formulier wilt weergeven dat wordt gehost in de publicatieomgeving van uw cloudservice, wijzigt u de naam van de `env_template` bestand.  Als u de naam van het bestand wilt wijzigen, klikt u met de rechtermuisknop op de knop **env_template** en selecteer de **Naam wijzigen** optie.

   ![](/help/forms/assets/screenshot2028116429.png)

   </br>

   ![](/help/forms/assets/screenshot2028116529.png)

1. Stel de volgende waarden in voor de variabelen in het .env-bestand en sla het bestand op:

   * **AEM_URL**: Geef uw publicatieomgeving voor de cloudservice op. Bijvoorbeeld, `https://publish-p105303-e986623.adobeaemcloud.com/`

   * **AEM_ADAPTIVE_FORM**: Geef het pad van het formulier op. Als het formulierpad bijvoorbeeld `/content/forms/af/registration`de waarde van deze variabele `registration`.

   ![](/help/forms/assets/screenshot2028116429.png)


1. Voer in het venster Opdrachtprompt de volgende opdracht uit:

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * Als u een bericht ontvangt waarin u wordt gevraagd om Npm bij te werken via het dialoogvenster `npm notice Run npm nstall -g npm@9.6.0`, negeert u het bericht.
   > * Stel geen andere npm bevelen in werking tenzij geïnstrueerd in het werkboek.


1. Voer nu de volgende opdracht uit om een voorbeeld van het formulier te bekijken.

   ```Shell
   npm run live
   ```

   ![](/help/forms/assets/screenshot2028117229.png)

   Zodra het bovenstaande bevel wordt uitgevoerd, wacht op `webpack compiled` bericht. Het formulier wordt weergegeven op een browsertabblad.

   >[!NOTE]
   >
   >Als u een leeg scherm in browser ervaart nadat u de opdracht `npm run live` gebruiken voor meer dan 3-4 minuten, wijzigen `localhost` in browser URL naar 127.0.0.1 en druk op **Enter**.


   ![](/help/forms/assets/screenshot2028115129.png)


1. In de Code van Visual Studio, open `PROJECT\src\site\_variables.scss` bestand. Let op: `$error` kleur is een kleur van RED.

   ![](/help/forms/assets/screenshot2028120729.png)

1. Verstuur het formulier in de browser om de rode kleur in het dialoogvenster **Voornaam** veld.

   ![](/help/forms/assets/screenshot2028120829.png)

1. Stel de **$error** kleur naar **#5736eb** en sla het bestand op.

   ![](/help/forms/assets/screenshot2028120729.png)

1. Vernieuw de browser en verzend het formulier. De kleur van de foutmelding in het veld Voornaam is dienovereenkomstig gewijzigd.

   ![](/help/forms/assets/screenshot2028121129.png)

1. Druk in de opdrachtprompt op **CTRL+C**, enter **Y** en drukken **Enter** sleutel om het npm proces te beëindigen. Het is belangrijk om de npm server tegen te houden zodat strijdt het niet met de volgende reeks oefeningen.
1. Sluit de Code van Visual Studio en de Snelle vensters van het Bevel.

## Les 4

### Doelstelling

Het formulier weergeven op web/mobiele en andere interfaces als een headless-formulier.

### Lessencontext

In deze les leert u als ontwikkelaar vooraf hoe u het adaptieve formulier dat u eerder hebt gemaakt, kunt weergeven als een vorm zonder kop met behulp van het raamwerk voor het ontwerpen van het spectrum met reacties.

### Uitoefening

De lokale bewaarplaats van de opstelling gebruikend reactie starter project:

1. Open de Herinnering van het Bevel gebruikend beheerderrechten.

   ![](/help/forms/assets/screenshot2028115829.png)

1. Voor de Herinnering van het Bevel, gebruik het volgende bevel om te navigeren aan **c:\git** map

   ```Shell
   cd c:\git
   ```

1. Gebruik de volgende opdracht om het aanpasbare formulier te klonen om te starten:

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028117329.png)

1. Gebruik de volgende opdrachten in de vermelde volgorde om naar de **response-starter-kit-aem-headless-forms** directory en open de Code van Visual Studio.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028117529.png)


   Het venster van de Code van Visual Studio opent.

   ![](/help/forms/assets/screenshot2028117429.png)

U kunt als volgt het formulier weergeven dat wordt gehost op uw cloudservice-publicatieomgeving:

1. Wijzig de naam van het env_template-bestand in .env-bestand. Als u de naam wilt wijzigen, klikt u met de rechtermuisknop op de knop **env_template** en selecteer de **Naam wijzigen** optie.

   ![](/help/forms/assets/screenshot2028117629.png)

   ![](/help/forms/assets/screenshot2028117729.png)

1. Stel de volgende waarden in voor de variabelen in het .env-bestand. Sla het bestand op nadat u de variabelen hebt bijgewerkt.

   * **AEM_URL**: Geef de URL van de publicatieomgeving van de cloudservice op. Bijvoorbeeld, `https://publish-p105303-e986623.adobeaemcloud.com`

   * **AEM_FORM_PATH**: Geef het pad op van het adaptieve formulier dat in de vorige les is gemaakt. Bijvoorbeeld, `/content/forms/af/registration/`

      ![](/help/forms/assets/screenshot202023-03-0820at202.49.1820pm.png)

1. Open het opdrachtvenster, controleer of u zich in de map met formulieren zonder hoofdletter en hoofdletter bevindt voor de reactie en voer de volgende opdracht uit:

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028118029.png)


1. Voer in het venster Opdrachtprompt de volgende opdracht uit:

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028118129.png)

   Met de bovenstaande opdracht start u een lokale ontwikkelingsserver waarmee de formulierdefinitie die is opgehaald van AEM, zonder kop wordt weergegeven met behulp van de frontend bibliotheek met het spectrum voor reacties.

   >[!NOTE]
   >
   > 
   > Als u een leeg scherm in browser ervaart nadat u de opdracht `npm start` gebruiken voor meer dan 3-4 minuten, wijzigen `localhost` in browser URL naar 127.0.0.1 en druk op **Enter**.

   ![](/help/forms/assets/screenshot2028118229.png)

Laten we de uitvoering van regels in deze vorm zonder kop controleren:

1. Selecteer **Schakel het selectievakje in als u 5% korting wilt ontvangen** optie. De volgende optie voor het toepassen van een creditcard is uitgeschakeld.

   ![](/help/forms/assets/screenshot2028126229.png)

1. Uitschakelen **Schakel het selectievakje in als u 5% korting wilt ontvangen** om de optie creditcard in te schakelen.

   ![](/help/forms/assets/screenshot2028126329.png)

We brengen wijzigingen aan in het formulier op de server als een zakelijke gebruiker. Wijzigingen worden dan automatisch doorgevoerd in het formulier zonder kop.

1. Open de AEM Forms-beheerinterface in de browser. Bijvoorbeeld: [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/forms.html/content/dam/formsanddocuments](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments).

1. Selecteer **registratie** formulier en klik op **Bewerken.** Het formulier wordt geopend in de editor voor adaptieve formulieren.

   ![](/help/forms/assets/screenshot2028118529.png)

1. Selecteer **Telefoonnummer** en klik op de knop **Bewerkingspictogram (potloodpictogram)** in de werkbalk. Als u de pop-upwerkbalk niet kunt zien, schakelt u over naar de modus Bewerken door op **Bewerken** knop rechtsboven, links naar **Voorvertoning** knop.

   ![](/help/forms/assets/screenshot2028119629.png)

1. Wijzig het label in Mobiel nummer. Klik op een lege ruimte in het formulier en de wijzigingen die in het formulier zijn aangebracht, worden opgeslagen.

   ![](/help/forms/assets/screenshot2028119729.png)

Laten we het bijgewerkte formulier publiceren om de wijzigingen in de publicatieomgeving door te geven.

1. Selecteer het registratieformulier op het tabblad AEM Forms-beheerinterface en klik op **Publiceren ongedaan maken**. Als u de **Publiceren ongedaan maken** gaat u naar stap 3 om de wijzigingen rechtstreeks te publiceren.

   ![](/help/forms/assets/screenshot2028119829.png)

1. Klikken **Publiceren ongedaan maken**. Klikken **Sluiten** in de respectieve dialoog.

   ![](/help/forms/assets/screenshot2028119929.png)

   ![](/help/forms/assets/screenshot2028120029.png)


1. Nadat de browser is vernieuwd, selecteert u het registratieformulier en klikt u op **Publiceren**.

   ![](/help/forms/assets/screenshot2028120129.png)


1. Klikken **Publiceren**. Klikken **Sluiten** in de respectieve dialoog.

   ![](/help/forms/assets/screenshot2028120329.png)

   ![](/help/forms/assets/screenshot2028120429.png)

1. Vernieuw de browsertab met de koploze vorm. Het label Telefoonnummer is gewijzigd in Mobiel nummer.

   ![](/help/forms/assets/screenshot2028120529.png)

1. Open het venster Opdrachtprompt waarmee het dialoogvenster **response-starter-kit-aem-headless-forms** project, pers **CTRL+C** en vervolgens voert u **Y** en druk op Enter om het npm-proces te beëindigen. Het is belangrijk om de npm server tegen te houden zodat strijdt het niet met de volgende reeks oefeningen.

1. Sluit de Code van Visual Studio en de Snelle vensters van het Bevel.


## Les 5

### Doelstelling

Het formulier weergeven als een formulier zonder kop met de gebruikersinterface voor Google-materiaal

### Lessencontext

In deze les leert u als ontwikkelaar aan de voorzijde hoe u het adaptieve formulier dat u eerder hebt gemaakt, kunt weergeven als een formulier zonder kop met de gebruikersinterface van Google Material.

### Uitoefening

Stel lokale opslagruimte in met een project voor het starten van een materiaalinterface:

1. Open de Herinnering van het Bevel gebruikend beheerderrechten.

   ![](/help/forms/assets/screenshot2028115829.png)


1. Voor de Herinnering van het Bevel, gebruik het volgende bevel om te navigeren aan **c:\git** map:

   ```Shell
   cd c:\git
   ```

1. Voer de volgende opdrachten in de vermelde volgorde uit om een map met de naam mui te maken en naar de map mui te navigeren met de volgende opdrachten:

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. Gebruik de volgende opdracht om het aanpasbare formulier te klonen om te starten:

   ```Shell
   git clone -b mui https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028126529.png)

1. Gebruik de volgende opdracht in de vermelde volgorde om naar de **response-starter-kit-aem-headless-forms** omslag en open de code in de Code van Visual Studio:

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028126829.png)

U kunt als volgt het formulier weergeven dat wordt gehost op uw cloudservice-publicatieomgeving:

1. De naam van de **env_template** bestand naar **.env** bestand. Als u de naam wilt wijzigen, klikt u met de rechtermuisknop op de knop **env_template** bestand en selecteer **Naam wijzigen**.

   ![](/help/forms/assets/screenshot2028126629.png)

1. Stel de volgende waarden in voor de variabelen in het .env-bestand. Sla het bestand op nadat u de variabelen hebt bijgewerkt. Gebruik de **CTRL + S** overschakelen op een andere combinatie om het bestand op te slaan.

   * **AEM_URL**: Geef de URL van de publicatieomgeving van de cloudservice op. Bijvoorbeeld: [https://publish-p105303-e986623.adobeaemcloud.com](https://publish-p105303-e986623.adobeaemcloud.com/)

   * **AEM_FORM_PATH**: Geef het pad op van het adaptieve formulier dat in de vorige les is gemaakt. Bijvoorbeeld: /content/forms/af/registration/

      ![](/help/forms/assets/screenshot2028126929.png)

1. Open het opdrachtvenster en zorg dat u zich bij de **response-starter-kit-aem-headless-forms** en voer de volgende opdracht uit:

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028127029.png)

1. Voer in het venster Opdrachtprompt de volgende opdracht uit:

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028127129.png)

   Met de opdracht wordt een lokale ontwikkelingsserver gestart en wordt de formulierdefinitie zonder kop opgehaald van AEM met behulp van de Google Material UI frontend-bibliotheek.

   >[!NOTE]
   >
   >Als u een leeg scherm in browser ervaart nadat u de opdracht `npm start` gebruiken voor meer dan 3-4 minuten, wijzigen `localhost` in browser URL naar 127.0.0.1 en druk op **Enter**.

   ![](/help/forms/assets/screenshot2028127229.png)

1. U kunt als volgt de uitvoering van dezelfde bedrijfslogica in deze formulieruitvoering evalueren:

   Selecteren **Schakel het selectievakje in als u 5% korting wilt ontvangen**. De volgende optie **Wilt u een aanvraag indienen voor het formulier voor creditcard van bedrijven?** wordt uitgeschakeld.

   ![](/help/forms/assets/screenshot2028127329.png)

## Les 6

### Doelstelling

Een ander uiterlijk van de vorm zonder kop maken met behulp van variaties in de materiaalinterface

### Lessencontext

In deze les leert u als front-end ontwikkelaar hoe u een alternatieve representatie van verschillende componenten kunt maken met behulp van materiaalinterface voor het adaptieve formulier dat eerder door de zakelijke gebruiker is gemaakt.

### Uitoefening

Werk de variatie van componenten in het hoofdloze project bij. De variant van de materiaalinterface-tekstinvoercomponent wijzigen in `OutlinedInput`:

1. In Visuele Code, navigeer aan de component van de tekstinput door te openen `index.tsx` bestand bij `src/components/textinput/index.tsx`.

1. Toevoegen `//` aan het begin van coderegel 103. De regel wordt omgezet in een opmerking.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. Voeg het volgende toe op regel 104 om een andere variant van component te gebruiken en het dossier op te slaan. Gebruik de **CTRL + S** overschakelen op een andere combinatie om het bestand op te slaan.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/forms/assets/screenshot2028127629.png)

   Het is essentieel om correcte kapitalisatie voor &quot;OutlinedInput&quot;variant anders te gebruiken zou compilatie ontbreken. De lokale compilatie van de ontwikkelomgeving begint automatisch in de Herinnering van het Bevel. Wacht tot u het volgende bericht ziet

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. Vernieuw de browser als deze niet automatisch wordt vernieuwd om te zien hoe de component voor tekstinvoer een andere variant gebruikt.

   ![](/help/forms/assets/screenshot2028127729.png)


   Deze wijziging vindt plaats voor eindgebruikers zonder dat de formulierdefinitie wordt gewijzigd op AEM Forms Server en is specifiek voor het kanaal zonder kop in kwestie. Bijvoorbeeld, Webkanaal in dit laboratorium.

   ![](/help/forms/assets/screenshot2028127529.png)


1. Sluit de Code van Visual Studio en de Snelle Vensters van het Bevel.

## Veelgestelde vragen

+++ Is de wizard Adaptief formulier openbaar?

Ja, het is beschikbaar bij AEM Forms als Cloud Service.

+++


+++ Zijn de kerncomponenten openbaar?

Ja, Adaptive Forms core-componenten zijn beschikbaar met AEM Forms als Cloud Service.

+++

+++ Zijn krantenloze formulieren openbaar?

Ja, koploze formulieren zijn beschikbaar met AEM Forms als Cloud Service.

+++

+++ Vereisen de Hoofdloze vormen een afzonderlijke vergunning?

Nee, voor Headless-formulieren wordt dezelfde licentiewaarde gebruikt, uitgedrukt in het aantal verzonden formulieren.

+++

+++ Zijn de componenten van de Kern en Zwaarloze vormen beschikbaar met AEM 6.5 Forms?

Ja, beide adaptieve formulieren bevatten kerncomponenten en headless formulieren die beschikbaar zijn met AEM Forms 6.5 Service Pack 16 en hoger.

+++


## Volgende stappen

Nu u hebt geleerd hoe u adaptieve formulieren kunt maken en deze op meerdere kanalen kunt aanbieden met behulp van headless-formulieren, moet u proberen uw nieuwe vaardigheden in werking te stellen. Maak plezier en ga door met het creëren en leveren van uitzonderlijke ervaringen voor het vastleggen van gegevens aan uw eindgebruikers, waar ze zich bevinden, op schaal!

## Bronnen

* [Inleiding van de kerncomponenten van Adaptive Form](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)

* [Adaptief formulier maken met behulp van kerncomponenten](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html)

* [Update styling voor kern op component-gebaseerde AF](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=en)

* [Hoofdloze adaptieve formulieren](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=en)

* [Startkit voor Headless React gebruiken](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=en)


