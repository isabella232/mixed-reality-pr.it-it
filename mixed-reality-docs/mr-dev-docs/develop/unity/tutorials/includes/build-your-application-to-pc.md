---
ms.openlocfilehash: be4a3243bc00f29f992957de0dfa29416c13284d
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392614"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="7cfc4-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="7cfc4-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

### <a name="1-switching-build-platform"></a><span data-ttu-id="7cfc4-102">1. Passaggio alla piattaforma di compilazione</span><span class="sxs-lookup"><span data-stu-id="7cfc4-102">1. Switching Build Platform</span></span>

<span data-ttu-id="7cfc4-103">Dal menu di Unity scegliere File > Build Settings (Impostazioni di compilazione) per visualizzare la finestra corrispondente.</span><span class="sxs-lookup"><span data-stu-id="7cfc4-103">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="7cfc4-104">Nella finestra Build Settings (Impostazioni compilazione) selezionare **PC, Mac & Linux Standalone** Platform (Piattaforma autonoma Linux) e fare clic sul pulsante **Switch Platform** (Cambia piattaforma) per modificare build platform (Piattaforma di compilazione):</span><span class="sxs-lookup"><span data-stu-id="7cfc4-104">In the Build Settings window, select **PC, Mac & Linux Standalone** Platform and click the **Switch Platform** button to change the Build Platform:</span></span>

![Passaggio alla piattaforma di compilazione](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-1.PNG)

<span data-ttu-id="7cfc4-106">Dopo che Unity ha terminato di cambiare piattaforma, fare clic sull'icona x per chiudere la finestra Build Settings (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="7cfc4-106">When Unity has finished switching the platform, click the x icon to close the Build Settings window.</span></span>

### <a name="2-set-the-project-settings"></a><span data-ttu-id="7cfc4-107">2. Impostare le impostazioni del progetto</span><span class="sxs-lookup"><span data-stu-id="7cfc4-107">2. Set the project settings</span></span>

<span data-ttu-id="7cfc4-108">Nel menu di Unity selezionare Edit Project Settings XR Plug-in Management (Modifica impostazioni progetto XR Plug-in Management) assicurarsi di essere nella scheda Windows Standalone e selezionare la casella di controllo  >    >   OpenXR and **Windows Mixed Reality feature set (Set** di funzionalità **openXR** e Windows Mixed Reality).</span><span class="sxs-lookup"><span data-stu-id="7cfc4-108">In the Unity menu, select **Edit** > **Project Settings** > **XR Plug-in Management** ensure that you are in Windows Standalone tab and check the **OpenXR** and **Windows Mixed Reality feature set** checkbox.</span></span>

![Abilitare OpenXR e il set Windows Mixed Reality funzionalità](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-2.PNG)

<span data-ttu-id="7cfc4-110">Nella finestra Project Settings (Impostazioni progetto) selezionare **OpenXR** e assicurarsi di essere nella scheda Windows Standalone e modificare la **modalità di** invio Depth (Profondità) da None (Nessuna) a **Depth 16 Bit (Profondità a 16 bit).**</span><span class="sxs-lookup"><span data-stu-id="7cfc4-110">In Project Settings window, select **OpenXR** and ensure that you are in Windows Standalone tab and change the **Depth submission mode** from None to **Depth 16 Bit**.</span></span>

<span data-ttu-id="7cfc4-111">Nella scheda dei profili di interazione aggiungere il profilo di interazione sguardo **fisso** e il profilo di **interazione con la mano Microsoft** facendo clic sul simbolo +.</span><span class="sxs-lookup"><span data-stu-id="7cfc4-111">In interaction profiles tab add **Eye Gaze Interaction Profile** and **Microsoft Hand Interaction Profile** by clicking on the + symbol.</span></span>

![Aggiungere il profilo di interazione con lo sguardo fisso e il profilo di interazione con la mano Microsoft](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-3.PNG)

<span data-ttu-id="7cfc4-113">In **Open XR feature groups (Apri gruppi** di funzionalità XR) > selezionare la casella di controllo  >   **Holographic App Remoting (Comunicazione remota app Holographic).**</span><span class="sxs-lookup"><span data-stu-id="7cfc4-113">Under **Open XR feature groups** > **All features** > check the **Holographic App Remoting** checkbox.</span></span>

![Abilitare Holographic App Remoting](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-4.PNG)

