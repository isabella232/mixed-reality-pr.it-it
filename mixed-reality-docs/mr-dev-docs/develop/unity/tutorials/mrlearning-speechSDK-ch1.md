---
title: Esercitazioni sui servizi vocali di Azure - 1. Integrazione e uso del riconoscimento vocale e della trascrizione
description: Completa questo corso per imparare a implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure, riconoscimento vocale, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 020c88bb7a872f11b5802b55e14201f4f60edb8d
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403392"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="276cb-105">1. Integrazione e uso del riconoscimento vocale e della trascrizione</span><span class="sxs-lookup"><span data-stu-id="276cb-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="276cb-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="276cb-106">Overview</span></span>

<span data-ttu-id="276cb-107">In questa serie di esercitazioni creerai un'applicazione di Realtà mista per esplorare l'uso dei servizi vocali di Azure con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="276cb-107">In this tutorial series, you will create a Mixed Reality application that explores the use of Azure Speech Services with the HoloLens 2.</span></span> <span data-ttu-id="276cb-108">Al termine di questa serie di esercitazioni, sarai in grado di usare il microfono del tuo dispositivo per trascrivere il parlato in testo in tempo reale, tradurre il parlato in altre lingue e utilizzare la funzionalità Riconoscimento finalità per comprendere i comandi vocali usando l'intelligenza artificiale.</span><span class="sxs-lookup"><span data-stu-id="276cb-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Intent recognition feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="276cb-109">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="276cb-109">Objectives</span></span>

* <span data-ttu-id="276cb-110">Imparare a integrare i servizi vocali di Azure con un'applicazione HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="276cb-110">Learn how to integrate Azure Speech Services with a HoloLens 2 application</span></span>
* <span data-ttu-id="276cb-111">Imparare a usare il riconoscimento vocale per trascrivere testo</span><span class="sxs-lookup"><span data-stu-id="276cb-111">Learn how to use speech recognition to transcribe text</span></span>

## <a name="prerequisites"></a><span data-ttu-id="276cb-112">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="276cb-112">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="276cb-113">Se non hai ancora completato la serie di [Esercitazioni introduttive](mr-learning-base-01.md), è consigliabile completare prima queste esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="276cb-113">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="276cb-114">Un PC Windows 10 configurato in cui siano [installati gli strumenti](../../install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="276cb-114">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="276cb-115">Windows 10 SDK 10.0.18362.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="276cb-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="276cb-116">Alcune funzionalità di programmazione C# di base</span><span class="sxs-lookup"><span data-stu-id="276cb-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="276cb-117">Un dispositivo HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="276cb-117">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="276cb-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2020/2019 LTS installato e il modulo piattaforma UWP (Universal Windows Platform) Build Support aggiunto</span><span class="sxs-lookup"><span data-stu-id="276cb-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020/2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!Important]
> <span data-ttu-id="276cb-119">Questa serie di esercitazioni supporta Unity 2020 LTS (attualmente 2020.3.x) se si usa Open XR o Windows XR Plugin e anche Unity 2019 LTS (attualmente 2019.4.x) se si usa WSA legacy o Windows XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="276cb-119">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA or Windows XR Plugin.</span></span> <span data-ttu-id="276cb-120">Questa istruzione sostituisce gli eventuali requisiti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.</span><span class="sxs-lookup"><span data-stu-id="276cb-120">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="276cb-121">Creazione e preparazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="276cb-121">Creating and preparing the Unity project</span></span>

<span data-ttu-id="276cb-122">In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="276cb-122">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="276cb-123">A questo scopo, segui prima l'esercitazione [Inizializzazione del progetto e prima applicazione](mr-learning-base-02.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), che include i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="276cb-123">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="276cb-124">[Creazione del progetto Unity](mr-learning-base-02.md#creating-the-unity-project) e assegnazione di un nome appropriato, ad esempio *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="276cb-124">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="276cb-125">Passaggio a un'altra piattaforma di compilazione</span><span class="sxs-lookup"><span data-stu-id="276cb-125">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="276cb-126">Importazione delle risorse essenziali TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="276cb-126">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="276cb-127">Importazione di Mixed Reality Toolkit e configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="276cb-127">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="276cb-128">[Creazione e configurazione della scena](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) e assegnazione di un nome appropriato, ad esempio *AzureSpeechServices*</span><span class="sxs-lookup"><span data-stu-id="276cb-128">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *AzureSpeechServices*</span></span>

