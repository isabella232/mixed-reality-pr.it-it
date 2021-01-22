---
title: Ancoraggi nello spazio di Azure per Android e iOS
description: In questo corso viene illustrato come distribuire un progetto Unity con Mixed Reality Toolkit (MRTK) e Ancoraggi nello spazio di Azure in Android e iOS.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, android, ios, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure, AR Foundation, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 741c000de0ab2feb3dcbff33e2a0b0acc70838e8
ms.sourcegitcommit: 3dad2adfdb5bdb8100d8d864f7845e34a3ef912d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/22/2021
ms.locfileid: "98699250"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="f73cf-104">5. Ancoraggi nello spazio di Azure per Android e iOS</span><span class="sxs-lookup"><span data-stu-id="f73cf-104">5. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="f73cf-105">Questa esercitazione illustra come compilare il progetto nei dispositivi Android e iOS usando AR Foundation, ARCore XR Plugin e ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="f73cf-105">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="f73cf-106">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f73cf-106">Objectives</span></span>

* <span data-ttu-id="f73cf-107">Imparare a compilare il progetto in un dispositivo Android usando Unity AR Foundation e ARCore XR Plugin</span><span class="sxs-lookup"><span data-stu-id="f73cf-107">Learn how to build your project to your Android device using Unity's AR Foundation and ARCore XR Plugin</span></span>
* <span data-ttu-id="f73cf-108">Imparare a compilare il progetto in un dispositivo iOS usando Unity AR Foundation e ARKit XR Plugin</span><span class="sxs-lookup"><span data-stu-id="f73cf-108">Learn how to build your project to your iOS device using Unity's AR Foundation and ARKit XR Plugin</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="f73cf-109">Installazione di pacchetti di Unity incorporati</span><span class="sxs-lookup"><span data-stu-id="f73cf-109">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="f73cf-110">In questa sezione verrà eseguito l'aggiornamento e l'installazione dei seguenti pacchetti incorporati:</span><span class="sxs-lookup"><span data-stu-id="f73cf-110">In this section, you will upgrade and install the following inbuilt packages:</span></span>

* <span data-ttu-id="f73cf-111">AR Foundation 3.1.3</span><span class="sxs-lookup"><span data-stu-id="f73cf-111">AR Foundation 3.1.3</span></span>
* <span data-ttu-id="f73cf-112">Helper di input legacy XR 2.1.6</span><span class="sxs-lookup"><span data-stu-id="f73cf-112">XR Legacy Input Helpers 2.1.6</span></span>
* <span data-ttu-id="f73cf-113">ARCore XR Plugin 3.1.3 per il supporto Android</span><span class="sxs-lookup"><span data-stu-id="f73cf-113">ARCore XR Plugin 3.1.3 for Android support</span></span>
* <span data-ttu-id="f73cf-114">ARKit XR plugin 3.1.3 per il supporto iOS</span><span class="sxs-lookup"><span data-stu-id="f73cf-114">ARKit XR plugin 3.1.3 for iOS support</span></span>

> [!CAUTION]
> <span data-ttu-id="f73cf-115">Non tutte le versioni sono compatibili con MRTK e solo alcune versioni interagiscono tra loro, quindi è importante assicurarsi di installare le versioni esatte elencate sopra.</span><span class="sxs-lookup"><span data-stu-id="f73cf-115">Not all version are compatible with MRTK and only certain version works together, so make sure you install the exact versions listed above.</span></span>

<span data-ttu-id="f73cf-116">Scegliere **Window** (Finestra)  > **Package Manager** (Gestione pacchetti) dal menu Unity per aprire la finestra Package Manager(Gestione pacchetti), quindi selezionare **AR Foundation** > **3.1.3** e fare clic sul pulsante **Update to 3.1.3** (Aggiorna a 3.1.3) per aggiornare il pacchetto:</span><span class="sxs-lookup"><span data-stu-id="f73cf-116">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** > **3.1.3** and click the **Update to 3.1.3** button to update the package:</span></span>

