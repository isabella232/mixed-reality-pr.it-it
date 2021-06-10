---
title: Modalità di gioco Unity
description: Informazioni su come usare la modalità di riproduzione nell'editor di Unity per visualizzare in anteprima le modifiche dell'applicazione in un dispositivo senza distribuire un'app.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, comunicazione remota, comunicazione remota olografica, lettore di comunicazione remota olografica, HoloLens, visore per realtà mista, visore windows mixed reality, visore di realtà virtuale, modalità di gioco unity
ms.openlocfilehash: caa9d7bf11104ee168fda24fc369de490feb7817
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547102"
---
# <a name="unity-play-mode"></a><span data-ttu-id="bb70c-104">Modalità di gioco Unity</span><span class="sxs-lookup"><span data-stu-id="bb70c-104">Unity Play Mode</span></span>

<span data-ttu-id="bb70c-105">Un modo rapido per lavorare al progetto Unity è usare la "modalità di riproduzione", che esegue l'app in locale nell'editor di Unity nel PC.</span><span class="sxs-lookup"><span data-stu-id="bb70c-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="bb70c-106">Unity usa Holographic Remoting per offrire un modo rapido per visualizzare in anteprima il contenuto in un dispositivo HoloLens reale.</span><span class="sxs-lookup"><span data-stu-id="bb70c-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="bb70c-107">La modalità di riproduzione può essere usata anche con Windows Mixed Reality visore collegato al PC di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="bb70c-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="bb70c-108">Configurazione della comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="bb70c-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="bb70c-109">Prima di tutto, è [necessario installare l'app Holographic Remoting Player](https://www.microsoft.com/store/productId/9NBLGGH4SV40) dal Microsoft Store nel HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="bb70c-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="bb70c-110">Eseguire l'app Holographic Remoting Player HoloLens 2 e verranno visualizzati il numero di versione e l'indirizzo IP a cui connettersi</span><span class="sxs-lookup"><span data-stu-id="bb70c-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="bb70c-111">Per usare il plug-in OpenXR è necessaria la versione 2.4 o successiva</span><span class="sxs-lookup"><span data-stu-id="bb70c-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Screenshot di Holographic Remoting Player in esecuzione in HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="bb70c-113">Comunicazione remota olografica in modalità di riproduzione dell'editor unity</span><span class="sxs-lookup"><span data-stu-id="bb70c-113">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="bb70c-114">La compilazione di un progetto Unity UWP Visual Studio progetto e quindi la creazione del pacchetto e la distribuzione in un dispositivo HoloLens 2 può richiedere del tempo.</span><span class="sxs-lookup"><span data-stu-id="bb70c-114">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="bb70c-115">Una soluzione consiste nell'abilitare la funzionalità comunicazione remota di Holographic Editor, che consente di eseguire il debug dello script C# usando la modalità "Play" direttamente in un dispositivo HoloLens 2 rete.</span><span class="sxs-lookup"><span data-stu-id="bb70c-115">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="bb70c-116">Questo scenario evita il sovraccarico della compilazione e della distribuzione di un pacchetto UWP nel dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="bb70c-116">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="bb70c-117">Seguire la procedura descritta in [Holographic Remoting setup (Configurazione di Holographic Remoting)](#holographic-remoting-setup)</span><span class="sxs-lookup"><span data-stu-id="bb70c-117">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="bb70c-118">Aprire Windows > XR > comunicazione remota **dell'editor OpenXR:**</span><span class="sxs-lookup"><span data-stu-id="bb70c-118">Open **Windows > XR > OpenXR Editor Remoting**:</span></span>

    ![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con la gestione dei plug-in XR evidenziata](images/openxr-features-img-02.png)

3. <span data-ttu-id="bb70c-120">Immettere l'indirizzo IP che si ottiene dall'app Holographic Remoting e selezionare Abilita comunicazione remota **dell'editor**</span><span class="sxs-lookup"><span data-stu-id="bb70c-120">Input the IP address you get from the Holographic Remoting app, and select **Enable Editor Remoting**</span></span>

    ![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con funzionalità evidenziate](images/openxr-features-img-03.png)

<span data-ttu-id="bb70c-122">È ora possibile fare clic sul pulsante "Play" (Riproduci) per riprodurre l'app Unity nell'app Holographic Remoting in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="bb70c-122">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="bb70c-123">È anche possibile [collegare Visual Studio a Unity per](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) eseguire il debug di script C# in modalità di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="bb70c-123">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="bb70c-124">A causa della versione 0.1.0, il runtime di Holographic Remoting non supporta ancoraggi e le funzionalità di ARAnchorManager non funzioneranno tramite la comunicazione remota.</span><span class="sxs-lookup"><span data-stu-id="bb70c-124">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="bb70c-125">Questa funzionalità sarà disponibile nelle versioni future.</span><span class="sxs-lookup"><span data-stu-id="bb70c-125">This feature is coming in future releases.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="bb70c-126">Modalità di riproduzione Unity con Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="bb70c-126">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="bb70c-127">Con Holographic Remoting è possibile sperimentare l'app in HoloLens mentre viene eseguita nell'editor unity nel PC.</span><span class="sxs-lookup"><span data-stu-id="bb70c-127">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="bb70c-128">Lo sguardo, il movimento, la voce e l'input di mapping spaziale vengono inviati dal dispositivo HoloLens al PC.</span><span class="sxs-lookup"><span data-stu-id="bb70c-128">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="bb70c-129">I fotogrammi sottoposti a rendering vengono quindi inviati nuovamente a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="bb70c-129">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="bb70c-130">Questo è un ottimo modo per eseguire rapidamente il debug dell'app senza compilare e distribuire un progetto completo.</span><span class="sxs-lookup"><span data-stu-id="bb70c-130">This is a great way to quickly debug your app without building and deploying a full project.</span></span>

[!INCLUDE[](includes/unity-play-mode.md)]

<span data-ttu-id="bb70c-131">Holographic Remoting richiede un PC veloce e Wi-Fi connessione.</span><span class="sxs-lookup"><span data-stu-id="bb70c-131">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="bb70c-132">Per altri dettagli, vedere la documentazione [di Holographic Remoting Player.](../platform-capabilities-and-apis/holographic-remoting-player.md)</span><span class="sxs-lookup"><span data-stu-id="bb70c-132">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="bb70c-133">Per ottenere risultati ottimali, assicurarsi che l'app imposta correttamente il [punto di attivazione.](focus-point-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="bb70c-133">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="bb70c-134">Ciò consente a Holographic Remoting di adattare al meglio la scena alla latenza della connessione wireless.</span><span class="sxs-lookup"><span data-stu-id="bb70c-134">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb70c-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bb70c-135">See Also</span></span>

* [<span data-ttu-id="bb70c-136">Holographic Remoting Player</span><span class="sxs-lookup"><span data-stu-id="bb70c-136">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
