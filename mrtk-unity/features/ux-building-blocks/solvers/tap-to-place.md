---
title: Toccare per posizionare
description: Documentazione di TapToPlace MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, Tap to Place,
ms.openlocfilehash: 1664509a08c2d589d22b71df580328f3f3655c61
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176407"
---
# <a name="tap-to-place"></a>Toccare per posizionare

![ToccareToPlace](../../images/solver/tap-to-place/TapToPlaceIntroGif.gif)

Toccare per posizionare è un componente di interazione lontano usato per posizionare un oggetto di gioco sulla superficie. Questo componente è utile per posizionare gli oggetti in una mesh spaziale. Tocca per posizionare usa una combinazione di due clic e dello spostamento della testa per posizionare un oggetto. Un clic per avviare il posizionamento, lo spostamento della testa per controllare la posizione dell'oggetto e un clic per posizionare l'oggetto nella scena.

## <a name="using-tap-to-place"></a>Uso di Toccare per posizionare

1. Configurare la scena
    - Creare una nuova scena unity
    - Aggiungere MRTK alla scena passando al Toolkit di realtà  >  **mista e configurarlo**
    > [!NOTE]
    > Toccare per posizionare usa i clic guidati dal sistema di input MRTK, ma può anche essere controllato senza clic. Vedere la sezione Tap To Place Code Configurability riportata di seguito.
    - Aggiungere un cubo alla scena e impostare la scala su 0,2 e impostare la posizione su (0, 0, 0,7).
1. Associare [il tocco a Place](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.TapToPlace) a un oggetto di gioco con un collisore

    ![ToccareToPlaceInspector](../../images/solver/tap-to-place/TapToPlaceInspector2.png)

    - Quando viene aggiunto il componente Tap to Place, verrà collegato anche un gestore del risolutore. Toccare per posizionare deriva dalla classe [Risolutore](solver.md) che richiede un gestore risolutore. La posizione di un oggetto Tap to Place viene calcolata rispetto a `TrackedTargetType` all'interno del gestore del risolutore. Per impostazione predefinita, Head è , ad esempio quando la testa viene spostata, l'oggetto `TrackedTargetType` segue se è selezionato.  Può `TrackedTargetType` anche essere impostato su Controller Ray, che ha l'oggetto che segue il controller. Il primo gruppo di proprietà nel controllo Tap to Place è [Common Solver Properties](solver.md#common-solver-properties).  
    > [!IMPORTANT]
    > Toccare per posizionare è un risolutore autonomo e non può essere concatenato ad altri risolutori. Non può essere concatenato perché SolverHandler.UpdateSolvers viene usato per aggiornare la posizione dell'oggetto mentre viene inserito.
    - Toccare per posizionare le proprietà:
        - `Auto Start`: se true, il risolutore Tap to Place inizierà a controllare la posizione dell'oggetto di gioco da posizionare. L'oggetto inizierà immediatamente dopo TrackedTargetType (Head o Controller Ray). Questo valore deve essere modificato prima che Start() venga richiamato per avere alcun effetto.
        - `Default Placement Distance`: la distanza predefinita (in metri) di un oggetto verrà posizionata rispetto a TrackedTargetType in avanti in SolverHandler. L'oggetto gioco verrà posizionato alla distanza di posizionamento predefinita se una superficie non viene colpita dal raycast.
        - `Max Raycast Distance`: distanza massima (metri) per il raycast in base all'origine 'TrackedTargetType'. Questo raycast cerca una superficie per posizionare un oggetto selezionato.
        - `UseDefaultSurfaceNormalOffset`: questa proprietà è true per impostazione predefinita, assicura che l'oggetto inserito sia allineato su una superficie. Se questa proprietà è true, verrà applicato l'offset normale della superficie predefinito anziché qualsiasi valore specificato per la `SurfaceNormalOffset` proprietà . Se false, verrà applicato il `SurfaceNormalOffset` valore per . L'offset normale della superficie predefinito è l'extent del collisore lungo l'asse z.
        - `Surface Normal Offset`: distanza tra il centro dell'oggetto del gioco da posizionare e una superficie lungo la normale superficie, se il raggio raggiunge una superficie. Questa proprietà viene applicata a un oggetto solo se `UseDefaultSurfaceNormalOffset` è false.
        - `Keep Orientation Vertical`: se true, l'oggetto di gioco da posizionare rimarrà in posizione verticale e in linea con Vector3.up.
        - `Rotate According to Surface`: se false, l'oggetto di gioco da posizionare non ne modificherà la rotazione in base all'hit della superficie.  L'oggetto rimarrà rivolto verso la fotocamera mentre IsBeingPlaced è true.
        - `Magnetic Surfaces`: matrice di LayerMasks da eseguire dalla priorità più alta a quella più bassa. Per i calcoli della posizione verrà usata la prima maschera di livello per fornire un hit raycast.
        - `Debug Enabled`: se true e nell'editor unity, la normale dell'hit raycast verrà disegnata in giallo. Il debug abilitato è utile quando è true perché disegna la normale del colpo di superficie che spiega visivamente perché l'oggetto è `RotateAccordingToSurface` impostato sull'orientamento corrente.
        - `On Placing Started`: questo evento viene attivato una volta quando viene selezionato l'oggetto di gioco da posizionare.
        - `On Placing Stopped`: questo evento viene attivato una volta quando l'oggetto del gioco da posizionare viene deselezionato e inserito.

