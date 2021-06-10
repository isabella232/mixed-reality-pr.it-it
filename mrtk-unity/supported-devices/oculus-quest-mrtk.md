---
title: Oculus Quest MRTK
description: Documentazione da configurare per Oculus Quest in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, Oculus Quest,
ms.openlocfilehash: 0892e0d416cd07d1bedbeea0ddb316e3eb012b94
ms.sourcegitcommit: 4c1dd5c22af69eeb192425118c2bfb95344b8dd9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2021
ms.locfileid: "110441180"
---
# <a name="building-and-deploying-mrtk-to-oculus-quest-using-the-xr-sdk-pipeline"></a><span data-ttu-id="92813-104">Compilazione e distribuzione di MRTK in Oculus Quest usando la pipeline XR SDK</span><span class="sxs-lookup"><span data-stu-id="92813-104">Building and deploying MRTK to Oculus Quest using the XR SDK pipeline</span></span>

<span data-ttu-id="92813-105">È [necessaria una oculus quest.](https://www.oculus.com/quest/)</span><span class="sxs-lookup"><span data-stu-id="92813-105">An [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="92813-106">Il supporto di MRTK per Oculus Quest viene fornito tramite due origini diverse, la pipeline XR SDK di Unity e il pacchetto Oculus Integration Unity.</span><span class="sxs-lookup"><span data-stu-id="92813-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR SDK pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="92813-107">Oculus **XRSDK provider di dati** l'uso di entrambe le origini e deve essere usato per distribuire MRTK in Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="92813-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to deploy MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="92813-108">[Unity XR SDK Pipeline](https://docs.unity3d.com/Manual/XR.html) consente l'uso dei controller Oculus Touch e del rilevamento della testa con Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="92813-108">The [Unity XR SDK Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="92813-109">Questa pipeline è lo standard per lo sviluppo di applicazioni XR in Unity 2019.3 e versioni diverse.</span><span class="sxs-lookup"><span data-stu-id="92813-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="92813-110">Per usare questa pipeline, assicurarsi di usare **Unity 2019.3 o versione più recente.**</span><span class="sxs-lookup"><span data-stu-id="92813-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span> <span data-ttu-id="92813-111">Questa operazione **è necessaria** per distribuire applicazioni MRTK in Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="92813-111">This is **required** to deploy MRTK applications to the Oculus Quest.</span></span> 

<span data-ttu-id="92813-112">Il [pacchetto Oculus Integration Unity](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) consente l'uso del **tracciamento manuale** con Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="92813-112">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span> <span data-ttu-id="92813-113">Questo provider di dati **NON usa** la **pipeline XR SDK** di Unity o la pipeline **XR legacy.**</span><span class="sxs-lookup"><span data-stu-id="92813-113">This data provider does **NOT** use Unity's **XR SDK Pipeline** or **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="92813-114">Configurazione del progetto per Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="92813-114">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="92813-115">Seguire [questa procedura](https://developer.oculus.com/documentation/unity/book-unity-gsg/) per assicurarsi che il progetto sia pronto per la distribuzione in Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="92813-115">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="92813-116">Assicurarsi che [la modalità sviluppatore](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) sia abilitata nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="92813-116">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="92813-117">L'installazione dei driver Oculus ADB è facoltativa.</span><span class="sxs-lookup"><span data-stu-id="92813-117">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a><span data-ttu-id="92813-118">Configurazione della pipeline XR SDK per Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="92813-118">Setting up the XR SDK Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="92813-119">Assicurarsi che il **plug-in Oculus XR** sia installato in **Finestra --> Gestione pacchetti**</span><span class="sxs-lookup"><span data-stu-id="92813-119">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Pacchetto del plug-in Oculus XR](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="92813-121">Assicurarsi che il provider di plug-in Oculus sia incluso nel progetto selezionando Modifica --impostazioni progetto **di > --> Gestione plug-in XR --provider plug-in >**</span><span class="sxs-lookup"><span data-stu-id="92813-121">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Provider di plug-in Oculus](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="92813-123">Configurazione del pacchetto Oculus Integration Unity per abilitare il handtracking</span><span class="sxs-lookup"><span data-stu-id="92813-123">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="92813-124">Scaricare e [importare Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) da Unity Asset Store.</span><span class="sxs-lookup"><span data-stu-id="92813-124">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="92813-125">La versione più recente testata per il funzionamento è 20.0.0.</span><span class="sxs-lookup"><span data-stu-id="92813-125">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="92813-126">Le versioni precedenti sono disponibili in questo [archivio](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span><span class="sxs-lookup"><span data-stu-id="92813-126">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span></span>

1. <span data-ttu-id="92813-127">Passare a Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules (Integra moduli di Oculus Integration Unity).</span><span class="sxs-lookup"><span data-stu-id="92813-127">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="92813-128">Questa operazione aggiornerà gli asmdef con le definizioni e i riferimenti necessari per il funzionamento del codice Oculus Quest pertinente.</span><span class="sxs-lookup"><span data-stu-id="92813-128">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="92813-129">Aggiornerà anche il file csc per filtrare gli avvisi obsoleti prodotti dagli asset di Oculus Integration.</span><span class="sxs-lookup"><span data-stu-id="92813-129">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="92813-130">Il repo MRTK contiene un file csc che converte gli avvisi in errori. Questa conversione interrompe il MRTK-Quest di configurazione.</span><span class="sxs-lookup"><span data-stu-id="92813-130">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Oculus Integration Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="92813-132">Nella cartella Oculus importata (si trova in Assets/Oculus) è presente un oggetto che può essere creato tramite script denominato OculusProjectConfig.</span><span class="sxs-lookup"><span data-stu-id="92813-132">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="92813-133">In questo file di configurazione è necessario impostare HandTrackingSupport su "Controllers and Hands".</span><span class="sxs-lookup"><span data-stu-id="92813-133">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Oculus Integration Controller And Hands](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="92813-135">Configurazione della scena</span><span class="sxs-lookup"><span data-stu-id="92813-135">Setting up the scene</span></span>

1. <span data-ttu-id="92813-136">Creare una nuova scena unity o aprire una scena preesiste, ad esempio HandInteractionExamples</span><span class="sxs-lookup"><span data-stu-id="92813-136">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples</span></span>
1. <span data-ttu-id="92813-137">Aggiungere MRTK alla scena passando a **Mixed Reality Toolkit** Add to Scene and Configure  >  **(Aggiungi alla scena e configura)**</span><span class="sxs-lookup"><span data-stu-id="92813-137">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="92813-138">Uso di Oculus XR SDK provider di dati</span><span class="sxs-lookup"><span data-stu-id="92813-138">Using the Oculus XR SDK Data Provider</span></span>

1. <span data-ttu-id="92813-139">Configurare il profilo per l'uso di **Oculus XR SDK provider di dati**</span><span class="sxs-lookup"><span data-stu-id="92813-139">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="92813-140">Se non si intende modificare i profili di configurazione</span><span class="sxs-lookup"><span data-stu-id="92813-140">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="92813-141">Modificare il profilo in DefaultXRSDKConfigurationProfile e passare a Compilare e [distribuire il progetto in Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span><span class="sxs-lookup"><span data-stu-id="92813-141">Change your profile to DefaultXRSDKConfigurationProfile and go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span></span>

    - <span data-ttu-id="92813-142">In caso contrario, seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="92813-142">Otherwise follow the following:</span></span>
        - <span data-ttu-id="92813-143">Selezionare l'oggetto gioco MixedRealityToolkit nella gerarchia e selezionare Copia e **personalizza** per clonare il profilo di realtà mista predefinito.</span><span class="sxs-lookup"><span data-stu-id="92813-143">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Clonare il profilo](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="92813-145">Selezionare il **profilo di configurazione** di input</span><span class="sxs-lookup"><span data-stu-id="92813-145">Select the **Input** Configuration Profile</span></span>

        ![Profilo di configurazione di input](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="92813-147">Selezionare **Clona** nel profilo di sistema di input per abilitare la modifica.</span><span class="sxs-lookup"><span data-stu-id="92813-147">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Clonare il profilo di sistema di input](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="92813-149">Aprire la **sezione Provider di dati** di input, selezionare **Aggiungi** provider di dati nella parte superiore e il nuovo provider di dati verrà aggiunto alla fine dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="92813-149">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="92813-150">Aprire il nuovo provider di dati e impostare **Type** su **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="92813-150">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**</span></span>

        ![Oculus Add XRSDK provider di dati](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)

1. <span data-ttu-id="92813-152">Oculus XR SDK provider di dati include un prefab OVR Camera Rig che configura automaticamente il progetto con un rig di fotocamera OVR e mani OVR per indirizzare correttamente l'input.</span><span class="sxs-lookup"><span data-stu-id="92813-152">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="92813-153">L'aggiunta manuale di un rig di fotocamera OVR alla scena richiederà la configurazione manuale delle impostazioni e dell'input.</span><span class="sxs-lookup"><span data-stu-id="92813-153">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="92813-154">Compilare e distribuire il progetto in Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="92813-154">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="92813-155">Collegare Oculus Quest tramite un cavo USB 3.0 -> USB C</span><span class="sxs-lookup"><span data-stu-id="92813-155">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="92813-156">Passare a **Impostazioni di > file**</span><span class="sxs-lookup"><span data-stu-id="92813-156">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="92813-157">Modificare la distribuzione in **Android**</span><span class="sxs-lookup"><span data-stu-id="92813-157">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="92813-158">Assicurarsi che Oculus Quest sia selezionato come dispositivo di esecuzione applicabile</span><span class="sxs-lookup"><span data-stu-id="92813-158">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Dispositivo di esecuzione Oculus](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="92813-160">Selezionare Compila ed esegui</span><span class="sxs-lookup"><span data-stu-id="92813-160">Select Build and Run</span></span>
    - <span data-ttu-id="92813-161">È probabile che si verifichi il set di errori di compilazione seguente quando si seleziona *Compila ed esegui* la prima volta.</span><span class="sxs-lookup"><span data-stu-id="92813-161">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="92813-162">Dovrebbe essere possibile eseguire correttamente la distribuzione selezionando Compila *ed esegui di* nuovo.</span><span class="sxs-lookup"><span data-stu-id="92813-162">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Errori di compilazione previsti di Oculus](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="92813-164">Accettare la _richiesta Consenti debug USB_ dall'interno della ricerca</span><span class="sxs-lookup"><span data-stu-id="92813-164">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="92813-165">Visualizzare la scena all'interno di Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="92813-165">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="92813-166">Rimozione dell'integrazione oculus dal progetto</span><span class="sxs-lookup"><span data-stu-id="92813-166">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="92813-167">Passare a Mixed Reality Toolkit > Oculus > Oculus Integration Unity Modules  ![ Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="92813-167">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="92813-168">Consentire l'aggiornamento di Unity quando i riferimenti in Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef e altri file vengono modificati in questo passaggio</span><span class="sxs-lookup"><span data-stu-id="92813-168">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="92813-169">Chiudere Unity</span><span class="sxs-lookup"><span data-stu-id="92813-169">Close Unity</span></span>
1. <span data-ttu-id="92813-170">Chiudere Visual Studio, se è aperto</span><span class="sxs-lookup"><span data-stu-id="92813-170">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="92813-171">Aprire Esplora file e passare alla radice del progetto UNITY MRTK</span><span class="sxs-lookup"><span data-stu-id="92813-171">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="92813-172">Eliminare la directory UnityProjectName/Library</span><span class="sxs-lookup"><span data-stu-id="92813-172">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="92813-173">Eliminare la directory UnityProjectName/Assets/Oculus</span><span class="sxs-lookup"><span data-stu-id="92813-173">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="92813-174">Eliminare il file UnityProjectName/Assets/Oculus.meta</span><span class="sxs-lookup"><span data-stu-id="92813-174">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="92813-175">Riaprire Unity</span><span class="sxs-lookup"><span data-stu-id="92813-175">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="92813-176">Errori comuni</span><span class="sxs-lookup"><span data-stu-id="92813-176">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="92813-177">Ricerca non riconosciuta da Unity</span><span class="sxs-lookup"><span data-stu-id="92813-177">Quest not recognized by Unity</span></span>

<span data-ttu-id="92813-178">Assicurarsi che i percorsi Android siano configurati correttamente.</span><span class="sxs-lookup"><span data-stu-id="92813-178">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="92813-179">Se si continuano a riscontrare problemi, seguire questa [guida](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="92813-179">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="92813-180">**Modificare > preferenze > strumenti esterni > Android**</span><span class="sxs-lookup"><span data-stu-id="92813-180">**Edit > Preferences > External Tools > Android**</span></span>

![Configurazione degli strumenti Android](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
