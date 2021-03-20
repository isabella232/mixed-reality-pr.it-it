---
title: README_TapToPlace
description: Documentazione di TapToPlace MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, tocco a posto,
ms.openlocfilehash: 837199d1b4d58f14478ea0ae9b429a25cfea8e46
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695688"
---
# <a name="tap-to-place"></a><span data-ttu-id="6a629-104">Toccare per posizionare</span><span class="sxs-lookup"><span data-stu-id="6a629-104">Tap to Place</span></span>

![TapToPlace](Images/Solver/TapToPlace/TapToPlaceIntroGif.gif)

<span data-ttu-id="6a629-106">Toccare per posizionare è un componente di interazione molto usato per posizionare un oggetto gioco sulla superficie.</span><span class="sxs-lookup"><span data-stu-id="6a629-106">Tap to Place is a far interaction component that is used to place a game object on surface.</span></span> <span data-ttu-id="6a629-107">Questo componente è utile per inserire oggetti in una rete spaziale.</span><span class="sxs-lookup"><span data-stu-id="6a629-107">This component is useful for placing objects on a spatial mesh.</span></span> <span data-ttu-id="6a629-108">Toccare per posizionare usa una combinazione di due clic e movimento Head per inserire un oggetto.</span><span class="sxs-lookup"><span data-stu-id="6a629-108">Tap to Place uses a combination of two clicks and head movement to place an object.</span></span> <span data-ttu-id="6a629-109">Un clic per avviare la selezione host, lo spostamento Head per controllare la posizione dell'oggetto e un clic per posizionare l'oggetto nella scena.</span><span class="sxs-lookup"><span data-stu-id="6a629-109">A click to start the placement, head movement to control the position of the object and a click to place the object in the scene.</span></span>

## <a name="using-tap-to-place"></a><span data-ttu-id="6a629-110">Uso del tocco per posizionare</span><span class="sxs-lookup"><span data-stu-id="6a629-110">Using Tap to Place</span></span>

1. <span data-ttu-id="6a629-111">Configurare la scena</span><span class="sxs-lookup"><span data-stu-id="6a629-111">Set up the scene</span></span>
    - <span data-ttu-id="6a629-112">Crea una nuova scena Unity</span><span class="sxs-lookup"><span data-stu-id="6a629-112">Create a new unity scene</span></span>
    - <span data-ttu-id="6a629-113">Per aggiungere MRTK alla scena, passare al Toolkit di **realtà mista**  >  **Aggiungi alla scena e configurare**</span><span class="sxs-lookup"><span data-stu-id="6a629-113">Add MRTK to the scene by navigating to the **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    > [!NOTE]
    > <span data-ttu-id="6a629-114">Toccare per posizionare usa i clic basati sul sistema di input MRTK, ma può anche essere controllato senza clic, vedere la sezione tap to Place configurabilità del codice riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="6a629-114">Tap to Place uses clicks driven by the MRTK Input System but it can also be controlled without clicks, see the Tap To Place Code Configurability section below.</span></span>
    - <span data-ttu-id="6a629-115">Aggiungere un cubo alla scena e impostare la scala su 0,2 e impostare la posizione su (0, 0, 0,7).</span><span class="sxs-lookup"><span data-stu-id="6a629-115">Add a cube to the scene and change the scale to 0.2 and change the position to (0, 0, 0.7).</span></span>