<span data-ttu-id="7cfc4-115">Selezionare quindi la casella **Windows Mixed Reality** di controllo e nel gruppo Windows Mixed Reality selezionare la casella di controllo **Holographic App Remoting.**</span><span class="sxs-lookup"><span data-stu-id="7cfc4-115">next select the **Windows Mixed Reality**  check box and under Windows Mixed Reality group select the  **Holographic App Remoting** checkbox.</span></span>

![Abilitare la Windows Mixed Reality holographic app remoting](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-5.PNG)

### <a name="3-build-the-unity-project"></a><span data-ttu-id="7cfc4-117">3. Compilare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="7cfc4-117">3. Build the Unity Project</span></span>

<span data-ttu-id="7cfc4-118">Dal menu di Unity scegliere File > Build Settings (Impostazioni di compilazione) per visualizzare la finestra corrispondente.</span><span class="sxs-lookup"><span data-stu-id="7cfc4-118">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="7cfc4-119">Nella finestra Build Settings (Impostazioni di compilazione) fare clic sul pulsante \***Add Open Scenes** _ (Aggiungi scene aperte) per aggiungere la scena corrente alle scene.</span><span class="sxs-lookup"><span data-stu-id="7cfc4-119">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="7cfc4-120">Nell'elenco Compila fare clic sul pulsante _ \*Compila\*\*:</span><span class="sxs-lookup"><span data-stu-id="7cfc4-120">In the Build list, then click the _ *Build*\* button:</span></span>

![Finestra Build Settings di Unity con la scena aggiunta](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-6.PNG)

<span data-ttu-id="7cfc4-122">scegliere un percorso appropriato per archiviare la compilazione, ad esempio Documenti\MixedRealityLearning.</span><span class="sxs-lookup"><span data-stu-id="7cfc4-122">choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="7cfc4-123">Creare una nuova cartella e assegnarle un nome appropriato, ad esempio PCHolographicRemoting.</span><span class="sxs-lookup"><span data-stu-id="7cfc4-123">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="7cfc4-124">Fare quindi clic sul pulsante ***Select Folder*** (Seleziona cartella) per avviare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="7cfc4-124">Then click the ***Select Folder*** button to start the build process:</span></span>

![Finestra Build Settings di Unity con la finestra di prompt Select Folder](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-7.png)

<span data-ttu-id="7cfc4-126">Attendere che Unity completi il processo di compilazione.</span><span class="sxs-lookup"><span data-stu-id="7cfc4-126">Wait for Unity to finish the build process.</span></span>

![Processo di compilazione di Unity in corso](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-8.png)

<span data-ttu-id="7cfc4-128">Fare doppio clic sul file eseguibile per aprire l'applicazione Holographic Remoting del PC nel PC.</span><span class="sxs-lookup"><span data-stu-id="7cfc4-128">double click on the Executable file to open the PC Holographic Remoting Application in your PC.</span></span>

> [!NOTE]
> <span data-ttu-id="7cfc4-129">A causa di alcuni problemi noti nell'app Holographic Remoting per PC compilata come piattaforma UWP, l'app per PC viene compilata come windows autonoma per OpenXR.</span><span class="sxs-lookup"><span data-stu-id="7cfc4-129">Due to some known issues in Holographic Remoting for PC app Built as UWP we are Building the PC App as Windows Standalone for OpenXR.</span></span>


# <a name="legacy-wsa"></a>[<span data-ttu-id="7cfc4-130">Legacy WSA</span><span class="sxs-lookup"><span data-stu-id="7cfc4-130">Legacy WSA</span></span>](#tab/wsa)

### <a name="1-set-the-player-settings"></a><span data-ttu-id="7cfc4-131">1. Configurare le impostazioni del lettore</span><span class="sxs-lookup"><span data-stu-id="7cfc4-131">1. Set the player settings</span></span>

<span data-ttu-id="7cfc4-132">Nella sezione **XR Settings** (Impostazioni XR) selezionare la casella di controllo **WSA Holographic Remoting Supported** e abilitare Holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="7cfc4-132">In the **XR Settings** section, select the **WSA Holographic Remoting Supported** checkbox and enable the Holographic Remoting.</span></span>