1. Test del comportamento del tocco per posizionare nell'editor
    - Premere play e tenere premuta la barra spaziatrice per visualizzare una mano di simulazione di input.
    - Spostare la mano fino a quando il cubo non è attivo e simulare un clic con la mano della simulazione di input facendo clic con il mouse a sinistra.
        - Se i collisori non sono presenti nella scena, l'oggetto seguirà `TrackedTargetType` in corrispondenza dell'oggetto `Default Placement Distance` definito.
    - L'oggetto seguirà lo spostamento dell'oggetto `TrackedTargetType` dopo la selezione. Per simulare lo spostamento della testa nell'editor, premere i tasti WASD. Modificare la rotazione della testa facendo clic e tenendo premuto il pulsante destro del mouse.
    - Per interrompere il posizionamento dell'oggetto, fare di nuovo clic.  Non è necessario che l'oggetto sia attivo per il clic di posizionamento di arresto. Lo stato attivo è necessario solo per il clic iniziale che avvia il processo di posizionamento.

    `TrackedTargetType`: Head (impostazione predefinita) |  `TrackedTargetType`: Controller Ray
    :-------------------------:|:-------------------------:
    ![Toccare Per posizionare il raggio di controllo head simulazione input](../../images/solver/tap-to-place/TapToPlaceInputSimulationHead.gif)  |  ![Toccare Per posizionare il controller di simulazione input Ray 2](../../images/solver/tap-to-place/TapToPlaceInputSimulationControllerRay.gif)

## <a name="tap-to-place-code-configurability"></a>Toccare per posizionare la configurazione del codice

È anche possibile controllare l'intervallo di selezione degli oggetti tramite e `StartPlacement()` invece di richiedere un evento `StopPlacement()` click. Questa funzionalità è utile per la scrittura di test e fornisce un metodo alternativo per inserire un oggetto nell'editor senza usare il sistema di input MRTK.

1. Creare un oggetto gioco vuoto
1. Creare e collegare lo script di esempio seguente all'oggetto gioco vuoto

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

1. In modalità di riproduzione premere *il tasto U* per iniziare a posizionare il cubo
1. Premere *il tasto I per* arrestare il posizionamento

## <a name="tap-to-place-example-scene"></a>Toccare per posizionare la scena di esempio

La scena di esempio Tap to Place è costituita da 4 oggetti posizionabili, ognuno con una configurazione diversa. La scena di esempio contiene le pareti per mostrare il comportamento di posizionamento della superficie disabilitato per impostazione predefinita nella gerarchia. La scena di esempio è disponibile in Microsoft.MixedReality. Toolkit. Pacchetto Unity.Examples unity disponibile nella [pagina di rilascio](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases). La posizione della scena è: *MRTK. Esempi/Demos/Risolutori/Scene/TapToPlaceExample.unity*

![Toccare To Place Example (Esempio di posizione)](../../images/solver/tap-to-place/TapToPlaceExampleScene.gif)

## <a name="see-also"></a>Vedere anche

- [Risolutori](solver.md)
- [Consapevolezza spaziale](../../spatial-awareness/spatial-awareness-getting-started.md)
- [Simulazione di input](../../input-simulation/input-simulation-service.md)
- [Tracciamento manuale](../../input/hand-tracking.md)
- [Sguardo fisso](../../input/gaze.md)