1. <span data-ttu-id="6a629-116">Associa il [tocco alla posizione](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.TapToPlace) di un oggetto gioco con un Collider</span><span class="sxs-lookup"><span data-stu-id="6a629-116">Attach [Tap to Place](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.TapToPlace) to a game object with a collider</span></span>

    ![TapToPlaceInspector](Images/Solver/TapToPlace/TapToPlaceInspector2.png)

    - <span data-ttu-id="6a629-118">Quando viene aggiunto il componente tap to Place, viene collegato anche un gestore del Risolutore.</span><span class="sxs-lookup"><span data-stu-id="6a629-118">When the Tap to Place component is added, a Solver Handler will also be attached.</span></span> <span data-ttu-id="6a629-119">Toccare per posizionare deriva dalla classe [Solver](README_Solver.md) che richiede un gestore del Risolutore.</span><span class="sxs-lookup"><span data-stu-id="6a629-119">Tap to Place derives from the [Solver](README_Solver.md) class which requires a Solver Handler.</span></span> <span data-ttu-id="6a629-120">La posizione di un oggetto Tap per posizionare viene calcolata in relazione all'oggetto `TrackedTargetType` all'interno del gestore del Risolutore.</span><span class="sxs-lookup"><span data-stu-id="6a629-120">The position of a Tap to Place object is calculated relative to the `TrackedTargetType` within the Solver Handler.</span></span> <span data-ttu-id="6a629-121">Per impostazione predefinita, l'intestazione è `TrackedTargetType` , ovvero quando viene spostata, l'oggetto segue se è selezionato.</span><span class="sxs-lookup"><span data-stu-id="6a629-121">By default the Head is the `TrackedTargetType`, i.e. when the head moves, the object follows if it is selected.</span></span>  <span data-ttu-id="6a629-122">`TrackedTargetType`Può anche essere impostato su un raggio del controller che ha l'oggetto che segue il controller.</span><span class="sxs-lookup"><span data-stu-id="6a629-122">The `TrackedTargetType` can also be set to Controller Ray which has the object follow the controller.</span></span> <span data-ttu-id="6a629-123">Il primo gruppo di proprietà nel controllo Tap to Place è costituito dalle [proprietà del Risolutore comune](README_Solver.md#common-solver-properties).</span><span class="sxs-lookup"><span data-stu-id="6a629-123">The first group of properties in the Tap to Place inspector are the [Common Solver Properties](README_Solver.md#common-solver-properties).</span></span>  
    > [!IMPORTANT]
    > <span data-ttu-id="6a629-124">Il tocco da posizionare è un risolutore autonomo e non può essere concatenato ad altri risolutori.</span><span class="sxs-lookup"><span data-stu-id="6a629-124">Tap to Place is a stand alone Solver and cannot be chained with other Solvers.</span></span> <span data-ttu-id="6a629-125">Non può essere concatenato perché SolverHandler. UpdateSolvers viene usato per aggiornare la posizione dell'oggetto durante la sua immissione.</span><span class="sxs-lookup"><span data-stu-id="6a629-125">It cannot be chained because SolverHandler.UpdateSolvers is used to update the object's position while it is being placed.</span></span>
    - <span data-ttu-id="6a629-126">Toccare per inserire le proprietà:</span><span class="sxs-lookup"><span data-stu-id="6a629-126">Tap to Place Properties:</span></span>
        - <span data-ttu-id="6a629-127">`Auto Start`: Se true, il tocco per posizionare il Risolutore inizierà a controllare la posizione dell'oggetto gioco da inserire.</span><span class="sxs-lookup"><span data-stu-id="6a629-127">`Auto Start`: If true, the Tap to Place solver will start out controlling the position of the game object to be placed.</span></span> <span data-ttu-id="6a629-128">L'oggetto inizierà immediatamente dopo TrackedTargetType (Head o Ray controller).</span><span class="sxs-lookup"><span data-stu-id="6a629-128">The object will immediately start following the TrackedTargetType (Head or Controller Ray).</span></span> <span data-ttu-id="6a629-129">Questo valore deve essere modificato prima che venga richiamato Start () per avere un effetto.</span><span class="sxs-lookup"><span data-stu-id="6a629-129">This value must be modified before Start() is invoked in order to have any effect.</span></span>
        - <span data-ttu-id="6a629-130">`Default Placement Distance`: Distanza predefinita (in metri) in cui un oggetto verrà inserito rispetto al TrackedTargetType successivo in SolverHandler.</span><span class="sxs-lookup"><span data-stu-id="6a629-130">`Default Placement Distance`: The default distance (in meters) an object will be placed relative to the TrackedTargetType forward in the SolverHandler.</span></span> <span data-ttu-id="6a629-131">Se una superficie non viene raggiunta da Raycast, l'oggetto Game verrà posizionato alla distanza di posizionamento predefinita.</span><span class="sxs-lookup"><span data-stu-id="6a629-131">The game object will be placed at the default placement distance if a surface is not hit by the raycast.</span></span>
        - <span data-ttu-id="6a629-132">`Max Raycast Distance`: Distanza massima (contatori) per il Raycast in base all'origine ' TrackedTargetType '.</span><span class="sxs-lookup"><span data-stu-id="6a629-132">`Max Raycast Distance`: The max distance (meters) for the raycast based on the 'TrackedTargetType' origin.</span></span> <span data-ttu-id="6a629-133">Questo Raycast cerca una superficie per inserire un oggetto selezionato.</span><span class="sxs-lookup"><span data-stu-id="6a629-133">This raycast looks for a surface to place a selected object.</span></span>
        - <span data-ttu-id="6a629-134">`Surface Normal Offset`: Distanza tra il centro dell'oggetto gioco e una superficie lungo la normale della superficie, se il Raycast raggiunge una superficie.</span><span class="sxs-lookup"><span data-stu-id="6a629-134">`Surface Normal Offset`: The distance between the center of the game object to place and a surface along the surface normal, if the raycast hits a surface.</span></span> <span data-ttu-id="6a629-135">Per impostazione predefinita, l'offset normale della superficie è 0 ma dopo l'avvio () l'offset normale della superficie è impostato sugli extent del Collider lungo l'asse z.</span><span class="sxs-lookup"><span data-stu-id="6a629-135">By default, the surface normal offset is 0 but after Start() the surface normal offset is set to the collider's extents along the z axis.</span></span>
        - <span data-ttu-id="6a629-136">`Keep Orientation Vertical`: Se è true, l'oggetto Game da inserire rimarrà in verticale e in linea con Vector3. up.</span><span class="sxs-lookup"><span data-stu-id="6a629-136">`Keep Orientation Vertical`: If true, the game object to place will remain upright and in line with Vector3.up.</span></span>
        - <span data-ttu-id="6a629-137">`Rotate According to Surface`: Se false, l'oggetto Game da inserire non modifica la rotazione in base alla superficie raggiunta.</span><span class="sxs-lookup"><span data-stu-id="6a629-137">`Rotate According to Surface`: If false, the game object to place will not change its rotation according to the surface hit.</span></span>  <span data-ttu-id="6a629-138">L'oggetto rimarrà connesso alla videocamera mentre IsBeingPlaced è true.</span><span class="sxs-lookup"><span data-stu-id="6a629-138">The object will remain facing the camera while IsBeingPlaced is true.</span></span>
        - <span data-ttu-id="6a629-139">`Magnetic Surfaces`: Matrice di LayerMasks da eseguire dalla priorità più alta alla più bassa.</span><span class="sxs-lookup"><span data-stu-id="6a629-139">`Magnetic Surfaces`: An array of LayerMasks to execute from highest to lowest priority.</span></span> <span data-ttu-id="6a629-140">Prima maschera di livello per fornire un hit Raycast verrà usato per i calcoli di posizione.</span><span class="sxs-lookup"><span data-stu-id="6a629-140">First layer mask to provide a raycast hit will be used for position calculations.</span></span>
        - <span data-ttu-id="6a629-141">`Debug Enabled`: Se è true e nell'editor di Unity, il valore normale del Raycast hit verrà disegnato in giallo.</span><span class="sxs-lookup"><span data-stu-id="6a629-141">`Debug Enabled`: If true and in the Unity Editor, the normal of the raycast hit will be drawn in yellow.</span></span> <span data-ttu-id="6a629-142">Il debug abilitato è utile quando `RotateAccordingToSurface` è true perché disegna la normale della superficie raggiunta, che spiega visivamente il motivo per cui l'oggetto viene impostato sull'orientamento corrente.</span><span class="sxs-lookup"><span data-stu-id="6a629-142">Debug enabled is useful when `RotateAccordingToSurface` is true because it draws the normal of the surface hit which visually explains why the object is set at its current orientation.</span></span>
        - <span data-ttu-id="6a629-143">`On Placing Started`: Questo evento viene attivato una volta quando viene selezionato l'oggetto gioco da inserire.</span><span class="sxs-lookup"><span data-stu-id="6a629-143">`On Placing Started`: This event is triggered once when the game object to place is selected.</span></span>
        - <span data-ttu-id="6a629-144">`On Placing Stopped`: Questo evento viene generato una volta quando l'oggetto Game da inserire viene deselezionato, inserito.</span><span class="sxs-lookup"><span data-stu-id="6a629-144">`On Placing Stopped`: This event is triggered once when the game object to place is unselected, placed.</span></span>

