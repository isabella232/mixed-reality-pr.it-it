---
title: Esercitazioni sull'audio spaziale - 4. Abilitazione e disabilitazione dell'audio spaziale in fase di esecuzione
description: Usare un pulsante per abilitare e disabilitare la spazializzazione dell'audio in fase di esecuzione.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens2, audio spaziale, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, funzione di trasferimento correlata alla testa, riverbero, Spazialista Microsoft
ms.openlocfilehash: 9d0fa432f2e653cdd6820cb6c779cc1acc5c4b15
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712756"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="74d0f-105">4. Abilitazione e disabilitazione della spazializzazione in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="74d0f-105">4. Enabling and disabling spatialization at run time</span></span>

## <a name="overview"></a><span data-ttu-id="74d0f-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="74d0f-106">Overview</span></span>

<span data-ttu-id="74d0f-107">In questa esercitazione si apprenderà come abilitare e disabilitare la spazializzazione in fase di esecuzione e testarla nell'editor di Unity e HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="74d0f-107">In this tutorial, you will learn how to Enable and disable spatialization at run time and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="74d0f-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="74d0f-108">Objectives</span></span>

* <span data-ttu-id="74d0f-109">Aggiungere un nuovo script per controllare la spazializzazione in un oggetto gioco</span><span class="sxs-lookup"><span data-stu-id="74d0f-109">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="74d0f-110">Eseguire lo script di controllo della spazializzazione dalle azioni dei pulsanti</span><span class="sxs-lookup"><span data-stu-id="74d0f-110">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="74d0f-111">Aggiungere lo script di controllo della spazializzazione</span><span class="sxs-lookup"><span data-stu-id="74d0f-111">Add spatialization control script</span></span>

 <span data-ttu-id="74d0f-112">Fare clic con il pulsante destro del mouse nella finestra Progetto e scegliere Crea script C# per creare un nuovo script C#, immettere un nome appropriato per lo script, ad esempio  >   _SpatializeOnOff:_</span><span class="sxs-lookup"><span data-stu-id="74d0f-112">Right-click in the Project window and choose **Create** > **C# Script** to create a new C# script, enter a suitable name for the script, for example, _SpatializeOnOff_:</span></span>

![Crea script](images/spatial-audio/spatial-audio-04-section1-step1-1.PNG)

<span data-ttu-id="74d0f-114">Fare doppio clic nello script nella finestra Progetto per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="74d0f-114">Double-click the script in the Project window to open it in Visual Studio.</span></span> <span data-ttu-id="74d0f-115">Sostituire il contenuto dello script predefinito con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="74d0f-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="74d0f-116">Diverse righe dello script sono commentate. Queste righe verranno decommentate in Next Chapter: Using reverb to add distance to spatial audio ( Capitolo successivo: Uso [del riverbero per aggiungere la distanza all'audio spaziale).](unity-spatial-audio-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="74d0f-116">Several lines of the script are commented out. These lines will be uncommented in [Next Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md).</span></span>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    //public AudioMixerGroup RoomEffectGroup;
    //public AudioMixerGroup MasterGroup;

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
        //m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        //m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

> [!NOTE]
> <span data-ttu-id="74d0f-117">Per abilitare o disabilitare la spazializzazione, lo script regola solo la proprietà **spatialBlend,** lasciando abilitata **la proprietà spatialization.**</span><span class="sxs-lookup"><span data-stu-id="74d0f-117">To enable or disable the spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="74d0f-118">In questa modalità Unity applica ancora la **curva volume.**</span><span class="sxs-lookup"><span data-stu-id="74d0f-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="74d0f-119">In caso contrario, se l'utente deve disabilitare la spazializzazione quando è lontano dall'origine, il volume aumenta improvvisamente.</span><span class="sxs-lookup"><span data-stu-id="74d0f-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span>
> <span data-ttu-id="74d0f-120">Se si preferisce disabilitare completamente la spazializzazione, modificare lo script per modificare anche la proprietà **booleana spatialization** della **variabile SourceObject.**</span><span class="sxs-lookup"><span data-stu-id="74d0f-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="74d0f-121">Collegare lo script e guidarlo dal pulsante</span><span class="sxs-lookup"><span data-stu-id="74d0f-121">Attach your script and drive it from the button</span></span>

<span data-ttu-id="74d0f-122">Selezionare **Quad** nella gerarchia e nella finestra Inspector (Controllo) usare il pulsante Add Component (Aggiungi componente) per aggiungere **SpatializeOnOff(Script)**</span><span class="sxs-lookup"><span data-stu-id="74d0f-122">Select **Quad** in the Hierarchy and in the Inspector window, use the Add Component button to add **SpatializeOnOff(Script)**</span></span>

