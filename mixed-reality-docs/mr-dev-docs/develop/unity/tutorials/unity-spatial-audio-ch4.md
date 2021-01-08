---
title: Abilitazione e disabilitazione dell'audio spaziale in fase di esecuzione
description: Informazioni su come scrivere uno script C# che usa un pulsante per abilitare e disabilitare la spazializzazione audio in fase di esecuzione.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale, MRTK, Toolkit per realtà mista, UWP, Windows 10, HRTF, funzione di trasferimento relativa alla testa, Reverb, Microsoft Spatializer
ms.openlocfilehash: eaaf8a05088b5bab674ca11b15b0c63383faa479
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007341"
---
# <a name="enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="b622f-104">Abilitazione e disabilitazione della spazializzazione in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="b622f-104">Enabling and disabling spatialization at run time</span></span>

## <a name="objectives"></a><span data-ttu-id="b622f-105">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="b622f-105">Objectives</span></span>

<span data-ttu-id="b622f-106">In questo quarto capitolo, verranno illustrate le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="b622f-106">In this 4th chapter, you'll:</span></span>
* <span data-ttu-id="b622f-107">Aggiungere un nuovo script per controllare la spazializzazione in un oggetto gioco</span><span class="sxs-lookup"><span data-stu-id="b622f-107">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="b622f-108">Unità dello script di controllo della spazializzazione dalle azioni dei pulsanti</span><span class="sxs-lookup"><span data-stu-id="b622f-108">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="b622f-109">Aggiungi script di controllo di spazializzazione</span><span class="sxs-lookup"><span data-stu-id="b622f-109">Add spatialization control script</span></span>

<span data-ttu-id="b622f-110">Fare clic con il pulsante destro del mouse nel riquadro **progetto** e creare un nuovo script c# scegliendo **Crea-> script c#**.</span><span class="sxs-lookup"><span data-stu-id="b622f-110">Right-click in the **Project** pane and create a new C# script by choosing **Create -> C# Script**.</span></span> <span data-ttu-id="b622f-111">Denominare lo script "SpatializeOnOff".</span><span class="sxs-lookup"><span data-stu-id="b622f-111">Name your script "SpatializeOnOff".</span></span>

![Crea script](images/spatial-audio/create-script.png)

<span data-ttu-id="b622f-113">Fare doppio clic sullo script nel riquadro **progetto** per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b622f-113">Double-click the script in the **Project** pane to open it in Visual Studio.</span></span> <span data-ttu-id="b622f-114">Sostituire il contenuto dello script predefinito con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="b622f-114">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="b622f-115">Diverse righe dello script sono impostate come commento. Queste righe verranno annullate come commento nel [capitolo 5](unity-spatial-audio-ch5.md).</span><span class="sxs-lookup"><span data-stu-id="b622f-115">Several lines of the script are commented out. These lines will be uncommented in [Chapter 5](unity-spatial-audio-ch5.md).</span></span>

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
> <span data-ttu-id="b622f-116">Per abilitare o disabilitare la spazializzazione, lo script regola solo la proprietà **spatialBlend** , lasciando abilitata la proprietà di **spazializzazione** .</span><span class="sxs-lookup"><span data-stu-id="b622f-116">To enable or disable spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="b622f-117">In questa modalità, Unity applica comunque la curva del **volume** .</span><span class="sxs-lookup"><span data-stu-id="b622f-117">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="b622f-118">In caso contrario, se l'utente dovesse disabilitare la spazializzazione quando si è distante dall'origine, l'incremento del volume verrà improvvisamente interrotto.</span><span class="sxs-lookup"><span data-stu-id="b622f-118">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span> <br> <br>
> <span data-ttu-id="b622f-119">Se si preferisce disabilitare completamente la spazializzazione, modificare lo script in modo da regolare anche la proprietà Boolean di **spazializzazione** della variabile **SourceObject** .</span><span class="sxs-lookup"><span data-stu-id="b622f-119">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="b622f-120">Alleghi lo script e lo guidi dal pulsante</span><span class="sxs-lookup"><span data-stu-id="b622f-120">Attach your script and drive it from the button</span></span>

