---
title: OculusQuestMRTK
description: Documentazione per la configurazione di Oculus quest in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Oculus quest,
ms.openlocfilehash: 5d3a6f465bb51ac640a7e9dcd17455755219af90
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782057"
---
# <a name="how-to-configure-oculus-quest-in-mrtk-using-the-xr-sdk-pipeline"></a><span data-ttu-id="3d4a3-104">Come configurare Oculus quest in MRTK usando la pipeline di XR SDK</span><span class="sxs-lookup"><span data-stu-id="3d4a3-104">How to configure Oculus Quest in MRTK using the XR SDK pipeline</span></span>

<span data-ttu-id="3d4a3-105">È necessaria una [missione Oculus](https://www.oculus.com/quest/) .</span><span class="sxs-lookup"><span data-stu-id="3d4a3-105">A [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="3d4a3-106">Il supporto di MRTK per l'Oculus missione viene fornito tramite due origini diverse, la pipeline XR di Unity e il pacchetto Oculus Integration Unity.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="3d4a3-107">Il **provider di dati Oculus XRSDK** consente l'uso di entrambe le origini e deve essere usato per usare MRTK in Oculus quest.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to use MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="3d4a3-108">La [pipeline di Unity XR](https://docs.unity3d.com/Manual/XR.html) consente di usare i controller Oculus touch e il rilevamento Head con l'Oculus quest.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-108">The [Unity's XR Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="3d4a3-109">Questa pipeline è lo standard per lo sviluppo di applicazioni XR in Unity 2019,3 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="3d4a3-110">Per usare questa pipeline, assicurarsi di usare **unity 2019,3 o versione successiva**.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span>

<span data-ttu-id="3d4a3-111">Il [pacchetto Oculus Integration Unity](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) consente di usare il **rilevamento manuale** con l'Oculus quest.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-111">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span>
<span data-ttu-id="3d4a3-112">Questo provider di dati **non usa la** pipeline **XR** di Unity o la **pipeline di XR legacy**, ma poiché i controller e headtracking vengono gestiti dalla pipeline XR di Unity, è necessario seguire la procedura di **configurazione del progetto per la ricerca Oculus** per assicurarsi che si stia usando la **pipeline XR** e non la **pipeline XR legacy**.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-112">This data provider does **NOT** use Unity's **XR Pipeline** or **Legacy XR Pipeline**, but because controllers and headtracking are handled by the Unity's XR Pipeline, the steps in **Setting up project for the Oculus Quest** must be followed to ensure that you are using the **XR Pipeline** and not the to-be-deprecated **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="3d4a3-113">Impostazione del progetto per la missione Oculus</span><span class="sxs-lookup"><span data-stu-id="3d4a3-113">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="3d4a3-114">Per assicurarsi che il progetto sia pronto per la distribuzione in Oculus quest, seguire [questa procedura](https://developer.oculus.com/documentation/unity/book-unity-gsg/) .</span><span class="sxs-lookup"><span data-stu-id="3d4a3-114">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="3d4a3-115">Verificare che nel dispositivo sia abilitata la [modalità sviluppatore](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) .</span><span class="sxs-lookup"><span data-stu-id="3d4a3-115">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="3d4a3-116">L'installazione dei driver Oculus ADB è facoltativa.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-116">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-pipeline-for-oculus-quest"></a><span data-ttu-id="3d4a3-117">Impostazione della pipeline XR per Oculus quest</span><span class="sxs-lookup"><span data-stu-id="3d4a3-117">Setting up the XR Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="3d4a3-118">Verificare che il **plug-in Oculus XR** sia installato in **Window--> Package Manager**</span><span class="sxs-lookup"><span data-stu-id="3d4a3-118">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Pacchetto di plug-in Oculus XR](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="3d4a3-120">Verificare che il provider del plug-in Oculus sia incluso nel progetto **modificando > impostazioni progetto--> gestione plug-in XR--> provider plug-in**</span><span class="sxs-lookup"><span data-stu-id="3d4a3-120">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Provider di plug-in Oculus](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="3d4a3-122">Configurazione del pacchetto Oculus Integration Unity per abilitare handtracking</span><span class="sxs-lookup"><span data-stu-id="3d4a3-122">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="3d4a3-123">Scaricare e importare l' [integrazione di Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) da Unity Asset Store.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-123">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="3d4a3-124">La versione più recente testata per funzionare è 20.0.0.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-124">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="3d4a3-125">Le versioni precedenti sono reperibili in questo [Archivio](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span><span class="sxs-lookup"><span data-stu-id="3d4a3-125">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span></span>

1. <span data-ttu-id="3d4a3-126">Passare a Mixed Reality Toolkit > Utilities > Oculus > integrare i moduli di Oculus Integration Unity.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-126">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="3d4a3-127">Questa operazione aggiornerà il asmdefs con le definizioni e i riferimenti necessari per il funzionamento del codice di Oculus missione pertinente.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-127">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="3d4a3-128">Aggiornerà anche il file CSC per filtrare gli avvisi obsoleti generati dalle risorse di integrazione Oculus.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-128">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="3d4a3-129">Il repository MRTK contiene un file CSC che converte gli avvisi in errori, questa conversione interrompe il processo di configurazione del MRTK-Quest.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-129">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Asmdef integrazione con Oculus](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="3d4a3-131">Nella cartella Oculus importata (dovrebbe trovarsi in asset/Oculus), è presente un oggetto con script denominato OculusProjectConfig.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-131">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="3d4a3-132">In tale file di configurazione è necessario impostare HandTrackingSupport su "Controllers and hands".</span><span class="sxs-lookup"><span data-stu-id="3d4a3-132">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Controller e Hands di integrazione Oculus](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="3d4a3-134">Impostazione della scena</span><span class="sxs-lookup"><span data-stu-id="3d4a3-134">Setting up the scene</span></span>

1. <span data-ttu-id="3d4a3-135">Creare una nuova scena Unity o aprire una scena preesistente, ad esempio HandInteractionExamples</span><span class="sxs-lookup"><span data-stu-id="3d4a3-135">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples</span></span>
1. <span data-ttu-id="3d4a3-136">Per aggiungere MRTK alla scena, passare a **mixed reality Toolkit**  >  **Aggiungi alla scena e configurare**</span><span class="sxs-lookup"><span data-stu-id="3d4a3-136">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="3d4a3-137">Uso di Oculus XR SDK provider di dati</span><span class="sxs-lookup"><span data-stu-id="3d4a3-137">Using the Oculus XR SDK Data Provider</span></span>

1. <span data-ttu-id="3d4a3-138">Configurare il profilo per l'uso di **Oculus XR SDK provider di dati**</span><span class="sxs-lookup"><span data-stu-id="3d4a3-138">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="3d4a3-139">Se non si intende modificare i profili di configurazione</span><span class="sxs-lookup"><span data-stu-id="3d4a3-139">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="3d4a3-140">Modificare il profilo in DefaultXRSDKInputSystemProfile e passare a [compilare e distribuire il progetto in Oculus quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span><span class="sxs-lookup"><span data-stu-id="3d4a3-140">Change your profile to DefaultXRSDKInputSystemProfile and go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span></span>

    - <span data-ttu-id="3d4a3-141">In caso contrario, seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="3d4a3-141">Otherwise follow the following:</span></span>
        - <span data-ttu-id="3d4a3-142">Selezionare l'oggetto gioco MixedRealityToolkit nella gerarchia e selezionare **copia e Personalizza** per clonare il profilo di realtà mista predefinito.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-142">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Clona profilo](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="3d4a3-144">Selezionare il profilo di configurazione di **input**</span><span class="sxs-lookup"><span data-stu-id="3d4a3-144">Select the **Input** Configuration Profile</span></span>

        ![Profilo di configurazione di input](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="3d4a3-146">Selezionare **clona** nel profilo di sistema di input per abilitare la modifica.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-146">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Clona profilo di sistema di input](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="3d4a3-148">Aprire la sezione **provider di dati di input** , selezionare **Aggiungi provider di dati** nella parte superiore e il nuovo provider di dati verrà aggiunto alla fine dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-148">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="3d4a3-149">Aprire il nuovo provider di dati e impostare il **tipo** su **Microsoft. MixedReality. Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="3d4a3-149">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**</span></span>

        ![provider di dati di aggiunta XRSDK](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)

1. <span data-ttu-id="3d4a3-151">Il provider di dati di Oculus XR SDK include una prefabbricazione del rig della fotocamera OVR che configura automaticamente il progetto con un rig della fotocamera OVR e OVR Hands per indirizzare correttamente l'input.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-151">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="3d4a3-152">Per aggiungere manualmente un rig della fotocamera OVR alla scena, è necessaria la configurazione manuale di impostazioni e input.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-152">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="3d4a3-153">Compila e Distribuisci il progetto in Oculus quest</span><span class="sxs-lookup"><span data-stu-id="3d4a3-153">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="3d4a3-154">Collegare l'Oculus quest tramite un cavo USB 3,0-> USB</span><span class="sxs-lookup"><span data-stu-id="3d4a3-154">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="3d4a3-155">Passa a **File > impostazioni di compilazione**</span><span class="sxs-lookup"><span data-stu-id="3d4a3-155">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="3d4a3-156">Modificare la distribuzione in **Android**</span><span class="sxs-lookup"><span data-stu-id="3d4a3-156">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="3d4a3-157">Verificare che l'Oculus cerca sia selezionata come dispositivo di esecuzione applicabile</span><span class="sxs-lookup"><span data-stu-id="3d4a3-157">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Dispositivo di esecuzione Oculus](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="3d4a3-159">Selezionare Compila ed Esegui</span><span class="sxs-lookup"><span data-stu-id="3d4a3-159">Select Build and Run</span></span>
    - <span data-ttu-id="3d4a3-160">Quando si seleziona *Compila ed Esegui* la prima volta, si verificherà probabilmente il set di errori di compilazione seguente.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-160">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="3d4a3-161">Si dovrebbe essere in grado di distribuire correttamente quando si seleziona *Compila ed Esegui* di nuovo.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-161">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Errore di compilazione previsto per Oculus](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="3d4a3-163">Accettare la richiesta di abilitazione del _debug USB_ dall'interno della ricerca</span><span class="sxs-lookup"><span data-stu-id="3d4a3-163">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="3d4a3-164">Guarda la tua scena all'interno di Oculus quest</span><span class="sxs-lookup"><span data-stu-id="3d4a3-164">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="3d4a3-165">Rimozione dell'integrazione di Oculus dal progetto</span><span class="sxs-lookup"><span data-stu-id="3d4a3-165">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="3d4a3-166">Passare al Toolkit di realtà mista > Oculus > separato Oculus Integration Unity modules  ![ Oculus separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="3d4a3-166">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="3d4a3-167">Consentire l'aggiornamento di Unity come riferimenti in Microsoft. MixedReality. Toolkit. Providers. Oculus. asmdef e altri file vengono modificati in questo passaggio</span><span class="sxs-lookup"><span data-stu-id="3d4a3-167">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="3d4a3-168">Chiudi Unity</span><span class="sxs-lookup"><span data-stu-id="3d4a3-168">Close Unity</span></span>
1. <span data-ttu-id="3d4a3-169">Chiudere Visual Studio, se è aperto</span><span class="sxs-lookup"><span data-stu-id="3d4a3-169">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="3d4a3-170">Aprire Esplora file e passare alla radice del progetto MRTK Unity</span><span class="sxs-lookup"><span data-stu-id="3d4a3-170">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="3d4a3-171">Elimina la directory UnityProjectName/Library</span><span class="sxs-lookup"><span data-stu-id="3d4a3-171">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="3d4a3-172">Eliminare la directory UnityProjectName/assets/Oculus</span><span class="sxs-lookup"><span data-stu-id="3d4a3-172">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="3d4a3-173">Eliminare il file UnityProjectName/assets/Oculus. meta</span><span class="sxs-lookup"><span data-stu-id="3d4a3-173">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="3d4a3-174">Riaprire Unity</span><span class="sxs-lookup"><span data-stu-id="3d4a3-174">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="3d4a3-175">Errori comuni</span><span class="sxs-lookup"><span data-stu-id="3d4a3-175">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="3d4a3-176">Ricerca non riconosciuta da Unity</span><span class="sxs-lookup"><span data-stu-id="3d4a3-176">Quest not recognized by Unity</span></span>

<span data-ttu-id="3d4a3-177">Assicurarsi che i percorsi Android siano configurati correttamente.</span><span class="sxs-lookup"><span data-stu-id="3d4a3-177">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="3d4a3-178">Se continui a riscontrare problemi, segui questa [Guida](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="3d4a3-178">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="3d4a3-179">**Modificare le preferenze di > > strumenti esterni > Android**</span><span class="sxs-lookup"><span data-stu-id="3d4a3-179">**Edit > Preferences > External Tools > Android**</span></span>

![Configurazione degli strumenti Android](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
