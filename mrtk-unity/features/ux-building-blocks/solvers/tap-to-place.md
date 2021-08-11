---
title: Toccare per posizionare
description: Documentazione di TapToPlace MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Tap to Place,
ms.openlocfilehash: 98408312ec2637dc3fa137e7d51cce1f37e816f9a21b703ec9216bf90251661f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198319"
---
# <a name="tap-to-place"></a>Toccare per posizionare

![ToccareToPlace](../../images/solver/tap-to-place/TapToPlaceIntroGif.gif)

Toccare per posizionare è un componente di interazione da lontano usato per posizionare un oggetto gioco sulla superficie. Questo componente è utile per posizionare gli oggetti in una mesh spaziale. Toccare per posizionare usa una combinazione di due clic e movimento della testa per posizionare un oggetto. Un clic per avviare il posizionamento, il movimento della testa per controllare la posizione dell'oggetto e un clic per posizionare l'oggetto nella scena.

## <a name="using-tap-to-place"></a>Uso del tocco per posizionare

1. Configurare la scena
    - Creare una nuova scena unity
    - Aggiungere MRTK alla scena passando alla pagina **Mixed Reality (Realtà mista) Toolkit** Add to Scene  >  **(Aggiungi alla scena) e Configure (Configura)**
    > [!NOTE]
    > Toccare per posizionare usa i clic guidati dal sistema di input MRTK, ma può anche essere controllato senza clic. Vedere la sezione Configurazione del codice tap to place più avanti.
    - Aggiungere un cubo alla scena, modificare la scala in 0,2 e modificare la posizione in (0, 0, 0,7).
