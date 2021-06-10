---
title: Esercitazioni sull'audio spaziale - 5. Uso del riverbero per aggiungere distanza all'audio spaziale
description: Aggiungere un effetto di riverbero per migliorare il senso di variazione della distanza nell'audio spaziale.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens2, spatial audio, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head-related transfer function, reverb, Microsoft Spatializer, audio mixer, SFX reverb
ms.openlocfilehash: 6f41fe904c21591915e0ef13b61dc6bff04527fe
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712688"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="98f93-105">5. Uso del riverbero per aggiungere distanza all'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="98f93-105">5. Using reverb to add distance to spatial audio</span></span>

## <a name="overview"></a><span data-ttu-id="98f93-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="98f93-106">Overview</span></span>

<span data-ttu-id="98f93-107">Nell'esercitazione precedente è stata aggiunta la spazializzazione per i suoni per dare loro un senso di direzione in questa esercitazione si aggiungerà un effetto riverbero per dare ai suoni un senso di distanza.</span><span class="sxs-lookup"><span data-stu-id="98f93-107">In previous tutorial, you have added spatialization for the sounds to give them a sense of direction in this tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

## <a name="objectives"></a><span data-ttu-id="98f93-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="98f93-108">Objectives</span></span>

* <span data-ttu-id="98f93-109">Migliorare la distanza percepita delle origini sonore aggiungendo il riverbero.</span><span class="sxs-lookup"><span data-stu-id="98f93-109">Improve perceived distance of sound sources by adding reverb.</span></span>
* <span data-ttu-id="98f93-110">Controllare la distanza percepita del suono usando la distanza dell'ascoltatore dall'ologramma.</span><span class="sxs-lookup"><span data-stu-id="98f93-110">Control perceived distance of the sound using the listener's distance to the hologram.</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="98f93-111">Aggiungere un gruppo di mixer e un effetto di riverbero</span><span class="sxs-lookup"><span data-stu-id="98f93-111">Add a mixer group and a reverb effect</span></span>

