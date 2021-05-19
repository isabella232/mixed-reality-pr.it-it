---
title: Hub di esempio
description: Panoramica sulle scene di esempio in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 212fc6e1489a22995241368a9bf4db96d206c44a
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144758"
---
# <a name="mrtk-examples-hub"></a>MRTK Examples Hub

![MRTK Examples Hub](../images/examples-hub/MRTK_ExamplesHub.png)

MrTK Examples Hub è una scena Unity che semplifica l'esperienza di più scene. Usa il sistema scene di MRTK per caricare & scaricare le scene.

**MRTKExamplesHub.unity è** la scena del contenitore con componenti condivisi, tra cui ``MixedRealityToolkit`` e ``MixedRealityPlayspace`` . **La scena MRTKExamplesHubMainMenu.unity** include i pulsanti del cubo.

## <a name="prerequisite"></a>Prerequisito

MrTK Examples Hub usa [scene transition service](../extensions/scene-transition-service.md) e script correlati. Se si usa MRTK tramite pacchetti Unity, importare **Microsoft.MixedReality.Toolkit.Unity.Extensions.x.x.x.unitypackage** che fa parte dei pacchetti [di versione](https://github.com/microsoft/MixedRealityToolkit-Unity/releases). Se si usa MRTK tramite il clone del repository, nel progetto dovrebbe essere già presente la cartella **MRTK/Extensions.**

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a>Scena MRTKExamplesHub e sistema della scena

Aprire **MRTKExamplesHub.unity** che si trova in Si tratta di una scena vuota con `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` MixedRealityToolkit, MixedRealityPlayspace e LoadHubOnStartup. Questa scena è configurata per l'uso del sistema di scena di MRTK. Fare `MixedRealitySceneSystem` clic in MixedRealityToolkit. Verranno visualizzate le informazioni del sistema della scena nel pannello Inspector (Controllo).

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

Nella parte inferiore di Inspector (Controllo) viene visualizzato l'elenco delle scene definite in Scene System Profile (Profilo sistema scena). È possibile fare clic sui nomi delle scene per caricarle/scaricarle.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3">Esempio di caricamento _della scena MRTKExamplesHub_ facendo clic sul nome della scena nell'elenco.
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4">Esempio di caricamento _della scena HandInteractionExamples._
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
Esempio di caricamento di più scene.

## <a name="running-the-scene"></a>Esecuzione della scena

La scena funziona sia in modalità di gioco di Unity che nel dispositivo. Eseguire la **scena MRTKExamplesHub** nell'editor di Unity e usare la simulazione di input di MRTK per interagire con il contenuto della scena. Per compilare e distribuire, è sufficiente compilare la scena **MRTKExamplesHub** con altre scene incluse nell'elenco del sistema di scena. Il controllo semplifica anche l'aggiunta di scene alle impostazioni di compilazione. In Impostazioni compilazione assicurarsi che **la scena MRTKExamplesHub** si trova all'inizio dell'elenco in corrispondenza dell'indice 0.

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
