---
title: Esercitazioni audio spaziali-4. Abilitazione e disabilitazione dell'audio spaziale in fase di esecuzione
description: Usare un pulsante per abilitare e disabilitare la spazializzazione dell'audio in fase di esecuzione.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale, MRTK, Toolkit per realtà mista, UWP, Windows 10, HRTF, funzione di trasferimento relativa alla testa, Reverb, Microsoft Spatializer
ms.openlocfilehash: c752f79f53b5167d674b9e778637357d97fb914a
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678210"
---
# <a name="enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="37d61-105">Abilitazione e disabilitazione della spazializzazione in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="37d61-105">Enabling and disabling spatialization at run time</span></span>

## <a name="objectives"></a><span data-ttu-id="37d61-106">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="37d61-106">Objectives</span></span>
<span data-ttu-id="37d61-107">In questo quarto capitolo, verranno illustrate le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="37d61-107">In this 4th chapter, you'll:</span></span>
* <span data-ttu-id="37d61-108">Aggiungere un nuovo script per controllare la spazializzazione in un oggetto gioco</span><span class="sxs-lookup"><span data-stu-id="37d61-108">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="37d61-109">Unità dello script di controllo della spazializzazione dalle azioni dei pulsanti</span><span class="sxs-lookup"><span data-stu-id="37d61-109">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="37d61-110">Aggiungi script di controllo di spazializzazione</span><span class="sxs-lookup"><span data-stu-id="37d61-110">Add spatialization control script</span></span>
<span data-ttu-id="37d61-111">Fare clic con il pulsante destro del mouse nel riquadro **progetto** e creare un nuovo script c# scegliendo **Crea-> script c#**.</span><span class="sxs-lookup"><span data-stu-id="37d61-111">Right-click in the **Project** pane and create a new C# script by choosing **Create -> C# Script**.</span></span> <span data-ttu-id="37d61-112">Denominare lo script "SpatializeOnOff".</span><span class="sxs-lookup"><span data-stu-id="37d61-112">Name your script "SpatializeOnOff".</span></span>

![Crea script](images/spatial-audio/create-script.png)

<span data-ttu-id="37d61-114">Fare doppio clic sullo script nel riquadro **progetto** per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="37d61-114">Double-click the script in the **Project** pane to open it in Visual Studio.</span></span> <span data-ttu-id="37d61-115">Sostituire il contenuto dello script predefinito con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="37d61-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="37d61-116">Diverse righe dello script sono impostate come commento. Queste righe verranno annullate come commento nel [capitolo 5](unity-spatial-audio-ch5.md).</span><span class="sxs-lookup"><span data-stu-id="37d61-116">Several lines of the script are commented out. These lines will be uncommented in [Chapter 5](unity-spatial-audio-ch5.md).</span></span>

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
> <span data-ttu-id="37d61-117">Per abilitare o disabilitare la spazializzazione, lo script regola solo la proprietà **spatialBlend** , lasciando abilitata la proprietà di **spazializzazione** .</span><span class="sxs-lookup"><span data-stu-id="37d61-117">To enable or disable spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="37d61-118">In questa modalità, Unity applica comunque la curva del **volume** .</span><span class="sxs-lookup"><span data-stu-id="37d61-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="37d61-119">In caso contrario, se l'utente dovesse disabilitare la spazializzazione quando si è distante dall'origine, l'incremento del volume verrà improvvisamente interrotto.</span><span class="sxs-lookup"><span data-stu-id="37d61-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span> <br> <br>
> <span data-ttu-id="37d61-120">Se si preferisce disabilitare completamente la spazializzazione, modificare lo script in modo da regolare anche la proprietà Boolean di **spazializzazione** della variabile **SourceObject** .</span><span class="sxs-lookup"><span data-stu-id="37d61-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="37d61-121">Alleghi lo script e lo guidi dal pulsante</span><span class="sxs-lookup"><span data-stu-id="37d61-121">Attach your script and drive it from the button</span></span>
<span data-ttu-id="37d61-122">Nel riquadro **Inspector** del **Quad** fare clic su **Add Component** e aggiungere lo script **Spatialize on off** :</span><span class="sxs-lookup"><span data-stu-id="37d61-122">On the **Inspector** pane of the **Quad**, click **Add Component** and add the **Spatialize On Off** script:</span></span>