1. Collegare [Tap to Place (Tocco](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.TapToPlace) per posizionare) a un oggetto gioco con un collisore

    ![ToccareToPlaceInspector](../../images/solver/tap-to-place/TapToPlaceInspector2.png)

    - Quando viene aggiunto il componente Tap to Place (Tocca per posizionare), viene collegato anche un gestore risolutore. Toccare per posizionare deriva dalla classe [Risolutore](solver.md) che richiede un gestore risolutore. La posizione di un oggetto Tap to Place viene calcolata in relazione all'oggetto `TrackedTargetType` all'interno del gestore risolutore. Per impostazione predefinita, head è , ad esempio quando la testa si sposta, l'oggetto `TrackedTargetType` segue se è selezionato.  Può `TrackedTargetType` anche essere impostato su Controller Ray, che ha l'oggetto che segue il controller. Il primo gruppo di proprietà nel controllo Tap to Place (Tocca per posizionare) è Common Solver Properties (Proprietà [risolutore comune).](solver.md#common-solver-properties)  
    > [!IMPORTANT]
    > Toccare per posizionare è un risolutore autonomo e non può essere concatenato ad altri risolutori. Non può essere concatenato perché SolverHandler.UpdateSolvers viene usato per aggiornare la posizione dell'oggetto mentre è posizionato.
    - Toccare Per posizionare le proprietà:
        - `Auto Start`: se true, il risolutore Tap to Place inizierà a controllare la posizione dell'oggetto gioco da posizionare. L'oggetto inizierà immediatamente dopo TrackedTargetType (Head o Controller Ray). Questo valore deve essere modificato prima che Start() venga richiamato per avere effetto.
        - `Default Placement Distance`: distanza predefinita (in metri) di un oggetto rispetto a TrackedTargetType in avanti in SolverHandler. L'oggetto gioco verrà posizionato alla distanza di posizionamento predefinita se una superficie non viene raggiata dal raycast.
        - `Max Raycast Distance`: distanza massima (metri) per il raycast in base all'origine 'TrackedTargetType'. Questo raycast cerca una superficie in cui posizionare un oggetto selezionato.
        - `UseDefaultSurfaceNormalOffset`: questa proprietà è true per impostazione predefinita, assicura che l'oggetto posizionato sia allineato su una superficie. Se questa proprietà è true, verrà applicato l'offset normale della superficie predefinito anziché qualsiasi valore specificato per la `SurfaceNormalOffset` proprietà . Se false, verrà applicato `SurfaceNormalOffset` il valore per . L'offset normale della superficie predefinito è l'estensione del collisore lungo l'asse z.
        - `Surface Normal Offset`: distanza tra il centro dell'oggetto gioco da posizionare e una superficie lungo la normale superficie, se il raycast raggiunge una superficie. Questa proprietà viene applicata a un oggetto solo se `UseDefaultSurfaceNormalOffset` è false.
        - `Keep Orientation Vertical`: se true, l'oggetto gioco da posizionare rimarrà in posizione verticale e in linea con Vector3.up.
        - `Rotate According to Surface`: se false, l'oggetto gioco da posizionare non cambierà la rotazione in base all'hit della superficie.  L'oggetto rimarrà rivolto verso la fotocamera mentre IsBeingPlaced è true.
        - `Magnetic Surfaces`: matrice di LayerMasks da eseguire dalla priorità più alta a quella più bassa. Per i calcoli della posizione verrà usata la prima maschera di livello per fornire un hit raycast.
        - `Debug Enabled`: se true e nell'editor di Unity, la normale dell'hit raycast verrà disegnata in giallo. Debug abilitato è utile quando è true perché disegna la normale dell'impatto della superficie che spiega visivamente il motivo per cui l'oggetto è `RotateAccordingToSurface` impostato sull'orientamento corrente.
        - `On Placing Started`: questo evento viene attivato una volta quando viene selezionato l'oggetto gioco da posizionare.
        - `On Placing Stopped`: questo evento viene attivato una volta quando l'oggetto gioco da posizionare è deselezionato e posizionato.

1. Test del comportamento tocco per posizionare nell'editor
    - Premere play e tenere premuta la barra spaziatrice per visualizzare una mano di simulazione di input.
    - Spostare la mano fino a quando il cubo non è attivo e simulare un clic con la mano di simulazione di input facendo clic con il mouse a sinistra.
        - Se i collisori non sono presenti nella scena, l'oggetto seguirà `TrackedTargetType` in corrispondenza dell'oggetto `Default Placement Distance` definito.
    - L'oggetto seguirà lo spostamento di dopo `TrackedTargetType` la selezione. Per simulare lo spostamento della testa nell'editor, premere i tasti WASD. Modificare la rotazione della testa facendo clic e tenendo premuto il pulsante destro del mouse.
    - Per interrompere il posizionamento dell'oggetto, fare di nuovo clic su .  Non è necessario che l'oggetto sia nello stato attivo per il clic di posizionamento di arresto. Lo stato attivo è necessario solo per il clic iniziale che avvia il processo di posizionamento.

    `TrackedTargetType`: Head (impostazione predefinita) |  `TrackedTargetType`: Controller Ray
    :-------------------------:|:-------------------------:
    ![Toccare To Place Input Simulation Head Control ray (Raggio di controllo head simulazione input)](../../images/solver/tap-to-place/TapToPlaceInputSimulationHead.gif)  |  ![Toccare To Place Input Simulation Controller Ray 2 (Per posizionare il controller simulazione input Ray 2)](../../images/solver/tap-to-place/TapToPlaceInputSimulationControllerRay.gif)

## <a name="tap-to-place-code-configurability"></a>Toccare per posizionare la configurazione del codice

Toccare per posizionare gli intervalli di selezione degli oggetti può anche essere controllato tramite `StartPlacement()` e invece di richiedere un evento `StopPlacement()` click. Questa funzionalità è utile per la scrittura di test e fornisce un metodo alternativo per inserire un oggetto nell'editor senza usare il sistema di input MRTK.

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

1. In modalità di riproduzione premere *il tasto U per* iniziare a posizionare il cubo
1. Premere *il tasto I per* arrestare la selezione host

## <a name="tap-to-place-example-scene"></a>Toccare per posizionare la scena di esempio

La scena di esempio Tap to Place è costituita da 4 oggetti posizionabili, ognuno con una configurazione diversa. La scena di esempio contiene le pareti per mostrare il comportamento di posizionamento della superficie disabilitato per impostazione predefinita nella gerarchia. La scena di esempio è disponibile in Microsoft.MixedReality. Toolkit. Pacchetto Unity.Examples disponibile nella [pagina release](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases). La posizione della scena è: *MRTK. Examples/Demos/Solvers/Scenes/TapToPlaceExample.unity*

![Esempio di tocco sul posto](../../images/solver/tap-to-place/TapToPlaceExampleScene.gif)

## <a name="see-also"></a>Vedi anche

- [Risolutori](solver.md)
- [Consapevolezza spaziale](../../spatial-awareness/spatial-awareness-getting-started.md)
- [Simulazione di input](../../input-simulation/input-simulation-service.md)
- [Tracciamento delle mani](../../input/hand-tracking.md)
- [Sguardo fisso](../../input/gaze.md)