1. <span data-ttu-id="6a629-145">Test del comportamento di tap per posizionare nell'editor</span><span class="sxs-lookup"><span data-stu-id="6a629-145">Testing Tap to Place behavior in editor</span></span>
    - <span data-ttu-id="6a629-146">Premere Riproduci e tenere premuto la barra spaziatrice per visualizzare una mano di simulazione di input.</span><span class="sxs-lookup"><span data-stu-id="6a629-146">Press play and hold the space bar to show an input simulation hand.</span></span>
    - <span data-ttu-id="6a629-147">Spostare la mano fino a quando il cubo non è attivo e simulare un clic con la mano della simulazione di input facendo clic con il pulsante sinistro del mouse.</span><span class="sxs-lookup"><span data-stu-id="6a629-147">Move the hand until the cube is in focus and simulate a click with the input simulation hand by clicking with the left mouse.</span></span>
        - <span data-ttu-id="6a629-148">Se i Collider non sono presenti nella scena, l'oggetto seguirà `TrackedTargetType` in corrispondenza dell'oggetto definito `Default Placement Distance` .</span><span class="sxs-lookup"><span data-stu-id="6a629-148">If colliders are not present in the scene, the object will follow the `TrackedTargetType` at the defined `Default Placement Distance`.</span></span>
    - <span data-ttu-id="6a629-149">L'oggetto seguirà lo spostamento della `TrackedTargetType` selezione dopo.</span><span class="sxs-lookup"><span data-stu-id="6a629-149">The object will follow the movement of the `TrackedTargetType` after selection.</span></span> <span data-ttu-id="6a629-150">Per simulare il movimento Head nell'editor, premere i tasti WASD.</span><span class="sxs-lookup"><span data-stu-id="6a629-150">To simulate head movement in editor, press the WASD keys.</span></span> <span data-ttu-id="6a629-151">Modificare la rotazione della testa facendo clic e tenendo premuto il pulsante destro del mouse.</span><span class="sxs-lookup"><span data-stu-id="6a629-151">Change head rotation by clicking and holding the right mouse.</span></span>
    - <span data-ttu-id="6a629-152">Per arrestare l'inserimento dell'oggetto, fare di nuovo clic su.</span><span class="sxs-lookup"><span data-stu-id="6a629-152">To stop placing the object, click again.</span></span>  <span data-ttu-id="6a629-153">Non è necessario che l'oggetto sia attivo per il clic su Arresta selezione host.</span><span class="sxs-lookup"><span data-stu-id="6a629-153">The object does not need to be in focus for the stop placement click.</span></span> <span data-ttu-id="6a629-154">Lo stato attivo è necessario solo per il clic iniziale che avvia il processo di selezione host.</span><span class="sxs-lookup"><span data-stu-id="6a629-154">Focus is only required for the initial click that starts the placement process.</span></span>

    <span data-ttu-id="6a629-155">`TrackedTargetType`: Head (impostazione predefinita)</span><span class="sxs-lookup"><span data-stu-id="6a629-155">`TrackedTargetType`: Head (Default)</span></span> |  <span data-ttu-id="6a629-156">`TrackedTargetType`: Raggio controller</span><span class="sxs-lookup"><span data-stu-id="6a629-156">`TrackedTargetType`: Controller Ray</span></span>
    :-------------------------:|:-------------------------:
    ![TapToPlaceInputSimulationHead](Images/Solver/TapToPlace/TapToPlaceInputSimulationHead.gif)  |  ![TapToPlaceInputSimulationControllerRay](Images/Solver/TapToPlace/TapToPlaceInputSimulationControllerRay.gif)

