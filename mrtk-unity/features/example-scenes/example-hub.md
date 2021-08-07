---
title: MRTK Examples Hub
description: Panoramica sulle scene di esempio in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 6f86a7b6469a8dc7f6253d81f8cf647fbcfe35830fa8cf044066ba8ae9c5a286
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209299"
---
# <a name="mrtk-examples-hub"></a>MRTK Examples Hub

![MRTK Examples Hub](../images/examples-hub/MRTK_ExamplesHub.png)

MrTK Examples Hub è una scena unity che semplifica l'esperienza di più scene. Usa il sistema scene di MRTK per caricare & scaricare le scene.

**MRTKExamplesHub.unity è** la scena del contenitore con componenti condivisi, tra cui ``MixedRealityToolkit`` e ``MixedRealityPlayspace`` . **La scena MRTKExamplesHubMainMenu.unity** include i pulsanti del cubo.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>Scaricare l'app Microsoft Store in HoloLens 2
Se si dispone di HoloLens 2, è possibile scaricare e installare direttamente l'app nel dispositivo.

<a href='//www.microsoft.com/store/apps/9mv8c39l2sj4?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>

## <a name="prerequisite"></a>Prerequisito

MrTK Examples Hub usa [scene transition service](../extensions/scene-transition-service.md) e script correlati. Se si usa MRTK tramite pacchetti Unity, importare **Microsoft.MixedReality.Toolkit. Unity.Extensions.x.x.x.unitypackage** che fa parte dei pacchetti [di versione](https://github.com/microsoft/MixedRealityToolkit-Unity/releases). Se si usa MRTK tramite il clone del repository, nel progetto dovrebbe essere già presente la **cartella MRTK/Extensions.**

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a>MRTKExamplesScenza diHub e sistema di scena

Aprire **MRTKExamplesHub.unity** che si trova in Si tratta di una scena vuota con `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` MixedRealityToolkit, MixedRealityPlayspace e LoadHubOnStartup. Questa scena è configurata per l'uso del sistema di scena di MRTK. Fare `MixedRealitySceneSystem` clic in MixedRealityToolkit. Verranno visualizzate le informazioni del sistema di scena nel pannello Controllo.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

Nella parte inferiore del controllo viene visualizzato l'elenco delle scene definite nel profilo di sistema della scena. È possibile fare clic sui nomi delle scene per caricarli/scaricarli.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3">Esempio di caricamento _della scena MRTKExamplesHub_ facendo clic sul nome della scena nell'elenco.
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4">Esempio di _caricamento della scena HandInteractionExamples._
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
Esempio di caricamento di più scene.

## <a name="running-the-scene"></a>Esecuzione della scena

La scena funziona sia in modalità di gioco di Unity che nel dispositivo. Eseguire la **scena MRTKExamplesHub** nell'editor di Unity e usare la simulazione di input di MRTK per interagire con il contenuto della scena. Per compilare e distribuire, è sufficiente compilare la scena **MRTKExamplesHub** con altre scene incluse nell'elenco del sistema di scena. Il controllo semplifica anche l'aggiunta di scene al controllo Impostazioni. Nella finestra di Impostazioni assicurarsi che la scena **MRTKExamplesHub** sia all'inizio dell'elenco in corrispondenza dell'indice 0.

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a>Come MRTKExamplesHub carica una scena

Nella scena **MRTKExamplesHub** è possibile trovare il ``ExamplesHubButton`` prefab.
Nel prefab è presente un oggetto **FrontPlate** che contiene ``Interactable`` .
Usando l'evento ``OnClick()`` e dell'oggetto Interactable, attiva la funzione ``OnTouch()`` LoadContent() dello script **LoadContent().** 
Nel controllo dello script **LoadContentScene** è possibile definire il nome della scena da caricare.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

Lo script usa la funzione LoadContent() del sistema di scena per caricare la scena.
Per altri dettagli, vedere la pagina [Sistema](../scene-system/scene-system-getting-started.md) scene.

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a>Tornare alla scena del menu principale

Per tornare alla scena del menu principale (scena MRTKExamplesHubMainMenu), è possibile usare lo stesso metodo Scene `LoadContent()` System. **ToggleFeaturesPanelExamplesHub.prefab** fornisce il pulsante "Home" che contiene lo script **LoadContentScene.** Usare questo prefab o fornire un pulsante Home personalizzato in ogni scena per consentire all'utente di tornare alla scena principale. È possibile inserire **ToggleFeaturesPanelExamplesHub.prefab** nella scena **MRTKExamplesHub** per renderlo sempre visibile perché **MRTKExamplesHub** è una scena contenitore condiviso. Assicurarsi di nascondere/disattivare **ToggleFeaturesPanel.prefab** in ogni scena di esempio.

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a>Aggiunta di altri pulsanti

**Nell'oggetto CubeCollection** duplicare (o aggiungere) prefab _ExampleHubButton_ e fare clic su **Update Collection** in `GridObjectCollection` .
In questo modo il layout del cilindro verrà aggiornato in base al nuovo numero totale di pulsanti.
Per altri dettagli, vedere la pagina [Raccolta](../ux-building-blocks/object-collection.md) di oggetti.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

Dopo aver aggiunto i pulsanti, aggiornare il nome della scena nello script **LoadContentScene** (illustrato in precedenza).
Aggiungere altre scene al profilo del sistema di scena.