![Finestra XR Settings di Unity con l'opzione WSA Holographic Remoting Supported abilitata](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a><span data-ttu-id="7cfc4-134">2. Compilare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="7cfc4-134">2. Build the Unity Project</span></span>

<span data-ttu-id="7cfc4-135">Dal menu di Unity scegliere File > Build Settings (Impostazioni di compilazione) per visualizzare la finestra corrispondente.</span><span class="sxs-lookup"><span data-stu-id="7cfc4-135">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="7cfc4-136">Nella finestra Build Settings (Impostazioni di compilazione) fare clic sul pulsante \***Add Open Scenes** _ (Aggiungi scene aperte) per aggiungere la scena corrente alle scene.</span><span class="sxs-lookup"><span data-stu-id="7cfc4-136">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="7cfc4-137">Nell'elenco Compila fare clic sul pulsante _ *_Compila_*\* per aprire la finestra Piattaforma UWP (Universal Windows Platform) compilazione:</span><span class="sxs-lookup"><span data-stu-id="7cfc4-137">In the Build list, then click the _ *_Build button_*\* to open the Build Universal Windows Platform window:</span></span>

![Finestra Build Settings di Unity con la scena aggiunta](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

<span data-ttu-id="7cfc4-139">Nella finestra Build Universal Windows Platform (Compilazione UWP) scegliere un percorso adatto per archiviare la compilazione, ad esempio Documenti\MixedRealityLearning.</span><span class="sxs-lookup"><span data-stu-id="7cfc4-139">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="7cfc4-140">Creare una nuova cartella e assegnarle un nome appropriato, ad esempio PCHolographicRemoting.</span><span class="sxs-lookup"><span data-stu-id="7cfc4-140">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="7cfc4-141">Fare quindi clic sul pulsante ***Select Folder*** (Seleziona cartella) per avviare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="7cfc4-141">Then click the ***Select Folder*** button to start the build process:</span></span>

![Finestra Build Settings di Unity con la finestra di prompt Select Folder](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

<span data-ttu-id="7cfc4-143">Attendere che Unity completi il processo di compilazione.</span><span class="sxs-lookup"><span data-stu-id="7cfc4-143">Wait for Unity to finish the build process.</span></span>

![Processo di compilazione di Unity in corso](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a><span data-ttu-id="7cfc4-145">3. Compilare e distribuire l'applicazione</span><span class="sxs-lookup"><span data-stu-id="7cfc4-145">3. Build and deploy the application</span></span>

<span data-ttu-id="7cfc4-146">Al termine del processo di compilazione, Unity richiederà a Esplora file di Windows di aprire il percorso in cui è stata archiviata la compilazione.</span><span class="sxs-lookup"><span data-stu-id="7cfc4-146">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="7cfc4-147">Spostarsi all'interno della cartella e fare doppio clic sul file con estensione sln per aprirlo in Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="7cfc4-147">Navigate inside the folder, and double-click the .sln file to open it in Visual Studio:</span></span>

![Esplora risorse con la soluzione di Visual Studio appena creata selezionata](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> <span data-ttu-id="7cfc4-149">Se Visual Studio chiede di installare nuovi componenti, dedicare qualche minuto a verificare che siano installati tutti i componenti indispensabili, come specificato nell'argomento Installare gli strumenti.</span><span class="sxs-lookup"><span data-stu-id="7cfc4-149">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the Install the Tools documentation.</span></span>

<span data-ttu-id="7cfc4-150">Configurare Visual Studio per PC selezionando la configurazione Release, l'architettura x64 e Local Machine (Computer locale) come destinazione:</span><span class="sxs-lookup"><span data-stu-id="7cfc4-150">Configure Visual Studio for PC by selecting the Release configuration, the x64 architecture, and Local Machine as target:</span></span>

![Visual Studio configurato per Computer locale](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

<span data-ttu-id="7cfc4-152">Fare clic sul pulsante ***Local Machine*** (Computer locale).</span><span class="sxs-lookup"><span data-stu-id="7cfc4-152">Click the button that says ***Local Machine***.</span></span> <span data-ttu-id="7cfc4-153">Viene avviata la compilazione e la distribuzione dell'applicazione nel PC.</span><span class="sxs-lookup"><span data-stu-id="7cfc4-153">It starts to build and deploy the application on to your PC.</span></span> <span data-ttu-id="7cfc4-154">L'applicazione verrà installata nel PC per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="7cfc4-154">The application will be installed in your PC by default.</span></span>
