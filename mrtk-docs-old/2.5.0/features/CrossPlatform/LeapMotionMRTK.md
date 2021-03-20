---
title: LeapMotionMRTK
description: Documentazione per la configurazione del movimento intercalare
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Leap Motion,
ms.openlocfilehash: 3c7170a97802483419cbee7b66d2a42bddda905a
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104692038"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="aa4c9-104">Come configurare il rilevamento manuale a salto (by Ultraleap) in MRTK</span><span class="sxs-lookup"><span data-stu-id="aa4c9-104">How to Configure Leap Motion (by Ultraleap) Hand Tracking in MRTK</span></span>

<span data-ttu-id="aa4c9-105">Per utilizzare questo provider di dati, è necessario un [controller di movimento Leap](https://www.ultraleap.com/product/leap-motion-controller/) .</span><span class="sxs-lookup"><span data-stu-id="aa4c9-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="aa4c9-106">Il movimento intercalare provider di dati Abilita il rilevamento a mano articolato per VR e può essere utile per la prototipazione rapida nell'editor.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="aa4c9-107">Il provider di dati può essere configurato in modo da usare il controller di movimento Leap montato su un auricolare o posizionato su una scrivania.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../Images/CrossPlatform/LeapMotion/LeapHandsGif3.gif)

<span data-ttu-id="aa4c9-109">Questo provider può essere usato nell'editor e nel dispositivo mentre si trova nella piattaforma autonoma.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="aa4c9-110">Può anche essere usato nell'editor mentre si trova nella piattaforma UWP, ma non in una compilazione UWP.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

|<span data-ttu-id="aa4c9-111">Versioni del modulo Leap Motion Unity supportate</span><span class="sxs-lookup"><span data-stu-id="aa4c9-111">Leap Motion Unity Modules Versions Supported</span></span>|
|---|
|<span data-ttu-id="aa4c9-112">4.5.0</span><span class="sxs-lookup"><span data-stu-id="aa4c9-112">4.5.0</span></span>|
|<span data-ttu-id="aa4c9-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="aa4c9-113">4.5.1</span></span>|

## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="aa4c9-114">Uso del rilevamento della mano Leap Motion (by Ultraleap) in MRTK</span><span class="sxs-lookup"><span data-stu-id="aa4c9-114">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="aa4c9-115">Importazione dei moduli MRTK e LEAP Unity Motion Unity</span><span class="sxs-lookup"><span data-stu-id="aa4c9-115">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="aa4c9-116">Installare [Leap Motion SDK 4.0.0](https://developer.leapmotion.com/releases/?category=orion) se non è già installato</span><span class="sxs-lookup"><span data-stu-id="aa4c9-116">Install the [Leap Motion SDK 4.0.0](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="aa4c9-117">Importare il pacchetto **Microsoft. MixedReality. Toolkit. Foundation** nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-117">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="aa4c9-118">Scaricare e importare la versione più recente dei [moduli Leap Motion Unity](https://developer.leapmotion.com/unity) nel progetto</span><span class="sxs-lookup"><span data-stu-id="aa4c9-118">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="aa4c9-119">Importa solo il pacchetto **principale** nei moduli Unity</span><span class="sxs-lookup"><span data-stu-id="aa4c9-119">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="aa4c9-120">Integrare i moduli Leap Motion Unity con MRTK</span><span class="sxs-lookup"><span data-stu-id="aa4c9-120">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="aa4c9-121">Dopo che i moduli Unity sono presenti nel progetto, passare a **mixed reality Toolkit**  >  **Leap Motion** Integration  >  **modules di Leap Motion Unity**</span><span class="sxs-lookup"><span data-stu-id="aa4c9-121">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="aa4c9-122">L'integrazione dei moduli Unity in MRTK aggiunge 10 definizioni di assembly al progetto e aggiunge riferimenti alla definizione dell'assembly **Microsoft. MixedReality. Toolkit. Providers. LeapMotion** .</span><span class="sxs-lookup"><span data-stu-id="aa4c9-122">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="aa4c9-123">Verificare che Visual Studio sia chiuso.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-123">Make sure Visual Studio is closed.</span></span>

     ![LeapMotionIntegration](../Images/CrossPlatform/LeapMotion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="aa4c9-125">Aggiunta del provider di dati di movimento Leap</span><span class="sxs-lookup"><span data-stu-id="aa4c9-125">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="aa4c9-126">Crea una nuova scena Unity</span><span class="sxs-lookup"><span data-stu-id="aa4c9-126">Create a new Unity scene</span></span>
    - <span data-ttu-id="aa4c9-127">Per aggiungere MRTK alla scena, passare a **mixed reality Toolkit**  >  **Aggiungi alla scena e configurare**</span><span class="sxs-lookup"><span data-stu-id="aa4c9-127">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="aa4c9-128">Selezionare l'oggetto gioco MixedRealityToolkit nella gerarchia e selezionare **copia e Personalizza** per clonare il profilo di realtà mista predefinito.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-128">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../Images/CrossPlatform/CloneProfile.png)

    - <span data-ttu-id="aa4c9-130">Selezionare il profilo di configurazione di **input**</span><span class="sxs-lookup"><span data-stu-id="aa4c9-130">Select the **Input** Configuration Profile</span></span>

    ![InputConfigurationProfile](../Images/CrossPlatform/InputConfigurationProfile.png)

    - <span data-ttu-id="aa4c9-132">Selezionare **clona** nel profilo di sistema di input per abilitare la modifica.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-132">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../Images/CrossPlatform/CloneInputSystemProfile.png)

    - <span data-ttu-id="aa4c9-134">Aprire la sezione **provider di dati di input** , selezionare **Aggiungi provider di dati** nella parte superiore, verrà aggiunto un nuovo provider di dati alla fine dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-134">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="aa4c9-135">Aprire il nuovo provider di dati e impostare il **tipo** su **Microsoft. MixedReality. Toolkit. LeapMotion. input > LeapMotionDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="aa4c9-135">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![LeapAddDataProvider](../Images/CrossPlatform/LeapMotion/LeapAddDataProvider.png)

    - <span data-ttu-id="aa4c9-137">Selezionare **clona** per modificare le impostazioni predefinite del movimento intercalare.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-137">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../Images/CrossPlatform/LeapMotion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="aa4c9-139">Il movimento intercalare provider di dati contiene la `LeapControllerOrientation` proprietà che rappresenta la posizione del controller di movimento LEAP.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-139">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="aa4c9-140">`LeapControllerOrientation.Headset` indica che il controller è montato su un auricolare.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-140">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="aa4c9-141">`LeapControllerOrientation.Desk` indica che il controller è posizionato sulla scrivania.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-141">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="aa4c9-142">Il valore predefinito è impostato su `LeapControllerOrientation.Headset` .</span><span class="sxs-lookup"><span data-stu-id="aa4c9-142">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="aa4c9-143">Ogni orientamento del controller contiene proprietà offset:</span><span class="sxs-lookup"><span data-stu-id="aa4c9-143">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="aa4c9-144">Le proprietà offset orientamento **auricolare** rispecchiano le proprietà offset nel componente LeapXRServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-144">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="aa4c9-145">In `LeapVRDeviceOffsetMode` sono disponibili tre opzioni: predefinita, offset Head manuale e trasformazione.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-145">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="aa4c9-146">Se la modalità offset è predefinita, un offset non verrà applicato al controller Leap Motion.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-146">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="aa4c9-147">La modalità di offset Head manuale consente la modifica di tre proprietà: `LeapVRDeviceOffsetY` , `LeapVRDeviceOffsetZ` e `LeapVRDeviceTiltX` .</span><span class="sxs-lookup"><span data-stu-id="aa4c9-147">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="aa4c9-148">I valori della proprietà offset asse vengono quindi applicati al posizionamento predefinito del controller.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-148">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="aa4c9-149">La modalità di offset della trasformazione contiene la `LeapVRDeviceOrigin` proprietà Transform che specifica una nuova origine per il controller di movimento LEAP.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-149">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="aa4c9-150">L'orientamento della **scrivania** contiene la `LeapControllerOffset` proprietà che definisce la posizione di ancoraggio delle lancette del banco intercalare.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-150">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="aa4c9-151">L'offset viene calcolato in relazione alla posizione principale della fotocamera e il valore predefinito è (0,-0,2, 0,35) per assicurarsi che le lancette vengano visualizzate in primo piano e in visualizzazione della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-151">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="aa4c9-152">Le proprietà offset nel profilo vengono applicate una volta all'avvio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-152">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="aa4c9-153">Per modificare i valori in fase di esecuzione, ottenere il provider di servizi di movimento Leap dal Gestione dispositivi di movimento intercalare:</span><span class="sxs-lookup"><span data-stu-id="aa4c9-153">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="aa4c9-154">`EnterPinchDistance` e `ExitPinchDistance` sono le soglie di distanza per il rilevamento del movimento del tocco di pizzico/aria.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-154">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="aa4c9-155">Il gesto del pizzico viene calcolato misurando la distanza tra la punta del dito dell'indice e il suggerimento.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-155">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="aa4c9-156">Per generare un evento su input inattivo, il valore predefinito `EnterPinchDistance` è impostato su 0,02.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-156">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="aa4c9-157">Per generare un evento di input in uscita (uscendo dal pizzico), la distanza predefinita tra il suggerimento per il dito dell'indice e il suggerimento del pollice è 0,05.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-157">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="aa4c9-158">`LeapControllerOrientation`: Auricolare (impostazione predefinita)</span><span class="sxs-lookup"><span data-stu-id="aa4c9-158">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="aa4c9-159">`LeapControllerOrientation`: Desk</span><span class="sxs-lookup"><span data-stu-id="aa4c9-159">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../Images/CrossPlatform/LeapMotion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../Images/CrossPlatform/LeapMotion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../Images/CrossPlatform/LeapMotion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../Images/CrossPlatform/LeapMotion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="aa4c9-164">Test del provider di dati di movimento intercalare</span><span class="sxs-lookup"><span data-stu-id="aa4c9-164">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="aa4c9-165">Dopo l'aggiunta del provider di dati di movimento Leap al profilo di sistema di input, premere Play, spostare la mano davanti a Leap Motion controller e visualizzare la rappresentazione congiunta della mano.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-165">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="aa4c9-166">Compilazione del progetto</span><span class="sxs-lookup"><span data-stu-id="aa4c9-166">Building your project</span></span>
    - <span data-ttu-id="aa4c9-167">Passa a **File > impostazioni di compilazione**</span><span class="sxs-lookup"><span data-stu-id="aa4c9-167">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="aa4c9-168">Solo le compilazioni autonome sono supportate se si usa l'provider di dati Leap Motion.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-168">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="aa4c9-169">Per istruzioni su come usare un auricolare di realtà mista di Windows per le compilazioni autonome, vedere [compilazione e distribuzione](../../updates-deployment/BuildAndDeploy.md#building-and-deploying-mrtk-to-a-windows-mixed-reality-headset).</span><span class="sxs-lookup"><span data-stu-id="aa4c9-169">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Build and Deploy](../../updates-deployment/BuildAndDeploy.md#building-and-deploying-mrtk-to-a-windows-mixed-reality-headset).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="aa4c9-170">Recupero delle giunzioni di mano</span><span class="sxs-lookup"><span data-stu-id="aa4c9-170">Getting the hand joints</span></span>

<span data-ttu-id="aa4c9-171">Il recupero di giunzioni tramite il provider di dati LEAP è identico a quello di una mano articolata MRTK.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-171">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="aa4c9-172">Per ulteriori informazioni, vedere la pagina relativa al [rilevamento manuale](../Input/HandTracking.md#polling-joint-pose-from-handjointutils).</span><span class="sxs-lookup"><span data-stu-id="aa4c9-172">For more information, see [Hand Tracking](../Input/HandTracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="aa4c9-173">Con MRTK in una scena Unity e il movimento Leap provider di dati aggiunto come input provider di dati nel profilo di sistema di input, creare un oggetto gioco vuoto e alleghi lo script di esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-173">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="aa4c9-174">Questo script è un semplice esempio di come recuperare la funzione del giunto di Palma in una mano di movimento.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-174">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="aa4c9-175">Una sfera segue la mano intercalare sinistra mentre un cubo segue la mano intercalare a destra.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-175">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

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

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="aa4c9-176">Suggerimento del flusso di lavoro dell'editor Unity</span><span class="sxs-lookup"><span data-stu-id="aa4c9-176">Unity editor workflow tip</span></span>

<span data-ttu-id="aa4c9-177">L'uso di Leap Motion provider di dati non richiede un auricolare VR.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-177">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="aa4c9-178">Le modifiche apportate a un'app MRTK possono essere testate nell'editor con la mano intercalare senza cuffie.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-178">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="aa4c9-179">Le lancette del movimento intercalare vengono visualizzate nell'editor, senza una cuffia VR collegata.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-179">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="aa4c9-180">Se `LeapControllerOrientation` è impostato su **auricolare**, è necessario che il controller di movimento intercalare venga mantenuto da una mano con la fotocamera rivolte verso l'alto.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-180">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="aa4c9-181">Se la fotocamera viene spostata usando chiavi WASD nell'editor e l' `LeapControllerOrientation` **auricolare** è, le mani non seguiranno la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-181">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="aa4c9-182">Le lancette seguiranno solo lo spostamento della fotocamera se una cuffia VR è collegata mentre `LeapControllerOrientation` è impostata l' **auricolare**.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-182">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="aa4c9-183">Se l'oggetto `LeapControllerOrientation` è impostato su **desk**, seguirà lo spostamento della fotocamera nell'editor.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-183">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="aa4c9-184">Rimozione del movimento intercalare dal progetto</span><span class="sxs-lookup"><span data-stu-id="aa4c9-184">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="aa4c9-185">Passare al **Toolkit di realtà mista** per i moduli di movimento a  >    >  **balzo separato**</span><span class="sxs-lookup"><span data-stu-id="aa4c9-185">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="aa4c9-186">Consentire l'aggiornamento di Unity come riferimento nel file **Microsoft. MixedReality. Toolkit. Providers. LeapMotion. asmdef** vengono modificati in questo passaggio</span><span class="sxs-lookup"><span data-stu-id="aa4c9-186">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="aa4c9-187">Chiudi Unity</span><span class="sxs-lookup"><span data-stu-id="aa4c9-187">Close Unity</span></span>
1. <span data-ttu-id="aa4c9-188">Chiudere Visual Studio, se è aperto</span><span class="sxs-lookup"><span data-stu-id="aa4c9-188">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="aa4c9-189">Aprire Esplora file e passare alla radice del progetto MRTK Unity</span><span class="sxs-lookup"><span data-stu-id="aa4c9-189">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="aa4c9-190">Elimina la directory **UnityProjectName/Library**</span><span class="sxs-lookup"><span data-stu-id="aa4c9-190">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="aa4c9-191">Elimina la directory **UnityProjectName/assets/plugins/LeapMotion**</span><span class="sxs-lookup"><span data-stu-id="aa4c9-191">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="aa4c9-192">Eliminare il file **UnityProjectName/assets/plugins/LeapMotion. meta**</span><span class="sxs-lookup"><span data-stu-id="aa4c9-192">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="aa4c9-193">Riaprire Unity</span><span class="sxs-lookup"><span data-stu-id="aa4c9-193">Reopen Unity</span></span>

<span data-ttu-id="aa4c9-194">In Unity 2018,4, è possibile notare che gli errori rimangono nella console dopo aver eliminato la libreria e le risorse di base del movimento intercalare.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-194">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="aa4c9-195">Se gli errori vengono registrati dopo la riapertura, riavviare Unity.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-195">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="aa4c9-196">Errori comuni</span><span class="sxs-lookup"><span data-stu-id="aa4c9-196">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="aa4c9-197">Leap Motion non è integrato con MRTK</span><span class="sxs-lookup"><span data-stu-id="aa4c9-197">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="aa4c9-198">Per verificare se i moduli Leap Motion Unity sono integrati con MRTK:</span><span class="sxs-lookup"><span data-stu-id="aa4c9-198">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="aa4c9-199">Passare a **mixed reality Toolkit > Utilities > Leap Motion > controllare lo stato di integrazione**</span><span class="sxs-lookup"><span data-stu-id="aa4c9-199">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="aa4c9-200">Verrà visualizzata una finestra popup con un messaggio che indica se i moduli Leap Motion Unity sono stati integrati con MRTK.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-200">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="aa4c9-201">Se il messaggio indica che gli asset non sono stati integrati:</span><span class="sxs-lookup"><span data-stu-id="aa4c9-201">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="aa4c9-202">Assicurarsi che i moduli Leap Motion Unity siano nel progetto</span><span class="sxs-lookup"><span data-stu-id="aa4c9-202">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="aa4c9-203">Verificare che la versione aggiunta sia supportata, vedere la tabella nella parte superiore della pagina per le versioni supportate.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-203">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="aa4c9-204">Provare **mixed reality Toolkit > Utilities > Leap motion > integrare i moduli Leap Motion Unity**</span><span class="sxs-lookup"><span data-stu-id="aa4c9-204">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="aa4c9-205">Copia HLAPI multiplayer assembly non riuscita</span><span class="sxs-lookup"><span data-stu-id="aa4c9-205">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="aa4c9-206">Durante l'importazione delle risorse di base di Leap Unity Motion, questo errore potrebbe essere registrato:</span><span class="sxs-lookup"><span data-stu-id="aa4c9-206">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```

Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="aa4c9-207">**Soluzione**</span><span class="sxs-lookup"><span data-stu-id="aa4c9-207">**Solution**</span></span>

- <span data-ttu-id="aa4c9-208">Una soluzione a breve termine prevede il riavvio di Unity.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-208">A short term solution is to restart Unity.</span></span> <span data-ttu-id="aa4c9-209">Per ulteriori informazioni, vedere il [problema 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) .</span><span class="sxs-lookup"><span data-stu-id="aa4c9-209">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="aa4c9-210">Scena di esempio Leap Motion</span><span class="sxs-lookup"><span data-stu-id="aa4c9-210">Leap Motion Example Scene</span></span>

<span data-ttu-id="aa4c9-211">La scena di esempio usa il profilo DefaultLeapMotionConfiguration e determina se il progetto Unity è stato configurato correttamente per l'uso del provider di dati di movimento LEAP.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-211">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="aa4c9-212">La scena di esempio è contenuta nel pacchetto **Microsoft. MixedReality. Toolkit. examples** in **MRTK/examples/Demos/HandTracking/** directory.</span><span class="sxs-lookup"><span data-stu-id="aa4c9-212">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="aa4c9-213">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="aa4c9-213">See also</span></span>

- [<span data-ttu-id="aa4c9-214">Provider di input</span><span class="sxs-lookup"><span data-stu-id="aa4c9-214">Input Providers</span></span>](../Input/InputProviders.md)
- [<span data-ttu-id="aa4c9-215">Rilevamento della mano</span><span class="sxs-lookup"><span data-stu-id="aa4c9-215">Hand Tracking</span></span>](../Input/HandTracking.md)
