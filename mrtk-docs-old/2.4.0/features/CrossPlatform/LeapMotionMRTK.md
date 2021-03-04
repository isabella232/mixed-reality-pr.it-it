---
title: LeapMotionMRTK
description: Documentazione per la configurazione del movimento intercalare
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Leap Motion,
ms.openlocfilehash: 7d774cebaa46b201ea380cec9047f602f45f4b3c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782282"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="618b1-104">Come configurare Leap Motion by Ultraleap Hand Tracking in MRTK</span><span class="sxs-lookup"><span data-stu-id="618b1-104">How to Configure Leap Motion by Ultraleap Hand Tracking in MRTK</span></span>

<span data-ttu-id="618b1-105">Per utilizzare questo provider di dati, è necessario un [controller di movimento Leap](https://www.ultraleap.com/product/leap-motion-controller/) .</span><span class="sxs-lookup"><span data-stu-id="618b1-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="618b1-106">Il movimento intercalare provider di dati Abilita il rilevamento a mano articolato per VR e può essere utile per la prototipazione rapida nell'editor.</span><span class="sxs-lookup"><span data-stu-id="618b1-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="618b1-107">Il provider di dati può essere configurato in modo da usare il controller di movimento Leap montato su un auricolare o posizionato su una scrivania.</span><span class="sxs-lookup"><span data-stu-id="618b1-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../Images/CrossPlatform/LeapMotion/LeapHandsGif3.gif)

## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="618b1-109">Uso di Leap Motion di Ultraleap Hand Tracking in MRTK</span><span class="sxs-lookup"><span data-stu-id="618b1-109">Using Leap Motion by Ultraleap hand tracking in MRTK</span></span>

1. <span data-ttu-id="618b1-110">Preparare il progetto MRTK per un movimento intercalare</span><span class="sxs-lookup"><span data-stu-id="618b1-110">Prepare MRTK project for Leap Motion</span></span>

    - <span data-ttu-id="618b1-111">**Questo passaggio si applica solo a Leap Motion Unity Core assets versione 4.4.0 e se l'origine di MRTK viene clonata dal repository git, non dai pacchetti Unity. Questo passaggio non è necessario se vengono usati gli asset principali della versione moduli di Leap Motion Unity 4.5.0. Se l'origine MRTK proverrà dai pacchetti Unity, iniziare dal passaggio successivo**</span><span class="sxs-lookup"><span data-stu-id="618b1-111">**This step only applies for the Leap Motion Unity Core Assets version 4.4.0 and if the source of MRTK is cloned from the git repo, NOT from the Unity packages. This step is not required if the Core Assets from Leap Motion Unity Modules version 4.5.0 are used. If the MRTK source is going to be from the Unity packages, start at the next step**</span></span>

    - <span data-ttu-id="618b1-112">Passare a **mixed reality Toolkit > Utilities > Leap motion > Configure CSC file for Leap Motion**.</span><span class="sxs-lookup"><span data-stu-id="618b1-112">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Configure CSC File for Leap Motion**.</span></span> <span data-ttu-id="618b1-113">L'aggiornamento del file CSC esclude gli avvisi obsoleti generati da Leap Motion Unity Core assets.</span><span class="sxs-lookup"><span data-stu-id="618b1-113">Updating the csc file filters out the obsolete warnings produced by the Leap Motion Unity Core Assets.</span></span>  <span data-ttu-id="618b1-114">Il repository MRTK contiene un file CSC che converte gli avvisi in errori, questa conversione interrompe il processo di configurazione MRTK Leap Motion.</span><span class="sxs-lookup"><span data-stu-id="618b1-114">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the Leap Motion MRTK configuration process.</span></span>  <span data-ttu-id="618b1-115">Il problema relativo agli avvisi obsoleti viene rilevato [qui](https://github.com/leapmotion/UnityModules/issues/1082).</span><span class="sxs-lookup"><span data-stu-id="618b1-115">The obsolete warnings issue is tracked [here](https://github.com/leapmotion/UnityModules/issues/1082).</span></span>

    ![LeapMotionUpdateCSCFile](../Images/CrossPlatform/LeapMotion/LeapMotionConfigureCSCFile2.png)

1. <span data-ttu-id="618b1-117">Importazione di MRTK e asset principali da Leap Motion Unity modules versione 4.5.0</span><span class="sxs-lookup"><span data-stu-id="618b1-117">Importing MRTK and the Core Assets from Leap Motion Unity Modules version 4.5.0</span></span>
    - <span data-ttu-id="618b1-118">Importare il pacchetto **Microsoft. MixedReality. Toolkit. Foundation** nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="618b1-118">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="618b1-119">Installare [Leap Motion SDK 4.0.0](https://developer.leapmotion.com/releases/?category=orion)</span><span class="sxs-lookup"><span data-stu-id="618b1-119">Install the [Leap Motion SDK 4.0.0](https://developer.leapmotion.com/releases/?category=orion)</span></span>
    - <span data-ttu-id="618b1-120">Scaricare e importare gli [asset principali da Leap Motion Unity Modules Version 4.5.0](https://github.com/leapmotion/UnityModules/releases/tag/UM-4.5.0)</span><span class="sxs-lookup"><span data-stu-id="618b1-120">Download and import the [Core Assets from Leap Motion Unity Modules version 4.5.0](https://github.com/leapmotion/UnityModules/releases/tag/UM-4.5.0)</span></span>
        - <span data-ttu-id="618b1-121">Sono supportate le risorse principali della versione [4.4.0](https://github.com/leapmotion/UnityModules/releases/tag/Release-CoreAsset-4.4.0) e gli asset principali della versione [4.5.0](https://github.com/leapmotion/UnityModules/releases/tag/UM-4.5.0) di Leap Motion Unity Modules, ma sono preferibili gli asset di base di Leap Motion Unity Modules Version 4.5.0.</span><span class="sxs-lookup"><span data-stu-id="618b1-121">Leap Motion Unity Core Assets version [4.4.0](https://github.com/leapmotion/UnityModules/releases/tag/Release-CoreAsset-4.4.0) and the Core Assets from Leap Motion Unity Modules version [4.5.0](https://github.com/leapmotion/UnityModules/releases/tag/UM-4.5.0) are supported, but Core Assets from Leap Motion Unity Modules version 4.5.0 are preferred.</span></span>
        - <span data-ttu-id="618b1-122">Se si usano asset di base per i moduli Leap Motion Unity versione 4.5.0, importare il pacchetto **principale** nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="618b1-122">If using Core Assets from Leap Motion Unity Modules version 4.5.0, import the **Core** package into the Unity project.</span></span>
    > [!NOTE]
    > <span data-ttu-id="618b1-123">Quando si importano gli asset principali, le directory di test vengono rimosse e al progetto vengono aggiunte 10 definizioni di assembly.</span><span class="sxs-lookup"><span data-stu-id="618b1-123">On import of the Core Assets, test directories are removed and 10 assembly definitions are added to the project.</span></span> <span data-ttu-id="618b1-124">Verificare che Visual Studio sia chiuso.</span><span class="sxs-lookup"><span data-stu-id="618b1-124">Make sure Visual Studio is closed.</span></span>
    - <span data-ttu-id="618b1-125">Se si usa Unity 2018.4. x</span><span class="sxs-lookup"><span data-stu-id="618b1-125">If using Unity 2018.4.x</span></span>
        - <span data-ttu-id="618b1-126">Dopo aver importato gli asset principali, passare a **assets/LeapMotion/**. dovrebbe essere presente un file LeapMotion. asmdef accanto alla directory principale.</span><span class="sxs-lookup"><span data-stu-id="618b1-126">After the Core Assets import, navigate to **Assets/LeapMotion/**, there should be a LeapMotion.asmdef file next to the Core directory.</span></span>  <span data-ttu-id="618b1-127">Se il file asmdef non è presente, passare agli [errori comuni del movimento Leap](#leap-motion-has-not-integrated-with-mrtk).</span><span class="sxs-lookup"><span data-stu-id="618b1-127">If the asmdef file is not present, go to the [Leap Motion Common Errors](#leap-motion-has-not-integrated-with-mrtk).</span></span> <span data-ttu-id="618b1-128">Se il file è presente, andare al passaggio successivo.</span><span class="sxs-lookup"><span data-stu-id="618b1-128">If the file is present, go to the next step.</span></span>

    - <span data-ttu-id="618b1-129">Se si usa Unity 2019.3. x, andare al passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="618b1-129">If using Unity 2019.3.x, go to the next step</span></span>

1. <span data-ttu-id="618b1-130">Aggiunta del provider di dati di movimento Leap</span><span class="sxs-lookup"><span data-stu-id="618b1-130">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="618b1-131">Crea una nuova scena Unity</span><span class="sxs-lookup"><span data-stu-id="618b1-131">Create a new Unity scene</span></span>
    - <span data-ttu-id="618b1-132">Per aggiungere MRTK alla scena, passare a **mixed reality Toolkit**  >  **Aggiungi alla scena e configurare**</span><span class="sxs-lookup"><span data-stu-id="618b1-132">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="618b1-133">Selezionare l'oggetto gioco MixedRealityToolkit nella gerarchia e selezionare **copia e Personalizza** per clonare il profilo di realtà mista predefinito.</span><span class="sxs-lookup"><span data-stu-id="618b1-133">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../Images/CrossPlatform/LeapMotion/LeapProfileClone.png)

    - <span data-ttu-id="618b1-135">Selezionare il profilo di configurazione di **input**</span><span class="sxs-lookup"><span data-stu-id="618b1-135">Select the **Input** Configuration Profile</span></span>

    ![InputConfigurationProfile](../Images/CrossPlatform/LeapMotion/LeapInputConfigurationProfile.png)

    - <span data-ttu-id="618b1-137">Selezionare **clona** nel profilo di sistema di input per abilitare la modifica.</span><span class="sxs-lookup"><span data-stu-id="618b1-137">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../Images/CrossPlatform/LeapMotion/LeapCloneInputSystemProfile.png)

    - <span data-ttu-id="618b1-139">Aprire la sezione **provider di dati di input** , selezionare **Aggiungi provider di dati** nella parte superiore, verrà aggiunto un nuovo provider di dati alla fine dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="618b1-139">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="618b1-140">Aprire il nuovo provider di dati e impostare il **tipo** su **Microsoft. MixedReality. Toolkit. LeapMotion. input > LeapMotionDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="618b1-140">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![LeapAddDataProvider](../Images/CrossPlatform/LeapMotion/LeapAddDataProvider.png)

    - <span data-ttu-id="618b1-142">Selezionare **clona** per modificare le impostazioni predefinite del movimento intercalare.</span><span class="sxs-lookup"><span data-stu-id="618b1-142">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../Images/CrossPlatform/LeapMotion/LeapDeviceManagerProfileBeforeClone.png)

    - <span data-ttu-id="618b1-144">Il movimento intercalare provider di dati contiene la `LeapControllerOrientation` proprietà che rappresenta la posizione del controller di movimento LEAP.</span><span class="sxs-lookup"><span data-stu-id="618b1-144">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="618b1-145">`LeapControllerOrientation.Headset` indica che il controller è montato su un auricolare.</span><span class="sxs-lookup"><span data-stu-id="618b1-145">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="618b1-146">`LeapControllerOrientation.Desk` indica che il controller è posizionato sulla scrivania.</span><span class="sxs-lookup"><span data-stu-id="618b1-146">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="618b1-147">Il valore predefinito è impostato su `LeapControllerOrientation.Headset` .</span><span class="sxs-lookup"><span data-stu-id="618b1-147">The default value is set to `LeapControllerOrientation.Headset`.</span></span>  <span data-ttu-id="618b1-148">Se l'orientamento è la scrivania, verrà visualizzata una proprietà aggiuntiva `LeapControllerOffset` .</span><span class="sxs-lookup"><span data-stu-id="618b1-148">If the orientation is the desk, an extra property `LeapControllerOffset` will appear.</span></span>  <span data-ttu-id="618b1-149">`LeapControllerOffset` è l'ancoraggio per la posizione delle lancette del banco intercalare.</span><span class="sxs-lookup"><span data-stu-id="618b1-149">`LeapControllerOffset` is the anchor for the position of the desk leap hands.</span></span>  <span data-ttu-id="618b1-150">L'offset viene calcolato in relazione alla posizione principale della fotocamera e il valore predefinito è (0,-0,2, 0,2) per assicurarsi che le lancette vengano visualizzate in primo piano e in visualizzazione della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="618b1-150">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.2) to make sure the hands appear in front and in view of the camera.</span></span>
    - <span data-ttu-id="618b1-151">`EnterPinchDistance` e `ExitPinchDistance` sono le soglie di distanza per il rilevamento del movimento del tocco di pizzico/aria.</span><span class="sxs-lookup"><span data-stu-id="618b1-151">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="618b1-152">Il gesto del pizzico viene calcolato misurando la distanza tra la punta del dito dell'indice e il suggerimento.</span><span class="sxs-lookup"><span data-stu-id="618b1-152">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="618b1-153">Per generare un evento su input inattivo, il valore predefinito `EnterPinchDistance` è impostato su 0,02.</span><span class="sxs-lookup"><span data-stu-id="618b1-153">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="618b1-154">Per generare un evento di input in uscita (uscendo dal pizzico), la distanza predefinita tra il suggerimento per il dito dell'indice e il suggerimento del pollice è 0,05.</span><span class="sxs-lookup"><span data-stu-id="618b1-154">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="618b1-155">`LeapControllerOrientation`: Auricolare (impostazione predefinita)</span><span class="sxs-lookup"><span data-stu-id="618b1-155">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="618b1-156">`LeapControllerOrientation`: Desk</span><span class="sxs-lookup"><span data-stu-id="618b1-156">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../Images/CrossPlatform/LeapMotion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../Images/CrossPlatform/LeapMotion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../Images/CrossPlatform/LeapMotion/LeapDeviceManagerHeadset.png) |     ![LeapDeskInspector](../Images/CrossPlatform/LeapMotion/LeapDeviceManagerDesk.png)

1. <span data-ttu-id="618b1-161">Test del provider di dati di movimento intercalare</span><span class="sxs-lookup"><span data-stu-id="618b1-161">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="618b1-162">Dopo l'aggiunta del provider di dati di movimento Leap al profilo di sistema di input, premere Play, spostare la mano davanti a Leap Motion controller e visualizzare la rappresentazione congiunta della mano.</span><span class="sxs-lookup"><span data-stu-id="618b1-162">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="618b1-163">Compilazione del progetto</span><span class="sxs-lookup"><span data-stu-id="618b1-163">Building your project</span></span>
    - <span data-ttu-id="618b1-164">Passa a **File > impostazioni di compilazione**</span><span class="sxs-lookup"><span data-stu-id="618b1-164">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="618b1-165">Solo le compilazioni autonome sono supportate se si usa l'provider di dati Leap Motion.</span><span class="sxs-lookup"><span data-stu-id="618b1-165">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="618b1-166">Per istruzioni su come usare un auricolare di realtà mista di Windows per le compilazioni autonome, vedere [compilazione e distribuzione](../../updates-deployment/BuildAndDeploy.md#building-and-deploying-mrtk-to-a-windows-mixed-reality-headset).</span><span class="sxs-lookup"><span data-stu-id="618b1-166">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Build and Deploy](../../updates-deployment/BuildAndDeploy.md#building-and-deploying-mrtk-to-a-windows-mixed-reality-headset).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="618b1-167">Recupero delle giunzioni di mano</span><span class="sxs-lookup"><span data-stu-id="618b1-167">Getting the hand joints</span></span>

<span data-ttu-id="618b1-168">Il recupero di giunzioni tramite il provider di dati LEAP è identico a quello di una mano articolata MRTK.</span><span class="sxs-lookup"><span data-stu-id="618b1-168">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="618b1-169">Per ulteriori informazioni, vedere la pagina relativa al [rilevamento manuale](../Input/HandTracking.md#polling-joint-pose-from-handjointutils).</span><span class="sxs-lookup"><span data-stu-id="618b1-169">For more information, see [Hand Tracking](../Input/HandTracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="618b1-170">Con MRTK in una scena Unity e il movimento Leap provider di dati aggiunto come input provider di dati nel profilo di sistema di input, creare un oggetto gioco vuoto e alleghi lo script di esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="618b1-170">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="618b1-171">Questo script è un semplice esempio di come recuperare la funzione del giunto di Palma in una mano di movimento.</span><span class="sxs-lookup"><span data-stu-id="618b1-171">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="618b1-172">Una sfera segue la mano intercalare sinistra mentre un cubo segue la mano intercalare a destra.</span><span class="sxs-lookup"><span data-stu-id="618b1-172">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

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

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="618b1-173">Suggerimento del flusso di lavoro dell'editor Unity</span><span class="sxs-lookup"><span data-stu-id="618b1-173">Unity editor workflow tip</span></span>

<span data-ttu-id="618b1-174">L'uso di Leap Motion provider di dati non richiede un auricolare VR.</span><span class="sxs-lookup"><span data-stu-id="618b1-174">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="618b1-175">Le modifiche apportate a un'app MRTK possono essere testate nell'editor con la mano intercalare senza cuffie.</span><span class="sxs-lookup"><span data-stu-id="618b1-175">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="618b1-176">Le lancette del movimento intercalare vengono visualizzate nell'editor, senza una cuffia VR collegata.</span><span class="sxs-lookup"><span data-stu-id="618b1-176">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="618b1-177">Se `LeapControllerOrientation` è impostato su **auricolare**, è necessario che il controller di movimento intercalare venga mantenuto da una mano con la fotocamera rivolte verso l'alto.</span><span class="sxs-lookup"><span data-stu-id="618b1-177">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="618b1-178">Se la fotocamera viene spostata usando chiavi WASD nell'editor e l' `LeapControllerOrientation` **auricolare** è, le mani non seguiranno la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="618b1-178">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="618b1-179">Le lancette seguiranno solo lo spostamento della fotocamera se una cuffia VR è collegata mentre `LeapControllerOrientation` è impostata l' **auricolare**.</span><span class="sxs-lookup"><span data-stu-id="618b1-179">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="618b1-180">Se l'oggetto `LeapControllerOrientation` è impostato su **desk**, seguirà lo spostamento della fotocamera nell'editor.</span><span class="sxs-lookup"><span data-stu-id="618b1-180">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="618b1-181">Rimozione del movimento intercalare dal progetto</span><span class="sxs-lookup"><span data-stu-id="618b1-181">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="618b1-182">Chiudi Unity</span><span class="sxs-lookup"><span data-stu-id="618b1-182">Close Unity</span></span>
1. <span data-ttu-id="618b1-183">Chiudere Visual Studio, se è aperto</span><span class="sxs-lookup"><span data-stu-id="618b1-183">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="618b1-184">Aprire Esplora file e passare alla radice del progetto MRTK Unity</span><span class="sxs-lookup"><span data-stu-id="618b1-184">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="618b1-185">Elimina la directory **UnityProjectName/Library**</span><span class="sxs-lookup"><span data-stu-id="618b1-185">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="618b1-186">Eliminare la directory **UnityProjectName/assets/LeapMotion**</span><span class="sxs-lookup"><span data-stu-id="618b1-186">Delete the **UnityProjectName/Assets/LeapMotion** directory</span></span>
    - <span data-ttu-id="618b1-187">Eliminare il file **UnityProjectName/assets/LeapMotion. meta**</span><span class="sxs-lookup"><span data-stu-id="618b1-187">Delete the **UnityProjectName/Assets/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="618b1-188">Riaprire Unity</span><span class="sxs-lookup"><span data-stu-id="618b1-188">Reopen Unity</span></span>

<span data-ttu-id="618b1-189">In Unity 2018,4, è possibile notare che gli errori rimangono nella console dopo aver eliminato la libreria e le risorse di base del movimento intercalare.</span><span class="sxs-lookup"><span data-stu-id="618b1-189">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="618b1-190">Se gli errori vengono registrati dopo la riapertura, riavviare Unity.</span><span class="sxs-lookup"><span data-stu-id="618b1-190">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="618b1-191">Errori comuni</span><span class="sxs-lookup"><span data-stu-id="618b1-191">Common Errors</span></span>

### <a name="leap-motion-obsolete-errors"></a><span data-ttu-id="618b1-192">Errori obsoleti del movimento di salto</span><span class="sxs-lookup"><span data-stu-id="618b1-192">Leap Motion Obsolete Errors</span></span>

<span data-ttu-id="618b1-193">Se l'origine di MRTK è dal repository e la versione di Unity è 2019.3. x, l'errore seguente potrebbe trovarsi nella console dopo l'importazione degli asset di base di Unity Motion.</span><span class="sxs-lookup"><span data-stu-id="618b1-193">If the source of MRTK is from the repo and the Unity version is 2019.3.x, the following error might be in the console after the import of the Leap Motion Unity Core Assets:</span></span>

```
Assets\LeapMotion\Core\Scripts\EditorTools\LeapPreferences.cs(84,6): error CS0618: 'PreferenceItem' is obsolete: '[PreferenceItem] is deprecated. Use [SettingsProvider] instead.
```

<span data-ttu-id="618b1-194">In Unity Version 2018.4. x è possibile che vengano registrati gli errori obsoleti seguenti:</span><span class="sxs-lookup"><span data-stu-id="618b1-194">In Unity version 2018.4.x, the following obsolete errors might be logged:</span></span>

```
Assets\LeapMotion\Core\Scripts\Attachments\AttachmentHands.cs(105,7): error CS0618: 'PrefabType' is obsolete: 'PrefabType no longer tells everything about Prefab instance.'
```

```
Assets\LeapMotion\Core\Scripts\Attachments\AttachmentHands.cs(105,31): error CS0618: 'PrefabUtility.GetPrefabType(Object)' is obsolete: 'Use GetPrefabAssetType and GetPrefabInstanceStatus to get the full picture about Prefab types.'
```

<span data-ttu-id="618b1-195">Questi errori vengono visualizzati se il **Toolkit di realtà mista > utilità > movimento Intercalare > configurare il file CSC per il movimento** intercalare non è stato selezionato prima dell'importazione degli asset di base di Unity Motion</span><span class="sxs-lookup"><span data-stu-id="618b1-195">These errors appear if **Mixed Reality Toolkit > Utilities > Leap Motion > Configure CSC File for Leap Motion** was not selected BEFORE the Leap Motion Unity Core Assets import.</span></span>

#### <a name="solution"></a><span data-ttu-id="618b1-196">Soluzione</span><span class="sxs-lookup"><span data-stu-id="618b1-196">Solution</span></span>

- <span data-ttu-id="618b1-197">Passare a **mixed reality Toolkit > Utilities > Leap motion > Configure CSC file for Leap Motion**, il file CSC verrà aggiornato in modo da filtrare gli avvisi di movimento Leap convertiti in errori nel repository MRTK.</span><span class="sxs-lookup"><span data-stu-id="618b1-197">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Configure CSC File for Leap Motion**, this will update the csc file to filter out Leap Motion warnings that are converted to errors in MRTK repo.</span></span>
- <span data-ttu-id="618b1-198">Chiudi Unity</span><span class="sxs-lookup"><span data-stu-id="618b1-198">Close Unity</span></span>
- <span data-ttu-id="618b1-199">Riaprire Unity</span><span class="sxs-lookup"><span data-stu-id="618b1-199">Reopen Unity</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="618b1-200">Leap Motion non è integrato con MRTK</span><span class="sxs-lookup"><span data-stu-id="618b1-200">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="618b1-201">Questo errore può verificarsi se la versione di Unity è 2018.4. x, l'origine MRTK è dai pacchetti Unity e dopo l'importazione degli asset di base di Unity di Leap Motion.</span><span class="sxs-lookup"><span data-stu-id="618b1-201">This error can occur if the Unity version is 2018.4.x, the MRTK source is from the Unity packages and after the import of the Leap Motion Unity Core Assets.</span></span>

<span data-ttu-id="618b1-202">Per verificare se MRTK riconosce la presenza degli asset di base di Unity Motion Unity, aprire la scena LeapMotionHandTrackingExample che si trova in MRTK/examples/Demos/HandTracking/e premere Play.</span><span class="sxs-lookup"><span data-stu-id="618b1-202">To test if MRTK recognizes the presence of the Leap Motion Unity Core Assets, open the LeapMotionHandTrackingExample scene located in MRTK/Examples/Demos/HandTracking/ and press play.</span></span>  <span data-ttu-id="618b1-203">Se le risorse di base di Unity Motion Unity vengono riconosciute, viene visualizzato un messaggio verde nel pannello informativo nella scena.</span><span class="sxs-lookup"><span data-stu-id="618b1-203">If the Leap Motion Unity Core Assets are recognized a green message on the informational panel in the scene will appear.</span></span>  <span data-ttu-id="618b1-204">Se le risorse di base di Unity Motion Unity non vengono riconosciute, verrà visualizzato un messaggio rosso.</span><span class="sxs-lookup"><span data-stu-id="618b1-204">If the Leap Motion Unity Core Assets are not recognized a red message will appear.</span></span>

<span data-ttu-id="618b1-205">Se gli asset di base di Unity Motion Unity si trovano nel progetto e viene visualizzato un messaggio rosso nel pannello informativo, è necessario configurare il progetto.</span><span class="sxs-lookup"><span data-stu-id="618b1-205">If the Leap Motion Unity Core Assets are in your project and you see a red message on the informational panel, the project needs to be configured.</span></span>

#### <a name="solution"></a><span data-ttu-id="618b1-206">Soluzione</span><span class="sxs-lookup"><span data-stu-id="618b1-206">Solution</span></span>

- <span data-ttu-id="618b1-207">Passare a **mixed reality Toolkit > Utilities > Leap motion > Configure Leap Motion**</span><span class="sxs-lookup"><span data-stu-id="618b1-207">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Configure Leap Motion**</span></span>
  - <span data-ttu-id="618b1-208">Verrà forzata l'integrazione del movimento Leap se il processo di configurazione non è stato avviato dopo l'importazione degli asset di base di Unity Motion Unity.</span><span class="sxs-lookup"><span data-stu-id="618b1-208">This will force Leap Motion integration if the configuration process was not started after the Leap Motion Unity Core Assets import.</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="618b1-209">Copia HLAPI multiplayer assembly non riuscita</span><span class="sxs-lookup"><span data-stu-id="618b1-209">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="618b1-210">Durante l'importazione delle risorse di base di Leap Unity Motion, questo errore potrebbe essere registrato:</span><span class="sxs-lookup"><span data-stu-id="618b1-210">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

#### <a name="solution"></a><span data-ttu-id="618b1-211">Soluzione</span><span class="sxs-lookup"><span data-stu-id="618b1-211">Solution</span></span>

- <span data-ttu-id="618b1-212">Una soluzione a breve termine prevede il riavvio di Unity.</span><span class="sxs-lookup"><span data-stu-id="618b1-212">A short term solution is to restart Unity.</span></span> <span data-ttu-id="618b1-213">Per ulteriori informazioni, vedere il [problema 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) .</span><span class="sxs-lookup"><span data-stu-id="618b1-213">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="618b1-214">Scena di esempio Leap Motion</span><span class="sxs-lookup"><span data-stu-id="618b1-214">Leap Motion Example Scene</span></span>

<span data-ttu-id="618b1-215">La scena di esempio usa il profilo DefaultLeapMotionConfiguration e determina se il progetto Unity è stato configurato correttamente per l'uso del provider di dati di movimento LEAP.</span><span class="sxs-lookup"><span data-stu-id="618b1-215">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="618b1-216">La scena di esempio è contenuta nel pacchetto **Microsoft. MixedReality. Toolkit. examples** in **MRTK/examples/Demos/HandTracking/** directory.</span><span class="sxs-lookup"><span data-stu-id="618b1-216">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="618b1-217">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="618b1-217">See also</span></span>

- [<span data-ttu-id="618b1-218">Provider di input</span><span class="sxs-lookup"><span data-stu-id="618b1-218">Input Providers</span></span>](../Input/InputProviders.md)
- [<span data-ttu-id="618b1-219">Rilevamento della mano</span><span class="sxs-lookup"><span data-stu-id="618b1-219">Hand Tracking</span></span>](../Input/HandTracking.md)