## <a name="tap-to-place-code-configurability"></a><span data-ttu-id="6a629-159">Toccare per inserire la configurabilità del codice</span><span class="sxs-lookup"><span data-stu-id="6a629-159">Tap to Place Code Configurability</span></span>

<span data-ttu-id="6a629-160">Toccare per posizionare la tempistica di selezione degli oggetti può anche essere controllata tramite `StartPlacement()` e `StopPlacement()` anziché richiedere un evento click.</span><span class="sxs-lookup"><span data-stu-id="6a629-160">Tap to Place object selection timing can also be controlled via `StartPlacement()` and `StopPlacement()` instead of requiring a click event.</span></span> <span data-ttu-id="6a629-161">Questa funzionalità è utile per la scrittura di test e fornisce un metodo alternativo per inserire un oggetto nell'editor senza usare il sistema di input MRTK.</span><span class="sxs-lookup"><span data-stu-id="6a629-161">This capability is useful for writing tests and provides an alternative method to place an object in editor without using the MRTK Input System.</span></span>

1. <span data-ttu-id="6a629-162">Creare un oggetto gioco vuoto</span><span class="sxs-lookup"><span data-stu-id="6a629-162">Create an empty game object</span></span>
1. <span data-ttu-id="6a629-163">Crea e alleghi lo script di esempio seguente all'oggetto gioco vuoto</span><span class="sxs-lookup"><span data-stu-id="6a629-163">Create and attach the following example script to the empty game object</span></span>

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

