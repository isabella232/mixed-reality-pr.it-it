---
title: LeapMotionMRTK
description: Documentazione da configurare per Leap Motion
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Leap Motion,
ms.openlocfilehash: ea9e257815116c364fe2f1e37ca3477ec56262cb
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852492"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="c4ca0-104">Come configurare il tracciamento delle mani Leap Motion (by Ultraleap) in MRTK</span><span class="sxs-lookup"><span data-stu-id="c4ca0-104">How to Configure Leap Motion (by Ultraleap) Hand Tracking in MRTK</span></span>

<span data-ttu-id="c4ca0-105">Per usare questo provider di dati, è necessario un controller del movimento [Leap.](https://www.ultraleap.com/product/leap-motion-controller/)</span><span class="sxs-lookup"><span data-stu-id="c4ca0-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="c4ca0-106">La funzionalità Leap Motion provider di dati il tracciamento delle mani articolato per la realtà virtuale e può essere utile per la creazione rapida di prototipi nell'editor.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="c4ca0-107">Il provider di dati può essere configurato per l'uso di Leap Motion Controller montato su un visore VR o posizionato su un visore della console.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="c4ca0-109">Questo provider può essere usato nell'editor e nel dispositivo nella piattaforma autonoma.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="c4ca0-110">Può essere usato anche nell'editor nella piattaforma UWP, ma NON in una build UWP.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

|<span data-ttu-id="c4ca0-111">Versioni supportate dei moduli Leap Motion Unity</span><span class="sxs-lookup"><span data-stu-id="c4ca0-111">Leap Motion Unity Modules Versions Supported</span></span>|
|---|
|<span data-ttu-id="c4ca0-112">4.5.0</span><span class="sxs-lookup"><span data-stu-id="c4ca0-112">4.5.0</span></span>|
|<span data-ttu-id="c4ca0-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="c4ca0-113">4.5.1</span></span>|

## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="c4ca0-114">Uso del tracciamento delle mani Leap Motion (by Ultraleap) in MRTK</span><span class="sxs-lookup"><span data-stu-id="c4ca0-114">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="c4ca0-115">Importazione di moduli MRTK e Leap Motion Unity</span><span class="sxs-lookup"><span data-stu-id="c4ca0-115">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="c4ca0-116">Installare [Leap Motion SDK 4.0.0](https://developer.leapmotion.com/releases/?category=orion) se non è già installato</span><span class="sxs-lookup"><span data-stu-id="c4ca0-116">Install the [Leap Motion SDK 4.0.0](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="c4ca0-117">Importare **il pacchetto Microsoft.MixedReality.Toolkit.Foundation** nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-117">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="c4ca0-118">Scaricare e importare la versione più recente [dei moduli Leap Motion Unity](https://developer.leapmotion.com/unity) nel progetto</span><span class="sxs-lookup"><span data-stu-id="c4ca0-118">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="c4ca0-119">Importare solo il **pacchetto Core** all'interno dei moduli Unity</span><span class="sxs-lookup"><span data-stu-id="c4ca0-119">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="c4ca0-120">Integrare i moduli Leap Motion Unity con MRTK</span><span class="sxs-lookup"><span data-stu-id="c4ca0-120">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="c4ca0-121">Quando i moduli Unity sono nel progetto, passare a **Mixed Reality Toolkit** Leap Motion Integrate Leap Motion Unity Modules (Mixed Reality Toolkit Leap  >  **Motion** Integrate Leap Motion Unity  >  **Modules)**</span><span class="sxs-lookup"><span data-stu-id="c4ca0-121">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="c4ca0-122">L'integrazione dei moduli Unity in MRTK aggiunge 10 definizioni di assembly al progetto e aggiunge riferimenti alla definizione dell'assembly **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.**</span><span class="sxs-lookup"><span data-stu-id="c4ca0-122">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="c4ca0-123">Verificare che Visual Studio sia chiuso.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-123">Make sure Visual Studio is closed.</span></span>

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="c4ca0-125">Aggiunta del movimento leap provider di dati</span><span class="sxs-lookup"><span data-stu-id="c4ca0-125">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="c4ca0-126">Creare una nuova scena di Unity</span><span class="sxs-lookup"><span data-stu-id="c4ca0-126">Create a new Unity scene</span></span>
    - <span data-ttu-id="c4ca0-127">Aggiungere MRTK alla scena passando a **Mixed Reality Toolkit** Aggiungi alla scena e  >  **configura**</span><span class="sxs-lookup"><span data-stu-id="c4ca0-127">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="c4ca0-128">Selezionare l'oggetto gioco MixedRealityToolkit nella gerarchia e selezionare Copia e **personalizza** per clonare il profilo di realtà mista predefinito.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-128">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="c4ca0-130">Selezionare il **profilo di configurazione** di input</span><span class="sxs-lookup"><span data-stu-id="c4ca0-130">Select the **Input** Configuration Profile</span></span>

    ![Profilo di configurazione di input 1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="c4ca0-132">Selezionare **Clona** nel profilo di sistema di input per abilitare la modifica.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-132">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="c4ca0-134">Aprire la **sezione Provider di dati** di input, selezionare **Aggiungi** provider di dati nella parte superiore, verrà aggiunto un nuovo provider di dati alla fine dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-134">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="c4ca0-135">Aprire il nuovo provider di dati e impostare **Type** su **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="c4ca0-135">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Leap Add provider di dati](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="c4ca0-137">Selezionare **Clona** per modificare le impostazioni predefinite di Leap Motion.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-137">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="c4ca0-139">L'provider di dati Leap Motion contiene `LeapControllerOrientation` la proprietà che rappresenta la posizione del controller di movimento Leap.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-139">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="c4ca0-140">`LeapControllerOrientation.Headset` indica che il controller è montato su un visore.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-140">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="c4ca0-141">`LeapControllerOrientation.Desk` indica che il controller è posizionato piano sulla scrivania.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-141">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="c4ca0-142">Il valore predefinito è impostato su `LeapControllerOrientation.Headset` .</span><span class="sxs-lookup"><span data-stu-id="c4ca0-142">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="c4ca0-143">Ogni orientamento del controller contiene le proprietà di offset:</span><span class="sxs-lookup"><span data-stu-id="c4ca0-143">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="c4ca0-144">Le **proprietà di** offset dell'orientamento del visore VR rispecchiano le proprietà di offset nel componente LeapXRServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-144">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="c4ca0-145">Ha `LeapVRDeviceOffsetMode` tre opzioni: Default, Manual Head Offset e Transform.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-145">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="c4ca0-146">Se la modalità di offset è Default, non verrà applicato un offset al controller del movimento Leap.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-146">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="c4ca0-147">La modalità Manual Head Offset (Offset head manuale) consente la modifica di tre proprietà: `LeapVRDeviceOffsetY` `LeapVRDeviceOffsetZ` e `LeapVRDeviceTiltX` .</span><span class="sxs-lookup"><span data-stu-id="c4ca0-147">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="c4ca0-148">I valori della proprietà offset dell'asse vengono quindi applicati alla posizione predefinita del controller.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-148">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="c4ca0-149">La modalità Offset trasformazione contiene la `LeapVRDeviceOrigin` proprietà Transform che specifica una nuova origine per leap motion controller.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-149">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="c4ca0-150">**L'orientamento desk** contiene la `LeapControllerOffset` proprietà che definisce la posizione di ancoraggio delle mani di salto della cassa.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-150">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="c4ca0-151">L'offset viene calcolato in relazione alla posizione principale della fotocamera e il valore predefinito è (0,-0,2, 0,35) per assicurarsi che le mani vengano visualizzate davanti e in vista della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-151">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="c4ca0-152">Le proprietà di offset nel profilo vengono applicate una sola volta all'avvio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-152">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="c4ca0-153">Per modificare i valori in fase di esecuzione, ottenere Leap Motion Service Provider da Leap Motion Device Manager:</span><span class="sxs-lookup"><span data-stu-id="c4ca0-153">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="c4ca0-154">`EnterPinchDistance` e `ExitPinchDistance` sono le soglie di distanza per il rilevamento del movimento di avvicinamento delle dita/tocco dell'aria.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-154">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="c4ca0-155">Il movimento di avvicinamento delle dita viene calcolato misurando la distanza tra la punta del dito indice e la punta del pollice.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-155">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="c4ca0-156">Per generare un evento on input down, il valore `EnterPinchDistance` predefinito è 0,02.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-156">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="c4ca0-157">Per generare un evento on input up (uscita dalla avvicinamento delle dita), la distanza predefinita tra la punta del dito indice e la punta del pollice è 0,05.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-157">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="c4ca0-158">`LeapControllerOrientation`: Visore VR (predefinito)</span><span class="sxs-lookup"><span data-stu-id="c4ca0-158">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="c4ca0-159">`LeapControllerOrientation`: Desk</span><span class="sxs-lookup"><span data-stu-id="c4ca0-159">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="c4ca0-164">Test del movimento leap provider di dati</span><span class="sxs-lookup"><span data-stu-id="c4ca0-164">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="c4ca0-165">Dopo aver aggiunto leap motion provider di dati al profilo del sistema di input, premere play, spostare la mano davanti a Leap Motion Controller e si dovrebbe vedere la rappresentazione congiunta della mano.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-165">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="c4ca0-166">Compilazione del progetto</span><span class="sxs-lookup"><span data-stu-id="c4ca0-166">Building your project</span></span>
    - <span data-ttu-id="c4ca0-167">Passare a **Impostazioni di > file**</span><span class="sxs-lookup"><span data-stu-id="c4ca0-167">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="c4ca0-168">Solo le compilazioni autonome sono supportate se si usa leap motion provider di dati.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-168">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="c4ca0-169">Per istruzioni su come usare un visore Windows Mixed Reality per le build autonome, vedere Compilazione e distribuzione [di MRTK (Standalone).](wmr-mrtk.md#building-and-deploying-mrtk-standalone)</span><span class="sxs-lookup"><span data-stu-id="c4ca0-169">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="c4ca0-170">Ottenere le giunzioni della mano</span><span class="sxs-lookup"><span data-stu-id="c4ca0-170">Getting the hand joints</span></span>

<span data-ttu-id="c4ca0-171">Ottenere le giunzioni usando il provider di dati leap è identico al recupero delle giunzioni della mano per una mano articolata MRTK.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-171">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="c4ca0-172">Per altre informazioni, vedere [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span><span class="sxs-lookup"><span data-stu-id="c4ca0-172">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="c4ca0-173">Con MRTK in una scena unity e leap motion provider di dati aggiunto come provider di dati di input nel profilo del sistema di input, creare un oggetto gioco vuoto e collegare lo script di esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-173">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="c4ca0-174">Questo script è un semplice esempio di come recuperare la posizione della giunzione del palmo in un Leap Motion Hand.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-174">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="c4ca0-175">Una sfera segue la mano intercalare sinistra mentre un cubo segue la mano di salto a destra.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-175">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

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

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="c4ca0-176">Suggerimento per il flusso di lavoro dell'editor unity</span><span class="sxs-lookup"><span data-stu-id="c4ca0-176">Unity editor workflow tip</span></span>

<span data-ttu-id="c4ca0-177">L'uso di Leap Motion provider di dati non richiede un visore VR.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-177">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="c4ca0-178">Le modifiche a un'app MRTK possono essere testate nell'editor con le mani Leap senza visore.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-178">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="c4ca0-179">Leap Motion Hands verrà visualizzato nell'editor, senza un visore VR collegato.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-179">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="c4ca0-180">Se `LeapControllerOrientation` l'opzione è impostata su **Headset,** il controller Leap Motion dovrà essere tenuto in mano da una mano con la fotocamera rivolta in avanti.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-180">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="c4ca0-181">Se la fotocamera viene spostata usando chiavi WASD nell'editor e l'oggetto è Headset, le mani `LeapControllerOrientation` non seguiranno la fotocamera. </span><span class="sxs-lookup"><span data-stu-id="c4ca0-181">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="c4ca0-182">Le mani seguiranno lo spostamento della fotocamera solo se un visore VR è collegato mentre `LeapControllerOrientation` l'opzione è impostata **su Headset**.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-182">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="c4ca0-183">Le mani leap seguiranno lo spostamento della fotocamera nell'editor se `LeapControllerOrientation` è impostato su **Desk**.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-183">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="c4ca0-184">Rimozione di Leap Motion dal progetto</span><span class="sxs-lookup"><span data-stu-id="c4ca0-184">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="c4ca0-185">Passare ai moduli **Leap**  >  **Motion Separate** leap  >  **motion unity di** Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="c4ca0-185">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="c4ca0-186">Consentire l'aggiornamento di Unity quando i riferimenti nel file **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** vengono modificati in questo passaggio</span><span class="sxs-lookup"><span data-stu-id="c4ca0-186">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="c4ca0-187">Chiudere Unity</span><span class="sxs-lookup"><span data-stu-id="c4ca0-187">Close Unity</span></span>
1. <span data-ttu-id="c4ca0-188">Chiudere Visual Studio, se è aperto</span><span class="sxs-lookup"><span data-stu-id="c4ca0-188">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="c4ca0-189">Aprire Esplora file e passare alla radice del progetto Unity MRTK</span><span class="sxs-lookup"><span data-stu-id="c4ca0-189">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="c4ca0-190">Eliminare la directory **UnityProjectName/Library**</span><span class="sxs-lookup"><span data-stu-id="c4ca0-190">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="c4ca0-191">Eliminare la directory **UnityProjectName/Assets/Plugins/LeapMotion**</span><span class="sxs-lookup"><span data-stu-id="c4ca0-191">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="c4ca0-192">Eliminare il file **UnityProjectName/Assets/Plugins/LeapMotion.meta**</span><span class="sxs-lookup"><span data-stu-id="c4ca0-192">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="c4ca0-193">Riaprire Unity</span><span class="sxs-lookup"><span data-stu-id="c4ca0-193">Reopen Unity</span></span>

<span data-ttu-id="c4ca0-194">In Unity 2018.4 è possibile notare che gli errori rimangono ancora nella console dopo l'eliminazione degli asset Library e Leap Motion Core.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-194">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="c4ca0-195">Se gli errori vengono registrati dopo la riapertura, riavviare di nuovo Unity.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-195">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="c4ca0-196">Errori comuni</span><span class="sxs-lookup"><span data-stu-id="c4ca0-196">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="c4ca0-197">Leap Motion non è integrato con MRTK</span><span class="sxs-lookup"><span data-stu-id="c4ca0-197">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="c4ca0-198">Per verificare se i moduli Leap Motion Unity sono integrati con MRTK:</span><span class="sxs-lookup"><span data-stu-id="c4ca0-198">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="c4ca0-199">Passare a **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status (Controlla stato integrazione)**</span><span class="sxs-lookup"><span data-stu-id="c4ca0-199">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="c4ca0-200">Verrà visualizzata una finestra popup con un messaggio che indica se i moduli Leap Motion Unity sono integrati o meno con MRTK.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-200">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="c4ca0-201">Se il messaggio indica che gli asset non sono stati integrati:</span><span class="sxs-lookup"><span data-stu-id="c4ca0-201">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="c4ca0-202">Assicurarsi che i moduli Leap Motion Unity siano presenti nel progetto</span><span class="sxs-lookup"><span data-stu-id="c4ca0-202">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="c4ca0-203">Assicurarsi che la versione aggiunta sia supportata. Vedere la tabella nella parte superiore della pagina per le versioni supportate.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-203">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="c4ca0-204">Provare **Mixed Reality Toolkit > Utilities > Leap Motion > integrare i moduli Leap Motion Unity**</span><span class="sxs-lookup"><span data-stu-id="c4ca0-204">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="c4ca0-205">Copia dell'assembly multiplayer HLAPI non riuscita</span><span class="sxs-lookup"><span data-stu-id="c4ca0-205">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="c4ca0-206">Durante l'importazione degli asset core di Leap Motion Unity, è possibile che venga registrato questo errore:</span><span class="sxs-lookup"><span data-stu-id="c4ca0-206">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="c4ca0-207">**Soluzione**</span><span class="sxs-lookup"><span data-stu-id="c4ca0-207">**Solution**</span></span>

- <span data-ttu-id="c4ca0-208">Una soluzione a breve termine consiste nel riavviare Unity.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-208">A short term solution is to restart Unity.</span></span> <span data-ttu-id="c4ca0-209">Per altre informazioni, vedere Problema [7761.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761)</span><span class="sxs-lookup"><span data-stu-id="c4ca0-209">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="c4ca0-210">Scena di esempio di movimento intercalare</span><span class="sxs-lookup"><span data-stu-id="c4ca0-210">Leap Motion Example Scene</span></span>

<span data-ttu-id="c4ca0-211">La scena di esempio usa il profilo DefaultLeapMotionConfiguration e determina se il progetto Unity è stato configurato correttamente per l'uso del provider di dati.</span><span class="sxs-lookup"><span data-stu-id="c4ca0-211">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="c4ca0-212">La scena di esempio è contenuta nel pacchetto **Microsoft.MixedReality.Toolkit.Examples** nella directory **MRTK/Examples/Demos/HandTracking/.**</span><span class="sxs-lookup"><span data-stu-id="c4ca0-212">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="c4ca0-213">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="c4ca0-213">See also</span></span>

<span data-ttu-id="c4ca0-214">-[Provider di input](../features/input/input-providers.md) 
- [Tracciamento manuale](../features/input/hand-tracking.md)</span><span class="sxs-lookup"><span data-stu-id="c4ca0-214">-[Input Providers](../features/input/input-providers.md)
-[Hand Tracking](../features/input/hand-tracking.md)</span></span>