<span data-ttu-id="b622f-121">Nel riquadro **Inspector** del **Quad** fare clic su **Add Component** e aggiungere lo script **Spatialize on off** :</span><span class="sxs-lookup"><span data-stu-id="b622f-121">On the **Inspector** pane of the **Quad**, click **Add Component** and add the **Spatialize On Off** script:</span></span>

![Aggiungi script a Quad](images/spatial-audio/add-script-to-quad.png)

<span data-ttu-id="b622f-123">Sul componente **Spatialize on off** del **Quad**:</span><span class="sxs-lookup"><span data-stu-id="b622f-123">On the **Spatialize On Off** component of the **Quad**:</span></span>
1. <span data-ttu-id="b622f-124">Trovare l'oggetto **PressableButtonHoloLens2-> IconAndText-> TextMeshPro** nella **gerarchia**:</span><span class="sxs-lookup"><span data-stu-id="b622f-124">Find the **PressableButtonHoloLens2 -> IconAndText -> TextMeshPro** subject in the **Hierarchy**:</span></span>

![Trovare l'oggetto PressableButtonHoloLens2 nella gerarchia](images/spatial-audio/pressable-button-object.png)

2. <span data-ttu-id="b622f-126">Trascinare l'oggetto **TextMeshPro** nel campo **ButtonTextObject** del componente **Spatialize on off**</span><span class="sxs-lookup"><span data-stu-id="b622f-126">Drag the **TextMeshPro** subject onto the **ButtonTextObject** field of the **Spatialize On Off** component</span></span>

<span data-ttu-id="b622f-127">Una volta apportate queste modifiche, il componente **Spatialize on** of the **Quad** sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="b622f-127">After these changes, the **Spatialize On Off** component of the **Quad** will look like this:</span></span>

![Spatialize on Basic](images/spatial-audio/spatialize-on-off-basic.png)

<span data-ttu-id="b622f-129">Per impostare il pulsante per chiamare lo script **Spatialize on off** quando si rilascia il pulsante, aprire il riquadro **Inspector** dell'oggetto **PressableButtonHoloLens2** , trovare il componente **interactable** e:</span><span class="sxs-lookup"><span data-stu-id="b622f-129">To set the button to call the **Spatialize On Off** script when the button is released, open the **Inspector** pane of the **PressableButtonHoloLens2** object, find the **Interactable** component, and:</span></span>
1. <span data-ttu-id="b622f-130">Trovare l'area **OnClick ()** della sottosezione **Events**</span><span class="sxs-lookup"><span data-stu-id="b622f-130">Find the **OnClick ()** region of the **Events** subsection</span></span>
2. <span data-ttu-id="b622f-131">Trascinare il **Quad** dalla **gerarchia** nello slot dell'oggetto di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b622f-131">Drag the **Quad** from the **Hierarchy** into the target object slot.</span></span>
3. <span data-ttu-id="b622f-132">Selezionare **SpatializeOnOff. SwapSpatialization** nella casella di riepilogo a discesa azione.</span><span class="sxs-lookup"><span data-stu-id="b622f-132">Select **SpatializeOnOff.SwapSpatialization** from the action drop-down box.</span></span>

<span data-ttu-id="b622f-133">Una volta apportate queste modifiche, il componente **interagisce** sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="b622f-133">After these changes, the **Interactable** component will look like this:</span></span>

![Impostazioni azione pulsante](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a><span data-ttu-id="b622f-135">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="b622f-135">Next steps</span></span>

<span data-ttu-id="b622f-136">Provare l'app in un HoloLens 2 o nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="b622f-136">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="b622f-137">Nell'app è ora possibile toccare il pulsante per attivare e disattivare la spazializzazione nel video.</span><span class="sxs-lookup"><span data-stu-id="b622f-137">In the app, you can now touch the button to activate and deactivate spatialization on the video.</span></span> <span data-ttu-id="b622f-138">Quando si esegue il test nell'editor di Unity, premere la barra spaziatrice e scorrere con la rotellina di scorrimento per attivare la simulazione manuale.</span><span class="sxs-lookup"><span data-stu-id="b622f-138">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="b622f-139">Capitolo 5</span><span class="sxs-lookup"><span data-stu-id="b622f-139">Chapter 5</span></span>](unity-spatial-audio-ch5.md) 

