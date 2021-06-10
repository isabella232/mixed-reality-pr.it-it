---
title: Ancoraggi nello spazio di Azure per Android e iOS
description: In questo corso viene illustrato come distribuire un progetto Unity con Mixed Reality Toolkit (MRTK) e Ancoraggi nello spazio di Azure in Android e iOS.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, android, ios, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure, AR Foundation, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 67bda33f8d2d0711c83791be2e76d91b53ff934f
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403438"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="27bdf-104">5. Ancoraggi nello spazio di Azure per Android e iOS</span><span class="sxs-lookup"><span data-stu-id="27bdf-104">5. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="27bdf-105">Questa esercitazione illustra come compilare il progetto nei dispositivi Android e iOS usando AR Foundation, ARCore XR Plugin e ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="27bdf-105">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="27bdf-106">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="27bdf-106">Objectives</span></span>

* <span data-ttu-id="27bdf-107">Imparare a compilare il progetto in un dispositivo Android usando Unity AR Foundation e ARCore XR Plugin</span><span class="sxs-lookup"><span data-stu-id="27bdf-107">Learn how to build your project to your Android device using Unity's AR Foundation and ARCore XR Plugin</span></span>
* <span data-ttu-id="27bdf-108">Imparare a compilare il progetto in un dispositivo iOS usando Unity AR Foundation e ARKit XR Plugin</span><span class="sxs-lookup"><span data-stu-id="27bdf-108">Learn how to build your project to your iOS device using Unity's AR Foundation and ARKit XR Plugin</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="27bdf-109">Installazione di pacchetti di Unity incorporati</span><span class="sxs-lookup"><span data-stu-id="27bdf-109">Installing inbuilt Unity packages</span></span>

[!INCLUDE[](includes/installing-inbuilt-unity-packages-for-asa-android-and-ios.md)]

## <a name="configure-mrtk-for-ar-foundation-camera"></a><span data-ttu-id="27bdf-110">Configurare MRTK per AR Foundation Camera</span><span class="sxs-lookup"><span data-stu-id="27bdf-110">Configure MRTK for AR Foundation Camera</span></span>

<span data-ttu-id="27bdf-111">In questa sezione verrà illustrato come configurare MRTK per la distribuzione in un dispositivo mobile.</span><span class="sxs-lookup"><span data-stu-id="27bdf-111">In this section, you will learn how to configure MRTK for deploying to a mobile device.</span></span>

<span data-ttu-id="27bdf-112">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit**.</span><span class="sxs-lookup"><span data-stu-id="27bdf-112">In the Hierarchy window, select the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="27bdf-113">Quindi, nella finestra Inspector (Controllo) selezionare la scheda **Camera** (Fotocamera), clonare i profilo della fotocamera e assegnare un nome adatto, ad esempio **AzureSpatialAnchors_ARCameraProfile**:</span><span class="sxs-lookup"><span data-stu-id="27bdf-113">Then in the Inspector window, select the **Camera** tab, clone the camera profile, and give it a suitable name, for example, **AzureSpatialAnchors_ARCameraProfile**:</span></span>

