---
title: MRTK 101 - Come usare Mixed Reality Toolkit Unity per le interazioni spaziali comuni (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
description: Come usare Mixed Reality Toolkit Unity per le interazioni di base (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality Toolkit, Windows Mixed Reality, progettazione, app di esempio, controlli, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.localizationpriority: high
ms.openlocfilehash: 95d8f8c52b226eda7ea1601feffc1464c2ea91c5
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677531"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a>MRTK 101: Come usare Mixed Reality Toolkit Unity per le interazioni spaziali comuni
![MRTK](images/MRTK101/MRTK101Cover.png)

Informazioni su come usare MRTK per ottenere alcuni dei comuni modelli di interazione più diffusi per la realtà mista.

- Come simulare le interazioni di input nell'editor di Unity?
- Come afferrare e spostare un oggetto?
- Come ridimensionare un oggetto?
- Come spostare o ruotare un oggetto con precisione?
- Come fare in modo che un oggetto risponda agli eventi di input?
- Come aggiungere feedback visivo?
- Come aggiungere feedback audio?
- Come usare i prefab dei pulsanti nello stile di HoloLens 2?
- Come fare in modo che un oggetto ti segua?
- Come fare in modo che un oggetto rimanga rivolto verso di te?

> [!NOTE]
> Questo articolo è stato aggiornato con le modifiche apportate in [MRTK v2.5.1](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1).

Tutto il contenuto di questa pagina può essere testato nell'editor di Unity con la simulazione di input di MRTK. Attenersi alla [Guida all'installazione di MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) per installare la versione più recente di MRTK se non si ha a disposizione.

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a>Come simulare le interazioni di input nell'editor di Unity?
MRTK supporta la simulazione di input nell'editor. È sufficiente eseguire la scena facendo clic sul pulsante di Unity per la riproduzione. Per simulare l'input, usa i tasti seguenti.
Premi W, A, S, D per spostare la fotocamera.
Tieni premuto il pulsante destro del mouse e sposta il puntatore del mouse per guardarti attorno.
Per far comparire le mani simulate, premi la barra spaziatrice (mano destra) o il tasto MAIUSC sinistro (mano sinistra). Per mantenere le mani simulate nella visualizzazione, premi T o Y. Per ruotare le mani simulate, premi Q o E (orizzontale)/R o F (verticale).

- [Altre informazioni sulla simulazione di input nella documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-an-object"></a>Come afferrare e spostare un oggetto?
Per rendere afferrabile un oggetto, assegna questi due script: **ObjectManipulator.cs** e **NearInteractionGrabbable.cs**(per afferrare l'oggetto direttamente con input di tracciamento della mano articolata). ObjectManipulator supporta sia le interazioni da vicino sia quelle da lontano. Puoi afferrare e spostare un oggetto con l'input di tracciamento della mano articolata di HoloLens 2 (da vicino), il raggio della mano (da lontano), il raggio del controller del movimento (da lontano), il cursore dello sguardo e la simulazione del tocco di HoloLens (da lontano).

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a>Come ridimensionare un oggetto?
**ObjectManipulator.cs** supporta il ridimensionamento e la rotazione a due mani. Questa operazione funziona con vari tipi di input, ad esempio l'input della mano articolata di HoloLens 2, l'input dello sguardo e del movimento di HoloLens 1 e l'input del controller del movimento del visore VR immersive di Windows Mixed Reality.

- [Altre informazioni su Object Manipulator nella documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>Come spostare o ruotare un oggetto con precisione?
Assegnare **BoundsControl.cs** a un oggetto in modo da usare il rettangolo di selezione che costituisce l'interfaccia per il ridimensionamento e la rotazione di un oggetto. Per impostazione predefinita, vengono visualizzati i quadratini e le linee blu nello stile di HoloLens 1. Per usare i quadratini animati basati su prossimità nello stile di HoloLens 2, devi assegnare prefab e materiali. 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [Altre informazioni su Bounds Control nella documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a>Come fare in modo che un oggetto risponda agli eventi di input?
Assegnare **PointerHandler.cs** a un oggetto. Nella finestra Inspector (Controllo) sarà possibile usare gli eventi OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged(). Per usare questi eventi in uno script, implementare **IMixedRealityPointerHandler**.

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [Altre informazioni sul sistema di input nella documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>Come aggiungere feedback visivo?
Assegnare **Interactable.cs** a un oggetto. Nella finestra Inspector (Controllo) aggiungere l'oggetto di destinazione e creare un nuovo tema. Utilizzando i profili dei temi di Interact, puoi aggiungere facilmente feedback visivo a tutti gli stati di interazione di input disponibili.

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


Interactable offre diversi tipi di temi, incluso il tema dello shader, che consente di controllare le proprietà dello shader in base allo stato di interazione.

- [Altre informazioni su Interactable nella documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

Un altro componente importante per il feedback visivo è lo **shader Standard di MRTK**. Con questo shader puoi aggiungere facilmente effetti di feedback visivo, ad esempio una luce in movimento e una luce di prossimità. Poiché lo shader MRTK Standard esegue molti meno calcoli rispetto allo shader Unity Standard, puoi creare un'esperienza con ottime prestazioni.

Crea un nuovo materiale e seleziona lo shader "Mixed Reality Toolkit > Standard". Puoi selezionare uno dei materiali esistenti che usano lo shader MRTK Standard.

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [Altre informazioni sullo shader MRTK Standard nella documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>Come aggiungere feedback audio?
Aggiungere **AudioSource** a un oggetto. Successivamente, negli script che espongono eventi di input, ad esempio Interactable.cs o PointerHandler.cs, assegnare l'oggetto con AudioSource all'evento e selezionare **AudioSource.PlayOneShot()** . Puoi usare i clip audio oppure sceglierne uno dalle risorse audio di MRTK.

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a>Come usare i prefab dei pulsanti nello stile di HoloLens 2?
MRTK offre vari tipi di pulsanti nello stile della shell (sistema operativo) di HoloLens 2. Fornisce feedback visivi sofisticati, come luce di prossimità, effetto di compressione e un effetto ondulato sulla superficie del pulsante, che migliorano la fiducia dell'utente.

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

È sufficiente selezionare e trascinare nella scena uno dei **prefab dei pulsanti a pressione nello stile di HoloLens 2**. Il prefab usa lo script Interactable.cs, che è stato introdotto in precedenza. Puoi usare gli eventi esposti, ad esempio OnClick(), in Interactable per attivare le azioni.

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [Altre informazioni sui prefab dei pulsanti nella documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a>Come fare in modo che un oggetto ti segua?
Assegnare lo script **RadialView.cs** o **Follow.cs** a un oggetto. Fa parte della serie di script Solver che consente di ottenere vari tipi di posizionamento degli oggetti nello spazio 3D. Verrà aggiunto automaticamente **SolverHandler.cs**.
Di seguito è riportato un esempio di configurazione di RadialView per ottenere un comportamento di tipo "inseguimento lento graduale" proprio come con il menu di avvio della shell di HoloLens. Puoi specificare la distanza minima/massima e i gradi di visualizzazione minimi/massimi. L'esempio seguente mostra il posizionamento dell'oggetto in un intervallo compreso tra 0,4 e 0,8 m entro 15 gradi. Modifica i valori relativi al tempo di salto per rendere più veloce o più lento l'aggiornamento della posizione.

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [Altre informazioni sui Solver nella documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a>Come fare in modo che un oggetto rimanga rivolto verso di te?
Assegnare lo script **Billboard.cs** a un oggetto. In questo modo sarà sempre rivolto verso di te, indipendentemente dalla posizione. Puoi specificare l'opzione dell'asse pivot.

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


Sei pronto a creare esperienze straordinarie per la realtà mista? Visita le pagine seguenti e scopri di più su MRTK e sulla realtà mista.

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>Designer di esperienza utente @Microsoft</td>
</tr>
</table>

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di checkpoint per lo sviluppo con Unity che abbiamo delineato, si stanno esplorando i blocchi predefiniti fondamentali in MRTK. Da qui è possibile passare al blocco predefinito successivo: 

> [!div class="nextstepaction"]
> [Fotocamera](camera-in-unity.md)

In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Guida all'installazione di MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [Mixed Reality Toolkit-Unity (MRTK) su GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Portale della documentazione di MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Linee guida per la portabilità da HoloToolkit a MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