![Aggiungi script a Quad](images/spatial-audio/add-script-to-quad.png)

<span data-ttu-id="37d61-124">Sul componente **Spatialize on off** del **Quad**:</span><span class="sxs-lookup"><span data-stu-id="37d61-124">On the **Spatialize On Off** component of the **Quad**:</span></span>
1. <span data-ttu-id="37d61-125">Trovare l'oggetto **PressableButtonHoloLens2-> IconAndText-> TextMeshPro** nella **gerarchia**:</span><span class="sxs-lookup"><span data-stu-id="37d61-125">Find the **PressableButtonHoloLens2 -> IconAndText -> TextMeshPro** subject in the **Hierarchy**:</span></span>

![Trovare l'oggetto PressableButtonHoloLens2 nella gerarchia](images/spatial-audio/pressable-button-object.png)

2. <span data-ttu-id="37d61-127">Trascinare l'oggetto **TextMeshPro** nel campo **ButtonTextObject** del componente **Spatialize on off**</span><span class="sxs-lookup"><span data-stu-id="37d61-127">Drag the **TextMeshPro** subject onto the **ButtonTextObject** field of the **Spatialize On Off** component</span></span>

<span data-ttu-id="37d61-128">Una volta apportate queste modifiche, il componente **Spatialize on** of the **Quad** sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="37d61-128">After these changes, the **Spatialize On Off** component of the **Quad** will look like this:</span></span>

![Spatialize on Basic](images/spatial-audio/spatialize-on-off-basic.png)

<span data-ttu-id="37d61-130">Per impostare il pulsante per chiamare lo script **Spatialize on off** quando si rilascia il pulsante, aprire il riquadro **Inspector** dell'oggetto **PressableButtonHoloLens2** , trovare il componente **interactable** e:</span><span class="sxs-lookup"><span data-stu-id="37d61-130">To set the button to call the **Spatialize On Off** script when the button is released, open the **Inspector** pane of the **PressableButtonHoloLens2** object, find the **Interactable** component, and:</span></span>
1. <span data-ttu-id="37d61-131">Trovare l'area **OnClick ()** della sottosezione **Events**</span><span class="sxs-lookup"><span data-stu-id="37d61-131">Find the **OnClick ()** region of the **Events** subsection</span></span>
2. <span data-ttu-id="37d61-132">Trascinare il **Quad** dalla **gerarchia** nello slot dell'oggetto di destinazione.</span><span class="sxs-lookup"><span data-stu-id="37d61-132">Drag the **Quad** from the **Hierarchy** into the target object slot.</span></span>
3. <span data-ttu-id="37d61-133">Selezionare **SpatializeOnOff. SwapSpatialization** nella casella di riepilogo a discesa azione.</span><span class="sxs-lookup"><span data-stu-id="37d61-133">Select **SpatializeOnOff.SwapSpatialization** from the action drop-down box.</span></span>

<span data-ttu-id="37d61-134">Una volta apportate queste modifiche, il componente **interagisce** sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="37d61-134">After these changes, the **Interactable** component will look like this:</span></span>

![Impostazioni azione pulsante](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a><span data-ttu-id="37d61-136">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="37d61-136">Next steps</span></span>
<span data-ttu-id="37d61-137">Provare l'app in un HoloLens 2 o nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="37d61-137">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="37d61-138">Nell'app è ora possibile toccare il pulsante per attivare e disattivare la spazializzazione nel video.</span><span class="sxs-lookup"><span data-stu-id="37d61-138">In the app, you can now touch the button to activate and deactivate spatialization on the video.</span></span> <span data-ttu-id="37d61-139">Quando si esegue il test nell'editor di Unity, premere la barra spaziatrice e scorrere con la rotellina di scorrimento per attivare la simulazione manuale.</span><span class="sxs-lookup"><span data-stu-id="37d61-139">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="37d61-140">Capitolo 5</span><span class="sxs-lookup"><span data-stu-id="37d61-140">Chapter 5</span></span>](unity-spatial-audio-ch5.md) 