<span data-ttu-id="276cb-129">Segui quindi [](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) le istruzioni riportate in Modifica dell'opzione di visualizzazione della consapevolezza spaziale per assicurarti che il profilo di configurazione di MRTK per la scena sia **DefaultHoloLens2ConfigurationProfile** e modifica le opzioni di visualizzazione per la mesh di consapevolezza spaziale in **Occlusion**.</span><span class="sxs-lookup"><span data-stu-id="276cb-129">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile**  and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="configuring-the-speech-commands-start-behavior"></a><span data-ttu-id="276cb-130">Configurazione del comportamento di avvio dei comandi vocali</span><span class="sxs-lookup"><span data-stu-id="276cb-130">Configuring the speech commands start behavior</span></span>

<span data-ttu-id="276cb-131">Poiché userai Speech SDK per il riconoscimento vocale e la trascrizione, devi configurare i comandi vocali di MRTK in modo che non interferiscano con le funzionalità di Speech SDK.</span><span class="sxs-lookup"><span data-stu-id="276cb-131">Because you will use the Speech SDK for speech recognition and transcription you need to configure the MRTK Speech Commands so they do not interfere with the Speech SDK functionality.</span></span> <span data-ttu-id="276cb-132">A tale scopo, puoi modificare il comportamento di avvio dei comandi vocali da Auto Start (Avvio automatico) a Manual Start (Avvio manuale).</span><span class="sxs-lookup"><span data-stu-id="276cb-132">To achieve this you can change the speech commands start behavior from Auto Start to Manual Start.</span></span>

<span data-ttu-id="276cb-133">Con l'oggetto **MixedRealityToolkit** selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) seleziona la scheda **Input**, clona **DefaultHoloLens2InputSystemProfile** e **DefaultMixedRealitySpeechCommandsProfile** e quindi modifica i comandi vocali di **Start Behavior** (Comportamento di avvio) in **Manual Start** (Avvio manuale):</span><span class="sxs-lookup"><span data-stu-id="276cb-133">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, select the **Input** tab, clone the **DefaultHoloLens2InputSystemProfile** and the **DefaultMixedRealitySpeechCommandsProfile**, and then change the speech commands **Start Behavior** to **Manual Start**:</span></span>

![mrlearning-speech 1](images/mrlearning-speech/tutorial1-section2-step1-1.png)

## <a name="configuring-the-capabilities"></a><span data-ttu-id="276cb-135">Configurazione delle funzionalità</span><span class="sxs-lookup"><span data-stu-id="276cb-135">Configuring the capabilities</span></span>

<span data-ttu-id="276cb-136">Dal menu Unity scegli **Edit** > **Project Settings...** (Modifica > Impostazioni del progetto) per aprire la finestra Project Settings (Impostazioni del progetto) e quindi individua la sezione **Player** >  **Publishing Settings** (Lettore > Impostazioni di pubblicazione):</span><span class="sxs-lookup"><span data-stu-id="276cb-136">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-speech 2](images/mrlearning-speech/tutorial1-section3-step1-1.png)

<span data-ttu-id="276cb-138">Nelle impostazioni di pubblicazione scorrere  verso il basso fino alla sezione Capabilities (Funzionalità) e verificare che le funzionalità **InternetClient**, **Microphone** e **SpatialPerception,** abilitate al momento della creazione del progetto all'inizio dell'esercitazione, siano abilitate.</span><span class="sxs-lookup"><span data-stu-id="276cb-138">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which was enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="276cb-139">Abilita quindi le funzionalità **InternetClientServer** e **PrivateNetworkClientServer**:</span><span class="sxs-lookup"><span data-stu-id="276cb-139">Then, enable the **InternetClientServer** and **PrivateNetworkClientServer** capabilities:</span></span>