![Package Manager di Unity con AR Foundation selezionato](images/mr-learning-asa/asa-05-section1-step1-1.png)

<span data-ttu-id="f73cf-118">Seguire lo stesso processo per importare i pacchetti rimanenti, in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="f73cf-118">Follow the same process to import the remaining packages as needed.</span></span>

> [!NOTE]
> <span data-ttu-id="f73cf-119">Se sviluppi il progetto per Android, non è necessario installare il pacchetto ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="f73cf-119">If you are developing this project for Android, there is no need to install the ARKit XR Plugin package.</span></span> <span data-ttu-id="f73cf-120">Analogamente, se sviluppi il progetto per iOS, non è necessario installare ARCore XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="f73cf-120">Similarly, if you are developing this project for iOS, you do not need to install the ARCore XR Plugin.</span></span>

## <a name="configure-mrtk-for-ar-foundation-camera"></a><span data-ttu-id="f73cf-121">Configurare MRTK per AR Foundation Camera</span><span class="sxs-lookup"><span data-stu-id="f73cf-121">Configure MRTK for AR Foundation Camera</span></span>

<span data-ttu-id="f73cf-122">In questa sezione verrà illustrato come configurare MRTK per la distribuzione in un dispositivo mobile.</span><span class="sxs-lookup"><span data-stu-id="f73cf-122">In this section, you will learn how to configure MRTK for deploying to a mobile device.</span></span>

<span data-ttu-id="f73cf-123">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit**.</span><span class="sxs-lookup"><span data-stu-id="f73cf-123">In the Hierarchy window, select the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="f73cf-124">Quindi, nella finestra Inspector (Controllo) selezionare la scheda **Camera** (Fotocamera), clonare i profilo della fotocamera e assegnare un nome adatto, ad esempio **AzureSpatialAnchors_ARCameraProfile**:</span><span class="sxs-lookup"><span data-stu-id="f73cf-124">Then in the Inspector window, select the **Camera** tab, clone the camera profile, and give it a suitable name, for example, **AzureSpatialAnchors_ARCameraProfile**:</span></span>

