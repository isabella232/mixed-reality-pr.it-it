---
title: Esercitazioni audio spaziali-5. Uso del riverbero per aggiungere distanza all'audio spaziale
description: Aggiungere un effetto di riverbero per migliorare il senso della variazione della distanza nell'audio spaziale.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale, MRTK, Toolkit per realtà mista, UWP, Windows 10, HRTF, funzione di trasferimento correlato alla testa, riverbero, Microsoft Spatializer, mixer audio, riverbero SFX
ms.openlocfilehash: f7a5270d969f2e462db0244bd6c68b99347ae1a7
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590723"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="7e6ab-105">5. Uso del riverbero per aggiungere distanza all'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="7e6ab-105">5. Using reverb to add distance to spatial audio</span></span>

## <a name="overview"></a><span data-ttu-id="7e6ab-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="7e6ab-106">Overview</span></span>

<span data-ttu-id="7e6ab-107">Nell'esercitazione precedente è stata aggiunta la spazializzazione per i suoni, per dare loro un senso di direzione in questa esercitazione, si aggiungerà un effetto di riverbero per dare un senso di distanza ai suoni.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-107">In previous tutorial, you have added spatialization for the sounds to give them a sense of direction in this tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

## <a name="objectives"></a><span data-ttu-id="7e6ab-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="7e6ab-108">Objectives</span></span>

* <span data-ttu-id="7e6ab-109">Migliorare la distanza percepita delle origini audio aggiungendo Reverb.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-109">Improve perceived distance of sound sources by adding reverb.</span></span>
* <span data-ttu-id="7e6ab-110">Controllare la distanza percepita del suono usando la distanza del listener con l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-110">Control perceived distance of the sound using the listener's distance to the hologram.</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="7e6ab-111">Aggiungere un gruppo di mixer e un effetto di riverbero</span><span class="sxs-lookup"><span data-stu-id="7e6ab-111">Add a mixer group and a reverb effect</span></span>

<span data-ttu-id="7e6ab-112">Nell' [esercitazione sull'interazione con il pulsante Spatializing](unity-spatial-audio-ch2.md)è stato aggiunto un mixer.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-112">In [Spatializing button interaction sounds Tutorial](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="7e6ab-113">Il mixer include un **gruppo** per impostazione predefinita denominato **Master**.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-113">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="7e6ab-114">Poiché si vuole applicare un effetto di riverbero solo ad alcuni suoni, aggiungere un secondo gruppo per i suoni.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-114">Because we'll only want to apply a reverb effect to some sounds, let's add a second Group for those sounds.</span></span> <span data-ttu-id="7e6ab-115">Per aggiungere un gruppo, fare clic con il pulsante destro del mouse sul gruppo master nel **mixer audio** scegliere **Aggiungi gruppo figlio** e assegnare un nome appropriato per l' _effetto spazio_ di esempio:</span><span class="sxs-lookup"><span data-stu-id="7e6ab-115">To add a Group, right click on the Master group in the **Audio Mixer** choose **Add child group** and give suitable name for example _Room Effect_:</span></span>

![Aggiungi gruppo figlio](images/spatial-audio/spatial-audio-05-section1-step1-1.png)

<span data-ttu-id="7e6ab-117">Ogni **gruppo** ha un proprio set di effetti.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-117">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="7e6ab-118">Aggiungere un effetto del riverbero al nuovo gruppo facendo clic su **Aggiungi...** nel nuovo gruppo e scegliendo il **riverbero SFX**:</span><span class="sxs-lookup"><span data-stu-id="7e6ab-118">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![Aggiungi Riverb SFX](images/spatial-audio/spatial-audio-05-section1-step1-2.png)

<span data-ttu-id="7e6ab-120">Nella terminologia audio, l'audio originale, non riverberato, viene chiamato _percorso asciutto_ e l'audio dopo l'applicazione di filtri con il filtro del riverbero viene chiamato _percorso bagnato_.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-120">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="7e6ab-121">Entrambi i percorsi vengono inviati all'output audio e i relativi punti di forza relativi in questa combinazione sono detti _mix bagnato/secco_.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-121">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="7e6ab-122">La combinazione Wet/Dry influiscono fortemente sul senso della distanza.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-122">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="7e6ab-123">Il **riverbero SFX** include i controlli per regolare la combinazione di Wet/Dry nell'effetto.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-123">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="7e6ab-124">Poiché il plug-in **Microsoft Spatializer** gestisce il percorso asciutto, verrà usato il **riverbero SFX** solo per il percorso bagnato.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-124">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="7e6ab-125">Nel riquadro Inspector del **riverbero SFX**:</span><span class="sxs-lookup"><span data-stu-id="7e6ab-125">On the Inspector pane of your **SFX Reverb**:</span></span>

* <span data-ttu-id="7e6ab-126">Impostare la proprietà **livello secco** sull'impostazione più bassa (-10000 MB)</span><span class="sxs-lookup"><span data-stu-id="7e6ab-126">Set the **Dry Level** property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="7e6ab-127">Imposta la **Proprietà room** sull'impostazione massima (0 MB)</span><span class="sxs-lookup"><span data-stu-id="7e6ab-127">Set the **Room property** to the highest setting (0 mB)</span></span>

![Proprietà del riverbero SFX](images/spatial-audio/spatial-audio-05-section1-step1-3.png)

