---
title: Audio spaziale in Unreal
description: Informazioni sui vantaggi e sugli svantaggi del plug-in di audio spaziale per Unreal Engine.
author: hferrone
ms.author: v-hferrone
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, comunicazione remota, realtà mista, sviluppo, guida introduttiva, funzionalità, nuovo progetto, emulatore, documentazione, guide, caratteristiche, ologrammi, sviluppo di giochi, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, audio spaziale
ms.openlocfilehash: 25fa60b4e55ec0f3bd0875ad88834981d198f7f5
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679800"
---
# <a name="spatial-audio-in-unreal"></a><span data-ttu-id="66abf-104">Audio spaziale in Unreal</span><span class="sxs-lookup"><span data-stu-id="66abf-104">Spatial Audio in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="66abf-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="66abf-105">Overview</span></span>

<span data-ttu-id="66abf-106">Diversamente dalla vista, gli umani sentono un suono surround a 360 gradi.</span><span class="sxs-lookup"><span data-stu-id="66abf-106">Unlike vision, humans hear in 360 degree surround sound.</span></span> <span data-ttu-id="66abf-107">L'audio spaziale emula il funzionamento dell'udito umano, fornendo i segnali necessari per identificare le posizioni del suono nello spazio mondo.</span><span class="sxs-lookup"><span data-stu-id="66abf-107">Spatial sound emulates how human hearing works, providing the cues needed to identify sound locations in world-space.</span></span> <span data-ttu-id="66abf-108">L'aggiunta dell'audio spaziale nelle applicazioni di realtà mista consente di migliorare il livello di immersione dell'esperienza degli utenti.</span><span class="sxs-lookup"><span data-stu-id="66abf-108">When you add spatial sound in your mixed reality applications, you're enhancing the level of immersion your users experience.</span></span>  

<span data-ttu-id="66abf-109">Dato che l'elaborazione dell'audio spaziale di qualità elevata è un'attività complessa, HoloLens 2 è dotato di un hardware dedicato per l'elaborazione di tali oggetti audio.</span><span class="sxs-lookup"><span data-stu-id="66abf-109">High quality spatial sound processing is complex, so the HoloLens 2 comes with dedicated hardware for processing those sound objects.</span></span>  <span data-ttu-id="66abf-110">Prima di poter accedere a questo supporto dell'elaborazione hardware, è necessario installare il plug-in **MicrosoftSpatialSound** nel progetto Unreal.</span><span class="sxs-lookup"><span data-stu-id="66abf-110">Before you can access this hardware processing support, you'll need to install the **MicrosoftSpatialSound** plugin in your Unreal project.</span></span> <span data-ttu-id="66abf-111">Questo articolo illustra come installare e configurare quel plug-in e suggerisce alcune risorse di approfondimento per l'uso dell'audio spaziale nel motore Unreal.</span><span class="sxs-lookup"><span data-stu-id="66abf-111">This article will walk you through the installation and configuration of that plugin and point you towards more in-depth resources for using spatial sound in the Unreal engine.</span></span>

## <a name="installing-the-microsoft-spatial-sound-plugin"></a><span data-ttu-id="66abf-112">Installazione del plug-in Microsoft Spatial Sound</span><span class="sxs-lookup"><span data-stu-id="66abf-112">Installing the Microsoft Spatial Sound plugin</span></span>

<span data-ttu-id="66abf-113">Per aggiungere l'audio spaziale a un progetto, prima di tutto è necessario installare il plug-in Microsoft Spatial Sound. Per trovarlo, procedi in questo modo:</span><span class="sxs-lookup"><span data-stu-id="66abf-113">The first step to adding spatial sound to your project is installing the Microsoft Spatial Sound plugin, which you can find by:</span></span>

