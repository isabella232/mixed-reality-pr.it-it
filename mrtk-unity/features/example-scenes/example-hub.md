---
title: ExampleHub
description: Panoramica su scene di esempio in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 2a2dd09523cc9a0ee16b293050c41d96223082bf
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783566"
---
# <a name="mrtk-examples-hub"></a>MRTK Examples Hub

![MRTK Examples Hub](../images/examples-hub/MRTK_ExamplesHub.png)

L'hub esempi di MRTK è una scena Unity che semplifica l'esperienza di più scene. Usa il sistema di scena di MRTK per caricare & scaricare le scene.

**MRTKExamplesHub. Unity** è la scena del contenitore con componenti condivisi ``MixedRealityToolkit`` , tra cui e ``MixedRealityPlayspace`` . La scena **MRTKExamplesHubMainMenu. Unity** contiene i pulsanti del cubo.

## <a name="prerequisite"></a>Prerequisito

L'hub esempi di MRTK usa il [servizio di transizione della scena](../extensions/scene-transition-service.md) e gli script correlati. Se si usa MRTK tramite i pacchetti Unity, importare **Microsoft. MixedReality. Toolkit. Unity. Extensions. x** . x.x. x. file unitypackage Tools che fa parte dei [pacchetti di versione](https://github.com/microsoft/MixedRealityToolkit-Unity/releases). Se si usa MRTK tramite il clone del repository, è necessario che nel progetto sia già presente la cartella **MRTK/Extensions** .

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a>Scena MRTKExamplesHub e sistema di scena

Aprire **MRTKExamplesHub. Unity** , che si trova in `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` una scena vuota con MixedRealityToolkit, MixedRealityPlayspace e LoadHubOnStartup. Questa scena è configurata per l'uso del sistema di scena di MRTK. Fare clic `MixedRealitySceneSystem` sotto MixedRealityToolkit. Visualizzerà le informazioni del sistema di scena nel pannello Inspector.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

Nella parte inferiore del controllo viene visualizzato l'elenco delle scene definite nel profilo di sistema della scena. È possibile fare clic sui nomi delle scene per caricarli/scaricarli.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3">Esempio di caricamento della scena _MRTKExamplesHub_ facendo clic sul nome della scena nell'elenco.
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4">Esempio di caricamento della scena _HandInteractionExamples_ .
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
Esempio di caricamento di più scene.

## <a name="running-the-scene"></a>Esecuzione della scena

La scena funziona sia nella modalità di gioco di Unity che nel dispositivo. Eseguire la scena **MRTKExamplesHub** nell'editor di Unity e usare la simulazione di input di MRTK per interagire con il contenuto della scena. Per compilare e distribuire, è sufficiente compilare la scena **MRTKExamplesHub** con altre scene incluse nell'elenco del sistema di scena. Il controllo consente inoltre di aggiungere facilmente le scene alle impostazioni di compilazione. Nelle impostazioni di compilazione assicurarsi che la scena **MRTKExamplesHub** si trovi nella parte superiore dell'elenco in corrispondenza dell'indice 0.

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a>Come MRTKExamplesHub carica una scena

Nella scena **MRTKExamplesHub** è possibile trovare il ``ExamplesHubButton`` prefabbricato.
Nel prefabbricato è presente un oggetto **coperchio** che contiene ``Interactable`` .
Utilizzando l'evento interactable ``OnClick()`` ``OnTouch()`` , viene attivata la funzione **LoadContent ()** dello script **LoadContentScene** .
Nel controllo dello script **LoadContentScene** è possibile definire il nome della scena da caricare.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

Lo script usa la funzione LoadContent () del sistema di scena per caricare la scena.
Per altri dettagli, vedere la pagina del [sistema della scena](../scene-system/scene-system-getting-started.md) .

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a>Tornare alla scena del menu principale

Per tornare alla scena del menu principale (scena MRTKExamplesHubMainMenu), è possibile usare lo stesso metodo di sistema della scena `LoadContent()` . Il **ToggleFeaturesPanelExamplesHub. prefabbricate** fornisce il pulsante "Home" che contiene lo script **LoadContentScene** . Usare questa prefabbricata o fornire un pulsante Home personalizzato in ogni scena per consentire all'utente di tornare alla scena principale. È possibile inserire il **ToggleFeaturesPanelExamplesHub. prefabric** nella scena **MRTKExamplesHub** per renderlo sempre visibile perché **MRTKExamplesHub** è una scena di contenitori condivisi. Assicurarsi di nascondere/disattivare **ToggleFeaturesPanel. prefabbricate** in ogni scena di esempio.

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a>Aggiunta di pulsanti aggiuntivi

Nell'oggetto **CubeCollection** duplicare (o aggiungere) i prefabbricati _ExampleHubButton_ e fare clic su **Aggiorna raccolta** in `GridObjectCollection` .
Il layout del cilindro verrà aggiornato in base al nuovo numero totale di pulsanti.
Per ulteriori informazioni, fare riferimento alla pagina [raccolta oggetti](../ux-building-blocks/object-collection.md) .

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

Dopo aver aggiunto i pulsanti, aggiornare il nome della scena nello script **LoadContentScene** (illustrato in precedenza).
Aggiungere altre scene al profilo del sistema della scena.