1. <span data-ttu-id="6a629-164">In modalità di riproduzione premere il *tasto U* per iniziare a inserire il cubo</span><span class="sxs-lookup"><span data-stu-id="6a629-164">In play mode, press the *U key* to start placing the cube</span></span>
1. <span data-ttu-id="6a629-165">Premere il *tasto* i per arrestare la selezione host</span><span class="sxs-lookup"><span data-stu-id="6a629-165">Press the *I key* to stop the placement</span></span>

## <a name="tap-to-place-example-scene"></a><span data-ttu-id="6a629-166">Toccare per inserire la scena di esempio</span><span class="sxs-lookup"><span data-stu-id="6a629-166">Tap to Place Example Scene</span></span>

<span data-ttu-id="6a629-167">La scena di esempio tap to Place è costituita da 4 oggetti posizionabili, ognuno con una configurazione diversa.</span><span class="sxs-lookup"><span data-stu-id="6a629-167">The Tap to Place example scene consists of 4 placeable objects, each with a different configuration.</span></span> <span data-ttu-id="6a629-168">La scena di esempio contiene i muri per mostrare il comportamento di posizionamento della superficie disabilitato per impostazione predefinita nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="6a629-168">The example scene contains walls to show the surface placement behavior that are disabled by default in the hierarchy.</span></span> <span data-ttu-id="6a629-169">La scena di esempio è disponibile nel pacchetto Microsoft. MixedReality. Toolkit. Unity. examples Unity disponibile nella [pagina della versione](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span><span class="sxs-lookup"><span data-stu-id="6a629-169">The example scene can be found in the Microsoft.MixedReality.Toolkit.Unity.Examples unity package found on the [Release Page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span> <span data-ttu-id="6a629-170">Il percorso della scena è: *MRTK. Esempi/demo/risolutori/scene/TapToPlaceExample. Unity*</span><span class="sxs-lookup"><span data-stu-id="6a629-170">The scene location is: *MRTK.Examples/Demos/Solvers/Scenes/TapToPlaceExample.unity*</span></span>

![TapToPlaceExampleScene](Images/Solver/TapToPlace/TapToPlaceExampleScene.gif)

## <a name="see-also"></a><span data-ttu-id="6a629-172">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="6a629-172">See also</span></span>

- [<span data-ttu-id="6a629-173">Risolutori</span><span class="sxs-lookup"><span data-stu-id="6a629-173">Solvers</span></span>](README_Solver.md)
- [<span data-ttu-id="6a629-174">Consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="6a629-174">Spatial Awareness</span></span>](SpatialAwareness/SpatialAwarenessGettingStarted.md)
- [<span data-ttu-id="6a629-175">Simulazione di input</span><span class="sxs-lookup"><span data-stu-id="6a629-175">Input Simulation</span></span>](InputSimulation/InputSimulationService.md)
- [<span data-ttu-id="6a629-176">Rilevamento della mano</span><span class="sxs-lookup"><span data-stu-id="6a629-176">Hand Tracking</span></span>](Input/HandTracking.md)
- [<span data-ttu-id="6a629-177">Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="6a629-177">Gaze</span></span>](Input/Gaze.md)