1. <span data-ttu-id="66abf-114">Fai clic su **Edit > Plugins** (Modifica > Plug-in) e immetti **MicrosoftSpatialSound** nella casella di ricerca.</span><span class="sxs-lookup"><span data-stu-id="66abf-114">Clicking **Edit > Plugins** and searching for **MicrosoftSpatialSound** in the search box.</span></span>
2. <span data-ttu-id="66abf-115">Seleziona la casella di controllo **Enabled** (Abilitato) nel plug-in **MicrosoftSpatialSound**.</span><span class="sxs-lookup"><span data-stu-id="66abf-115">Selecting the **Enabled** checkbox in the **MicrosoftSpatialSound** plugin.</span></span>
3. <span data-ttu-id="66abf-116">Riavvia Unreal Editor selezionando **Restart Now** (Riavvia ora) nella pagina dei plug-in.</span><span class="sxs-lookup"><span data-stu-id="66abf-116">Restarting the Unreal Editor by selecting **Restart Now** from the plugins page.</span></span>

> [!NOTE]
> <span data-ttu-id="66abf-117">Se non l'hai già fatto, devi installare i plug-in **Microsoft Windows Mixed Reality** e **HoloLens** seguendo le istruzioni riportate nella sezione relativa all' **[inizializzazione del progetto](tutorials/unreal-uxt-ch2.md)** della nostra serie di tutorial su Unreal.</span><span class="sxs-lookup"><span data-stu-id="66abf-117">If you haven't already, you'll need to install the **Microsoft Windows Mixed Reality** and **HoloLens** plugins by following the instructions in the **[Initializing your project](tutorials/unreal-uxt-ch2.md)** section of our Unreal tutorial series.</span></span>

![Plug-in audio spaziale di Unreal](images/unreal-spatial-audio-img-01.png)

<span data-ttu-id="66abf-119">Una volta riavviato l'editor, il progetto è impostato.</span><span class="sxs-lookup"><span data-stu-id="66abf-119">Once the editor restarts, your project is all set!</span></span>


## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a><span data-ttu-id="66abf-120">Impostazione del plug-in di spazializzazione per la piattaforma HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="66abf-120">Setting the spatialization plugin for HoloLens 2 platform</span></span>
<span data-ttu-id="66abf-121">La configurazione del plug-in di spazializzazione è specifica delle singole piattaforme.</span><span class="sxs-lookup"><span data-stu-id="66abf-121">Configuring the spatialization plugin is done on a per-platform basis.</span></span>  <span data-ttu-id="66abf-122">Per abilitare il plug-in Microsoft spatial audio per HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="66abf-122">You can enable the Microsoft Spatial Sound plugin for the HoloLens 2 by:</span></span>
1. <span data-ttu-id="66abf-123">Seleziona **Edit > Project Settings** (Modifica > Impostazioni progetto), scorri fino a **Platforms** (Piattaforme) e fai clic su **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="66abf-123">Selecting **Edit > Project Settings**, scrolling to **Platforms** and clicking **HoloLens**.</span></span>
2. <span data-ttu-id="66abf-124">Espandi le proprietà **Audio** e imposta il campo **Spatialization Plugin** (Plug-in di spazializzazione) su **Microsoft Spatial Sound**.</span><span class="sxs-lookup"><span data-stu-id="66abf-124">Expanding the **Audio** properties and setting the **Spatialization Plugin** field to **Microsoft Spatial Sound**.</span></span>

![Plug-in di spazializzazione per la piattaforma HoloLens](images/unreal-spatial-audio-img-02.png)

<span data-ttu-id="66abf-126">Se prevedi di visualizzare in anteprima l'applicazione nell'editor Unreal su un PC desktop, dovrai ripetere i passaggi precedenti per la piattaforma **Windows**:</span><span class="sxs-lookup"><span data-stu-id="66abf-126">If you're going to be previewing your application in the Unreal editor on a desktop PC, you'll need to repeat the above steps for the **Windows** platform:</span></span>