![Unity con il profilo ARCameraProfile appena creato selezionato](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="f73cf-126">Per rivedere la procedura di clonazione dei profili MRTK, fare riferimento alle istruzioni contenute in [Configurazione dei profili di Mixed Reality Toolkit](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="f73cf-126">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="f73cf-127">Con la scheda **Camera** (Fotocamera) ancora selezionata nella finestra Inspector (Controllo), espandere **Camera Setting Providers** (Provider impostazioni fotocamera) e fare clic sul pulsante **+ Add Camera Setting Provider** (+ Aggiungi provider impostazioni fotocamera), quindi espandere **New data provider 1** (Nuovo provider di dati 1):</span><span class="sxs-lookup"><span data-stu-id="f73cf-127">With the **Camera** tab still selected in the Inspector window, expand the **Camera Setting Providers** and click the **+ Add Camera Setting Provider** button, then expand the newly added **New data provider 1**:</span></span>

![Profilo ARCameraProfile di Unity con il nuovo provider di dati aggiunto](images/mr-learning-asa/asa-05-section2-step1-2.png)

<span data-ttu-id="f73cf-129">Usando l'elenco a discesa **Type** (Tipo), cambiare il tipo in **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span><span class="sxs-lookup"><span data-stu-id="f73cf-129">Using the **Type** dropdown, change the type to **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span></span>

![Profilo ARCameraProfile di Unity con il percorso di selezione del tipo di provider di dati](images/mr-learning-asa/asa-05-section2-step1-3.png)

<span data-ttu-id="f73cf-131">Con l'oggetto **MixedRealityToolkit** ancora selezionato nella finestra Hierarchy (Gerarchia), usare il pulsante **Add Component** (Aggiungi componente) nella finestra Inspector (Controllo) per aggiungere i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="f73cf-131">With the **MixedRealityToolkit** object still selected in the Hierarchy window, use the **Add Component** button in the Inspector window to add the following components:</span></span>

* <span data-ttu-id="f73cf-132">AR Anchor Manager (Script)</span><span class="sxs-lookup"><span data-stu-id="f73cf-132">AR Anchor Manager (Script)</span></span>
* <span data-ttu-id="f73cf-133">DisableDiagnosticsSystem (Script)</span><span class="sxs-lookup"><span data-stu-id="f73cf-133">DisableDiagnosticsSystem (Script)</span></span>

![<span data-ttu-id="f73cf-134">Oggetto MixedRealityToolkit di Unity con i componenti AR Anchor Manager e DisableDiagnosticsSystem aggiunti</span><span class="sxs-lookup"><span data-stu-id="f73cf-134">Unity MixedRealityToolkit object with AR Anchor Manager and DisableDiagnosticsSystem components added</span></span> ](images/mr-learning-asa/asa-05-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="f73cf-135">Quando si aggiunge il componente AR Reference Point Manager (Script), viene aggiunto automaticamente il componente AR Session Origin (Script) perché è richiesto dal componente AR Reference Point Manager (Script).</span><span class="sxs-lookup"><span data-stu-id="f73cf-135">When you add the AR Reference Point Manager (Script) component, the AR Session Origin (Script) component is automatically added because it is required by the AR Reference Point Manager (Script) component.</span></span>



<span data-ttu-id="f73cf-136">Aggiornare lo script di MRTK Unity per le definizioni richiamando la voce di menu: **mixed reality Toolkit**  >  **Utilities**  >  **Unity** > Update scripting definisce</span><span class="sxs-lookup"><span data-stu-id="f73cf-136">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality Toolkit** > **Utilities** > **UnityAR** > Update Scripting Defines</span></span>

## <a name="building-your-application-to-your-android-device"></a><span data-ttu-id="f73cf-137">Compilazione dell'applicazione in un dispositivo Android</span><span class="sxs-lookup"><span data-stu-id="f73cf-137">Building your application to your Android device</span></span>

<span data-ttu-id="f73cf-138">In questa sezione verrà illustrato come configurare il progetto per la compilazione e la distribuzione in un dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="f73cf-138">In this section, you will learn how to configure your project to build and deploy it to an Android device.</span></span>

<span data-ttu-id="f73cf-139">Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente, quindi impostare la piattaforma su Android:</span><span class="sxs-lookup"><span data-stu-id="f73cf-139">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and then switch the platform to Android:</span></span>

![Finestra Build Settings di Unity con la piattaforma Android selezionata](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="f73cf-141">Per rivedere la procedura per cambiare piattaforma di compilazione, fare riferimento alle istruzioni contenute in [Passaggio a un'altra piattaforma di compilazione](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="f73cf-141">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="f73cf-142">Chiudere la finestra Build Settings (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="f73cf-142">Close the Build Settings window.</span></span>

<span data-ttu-id="f73cf-143">Nel menu di Unity selezionare **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore progetto MRTK), verificare che tutte le opzioni siano selezionate, quindi fare clic sul pulsante **Apply** (Applica) per applicare le impostazioni:</span><span class="sxs-lookup"><span data-stu-id="f73cf-143">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Finestra MRTK Project Configurator di Unity - Android](images/mr-learning-asa/asa-05-section3-step1-2.png)

<span data-ttu-id="f73cf-145">Dal menu Unity scegliere **Edit** > **Project Settings...** (Modifica > Impostazioni del progetto) per aprire la finestra Player Settings (Impostazioni lettore) e quindi individuare la sezione **Player** >  **Other Settings** (Lettore > Altre impostazioni), selezionare **Vulkan** e rimuoverlo facendo clic sul simbolo **"-"** :</span><span class="sxs-lookup"><span data-stu-id="f73cf-145">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, select **Vulkan** and remove it by clicking the **"-"** symbol:</span></span>

![Area Other Settings di Unity con Vulkan selezionato](images/mr-learning-asa/asa-05-section3-step1-3.png)

<span data-ttu-id="f73cf-147">Nel menu Unity selezionare **modifica**  >  **Impostazioni progetto...**  > **Lettore** >  di **Impostazione di XR**, assicurarsi di trovarsi nella piattaforma **Android** e selezionare la casella di controllo **Virtual Reality supported** , quindi fare clic sull'icona + e selezionare None:</span><span class="sxs-lookup"><span data-stu-id="f73cf-147">In the Unity menu, select **Edit** > **Project Settings...** >**Player**> **XR Setting**, make sure you are in **Android** platform and check the **Virtual Reality Supported** checkbox then click the + icon, and select None:</span></span>

![Finestra MRTK Project Configurator di Unity - Android](images/mr-learning-asa/asa-05-section3-step1-2-1.png)

<span data-ttu-id="f73cf-149">Chiudere la finestra Player Settings (Impostazioni giocatore) e aprire di nuovo la finestra Build Settings (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="f73cf-149">Close the Player Settings window and open the Build Settings window again.</span></span>

<span data-ttu-id="f73cf-150">Nella finestra Build Settings (Impostazioni di compilazione) fare clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene nella compilazione).</span><span class="sxs-lookup"><span data-stu-id="f73cf-150">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span> <span data-ttu-id="f73cf-151">Quindi, usare un cavo USB, connettere il dispositivo Android al computer e selezionarlo nell'elenco a discesa **Run Device** (Esegui dispositivo):</span><span class="sxs-lookup"><span data-stu-id="f73cf-151">Then, use a USB cable, connect your Android device to your computer and select it from the **Run Device** dropdown:</span></span>

![Finestra Build Settings di Unity con la scena aggiunta e Run Device selezionato](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> <span data-ttu-id="f73cf-153">Se il dispositivo non è presente nell'elenco a discesa Run Device (Esegui dispositivo), potrebbe essere necessario premere il pulsante Refresh (Aggiorna) accanto all'elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="f73cf-153">If your device does not appear in the Run Device dropdown, you might need to press the Refresh button next to the dropdown.</span></span>

<span data-ttu-id="f73cf-154">Nella finestra delle impostazioni di compilazione fare clic sul pulsante **Build And Run** (Compila ed esegui) per aprire la finestra Build Android (Compila in Android).</span><span class="sxs-lookup"><span data-stu-id="f73cf-154">In the Build Settings window, click the **Build And Run** button to open the Build Android window.</span></span>

<span data-ttu-id="f73cf-155">Scegliere il percorso in cui archiviare la build, ad esempio _D:\MixedRealityLearning\Builds_, quindi assegnare un nome adeguato all'apk, ad esempio _MRTKTutorials-AzureSpatialAnchors_, e fare clic sul pulsante **Save** (Salva) per avviare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="f73cf-155">Choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, then give the apk a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and click the **Save** button to start the build process:</span></span>

![Finestra Build Settings di Unity con la finestra del prompt di salvataggio - Android](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
<span data-ttu-id="f73cf-157">Se nella finestra della console Unity viene visualizzato un errore relativo ai moduli Android SDK, NDK o JDK, è necessario aprire Unity Hub e installare i moduli Android Build Support associati.</span><span class="sxs-lookup"><span data-stu-id="f73cf-157">If you get any error in the Unity Console window related to Android SDK, NDK, or JDK modules, you need to open Unity Hub and install the associated Android Build Support modules.</span></span>

<span data-ttu-id="f73cf-158">Al termine del processo di compilazione, le app dovrebbero essere caricate automaticamente nel dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="f73cf-158">When the build process is complete, your apps should automatically load on your Android device.</span></span>

## <a name="building-your-application-to-your-ios-device"></a><span data-ttu-id="f73cf-159">Compilazione dell'applicazione in un dispositivo iOS</span><span class="sxs-lookup"><span data-stu-id="f73cf-159">Building your application to your iOS device</span></span>

<span data-ttu-id="f73cf-160">In questa sezione verrà illustrato come configurare il progetto per la compilazione e la distribuzione in un dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="f73cf-160">In this section, you will learn how to configure your project, to build and deploy it to your iOS device.</span></span>

<span data-ttu-id="f73cf-161">Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente e impostare la piattaforma su iOS:</span><span class="sxs-lookup"><span data-stu-id="f73cf-161">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and switch platform to iOS:</span></span>

![Finestra Build Settings di Unity con la piattaforma iOS selezionata](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="f73cf-163">Per rivedere la procedura per cambiare piattaforma di compilazione, fare riferimento alle istruzioni contenute in [Passaggio a un'altra piattaforma di compilazione](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="f73cf-163">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="f73cf-164">Chiudere la finestra Build Settings (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="f73cf-164">Close the Build Settings window.</span></span>

<span data-ttu-id="f73cf-165">Nel menu di Unity selezionare **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore progetto MRTK), verificare che tutte le opzioni siano selezionate, quindi fare clic sul pulsante **Apply** (Applica) per applicare le impostazioni:</span><span class="sxs-lookup"><span data-stu-id="f73cf-165">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Finestra MRTK Project Configurator di Unity - iOS](images/mr-learning-asa/asa-05-section4-step1-2.png)

<span data-ttu-id="f73cf-167">Dal menu Unity scegliere **Edit** > **Project Settings...** (Modifica > Impostazioni del progetto) per aprire la finestra Player Settings (Impostazioni lettore) e quindi individuare la sezione **Player** >  **Other Settings** (Lettore > Altre impostazioni), deselezionare la casella di controllo **Strip Engine Code** (Rimuovi codice motore) per disabilitarla:</span><span class="sxs-lookup"><span data-stu-id="f73cf-167">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, uncheck the **Strip Engine Code** checkbox to disable it:</span></span>

![Area Other Settings di Unity con l'opzione Strip Engine Code disabilitata](images/mr-learning-asa/asa-05-section4-step1-3.png)

<span data-ttu-id="f73cf-169">Chiudere la finestra Player Settings (Impostazioni lettore) e aprire di nuovo la finestra **Build Settings** (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="f73cf-169">Close the Player Settings window and open the **Build Settings** window again.</span></span>

<span data-ttu-id="f73cf-170">Nella finestra Build Settings (Impostazioni di compilazione) fare clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene nella compilazione):</span><span class="sxs-lookup"><span data-stu-id="f73cf-170">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list:</span></span>

![Finestra Build Settings di Unity con la scena aggiunta](images/mr-learning-asa/asa-05-section4-step1-4.png)

<span data-ttu-id="f73cf-172">Nella finestra delle impostazioni di compilazione fare clic sul pulsante **Build** (Compila) per aprire la finestra Build iOS (Compila in iOS).</span><span class="sxs-lookup"><span data-stu-id="f73cf-172">In the Build Settings window, click the **Build** button to open the Build iOS window.</span></span>

<span data-ttu-id="f73cf-173">Scegliere un percorso appropriato in cui archiviare il progetto Xcode, ad esempio _D:\MixedRealityLearning\Builds_, creare una nuova cartella e assegnarle un nome adatto, ad esempio, _MRTKTutorials-AzureSpatialAnchors_, e quindi fare clic sul pulsante **Select Folder** (Seleziona cartella) per avviare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="f73cf-173">Choose a suitable location to store your Xcode project, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and then click the **Select Folder** button to start the build process:</span></span>

![Finestra Build Settings di Unity con la finestra del prompt di salvataggio - iOS](images/mr-learning-asa/asa-05-section4-step1-5.png)

<span data-ttu-id="f73cf-175">Al termine del processo di compilazione, seguire le istruzioni in [Esportare il progetto Xcode](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) per informazioni su come distribuire il progetto Xcode in un dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="f73cf-175">When the build process is complete, follow the [Export the Xcode project](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) instructions to learn to deploy your Xcode project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="f73cf-176">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="f73cf-176">Congratulations</span></span>

<span data-ttu-id="f73cf-177">In questa esercitazione è stato descritto come compilare il progetto nei dispositivi Android e iOS usando AR Foundation, ARCore XR Plugin e ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="f73cf-177">In this tutorial, you learned how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>