![mrlearning-speech 3](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="276cb-141">Importazione degli asset dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="276cb-141">Importing the tutorial assets</span></span>

<span data-ttu-id="276cb-142">Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:</span><span class="sxs-lookup"><span data-stu-id="276cb-142">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="276cb-143">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (versione più recente)</span><span class="sxs-lookup"><span data-stu-id="276cb-143">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)</span></span>
* [<span data-ttu-id="276cb-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="276cb-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="276cb-145">MRTK. HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="276cb-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage</span></span>](https://github.com/onginnovations/MixedRealityLearning/releases/download/azure-speech-services-v2.5.2/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage)

> [!TIP]
> <span data-ttu-id="276cb-146">Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, è possibile fare riferimento alle istruzioni riportate in [Importazione di Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-tutorial-assets).</span><span class="sxs-lookup"><span data-stu-id="276cb-146">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-tutorial-assets) instructions.</span></span>

<span data-ttu-id="276cb-147">Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="276cb-147">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-speech 4](images/mrlearning-speech/tutorial1-section4-step1-1.png)

<span data-ttu-id="276cb-149">È necessario configurare il progetto Unity per pubblicare i plug-in di Riconoscimento vocale di Azure per ARM64. A tale scopo, nella finestra Project (Progetto) passare ad  >  **Assets SpeechSDK** Plugins (Plug-in SpeechSDK)  >    >  **WSA** ARM64 e selezionare  >   **Microsoft.CognitiveServices.Speech.core plugin (Plug-in Microsoft.CognitiveServices.Speech.core).**</span><span class="sxs-lookup"><span data-stu-id="276cb-149">You need to setup the Unity project to publish the Azure Speech plugins for ARM64,to do this in the Project window, navigate to **Assets** > **SpeechSDK** > **Plugins** > **WSA** > **ARM64** and select **Microsoft.CognitiveServices.Speech.core** plugin.</span></span>

![mrlearning-speech 5](images/mrlearning-speech/tutorial1-section4-step1-2.PNG)

<span data-ttu-id="276cb-151">Con il **plug-in Microsoft.CognitiveServices.Speech.core** ancora selezionato, nella  finestra di controllo abilitare **WSA Player,** quindi in Impostazioni piattaforma selezionare **UWP** per SDK, **ARM64** per la CPU e fare clic su Applica per applicare queste impostazioni al plug-in.</span><span class="sxs-lookup"><span data-stu-id="276cb-151">with **Microsoft.CognitiveServices.Speech.core** plugin still selected, in the inspector window Enable **WSA Player** then under **Platform settings** select **UWP** for SDK, **ARM64** for CPU and click on Apply to apply these settings to the plugin.</span></span>

![mrlearning-speech 6](images/mrlearning-speech/tutorial1-section4-step1-3.PNG)

<span data-ttu-id="276cb-153">Ripetere questa procedura per ognuno dei plug-in rimanenti:</span><span class="sxs-lookup"><span data-stu-id="276cb-153">Repeat this steps for each of the remaining plugins:</span></span>

* <span data-ttu-id="276cb-154">**Microsoft.CognitiveServices.Speech.extension.audio.sys**</span><span class="sxs-lookup"><span data-stu-id="276cb-154">**Microsoft.CognitiveServices.Speech.extension.audio.sys**</span></span>
* <span data-ttu-id="276cb-155">**Microsoft.CognitiveServices.Speech.extension.kws**</span><span class="sxs-lookup"><span data-stu-id="276cb-155">**Microsoft.CognitiveServices.Speech.extension.kws**</span></span>
* <span data-ttu-id="276cb-156">**Microsoft.CognitiveServices.Speech.extension.lu**</span><span class="sxs-lookup"><span data-stu-id="276cb-156">**Microsoft.CognitiveServices.Speech.extension.lu**</span></span>
* <span data-ttu-id="276cb-157">**Microsoft.CognitiveServices.Speech.extension.silk_codec**</span><span class="sxs-lookup"><span data-stu-id="276cb-157">**Microsoft.CognitiveServices.Speech.extension.silk_codec**</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="276cb-158">Preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="276cb-158">Preparing the scene</span></span>

<span data-ttu-id="276cb-159">In questa sezione preparerai la scena aggiungendo il prefab dell'esercitazione e configurerai il componente Lunarcom Controller (Script) (Controller Lunarcom - Script) per il controllo della scena.</span><span class="sxs-lookup"><span data-stu-id="276cb-159">In this section, you will prepare the scene by adding the tutorial prefab and configure the Lunarcom Controller (Script) component to control your scene.</span></span>