<span data-ttu-id="7e6ab-129">Le altre impostazioni controllano l'aspetto della stanza simulata.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-129">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="7e6ab-130">In particolare, il **tempo di decadimento** è correlato alla dimensione della stanza percepita.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-130">In particular, **Decay Time** is related to perceived room size.</span></span>

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="7e6ab-131">Abilitare il riverbero per la riproduzione video</span><span class="sxs-lookup"><span data-stu-id="7e6ab-131">Enable reverb on the video playback</span></span>

<span data-ttu-id="7e6ab-132">Per abilitare il riverbero in un'origine audio sono necessari due passaggi:</span><span class="sxs-lookup"><span data-stu-id="7e6ab-132">There are two steps to enable reverb on an audio source:</span></span>

* <span data-ttu-id="7e6ab-133">Indirizzare l' **origine audio** al **gruppo** appropriato</span><span class="sxs-lookup"><span data-stu-id="7e6ab-133">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="7e6ab-134">Impostare il plug-in **Microsoft Spatializer** per passare l'audio al **gruppo** per l'elaborazione</span><span class="sxs-lookup"><span data-stu-id="7e6ab-134">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="7e6ab-135">Nei passaggi seguenti si modificherà lo script per controllare il routing audio e si collegherà uno script di controllo fornito con il plug-in **Microsoft Spatializer** per inserire i dati nel Reverbo.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-135">In the following steps, you will adjust the script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="7e6ab-136">Con il **Quad** selezionato nella gerarchia fare clic su **Aggiungi componente** nella finestra di controllo e aggiungere il **livello di invio dell'effetto spazio (script)**:</span><span class="sxs-lookup"><span data-stu-id="7e6ab-136">With the **Quad** selected in the Hierarchy click **Add Component** On the Inspector window and add the **Room Effect Send Level(Script)**:</span></span>

![Aggiungi script del livello di trasmissione](images/spatial-audio/spatial-audio-05-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="7e6ab-138">A meno che non si abiliti la funzionalità di **trasmissione dell'effetto spazio** del plug-in **Microsoft Spatializer** , non viene inviato alcun audio al motore audio Unity per l'elaborazione degli effetti.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-138">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="7e6ab-139">Il componente del **livello di invio dell'effetto chat** include un controllo grafico che imposta il livello dell'audio inviato al motore audio di Unity per l'elaborazione dei verbi.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-139">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="7e6ab-140">Per aprire il controllo grafico, fare clic sul **livello di invio dell'effetto chat room**.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-140">To open the graph control, click on the **Room Effect Send Level**.</span></span>  <span data-ttu-id="7e6ab-141">Fare clic e trascinare la curva verde verso il basso per impostare il livello su about-30dB:</span><span class="sxs-lookup"><span data-stu-id="7e6ab-141">Click and drag the green curve downwards to set the level to about -30dB:</span></span>

![Modificare la curva del riverbero](images/spatial-audio/spatial-audio-05-section2-step1-2.png)

<span data-ttu-id="7e6ab-143">Rimuovere quindi il commento dalle 4 righe commentate nello script **SpatializeOnOff** .</span><span class="sxs-lookup"><span data-stu-id="7e6ab-143">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="7e6ab-144">Lo script sarà ora simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="7e6ab-144">The script will now look like this:</span></span>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

<span data-ttu-id="7e6ab-145">Una volta che queste righe sono state annullate, vengono aggiunte due proprietà al controllo dello **script SpatializeOnOff**.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-145">Once these lines are Uncommented  it adds two properties to the Inspector of the **SpatializeOnOff script**.</span></span> <span data-ttu-id="7e6ab-146">assegnare questi elementi nella finestra di controllo del componente **SpatializeOnOff** del **Quad**.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-146">assign these on the Inspector window of **SpatializeOnOff** component of the **Quad**.</span></span>

<span data-ttu-id="7e6ab-147">Con l'oggetto Quad ancora selezionato nella gerarchia, nella finestra di controllo individuare il componente **script SpatializeOnOff** e:</span><span class="sxs-lookup"><span data-stu-id="7e6ab-147">With the Quad object still selected in the Hierarchy , in the Inspector window locate the **SpatializeOnOff Script** component and :</span></span>

* <span data-ttu-id="7e6ab-148">Impostare la proprietà **gruppo effetti Room** sul nuovo gruppo di mixer effetti della stanza</span><span class="sxs-lookup"><span data-stu-id="7e6ab-148">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="7e6ab-149">Impostare la proprietà **gruppo Master** sul gruppo di mixer Master</span><span class="sxs-lookup"><span data-stu-id="7e6ab-149">Set the **Master Group** property to the Master mixer group</span></span>

![Spatialize su off esteso](images/spatial-audio/spatial-audio-05-section2-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="7e6ab-151">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="7e6ab-151">Congratulations</span></span>

<span data-ttu-id="7e6ab-152">Sono state completate le esercitazioni audio spaziali HoloLens 2 per Unity.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-152">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="7e6ab-153">Provare l'app in un HoloLens 2 o Unity.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-153">Try out the app on a HoloLens 2 or Unity.</span></span> <span data-ttu-id="7e6ab-154">Quando si fa clic sul pulsante nell'app per attivare la spazializzazione, lo script instrada l'audio del video al gruppo di effetti della stanza per aggiungere Reverb.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-154">When you click the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="7e6ab-155">Quando si passa a stereo, l'audio viene indirizzato al gruppo Master ed è possibile evitare di aggiungere Reverb.</span><span class="sxs-lookup"><span data-stu-id="7e6ab-155">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

> [!TIP]
> <span data-ttu-id="7e6ab-156">Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="7e6ab-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>