![Plug-in di spazializzazione per la piattaforma Windows](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a><span data-ttu-id="66abf-128">Abilitazione dell'audio spaziale in una workstation</span><span class="sxs-lookup"><span data-stu-id="66abf-128">Enabling spatial audio on your workstation</span></span>
<span data-ttu-id="66abf-129">L'audio spaziale è disabilitato per impostazione predefinita nelle versioni desktop di Windows.</span><span class="sxs-lookup"><span data-stu-id="66abf-129">Spatial audio is disabled by default on desktop versions of Windows.</span></span> <span data-ttu-id="66abf-130">Per abilitarlo, puoi:</span><span class="sxs-lookup"><span data-stu-id="66abf-130">You can enable it by:</span></span>
* <span data-ttu-id="66abf-131">Fare clic con il pulsante destro del mouse sul **volume** sulla barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="66abf-131">Right-clicking on the **volume** icon in the task bar.</span></span>
    + <span data-ttu-id="66abf-132">Scegli **Audio spaziale -> Windows Sonic per cuffie** per ottenere la migliore rappresentazione di ciò che sentirai su HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="66abf-132">Choose **Spatial sound -> Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

![Plug-in di spazializzazione](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
><span data-ttu-id="66abf-134">Questa impostazione è necessaria solo se prevedi di testare il progetto nell'editor Unreal.</span><span class="sxs-lookup"><span data-stu-id="66abf-134">This setting is only required if you plan to test your project in the Unreal editor.</span></span>

## <a name="creating-attenuation-objects"></a><span data-ttu-id="66abf-135">Creazione di oggetti di attenuazione</span><span class="sxs-lookup"><span data-stu-id="66abf-135">Creating Attenuation objects</span></span>
<span data-ttu-id="66abf-136">Dopo avere installato e configurato i plug-in necessari:</span><span class="sxs-lookup"><span data-stu-id="66abf-136">After you've installed and configured the necessary plugins:</span></span>
1. <span data-ttu-id="66abf-137">Cerca un attore **Ambient Sound** (Suono ambientale) nella finestra **Place Actors** (Posiziona attori) e trascinalo nella finestra **Scene** (Scena).</span><span class="sxs-lookup"><span data-stu-id="66abf-137">Search for an **Ambient Sound** actor in the **Place Actors** window and drag it into the **Scene** window.</span></span>

![Aggiunta dell'attore del suono ambientale](images/unreal-spatial-audio-img-07.png)

2. <span data-ttu-id="66abf-139">Imposta l'attore **Ambient Sound** (Suono ambientale) come figlio di un elemento visivo nella scena.</span><span class="sxs-lookup"><span data-stu-id="66abf-139">Make the **Ambient Sound** actor a child of a visual element in your scene.</span></span>
    * <span data-ttu-id="66abf-140">Per impostazione predefinita, un attore Ambient Sound (Suono ambientale) non ha alcuna rappresentazione visiva, quindi sentirai solo un suono dalla sua posizione nella scena.</span><span class="sxs-lookup"><span data-stu-id="66abf-140">An Ambient Sound actor doesn't have any visual representation by default, so you'll only hear a sound from its position in the scene.</span></span> <span data-ttu-id="66abf-141">Se viene collegato a un elemento visivo, puoi vedere e spostare l'attore come qualsiasi altro asset.</span><span class="sxs-lookup"><span data-stu-id="66abf-141">Attaching it to a visual element let's you see and move the actor like any other asset.</span></span>

3.  <span data-ttu-id="66abf-142">Fai clic con il pulsante destro del mouse su **Content Browser** (Browser contenuto) e seleziona **Create Advanced Asset -> Sounds -> Sound Attenuation** (Crea asset avanzato -> Suoni-> Attenuazione suono):</span><span class="sxs-lookup"><span data-stu-id="66abf-142">Right-click on the **Content Browser** and selecting **Create Advanced Asset -> Sounds -> Sound Attenuation**:</span></span>

![Creazione di un asset di attenuazione del suono](images/unreal-spatial-audio-img-06.png)

4. <span data-ttu-id="66abf-144">Fai clic con il pulsante destro del mouse sull'asset **Sound Attenuation** (Attenuazione del suono) nella finestra **Content Browser** (Browser contenuto) e scegli l'opzione **Edit** (Modifica) per visualizzare la finestra delle proprietà.</span><span class="sxs-lookup"><span data-stu-id="66abf-144">Right-click on the **Sound Attenuation** asset in the **Content Browser** window and select the **Edit** option to bring up the properties window.</span></span>
    * <span data-ttu-id="66abf-145">Imposta **Spatialization Method** (Metodo di spazializzazione) su **Binaural** (Binaurale).</span><span class="sxs-lookup"><span data-stu-id="66abf-145">Switch the **Spatialization Method** to **Binaural**.</span></span>

![Impostazione del metodo di spazializzazione](images/unreal-spatial-audio-img-03.png)

5. <span data-ttu-id="66abf-147">Seleziona l'attore **Ambient Sound** (Suono ambientale) e scorri fino alla sezione **Attenuation** (Attenuazione) nel pannello **Details** (Dettagli).</span><span class="sxs-lookup"><span data-stu-id="66abf-147">Select the **Ambient Sound** actor and scroll down to the **Attenuation** section in the **Details** panel.</span></span>
    * <span data-ttu-id="66abf-148">Imposta la proprietà **Attenuation Settings** (Impostazioni attenuazione) sull'asset **Sound Attenuation** (Attenuazione del suono) che hai creato.</span><span class="sxs-lookup"><span data-stu-id="66abf-148">Set the **Attenuation Settings** property to the **Sound Attenuation** asset you created.</span></span>

![Impostazione dell'attenuazione](images/unreal-spatial-audio-img-08.png)

6. <span data-ttu-id="66abf-150">Imposta l'oggetto **Sound Asset** (Asset audio) che vuoi associare all'attore Ambient Sound (Suono ambientale) aggiornando la proprietà **Sound** (Suono) dell'attore Ambient Sound (Suono ambientale) per specificare il file SoundAsset da usare.</span><span class="sxs-lookup"><span data-stu-id="66abf-150">Set the **Sound Asset** you want to attach to the Ambient Sound actor by updating the **Sound** property of the Ambient Sound actor to specify the SoundAsset file to use.</span></span>

![Impostazione dell'asset audio](images/unreal-spatial-audio-img-09.png)

> [!NOTE]
> <span data-ttu-id="66abf-152">Il file SoundAsset deve essere mono per la spazializzazione con il plug-in Microsoft Spatial Sound.</span><span class="sxs-lookup"><span data-stu-id="66abf-152">The SoundAsset file needs to be mono to be spatialized with the Microsoft Spatial Sound plug-in.</span></span> <span data-ttu-id="66abf-153">È possibile trovare le proprietà del file audio posizionando il puntatore del mouse sull'asset nella finestra Content Browser (Browser contenuto), come illustrato nello screenshot seguente.</span><span class="sxs-lookup"><span data-stu-id="66abf-153">You can find the sound file properties by hovering over the asset in the Content Browser window as shown in the screenshot below.</span></span>

![Nuovo asset di attenuazione del suono](images/unreal-spatial-audio-img-10.png)

<span data-ttu-id="66abf-155">Terminata questa configurazione, il suono ambientale può essere spazializzato usando il supporto di offload hardware dedicato in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="66abf-155">Once all of this is configured the ambient sound can be spatialized using the dedicated hardware offload support on HoloLens 2.</span></span>

## <a name="configuring-objects-for-spatialization"></a><span data-ttu-id="66abf-156">Configurazione degli oggetti per la spazializzazione</span><span class="sxs-lookup"><span data-stu-id="66abf-156">Configuring objects for spatialization</span></span>
<span data-ttu-id="66abf-157">Quando usi l'audio spaziale, sei tu a gestire il comportamento del suono in un ambiente virtuale.</span><span class="sxs-lookup"><span data-stu-id="66abf-157">Working with spatial audio means you're in charge of managing how sound behaves in a virtual environment.</span></span> <span data-ttu-id="66abf-158">L'obiettivo principale consiste nel creare oggetti audio che producono un suono più forte quando l'utente è vicino e un suono più debole quando è lontano.</span><span class="sxs-lookup"><span data-stu-id="66abf-158">Your main focus is creating sound objects that appear louder when the user is close, and quieter when the user is far away.</span></span> <span data-ttu-id="66abf-159">Grazie a questo effetto, detto attenuazione del suono, i suoni sembrano collocati in un punto fisso.</span><span class="sxs-lookup"><span data-stu-id="66abf-159">This is referred to as sound attenuation, making sounds appear as if they are positioned in a fixed spot.</span></span>

<span data-ttu-id="66abf-160">Tutti gli oggetti di attenuazione includono impostazioni modificabili per:</span><span class="sxs-lookup"><span data-stu-id="66abf-160">All attenuation objects come with modifiable settings for:</span></span>
* <span data-ttu-id="66abf-161">Distanza</span><span class="sxs-lookup"><span data-stu-id="66abf-161">Distance</span></span>
* <span data-ttu-id="66abf-162">Spazializzazione</span><span class="sxs-lookup"><span data-stu-id="66abf-162">Spatialization</span></span>
* <span data-ttu-id="66abf-163">Assorbimento dell'aria</span><span class="sxs-lookup"><span data-stu-id="66abf-163">Air Absorption</span></span>
* <span data-ttu-id="66abf-164">Focus sull'ascoltatore</span><span class="sxs-lookup"><span data-stu-id="66abf-164">Listener Focus</span></span>
* <span data-ttu-id="66abf-165">Riverbero</span><span class="sxs-lookup"><span data-stu-id="66abf-165">Reverb Send</span></span>
* <span data-ttu-id="66abf-166">Occlusione</span><span class="sxs-lookup"><span data-stu-id="66abf-166">Occlusion</span></span>

<span data-ttu-id="66abf-167">Nella pagina dedicata all'[attenuazione del suono in Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) sono forniti dettagli e specifiche di implementazione su ognuno di questi argomenti.</span><span class="sxs-lookup"><span data-stu-id="66abf-167">[Sound attenuation in Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) has details and implementation specifics on each of these topics.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="66abf-168">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="66abf-168">Next Development Checkpoint</span></span>

<span data-ttu-id="66abf-169">Se si segue il percorso di checkpoint per lo sviluppo con Unreal che è stato delineato, si stanno esplorando i blocchi predefiniti fondamentali di MRTK.</span><span class="sxs-lookup"><span data-stu-id="66abf-169">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="66abf-170">Da qui è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="66abf-170">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66abf-171">Input vocale</span><span class="sxs-lookup"><span data-stu-id="66abf-171">Voice input</span></span>](unreal-voice-input.md)

<span data-ttu-id="66abf-172">In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="66abf-172">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66abf-173">Fotocamera HoloLens</span><span class="sxs-lookup"><span data-stu-id="66abf-173">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="66abf-174">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="66abf-174">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="see-also"></a><span data-ttu-id="66abf-175">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="66abf-175">See also</span></span>
* [<span data-ttu-id="66abf-176">Audio spaziale</span><span class="sxs-lookup"><span data-stu-id="66abf-176">Spatial Sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [<span data-ttu-id="66abf-177">Progettazione dell'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="66abf-177">Spatial Sound Design</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [<span data-ttu-id="66abf-178">Spaziale MR 220: Audio spaziale</span><span class="sxs-lookup"><span data-stu-id="66abf-178">MR Spatial 220: Spatial sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/holograms-220)