<span data-ttu-id="276cb-160">Nella finestra Project (Progetto) passa ad **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** (Asset > MRTK.Tutorials.AzureSpeechServices > Prefab) e trascina il prefab **Lunarcom** nella finestra Hierarchy (Gerarchia) per aggiungerlo alla scena:</span><span class="sxs-lookup"><span data-stu-id="276cb-160">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** folder and drag the **Lunarcom** prefab into the Hierarchy window to add it to your scene:</span></span>

![mrlearning-speech 7](images/mrlearning-speech/tutorial1-section5-step1-1.png)

<span data-ttu-id="276cb-162">Con l'oggetto **Lunarcom** ancora selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Lunarcom Controller (Script)** (Controller Lunarcom - Script) all'oggetto Lunarcom:</span><span class="sxs-lookup"><span data-stu-id="276cb-162">With the **Lunarcom** object still selected in the Hierarchy window, in the Inspector window, use the **Add Component** button to add the **Lunarcom Controller (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech 8](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> <span data-ttu-id="276cb-164">Il componente Lunarcom Controller (Script) (Controller Lunarcom - Script) non fa parte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="276cb-164">The Lunarcom Controller (Script) component is not part of MRTK.</span></span> <span data-ttu-id="276cb-165">È stato fornito con gli asset dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="276cb-165">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="276cb-166">Con l'oggetto **Lunarcom** ancora selezionato, espandi l'oggetto in modo da visualizzarne gli oggetti figlio e quindi trascina l'oggetto **Terminal** nel campo **Terminal** (Terminale) del componente Lunarcom Controller (Script) (Controller Lunarcom - Script):</span><span class="sxs-lookup"><span data-stu-id="276cb-166">With the **Lunarcom** object still selected, expand it to reveal its child objects, then drag the **Terminal** object into the Lunarcom Controller (Script) component's **Terminal** field:</span></span>

![mrlearning-speech 9](images/mrlearning-speech/tutorial1-section5-step1-3.png)

<span data-ttu-id="276cb-168">Con l'oggetto **Lunarcom** ancora selezionato, espandi l'oggetto Terminal in modo da visualizzarne gli oggetti figlio e quindi trascina l'oggetto **ConnectionLight** nel campo **Connection Light** (Luce di connessione) e l'oggetto **OutputText** nel campo **Output Text** (Testo di output) del componente Lunarcom Controller (Script) (Controller Lunarcom - Script):</span><span class="sxs-lookup"><span data-stu-id="276cb-168">With the **Lunarcom** object still selected, expand the Terminal object to reveal its child objects, then drag the **ConnectionLight** object into the Lunarcom Controller (Script) component's **Connection Light** field and the **OutputText** object into the **Output Text** field:</span></span>

![mrlearning-speech 10](images/mrlearning-speech/tutorial1-section5-step1-4.png)

<span data-ttu-id="276cb-170">Con l'oggetto **Lunarcom** ancora selezionato, espandi l'oggetto Buttons per visualizzarne gli oggetti figlio e quindi nella finestra Inspector (Controllo) espandi l'elenco **Buttons** (Pulsanti), imposta **Size** (Dimensioni) su 3 e trascina gli oggetti **MicButton**, **SatelliteButton** e **RocketButton** rispettivamente nei campi **Element** (Elemento) 0, 1 e 2:</span><span class="sxs-lookup"><span data-stu-id="276cb-170">With the **Lunarcom** object still selected, expand the Buttons object to reveal its child objects, and then in the Inspector window, expand the **Buttons** list, set its **Size** to 3, and drag the **MicButton**, **SatelliteButton**, and **RocketButton** objects into the **Element** 0, 1, and 2 fields respectively:</span></span>

![mrlearning-speech 11](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a><span data-ttu-id="276cb-172">Connessione del progetto Unity alla risorsa di Azure</span><span class="sxs-lookup"><span data-stu-id="276cb-172">Connecting the Unity project to the Azure resource</span></span>

<span data-ttu-id="276cb-173">Per usare i servizi vocali di Azure, devi creare una risorsa di Azure e ottenere una chiave API per il servizio vocale.</span><span class="sxs-lookup"><span data-stu-id="276cb-173">To use Azure Speech Services, you need to create an Azure resource and obtain an API key for the Speech Service.</span></span> <span data-ttu-id="276cb-174">Segui le istruzioni contenute in [Provare gratuitamente il servizio Voce](/azure/cognitive-services/speech-service/get-started) e prendi nota dell'area geografica del servizio, (definita anche posizione) e della chiave API (definita anche Key1 o Key2).</span><span class="sxs-lookup"><span data-stu-id="276cb-174">Follow the [Try the Speech service for free](/azure/cognitive-services/speech-service/get-started) instructions and make a note of your service region (also known as Location) and API key (also known as Key1 or Key2).</span></span>

<span data-ttu-id="276cb-175">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom** e quindi nella finestra Inspector (Controllo) individua la sezione **Speech SDK Credentials** (Credenziali Speech SDK) del componente **Lunarcom Controller (Script)** (Controller Lunarcom - Script) e configurala come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="276cb-175">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Controller (Script)** component's **Speech SDK Credentials** section and configure it as follows:</span></span>

* <span data-ttu-id="276cb-176">Nel campo **Speech Service API Key** (Chiave API servizio vocale) immetti la chiave API (Key1 o Key2)</span><span class="sxs-lookup"><span data-stu-id="276cb-176">In the **Speech Service API Key** field, enter your API key (Key1 or Key2)</span></span>
* <span data-ttu-id="276cb-177">Nel campo **Speech Service Region** (Area del servizio vocale) immetti l'area geografica del servizio (posizione) usando lettere minuscole e rimuovendo gli spazi</span><span class="sxs-lookup"><span data-stu-id="276cb-177">In the **Speech Service Region** field, enter your service region (Location) using lowercase letters and spaces removed</span></span>

![mrlearning-speech 12](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a><span data-ttu-id="276cb-179">Uso del riconoscimento vocale per la trascrizione di testo</span><span class="sxs-lookup"><span data-stu-id="276cb-179">Using speech recognition to transcribe speech</span></span>

<span data-ttu-id="276cb-180">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom** e quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Lunarcom Speech Recognizer (Script)** (Riconoscimento vocale Lunarcom - Script) all'oggetto Lunarcom:</span><span class="sxs-lookup"><span data-stu-id="276cb-180">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Speech Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech 13](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> <span data-ttu-id="276cb-182">Il componente Lunarcom Speech Recognizer (Script) (Riconoscimento vocale Lunarcom - Script) non fa parte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="276cb-182">The Lunarcom Speech Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="276cb-183">È stato fornito con gli asset dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="276cb-183">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="276cb-184">Se ora attivi la modalità gioco, puoi testare il riconoscimento vocale selezionando prima il pulsante del microfono:</span><span class="sxs-lookup"><span data-stu-id="276cb-184">If you now enter Game mode, you can test the speech recognition by first pressing the microphone button:</span></span>

![mrlearning-speech 14](images/mrlearning-speech/tutorial1-section7-step1-2.png)

<span data-ttu-id="276cb-186">Supponendo quindi che il computer disponga di un microfono, quando pronunci una frase, questa verrà trascritta nel pannello del terminale:</span><span class="sxs-lookup"><span data-stu-id="276cb-186">Then, assuming your computer has a microphone, when you say something, your speech will be transcribed on the terminal panel:</span></span>

![mrlearning-speech 15](images/mrlearning-speech/tutorial1-section7-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="276cb-188">Poiché l'applicazione deve connettersi ad Azure, assicurati che il computer o il dispositivo sia connesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="276cb-188">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="276cb-189">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="276cb-189">Congratulations</span></span>

<span data-ttu-id="276cb-190">Hai implementato il riconoscimento vocale basato su Azure.</span><span class="sxs-lookup"><span data-stu-id="276cb-190">You have implemented speech recognition powered by Azure.</span></span> <span data-ttu-id="276cb-191">Esegui l'applicazione nel dispositivo per verificare che la funzionalità venga eseguita correttamente.</span><span class="sxs-lookup"><span data-stu-id="276cb-191">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="276cb-192">Nell'esercitazione successiva apprenderai come eseguire i comandi con il riconoscimento vocale di Azure.</span><span class="sxs-lookup"><span data-stu-id="276cb-192">In the next tutorial, you will learn how to execute commands using Azure speech recognition.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="276cb-193">Esercitazione successiva: 2. Uso del riconoscimento vocale per l'esecuzione di comandi</span><span class="sxs-lookup"><span data-stu-id="276cb-193">Next tutorial: 2. Using speech recognition to execute commands</span></span>](mrlearning-speechSDK-ch2.md)