![Aggiungere lo script al quad](images/spatial-audio/spatial-audio-04-section2-step1-1.PNG)

<span data-ttu-id="74d0f-124">Nella gerarchia individuare **PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro**.</span><span class="sxs-lookup"><span data-stu-id="74d0f-124">In the Hierarchy locate **PressableButtonHoloLens2** > **IconAndText** > **TextMeshPro**.</span></span>

<span data-ttu-id="74d0f-125">Con l'oggetto **Quad** ancora selezionato nella gerarchia, nella finestra Inspector (Controllo) individua il componente **Spatialize On Off (Script) (Spazializza** su off - Script) e trascina TextMeshPro Component (Componente **TextMeshPro)** di PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="74d0f-125">With the **Quad** object still selected in the Hierarchy, in the Inspector window, locate the **Spatialize On Off (Script)** component and Drag and drop **TextMeshPro** Component of the PressableButtonHoloLens2.</span></span>

![Trovare l'oggetto PressableButtonHoloLens2 nella gerarchia](images/spatial-audio/spatial-audio-04-section2-step1-2.PNG)

<span data-ttu-id="74d0f-127">Per impostare il pulsante in modo che chiami lo script **SpatializeOnOff** quando viene rilasciato, è necessario configurare lo script con interazione.</span><span class="sxs-lookup"><span data-stu-id="74d0f-127">To set the button to call the **SpatializeOnOff** script when the button is released You need to configure interactable script.</span></span>

<span data-ttu-id="74d0f-128">Nella finestra Hierarchy (Gerarchia) seleziona **PressableButtonHoloLens2.**</span><span class="sxs-lookup"><span data-stu-id="74d0f-128">In the Hierarchy window, select the **PressableButtonHoloLens2**.</span></span> <span data-ttu-id="74d0f-129">Nella finestra Inspector (Controllo) individua il **componente Interactable (Script) (Interagiscibile - Script)** e fai clic sull'icona + sotto l'evento OnClick ().</span><span class="sxs-lookup"><span data-stu-id="74d0f-129">In the Inspector window, locate the **Interactable (Script)** component and click on + icon under OnClick () event.</span></span>

* <span data-ttu-id="74d0f-130">Con l'oggetto **PressableButtonHoloLens2** ancora selezionato nella finestra Hierarchy (Gerarchia), fai clic e trascina l'oggetto **Quad** dalla finestra Hierarchy (Gerarchia) nel campo **vuoto None (Object) (Nessuno - Oggetto)** dell'evento appena aggiunto per fare in modo che l'oggetto ButtonParent sia in ascolto dell'evento click del pulsante da questo pulsante:</span><span class="sxs-lookup"><span data-stu-id="74d0f-130">With the **PressableButtonHoloLens2** object still selected in the Hierarchy window, click-and-drag the **Quad** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

* <span data-ttu-id="74d0f-131">Fai clic sull'elenco a discesa **No Function** (Nessuna funzione) dello stesso evento.</span><span class="sxs-lookup"><span data-stu-id="74d0f-131">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="74d0f-132">Selezionare quindi **SpatializeOnOff**  >  **SwapSpatialization () per** attivare e disattivare l'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="74d0f-132">Then select **SpatializeOnOff** > **SwapSpatialization ()** to turn on and off the Spatial audio</span></span>

![Impostazioni dell'azione pulsante](images/spatial-audio/spatial-audio-04-section2-step1-3.PNG)

## <a name="congratulations"></a><span data-ttu-id="74d0f-134">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="74d0f-134">Congratulations</span></span>

<span data-ttu-id="74d0f-135">In questa esercitazione si è appreso come abilitare e disabilitare la spazializzazione in fase di esecuzione, testare l'app in un HoloLens 2 o nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="74d0f-135">In this tutorial, you have learned how to enable and disable spatialization at run time, test out the app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="74d0f-136">Nell'app è ora possibile fare clic sul pulsante per attivare e disattivare la spazializzazione dell'audio.</span><span class="sxs-lookup"><span data-stu-id="74d0f-136">In the app, you can now click the button to activate and deactivate spatialization of the audio.</span></span>

<span data-ttu-id="74d0f-137">Nell'esercitazione successiva si aggiungerà un effetto riverbero per dare ai suoni un senso di distanza.</span><span class="sxs-lookup"><span data-stu-id="74d0f-137">In the next tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

> [!TIP]
> <span data-ttu-id="74d0f-138">Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="74d0f-138">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="74d0f-139">Esercitazione successiva: 5. Uso del riverbero per aggiungere la distanza all'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="74d0f-139">Next Tutorial: 5. Using reverb to add distance to spatial audio</span></span>](unity-spatial-audio-ch5.md)
