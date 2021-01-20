---
title: Esercitazioni audio spaziali-4. Abilitazione e disabilitazione dell'audio spaziale in fase di esecuzione
description: Usare un pulsante per abilitare e disabilitare la spazializzazione dell'audio in fase di esecuzione.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale, MRTK, Toolkit per realtà mista, UWP, Windows 10, HRTF, funzione di trasferimento relativa alla testa, Reverb, Microsoft Spatializer
ms.openlocfilehash: 9239c45efa5196b94fe2e05f85a2e83df6c7789f
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578320"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a>4. Abilitazione e disabilitazione della spazializzazione in fase di esecuzione

## <a name="overview"></a>Panoramica

In questa esercitazione si apprenderà come abilitare e disabilitare la spazializzazione in fase di esecuzione e come testarla nell'editor di Unity e in HoloLens 2.

## <a name="objectives"></a>Obiettivi

* Aggiungere un nuovo script per controllare la spazializzazione in un oggetto gioco
* Unità dello script di controllo della spazializzazione dalle azioni dei pulsanti

## <a name="add-spatialization-control-script"></a>Aggiungi script di controllo di spazializzazione

 Fare clic con il pulsante destro del mouse nella finestra del progetto e scegliere **Crea**  >  **script c#** per creare un nuovo script c#, immettere un nome appropriato per lo script, ad esempio _SpatializeOnOff_:

![Crea script](images/spatial-audio/spatial-audio-04-section1-step1-1.png)

Fare doppio clic sullo script nella finestra del progetto per aprirlo in Visual Studio. Sostituire il contenuto dello script predefinito con il codice seguente:

> [!NOTE]
> Diverse righe dello script sono impostate come commento. Queste righe verranno annullate come commento nel [capitolo successivo: uso di Reverb per aggiungere la distanza all'audio spaziale](unity-spatial-audio-ch5.md).

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
> Per abilitare o disabilitare la spazializzazione, lo script regola solo la proprietà **spatialBlend** , lasciando abilitata la proprietà di **spazializzazione** . In questa modalità, Unity applica comunque la curva del **volume** . In caso contrario, se l'utente dovesse disabilitare la spazializzazione quando si è distante dall'origine, l'incremento del volume verrà improvvisamente interrotto.
> Se si preferisce disabilitare completamente la spazializzazione, modificare lo script in modo da regolare anche la proprietà Boolean di **spazializzazione** della variabile **SourceObject** .

## <a name="attach-your-script-and-drive-it-from-the-button"></a>Alleghi lo script e lo guidi dal pulsante

Selezionare **Quad** nella gerarchia e nella finestra di controllo usare il pulsante Aggiungi componente per aggiungere **SpatializeOnOff (script)**

![Aggiungi script a Quad](images/spatial-audio/spatial-audio-04-section2-step1-1.png)

Nella gerarchia individuare **PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro**.

Con l'oggetto **Quad** ancora selezionato nella gerarchia, nella finestra Inspector individuare il componente **Spatialize on (script)** , quindi trascinare e rilasciare il componente **TextMeshPro** di PressableButtonHoloLens2.

![Trovare l'oggetto PressableButtonHoloLens2 nella gerarchia](images/spatial-audio/spatial-audio-04-section2-step1-2.png)

Per impostare il pulsante per chiamare lo script **SpatializeOnOff** quando viene rilasciato il pulsante, è necessario configurare lo script interagibile.

Nella finestra gerarchia selezionare il **PressableButtonHoloLens2**. Nella finestra di controllo individuare il componente **interactable (script)** e fare clic sull'icona + sotto l'evento OnClick ().

* Con l'oggetto **PressableButtonHoloLens2** ancora selezionato nella finestra gerarchia, fare clic e trascinare l'oggetto **Quad** dalla finestra gerarchia nel campo vuoto **None (oggetto)** dell'evento appena aggiunto per rendere l'oggetto ButtonParent in ascolto dell'evento click del pulsante da questo pulsante:

* Fai clic sull'elenco a discesa **No Function** (Nessuna funzione) dello stesso evento. Selezionare quindi **SpatializeOnOff**  >  **SwapSpatialization ()** per attivare e disattivare l'audio spaziale

![Impostazioni azione pulsante](images/spatial-audio/spatial-audio-04-section2-step1-3.png)

## <a name="congratulations"></a>Lezione completata

In questa esercitazione si è appreso come abilitare e disabilitare la spazializzazione in fase di esecuzione, testare l'app in un HoloLens 2 o nell'editor di Unity. Nell'app è ora possibile fare clic sul pulsante per attivare e disattivare la spazializzazione dell'audio.

Nell'esercitazione successiva verrà aggiunto un effetto di riverbero per dare un senso alla distanza.

> [!TIP]
> Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!div class="nextstepaction"]
> [Esercitazione successiva: 5. uso di Reverb per aggiungere la distanza all'audio spaziale](unity-spatial-audio-ch5.md)
