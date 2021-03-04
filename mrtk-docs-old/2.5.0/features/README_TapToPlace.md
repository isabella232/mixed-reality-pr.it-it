---
title: README_TapToPlace
description: Documentazione di TapToPlace MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, tocco a posto,
ms.openlocfilehash: 6a8ac4a5f65f25ffaea690733847e9e720fef294
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783100"
---
# <a name="tap-to-place"></a>Toccare per posizionare

![TapToPlace](Images/Solver/TapToPlace/TapToPlaceIntroGif.gif)

Toccare per posizionare è un componente di interazione molto usato per posizionare un oggetto gioco sulla superficie. Questo componente è utile per inserire oggetti in una rete spaziale. Toccare per posizionare usa una combinazione di due clic e movimento Head per inserire un oggetto. Un clic per avviare la selezione host, lo spostamento Head per controllare la posizione dell'oggetto e un clic per posizionare l'oggetto nella scena.

## <a name="using-tap-to-place"></a>Uso del tocco per posizionare

1. Configurare la scena
    - Crea una nuova scena Unity
    - Per aggiungere MRTK alla scena, passare al Toolkit di **realtà mista**  >  **Aggiungi alla scena e configurare**
    > [!NOTE]
    > Toccare per posizionare usa i clic basati sul sistema di input MRTK, ma può anche essere controllato senza clic, vedere la sezione tap to Place configurabilità del codice riportata di seguito.
    - Aggiungere un cubo alla scena e impostare la scala su 0,2 e impostare la posizione su (0, 0, 0,7).
1. Associa il [tocco alla posizione](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.TapToPlace) di un oggetto gioco con un Collider

    ![TapToPlaceInspector](Images/Solver/TapToPlace/TapToPlaceInspector2.png)

    - Quando viene aggiunto il componente tap to Place, viene collegato anche un gestore del Risolutore. Toccare per posizionare deriva dalla classe [Solver](README_Solver.md) che richiede un gestore del Risolutore. La posizione di un oggetto Tap per posizionare viene calcolata in relazione all'oggetto `TrackedTargetType` all'interno del gestore del Risolutore. Per impostazione predefinita, l'intestazione è `TrackedTargetType` , ovvero quando viene spostata, l'oggetto segue se è selezionato.  `TrackedTargetType`Può anche essere impostato su un raggio del controller che ha l'oggetto che segue il controller. Il primo gruppo di proprietà nel controllo Tap to Place è costituito dalle [proprietà del Risolutore comune](README_Solver.md#common-solver-properties).  
    > [!IMPORTANT]
    > Il tocco da posizionare è un risolutore autonomo e non può essere concatenato ad altri risolutori. Non può essere concatenato perché SolverHandler. UpdateSolvers viene usato per aggiornare la posizione dell'oggetto durante la sua immissione.
    - Toccare per inserire le proprietà:
        - `Auto Start`: Se true, il tocco per posizionare il Risolutore inizierà a controllare la posizione dell'oggetto gioco da inserire. L'oggetto inizierà immediatamente dopo TrackedTargetType (Head o Ray controller). Questo valore deve essere modificato prima che venga richiamato Start () per avere un effetto.
        - `Default Placement Distance`: Distanza predefinita (in metri) in cui un oggetto verrà inserito rispetto al TrackedTargetType successivo in SolverHandler. Se una superficie non viene raggiunta da Raycast, l'oggetto Game verrà posizionato alla distanza di posizionamento predefinita.
        - `Max Raycast Distance`: Distanza massima (contatori) per il Raycast in base all'origine ' TrackedTargetType '. Questo Raycast cerca una superficie per inserire un oggetto selezionato.
        - `UseDefaultSurfaceNormalOffset`: Questa proprietà è true per impostazione predefinita, assicura che l'oggetto da posizionare sia allineato in una superficie. Se questa proprietà è true, verrà applicato l'offset normale della superficie predefinita al posto di qualsiasi valore specificato per la `SurfaceNormalOffset` Proprietà. Se false, verrà applicato il valore per `SurfaceNormalOffset` . L'offset normale della superficie predefinita è l'extent del Collider lungo l'asse z.
        - `Surface Normal Offset`: Distanza tra il centro dell'oggetto gioco e una superficie lungo la normale della superficie, se il Raycast raggiunge una superficie. Questa proprietà viene applicata a un oggetto solo se `UseDefaultSurfaceNormalOffset` è false.
        - `Keep Orientation Vertical`: Se è true, l'oggetto Game da inserire rimarrà in verticale e in linea con Vector3. up.
        - `Rotate According to Surface`: Se false, l'oggetto Game da inserire non modifica la rotazione in base alla superficie raggiunta.  L'oggetto rimarrà connesso alla videocamera mentre IsBeingPlaced è true.
        - `Magnetic Surfaces`: Matrice di LayerMasks da eseguire dalla priorità più alta alla più bassa. Prima maschera di livello per fornire un hit Raycast verrà usato per i calcoli di posizione.
        - `Debug Enabled`: Se è true e nell'editor di Unity, il valore normale del Raycast hit verrà disegnato in giallo. Il debug abilitato è utile quando `RotateAccordingToSurface` è true perché disegna la normale della superficie raggiunta, che spiega visivamente il motivo per cui l'oggetto viene impostato sull'orientamento corrente.
        - `On Placing Started`: Questo evento viene attivato una volta quando viene selezionato l'oggetto gioco da inserire.
        - `On Placing Stopped`: Questo evento viene generato una volta quando l'oggetto Game da inserire viene deselezionato, inserito.

