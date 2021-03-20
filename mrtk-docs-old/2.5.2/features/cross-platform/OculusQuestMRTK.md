---
title: OculusQuestMRTK
description: Documentazione per la configurazione di Oculus quest in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Oculus quest,
ms.openlocfilehash: ad8d65d5331fc30b068c31a403bfbc4a88ab0964
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687011"
---
# <a name="how-to-configure-oculus-quest-in-mrtk-using-the-xrsdk-pipeline"></a><span data-ttu-id="fdad2-104">Come configurare Oculus quest in MRTK usando la pipeline XRSDK</span><span class="sxs-lookup"><span data-stu-id="fdad2-104">How to configure Oculus Quest in MRTK using the XRSDK pipeline</span></span>

<span data-ttu-id="fdad2-105">È necessaria una [missione Oculus](https://www.oculus.com/quest/) .</span><span class="sxs-lookup"><span data-stu-id="fdad2-105">A [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="fdad2-106">Il supporto di MRTK per l'Oculus missione viene fornito tramite due origini diverse, la pipeline XR di Unity e il pacchetto Oculus Integration Unity.</span><span class="sxs-lookup"><span data-stu-id="fdad2-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="fdad2-107">Il **provider di dati Oculus XRSDK** consente l'uso di entrambe le origini e deve essere usato per usare MRTK in Oculus quest.</span><span class="sxs-lookup"><span data-stu-id="fdad2-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to use MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="fdad2-108">La [pipeline di Unity XR](https://docs.unity3d.com/Manual/XR.html) consente di usare i controller Oculus touch e il rilevamento Head con l'Oculus quest.</span><span class="sxs-lookup"><span data-stu-id="fdad2-108">The [Unity's XR Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="fdad2-109">Questa pipeline è lo standard per lo sviluppo di applicazioni XR in Unity 2019,3 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="fdad2-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="fdad2-110">Per usare questa pipeline, assicurarsi di usare **unity 2019,3 o versione successiva**.</span><span class="sxs-lookup"><span data-stu-id="fdad2-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span>

<span data-ttu-id="fdad2-111">Il [pacchetto Oculus Integration Unity](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) consente di usare il **rilevamento manuale** con l'Oculus quest.</span><span class="sxs-lookup"><span data-stu-id="fdad2-111">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span>
<span data-ttu-id="fdad2-112">Questo provider di dati **non usa la** pipeline **XR** di Unity o la **pipeline di XR legacy**, ma poiché i controller e headtracking vengono gestiti dalla pipeline XR di Unity, è necessario seguire la procedura di **configurazione del progetto per la ricerca Oculus** per assicurarsi che si stia usando la **pipeline XR** e non la **pipeline XR legacy**.</span><span class="sxs-lookup"><span data-stu-id="fdad2-112">This data provider does **NOT** use Unity's **XR Pipeline** or **Legacy XR Pipeline**, but because controllers and headtracking are handled by the Unity's XR Pipeline, the steps in **Setting up project for the Oculus Quest** must be followed to ensure that you are using the **XR Pipeline** and not the to-be-deprecated **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="fdad2-113">Impostazione del progetto per la missione Oculus</span><span class="sxs-lookup"><span data-stu-id="fdad2-113">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="fdad2-114">Per assicurarsi che il progetto sia pronto per la distribuzione in Oculus quest, seguire [questa procedura](https://developer.oculus.com/documentation/unity/book-unity-gsg/) .</span><span class="sxs-lookup"><span data-stu-id="fdad2-114">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="fdad2-115">Verificare che nel dispositivo sia abilitata la [modalità sviluppatore](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) .</span><span class="sxs-lookup"><span data-stu-id="fdad2-115">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="fdad2-116">L'installazione dei driver Oculus ADB è facoltativa.</span><span class="sxs-lookup"><span data-stu-id="fdad2-116">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-pipeline-for-oculus-quest"></a><span data-ttu-id="fdad2-117">Impostazione della pipeline XR per Oculus quest</span><span class="sxs-lookup"><span data-stu-id="fdad2-117">Setting up the XR Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="fdad2-118">Verificare che il **plug-in Oculus XR** sia installato in **Window--> Package Manager**</span><span class="sxs-lookup"><span data-stu-id="fdad2-118">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![OculusXRPluginPackageView](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="fdad2-120">Verificare che il provider del plug-in Oculus sia incluso nel progetto **modificando > impostazioni progetto--> gestione plug-in XR--> provider plug-in**</span><span class="sxs-lookup"><span data-stu-id="fdad2-120">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![OculusPluginProviderView](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="fdad2-122">Configurazione del pacchetto Oculus Integration Unity per abilitare handtracking</span><span class="sxs-lookup"><span data-stu-id="fdad2-122">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="fdad2-123">Scaricare e importare l' [integrazione di Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) da Unity Asset Store.</span><span class="sxs-lookup"><span data-stu-id="fdad2-123">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="fdad2-124">La versione più recente testata per funzionare è 20.0.0.</span><span class="sxs-lookup"><span data-stu-id="fdad2-124">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="fdad2-125">Le versioni precedenti sono reperibili in questo [Archivio](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span><span class="sxs-lookup"><span data-stu-id="fdad2-125">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span></span>

1. <span data-ttu-id="fdad2-126">Passare a Mixed Reality Toolkit > Utilities > Oculus > integrare i moduli di Oculus Integration Unity.</span><span class="sxs-lookup"><span data-stu-id="fdad2-126">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="fdad2-127">Questa operazione aggiornerà il asmdefs con le definizioni e i riferimenti necessari per il funzionamento del codice di Oculus missione pertinente.</span><span class="sxs-lookup"><span data-stu-id="fdad2-127">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="fdad2-128">Aggiornerà anche il file CSC per filtrare gli avvisi obsoleti generati dalle risorse di integrazione Oculus.</span><span class="sxs-lookup"><span data-stu-id="fdad2-128">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="fdad2-129">Il repository MRTK contiene un file CSC che converte gli avvisi in errori, questa conversione interrompe il processo di configurazione del MRTK-Quest.</span><span class="sxs-lookup"><span data-stu-id="fdad2-129">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![OculusIntegrationAsmdefView](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="fdad2-131">Nella cartella Oculus importata (dovrebbe trovarsi in asset/Oculus), è presente un oggetto con script denominato OculusProjectConfig.</span><span class="sxs-lookup"><span data-stu-id="fdad2-131">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="fdad2-132">In tale file di configurazione è necessario impostare HandTrackingSupport su "Controllers and hands".</span><span class="sxs-lookup"><span data-stu-id="fdad2-132">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![OculusIntegrationControllerAndHandsView](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="fdad2-134">Impostazione della scena</span><span class="sxs-lookup"><span data-stu-id="fdad2-134">Setting up the scene</span></span>

1. <span data-ttu-id="fdad2-135">Creare una nuova scena Unity o aprire una scena preesistente, ad esempio HandInteractionExamples</span><span class="sxs-lookup"><span data-stu-id="fdad2-135">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples</span></span>
1. <span data-ttu-id="fdad2-136">Per aggiungere MRTK alla scena, passare a **mixed reality Toolkit**  >  **Aggiungi alla scena e configurare**</span><span class="sxs-lookup"><span data-stu-id="fdad2-136">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>

## <a name="using-the-oculus-xrsdk-data-provider"></a><span data-ttu-id="fdad2-137">Uso di Oculus XRSDK provider di dati</span><span class="sxs-lookup"><span data-stu-id="fdad2-137">Using the Oculus XRSDK Data Provider</span></span>

1. <span data-ttu-id="fdad2-138">Configurare il profilo per l'uso di **Oculus XRSDK provider di dati**</span><span class="sxs-lookup"><span data-stu-id="fdad2-138">Configure your profile to use the **Oculus XRSDK Data Provider**</span></span>
    - <span data-ttu-id="fdad2-139">Se non si intende modificare i profili di configurazione</span><span class="sxs-lookup"><span data-stu-id="fdad2-139">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="fdad2-140">Modificare il profilo in DefaultXRSDKInputSystemProfile e passare a [compilare e distribuire il progetto in Oculus quest](OculusQuestMRTK.md#build-and-deploy-your-project-to-oculus-quest)</span><span class="sxs-lookup"><span data-stu-id="fdad2-140">Change your profile to DefaultXRSDKInputSystemProfile and go to [Build and deploy your project to Oculus Quest](OculusQuestMRTK.md#build-and-deploy-your-project-to-oculus-quest)</span></span>

    - <span data-ttu-id="fdad2-141">In caso contrario, seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="fdad2-141">Otherwise follow the following:</span></span>
        - <span data-ttu-id="fdad2-142">Selezionare l'oggetto gioco MixedRealityToolkit nella gerarchia e selezionare **copia e Personalizza** per clonare il profilo di realtà mista predefinito.</span><span class="sxs-lookup"><span data-stu-id="fdad2-142">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![CloneProfileView](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="fdad2-144">Selezionare il profilo di configurazione di **input**</span><span class="sxs-lookup"><span data-stu-id="fdad2-144">Select the **Input** Configuration Profile</span></span>

        ![InputConfigurationProfileView](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="fdad2-146">Selezionare **clona** nel profilo di sistema di input per abilitare la modifica.</span><span class="sxs-lookup"><span data-stu-id="fdad2-146">Select **Clone** in the input system profile to enable modification.</span></span>

        ![CloneInputSystemProfileView](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="fdad2-148">Aprire la sezione **provider di dati di input** , selezionare **Aggiungi provider di dati** nella parte superiore e il nuovo provider di dati verrà aggiunto alla fine dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="fdad2-148">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="fdad2-149">Aprire il nuovo provider di dati e impostare il **tipo** su **Microsoft. MixedReality. Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="fdad2-149">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**</span></span>

        ![OculusAddXRSDKDataProviderView](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)

    - <span data-ttu-id="fdad2-151">È possibile verificare che i controller Oculus siano rilevati da</span><span class="sxs-lookup"><span data-stu-id="fdad2-151">You can verify that the Oculus Controllers are detected by</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="fdad2-152">Compila e Distribuisci il progetto in Oculus quest</span><span class="sxs-lookup"><span data-stu-id="fdad2-152">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="fdad2-153">Collegare l'Oculus quest tramite un cavo USB 3,0-> USB</span><span class="sxs-lookup"><span data-stu-id="fdad2-153">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="fdad2-154">Passa a **File > impostazioni di compilazione**</span><span class="sxs-lookup"><span data-stu-id="fdad2-154">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="fdad2-155">Modificare la distribuzione in **Android**</span><span class="sxs-lookup"><span data-stu-id="fdad2-155">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="fdad2-156">Verificare che l'Oculus cerca sia selezionata come dispositivo di esecuzione applicabile</span><span class="sxs-lookup"><span data-stu-id="fdad2-156">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![OculusRunDeviceView](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="fdad2-158">Selezionare Compila ed Esegui</span><span class="sxs-lookup"><span data-stu-id="fdad2-158">Select Build and Run</span></span>
    - <span data-ttu-id="fdad2-159">Quando si seleziona *Compila ed Esegui* la prima volta, si verificherà probabilmente il set di errori di compilazione seguente.</span><span class="sxs-lookup"><span data-stu-id="fdad2-159">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="fdad2-160">Si dovrebbe essere in grado di distribuire correttamente quando si seleziona *Compila ed Esegui* di nuovo.</span><span class="sxs-lookup"><span data-stu-id="fdad2-160">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![OculusExpectedBuildErrorsView](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="fdad2-162">Accettare la richiesta di abilitazione del _debug USB_ dall'interno della ricerca</span><span class="sxs-lookup"><span data-stu-id="fdad2-162">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="fdad2-163">Guarda la tua scena all'interno di Oculus quest</span><span class="sxs-lookup"><span data-stu-id="fdad2-163">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="fdad2-164">Rimozione dell'integrazione di Oculus dal progetto</span><span class="sxs-lookup"><span data-stu-id="fdad2-164">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="fdad2-165">Passare al Toolkit di realtà mista > Oculus > moduli di integrazione di Oculus di OculusSeparationAsmdefView separati. ![](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="fdad2-165">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![OculusSeparationAsmdefView](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="fdad2-166">Consentire l'aggiornamento di Unity come riferimenti in Microsoft. MixedReality. Toolkit. Providers. Oculus. asmdef e altri file vengono modificati in questo passaggio</span><span class="sxs-lookup"><span data-stu-id="fdad2-166">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="fdad2-167">Chiudi Unity</span><span class="sxs-lookup"><span data-stu-id="fdad2-167">Close Unity</span></span>
1. <span data-ttu-id="fdad2-168">Chiudere Visual Studio, se è aperto</span><span class="sxs-lookup"><span data-stu-id="fdad2-168">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="fdad2-169">Aprire Esplora file e passare alla radice del progetto MRTK Unity</span><span class="sxs-lookup"><span data-stu-id="fdad2-169">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="fdad2-170">Elimina la directory UnityProjectName/Library</span><span class="sxs-lookup"><span data-stu-id="fdad2-170">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="fdad2-171">Eliminare la directory UnityProjectName/assets/Oculus</span><span class="sxs-lookup"><span data-stu-id="fdad2-171">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="fdad2-172">Eliminare il file UnityProjectName/assets/Oculus. meta</span><span class="sxs-lookup"><span data-stu-id="fdad2-172">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="fdad2-173">Riaprire Unity</span><span class="sxs-lookup"><span data-stu-id="fdad2-173">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="fdad2-174">Errori comuni</span><span class="sxs-lookup"><span data-stu-id="fdad2-174">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="fdad2-175">Ricerca non riconosciuta da Unity</span><span class="sxs-lookup"><span data-stu-id="fdad2-175">Quest not recognized by Unity</span></span>

<span data-ttu-id="fdad2-176">Assicurarsi che i percorsi Android siano configurati correttamente.</span><span class="sxs-lookup"><span data-stu-id="fdad2-176">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="fdad2-177">Se continui a riscontrare problemi, segui questa [Guida](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="fdad2-177">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="fdad2-178">**Modificare le preferenze di > > strumenti esterni > Android**</span><span class="sxs-lookup"><span data-stu-id="fdad2-178">**Edit > Preferences > External Tools > Android**</span></span>

![AndroidToolsConfigView](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
