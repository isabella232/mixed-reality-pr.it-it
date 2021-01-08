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
# <a name="enabling-and-disabling-spatialization-at-run-time"></a>Abilitazione e disabilitazione della spazializzazione in fase di esecuzione

## <a name="objectives"></a>Obiettivi

In questo quarto capitolo, verranno illustrate le operazioni seguenti:
* Aggiungere un nuovo script per controllare la spazializzazione in un oggetto gioco
* Unità dello script di controllo della spazializzazione dalle azioni dei pulsanti

## <a name="add-spatialization-control-script"></a>Aggiungi script di controllo di spazializzazione

Fare clic con il pulsante destro del mouse nel riquadro **progetto** e creare un nuovo script c# scegliendo **Crea-> script c#**. Denominare lo script "SpatializeOnOff".

![Crea script](images/spatial-audio/create-script.png)

Fare doppio clic sullo script nel riquadro **progetto** per aprirlo in Visual Studio. Sostituire il contenuto dello script predefinito con il codice seguente:

> [!NOTE]
> Diverse righe dello script sono impostate come commento. Queste righe verranno annullate come commento nel [capitolo 5](unity-spatial-audio-ch5.md).

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
> Per abilitare o disabilitare la spazializzazione, lo script regola solo la proprietà **spatialBlend** , lasciando abilitata la proprietà di **spazializzazione** . In questa modalità, Unity applica comunque la curva del **volume** . In caso contrario, se l'utente dovesse disabilitare la spazializzazione quando si è distante dall'origine, l'incremento del volume verrà improvvisamente interrotto. <br> <br>
> Se si preferisce disabilitare completamente la spazializzazione, modificare lo script in modo da regolare anche la proprietà Boolean di **spazializzazione** della variabile **SourceObject** .

## <a name="attach-your-script-and-drive-it-from-the-button"></a>Alleghi lo script e lo guidi dal pulsante

Nel riquadro **Inspector** del **Quad** fare clic su **Add Component** e aggiungere lo script **Spatialize on off** :

![Aggiungi script a Quad](images/spatial-audio/add-script-to-quad.png)

Sul componente **Spatialize on off** del **Quad**:
1. Trovare l'oggetto **PressableButtonHoloLens2-> IconAndText-> TextMeshPro** nella **gerarchia**:

![Trovare l'oggetto PressableButtonHoloLens2 nella gerarchia](images/spatial-audio/pressable-button-object.png)

2. Trascinare l'oggetto **TextMeshPro** nel campo **ButtonTextObject** del componente **Spatialize on off**

Una volta apportate queste modifiche, il componente **Spatialize on** of the **Quad** sarà simile al seguente:

![Spatialize on Basic](images/spatial-audio/spatialize-on-off-basic.png)

Per impostare il pulsante per chiamare lo script **Spatialize on off** quando si rilascia il pulsante, aprire il riquadro **Inspector** dell'oggetto **PressableButtonHoloLens2** , trovare il componente **interactable** e:
1. Trovare l'area **OnClick ()** della sottosezione **Events**
2. Trascinare il **Quad** dalla **gerarchia** nello slot dell'oggetto di destinazione.
3. Selezionare **SpatializeOnOff. SwapSpatialization** nella casella di riepilogo a discesa azione.

Una volta apportate queste modifiche, il componente **interagisce** sarà simile al seguente:

![Impostazioni azione pulsante](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a>Passaggi successivi

Provare l'app in un HoloLens 2 o nell'editor di Unity. Nell'app è ora possibile toccare il pulsante per attivare e disattivare la spazializzazione nel video. Quando si esegue il test nell'editor di Unity, premere la barra spaziatrice e scorrere con la rotellina di scorrimento per attivare la simulazione manuale. 

> [!div class="nextstepaction"]
> [Capitolo 5](unity-spatial-audio-ch5.md) 