1. Test del comportamento di tap per posizionare nell'editor
    - Premere Riproduci e tenere premuto la barra spaziatrice per visualizzare una mano di simulazione di input.
    - Spostare la mano fino a quando il cubo non è attivo e simulare un clic con la mano della simulazione di input facendo clic con il pulsante sinistro del mouse.
        - Se i Collider non sono presenti nella scena, l'oggetto seguirà `TrackedTargetType` in corrispondenza dell'oggetto definito `Default Placement Distance` .
    - L'oggetto seguirà lo spostamento della `TrackedTargetType` selezione dopo. Per simulare il movimento Head nell'editor, premere i tasti WASD. Modificare la rotazione della testa facendo clic e tenendo premuto il pulsante destro del mouse.
    - Per arrestare l'inserimento dell'oggetto, fare di nuovo clic su.  Non è necessario che l'oggetto sia attivo per il clic su Arresta selezione host. Lo stato attivo è necessario solo per il clic iniziale che avvia il processo di selezione host.

    `TrackedTargetType`: Head (impostazione predefinita) |  `TrackedTargetType`: Raggio controller
    :-------------------------:|:-------------------------:
    ![TapToPlaceInputSimulationHead](Images/Solver/TapToPlace/TapToPlaceInputSimulationHead.gif)  |  ![TapToPlaceInputSimulationControllerRay](Images/Solver/TapToPlace/TapToPlaceInputSimulationControllerRay.gif)

## <a name="tap-to-place-code-configurability"></a>Toccare per inserire la configurabilità del codice

Toccare per posizionare la tempistica di selezione degli oggetti può anche essere controllata tramite `StartPlacement()` e `StopPlacement()` anziché richiedere un evento click. Questa funzionalità è utile per la scrittura di test e fornisce un metodo alternativo per inserire un oggetto nell'editor senza usare il sistema di input MRTK.

1. Creare un oggetto gioco vuoto
1. Crea e alleghi lo script di esempio seguente all'oggetto gioco vuoto

    ```c#
    using UnityEngine;
    using Microsoft.MixedReality.Toolkit.Utilities.Solvers;

    public class TapToPlaceInputExample : MonoBehaviour
    {
        private GameObject cube;
        private TapToPlace tapToPlace;

        void Start()
        {
            cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
            cube.transform.localScale = Vector3.one * 0.2f;
            cube.transform.position = Vector3.forward * 0.7f;

            tapToPlace = cube.AddComponent<TapToPlace>();
        }

        void Update()
        {
            if (Input.GetKeyDown(KeyCode.U))
            {
                tapToPlace.StartPlacement();
            }
            if (Input.GetKeyDown(KeyCode.I))
            {
                tapToPlace.StopPlacement();
            }
        }
    }
    ```

1. In modalità di riproduzione premere il *tasto U* per iniziare a inserire il cubo
1. Premere il *tasto* i per arrestare la selezione host

## <a name="tap-to-place-example-scene"></a>Toccare per inserire la scena di esempio

La scena di esempio tap to Place è costituita da 4 oggetti posizionabili, ognuno con una configurazione diversa. La scena di esempio contiene i muri per mostrare il comportamento di posizionamento della superficie disabilitato per impostazione predefinita nella gerarchia. La scena di esempio è disponibile nel pacchetto Microsoft. MixedReality. Toolkit. Unity. examples Unity disponibile nella [pagina della versione](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases). Il percorso della scena è: *MRTK. Esempi/demo/risolutori/scene/TapToPlaceExample. Unity*

![TapToPlaceExampleScene](Images/Solver/TapToPlace/TapToPlaceExampleScene.gif)

## <a name="see-also"></a>Vedi anche

- [Risolutori](README_Solver.md)
- [Consapevolezza spaziale](SpatialAwareness/SpatialAwarenessGettingStarted.md)
- [Simulazione di input](InputSimulation/InputSimulationService.md)
- [Rilevamento della mano](Input/HandTracking.md)
- [Sguardo fisso](Input/Gaze.md)