![Unity con il profilo ARCameraProfile appena creato selezionato](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="27bdf-115">Per rivedere la procedura di clonazione dei profili MRTK, fare riferimento alle istruzioni contenute in [Configurazione dei profili di Mixed Reality Toolkit](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="27bdf-115">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="27bdf-116">Con la **scheda Fotocamera** ancora selezionata nella  finestra Inspector (Controllo), espandere i provider di impostazioni della fotocamera e fare clic su "-" per rimuovere le impostazioni della fotocamera **Windows Mixed Reality** o XR SDK Windows Mixed Reality Camera Setting (Impostazioni fotocamera **XR SDK):**</span><span class="sxs-lookup"><span data-stu-id="27bdf-116">With the **Camera** tab still selected in the Inspector window, expand the **Camera Setting Providers** and by clicking the "-" remove the **Windows Mixed Reality Camera Setting** or **XR SDK Windows Mixed Reality Camera Setting**:</span></span>

![<span data-ttu-id="27bdf-117">Profilo ARCameraProfile di Unity con il nuovo provider di dati aggiunto</span><span class="sxs-lookup"><span data-stu-id="27bdf-117">Unity ARCameraProfile with new data provider added</span></span> ](images/mr-learning-asa/asa-05-section2-step1-2.png)

<span data-ttu-id="27bdf-118">fare clic sul pulsante + Add Camera Setting Provider (+ Aggiungi provider di impostazioni **fotocamera),** quindi espandere il **nuovo provider di dati aggiunto:**</span><span class="sxs-lookup"><span data-stu-id="27bdf-118">and click the **+ Add Camera Setting Provider** button, then expand the newly added **New data provider**:</span></span>

![Fotocamera AR aggiunta per Android](images/mr-learning-asa/asa-05-section2-step1-3.png)

<span data-ttu-id="27bdf-120">Usando l'elenco a discesa **Type** (Tipo), cambiare il tipo in **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span><span class="sxs-lookup"><span data-stu-id="27bdf-120">Using the **Type** dropdown, change the type to **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span></span>

![Profilo ARCameraProfile di Unity con il percorso di selezione del tipo di provider di dati](images/mr-learning-asa/asa-05-section2-step1-4.png)

<span data-ttu-id="27bdf-122">Aggiornare le definizione di scripting unityAR di MRTK richiamando la voce di menu: **Mixed Reality**  >  **Toolkit**  >  **Utilities**  >  **UnityAR** > Update Scripting Defines</span><span class="sxs-lookup"><span data-stu-id="27bdf-122">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality** > **Toolkit** > **Utilities** > **UnityAR** > Update Scripting Defines</span></span>

## <a name="building-your-application-to-your-android-device"></a><span data-ttu-id="27bdf-123">Compilazione dell'applicazione in un dispositivo Android</span><span class="sxs-lookup"><span data-stu-id="27bdf-123">Building your application to your Android device</span></span>

<span data-ttu-id="27bdf-124">In questa sezione verrà illustrato come configurare il progetto per la compilazione e la distribuzione in un dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="27bdf-124">In this section, you will learn how to configure your project to build and deploy it to an Android device.</span></span>

<span data-ttu-id="27bdf-125">Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente, quindi impostare la piattaforma su Android:</span><span class="sxs-lookup"><span data-stu-id="27bdf-125">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and then switch the platform to Android:</span></span>

![Finestra Build Settings di Unity con la piattaforma Android selezionata](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="27bdf-127">Per rivedere la procedura per cambiare piattaforma di compilazione, fare riferimento alle istruzioni contenute in [Passaggio a un'altra piattaforma di compilazione](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="27bdf-127">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="27bdf-128">Chiudere la finestra Build Settings (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="27bdf-128">Close the Build Settings window.</span></span>

<span data-ttu-id="27bdf-129">Nel menu di Unity seleziona **Mixed Reality** Toolkit Utilities Configure Project for MRTK (Configura progetto per MRTK) per aprire la finestra  >    >    >   **MRTK Project Configurator (Configuratore progetto MRTK),**  verifica che tutte le opzioni siano selezionate e quindi fai clic sul pulsante Apply (Applica) per applicare le impostazioni:</span><span class="sxs-lookup"><span data-stu-id="27bdf-129">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Unity MRTK Project Configurator 1](images/mr-learning-asa/asa-05-section3-step1-2.png)

<span data-ttu-id="27bdf-131">Dal menu Unity scegliere **Edit** > **Project Settings...** (Modifica > Impostazioni del progetto) per aprire la finestra Player Settings (Impostazioni lettore) e quindi individuare la sezione **Player** >  **Other Settings** (Lettore > Altre impostazioni), selezionare **Vulkan** e rimuoverlo facendo clic sul simbolo **"-"** :</span><span class="sxs-lookup"><span data-stu-id="27bdf-131">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, select **Vulkan** and remove it by clicking the **"-"** symbol:</span></span>

![Area Other Settings di Unity con Vulkan selezionato](images/mr-learning-asa/asa-05-section3-step1-3.png)

[!INCLUDE[](includes/project-setting-for-asa-android.md)]

<span data-ttu-id="27bdf-133">Nella finestra Build Settings (Impostazioni di compilazione) fare clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene nella compilazione).</span><span class="sxs-lookup"><span data-stu-id="27bdf-133">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span> <span data-ttu-id="27bdf-134">Quindi, usare un cavo USB, connettere il dispositivo Android al computer e selezionarlo nell'elenco a discesa **Run Device** (Esegui dispositivo):</span><span class="sxs-lookup"><span data-stu-id="27bdf-134">Then, use a USB cable, connect your Android device to your computer and select it from the **Run Device** dropdown:</span></span>

![Finestra Build Settings di Unity con la scena aggiunta e Run Device selezionato](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> <span data-ttu-id="27bdf-136">Se il dispositivo non è presente nell'elenco a discesa Run Device (Esegui dispositivo), potrebbe essere necessario premere il pulsante Refresh (Aggiorna) accanto all'elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="27bdf-136">If your device does not appear in the Run Device dropdown, you might need to press the Refresh button next to the dropdown.</span></span>

<span data-ttu-id="27bdf-137">Nella finestra delle impostazioni di compilazione fare clic sul pulsante **Build And Run** (Compila ed esegui) per aprire la finestra Build Android (Compila in Android).</span><span class="sxs-lookup"><span data-stu-id="27bdf-137">In the Build Settings window, click the **Build And Run** button to open the Build Android window.</span></span>

<span data-ttu-id="27bdf-138">Scegliere il percorso in cui archiviare la build, ad esempio _D:\MixedRealityLearning\Builds_, quindi assegnare un nome adeguato all'apk, ad esempio _MRTKTutorials-AzureSpatialAnchors_, e fare clic sul pulsante **Save** (Salva) per avviare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="27bdf-138">Choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, then give the apk a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and click the **Save** button to start the build process:</span></span>

![Finestra Build Settings di Unity con la finestra del prompt di salvataggio - Android](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
> <span data-ttu-id="27bdf-140">Se nella finestra della console Unity viene visualizzato un errore relativo ai moduli Android SDK, NDK o JDK, è necessario aprire Unity Hub e installare i moduli Android Build Support associati.</span><span class="sxs-lookup"><span data-stu-id="27bdf-140">If you get any error in the Unity Console window related to Android SDK, NDK, or JDK modules, you need to open Unity Hub and install the associated Android Build Support modules.</span></span>

<span data-ttu-id="27bdf-141">Al termine del processo di compilazione, le app dovrebbero essere caricate automaticamente nel dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="27bdf-141">When the build process is complete, your apps should automatically load on your Android device.</span></span>

## <a name="building-your-application-to-your-ios-device"></a><span data-ttu-id="27bdf-142">Compilazione dell'applicazione in un dispositivo iOS</span><span class="sxs-lookup"><span data-stu-id="27bdf-142">Building your application to your iOS device</span></span>

<span data-ttu-id="27bdf-143">In questa sezione verrà illustrato come configurare il progetto per la compilazione e la distribuzione in un dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="27bdf-143">In this section, you will learn how to configure your project, to build and deploy it to your iOS device.</span></span>

<span data-ttu-id="27bdf-144">Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente e impostare la piattaforma su iOS:</span><span class="sxs-lookup"><span data-stu-id="27bdf-144">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and switch platform to iOS:</span></span>

![Finestra Build Settings di Unity con la piattaforma iOS selezionata](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="27bdf-146">Per rivedere la procedura per cambiare piattaforma di compilazione, fare riferimento alle istruzioni contenute in [Passaggio a un'altra piattaforma di compilazione](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="27bdf-146">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="27bdf-147">Chiudere la finestra Build Settings (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="27bdf-147">Close the Build Settings window.</span></span>

<span data-ttu-id="27bdf-148">Nel menu di Unity seleziona **Mixed Reality** Toolkit Utilities Configure Project for MRTK (Configura progetto per MRTK) per aprire la finestra  >    >    >   **MRTK Project Configurator (Configuratore progetto MRTK),**  verifica che tutte le opzioni siano selezionate e quindi fai clic sul pulsante Apply (Applica) per applicare le impostazioni:</span><span class="sxs-lookup"><span data-stu-id="27bdf-148">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Finestra MRTK Project Configurator di Unity - iOS](images/mr-learning-asa/asa-05-section4-step1-2.png)

[!INCLUDE[](includes/project-setting-for-asa-ios.md)]

<span data-ttu-id="27bdf-150">Dal menu Unity scegliere **Edit** > **Project Settings...** (Modifica > Impostazioni del progetto) per aprire la finestra Player Settings (Impostazioni lettore) e quindi individuare la sezione **Player** >  **Other Settings** (Lettore > Altre impostazioni), deselezionare la casella di controllo **Strip Engine Code** (Rimuovi codice motore) per disabilitarla:</span><span class="sxs-lookup"><span data-stu-id="27bdf-150">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, uncheck the **Strip Engine Code** checkbox to disable it:</span></span>

![Area Other Settings di Unity con l'opzione Strip Engine Code disabilitata](images/mr-learning-asa/asa-05-section4-step1-3.png)

<span data-ttu-id="27bdf-152">Chiudere la finestra Player Settings (Impostazioni lettore) e aprire di nuovo la finestra **Build Settings** (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="27bdf-152">Close the Player Settings window and open the **Build Settings** window again.</span></span>

<span data-ttu-id="27bdf-153">Nella finestra Build Settings (Impostazioni di compilazione) fare clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene nella compilazione):</span><span class="sxs-lookup"><span data-stu-id="27bdf-153">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list:</span></span>

![Finestra Build Settings di Unity con la scena aggiunta](images/mr-learning-asa/asa-05-section4-step1-4.png)

<span data-ttu-id="27bdf-155">Nella finestra delle impostazioni di compilazione fare clic sul pulsante **Build** (Compila) per aprire la finestra Build iOS (Compila in iOS).</span><span class="sxs-lookup"><span data-stu-id="27bdf-155">In the Build Settings window, click the **Build** button to open the Build iOS window.</span></span>

<span data-ttu-id="27bdf-156">Scegliere un percorso appropriato in cui archiviare il progetto Xcode, ad esempio _D:\MixedRealityLearning\Builds_, creare una nuova cartella e assegnarle un nome adatto, ad esempio, _MRTKTutorials-AzureSpatialAnchors_, e quindi fare clic sul pulsante **Select Folder** (Seleziona cartella) per avviare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="27bdf-156">Choose a suitable location to store your Xcode project, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and then click the **Select Folder** button to start the build process:</span></span>

![Finestra Build Settings di Unity con la finestra del prompt di salvataggio - iOS](images/mr-learning-asa/asa-05-section4-step1-5.png)

<span data-ttu-id="27bdf-158">Al termine del processo di compilazione, seguire le istruzioni in [Esportare il progetto Xcode](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) per informazioni su come distribuire il progetto Xcode in un dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="27bdf-158">When the build process is complete, follow the [Export the Xcode project](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) instructions to learn to deploy your Xcode project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="27bdf-159">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="27bdf-159">Congratulations</span></span>

<span data-ttu-id="27bdf-160">In questa esercitazione è stato descritto come compilare il progetto nei dispositivi Android e iOS usando AR Foundation, ARCore XR Plugin e ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="27bdf-160">In this tutorial, you learned how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>
