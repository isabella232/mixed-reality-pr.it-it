---
title: Leap Motion MRTK
description: Documentazione da configurare per Leap Motion
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, Leap Motion,
ms.openlocfilehash: 44593713f08a00fa53325eebfae2cf9042d386be
ms.sourcegitcommit: 62beb626b2db6ce7df86014bd22bf1946b8906b9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2021
ms.locfileid: "110207473"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="103cd-104">Come configurare leap motion (by Ultraleap) Hand Tracking in MRTK</span><span class="sxs-lookup"><span data-stu-id="103cd-104">How to Configure Leap Motion (by Ultraleap) Hand Tracking in MRTK</span></span>

<span data-ttu-id="103cd-105">Per [usare questo provider](https://www.ultraleap.com/product/leap-motion-controller/) di dati è necessario un leap motion controller.</span><span class="sxs-lookup"><span data-stu-id="103cd-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="103cd-106">La funzionalità Leap Motion provider di dati il tracciamento articolato della mano per la realtà virtuale e può essere utile per la creazione rapida di prototipi nell'editor.</span><span class="sxs-lookup"><span data-stu-id="103cd-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="103cd-107">Il provider di dati può essere configurato per l'uso del Leap Motion Controller montato su un visore o posizionato su un visore da tavolo.</span><span class="sxs-lookup"><span data-stu-id="103cd-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="103cd-109">Questo provider può essere usato nell'editor e nel dispositivo mentre si usa la piattaforma autonoma.</span><span class="sxs-lookup"><span data-stu-id="103cd-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="103cd-110">Può anche essere usato nell'editor nella piattaforma UWP, ma NON in una build UWP.</span><span class="sxs-lookup"><span data-stu-id="103cd-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

| <span data-ttu-id="103cd-111">Versione di MRTK</span><span class="sxs-lookup"><span data-stu-id="103cd-111">MRTK Version</span></span> | <span data-ttu-id="103cd-112">Versioni dei moduli Leap Motion Unity supportate</span><span class="sxs-lookup"><span data-stu-id="103cd-112">Leap Motion Unity Modules Versions Supported</span></span> |
| --- | --- |
|<span data-ttu-id="103cd-113">2.6.x</span><span class="sxs-lookup"><span data-stu-id="103cd-113">2.6.x</span></span> | <span data-ttu-id="103cd-114">4.5.0, 4.5.1</span><span class="sxs-lookup"><span data-stu-id="103cd-114">4.5.0, 4.5.1</span></span>|
|<span data-ttu-id="103cd-115">2.7.x</span><span class="sxs-lookup"><span data-stu-id="103cd-115">2.7.x</span></span>| <span data-ttu-id="103cd-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1</span><span class="sxs-lookup"><span data-stu-id="103cd-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1</span></span>|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="103cd-117">Uso del tracciamento manuale leap motion (by Ultraleap) in MRTK</span><span class="sxs-lookup"><span data-stu-id="103cd-117">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="103cd-118">Importazione di moduli MRTK e Leap Motion Unity</span><span class="sxs-lookup"><span data-stu-id="103cd-118">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="103cd-119">Installare [l'SDK Leap Motion più](https://developer.leapmotion.com/releases/?category=orion) recente se non è già installato</span><span class="sxs-lookup"><span data-stu-id="103cd-119">Install the latest [Leap Motion SDK](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="103cd-120">Importare **il pacchetto Microsoft.MixedReality.Toolkit.Foundation** nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="103cd-120">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="103cd-121">Scaricare e importare la versione più recente [dei moduli Leap Motion Unity](https://developer.leapmotion.com/unity) nel progetto</span><span class="sxs-lookup"><span data-stu-id="103cd-121">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="103cd-122">Importare solo il **pacchetto Core** all'interno dei moduli Unity</span><span class="sxs-lookup"><span data-stu-id="103cd-122">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="103cd-123">Integrare i moduli Leap Motion Unity con MRTK</span><span class="sxs-lookup"><span data-stu-id="103cd-123">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="103cd-124">Quando i moduli Unity sono nel progetto, passare a **Mixed Reality Toolkit** Leap Motion Integrate Leap Motion Unity Modules (Mixed Reality Toolkit Leap  >  **Motion** Integrate Leap Motion Unity  >  **Modules)**</span><span class="sxs-lookup"><span data-stu-id="103cd-124">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="103cd-125">L'integrazione dei moduli Unity in MRTK aggiunge 10 definizioni di assembly al progetto e aggiunge riferimenti alla definizione dell'assembly **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.**</span><span class="sxs-lookup"><span data-stu-id="103cd-125">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="103cd-126">Verificare che Visual Studio sia chiuso.</span><span class="sxs-lookup"><span data-stu-id="103cd-126">Make sure Visual Studio is closed.</span></span>

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="103cd-128">Aggiunta della proprietà Leap Motion provider di dati</span><span class="sxs-lookup"><span data-stu-id="103cd-128">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="103cd-129">Creare una nuova scena Unity</span><span class="sxs-lookup"><span data-stu-id="103cd-129">Create a new Unity scene</span></span>
    - <span data-ttu-id="103cd-130">Aggiungere MRTK alla scena passando a **Mixed Reality Toolkit** Add to Scene and Configure (Aggiungi alla scena e  >  **configura)**</span><span class="sxs-lookup"><span data-stu-id="103cd-130">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="103cd-131">Selezionare l'oggetto gioco MixedRealityToolkit nella gerarchia e selezionare Copia e **personalizza** per clonare il profilo di realtà mista predefinito.</span><span class="sxs-lookup"><span data-stu-id="103cd-131">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="103cd-133">Selezionare il profilo **di configurazione** dell'input</span><span class="sxs-lookup"><span data-stu-id="103cd-133">Select the **Input** Configuration Profile</span></span>

    ![Profilo di configurazione dell'input 1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="103cd-135">Selezionare **Clona** nel profilo di sistema di input per abilitare la modifica.</span><span class="sxs-lookup"><span data-stu-id="103cd-135">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="103cd-137">Aprire la **sezione Provider di** dati di input, selezionare **Aggiungi** provider di dati nella parte superiore. Alla fine dell'elenco verrà aggiunto un nuovo provider di dati.</span><span class="sxs-lookup"><span data-stu-id="103cd-137">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="103cd-138">Aprire il nuovo provider di dati e impostare **Type** su **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="103cd-138">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Leap Add provider di dati](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="103cd-140">Selezionare **Clona** per modificare le impostazioni predefinite di Leap Motion.</span><span class="sxs-lookup"><span data-stu-id="103cd-140">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="103cd-142">L'provider di dati Leap Motion contiene `LeapControllerOrientation` la proprietà che rappresenta la posizione del controller di movimento Leap.</span><span class="sxs-lookup"><span data-stu-id="103cd-142">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="103cd-143">`LeapControllerOrientation.Headset` indica che il controller è montato su un visore.</span><span class="sxs-lookup"><span data-stu-id="103cd-143">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="103cd-144">`LeapControllerOrientation.Desk` indica che il controller è posizionato piano sulla scrivania.</span><span class="sxs-lookup"><span data-stu-id="103cd-144">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="103cd-145">Il valore predefinito è impostato su `LeapControllerOrientation.Headset` .</span><span class="sxs-lookup"><span data-stu-id="103cd-145">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="103cd-146">Ogni orientamento del controller contiene le proprietà di offset:</span><span class="sxs-lookup"><span data-stu-id="103cd-146">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="103cd-147">Le **proprietà di** offset dell'orientamento visore rispecchiano le proprietà di offset nel componente LeapXRServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="103cd-147">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="103cd-148">Dispone `LeapVRDeviceOffsetMode` di tre opzioni: Predefinito, Offset testina manuale e Trasformazione.</span><span class="sxs-lookup"><span data-stu-id="103cd-148">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="103cd-149">Se la modalità di offset è Default, non verrà applicato un offset al Controller di movimento Leap.</span><span class="sxs-lookup"><span data-stu-id="103cd-149">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="103cd-150">La modalità Offset head manuale consente la modifica di tre proprietà: `LeapVRDeviceOffsetY` e `LeapVRDeviceOffsetZ` `LeapVRDeviceTiltX` .</span><span class="sxs-lookup"><span data-stu-id="103cd-150">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="103cd-151">I valori della proprietà offset dell'asse vengono quindi applicati al posizionamento predefinito del controller.</span><span class="sxs-lookup"><span data-stu-id="103cd-151">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="103cd-152">La modalità Offset trasformazione contiene la `LeapVRDeviceOrigin` proprietà Transform che specifica una nuova origine per Leap Motion Controller.</span><span class="sxs-lookup"><span data-stu-id="103cd-152">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="103cd-153">**L'orientamento desk** contiene la `LeapControllerOffset` proprietà che definisce la posizione di ancoraggio delle mani intercalare della scrivania.</span><span class="sxs-lookup"><span data-stu-id="103cd-153">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="103cd-154">L'offset viene calcolato in relazione alla posizione principale della fotocamera e il valore predefinito è (0,-0,2, 0,35) per assicurarsi che le mani vengano visualizzate davanti e in vista della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="103cd-154">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="103cd-155">Le proprietà di offset nel profilo vengono applicate una volta all'avvio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="103cd-155">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="103cd-156">Per modificare i valori durante il runtime, ottenere Leap Motion Service Provider da Leap Motion Device Manager:</span><span class="sxs-lookup"><span data-stu-id="103cd-156">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="103cd-157">`EnterPinchDistance` e `ExitPinchDistance` sono le soglie di distanza per il rilevamento dei movimenti di tocco di avvicinamento/aria.</span><span class="sxs-lookup"><span data-stu-id="103cd-157">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="103cd-158">Il movimento di avvicinamento delle dita viene calcolato misurando la distanza tra la punta dell'indice e la punta del pollice.</span><span class="sxs-lookup"><span data-stu-id="103cd-158">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="103cd-159">Per generare un evento on input down, il valore `EnterPinchDistance` predefinito è 0,02.</span><span class="sxs-lookup"><span data-stu-id="103cd-159">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="103cd-160">Per generare un evento on input up (uscita dalla dita), la distanza predefinita tra la punta dell'indice e la punta del pollice è 0,05.</span><span class="sxs-lookup"><span data-stu-id="103cd-160">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="103cd-161">`LeapControllerOrientation`: Visore (impostazione predefinita)</span><span class="sxs-lookup"><span data-stu-id="103cd-161">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="103cd-162">`LeapControllerOrientation`: Desk</span><span class="sxs-lookup"><span data-stu-id="103cd-162">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="103cd-167">Test del movimento leap provider di dati</span><span class="sxs-lookup"><span data-stu-id="103cd-167">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="103cd-168">Dopo aver aggiunto Leap Motion provider di dati al profilo del sistema di input, premere play, spostare la mano davanti a Leap Motion Controller. Verrà visualizzata la rappresentazione congiunta della mano.</span><span class="sxs-lookup"><span data-stu-id="103cd-168">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="103cd-169">Compilazione del progetto</span><span class="sxs-lookup"><span data-stu-id="103cd-169">Building your project</span></span>
    - <span data-ttu-id="103cd-170">Passare a **Impostazioni di compilazione > file**</span><span class="sxs-lookup"><span data-stu-id="103cd-170">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="103cd-171">Sono supportate solo le build autonome se si usa leap motion provider di dati.</span><span class="sxs-lookup"><span data-stu-id="103cd-171">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="103cd-172">Per istruzioni su come usare un visore VR Windows Mixed Reality per le build autonome, vedere Compilazione e distribuzione di [MRTK (Standalone).](wmr-mrtk.md#building-and-deploying-mrtk-standalone)</span><span class="sxs-lookup"><span data-stu-id="103cd-172">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="103cd-173">Ottenere le giunzioni della mano</span><span class="sxs-lookup"><span data-stu-id="103cd-173">Getting the hand joints</span></span>

<span data-ttu-id="103cd-174">Ottenere giunzioni usando il provider di dati leap è identico al recupero delle giunzioni delle mani per una mano articolata MRTK.</span><span class="sxs-lookup"><span data-stu-id="103cd-174">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="103cd-175">Per altre informazioni, vedere [Tracciamento delle mani.](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils)</span><span class="sxs-lookup"><span data-stu-id="103cd-175">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="103cd-176">Con MRTK in una scena unity e il provider di dati Leap Motion aggiunto come provider di dati di input nel profilo input system, creare un oggetto gioco vuoto e allegare lo script di esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="103cd-176">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="103cd-177">Questo script è un semplice esempio di come recuperare la posizione del giunzione del palmo in un leap motion hand.</span><span class="sxs-lookup"><span data-stu-id="103cd-177">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="103cd-178">Una sfera segue la mano leap sinistra, mentre un cubo segue la mano leap destra.</span><span class="sxs-lookup"><span data-stu-id="103cd-178">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using System.Collections.Generic;
using UnityEngine;

public class LeapHandJoints : MonoBehaviour, IMixedRealityHandJointHandler
{
    private GameObject leftHandSphere;
    private GameObject rightHandCube;

    private void Start()
    {
        // Register the HandJointHandler as a global listener
        CoreServices.InputSystem.RegisterHandler<IMixedRealityHandJointHandler>(this);

        // Create a sphere to follow the left hand palm position
        leftHandSphere = GameObject.CreatePrimitive(PrimitiveType.Sphere);
        leftHandSphere.transform.localScale = Vector3.one * 0.03f;

        // Create a cube to follow the right hand palm position
        rightHandCube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        rightHandCube.transform.localScale = Vector3.one * 0.03f;
    }

    public void OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == Handedness.Left)
        {
            Vector3 leftHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            leftHandSphere.transform.position = leftHandPalmPosition;
        }

        if (eventData.Handedness == Handedness.Right)
        {
            Vector3 rightHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            rightHandCube.transform.position = rightHandPalmPosition;
        }
    }
```

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="103cd-179">Suggerimento per il flusso di lavoro dell'editor unity</span><span class="sxs-lookup"><span data-stu-id="103cd-179">Unity editor workflow tip</span></span>

<span data-ttu-id="103cd-180">L'uso dell'provider di dati Leap non richiede un visore VR.</span><span class="sxs-lookup"><span data-stu-id="103cd-180">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="103cd-181">Le modifiche apportate a un'app MRTK possono essere testate nell'editor con le mani leap senza visore VR.</span><span class="sxs-lookup"><span data-stu-id="103cd-181">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="103cd-182">Leap Motion Hands verrà visualizzato nell'editor, senza un visore VR collegato.</span><span class="sxs-lookup"><span data-stu-id="103cd-182">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="103cd-183">Se `LeapControllerOrientation` l'opzione è impostata su **Headset,** il controller Leap Motion dovrà essere tenuto in mano da una mano con la fotocamera rivolta in avanti.</span><span class="sxs-lookup"><span data-stu-id="103cd-183">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="103cd-184">Se la fotocamera viene spostata usando chiavi WASD nell'editor e l'oggetto è Headset, le mani `LeapControllerOrientation` non seguiranno la fotocamera. </span><span class="sxs-lookup"><span data-stu-id="103cd-184">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="103cd-185">Le mani seguiranno lo spostamento della fotocamera solo se un visore VR è collegato mentre `LeapControllerOrientation` l'opzione è impostata **su Headset**.</span><span class="sxs-lookup"><span data-stu-id="103cd-185">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="103cd-186">Le mani leap seguiranno lo spostamento della fotocamera nell'editor se `LeapControllerOrientation` è impostato su **Desk**.</span><span class="sxs-lookup"><span data-stu-id="103cd-186">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="103cd-187">Rimozione del movimento leap dal progetto</span><span class="sxs-lookup"><span data-stu-id="103cd-187">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="103cd-188">Passare ai moduli **Leap Motion** Separate Leap Motion Unity  >    >  **di** Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="103cd-188">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="103cd-189">Consentire l'aggiornamento di Unity quando i riferimenti nel file **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** vengono modificati in questo passaggio</span><span class="sxs-lookup"><span data-stu-id="103cd-189">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="103cd-190">Chiudere Unity</span><span class="sxs-lookup"><span data-stu-id="103cd-190">Close Unity</span></span>
1. <span data-ttu-id="103cd-191">Chiudere Visual Studio, se è aperto</span><span class="sxs-lookup"><span data-stu-id="103cd-191">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="103cd-192">Aprire Esplora file e passare alla radice del progetto UNITY MRTK</span><span class="sxs-lookup"><span data-stu-id="103cd-192">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="103cd-193">Eliminare la directory **UnityProjectName/Library**</span><span class="sxs-lookup"><span data-stu-id="103cd-193">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="103cd-194">Eliminare la directory **UnityProjectName/Assets/Plugins/LeapMotion**</span><span class="sxs-lookup"><span data-stu-id="103cd-194">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="103cd-195">Eliminare il file **UnityProjectName/Assets/Plugins/LeapMotion.meta**</span><span class="sxs-lookup"><span data-stu-id="103cd-195">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="103cd-196">Riaprire Unity</span><span class="sxs-lookup"><span data-stu-id="103cd-196">Reopen Unity</span></span>

<span data-ttu-id="103cd-197">In Unity 2018.4 è possibile notare che gli errori rimangono nella console dopo l'eliminazione della libreria e degli asset leap motion core.</span><span class="sxs-lookup"><span data-stu-id="103cd-197">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="103cd-198">Se vengono registrati errori dopo la riapertura, riavviare di nuovo Unity.</span><span class="sxs-lookup"><span data-stu-id="103cd-198">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="103cd-199">Errori comuni</span><span class="sxs-lookup"><span data-stu-id="103cd-199">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="103cd-200">Leap Motion non è integrato con MRTK</span><span class="sxs-lookup"><span data-stu-id="103cd-200">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="103cd-201">Per verificare se i moduli Leap Motion Unity sono integrati con MRTK:</span><span class="sxs-lookup"><span data-stu-id="103cd-201">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="103cd-202">Passare a **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span><span class="sxs-lookup"><span data-stu-id="103cd-202">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="103cd-203">Verrà visualizzata una finestra popup con un messaggio che indica se i moduli Leap Motion Unity sono integrati o meno con MRTK.</span><span class="sxs-lookup"><span data-stu-id="103cd-203">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="103cd-204">Se il messaggio indica che gli asset non sono stati integrati:</span><span class="sxs-lookup"><span data-stu-id="103cd-204">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="103cd-205">Assicurarsi che i moduli Leap Motion Unity siano presenti nel progetto</span><span class="sxs-lookup"><span data-stu-id="103cd-205">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="103cd-206">Assicurarsi che la versione aggiunta sia supportata. Vedere la tabella nella parte superiore della pagina per le versioni supportate.</span><span class="sxs-lookup"><span data-stu-id="103cd-206">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="103cd-207">Provare **Mixed Reality Toolkit > Utilities > Leap Motion > integrare i moduli Leap Motion Unity**</span><span class="sxs-lookup"><span data-stu-id="103cd-207">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="103cd-208">La copia dell'assembly Multiplayer HLAPI non è riuscita</span><span class="sxs-lookup"><span data-stu-id="103cd-208">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="103cd-209">Durante l'importazione degli asset principali di Leap Motion Unity, è possibile che venga registrato questo errore:</span><span class="sxs-lookup"><span data-stu-id="103cd-209">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="103cd-210">**Soluzione**</span><span class="sxs-lookup"><span data-stu-id="103cd-210">**Solution**</span></span>

- <span data-ttu-id="103cd-211">Una soluzione a breve termine consiste nel riavviare Unity.</span><span class="sxs-lookup"><span data-stu-id="103cd-211">A short term solution is to restart Unity.</span></span> <span data-ttu-id="103cd-212">Per [altre informazioni, vedere il problema 7761.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761)</span><span class="sxs-lookup"><span data-stu-id="103cd-212">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="103cd-213">Scena di esempio leap motion</span><span class="sxs-lookup"><span data-stu-id="103cd-213">Leap Motion Example Scene</span></span>

<span data-ttu-id="103cd-214">La scena di esempio usa il profilo DefaultLeapMotionConfiguration e determina se il progetto Unity è stato configurato correttamente per usare leap motion provider di dati.</span><span class="sxs-lookup"><span data-stu-id="103cd-214">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="103cd-215">La scena di esempio è contenuta nel pacchetto **Microsoft.MixedReality.Toolkit.Examples** nella directory **MRTK/Examples/Demos/HandTracking/.**</span><span class="sxs-lookup"><span data-stu-id="103cd-215">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="103cd-216">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="103cd-216">See also</span></span>

- [<span data-ttu-id="103cd-217">Provider di input</span><span class="sxs-lookup"><span data-stu-id="103cd-217">Input Providers</span></span>](../features/input/input-providers.md)
- [<span data-ttu-id="103cd-218">Tracciamento delle mani</span><span class="sxs-lookup"><span data-stu-id="103cd-218">Hand Tracking</span></span>](../features/input/hand-tracking.md)