<span data-ttu-id="98f93-112">In [Spatializing button interaction sounds Tutorial (Esercitazione)](unity-spatial-audio-ch2.md)è stato aggiunto un mixer.</span><span class="sxs-lookup"><span data-stu-id="98f93-112">In [Spatializing button interaction sounds Tutorial](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="98f93-113">Il mixer include un **gruppo per** impostazione predefinita denominato **Master.**</span><span class="sxs-lookup"><span data-stu-id="98f93-113">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="98f93-114">Poiché si vuole applicare solo un effetto riverbero ad alcuni suoni, si aggiungerà un secondo gruppo per tali suoni.</span><span class="sxs-lookup"><span data-stu-id="98f93-114">Because we'll only want to apply a reverb effect to some sounds, let's add a second Group for those sounds.</span></span> <span data-ttu-id="98f93-115">Per aggiungere un gruppo, fare clic con il  pulsante destro del mouse sul gruppo Master nel **mixer audio** e scegliere Aggiungi gruppo figlio e assegnare un nome appropriato, ad esempio _Effetto stanza:_</span><span class="sxs-lookup"><span data-stu-id="98f93-115">To add a Group, right click on the Master group in the **Audio Mixer** choose **Add child group** and give suitable name for example _Room Effect_:</span></span>

![Aggiungere un gruppo figlio](images/spatial-audio/spatial-audio-05-section1-step1-1.PNG)

<span data-ttu-id="98f93-117">Ogni **gruppo** ha un proprio set di effetti.</span><span class="sxs-lookup"><span data-stu-id="98f93-117">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="98f93-118">Aggiungere un effetto di riverbero al nuovo gruppo facendo clic su **Aggiungi...** nel nuovo gruppo e scegliendo **SFX Reverb**:</span><span class="sxs-lookup"><span data-stu-id="98f93-118">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![Aggiungere il riverbero SFX](images/spatial-audio/spatial-audio-05-section1-step1-2.PNG)

<span data-ttu-id="98f93-120">Nella terminologia audio, l'audio originale non riverberato viene chiamato percorso arido e l'audio dopo il filtro con il filtro riverbero viene chiamato _percorso umido._ </span><span class="sxs-lookup"><span data-stu-id="98f93-120">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="98f93-121">Entrambi i percorsi vengono inviati all'output audio e i relativi punti di forza in questa combinazione sono denominati _combinazione umida/asciutta._</span><span class="sxs-lookup"><span data-stu-id="98f93-121">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="98f93-122">La combinazione umida/asciutta influisce fortemente sul senso della distanza.</span><span class="sxs-lookup"><span data-stu-id="98f93-122">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="98f93-123">Il **riverbero SFX include** controlli per regolare la combinazione umida/asciutta all'interno dell'effetto.</span><span class="sxs-lookup"><span data-stu-id="98f93-123">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="98f93-124">Poiché il **plug-in Microsoft Spatializer** gestisce il percorso secco, si usa **il riverbero SFX** solo per il percorso umido.</span><span class="sxs-lookup"><span data-stu-id="98f93-124">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="98f93-125">Nel riquadro Inspector (Controllo) del **riverbero SFX**:</span><span class="sxs-lookup"><span data-stu-id="98f93-125">On the Inspector pane of your **SFX Reverb**:</span></span>

* <span data-ttu-id="98f93-126">Impostare la **proprietà Dry Level** sull'impostazione più bassa (-10000 mB)</span><span class="sxs-lookup"><span data-stu-id="98f93-126">Set the **Dry Level** property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="98f93-127">Impostare la **proprietà Room** sull'impostazione più alta (0 mB)</span><span class="sxs-lookup"><span data-stu-id="98f93-127">Set the **Room property** to the highest setting (0 mB)</span></span>

![Proprietà del riverbero SFX](images/spatial-audio/spatial-audio-05-section1-step1-3.PNG)

<span data-ttu-id="98f93-129">Le altre impostazioni controllano l'aspetto della stanza simulata.</span><span class="sxs-lookup"><span data-stu-id="98f93-129">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="98f93-130">In particolare, **il tempo di decadimento** è correlato alle dimensioni percepite della stanza.</span><span class="sxs-lookup"><span data-stu-id="98f93-130">In particular, **Decay Time** is related to perceived room size.</span></span>

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="98f93-131">Abilitare il riverbero nella riproduzione video</span><span class="sxs-lookup"><span data-stu-id="98f93-131">Enable reverb on the video playback</span></span>

<span data-ttu-id="98f93-132">Esistono due passaggi per abilitare il riverbero in un'origine audio:</span><span class="sxs-lookup"><span data-stu-id="98f93-132">There are two steps to enable reverb on an audio source:</span></span>

* <span data-ttu-id="98f93-133">Instradare **l'origine** audio al gruppo **appropriato**</span><span class="sxs-lookup"><span data-stu-id="98f93-133">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="98f93-134">Impostare il **plug-in Microsoft Spatializer** per passare l'audio al **gruppo per** l'elaborazione</span><span class="sxs-lookup"><span data-stu-id="98f93-134">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="98f93-135">Nei passaggi seguenti si regola lo script per controllare il routing audio e si allega uno script di controllo fornito con il plug-in **Microsoft Spatializer** per alimentare i dati nel riverbero.</span><span class="sxs-lookup"><span data-stu-id="98f93-135">In the following steps, you will adjust the script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="98f93-136">Con il **quad selezionato** nella gerarchia fare clic su **Aggiungi componente** nella finestra Inspector (Controllo) e aggiungere Room Effect Send Level (Script) (Livello di invio **dell'effetto stanza(Script)**:</span><span class="sxs-lookup"><span data-stu-id="98f93-136">With the **Quad** selected in the Hierarchy click **Add Component** On the Inspector window and add the **Room Effect Send Level(Script)**:</span></span>

![Aggiungere uno script a livello di invio](images/spatial-audio/spatial-audio-05-section2-step1-1.PNG)

> [!NOTE]
> <span data-ttu-id="98f93-138">A meno che non **si abiliti** la funzionalità Livello di invio effetto stanza del plug-in **Microsoft Spatializer,** non invia audio al motore audio Unity per l'elaborazione degli effetti.</span><span class="sxs-lookup"><span data-stu-id="98f93-138">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="98f93-139">Il **componente Livello di invio effetto** stanza include un controllo grafico che imposta il livello dell'audio inviato al motore audio Unity per l'elaborazione del riverbero.</span><span class="sxs-lookup"><span data-stu-id="98f93-139">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="98f93-140">Per aprire il controllo grafico, fare clic su **Livello di invio effetto stanza**.</span><span class="sxs-lookup"><span data-stu-id="98f93-140">To open the graph control, click on the **Room Effect Send Level**.</span></span>  <span data-ttu-id="98f93-141">Fare clic e trascinare la curva verde verso il basso per impostare il livello su circa -30dB:</span><span class="sxs-lookup"><span data-stu-id="98f93-141">Click and drag the green curve downwards to set the level to about -30dB:</span></span>

![Regolare la curva di riverbero](images/spatial-audio/spatial-audio-05-section2-step1-2.PNG)

<span data-ttu-id="98f93-143">Rimuovere quindi il commento delle 4 righe commentate nello script **SpatializeOnOff.**</span><span class="sxs-lookup"><span data-stu-id="98f93-143">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="98f93-144">Lo script avrà ora un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="98f93-144">The script will now look like this:</span></span>

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

<span data-ttu-id="98f93-145">Dopo aver decommentato queste righe, vengono aggiunte due proprietà al controllo dello **script SpatializeOnOff.**</span><span class="sxs-lookup"><span data-stu-id="98f93-145">Once these lines are Uncommented  it adds two properties to the Inspector of the **SpatializeOnOff script**.</span></span> <span data-ttu-id="98f93-146">assegnarli nella finestra Inspector del **componente SpatializeOnOff** del **quad**.</span><span class="sxs-lookup"><span data-stu-id="98f93-146">assign these on the Inspector window of **SpatializeOnOff** component of the **Quad**.</span></span>

<span data-ttu-id="98f93-147">Con l'oggetto Quad ancora selezionato nella gerarchia , nella finestra Inspector individuare il **componente SpatializeOnOff Script** e :</span><span class="sxs-lookup"><span data-stu-id="98f93-147">With the Quad object still selected in the Hierarchy , in the Inspector window locate the **SpatializeOnOff Script** component and :</span></span>

* <span data-ttu-id="98f93-148">Impostare la **proprietà Gruppo effetti stanza** sul nuovo gruppo di mixer effetto stanza</span><span class="sxs-lookup"><span data-stu-id="98f93-148">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="98f93-149">Impostare la **proprietà Gruppo master** sul gruppo mixer master</span><span class="sxs-lookup"><span data-stu-id="98f93-149">Set the **Master Group** property to the Master mixer group</span></span>

![Spatialize On Off Extended](images/spatial-audio/spatial-audio-05-section2-step1-3.PNG)

## <a name="congratulations"></a><span data-ttu-id="98f93-151">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="98f93-151">Congratulations</span></span>

<span data-ttu-id="98f93-152">Sono stati completati i HoloLens 2 di audio spaziale per Unity.</span><span class="sxs-lookup"><span data-stu-id="98f93-152">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="98f93-153">Provare l'app in un HoloLens 2 o Unity.</span><span class="sxs-lookup"><span data-stu-id="98f93-153">Try out the app on a HoloLens 2 or Unity.</span></span> <span data-ttu-id="98f93-154">Quando si fa clic sul pulsante nell'app per attivare la spazializzazione, lo script instraderà l'audio del video al gruppo di effetti della stanza per aggiungere il riverbero.</span><span class="sxs-lookup"><span data-stu-id="98f93-154">When you click the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="98f93-155">Quando si passa allo stereo, instraderà l'audio al gruppo Master ed eviterà di aggiungere riverbero.</span><span class="sxs-lookup"><span data-stu-id="98f93-155">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

> [!TIP]
> <span data-ttu-id="98f93-156">Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="98f93-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>
