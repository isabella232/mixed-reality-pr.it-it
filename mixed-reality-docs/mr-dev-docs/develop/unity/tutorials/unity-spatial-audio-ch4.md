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
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a>4. Abilitazione e disabilitazione della spazializzazione in fase di esecuzione

## <a name="overview"></a>Panoramica

In questa esercitazione si apprenderà come abilitare e disabilitare la spazializzazione in fase di esecuzione e testarla nell'editor di Unity e HoloLens 2.

## <a name="objectives"></a>Obiettivi

* Aggiungere un nuovo script per controllare la spazializzazione in un oggetto gioco
* Eseguire lo script di controllo della spazializzazione dalle azioni dei pulsanti

## <a name="add-spatialization-control-script"></a>Aggiungere lo script di controllo della spazializzazione

 Fare clic con il pulsante destro del mouse nella finestra Progetto e scegliere Crea script C# per creare un nuovo script C#, immettere un nome appropriato per lo script, ad esempio  >   _SpatializeOnOff:_

![Crea script](images/spatial-audio/spatial-audio-04-section1-step1-1.PNG)

Fare doppio clic nello script nella finestra Progetto per aprirlo in Visual Studio. Sostituire il contenuto dello script predefinito con il codice seguente:

> [!NOTE]
> Diverse righe dello script sono commentate. Queste righe verranno decommentate in Next Chapter: Using reverb to add distance to spatial audio ( Capitolo successivo: Uso [del riverbero per aggiungere la distanza all'audio spaziale).](unity-spatial-audio-ch5.md)

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
> Per abilitare o disabilitare la spazializzazione, lo script regola solo la proprietà **spatialBlend,** lasciando abilitata **la proprietà spatialization.** In questa modalità Unity applica ancora la **curva volume.** In caso contrario, se l'utente deve disabilitare la spazializzazione quando è lontano dall'origine, il volume aumenta improvvisamente.
> Se si preferisce disabilitare completamente la spazializzazione, modificare lo script per modificare anche la proprietà **booleana spatialization** della **variabile SourceObject.**

## <a name="attach-your-script-and-drive-it-from-the-button"></a>Collegare lo script e guidarlo dal pulsante

Selezionare **Quad** nella gerarchia e nella finestra Inspector (Controllo) usare il pulsante Add Component (Aggiungi componente) per aggiungere **SpatializeOnOff(Script)**

![Aggiungere lo script al quad](images/spatial-audio/spatial-audio-04-section2-step1-1.PNG)

Nella gerarchia individuare **PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro**.

Con l'oggetto **Quad** ancora selezionato nella gerarchia, nella finestra Inspector (Controllo) individua il componente **Spatialize On Off (Script) (Spazializza** su off - Script) e trascina TextMeshPro Component (Componente **TextMeshPro)** di PressableButtonHoloLens2.

![Trovare l'oggetto PressableButtonHoloLens2 nella gerarchia](images/spatial-audio/spatial-audio-04-section2-step1-2.PNG)

Per impostare il pulsante in modo che chiami lo script **SpatializeOnOff** quando viene rilasciato, è necessario configurare lo script con interazione.

Nella finestra Hierarchy (Gerarchia) seleziona **PressableButtonHoloLens2.** Nella finestra Inspector (Controllo) individua il **componente Interactable (Script) (Interagiscibile - Script)** e fai clic sull'icona + sotto l'evento OnClick ().

* Con l'oggetto **PressableButtonHoloLens2** ancora selezionato nella finestra Hierarchy (Gerarchia), fai clic e trascina l'oggetto **Quad** dalla finestra Hierarchy (Gerarchia) nel campo **vuoto None (Object) (Nessuno - Oggetto)** dell'evento appena aggiunto per fare in modo che l'oggetto ButtonParent sia in ascolto dell'evento click del pulsante da questo pulsante:

* Fai clic sull'elenco a discesa **No Function** (Nessuna funzione) dello stesso evento. Selezionare quindi **SpatializeOnOff**  >  **SwapSpatialization () per** attivare e disattivare l'audio spaziale

![Impostazioni dell'azione pulsante](images/spatial-audio/spatial-audio-04-section2-step1-3.PNG)

## <a name="congratulations"></a>Lezione completata

In questa esercitazione si è appreso come abilitare e disabilitare la spazializzazione in fase di esecuzione, testare l'app in un HoloLens 2 o nell'editor di Unity. Nell'app è ora possibile fare clic sul pulsante per attivare e disattivare la spazializzazione dell'audio.

Nell'esercitazione successiva si aggiungerà un effetto riverbero per dare ai suoni un senso di distanza.

> [!TIP]
> Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!div class="nextstepaction"]
> [Esercitazione successiva: 5. Uso del riverbero per aggiungere la distanza all'audio spaziale](unity-spatial-audio-ch5.md)
